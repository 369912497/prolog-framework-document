# redis** - redis访问模块**

> #### 模块名称

```
plg-fx-redis
```

> #### 引用

```xml
<dependency>
     <groupId>com.prolog.framework</groupId>
     <artifactId>plg-fx-starter-redis</artifactId>
     <version>${plg.fx.verison}</version>
 </dependency>
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



