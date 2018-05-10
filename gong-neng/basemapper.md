## BaseMapper

BaseMapper是封装在plg-fx-dao模块中，BaseMapper对数据库操作的通用方法进行了封装，具体封装了如下方法：

![](/assets/import3.png)

使用时直接对BaseMapper进行继承即可

```
import com.prolog.framework.dao.mapper.BaseMapper;
import com.prolog.project.wms.model.User;

public interface UserMapper extends BaseMapper<User>{

}
```

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

> #### deleteByIds\(Object\[\] ids,Class&lt;T&gt; c\)

```
@Test
public void testDelete(){
       mapper.deleteByIds(new Integer[]{1,2,3}, User.class);
}
```



