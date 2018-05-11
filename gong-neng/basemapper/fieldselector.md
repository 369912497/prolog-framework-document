## FeildSelector

FeildSelector是对字段进行过滤，主要用于数据的查询、插入和修改。FieldSelector中包含newInstance静态方法进构建FieldSelector对象。

![](/assets/import6.png)

使用方法如下：

```java
@Test
    public void testUpdate2(){
        User u = new User();
        u.setId(8);
        u.setNumber("008");
        u.setName("沙僧");
        LmsTmsZone ltz =new LmsTmsZone();
        ltz.setZoneid("01100118");
        u.setZone(ltz);
        LmsTmsZone ltz2 =new LmsTmsZone();
        ltz2.setZoneid("01100108");
        u.setZone2(ltz2);
        mapper.updateFields(u, FieldSelector.newInstance().include("zone").include("name"));
    }
```



