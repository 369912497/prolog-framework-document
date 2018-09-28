工作流plg-fx-activiti

作为jar包使用，环境搭建。

> 引用

```
    <dependency>
        <groupId>org.activiti</groupId>
        <artifactId>activiti-engine</artifactId>
        <version>6.0.0</version>
    </dependency>

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

> 配置
>
> 使用

service层提供的方法

1. 向组任务中添加或者删除成员

```java
       //向组任务中添加或删除成员
    public void addOrDeleteEmpToGroupTask(String taskId,List<String> DelaUserName,String flag)
```

        参数：任务id，成员名称list，flag（add或者delete代表新增或者删除）

1. 




