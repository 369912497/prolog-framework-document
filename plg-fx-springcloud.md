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
prolog: 
  redis: #redis pool 配置
    maxTotal: 15 #最大连接数
    maxIdle: 10 #最大空闲连接数
    minIdle: 1 #最小空闲连接数
    maxWaitMillis: 10000 #ms 连接等待时间
    host: 127.0.0.1
    port: 6379
    timeout: 5000 #ms
    password: prolog0212
    database: 0
    ssl: false
```

> #### 使用

* 直接使用JedisManager的静态方法

```java
JedisManager.getString(key);
```



