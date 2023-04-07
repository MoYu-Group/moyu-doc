# 建表规范
为保证开发风格统一，MoYu 小组在开发的时候需要遵循以下建表规范：

## 公共字段

所有数据表在创建时应该统一包含以下字段和属性，关联表除外，方便抽离到基类中统一管理
```sql
CREATE TABLE `moyu`  (
  `id` bigint UNSIGNED NOT NULL AUTO_INCREMENT COMMENT '主键',
  `create_by` varchar(128) NOT NULL DEFAULT '' COMMENT '创建人',
  `update_by` varchar(128) NOT NULL DEFAULT '' COMMENT '修改人',
  `create_time` datetime NOT NULL DEFAULT CURRENT_TIMESTAMP COMMENT '创建时间',
  `update_time` datetime NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '修改时间',
  `is_deleted` tinyint UNSIGNED NOT NULL DEFAULT 0 COMMENT '是否删除 0--未删除 1--已删除',
  PRIMARY KEY (`id`)
);
```