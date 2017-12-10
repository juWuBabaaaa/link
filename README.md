create database ;
show databases ;
drop dataebase ;

create table table_name (
	colum_name data_type,
	colum_name data_type,
	.
	.
	.
	clolum_name data_type
) ;

eg:

create table account (
	id bigint(20),        
	createTime datetime,	
	ip varchar(255),	
	mobile varchar(255),	
	nickname varchar(255),
	passwd varchar(255),
	username varchar(255),
	avatar varchar(255),	
	brief text,		
	job varchar(255),	
	location varchar(255),
	qq varchar(255),
	gender int(11), 	
	city varchar(255),	
	province varchar(255)	
) ;

用户登录时的ip（varchar数据类型的优势：实际多少位就给多少位不一定255）

删除数据表

命令代码：
drop table table_name ;

use gc  使用gc这个数据库

show tables ;

drop table table_name ;

describe table_name ;

增加列
alter table 【table_name】 add 【column_name】 【data_type】[not null] [default]
eg:
alter table account add c1 int(11) not null default 1 ;(该列不为null，默认值为1)

还有一些别的尾项。
删除列：

alter table 【table_name】 drop 【column_name】
eg:
alter table account drop c1 ;

修改列：
alter table 【table_name】 change 【old_column_name】 【new_column_name】 【data_type】

修改表名：
alter table 【table_name】 rename 【new_table_name】


查看表的数据：
select * from table_name ;

select col_name1,col_name2,... from table_name ;

插入数据：

insert into 【table_name】 values(值1,值2，...)

insert into 【table_name】 (列1，列2...) values (值1，值2，...)

eg:
insert into book(title) values('title1') ;

where 语法:
select * from table_name where col_name 运算符值
eg: select * from book where title = 't';

运算符除常见的还有：between \like (按某个模式查找)
等于  是 “=”

条件组合 and  or  

