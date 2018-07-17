# plg-fx-authority-core

> #### 模块名称

```
plg-fx-authority-core
```

> #### 引用

```xml
<dependency>
     <groupId>com.prolog.framework</groupId>
     <artifactId>plg-fx-authority-core</artifactId>
     <version>${plg.fx.verison}</version>
 </dependency>
```

> #### 配置

```yaml

```

> #### 使用

在启动类上添加标签

```java
@EnablePrologSecurityServer(resourceConfig=true,webConfig=true)
```

@EnablePrologSecurityServer有两个参数resourceConfig和webConfig，他们都是boolean类型的。

* resourceConfig为true是启用资源服务，须实现IAuthorityService接口

* webConfig为true是启用web拦截（使用框架提供的WebSecurityConfigurerAdapter），须实现IUserService接口和IAuthorityService接口



