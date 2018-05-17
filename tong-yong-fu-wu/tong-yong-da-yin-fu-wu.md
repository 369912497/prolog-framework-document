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
          }
});

//reportJsonData数据格式
｛
grf:'grfName',//模板名称
data:reportData
｝
```



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
            },
            {
                "CustomerID": "CHOPS",
                "CompanyName": "浩天旅行社",
                "ContactName": "方先生",
                "ContactTitle": "物主",
                "Address": "白广路 314 号",
                "City": "天津",
                "Region": "华北",
                "PostalCode": "234254",
                "Country": "中国",
                "Phone": "(030) 30076545"
            },
            {
                "CustomerID": "COMMI",
                "CompanyName": "同恒",
                "ContactName": "刘先生",
                "ContactTitle": "销售员",
                "Address": "七一路 37 号",
                "City": "天津",
                "Region": "华北",
                "PostalCode": "453466",
                "Country": "中国",
                "Phone": "(030) 35557647"
            },
            {
                "CustomerID": "EASTC",
                "CompanyName": "中通",
                "ContactName": "林小姐",
                "ContactTitle": "销售代理",
                "Address": "光复北路 895 号",
                "City": "天津",
                "Region": "华北",
                "PostalCode": "809784",
                "Country": "中国",
                "Phone": "(030) 35550297",
                "Fax": "(030) 35553373"
            },
            {
                "CustomerID": "FISSA",
                "CompanyName": "嘉元实业",
                "ContactName": "刘小姐",
                "ContactTitle": "结算经理",
                "Address": "东湖大街 28 号",
                "City": "天津",
                "Region": "华北",
                "PostalCode": "458965",
                "Country": "中国",
                "Phone": "(091) 25559444",
                "Fax": "(091) 25555593"
            },
            {
                "CustomerID": "GROSR",
                "CompanyName": "光远商贸",
                "ContactName": "陈先生",
                "ContactTitle": "物主",
                "Address": "成川东街 951 号",
                "City": "天津",
                "Region": "华北",
                "PostalCode": "122096",
                "Country": "中国",
                "Phone": "(030) 32832951",
                "Fax": "(030) 32833397"
            },
            {
                "CustomerID": "HUNGO",
                "CompanyName": "师大贸易",
                "ContactName": "苏先生",
                "ContactTitle": "销售员",
                "Address": "黄岗北路 73 号",
                "City": "天津",
                "Region": "华北",
                "PostalCode": "683045",
                "Country": "中国",
                "Phone": "(030) 29672542",
                "Fax": "(030) 29673333"
            },
            {
                "CustomerID": "LAMAI",
                "CompanyName": "池春建设",
                "ContactName": "王先生",
                "ContactTitle": "销售经理",
                "Address": "青年南街 291 号",
                "City": "天津",
                "Region": "华北",
                "PostalCode": "502564",
                "Country": "中国",
                "Phone": "(030) 61776110",
                "Fax": "(030) 61776111"
            },
            {
                "CustomerID": "LAUGB",
                "CompanyName": "和福建设",
                "ContactName": "刘先生",
                "ContactTitle": "市场助理",
                "Address": "创业西路 238 号",
                "City": "天津",
                "Region": "华北",
                "PostalCode": "055654",
                "Country": "中国",
                "Phone": "(030) 15553392",
                "Fax": "(030) 15557293"
            },
            {
                "CustomerID": "LILAS",
                "CompanyName": "富泰人寿",
                "ContactName": "陈先生",
                "ContactTitle": "结算经理",
                "Address": "光伦东路 381 号",
                "City": "天津",
                "Region": "华北",
                "PostalCode": "995085",
                "Country": "中国",
                "Phone": "(030) 33116954",
                "Fax": "(030) 33117256"
            },
            {
                "CustomerID": "LONEP",
                "CompanyName": "正太实业",
                "ContactName": "林慧音",
                "ContactTitle": "销售经理",
                "Address": "花园西街 28 号",
                "City": "天津",
                "Region": "华北",
                "PostalCode": "440875",
                "Country": "中国",
                "Phone": "(030) 25559573",
                "Fax": "(030) 25559646"
            },
            {
                "CustomerID": "MORGK",
                "CompanyName": "仲堂企业",
                "ContactName": "徐文彬",
                "ContactTitle": "市场助理",
                "Address": "创业街 57 号",
                "City": "天津",
                "Region": "华北",
                "PostalCode": "440007",
                "Country": "中国",
                "Phone": "(030) 34202376"
            },
            {
                "CustomerID": "PERIC",
                "CompanyName": "就业广兑",
                "ContactName": "唐小姐",
                "ContactTitle": "销售代表",
                "Address": "淮水路 348 号",
                "City": "天津",
                "Region": "华北",
                "PostalCode": "786785",
                "Country": "中国",
                "Phone": "(030) 55223745",
                "Fax": "(030) 55453745"
            },
            {
                "CustomerID": "QUICK",
                "CompanyName": "高上补习班",
                "ContactName": "徐先生",
                "ContactTitle": "结算经理",
                "Address": "广场路 205 号",
                "City": "天津",
                "Region": "华北",
                "PostalCode": "787869",
                "Country": "中国",
                "Phone": "(030) 72035188"
            },
            {
                "CustomerID": "REGGC",
                "CompanyName": "建国科技",
                "ContactName": "陈先生",
                "ContactTitle": "销售员",
                "Address": "肥水路 93 号",
                "City": "天津",
                "Region": "华北",
                "PostalCode": "345256",
                "Country": "中国",
                "Phone": "(030) 52256721",
                "Fax": "(030) 52256722"
            },
            {
                "CustomerID": "RICAR",
                "CompanyName": "宇欣实业",
                "ContactName": "黄雅玲",
                "ContactTitle": "助理销售代理",
                "Address": "大峪口街 702 号",
                "City": "天津",
                "Region": "华北",
                "PostalCode": "101046",
                "Country": "中国",
                "Phone": "(030) 45553412"
            },
            {
                "CustomerID": "ROMEY",
                "CompanyName": "德化食品",
                "ContactName": "王先生",
                "ContactTitle": "结算经理",
                "Address": "劝业路 103 号",
                "City": "天津",
                "Region": "华北",
                "PostalCode": "871108",
                "Country": "中国",
                "Phone": "(030) 74546200",
                "Fax": "(030) 77456210"
            },
            {
                "CustomerID": "SEVES",
                "CompanyName": "艾德高科技",
                "ContactName": "谢小姐",
                "ContactTitle": "销售经理",
                "Address": "起义路 231 号",
                "City": "天津",
                "Region": "华北",
                "PostalCode": "013072",
                "Country": "中国",
                "Phone": "(030) 55657717",
                "Fax": "(030) 55655646"
            },
            {
                "CustomerID": "SIMOB",
                "CompanyName": "百达电子",
                "ContactName": "徐文彬",
                "ContactTitle": "物主",
                "Address": "黄口江路 521 号",
                "City": "天津",
                "Region": "华北",
                "PostalCode": "972077",
                "Country": "中国",
                "Phone": "(030) 31123456",
                "Fax": "(030) 31133557"
            },
            {
                "CustomerID": "SUPRD",
                "CompanyName": "福星制衣厂股份有限公司",
                "ContactName": "徐先生",
                "ContactTitle": "结算经理",
                "Address": "机场东路 951 号",
                "City": "天津",
                "Region": "华北",
                "PostalCode": "050337",
                "Country": "中国",
                "Phone": "(030) 23672220",
                "Fax": "(030) 23672221"
            },
            {
                "CustomerID": "TORTU",
                "CompanyName": "协昌妮绒有限公司",
                "ContactName": "王先生",
                "ContactTitle": "物主",
                "Address": "长春路 371 号",
                "City": "天津",
                "Region": "华北",
                "PostalCode": "507392",
                "Country": "中国",
                "Phone": "(030) 45552933"
            },
            {
                "CustomerID": "VINET",
                "CompanyName": "山泰企业",
                "ContactName": "黎先生",
                "ContactTitle": "结算经理",
                "Address": "舜井街 561 号",
                "City": "天津",
                "Region": "华北",
                "PostalCode": "575909",
                "Country": "中国",
                "Phone": "(030) 26471510",
                "Fax": "(030) 26471511"
            },
            {
                "CustomerID": "WANDK",
                "CompanyName": "凯旋科技",
                "ContactName": "方先生",
                "ContactTitle": "销售代表",
                "Address": "使馆路 371 号",
                "City": "天津",
                "Region": "华北",
                "PostalCode": "212400",
                "Country": "中国",
                "Phone": "(030) 71100361",
                "Fax": "(030) 07115428"
            },
            {
                "CustomerID": "WOLZA",
                "CompanyName": "汉典电机",
                "ContactName": "刘先生",
                "ContactTitle": "物主",
                "Address": "潼关路 41 号",
                "City": "天津",
                "Region": "华北",
                "PostalCode": "421008",
                "Country": "中国",
                "Phone": "(030) 56427012",
                "Fax": "(030) 56427012"
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

服务会在工作目录下的grf文件夹中查找，所以报表模板需要放在工作目录的grf文件夹中，通过主界面上的模板目录按钮可以快速打开grf文件夹。

#### 显示打印对话框

在主界面中勾选“显示打印对话框”后，每次提交数据打印都会先弹出打印对话框。

![](/assets/import17.png)

#### 预览或打印

在主界面中选择“打印”，提交数据后会直接进入打印，勾选预览，提交数据后会进入预览界面，如下图示。

![](/assets/import18.png)

