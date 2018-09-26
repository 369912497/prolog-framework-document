Plg-fx-activiti

# activiti-工作流通用接口

> 

```
g-cs-activiti
```

> 引用

```
    <dependency>
        <groupId>org.activiti</groupId>
        <artifactId>activiti-spring</artifactId>
        <version>6.0.0</version>
    </dependency>

    <dependency>
        <groupId>org.activiti</groupId>
        <artifactId>activiti-json-converter</artifactId>
        <version>6.0.0</version>
    </dependency>
```

> 配置        application.yml

* ```
  prolog: 
    activiti: 
       filePath: C:/kingsley/plg_work/workspace/20180925/plg-cs-activiti/src/main/resources/bpm
  ```


```
   这里是配置bpmn的上传的存放的路径。
```

> 使用

* 上传bpmn文件。
  在画好bpmn文件之后，将bpmn文件上传至工程资源文件。
  url:localhost:9900\/activiti\/fileUpload

```java
    @ApiOperation(value="上传bpmn文件",notes="上传bpmn文件")
    @PostMapping("/fileUpload")
    public RestMessage<?> upBPMNfile(MultipartFile file) throws Exception
```



