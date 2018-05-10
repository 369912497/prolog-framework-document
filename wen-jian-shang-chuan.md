文件上传/下载

配置：

```
prolog:
  web:
    multipart:  #文件上传配置
      maxFileSize: 100MB
      maxRequestSize: 100MB
```

文件上传，推荐实践：

```
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

文件下载，推荐实践：

```
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



