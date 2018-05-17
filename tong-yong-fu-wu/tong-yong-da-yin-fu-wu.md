## 通用打印服务 - PlgPrintServer

> ##### 简介

通用打印服务是一个兼容多种打印方案的通用服务，支持B/S、C/S打印，支持客户端部署和集中部署。服务使用web api接口对外提供服务。

打印服务是基于grid++report开发，所以打印规范遵循grid++report规范。

> ##### 快速使用

#### 安装

安装好打印服务程序，启动服务，可在系统托盘看到服务程序图标，如下图示：

![](/assets/import11.png)

#### 运行

双击图标或右键选择显示主界面，在主界面中启动服务，默认已启动，默认端口6060

![](/assets/import20.png)

#### 提交打印请求

客户端直接向服务端发送打印请求，即可进行打印。示例如下

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
             //{"success":true,"message":"打印请求成功"}
          }
});
```

reportJsonData数据格式

```json
 {"url": "http://www.gridreport.cn/demos/grf/4d.grf",
    "printName":"Microsoft XPS Document Writer",
    "data":{
        "City":"武汉",
        "Customer": [{
                "CustomerID": "ALFKI",
                "CompanyName": "三川实业有限公司",
                "ContactName": "刘小姐",
                "ContactTitle": "销售代表",
                "Address": "大崇明路 50 号",
                "City": "天津",
                "Region": "华北",
                "PostalCode": "343567",
                "Country": "中国",
                "Phone": "(030) 30074321",
                "Fax": "(030) 30765452"
            },
            {
                "CustomerID": "ANATR",
                "CompanyName": "东南实业",
                "ContactName": "王先生",
                "ContactTitle": "物主",
                "Address": "承德西路 80 号",
                "City": "天津",
                "Region": "华北",
                "PostalCode": "234575",
                "Country": "中国",
                "Phone": "(030) 35554729",
                "Fax": "(030) 35553744"
            },
            {
                "CustomerID": "BLAUS",
                "CompanyName": "森通",
                "ContactName": "王先生",
                "ContactTitle": "销售代表",
                "Address": "常保阁东 80 号",
                "City": "天津",
                "Region": "华北",
                "PostalCode": "787045",
                "Country": "中国",
                "Phone": "(030) 30058460",
                "Fax": "(030)  33008924"
            }
        ],
        "Supplier": [{
            "SupplierID": 11,
            "CompanyName": "小当",
            "ContactName": "徐先生",
            "ContactTitle": "销售经理",
            "Address": "新华路 78 号",
            "City": "天津",
            "Region": "华北",
            "PostalCode": "307853",
            "Country": "中国",
            "Phone": "(020) 99845103"
        }]
    }}
```

请求地址直接向[http://\(server\):6060/print发送打印请求，即可](http://%28server%29:6060/print发送打印请求，即可)

#### 更改服务设置

停止服务，单击服务设置，在弹出的对话框中对端口、默认打印机、工作目录进行设置。

![](/assets/import16.png)

#### 模版设置

* 未勾选"使用本地模板",服务会根据提交的参数中加载url模板。

* 勾选了"使用本地模板"后服务会在服务安装录下的grf文件夹中查找，所以报表模板需要放在工作目录的grf文件夹中，通过主界面上的模板目录按钮可以快速打开grf文件夹。

#### 显示打印对话框

在主界面中勾选“显示打印对话框”后，每次提交数据打印都会先弹出打印对话框。

![](/assets/import17.png)

#### 预览或打印

在主界面中选择“打印”，提交数据后会直接进入打印，勾选预览，提交数据后会进入预览界面，如下图示。

![](/assets/import18.png)

