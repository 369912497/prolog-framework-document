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

@EnablePrologSecurityServer\(webConfig=false,resourceConfig=true\)

@EnablePrologTokenInterceptor

