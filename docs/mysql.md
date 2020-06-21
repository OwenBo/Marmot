# mySql
```sql
mysqldump -u root -p test actors >d:\backup2.sql
mysql -h 127.0.0.1 -uroot -p test1_db < d:\1.sql
```
```sql
创建表  
    create table t1(
    id int unsigned not null auto_increment primary key, --进行主键自增
    name varchar(30)
    );
复制表  insert into t2 seclect * from t1;   --不存在
删除表  drop table t1;
查看表结构  desc t1;
往表插入数据
	insert into t1(name) values ("user1");
	insert into t1(name) values ("user2");
查询表内容
	select * from t1;
复制表时注意复制表的结构
	create table t2 like t1;
create 创建索引 不赞成使用
	create index in_name on t1(name);
	show index from t1;  --查看索引
	drop index in_name on t1;  --删除索引
	show index from t1;  --查看索引
	把neme变成唯一索引
	create unique index un_name on t1(name)

连接另一台服务器数据库
    mysql -hsp50417eac314af.mysql.rds.aliyuncs.com -ushoushou -pqihao313 shoushou
    mysql -h52.9.84.9 -uwww -pbbs772bbs88 de_forum


1.查询表中有多少数据；
    select count(*) from tko_getcard;
2.去掉字段中重复的查询
    select distinct pid from tk_launcher;
3.下例删除 authors 表中的所有数据。
   truncate table --表名；
   delete from --表名;
   delete from tk_launcher where id ='4'; --删除一行
   drop table tb_admin; --删除表
4.创建表
    create table tb_user(id int not null auto_increment primary key,name varchar(30),age int, sex int(10),email varchar(60),primt int);
    create table user (userid char(6) primary key,username varchar(20),age int);

                               非空    自动增长       主键           名字           年龄      性别       email            日期
创建表（并学习其他表结构）
    create table tb_admin1 like tb_admin; 

插入数据
    mysql> insert into tb_user values(null,'admin','10','nan','admin@qq.com','10:31');
    mysql> insert into tb_user(user,password,email,createtime) values('jie','55555','jie@hotmial.com','2008-2-05 05:03:10');

5.要想将文本文件“pet.txt”装载到pet表中，使用这个命令：
    mysql> load data local infile '/path/pet.txt' into table pet;
6.修改：用一个UPDATE语句仅修正错误记录：
    mysql> update pet set birth = '1989-08-31' where name = 'Bowser';
7.导出表
    mysql>select * into outfile '111.txt' from tk_launcher; --保存在/data/app/mysql-item/  下面
8.对指定 列进行排序
    mysql>select password from tb_user order by password;
  对指定 多列进行排序
    select id, password from tb_user order by id,password;
9.重命名表
    rename table tb_admin to tb_admin1;

10.创建表（并学习其他表结构）
    create table tb_admin1 like tb_admin; 

11.更新表
    update qjp2_getcard set uid=0,uname='',issend=0,gettime=0,ip='NULL',email='',mobile='' where issend=1;

12.mysql  时间转换
    select unix_timestamp('2013-01-21')
    SELECT FROM_UNIXTIME(1267372800)

    select distinct(name),count(*) from tabname group by name;
13.添加字段
    alter table 表名 add 字段名 值; 
    alter table newexample add address varchar(110) after stu_id;

//增加一个新列
    alter table t2 add d timestamp;
    alter table infos add ex tinyint not null default ‘0′;

//删除列
    alter table t2 drop column c;

//重命名列
    alter table t1 change a b integer;

//改变列的类型
    alter table t1 change b b bigint not null;
    alter table infos change list list tinyint not null default ‘0′;


14.同时查询多个表
    SELECT movies.title, movies.year, actors.name
    FROM movies, actors
    WHERE movies.actor = actors.id
    ORDER BY movies.year ASC 

15.删除唯一索引
    alter table sgyxz_email drop index email;
    alter table xxx drop key email

    select sum(consume_coins),user_id from astd_pay_log group by user_id order by sum(consume_coins) desc limit 2;
    select sum(consume_coins) from astd_pay_log group by user_id order by sum(consume_coins) desc limit 5;

    select * from as_draw_code group by code having count(1)>=2;

16.  mysqldump
    1、导出數據库為dbname的表结构（其中用戶名為root,密码為dbpasswd,生成的脚本名為db.sql）
    mysqldump -uroot -pdbpasswd -d dbname >db.sql;

    2、导出數據库為dbname某张表(test)结构
    mysqldump -uroot -pdbpasswd -d dbname test>db.sql;

    3、导出數據库為dbname所有表结构及表數據（不加-d）
    mysqldump -uroot -pdbpasswd  dbname >db.sql;

    4、导出數據库為dbname某张表(test)结构及表數據（不加-d）  导出到当前目录
    #mysqldump -uroot -pdbpasswd dbname test>db.sql;     

17.查询每日总数
    SELECT count(*),DATE_FORMAT(FROM_UNIXTIME(time), '%Y-%m-%d') AS t FROM coc_newworld doc WHERE DATE_FORMAT(FROM_UNIXTIME(time), '%Y-%m') = '2017-05' group by t;

18. 查看数据导出的默认目录   (select * into outfile'11.txt'    )
    show variables like '%secure%'

新设置用户或更改密码后需用flush privileges刷新MySQL的系统权限相关表

导入
    source /data/app/bin
    mysql -uroot -p 库名 < aaa.sql

    mysqldump -ukunluntw -pNoNeed4Pass32768 kunlun_code sengoku_getcode_hdcard>sengoku.sql;

    充值id排序
    alter table tablename drop column id;
    alter table tablename add id mediumint(8) not null primary key auto_increment first;

授权
    grant all privileges on *.* to pushall_info@203.69.146.220 identified by 'hP58sfSAwardPlatfoUopass32768';
    grant all on wenbo_db.* to "test_db"@"127.0.0.1" identified by "123456"
    grant all privileges on *.* to activity_test@42.62.107.108 identified by "hP58sfSAwardPlatfoUopass32768"


$thisDayStart=mktime(0,0,0,date("m"),date("d"),date("Y"));
$thisDayEnd=mktime(23,59,59,date("m"),date("d"),date("Y"));

    select count(id) from com_users where addtime>=".$thisDayStart." and addtime<".$thisDayEnd.";

mysql配置  数据语言包导入
mysql_tzinfo_to_sql
/usr/share/zoneinfo
mysql_tzinfo_to_sql /usr/share/zoneinfo |mysql -uroot mysql

/usr/bin/mysql --default-character-set=utf8 --socket=/data/app/mysql-item/mysql.sock -uroot -p"RVRW5MJvGxyt" kunlun_code -e "select email from alitathegame_age_email" > alita.txt

全局读锁定
    FLUSH TABLES WITH READ LOCK

解锁的语句
    unlock tables
```
## demo

