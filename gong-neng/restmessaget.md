## RestMessage&lt;T&gt;

RestMessage&lt;T&gt;是对返回结果进行了封装，其数据展现形式为：

```
｛
success:true,
message:"消息",
data:Object
｝
```

使用方法：

```
RestMessage.newInstance(true, "获取数据成功",list);

RestMessage.newInstance(true, "获取数据成功",User);
```



