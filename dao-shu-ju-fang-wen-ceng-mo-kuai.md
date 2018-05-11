# dao** - 数据访问层模块**

> #### 模块名称

```
plg-fx-dao
```

> #### 引用

```xml
<dependency>
     <groupId>com.prolog.framework</groupId>
     <artifactId>plg-fx-starter-dao</artifactId>
     <version>${plg.fx.verison}</version>
 </dependency>
```

> #### 配置

```yaml
prolog: 
  dao : 
    dialect: mysql
    pagehelper: #pagehelper分页插件配置
      helperDialect: ${prolog.dao.dialect}
      reasonable: true
      supportMethodsArguments: true
      pageSizeZero: false
      params: count=countSql
    #公共配置与profiles选择无关 mapperLocations指的路径是src/main/resources
    mybatis: 
      typeAliasesPackage: com.prolog.test.product.model
      mapperLocations: classpath:mappers/*.xml
```

> #### 使用

* 对mybaits和com.github.pagehelper进行了无侵入式封装，配置和使用不变

* 在开发mapper时可继承BaseMapper，BaseMapper中封装了curd的通用方法，如：

```java
import com.prolog.framework.dao.mapper.BaseMapper;
import com.prolog.test.mysqlplus.model.Dept;

public interface DeptMapper extends BaseMapper<Dept>{

}
```

* 使用分页参考方式如下

```
import com.prolog.framework.core.dto.Page;
import com.github.pagehelper.PageHelper;

public Page<Product> getPage(int pageNum, int pageSize) {
           PageHelper.startPage(pageNum, pageSize);
           Page<Product> page = PageUtils.getPage(productMapper.findByMap(null, Product.class));
           return page;
     }
```

* CommonMapper是可以直接使用的通用mapper

```
//oracle sequence
String getSequenceNextVal(String sequenceName);
//存储过程调用
List<Map<String,Object>> execProcedure(String procedureName,Map<String,Object> params,List<ProcedureParam> paramInfo)

    @Autowired
    private CommonMapper cmapper;

    @Test
     public void testSequence(){
           String val = cmapper.getSequenceNextVal("SYS_CODE");
           System.out.println(val);
     }

     @Test
     public void testProc2(){

           Map<String,Object> map = new HashMap<String,Object>();
           map.put("errorCode", 0);
           map.put("errorText", "");
           map.put("codeType", "CarrierID");
           map.put("segid", "Seed");

           List<ProcedureParam> list = new ArrayList<ProcedureParam>();
           ProcedureParam pp1 = new ProcedureParam("errorCode",Mode.MODE_OUT,JdbcType.INTEGER.name());
           ProcedureParam pp2 = new ProcedureParam("errorText",Mode.MODE_OUT,JdbcType.VARCHAR.name());
           ProcedureParam pp3 = new ProcedureParam("codeType",Mode.MODE_IN,JdbcType.VARCHAR.name());
           ProcedureParam pp4 = new ProcedureParam("segid",Mode.MODE_IN,JdbcType.VARCHAR.name());

           list.add(pp1);
           list.add(pp2);
           list.add(pp3);
           list.add(pp4);

           cmapper.execProcedure("P_GENBILLNO", map, list);
           //mapper.getCompanyId(map);
           System.out.println(map.get("errorCode"));
           System.out.println(map.get("errorText"));

     }
```