### 按分钟统计

```sql
SELECT DATE_FORMAT(TimeStart, '%Y-%m-%d %H:%i:00') AS time, COUNT(*) AS num
FROM track 
WHERE Flag = 0 AND Duration >= 300
GROUP BY time
ORDER BY time;
```

### 按n分钟统计
```sql
SELECT time, COUNT( * ) AS num 
FROM
	(
	SELECT Duration,
		DATE_FORMAT(
			concat( date( TimeStart ), ' ', HOUR ( TimeStart ), ':', floor( MINUTE ( TimeStart ) / 30 ) * 30 ),
			'%Y-%m-%d %H:%i' 
		) AS time 
	FROM tarck
	WHERE Flag = 0  AND Duration >= 300 
	) a 
GROUP BY DATE_FORMAT( time, '%Y-%m-%d %H:%i' ) 
ORDER BY time;
```

### 按小时统计
```sql
SELECT DATE_FORMAT(TimeStart, '%Y-%m-%d %H:00:00') AS time, COUNT(*) AS num
FROM track
WHERE Flag = 0 AND Duration >= 300
GROUP BY time
ORDER BY time;
```


### 按天时统计

```sql
SELECT DATE(TimeStart) AS date, COUNT(*) AS num
FROM track
WHERE Flag = 0 AND Duration >= 300 
GROUP BY date
ORDER BY date;
```
