## 微服务模块plg-fx-microservice

> #### 模块名称

```
plg-fx-microservice
```

> #### 引用

```xml
    <parent>
        <groupId>com.prolog.framework</groupId>
          <artifactId>plg-fx-springcloud-parent</artifactId>
          <version>${plg.fx.verison}</version>
    </parent>

<dependency>
     <groupId>com.prolog.framework</groupId>
     <artifactId>plg-fx-microservice</artifactId>
     <version>${plg.fx.verison}</version>
 </dependency>
```

> #### 配置

```yaml
eureka: 
  client: 
    serviceUrl: 
      defaultZone: http://127.0.0.1:8761/eureka/
  instance: 
    # 注册时使用ip而不是主机名
    preferIpAddress: true
    instanceId: ${server.ipAddress}:${server.port}
    health-check-url-path: /actuator/health
    # 状态地址为api地址
    statusPageUrlPath: /${server.servlet.contextpath}/apidoc.html

```

> #### 使用

* 在controller中使用注解 @ControllerLog 进行注解，可注解在类上，亦可注解在方法上



