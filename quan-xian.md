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
spring:
  redis:
    host: 192.168.0.206
    port: 6379
    password: prolog0212

#当作为客户端时，须配置如下参数
prolog: 
  ms: 
    clientId: ${spring.application.name}
    clientSecret: prolog0212
    oauthServer: service-authorization
```

> #### 使用

在启动类上添加标签

```java
@EnablePrologSecurityServer(resourceConfig=true,webConfig=true)
```

@EnablePrologSecurityServer有两个参数resourceConfig和webConfig，他们都是boolean类型的。

* resourceConfig为true是启用资源服务（使用框架提供的ResourceServerConfigurerAdapter），须实现IAuthorityService接口

* webConfig为true是启用web拦截（使用框架提供的WebSecurityConfigurerAdapter），须实现IUserService接口和IAuthorityService接口

* 若使用自定义的ResourceServerConfigurerAdapter和WebSecurityConfigurerAdapter，可配置@EnablePrologSecurityServer\(resourceConfig=false,webConfig=false\)

```
@EnablePrologTokenInterceptor
```



