普罗格应用服务-PrologApplicationService

> ### 简介

普罗格应用服务提供了打印服务、称重服务功能。

* 打印服务是一个兼容多种打印方案的通用服务，支持B/S、C/S打印，支持客户端部署和集中部署。服务使用web api接口对外提供服务。打印服务是基于grid++report开发，所以报表模板和数据grid++report规范。
* 称重服务是通过串口与电子秤进行连接，读取到数据后以websocket server方式对外发布数据，因此与客户端通过websocket协议进行连接。

安装

快速使用

