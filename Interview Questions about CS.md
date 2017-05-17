# Interview Questions about CS

## Database

MySQL 为关系型数据库(Relational Database Management System), 这种所谓的"关系型"可以理解为"表格"的概念, 一个关系型数据库由一个或数个表格组成.

Q & A:

```
什么是存储过程？有哪些优缺点？

存储过程是一些预编译的SQL语句。
更加直白的理解：存储过程可以说是一个记录集，它是由一些T-SQL语句组成的代码块，
这些T-SQL语句代码像一个方法一样实现一些功能（对单表或多表的增删改查），
然后再给这个代码块取一个名字，在用到这个功能的时候调用他就行了。
存储过程是一个预编译的代码块，执行效率比较高
一个存储过程替代大量T_SQL语句 ，可以降低网络通信量，提高通信速率
可以一定程度上确保数据安全
```

###索引
**索引**是什么？有什么作用以及优缺点？

索引是对数据库表中一或多个列的值进行排序的结构，是帮助MySQL高效获取数据的数据结构

你也可以这样理解：索引就是加快检索表中数据的方法。数据库的索引类似于书籍的索引。
在书籍中，索引允许用户不必翻阅完整个书就能迅速地找到所需要的信息。
在数据库中，索引也允许数据库程序迅速地找到表中的数据，而不必扫描整个数据库。

MySQL数据库几个基本的索引类型：**普通索引、唯一索引、主键索引、全文索引**

索引加快数据库的检索速度
索引降低了插入、删除、修改等维护任务的速度
唯一索引可以确保每一行数据的唯一性
通过使用索引，可以在查询的过程中使用优化隐藏器，提高系统的性能
索引需要占物理和数据空间
http://kb.cnblogs.com/page/45712/

一条索引记录中包含的**基本信息**包括：
键值（即你定义索引时指定的所有字段的值）+逻辑指针（指向数据页或者另一索引页）。

通常状况下，由于索引记录仅包含索引字段值（以及4-9字节的指针），索引实体比真实的数据行要小许多，
索引页相较数据页来说要密集许多。
一个索引页可以存储数量更多的索引记录，这意味着在索引中查找时在I/O上占很大的优势，
理解这一点有助于从本质上了解使用索引的优势。

**索引类型**：  
A）聚集索引，表数据按照索引的顺序来存储的。对于聚集索引，叶子结点即存储了真实的数据行，不再有另外单独的数据页。  
B）非聚集索引，表数据存储顺序与索引顺序无关。对于非聚集索引，叶结点包含索引字段值及指向数据页数据行的逻辑指针，该层紧邻数据页，其行数量与数据表行数据量一致。 在一张表上只能创建一个聚集索引，因为真实数据的物理顺序只可能是一种。如果一张表没有聚集索引，那么它被称为“堆集”（Heap）。这样的表中的数据行没有特定的顺序，
所有的新行将被添加的表的末尾位置。 

我们常见的数据库系统，其索引使用的数据结构多是B-Tree或者B+Tree。
例如，MsSql使用的是B+Tree，Oracle及Sysbase使用的是B-Tree。

B-Tree不同于Binary Tree（二叉树，最多有两个子树），一棵M阶的B-Tree满足以下条件：
1）每个结点至多有M个孩子；  
2）除根结点和叶结点外，其它每个结点至少有M/2个孩子；  
3）根结点至少有两个孩子（除非该树仅包含一个结点）；  
4）所有叶结点在同一层，叶结点不包含任何关键字信息；  
5）有K个关键字的非叶结点恰好包含K+1个孩子；  

对于一个结点，其内部的关键字是从小到大排序的。
查找流程： 使用顺序查找（数组长度较短时）或折半查找方法查找Key[]数组，若找到关键字K，则返回该结点的地址及K在Key[]中的位置；否则，可确定K在某个Key[i]和Key[i+1]之间，则从Son[i]所指的子结点继续查找，直到在某结点中查找成功；或直至找到叶结点且叶结点中的查找仍不成功时，查找过程失败。

