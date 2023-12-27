# 建表规范
建表时以 MySQL 数据库为代表举例，其他类型数据库自行参考；

为保证开发风格统一，MoYu 小组在开发的时候需要遵循以下建表规范：

## 字段名称

- 表达是与否概念的字段，必须使用 `is_xxx` 的方式命名，数据类型是 `unsigned tinyint`（1 表示是，0 表示否）；
- 表名、字段名必须使用小写字母或数字，禁止出现数字开头，禁止两个下划线中间只出现数字；
- 表名不使用复数名词；
  - 表名应该仅仅表示表里面的实体内容，不应该表示实体数量，对应于 DO 类名也是单数形式，符合表达习惯；
- 禁用保留字，如 `desc`、`range`、`match`、`delayed` 等，请参考 MySQL 官方保留字；
- 小数类型为 `decimal`，禁止使用 `float` 和 `double`；
- 表必备字段：所有数据表在创建时应该统一包含以下字段和属性，关联表除外，方便抽离到基类中统一管理
```sql
CREATE TABLE `moyu`  (
  `id` bigint UNSIGNED NOT NULL AUTO_INCREMENT COMMENT '主键',
  `creator` varchar(128) NOT NULL DEFAULT '' COMMENT '创建人ID',
  `modifier` varchar(128) NOT NULL DEFAULT '' COMMENT '修改人ID',
  `create_time` datetime NOT NULL DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间',
  `update_time` datetime NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '修改时间',
  `is_deleted` tinyint UNSIGNED NOT NULL DEFAULT 0 COMMENT '是否删除 0--未删除 1--已删除',
  PRIMARY KEY (`id`)
);
```
