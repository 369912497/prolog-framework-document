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

模块包含了注解@EnablePrologService，此注解包含了如下注解

* @Configuration
* @EnableDiscoveryClient

* @EnableConfigurationProperties\({MicroServiceConfigProperties.class}\)四个注解，通常注解在启动类上。

```java
package com.prolog.framework.cs.authorization;

import org.mybatis.spring.annotation.MapperScan;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.transaction.annotation.EnableTransactionManagement;

import com.prolog.framework.authority.core.annotation.EnablePrologSecurityServer;
import com.prolog.framework.microservice.annotation.EnablePrologService;

@SpringBootApplication()
@EnablePrologService(loadBalanced=true)
public class AuthorizationApplication {

    public static void main( String[] args )
    {
        SpringApplication.run(AuthorizationApplication.class, args);
    }

}
```

添加此注解后，系统会自动生成一个RestTemplate的bean。通过参数loadBalanced来控制是否启用负载均衡，默认为true，当开启负载均衡时，将自动配置@EnableFeignClients

