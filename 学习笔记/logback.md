## logback的日志级别

TRACE、DEBUG、INFO、WARN 和 ERROR

TRACE 很低的日志级别，一般不会使用。

DEBUG 指出细粒度信息事件对调试应用程序是非常有帮助的，主要用于开发过程中打印一些运行信息。

INFO 消息在粗粒度级别上突出强调应用程序的运行过程。打印一些你感兴趣的或者重要的信息，这个可以用于生产环境中输出程序运行的一些重要信息，但是不能滥用，避免打印过多的日志。

WARN 表明会出现潜在错误的情形，有些信息不是错误信息，但是也要给程序员的一些提示。

ERROR 指出虽然发生错误事件，但仍然不影响系统的继续运行。打印错误和异常信息，如果不想输出太多的日志，可以使用这个级别。





## 参考资料

[log4j的8个日志级别（OFF、FATAL、ERROR、WARN、INFO、DEBUG、TRACE、 ALL）](<https://blog.csdn.net/shiyong1949/article/details/52643711/>)