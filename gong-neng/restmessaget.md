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

将json字符串转为RestMessage对象

```
RestMessage<UserDto> msg = RestMessage.parseJsonString(ms,new TypeReference<RestMessage<UserDto>>(){});
UserDto userDto = msg.getData();
```

源代码：

```
public class RestMessage<T> implements Message {

    @ApiModelProperty(value = "是否成功")
    private boolean success;
    @ApiModelProperty(value = "消息对象")
    private String message;
    @ApiModelProperty(value = "返回对象")
    private T data;

    public RestMessage(){

    }


    public static <T> RestMessage<T> newInstance(boolean success,String message,T data){
        return new RestMessage<T>(success,message,data);
    }

    public RestMessage(boolean success,String message,T data){
        this.success = success;
        this.message = message;
        this.data = data;
    }

    public boolean isSuccess() {
        return success;
    }
    public void setSuccess(boolean success) {
        this.success = success;
    }
    public String getMessage() {
        return message;
    }
    public void setMessage(String message) {
        this.message = message;
    }
    public T getData() {
        return data;
    }
    public void setData(T data) {
        this.data = data;
    }

    @Override
    public String toJsonString() {
        ObjectMapper mapper = new ObjectMapper();
        try {
            return mapper.writeValueAsString(this);
        } catch (JsonProcessingException e) {
            e.printStackTrace();
            return null;
        }
    }

    public static <S> RestMessage<S> parseJsonString(String jsonstr,TypeReference<RestMessage<S>> typeReference) throws IOException{
        ObjectMapper mapper = new ObjectMapper();
        RestMessage<S> rest = mapper.readValue(jsonstr, typeReference);
        return rest;
    }


}
```