###事务

事务（Transaction）是并发控制的基本单位。所谓的事务，它是一个操作序列，这些操作**要么都执行，要么都不执行**，它是一个不可分割的工作单位。事务是数据库**维护数据一致性**的单位，在每个事务结束时，都能保持数据一致性。事务的提出主要是为了解决并发情况下保持数据一致性的问题。

#### 事务的基本特性：

- Atomic（原子性）：事务中包含的操作被看做一个逻辑单元，这个逻辑单元中的操作要么全部成功，要么全部失败。
- Consistency（一致性）：只有合法的数据可以被写入数据库，否则事务应该将其回滚到最初状态。
- Isolation（隔离性）：事务允许多个用户对同一个数据进行并发访问，而不破坏数据的正确性和完整性。同时，并行事务的修改必须与其他并行事务的修改相互独立。
- Durability（持久性）：事务结束后，事务处理的结果必须能够得到固化。

#### 事务的四个属性

- 原子性(Atomicity)：事务中的所有元素作为一个整体提交或回滚，事务的个元素是不可分的，事务是一个完整操作。
- 一致性(Consistemcy)：事物完成时，数据必须是一致的，也就是说，和事物开始之前，数据存储中的数据处于一致状态。保证数据的无损。
- 隔离性(Isolation)：对数据进行修改的多个事务是彼此隔离的。这表明事务必须是独立的，不应该以任何方式以来于或影响其他事务。
- 持久性(Durability)：事务完成之后，它对于系统的影响是永久的，该修改即使出现系统故障也将一直保留，真实的修改了数据库

### 乐观锁和悲观锁
http://www.open-open.com/lib/view/open1452046967245.html   

数据库管理系统（DBMS）中的**并发控制**的任务是确保在多个事务同时存取数据库中同一数据时不破坏事务的隔离性和统一性以及数据库的统一性。

乐观并发控制(乐观锁)和悲观并发控制（悲观锁）是并发控制主要采用的技术手段。

悲观锁：假定会发生并发冲突，屏蔽一切可能违反数据完整性的操作。  
乐观锁：假设不会发生并发冲突，只在提交操作时检查是否违反数据完整性。

#### 悲观锁

在关系数据库管理系统里，悲观并发控制（又名“悲观锁”，Pessimistic Concurrency Control，缩写“PCC”）是一种并发控制的方法。它可以阻止一个事务以影响其他用户的方式来修改数据。如果一个事务执行的操作都某行数据应用了锁，那只有当这个事务把锁释放，其他事务才能够执行与该锁冲突的操作。悲观并发控制主要用于数据争用激烈的环境，以及发生并发冲突时使用锁保护数据的成本要低于回滚事务的成本的环境中。

悲观锁，正如其名，它指的是对数据被外界（包括本系统当前的其他事务，以及来自外部系统的事务处理）修改持保守态度(悲观)，因此，在整个数据处理过程中，将数据处于锁定状态。 悲观锁的实现，往往**依靠数据库提供的锁机制** （也只有数据库层提供的锁机制才能真正保证数据访问的排他性，否则，即使在本系统中实现了加锁机制，也无法保证外部系统不会修改数据）

##### 悲观锁流程： 

在对任意记录进行修改前，先尝试为该记录加上**排他锁**（exclusive locking）。  
如果加锁失败，说明该记录正在被修改，那么当前查询可能要等待或者抛出异常。 具体响应方式由开发者根据实际需要决定。  
如果成功加锁，那么就可以对记录做修改，事务完成后就会解锁了。  
其间如果有其他对该记录做修改或加排他锁的操作，都会等待我们解锁或直接抛出异常。

