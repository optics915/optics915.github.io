> 作者：optics915。
>
> **介绍:** 这是一个随手化的类似笔记的个人博客 作者: **[optics915](https://optics915.gitee.io/docsify-blog)** 。一般会在此记录一些从知乎、B站、GitHub上学来的有意思的操作，每一个过程都先自己操作成功之后再将其记录下来，以方便日后碰到相似类型时有理可依。

这个系列的文章是之前在牛客网上做基础题时遇到的一些自己认为有难度以及做错的题目，某种程度上这些题目可以给面试带来一些辅助作用，很多是基础问题，有利于面试前的突击。

#### 1. SQL中属于分组查询的语句是？（）
		a. 选项	C
			i. Where
			ii. 联盟链
			iii. Group By
			iv. Having
		b. 解析
			i. where是筛选、group by是分组。order by 是排序，having+order by是筛选分组
			ii. mysql中这些关键字是按照如下顺序进行执行的：Where, Group By, Having, Order by。
				1) 首先where将最原始记录中不满足条件的记录删除(所以应该在where语句中尽量的将不符合条件的记录筛选掉，这样可以减少分组的次数)
				2) 然后通过Group By关键字对视图进行分组 
				3) 接着根据Having关键字后面指定的筛选条件，将分组后不满足条件的记录筛选掉
				4) 最后按照Order By语句对视图进行排序，这样最终的结果就产生了。
