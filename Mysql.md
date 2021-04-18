1、亿级流量怎么优化Mysql数据库性能？

**分库分表**

原理：主表master进行数据库操作(update、insert、delete)的时候生成一个binlog日志文件，从表salver里会开启2个线程，一个是IO线程，负责把主库master生成的binlog日志文件拿到从库salver，另一个线程SQL线程负责执行binlog文件里面的sql语句。这样就保证每次操作主库，数据会及时更新到从库。

2、怎么保证分库分表中update、insert、delete的操作在主库执行，select在从库执行？

**方案一：proxy代理层分片，主要有mycat等**

**方案二：jdbc应用层分片，主要当当网sharding-jdbc实现**

>分库分表中间件简单易用
>
>* 当当网sharing-jdbc
>
>* 蘑菇街TSharding
>
>重量级
>
>- TDDL Smart Client的方式（淘宝）
>- Atlas(Qihoo 360)
>- alibaba.cobar(是阿里巴巴（B2B）部门开发)
>- MyCAT（基于阿里开源的Cobar产品而研发）
>- Oceanus(58同城数据库中间件)
>- OneProxy(支付宝首席架构师楼方鑫开发)
>- vitess（谷歌开发的数据库中间件）

**方案一proxy缺点性能比较低（需要连接proxy库），而且有强制路由弊端，优点是跨平台。**

**强制路由弊端**

原理：网络异步延迟阻塞原因导致从库salver可能还没有及时拿到主库的binlog文件进行同步，此时就要在从库读取刚才插入主库的数据，从库没有此条数据的问题。如下：

```
t表msg字段值 master库为“更新主库信息”，proxy、salver库为“还没同步”，即从库没同步最新的主库binlog数据
三个mysql连接，master-sql、proxy-sql、salver-sql
一定要在proxy-sql数据库执行以下语句
select t.msg from t            返回结果： 还没同步
/*master*/select t.msg from t  返回结果： 更新主库信息
```

**什么是Mysql回表?**

简单来说就是数据库根据索引（非主键）找到了指定的记录所在行后，还需要根据主键再次到数据块里获取数据。

“回表”一般就是指执行计划里显示的“TABLE ACCESS BY INDEX ROWID”。
再例如，虽然只查询索引里的列，但是需要回表过滤掉其他行。

**怎么预防回表操作？**

将被查询的字段，建立到联合索引里去。

