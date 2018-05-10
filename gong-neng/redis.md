Redis

框架提供了Redis连接池服务，配置如下：

```
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

使用方法：

![](/assets/import9.png)

```
JedisManager.getString(key);
JedisManager.setString(key,value);
JedisManager.setString(key,seconds,value);
JedisManager.del(key);
```



