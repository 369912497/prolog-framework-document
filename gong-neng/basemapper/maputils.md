## MapUtils

MapUtils是一个快速构建map的工具类，使用方法如下：

```java
    @Test
    public void testSelect2(){
        List<User> list = mapper.findByMap(MapUtils.put("zone", "01100110").getMap(), User.class);
        list.forEach((x) -> System.out.println(x.getId()+"\t"+x.getZone().getZname()));
        System.out.println(list.size());
    }
```



