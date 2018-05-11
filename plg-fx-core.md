# **core - 核心模块**

> #### 模块名称

```
plg-fx-core
```

> #### 引用

```xml
<dependency>
     <groupId>com.prolog.framework</groupId>
     <artifactId>plg-fx-starter-log</artifactId>
     <version>${plg.fx.verison}</version>
 </dependency>
```

> #### 配置

```yaml
#日志配置文件,在引用中添加以下配置
prolog:
  log:
    implement: com.prolog.framework.log.service.FileLogService #日志实现类全名
    logFilePath: d:/prolog-log.txt #对应实现类需要的参数
```

> #### 使用

* 在controller中使用注解 @ControllerLog 进行注解，可注解在类上，亦可注解在方法上



