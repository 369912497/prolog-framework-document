## 通用打印服务 - PlgPrintServer {#chenyc}

> ### 简介

通用打印服务是一个兼容多种打印方案的通用服务，支持B/S、C/S打印，支持客户端部署和集中部署。服务使用web api接口对外提供服务。

打印服务是基于grid++report开发，所以打印规范遵循grid++report规范。

> ### 快速使用

#### 安装

安装好打印服务程序，启动服务，可在系统托盘看到服务程序图标，如下图示：

![](/assets/import11.png)

#### 运行

双击图标或右键选择显示主界面，在主界面中启动服务，默认已启动，默认端口6060

![](/assets/import29.png)

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

* 当数据类型选择"URL"时：

```json
 {"url": "http://www.gridreport.cn/demos/grf/4d.grf",
    "printName":"Microsoft XPS Document Writer",
    "data":"http://www.gridreport.cn/demos/data/DataCenter.ashx?data=SubReport_4d&city=%E5%A4%A9%E6%B4%A5"
 }
```

* 当数据类型选择"DATA"时：

```json
 //当数据格式为"JSON"

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



```json

    //当数据格式为"XML
    {"url": "http://www.gridreport.cn/demos/grf/4d.grf",
    "printName":"Microsoft XPS Document Writer",
    "data":"<data><City>武汉</City><Customer><CustomerID>ALFKI</CustomerID><CompanyName>三川实业有限公司</CompanyName><ContactName>刘小姐</ContactName><ContactTitle>销售代表</ContactTitle><Address>大崇明路 50 号</Address><City>天津</City><Region>华北</Region><PostalCode>343567</PostalCode><Country>中国</Country><Phone>(030) 30074321</Phone><Fax>(030) 30765452</Fax></Customer><Customer><CustomerID>ANATR</CustomerID><CompanyName>东南实业</CompanyName><ContactName>王先生</ContactName><ContactTitle>物主</ContactTitle><Address>承德西路 80 号</Address><City>天津</City><Region>华北</Region><PostalCode>234575</PostalCode><Country>中国</Country><Phone>(030) 35554729</Phone><Fax>(030) 35553744</Fax></Customer><Customer><CustomerID>BLAUS</CustomerID><CompanyName>森通</CompanyName><ContactName>王先生</ContactName><ContactTitle>销售代表</ContactTitle><Address>常保阁东 80 号</Address><City>天津</City><Region>华北</Region><PostalCode>787045</PostalCode><Country>中国</Country><Phone>(030) 30058460</Phone><Fax>(030)  33008924</Fax></Customer><Customer><CustomerID>CHOPS</CustomerID><CompanyName>浩天旅行社</CompanyName><ContactName>方先生</ContactName><ContactTitle>物主</ContactTitle><Address>白广路 314 号</Address><City>天津</City><Region>华北</Region><PostalCode>234254</PostalCode><Country>中国</Country><Phone>(030) 30076545</Phone></Customer><Customer><CustomerID>COMMI</CustomerID><CompanyName>同恒</CompanyName><ContactName>刘先生</ContactName><ContactTitle>销售员</ContactTitle><Address>七一路 37 号</Address><City>天津</City><Region>华北</Region><PostalCode>453466</PostalCode><Country>中国</Country><Phone>(030) 35557647</Phone></Customer><Customer><CustomerID>EASTC</CustomerID><CompanyName>中通</CompanyName><ContactName>林小姐</ContactName><ContactTitle>销售代理</ContactTitle><Address>光复北路 895 号</Address><City>天津</City><Region>华北</Region><PostalCode>809784</PostalCode><Country>中国</Country><Phone>(030) 35550297</Phone><Fax>(030) 35553373</Fax></Customer><Customer><CustomerID>FISSA</CustomerID><CompanyName>嘉元实业</CompanyName><ContactName>刘小姐</ContactName><ContactTitle>结算经理</ContactTitle><Address>东湖大街 28 号</Address><City>天津</City><Region>华北</Region><PostalCode>458965</PostalCode><Country>中国</Country><Phone>(091) 25559444</Phone><Fax>(091) 25555593</Fax></Customer><Customer><CustomerID>GROSR</CustomerID><CompanyName>光远商贸</CompanyName><ContactName>陈先生</ContactName><ContactTitle>物主</ContactTitle><Address>成川东街 951 号</Address><City>天津</City><Region>华北</Region><PostalCode>122096</PostalCode><Country>中国</Country><Phone>(030) 32832951</Phone><Fax>(030) 32833397</Fax></Customer><Customer><CustomerID>HUNGO</CustomerID><CompanyName>师大贸易</CompanyName><ContactName>苏先生</ContactName><ContactTitle>销售员</ContactTitle><Address>黄岗北路 73 号</Address><City>天津</City><Region>华北</Region><PostalCode>683045</PostalCode><Country>中国</Country><Phone>(030) 29672542</Phone><Fax>(030) 29673333</Fax></Customer><Customer><CustomerID>LAMAI</CustomerID><CompanyName>池春建设</CompanyName><ContactName>王先生</ContactName><ContactTitle>销售经理</ContactTitle><Address>青年南街 291 号</Address><City>天津</City><Region>华北</Region><PostalCode>502564</PostalCode><Country>中国</Country><Phone>(030) 61776110</Phone><Fax>(030) 61776111</Fax></Customer><Customer><CustomerID>LAUGB</CustomerID><CompanyName>和福建设</CompanyName><ContactName>刘先生</ContactName><ContactTitle>市场助理</ContactTitle><Address>创业西路 238 号</Address><City>天津</City><Region>华北</Region><PostalCode>055654</PostalCode><Country>中国</Country><Phone>(030) 15553392</Phone><Fax>(030) 15557293</Fax></Customer><Customer><CustomerID>LILAS</CustomerID><CompanyName>富泰人寿</CompanyName><ContactName>陈先生</ContactName><ContactTitle>结算经理</ContactTitle><Address>光伦东路 381 号</Address><City>天津</City><Region>华北</Region><PostalCode>995085</PostalCode><Country>中国</Country><Phone>(030) 33116954</Phone><Fax>(030) 33117256</Fax></Customer><Customer><CustomerID>LONEP</CustomerID><CompanyName>正太实业</CompanyName><ContactName>林慧音</ContactName><ContactTitle>销售经理</ContactTitle><Address>花园西街 28 号</Address><City>天津</City><Region>华北</Region><PostalCode>440875</PostalCode><Country>中国</Country><Phone>(030) 25559573</Phone><Fax>(030) 25559646</Fax></Customer><Customer><CustomerID>MORGK</CustomerID><CompanyName>仲堂企业</CompanyName><ContactName>徐文彬</ContactName><ContactTitle>市场助理</ContactTitle><Address>创业街 57 号</Address><City>天津</City><Region>华北</Region><PostalCode>440007</PostalCode><Country>中国</Country><Phone>(030) 34202376</Phone></Customer><Customer><CustomerID>PERIC</CustomerID><CompanyName>就业广兑</CompanyName><ContactName>唐小姐</ContactName><ContactTitle>销售代表</ContactTitle><Address>淮水路 348 号</Address><City>天津</City><Region>华北</Region><PostalCode>786785</PostalCode><Country>中国</Country><Phone>(030) 55223745</Phone><Fax>(030) 55453745</Fax></Customer><Customer><CustomerID>QUICK</CustomerID><CompanyName>高上补习班</CompanyName><ContactName>徐先生</ContactName><ContactTitle>结算经理</ContactTitle><Address>广场路 205 号</Address><City>天津</City><Region>华北</Region><PostalCode>787869</PostalCode><Country>中国</Country><Phone>(030) 72035188</Phone></Customer><Customer><CustomerID>REGGC</CustomerID><CompanyName>建国科技</CompanyName><ContactName>陈先生</ContactName><ContactTitle>销售员</ContactTitle><Address>肥水路 93 号</Address><City>天津</City><Region>华北</Region><PostalCode>345256</PostalCode><Country>中国</Country><Phone>(030) 52256721</Phone><Fax>(030) 52256722</Fax></Customer><Customer><CustomerID>RICAR</CustomerID><CompanyName>宇欣实业</CompanyName><ContactName>黄雅玲</ContactName><ContactTitle>助理销售代理</ContactTitle><Address>大峪口街 702 号</Address><City>天津</City><Region>华北</Region><PostalCode>101046</PostalCode><Country>中国</Country><Phone>(030) 45553412</Phone></Customer><Customer><CustomerID>ROMEY</CustomerID><CompanyName>德化食品</CompanyName><ContactName>王先生</ContactName><ContactTitle>结算经理</ContactTitle><Address>劝业路 103 号</Address><City>天津</City><Region>华北</Region><PostalCode>871108</PostalCode><Country>中国</Country><Phone>(030) 74546200</Phone><Fax>(030) 77456210</Fax></Customer><Customer><CustomerID>SEVES</CustomerID><CompanyName>艾德高科技</CompanyName><ContactName>谢小姐</ContactName><ContactTitle>销售经理</ContactTitle><Address>起义路 231 号</Address><City>天津</City><Region>华北</Region><PostalCode>013072</PostalCode><Country>中国</Country><Phone>(030) 55657717</Phone><Fax>(030) 55655646</Fax></Customer><Customer><CustomerID>SIMOB</CustomerID><CompanyName>百达电子</CompanyName><ContactName>徐文彬</ContactName><ContactTitle>物主</ContactTitle><Address>黄口江路 521 号</Address><City>天津</City><Region>华北</Region><PostalCode>972077</PostalCode><Country>中国</Country><Phone>(030) 31123456</Phone><Fax>(030) 31133557</Fax></Customer><Customer><CustomerID>SUPRD</CustomerID><CompanyName>福星制衣厂股份有限公司</CompanyName><ContactName>徐先生</ContactName><ContactTitle>结算经理</ContactTitle><Address>机场东路 951 号</Address><City>天津</City><Region>华北</Region><PostalCode>050337</PostalCode><Country>中国</Country><Phone>(030) 23672220</Phone><Fax>(030) 23672221</Fax></Customer><Customer><CustomerID>TORTU</CustomerID><CompanyName>协昌妮绒有限公司</CompanyName><ContactName>王先生</ContactName><ContactTitle>物主</ContactTitle><Address>长春路 371 号</Address><City>天津</City><Region>华北</Region><PostalCode>507392</PostalCode><Country>中国</Country><Phone>(030) 45552933</Phone></Customer><Customer><CustomerID>VINET</CustomerID><CompanyName>山泰企业</CompanyName><ContactName>黎先生</ContactName><ContactTitle>结算经理</ContactTitle><Address>舜井街 561 号</Address><City>天津</City><Region>华北</Region><PostalCode>575909</PostalCode><Country>中国</Country><Phone>(030) 26471510</Phone><Fax>(030) 26471511</Fax></Customer><Customer><CustomerID>WANDK</CustomerID><CompanyName>凯旋科技</CompanyName><ContactName>方先生</ContactName><ContactTitle>销售代表</ContactTitle><Address>使馆路 371 号</Address><City>天津</City><Region>华北</Region><PostalCode>212400</PostalCode><Country>中国</Country><Phone>(030) 71100361</Phone><Fax>(030) 07115428</Fax></Customer><Customer><CustomerID>WOLZA</CustomerID><CompanyName>汉典电机</CompanyName><ContactName>刘先生</ContactName><ContactTitle>物主</ContactTitle><Address>潼关路 41 号</Address><City>天津</City><Region>华北</Region><PostalCode>421008</PostalCode><Country>中国</Country><Phone>(030) 56427012</Phone><Fax>(030) 56427012</Fax></Customer><Supplier><SupplierID>11</SupplierID><CompanyName>小当</CompanyName><ContactName>徐先生</ContactName><ContactTitle>销售经理</ContactTitle><Address>新华路 78 号</Address><City>天津</City><Region>华北</Region><PostalCode>307853</PostalCode><Country>中国</Country><Phone>(020) 99845103</Phone></Supplier></data>"
    }}



```

请求地址直接向[http://\(server\):6060/print发送打印请求，即可](http://%28server%29:6060/print发送打印请求，即可)

#### 更改服务设置

停止服务，单击服务设置，在弹出的对话框中对端口、默认打印机、工作目录进行设置。

![](/assets/import16.png)

#### 打印机选择

* 未勾选"锁定打印机",服务会根据提交的参数中选择打印机，若打印机不存在则使用配置的默认打印机。

* 勾选了"锁定打印机"后服务会对所有请求都使用本地设置的默认打印机。

#### 模版设置

* 未勾选"使用本地模板",服务会根据提交的参数中加载url模板。

* 勾选了"使用本地模板"后服务会在服务安装录下的grf文件夹中查找，所以报表模板需要放在工作目录的grf文件夹中，通过主界面上的模板目录按钮可以快速打开grf文件夹。

#### 显示打印对话框

在主界面中勾选“显示打印对话框”后，每次提交数据打印都会先弹出打印对话框。

![](/assets/import17.png)

#### 预览或打印

在主界面中选择“打印”，提交数据后会直接进入打印，勾选预览，提交数据后会进入预览界面，如下图示。

![](/assets/import18.png)