```sql
//0.开始事务
begin;/begin work;/start transaction; (三者选一就可以)
//1.查询出商品信息
select status from t_goods where id=1 for update;
//2.根据商品信息生成订单
insert into t_orders (id,goods_id) values (null,1);
//3.修改商品status为2
update t_goods set status=2;
//4.提交事务
commit;/commit work;
```
上面的查询语句中，使用了 select…for update 的方式，这样就通过开启排他锁的方式实现了悲观锁。此时在t_goods表中，id为1的 那条数据就被我们锁定了，其它的事务必须等本次事务提交之后才能执行。这样我们可以保证当前的数据不会被其它事务修改。

上面我们提到，使用 select…for update 会把数据给锁住，不过我们需要注意一些锁的级别，MySQL InnoDB默认行级锁。行级锁都是基于索引的，如果一条SQL语句用不到索引是不会使用行级锁的，会使用表级锁把整张表锁住，这点需要注意。

##### 悲观锁优点与不足 

悲观并发控制实际上是“先取锁再访问”的保守策略，为数据处理的安全提供了保证。但是在效率方面，处理加锁的机制会让数据库产生额外的开销，还有增加产生死锁的机会；另外，在只读型事务处理中由于不会产生冲突，也没必要使用锁，这样做只能增加系统负载；还有会降低了并行性，一个事务如果锁定了某行数据，其他事务就必须等待该事务处理完才可以处理那行数

#### **乐观锁**

在关系数据库管理系统里，乐观并发控制（又名“乐观锁”，Optimistic Concurrency Control，缩写“OCC”）是一种并发控制的方法。它**假设多用户并发的事务在处理时不会彼此互相影响**，各事务能够在不产生锁的情况下处理各自影响的那部分数据。在提交数据更新之前，每个事务会先检查在该事务读取数据后，有没有其他事务又修改了该数据。如果其他事务有更新的话，正在提交的事务会进行回滚。乐观事务控制最早是由孔祥重（H.T.Kung）教授提出。

乐观锁（ Optimistic Locking ） 相对悲观锁而言，乐观锁假设认为**数据一般情况下不会造成冲突**，所以在数据进行提交更新的时候，才会正式对数据的冲突与否进行检测，如果发现冲突了，则让返回用户错误的信息，让用户决定如何去做。**乐观锁并不会使用数据库提供的锁机制**。一般的实现乐观锁的方式就是**记录数据版本**。

##### 数据版本

为数据增加的一个版本标识。当读取数据时，将版本标识的值一同读出，数据每更新一次，同时对版本标识进行更新。当我们提交更新的时候，判断数据库表对应记录的当前版本信息与第一次取出来的版本标识进行比对，如果数据库表当前版本号与第一次取出来的版本标识值相等，则予以更新，否则认为是过期数据。

实现数据版本有两种方式，第一种是使用**版本号**，第二种是使用**时间戳**。

##### 乐观所优点与不足 

乐观并发控制相信事务之间的**数据竞争**(data race)的概率是比较小的，因此尽可能直接做下去，直到提交的时候才去锁定，所以不会产生任何锁和死锁。但如果直接简单这么做，还是有可能会遇到不可预期的结果，例如两个事务都读取了数据库的某一行，经过修改以后写回数据库，这时就遇到了问题。

### 使用索引查询一定能提高查询的性能吗？为什么

通常,通过索引查询数据比全表扫描要快.但是我们也必须注意到它的代价.

索引需要空间来存储,也需要定期维护, 每当有记录在表中增减或索引列被修改时,索引本身也会被修改. 这意味着每条记录的INSERT,DELETE,UPDATE将为此多付出4,5 次的磁盘I/O. 因为索引需要额外的存储空间和处理,那些不必要的索引反而会使查询反应时间变慢.使用索引查询不一定能提高查询性能,索引范围查询(INDEX RANGE SCAN)适用于两种情况:

基于一个范围的检索,一般查询返回结果集小于表中记录数的30%
基于非唯一性索引的检索














