# service** - web服务模块**

> #### 模块名称

```
plg-fx-service
```

> #### 引用

```xml
<dependency>
     <groupId>com.prolog.framework</groupId>
     <artifactId>plg-fx-starter-service</artifactId>
     <version>${plg.fx.verison}</version>
 </dependency>
```

> #### 配置

```yaml
prolog: 
  web: 
    multipart:  #文件上传配置
      maxFileSize: 100MB
      maxRequestSize: 100MB
```

> #### 使用

* 实现了controller全局异常捕获，在controller中的方法中，可以直接进行异常的抛出，不用处理

* 异常输出为：

```json
｛ "success":false,"message":e.getMessage(),"data":null｝
```

* 文件上传，推荐实践：

```java
@ApiOperation(value="文件上传测试")
    @PostMapping("/testupload")
    public RestMessage<String> uploadImg(@RequestParam("file") List<MultipartFile> files,HttpServletRequest request) throws IOException, Exception {
        for(MultipartFile file : files){
           String contentType = file.getContentType();
            String fileName = file.getOriginalFilename();
            FileUtils.saveFile(file.getBytes(), "D:/", fileName);
        }
        //返回json
        return RestMessage.newInstance(true, "保存成功",null);
    }
```

* 文件下载，推荐实践：

```java
 @ApiOperation(value="文件下载测试")
     @GetMapping("/download")
    public void downLoad(HttpServletResponse response) throws IOException{
        String filename="AliDouble11.pdf";
        String filePath = "d:/" ;
        File file = new File(filePath + "/" + filename);
        response.setContentType("application/force-download");
        response.setHeader("Content-Disposition", "attachment;fileName=" + filename);
        FileUtils.printFile(response.getOutputStream(), file);
    }
```



