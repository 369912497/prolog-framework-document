## Web API注解 - 注解controller

Web API 文档核心注解是在controller中，其中包含多个注解标签。

```
@Api(tags="产品服务") //注解api分类名称
```

```
@ApiOperation(value="新增商品", notes="新增商品") //注解操作
```

```
@ApiImplicitParam(name="id",value="商品id",required = true,paramType = "path")//注解单个参数
```



示例：

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

    @ApiOperation(value="更新商品", notes="更新商品")
    @ApiImplicitParam(name="id",value="商品id",required = true,paramType = "path")
    @PutMapping("/{id}")
    @ControllerLog("更新商品")
    public RestMessage<?> updateProduct(Product product,@PathVariable("id")int id) throws Exception{
        product.setId(id);
        productBiz.update(product);
        return  RestMessage.newInstance(true, "更新成功",null);
    }

    @ApiOperation(value="获取产品详细信息", notes="根据url的id来获取产品详细信息")
    @ApiImplicitParam(name = "id", value = "产品ID", required = true, dataType = "int", paramType = "path")
    @GetMapping("/{id}")
    @ControllerLog("获取产品详细信息")
    public RestMessage<Product> getOrder(@PathVariable("id")int id){
        Product pro = productBiz.getById(id);
        //System.out.println(String.format("id:%s,number:%s,name:%s", pro.getId(),pro.getNumber(),pro.getName()));
        return RestMessage.newInstance(true, "查询成功", pro);
    }

    @ApiOperation(value="分页查询产品详细信息", notes="根据url的pageNum和pageSize来获取产品详细信息")
    @ApiImplicitParams({
        @ApiImplicitParam(name = "pageNum", value = "页码", required = true, dataType = "int",paramType = "path")
    })
    @GetMapping("/page/{pageNum}")
    public RestMessage<Page<Product>> getPage(@PathVariable("pageNum")int pageNum,int pageSize){
        return RestMessage.newInstance(true, "查询成功", productBiz.getPage(pageNum, pageSize));
    }

    @ApiOperation(value="根据条件分页查询产品详细信息", notes="根据条件分页查询产品详细信息")
    @ApiImplicitParams({
        @ApiImplicitParam(name = "pageNum", value = "页码", required = true, dataType = "int",paramType = "path"),
        @ApiImplicitParam(name = "pageSize", value = "每页记录数", required = true, dataType = "int")
    })
    @GetMapping("/map/{pageNum}")
    public RestMessage<Page<Product>> getPage(@RequestParam Map<String,Object> map,@PathVariable("pageNum")int pageNum,int pageSize) throws Exception{
        map.remove("pageSize");
        return RestMessage.newInstance(true, "查询成功", productBiz.getByMapForPage(map, pageNum, pageSize));
    }

}
```



