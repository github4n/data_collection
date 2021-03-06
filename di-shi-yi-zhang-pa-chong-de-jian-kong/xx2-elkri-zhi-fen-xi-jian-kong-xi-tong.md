## 14.2 ELK 日志分析监控系统

当我们的业务或者项目规模越来越庞大以后,传统的服务器日志管理模式，会显得十分繁琐，低效,那么进行日志集中管理便显得十分必要。例如：使用开源的syslog，将所有服务器上的日志收集汇总。

但集中化管理日志后，日志的统计和检索又成为一件比较麻烦的事情，一般我们使用 grep、awk 和 wc 等 Linux 命令能实现检索和统计，但是对于要求更高的查询、排序和统计等要求和庞大的机器数量依然使用这样的方法难免有点力不从心。

此时，开源实时日志分析ELK平台能够完美的解决我们上述的问题，ELK 由ElasticSearch、Logstash 和 Kiabana 三个开源工具组成。这三个工具各司其职，最终形成一整套的监控架构。

***Elasticsearch***

ElasticSearch 是一个基于 Lucene 的搜索服务器。它提供了一个分布式多用户能力的全文搜索引擎，基于 RESTful web 接口。Elasticsearch 是用 Java 开发的，并作为 Apache 许可条款下的开放源码发布，是当前流行的企业级搜索引擎。设计用于云计算中，能够达到实时搜索，稳定，可靠，快速，安装使用方便。
我们使用 Elasticsearch 来完成日志的检索、分析工作。

![](/assets/es界面1.jpg)

***Logstash***

Logstash 是一个用于管理日志和事件的工具，你可以用它去收集日志、转换日志、解析日志并将他们作为数据提供给其它模块调用，例如搜索、存储等。
我们使用 Logstash 来完成日志的解析、存储工作。

***Kibana***

Kibana 是一个优秀的前端日志展示框架，它可以非常详细的将日志转化为各种图表，为用户提供强大的数据可视化支持。
我们使用 Kibana 来进行日志数据的展示工作。

以上三个框架，就构成了我们这套架构的核心。