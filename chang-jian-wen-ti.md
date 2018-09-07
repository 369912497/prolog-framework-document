问题描述

以debug方式启动项目时，程序都会在SilentExitExceptionHandler类中的throw new SilentExitException\(\)处终止

问题分析

解决方案

在eclips中，window -&gt; preferences -&gt; java -&gt; debug 取消“suspend execution on uncaught exceptions”选项即可

