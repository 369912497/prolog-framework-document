# **plg-fx-apidoc**

> #### 引用

```
<dependency>
     <groupId>com.prolog.framework</groupId>
     <artifactId>plg-fx-starter-apidoc</artifactId>
     <version>${plg.fx.verison}</version>
 </dependency>
```

> #### 配置

```
prolog:
  apidoc:
    title: 订单服务API文档
    basePackage: com.prolog.framework
    description: 订单服务api
    version: 1.0prolog:
```

> #### 使用

* 在传输对象包括Entity、vo、Dto使用@ApiModel\(description="产品实体"\) 或 @ApiModelProperty\(value = "产品id"\) 进行注解

* controller进行相关注解（注解参考swagger2），如下示例：

```
@Api(tags="产品服务")
@RestController
@RequestMapping("/product")
@ControllerLog("测试-日志")
public class ProductController {

     @Autowired
     private IProductBiz productBiz;

     @ApiOperation(value="新增商品", notes="新增商品")
     @PostMapping("/0")
     @ControllerLog("新增商品")
     public RestMessage<?> saveProduct(Product product) throws Exception{
           productBiz.save(product);
           return  RestMessage.newInstance(true, "保存成功",product.getId());
     }
｝
```

* 启动项目访问地址：http://host:port/contextpath/apidoc.html



