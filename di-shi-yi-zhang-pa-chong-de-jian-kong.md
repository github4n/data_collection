# 第十四章 爬虫的监控

为了了解当前爬虫的运行效率，机器和系统负载，以及爬虫异常的原因，针对爬虫进行监控是很有必要的。在实际工作中运维和开发的时间差不多甚至更多一些。维护已经在工作的爬虫是一个繁重的工作。

随着工作时间增加，一般我们都会学着让写出来的爬虫更好维护一些。比如爬虫的日志系统，数据量的统计等。将爬虫工程师和运维分开也不太合理，因为如果一个爬虫不工作了，那原因可能是要抓的网页更新了结构，也有可能出现在系统上，也有可能是当初开发爬虫的时候没发现反扒策略，上线之后出问题了，也可能是对方网站发现了你是爬虫把你封杀了，所以一般来说爬虫开发也要兼顾运维。

所以爬虫的运维我可以提供下面几个思路：

首先，从数据增量监控。定向爬虫（指的是只针对一个网站的爬虫）比较容易，一段时间之后对一些网站的数据增量会有一个大体的了解。经常看看这些数据的增加趋势是否是正常就可以了（Grafana）。非定向爬虫的数据增量不是很稳定，一般看机器的网络状况，网站的更新情况等（只是，这方面我个人的经验还是比较欠缺的）。

其次，还要看爬虫执行的成功情况。在上面提到了用\(消息\)任务队列控制爬虫工作，这样解耦可以带来很多好处，其中一个就是可以就是可以对一次爬虫执行进行日志。可以在每次爬虫任务执行的时候，将执行的时间、状态、目标url、异常等放入一个日志系统（比如kibana），然后通过一个可视化的手段可以清晰地看到爬虫的失败率。所以在这里我们也会简单地讲一下 ELK Stack 日志监控系统的搭建。

最后，针对爬虫抛出的Exception。在许多公司之中都会用到错误日志收集（Sentry），这里需要注意的一点是，我们需要忽略正常的异常（比如Connection错误，锁冲突等），否则，会被这些错误淹没。