#### 2. SQL语言共分为三大类（亦有说法分为四大类），那么不属于数据操纵语言的有（）
		a. 选项	B
			i. update
			ii. grant
			iii. delete
			iv. insert
		b. 解析
			i. 数据查询语言（DQL）：是由SELECT子句，FROM子句，WHERE子句组成的查询块 
			ii. 数据操纵语言（DML）: SELECT(查询) INSERT(插入) UPDATE(更新) DELETE(删除） 
			iii. 数据定义语言（DDL）：CREATE(创建数据库或表或索引）ALTER(修改表或者数据库）DROP(删除表或索引） 
			iv. 数据控制语言（DCL）：GRANT(赋予用户权限） REVOKE(收回权限） DENY(禁止权限) 
			v. 事务控制语言（TCL）：SAVEPOINT (设置保存点）ROLLBACK (回滚) COMMIT(提交)
#### 3. 设有图书管理数据库：
	图书(总编号C(6),分类号C(8),书名C(16),作者C(6),出版单位C(20),单价N(6,2))
	读者(借书证号C(4),单位C(8),姓名C(6),性别C(2),职称C(6),地址C(20))
	借阅(借书证号C(4),总编号C(6),借书日期D(8))
	对于图书管理数据库，查询0001号借书证的读者姓名和所借图书的书名。
	
	SQL语句正确的是______。
	SELECT 姓名,书名 FROM 借阅,图书,读者 WHERE;
	借阅.借书证号="0001" AND;
	_____
	____
		a. 选项
			i. 图书.分类号=借阅.分类号 AND;
			读者.借书证号=借阅.借书证号
			ii. 图书.总编号=借阅.总编号 AND;
			读者.借书证号=借阅.借书证号
			iii. 读者.总编号=借阅.总编号 AND;
			读者.借书证号=借阅.借书证号
			iv. 图书.总编号=借阅.总编号 AND;
			读者.书名=借阅.书名
		b. 解析
			i. 本题图书的总编号<->借阅中的总编号;借阅表中的借书证号<->读者表中的借书证号；借阅表将图书表和读者表联系在一起！
#### 4. 请取出 BORROW表中日期(RDATE字段)为当天的所有记录？(RDATE字段为datetime型，包含日期与时间)。SQL语句实现正确的是：（      ）
		a. 选项	A
			i. select * from BORROW where datediff(dd,RDATE,getdate())=0
			ii. select * from BORROW where RDATE=getdate()
			iii. select * from BORROW where RDATE-getdate()=0
			iv. select * from BORROW where RDATE&gt;getdate()
		b. 解析
			i. 理解datediff（dd,RDDATE,getdate()）==0含义，即返回以日为单位（dd），和当前日期（getdate）相差为0日的RDDATE。
			ii. MySQL中DATEDIFF()函数语法为DATEDIFF(date1,date2)， 返回两个日期之间的天数
#### 5. 下面有关sql 语句中 delete truncate的说法正确的是？（）
		a. 选项	AC
			i. 论清理表数据的速度，truncate一般比delete更快
			ii. truncate命令可以用来删除部分数据。
			iii. truncate只删除表的数据不删除表的结构
			iv. delete能够回收高水位
		b. 解析
			1、处理效率：drop>trustcate>delete
			2、drop删除整个表；trustcate删除全部记录，但不删除表；delete删除部分记录
			3、delete不影响所用extent，高水线保持原位置不动；trustcate会将高水线复位。
#### 6. 数据库的（ ）是指数据的正确性和相容性
		a. 选项	B
			i. 并发控制
			ii. 完整性
			iii. 安全性
			iv. 共享性
		b. 解析
			i. 数据库完整性 （Database Integrity）是指数据库中数据在逻辑上的一致性、正确性、 有效性 和相容性。
#### 7. 事务是数据库操作的基本工作单位。如果一个事务执行成功，则全部更新提交；如果一个事务执行失败，则已做过的更新被恢复原状，好像整个事务从未有过这些更新，这样保持了数据库处于（ ）状态。
		a. 选项	B
			i. 安全性
			ii. 一致性
			iii. 完整性
			iv. 可靠性
		b. 解析
			i. 事务的四个基本要素是ACID 
			ii. 原子性(Atomic)：整个事务中所有的***作要么全部完成，要么全部不完成，不可能停滞在中间的某个环节，事务在执行过程中发生错误，会被回滚到事务开始前的状态，就像这个事务未被执行过一样。 
			iii. 一致性(Correspondence) ：在事务开始之前和结束之后，数据库的完整性约束不会被破坏。事务的一致性决定了一个系统设计和实现的复杂度。事务可以不同程度的一致性。
			iv. 隔离性(Isolation)：并发事务之间互相影响的程度，比如一个事务会不会读取到另一个未提交的事务修改的数据。在事务并发***作时，可能出现的问题有：脏读，不可重复读，幻读。
			v. 持久性(Durability)：在事务完成以后，该事务对数据库所做的更改持久的保存在数据库中，并不会被回滚。
#### 8. SQL语言具有的功能是　( )
		a. 选项	B
			i. 关系规范化，数据操纵，数据控制
			ii. 数据定义，数据操纵，数据控制
			iii. 数据定义，关系规范化，数据控制
			iv. 数据定义，关系规范化，数据操纵
		b. 解析
			SQL主要功能分成四部分： 
			1. 数据定义：（DDL）用于定义SQL模式、基本表、视图和索引的创建和撤消操作。 
			2. 数据操纵：（DML）数据操纵分成数据查询和数据更新两类。数据更新又分成插入、删除、和修改三种操作。  
			3. 数据控制：包括对基本表和视图的授权，完整性规则的描述，事务控制等内容。  
			4. 嵌入式SQL的使用规定：涉及到SQL语句嵌入在宿主语言程序中使用的规则。
#### 9. 在数据库设计中，将ER图转换成关系数据模型的过程属于(  ) 
		a. 选项	B
			1. 需求分析阶段
			2. 逻辑设计阶段
			3. 概念设计阶段
			4. 物理设计阶段
		b. 解析
			1. 数据库设计通常分为6个阶段
				1) 需求分析：分析用户的需求，包括数据、功能和性能需求；
				2) 概念结构设计：主要采用E-R模型进行设计，包括画E-R图；
				3) 逻辑结构设计：通过将E-R图转换成表，实现从E-R模型到关系模型的转换；
				4) 数据库物理设计：主要是为所设计的数据库选择合适的存储结构和存取路径；
				5) 数据库的实施：包括编程、测试和试运行；
				6) 数据库运行与维护：系统的运行与数据库的日常维护。）,主要讨论其中的第3个阶段,即逻辑设计。通过一个实际的案例说明在逻辑设计中E-R图向关系模式的转换。
#### 10. 一张学生成绩表score，部分内容如下：
	name       course     grade
	张三        操作系统      67
	张三        数据结构      86
	李四        软件工程      89
		a. 用一条SQL 语句查询出每门课都大于80 分的学生姓名，SQL语句实现正确的是：（      ）
		b. 选项	A
			1. Select distinct name from score where name not in(Select name from score where grade <= 80);
			2. Select distinct name from score where name  in(Select name from score where grade <= 80);
			3. Select  name from score where name not in(Select name from score where grade <= 80);
			4. Select  name from score where name  in(Select name from score where grade <= 80);
		c. 解析
			1. where name not in(Select name from score where grade <= 80);
				1) 选择分数不在80分及以下的名字，你想小王数据结构81，小王操作系统99......就会选出多个小王。 
				2) 在表中，可能会包含重复值。这并不成问题，不过，有时您也许希望仅仅列出不同（distinct）的值。 
			2. 关键词 DISTINCT 用于返回唯一不同的值。
#### 11. 某软件公司正在升级一套水务管理系统。该系统用于县市级供排水企业、供水厂、排水厂中水务数据的管理工作。系统经重新整合后，开发人员决定不再使用一张备份数据表waterinfo001表，需永久删除。选出符合要求的语句。 
		a. 选项	C
			1. DELETE TABLE waterinfo001
			2. DELETE FROM TABLE waterinfo001
			3. DROP TABLE waterinfo001
			4. DROP FROM TABLE waterinfo001
		b. 解析
			1. drop是完全删除表，包括表结构
			2. delete是删除表数据，保留表的结构，而且可以加where,只删除一行或者多行
			3. truncate 只能删除表数据，会保留表结构，而且不能加where
