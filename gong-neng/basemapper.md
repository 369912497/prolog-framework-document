## BaseMapper

BaseMapper是封装在plg-fx-dao模块中，BaseMapper对数据库操作的通用方法进行了封装，具体封装了如下方法：

![](/assets/import3.png)

> #### deleteByCriteria\(Criteria criteria\)

```
    @Test
    public void testDelete2(){
        Criteria c = Criteria.forClass(User.class);
        c.setRestriction(Restrictions.eq("id", 7));
        mapper.deleteByCriteria(c);;
    }
```

备注：对于实体字段（@one注解），直接写字段名

> #### deleteById\(Object id,Class&lt;T&gt; c\)

```
    @Test
  public void testDelete1(){
		User u = new User();
		u.setId(8);
		mapper.deleteById(8, User.class);
	}
```



