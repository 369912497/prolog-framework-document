## 权限模块

> #### 模块名称

```
plg-fx-authority-core
```

> #### 引用

```xml
   <dependency>
        <groupId>com.prolog.framework</groupId>
        <artifactId>plg-fx-authorization-core</artifactId>
        <version>${prolog.framework.version}</version>
    </dependency>
```

> #### 配置

```yaml
prolog: 
  ms: 
    clientId: ${spring.application.name}
    clientSecret: prolog0212
    oauthServer: service-authorization
```

> #### 使用

@EnablePrologSecurityServer\(webConfig=false,resourceConfig=true\)，开启权限服务，参数webConfig用于标识是否开启系统权限拦截，默认关闭。resourceConfig用于标识是否开启资源服务权限拦截，默认开启。

当webConfig=true时，需要实现

@EnablePrologTokenInterceptor