#### 12. 有一个名为app的MySQL数据库表，其建表语句如下：
	1	CREATE TABLE `app` (
	2	`app_id` int(10) DEFAULT '0',//应用ID
	3	`version_code` int(10) DEFAULT '0',//应用的版本号
	4	`download_count` int(10) DEFAULT '0'//当前版本的下载量
	5	) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4
	当前表中数据记录如下，一条记录表示某个应用的某个版本的下载量记录：
	+--------+--------------+----------------+
	| app_id | version_code | download_count |
	+--------+--------------+----------------+
	|      1 |           10 |             90 |
	|      1 |           11 |            100 |
	|      1 |           10 |             20 |
	|      2 |           15 |             10 |
	|      2 |           16 |             15 |
	|      2 |           17 |             30 |
	|      2 |           16 |              5 |
	|      3 |            2 |             50 |
	+--------+--------------+----------------+
	
		a. 问： 下面那个MySQL语句可以查出每个应用中总下载量最大的版本号和次数（ ）？
		b. 选项	B
			1. select t.app_id, t.version_code, max(t.download_sum) from (select app_id, version_code, sum(download_count) download_sum from app
			group by app_id, version_code) as t group by t.app_id having t.download_sum > max(t.download_sum);
			2. select t.app_id, t.version_code, max(t.download_sum) from (select app_id, version_code, sum(download_count) download_sum from app
			group by app_id, version_code order by download_sum desc) as t group by t.app_id;
			3. select 1.app_id, l.version_code, max(download_sum) from app l inner join (select app_id , version_code, sum(download_count) as
			download_sum from app group by app_id, version_code ) as t on l.app_id = t.app_id and l.version_code = t.version_code group by l.app_id, l.version_code;
			4. select l.app_id, l.version_code, max(download_sum) from app l inner join (select app_id , version_code, sum(download_count) as
			download_sum from app group by app_id, version_code ) as t on l.app_id = t.app_id and l.version_code = t.version_code group by l.app_id;
		c. 解析
			1. 先按照哪个应用的具体哪个版本分好类，from app group by app_id, version_code；
			2. 然后取出id，版本号，最关键的是按照聚类累加一下下载量并对其重命名，select app_id, version_code, sum(download_count) download_sum from app  group by app_id, version_code；
			3. 之后对选出的数据按照下载量降序排序处理；select app_id, version_code, sum(download_count) download_sum from app group by app_id, version_code order by download_sum desc；
			4. 题目要求:每个应用中总下载量最大的版本号和次数，那么对整理后的新表重命名并按照应用id进行分类，(select app_id, version_code, sum(download_count) download_sum from app group by app_id, version_code order by download_sum desc) as t group by t.app_id
			5. 选出每一类（也就是每一个应用）中最大下载量的数据表信息。
#### 13. 在SQL中语法规范中，having子句的使用下面描述正确的是：（    ）
		a. 选项	AC
			1. having子句即可包含聚合函数作用的字段也可包括普通的标量字段
			2. 使用having的同时不能使用where子句
			3. having子句必须于group by 子句同时使用，不能单独使用
			4. 使用having子句的作用是限定分组条件
			5. Having子句和where子句是等同的
			6. 如果select语句中没有聚合函数的使用，就不能使用having子句
		b. 解析
			1. SQL中各字句执行顺序：
				1) select col_name from table
where col_name > xxx
group by col_name
having ...
order by ... desc
			2. B：where在分组前过滤，having在分组后过滤，两者之间不冲突。 
			3. D：group by 限定分组条件，即用按照那一列进行分组，相同列值被分为一组。
			4. F：没有聚合函数的使用也可以用having过滤。
				1) 聚合函数
					a) 聚合函数对一组值执行计算并返回单一的值
					b) 应用：求个数/记录数/项目数等：count()
#### 14. 下面有关sql 语句中 delete truncate的说法正确的是？（）
		a. 选项	AC
			1. 论清理表数据的速度，truncate一般比delete更快
			2. truncate命令可以用来删除部分数据。
			3. truncate只删除表的数据不删除表的结构
			4. delete能够回收高水位
		b. 解析
			1. 处理效率：drop>trustcate>delete
			2. drop删除整个表；trustcate删除全部记录，但不删除表；delete删除部分记录
			3. delete不影响所用extent，高水线保持原位置不动；trustcate会将高水线复位。
#### 15. 修改表test_tbl字段i的缺省值为1000，可以使用SQL语句（      ）
		a. 选项	A
			1. ALTER TABLE test_tbl ALTER i SET DEFAULT 1000;
			2. ALTER TABLE test_tbl i SET DEFAULT 1000;
			3. ALTER TABLE test_tbl MODIFY i SET DEFAULT 1000;
			4. ALTER TABLE test_tbl CHANGE i SET DEFAULT 1000;
		b. 解析
			1. CHANGE 用来修改字段名字以及类型 
			2. modify 用来修改字段类型 
			3. alter column ... set  用来修改字段数据
			ALTER TABLE <表名> [修改选项]
			{ ADD COLUMN <列名> <类型>
			| CHANGE COLUMN <旧列名> <新列名> <新列类型>
			| ALTER COLUMN <列名> { SET DEFAULT <默认值> | DROP DEFAULT }
			| MODIFY COLUMN <列名> <类型>
			| DROP COLUMN <列名>
			| RENAME TO <新表名> }
