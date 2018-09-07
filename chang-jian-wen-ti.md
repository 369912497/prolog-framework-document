> 问题描述

以debug方式启动项目时，程序都会在SilentExitExceptionHandler类中的throw new SilentExitException\(\)处终止

> 问题分析

spring-boot-devtools工具包中有一个未捕获的异常

> 解决方案

在eclips中，window -&gt; preferences -&gt; java -&gt; debug 取消“suspend execution on uncaught exceptions”选项即可

![](/assets/impo12112.png)

