# 权限模块

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

* resourceConfig为true是启用资源服务（使用框架提供的ResourceServerConfigurerAdapter），须实现com.prolog.framework.authority.core.service.IAuthorityService接口

* webConfig为true是启用web拦截（使用框架提供的WebSecurityConfigurerAdapter），须实现com.prolog.framework.authority.core.service.IUserService接口和com.prolog.framework.authority.core.service.IAuthorityService接口

* 若使用自定义的ResourceServerConfigurerAdapter和WebSecurityConfigurerAdapter，可配置@EnablePrologSecurityServer\(resourceConfig=false,webConfig=false\)

```java
@EnablePrologTokenInterceptor
```

@EnablePrologTokenInterceptor注解将启用feign的token拦截器，根据配置将去权限服务器获取token并放入feign请求header中。

```
@EnablePrologAuthorizationServer
```

定义一个授权服务，需要实现com.prolog.framework.authority.core.service.IClientService接口和com.prolog.framework.authority.core.service.IUserService，同时需要提供AuthenticationManager实例

```
@EnablePrologResourceServer
```

与@EnablePrologSecurityServer\(resourceConfig=true,webConfig=false\)功能相同



```
@EnablePrologWebSecurityServer
```

与@EnablePrologSecurityServer\(resourceConfig=false,webConfig=true\)功能相同

