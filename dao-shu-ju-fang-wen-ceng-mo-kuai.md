# dao** - 数据访问层模块**

> #### 模块名称

```
plg-fx-dao
```

> #### 引用

```
<dependency>
     <groupId>com.prolog.framework</groupId>
     <artifactId>plg-fx-starter-dao</artifactId>
     <version>${plg.fx.verison}</version>
 </dependency>
```

> #### 配置

```
prolog:
  dao:
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

```
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



