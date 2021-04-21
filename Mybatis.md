**Mybatis介绍**

Mybatis 是一个半 ORM（对象关系映射）框架，它内部封装了 JDBC，开发时

只需要关注 SQL 语句本身，不需要花费精力去处理加载驱动、创建连接、创建

statement 等繁杂的过程。

**Mybatis优点**

1、基于 SQL 语句编程，相当灵活，不会对应用程序或者数据库的现有设计造成任

何影响，SQL 写在 XML 里，解除 sql 与程序代码的耦合，便于统一管理；提供 XML

标签，支持编写动态 SQL 语句，并可重用。

2、与 JDBC 相比，减少了 50%以上的代码量，消除了 JDBC 大量冗余的代码，不

需要手动开关连接；

3、很好的与各种数据库兼容（因为 MyBatis 使用 JDBC 来连接数据库，所以只要

JDBC 支持的数据库 MyBatis 都支持）。

4、能够与 Spring 很好的集成；

5、提供映射标签，支持对象与数据库的 ORM 字段关系映射；提供对象关系映射

标签，支持对象关系组件维护。

**Mybatis缺点**

1、SQL 语句的编写工作量较大，尤其当字段多、关联表多时，对开发人员编写

SQL 语句的功底有一定要求。

2、SQL 语句依赖于数据库，导致数据库移植性差，不能随意更换数据库。

**Mybatis与Hibernate不同点**

1、Mybatis 和 hibernate 不同，它不完全是一个 ORM 框架，因为 MyBatis 需要

程序员自己编写 Sql 语句。

2、Mybatis 直接编写原生态 sql，可以严格控制 sql 执行性能，灵活度高，非常

适合对关系数据模型要求不高的软件开发，因为这类软件需求变化频繁，一但需

求变化要求迅速输出成果。但是灵活的前提是 mybatis 无法做到数据库无关性，

如果需要实现支持多种数据库的软件，则需要自定义多套 sql 映射文件，工作量大。 

3、Hibernate 对象/关系映射能力强，数据库无关性好，对于关系模型要求高的

软件，如果用 hibernate 开发可以节省很多代码，提高效率。

**#{}与${}的区别**

\#{}是预编译处理，${}是字符串替换。

Mybatis 在处理#{}时，会将 sql 中的#{}替换为?号，调用 PreparedStatement 的

set 方法来赋值；

Mybatis 在处理${}时，就是把${}替换成变量的值。

使用#{}可以有效的防止 SQL 注入，提高系统安全性。  

**Mybatis 是如何进行分页的？分页插件的原理是什么？**

Mybatis 使用 RowBounds 对象进行分页，它是针对 ResultSet 结果集执行的内

存分页，而非物理分页。可以在 sql 内直接书写带有物理分页的参数来完成物理分

页功能，也可以使用分页插件来完成物理分页。

分页插件的基本原理是使用 Mybatis 提供的插件接口，实现自定义插件，在插件

的拦截方法内拦截待执行的 sql，然后重写 sql，根据 dialect 方言，添加对应的物

理分页语句和物理分页参数

**Mybatis 动态 sql 有什么用？执行原理？有哪些动态 sql？**

Mybatis 动态 sql 可以在 Xml 映射文件内，以标签的形式编写动态 sql，执行原理

是根据表达式的值 完成逻辑判断并动态拼接 sql 的功能。

Mybatis 提供了 9 种动态 sql 标签：trim | where | set | foreach | if | choose

| when | otherwise | bind。

**Mybatis 的一级、二级缓存**

1、一级缓存: 基于 PerpetualCache 的 HashMap 本地缓存，其存储作用域为

Session，当 Session flush 或 close 之后，该 Session 中的所有 Cache 就

将清空，默认打开一级缓存。

2、二级缓存与一级缓存其机制相同，默认也是采用 PerpetualCache，HashMap

存储，不同在于其存储作用域为 Mapper(Namespace)，并且可自定义存储源，

如 Ehcache。默认不打开二级缓存，要开启二级缓存，使用二级缓存属性类需要

实现 Serializable 序列化接口(可用来保存对象的状态),可在它的映射文件中配置

<cache/> ； 

3、对于缓存数据更新机制，当某一个作用域(一级缓存 Session/二级缓存

Namespaces)的进行了 C/U/D 操作后，默认该作用域下所有 select 中的缓存将

被 clear。

