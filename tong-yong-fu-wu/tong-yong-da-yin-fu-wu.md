## 通用打印服务 - PlgPrintServer

> ##### 简介

通用打印服务是一个兼容多种打印方案的通用服务，支持B/S、C/S打印，支持客户端部署和集中部署。服务使用web api接口对外提供服务。

打印服务是基于grid++report开发，所以打印规范遵循grid++report规范。

> ##### 快速使用

1. 安装好打印服务程序，启动服务，可在系统托盘看到服务程序图标，如下图示：

![](/assets/import11.png)

2.双击图标或右键选择显示主界面，在主界面中启动服务，默认已启动，默认端口6060

![](/assets/import15.png)

3.提交打印请求。客户端直接向服务端发送打印请求，即可进行打印。示例如下

```js
//通过ajax提交请求
 $.ajax({
 type: "POST",
 url: "http://localhost:6060/print", //打印服务地址，print是固定值
 data: reportJsonData, //报表数据 
 contentType:'application/json',
 dataType: "json",
 success: function(data){
             //处理返回值
          }
});
```

请求地址直接向[http://\(server\):6060/print发送打印请求，即可](http://%28server%29:6060/print发送打印请求，即可)

4.更改服务设置。停止服务，单击服务设置，在弹出的对话框中对端口、默认打印机、工作目录进行设置。

![](/assets/import16.png)

5.模版设置。服务会在工作目录下的grf文件夹中查找，所以报表模板需要放在工作目录的grf文件夹中，通过主界面上的模板目录按钮可以快速打开grf文件夹。

```

```



