Plg-cs-activiti

# activiti-工作流通用接口

&gt;

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
    public RestMessage<String> upBPMNfile(MultipartFile file) throws Exception
```

这里我们会得到文件上传后的相对路径，以便后面进行部署bpmn文件

* 根据bpmn文件部署流程定义

  ```
   url:localhost:9900/activiti/deploybpmn
  ```

```java
       @ApiOperation(value="部署bpmn文件",notes="根据bpmn文件部署流程定义")
    @GetMapping("/deploybpmn")
    public RestMessage<Deployment> deployByBpmn(String bpmnurl) throws Exception
```

这里我们使用bpmn文件的相对路径来部署流程定义，返回流程定义的信息，流程定义Id，定义名称，部署时间等等。

* 根据流程定义ID下载bpmn和png 文件

  ```
   url:localhost:9900/activiti/resource
  ```

  ```
   将文件下载到本地C盘的根目录
  ```

```java
        @ApiOperation(value="下载流程资源文件",notes="根据流程定义id来下载流程资源文件")
    @GetMapping("/resource")
    public RestMessage<?> downResource(String processDefinitionId) throws Exception
```

返回文件的路径，两个文件路径用-隔开。

* 按照流程key值来启动流程定义，带有流程变量定义

  ```
  url：localhost:9900/activiti/processes
  ```

  根据流程的key值，也就是创建bpmn文件的id的值来启动流程，这里我们可以灵活传递一些流程变量来赋值一些变量。

```java
@ApiOperation(value="启动流程",notes="附属流程变量")
    @ApiImplicitParams({
        @ApiImplicitParam(name = "ProcessInstanceKey", value = "流程key值", required = true, dataType = "String")
    })
    @PostMapping("/processes")
    public RestMessage<?> processStart(@RequestParam Map<String,Object> map,String ProcessInstanceKey) throws Exception
```

我们会得到流程实例的一些信息和任务信息。

* 查询待认领任务,根据用户来查询待认领任务

  ```
   url:localhost:9900/activiti/task
  ```

```java
      @ApiOperation(value="查询个人待认领任务",notes="根据用户来查询待认领任务")
    @GetMapping("/task")
    public RestMessage<?> taskingByUser(@RequestParam String userId)
```

这里会返回任务list，包含任务id，名称，以及一些流程变量。

* 根据任务ID查询办理人列表

url:localhost:9900/activiti/identityLinksForTask

```java
    @ApiOperation(value="任务办理人",notes="根据任务id查询办理人")
    @GetMapping("/identityLinksForTask")
    public RestMessage<?> identityLinksForTask(String taskId) throws Exception
```

返回List&lt;IdentityLink&gt;。

* 认领任务

```java
@ApiOperation(value="认领任务",notes="根据用户和流程实例id认领任务")
    @GetMapping("/tasktouser")
    public RestMessage<?> taskGet(String user ,String instanceId)
```

* 完后任务

```java
@ApiOperation(value="完成任务",notes="完成任务")
    @GetMapping("/taskdown")
    public RestMessage<?> taskdown(String taskId)
```

* 查询历史任务,单条流程实例id查询

```java
@ApiOperation(value="流程实例历史记录",notes="根据流程实例id查询历史记录")
    @GetMapping("/history")
    public RestMessage<?> historyInfo(String instanceId) throws Exception
```

* 按照流程定义id来查询历史记录

```java
@ApiOperation(value="流程定义历史记录",notes="根据流程定义id查询历史记录")
    @GetMapping("/history/define")
    public RestMessage<?> historyInfoByde(String defineId) throws Exception
```

* 根据用户来查询他参与过的流程信息

```java
@ApiOperation(value="用户流程历史记录",notes="根据用户查询历史记录")
    @GetMapping("/historyaboutusr")
    public RestMessage<?> historyInfoByUser(String username) throws Exception
```

* 删除流程定义

```java
@ApiOperation(value="删除流程",notes="根据流程部署id删除，后面的参数是是否级联删除")
    @GetMapping("/deleteProcess")
    public RestMessage<?> deleteProcessDefinitonByDeploymentId(String deploymentId,boolean cascade) throws Exception
```

* 获取所有部署的流程信息
  ```
  //查询所有历史记录
  ```

```java
//获取所有部署的流程信息
    //查询所有历史记录
    @ApiOperation(value="流程部署记录",notes="所有")
    @GetMapping("/deployhistoryall")
    public RestMessage<?> deployhistoryall(int maxResults,int firstResult) throws Exception
```

* 查询所有历史记录

```java
//查询所有历史记录
    @ApiOperation(value="查询所有历史记录",notes="查询所有历史记录")
    @GetMapping("/historyall")
    public RestMessage<?> historyall(int maxResults,int firstResult) throws Exception
```



