## @Table

> ##### 说明

@Table用于定义实体与表名的对应关系

> ##### 配置

```
String value(); //表名
String columnPrefix() default "";//所有列前缀
```

如果字段中配置有@Column，columnPrefix无效

