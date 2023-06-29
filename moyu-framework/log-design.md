# 日志规范
摸鱼框架统一对日志进行切面处理，这样应用在使用摸鱼框架时就不用关心日志的配置

引入摸鱼框架中的web快速开发模块即可开启aop接口日志

## 格式
摸鱼框架会对aop切面打印两份日志
1. 控制台日志
2. 接口监控日志

### 1 控制台日志
默认位置：应用 `/logs/application.log`

日志格式：`IP地址|httpMethod|请求地址|是否成功|响应耗时|类名|方法名|参数|返回值|错误码|错误日志`
### 2 监控日志
默认位置：应用 `/logs/monitor/operation.log`

日志格式：`AppName|类名|方法名|真实IP|httpMethod|请求地址|是否成功|响应耗时|请求参数|返回值|错误码|错误日志`

## 日志等级
日志等级分为：INFO/DEBUG/WARN/ERROR 四个级别；

其中 ERROR 级别日志是需要开发人员关注的日志，应配置应用 ERROR 级别日志告警；

日志 aop 切面会对继承 BizException 的异常标注对应的异常等级，应用在抛出异常时应统一使用 BizException 异常抛出，抛出时可指定日志等级；

也可继承 ExceptionEnum 枚举基类，在定义枚举的时候定义异常等级，使用枚举抛出 BizException 异常。

## 使用
1. 目前使用需要pom文件加入MoYu共有仓库
```xml
<repositories>
    <repository>
        <id>moyu-group-snapshots</id>
        <name>moyu-group-repository-snapshots</name>
        <url>https://maven.ffis.me/snapshots</url>
        <releases>
            <enabled>false</enabled>
        </releases>
        <snapshots>
            <enabled>true</enabled>
        </snapshots>
    </repository>
</repositories>
```
2. 然后父工程依赖 moyu-framework
```xml
<parent>
    <artifactId>moyu-framework</artifactId>
    <groupId>io.github.moyu-group</groupId>
    <version>1.0.0-SNAPSHOT</version>
</parent>
```
3. 之后导入moyu-web快速开发模块
```xml
<dependency>
    <groupId>io.github.moyu-group</groupId>
    <artifactId>moyu-web-autoconfiguers</artifactId>
</dependency>
```

## 配置
logback-spring.xml 配置引用摸鱼公共日志配置，参考
```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <!--引用 MoYu 框架公共日志配置-->
    <include resource="io/github/moyugroup/logback/logback-base.xml"/>

    <!--定义日志的根logger对象-->
    <root level="INFO">
        <appender-ref ref="CONSOLE"/>
        <appender-ref ref="APPLICATION_ASYNC"/>
    </root>
</configuration>
```
spring 配置文件添加日志切面配置，一般针对 controller 接口层进行 aop 切面处理，可指定日志的输出位置。
```yaml
moyu:
  #方法运行切面日志配置
  method-time:
    #是否启用
    enabled: true
    #日志切点
    pointcut-expression: execution(* io.github.moyugroup..controller..*(..))
    #接口参数截取长度
    paramsMaxLength: 2000
logging:
  #日志输出目录
  file:
    path: ./logs
```
