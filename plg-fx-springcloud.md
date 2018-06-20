# plg-fx-springcloud

> #### 模块名称

```
plg-fx-cloud
```

> #### 引用

```xml
<dependency>
     <groupId>com.prolog.framework</groupId>
     <artifactId>plg-fx-springcloud</artifactId>
     <version>${plg.fx.verison}</version>
 </dependency>

 <dependencyManagement>
    <dependencies>
        <dependency>
             <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-parent</artifactId>
            <version>Finchley.RC2</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>
    </dependencies>
</dependencyManagement>

<repositories>
  <repository>
      <id>spring-milestones</id>
      <name>Spring Milestones</name>
      <url>https://repo.spring.io/libs-milestone</url>
      <snapshots>
          <enabled>false</enabled>
      </snapshots>
  </repository>
</repositories>
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

* 直接使用JedisManager的静态方法

```java
JedisManager.getString(key);
```



