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
#eureka client配置
eureka: 
  client: 
    serviceUrl: 
      defaultZone: http://192.168.3.206:8761/eureka/
  instance: 
    # 注册时使用ip而不是主机名
    preferIpAddress: true
    instanceId: ${server.ipAddress}:${server.port}
    # 状态地址为api地址
    statusPageUrlPath: /${server.servlet.contextpath}/apidoc.html
```

> #### 使用

```java
@EnableDiscoveryClient
```



