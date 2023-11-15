MySQL
# 基础篇
MySQL匹配环境后，直接win+R进cmd

```mysql
mysql -u root -p
password:xxxx
```

## 通用语法及分类
### DDL（数据定义语言）
`数据库`操作
```MySQL
-- 数据库操作
/* 多行注释 */
show databases; -- 查所有数据库
select database(); -- 当前在哪个数据库下操作
use database_name; -- 使用数据库，转换到需要操作的数据库对象

create databases [if not exists] database_name charset utf8mb4; -- 创建数据库
drop databases [if exists] database_name; -- 删除数据库
```

 `表结构`操作
```MySQL
-- 表操作
show tables; -- 查询当前数据库所有表
desc tb_name;  -- 查询表框架
show create table tb_name; -- 看创建表的具体语句

-- 创建表
create table tb_name(
id int [comment 字段注释];
name char(10) [comment 姓名];
age int [comment 年龄];
gender char(10) [comment 性别]
) comment 用户表; -- 最后一个字段后面没有逗号

-- 表内容的增改删
alter table tb_name add nickname char(10) [comment '昵称']; 
-- 添加字段
alter table tb_name drop id_change; -- 删除字段
alter table tb_name modify id char(10); -- 修改数据类型
alter table tb_name change id id_change char(10) [comment '用户名']; -- 修改字段名和字段类型
alter table tb_name rename to tb_name_new; -- 修改表名

-- 删除表
drop table [if exists] tb_name_new; -- 删除表
truncate table tb_name_new; -- 删除原表并创建一样表头的新表 
```

[字段（数据）类型](MySQL/字段（数据）类型.md)

### DML（数据操作语言）
对`表中数据`进行操作

```MySQL
-- 单一添加
insert into tb_name (field_name1,field_name2... ) values (值1,值2...); -- 对指定字段添加数据
INSERT INTO tb_name VALUES (值1, 值2, ...);  -- 对全部字段添加数据

-- 批量添加
INSERT INTO tb_name (字段名1, 字段名2, ...) VALUES (值1, 值2, ...), (值1, 值2, ...), (值1, 值2, ...); -- 指定字段
INSERT INTO tb_name VALUES (值1, 值2, ...), (值1, 值2, ...), (值1, 值2, ...); -- 全部字段

-- 改
UPDATE tb_name SET 字段名1 = 值1, 字段名2 = 值2, ... 
[ WHERE id = 1];  

-- 删
DELETE FROM 表名 [ WHERE 条件 ]; 
```

注意事项

- 字符串和日期类型数据应该包含在**引号中**

- 插入的数据大小应该在字段的规定**范围内**


### DQL（数据查询语言）

```MySQL
-- 编写顺序：
select 字段列表 
from 表名列表 
where 条件列表 
group by 分组字段列表 
having 分组后条件列表 
order by 排序字段列表
limit 分页参数；

-- 执行顺序：
FROM -> WHERE -> GROUP BY -> HAVING -> SELECT -> ORDER BY -> LIMIT

-- 1，基础查询
select field_name1,field_name2... from tb_name;  -- 查询多个字段
select * from tb_name; -- 查询所有字段

select field_name1 [as filed_name2] from tb_name; -- 设置别名1
select field_name1 filed_name2 from tb_name; -- 设置别名2

select distinct field_name from tb_name; -- 去重

-- 2，条件查询
 select field_name from tb_name where 条件列表； -- 细看下面的举例
 
-- 聚合函数
SELECT 聚合函数(field_name1,field_name2...) FROM tb_name; -- NULL值不参与聚合函数

-- 分组查询
SELECT field_name1,field_name2... FROM tb_name [ WHERE 条件列表 ] GROUP BY 分组字段名 [ HAVING 分组后的过滤条件 ]; -- where筛选，再分组，执行聚合函数，再根据having二次筛选

-- 排序查询
SELECT field_name1,field_name2... FROM tb_name ORDER BY 字段1 排序方式1, 字段2 排序方式2; -- ASC: 升序（默认）;DESC: 降序

-- 分页查询
语法：  
SELECT field_name1,field_name2... FROM tb_name LIMIT 起始索引, 查询记录数;
```

#### 1，基础查询

#### 2，条件查询
转义：

`SELECT * FROM 表名 WHERE name LIKE '/_张三' ESCAPE '/'`  

/ 之后的\_不作为通配符  

| 比较运算符          | 功能                                        |     |
| ------------------- | ------------------------------------------- | --- |
| >                   | 大于                                        |     |
| >=                  | 大于等于                                    |     |
| <                   | 小于                                        |     |
| <=                  | 小于等于                                    |     |
| =                   | 等于                                        |     |
| <> 或 !=            | 不等于                                      |     |
| BETWEEN ... AND ... | 在某个范围内（含最小、最大值）              |     |
| IN(...)             | 在in之后的列表中的值，多选一                |     |
| LIKE 占位符         | 模糊匹配（\_匹配单个字符，%匹配任意个字符） |     |
| IS NULL             | 是NULL                                      |     |

关于**in**取范围值！

where `交易卡号`IN ('621582xxxxxxxxxxxxx', '6228480xxxxxxxxxxxxx')

| 逻辑运算符         | 功能                         |
| ------------------ | ---------------------------- |
| AND 或 &&          | 并且（多个条件同时成立）     |
| OR 或 &#124;&#124; | 或者（多个条件任意一个成立） |
| NOT 或 !           | 非，不是                     |

例子：

```mysql
-- 年龄等于30
select * from employee where age = 30;
-- 年龄小于30
select * from employee where age < 30;
-- 小于等于
select * from employee where age <= 30;
-- 没有身份证
select * from employee where idcard is null or idcard = '';
-- 有身份证
select * from employee where idcard;
select * from employee where idcard is not null;
-- 不等于
select * from employee where age != 30;
-- 年龄在20到30之间
select * from employee where age between 20 and 30;
select * from employee where age >= 20 and age <= 30;
-- 下面语句不报错，但查不到任何信息
select * from employee where age between 30 and 20;
-- 性别为女且年龄小于30
select * from employee where age < 30 and gender = '女';
-- 年龄等于25或30或35
select * from employee where age = 25 or age = 30 or age = 35;
select * from employee where age in (25, 30, 35);
-- 姓名为两个字
select * from employee where name like '__';
-- 身份证最后为X
select * from employee where idcard like '%X';
select * from employee where idcard like '_________________X';
```

#### 3，聚合查询（聚合函数）

常见聚合函数：

| 函数  | 功能     |
| ----- | -------- |
| count | 统计数量 |
| max   | 最大值   |
| min   | 最小值   |
| avg   | 平均值,不是“mean”   |
| sum   | 求和     |

例子：

```MySQL
-- count()
SELECT count(id) from employee where workaddress = "广东省";
SELECT count(*) from employee where workaddress = "广东省";
```


#### 4，分组查询
where 和 having 的区别：

- 执行时机不同：where是**分组之前进行过滤**，不满足where条件**不参与分组**；having是**分组后对结果进行过滤**。

- 判断条件不同：where**不能对聚合函数**进行判断，而having可以。

 注意事项：
 
- 执行顺序：**where > 聚合函数 > having**

- 分组之后，查询的字段一般为聚合函数和分组字段，查询其他字段无任何意义

例子：

```mysql
-- 根据性别分组，统计男性和女性数量（只显示分组数量，不显示哪个是男哪个是女）
select count(*) from employee group by gender;
-- 根据性别分组，统计男性和女性数量
select gender, count(*) from employee group by gender;
-- 根据性别分组，统计男性和女性的平均年龄
select gender, avg(age) from employee group by gender;
-- 年龄小于45，并根据工作地址分组
select workaddress, count(*) from employee where age < 45 group by workaddress;
-- 年龄小于45，并根据工作地址分组，获取员工数量大于等于3的工作地址
select workaddress, count(*) address_count from employee where age < 45 group by workaddress having address_count >= 3;
```

#### 5，排序查询
注意事项

如果是多字段排序，先对第一个字段进行排序，在次基础上，在相同的第一字段下再对第二字段进行排序；

例子：
```mysql
-- 根据年龄升序排序
SELECT * FROM employee ORDER BY age ASC;
SELECT * FROM employee ORDER BY age;
-- 两字段排序，根据年龄升序排序，入职时间降序排序(如果年龄相同那么就按这个)
SELECT * FROM employee ORDER BY age ASC, entrydate DESC;
```

#### 6，分页查询
例子：
```mysql
-- 查询第一页数据，展示10条
SELECT * FROM employee LIMIT 0, 10;
SELECT * FROM employee LIMIT    10;
-- 查询第二页
SELECT * FROM employee LIMIT 10, 10;
```

注意事项
- 起始索引从0开始，起始索引 = （**查询页码 - 1**） * 每页显示记录数

- 分页查询是**数据库的方言**，不同数据库**有不同实现**，MySQL是LIMIT

- 如果查询的是第一页数据，起始索引可以省略，直接简写 LIMIT 10，省略了0

### DCL数据控制
```mysql
-- 1，管理用户
-- 查询用户：
USER mysql;
SELECT * FROM user;
-- 创建用户:  
CREATE USER '用户名'@'主机名' IDENTIFIED BY '密码';
-- 修改用户密码：  
ALTER USER '用户名'@'主机名' IDENTIFIED WITH mysql_native_password BY '新密码';
-- 删除用户：  
DROP USER '用户名'@'主机名';


-- 2，权限控制
-- 查询权限：  
SHOW GRANTS FOR '用户名'@'主机名';
-- 授予权限：  
GRANT 权限列表 ON 数据库名.表名 TO '用户名'@'主机名';
-- 撤销权限：  
REVOKE 权限列表 ON 数据库名.表名 FROM '用户名'@'主机名';

```

注意事项

- 主机名可以使用 % 通配

- 多个权限用逗号分隔

- 授权时，数据库名和表名可以用 * 进行通配，代表所有

| 权限                | 说明               |
| ------------------- | ------------------ |
| ALL, ALL PRIVILEGES | 所有权限           |
| SELECT              | 查询数据           |
| INSERT              | 插入数据           |
| UPDATE              | 修改数据           |
| DELETE              | 删除数据           |
| ALTER               | 修改表             |
| DROP                | 删除数据库/表/视图 |
| CREATE              | 创建数据库/表      |

## 函数
指一段可以直接被另外一段程序调用的程序或代码。

### 字符串函数
以字符串为单位进行增、改、删的操作

```mysql
-- 拼接
SELECT CONCAT('Hello', 'World');
-- 左填充，使字符串总长度达到5个为止
SELECT LPAD('01', 5, '-');
-- 右填充
SELECT RPAD('01', 5, '-');

-- 小写
SELECT LOWER('Hello');
-- 大写
SELECT UPPER('Hello');

-- 去头尾除空格
SELECT TRIM(' Hello World ');
-- 切片（起始索引为1）
SELECT SUBSTRING('Hello World', 1, 5);

-- 案例：将员工编号统一修改为5位数，如1号员工应为00001
update tb_name set field_name1 = lpad(field_name1, 5 , '0')

```



| 函数  | 功能  |
| ------------ | ------------ |
| CONCAT(s1, s2, ..., sn)  | 字符串拼接，将s1, s2, ..., sn拼接成一个字符串  |
| LPAD(str, n, pad)  | 左填充，用字符串pad对str的左边进行填充，达到n个字符串长度  |
| RPAD(str, n, pad)  | 右填充，用字符串pad对str的右边进行填充，达到n个字符串长度  |
| LOWER(str)  | 将字符串全部转为小写  |
| UPPER(str)  | 将字符串全部转为大写  |
| TRIM(str)  | 去掉字符串头部和尾部的空格  |
| SUBSTRING(str, start, len)  | 返回从字符串str从start位置起的len个长度的字符串  |

### 数值函数
```MySQL
-- 向上取整
select ceil(1.1)

-- 向下取整
select floor(1.9)

-- 求模（求余）
select mod(7,3)

-- 取随机数
select rand()

-- 保留到指定位小数 
select round(x, y)

-- 案例：通过数据库的函数，生成一个六位数的随机验证码
select lpad(round(rand()*1000000, 0), 6, '0')

```


| 函数  | 功能  |
| ------------ | ------------ |
| CEIL(x)  | 向上取整  |
| FLOOR(x)  | 向下取整  |
| MOD(x, y)  | 返回x/y的模  |
| RAND() | 返回0~1内的随机数 |
| ROUND(x, y) | 求参数x的四舍五入值，保留y位小数 |

### 日期函数
```mysql
-- 当前日期
select curdate()
-- 当前时间
select curtime()
-- 当前日期和时间
select now()

-- 获取日期的年、月、日
select year(now())
select month(now())
select day(now())

-- 获得推算日期
select date_add(now(), interval 70 year/month/day);

-- 获得日期间隔
select datediff(date1, date2)

-- 案例：查询所有员工的入职天数，并根据入职天数倒序排序
select datediff(curdate(), field_name1) as 入职天数 
from tb_name;
order by 入职天数
```

| 函数  | 功能  |
| ------------ | ------------ |
| CURDATE()  | 返回当前日期  |
| CURTIME()  | 返回当前时间  |
| NOW()  | 返回当前日期和时间  |
| YEAR(date)  | 获取指定date的年份  |
| MONTH(date)  | 获取指定date的月份  |
| DAY(date)  | 获取指定date的日期  |
| DATE_ADD(date, INTERVAL expr type)  | 返回一个日期/时间值加上一个时间间隔expr后的时间值  |
| DATEDIFF(date1, date2)  | 返回起始时间date1和结束时间date2之间的天数，用第一个时间减去第二个时间  |

### 流程函数
执行条件筛选，提高语句的效率

```mysql
-- if
select if(true, '1', '0')

-- ifnull
select ifnull(null, 'null') -- null才能代表空值，返回默认值null
select ifnull(' ', 'null') -- 非空，返回空格

-- case
-- 简单形式
select
	name,
	case workaddress when '北京市' then '一线城市'
	                  when '上海市' then '一线城市'
	                  else '二线城市' end  as '工作地址'
from employee;

-- 搜索形式
select
	name,
	case when age > 60 then '老年' 
	      when age > 30 then '中年' 
	      else '青年' end as '人群'
from employee;




```

| 函数  | 功能  |
| ------------ | ------------ |
| IF(value, t, f)  | 如果value为true，则返回t，否则返回f  |
| IFNULL(value1, value2)  | 如果value1不为空，返回value1，否则返回value2  |
| CASE [ expr ] WHEN [ val1 ] THEN [ res1 ] ... ELSE [ default ] END  | 如果expr的值等于val1，返回res1，... 否则返回default默认值  |
| CASE WHEN [ val1 ] THEN [ res1 ] ... ELSE [ default ] END  | 如果val1为true，返回res1，... 否则返回default默认值  |

## `约束`
用来作用于表中**字段上的规则**，用于**限制存储**在表中的数据，以保证数据库中的数据的正确、有效性和完整性

| 约束     | 描述                                                 | 关键字   |
| -------- | ---------------------------------------------------- | -------- |
| 主键  | 主键是一行数据的唯一标识，要求**非空且唯一**  | PRIMARY KEY  |
| 自动增长  |   **自动创建主键**字段的值              |   AUTO_INCREMENT |
| 非空 | 限制该字段的数据不能为null                           | NOT NULL |
| 唯一 | 保证该字段的所有数据都是**唯一、不重复**的，可以为空 | UNIQUE   |
| 默认约束  | 保存数据时，如果未指定该字段的值，则采用默认值  | DEFAULT  |
| 检查约束（逻辑条件）  | 保证字段值满足某一个条件  | CHECK  |
| 外键  | 用来让**两张**表的数据之间建立连接，保证数据的一致性和完整性  | FOREIGN KEY  |

### 常用约束
```mysql
create table user(
	id int primary key auto_increment comment '主键',
	name varchar(10) not null unique comment '姓名',
	age int check(age > 0 and age < 120) comment '年龄',
	status char(1) default '1' comment '状态',
	gender char(1) comment '性别'
) comment '用户表';

-- 验证表格约束
insert into user(name, age, status, gender) 
            values ('张三', '23', '1', '男'), ('李四', '25', '0', '男') -- 主键不用填，自动补充。即便添加数据错误，相应主键也会被申请使用
```

![Pasted image 20230715164632](attachments/Pasted%20image%2020230715164632.png)

### 外键约束：比较特殊的约束
外键用来让两张表的数据之间建立**逻辑连接**，**子表的外键是父表(主表)的主键**。父表中主键缺失下，子表中的数据的完整性无法保证。

```mysql
-- 1，创建表时同时添加指定外键
CREATE TABLE tb_name(
	字段名 字段类型,
	...
	[CONSTRAINT] [外键名称]（fk_子表名_字段） FOREIGN KEY (子表的外键字段) REFERENCES 主表(关联上的主表字段)
);  
-- 2，建表后，对表修改添加外键
ALTER TABLE 子表 ADD CONSTRAINT 外键名称（fk_子表名_字段） FOREIGN KEY (子表的外键字段) REFERENCES 主表 (关联上的主表字段名);
-- 更改删除/更新行为
ALTER TABLE 表名 ADD CONSTRAINT 外键名称（fk_子表名_字段） FOREIGN KEY (子表的外键字段) REFERENCES 主表名(主表字段名) ON UPDATE 行为 ON DELETE 行为;  
-- 删除外键：  
ALTER TABLE tb_name DROP FOREIGN KEY 外键名称（fk_子表名_字段）;

-- 例子  
alter table emp add constraint fk_emp_dept_id foreign key(dept_id) references dept(id);  
-- 查询外键？？？
SELECT * FROM INFORMATION_SCHEMA.KEY_COLUMN_USAGE WHERE constraint_schema = 'fundb' AND table_name = 't_score_math';
```

**外键名称**与子表外键字段不同，子表中显示的是子表与外键关联的外键字段，并不会显示外键名称。如果不添加外键名称，会指定为**f_mykey**，constraint \`f_mykey\`可以省略。fk_子表名_字段的命名方式只是为了方便识别！**f_子表外键**应该更常见

![Pasted image 20230715165707](attachments/Pasted%20image%2020230715165707.png)

| 行为  | 说明  |
| ------------ | ------------ |
| NO ACTION  | 当在父表中删除/更新对应记录时，首先检查该记录是否有对应外键，如果有则不允许删除/更新（与RESTRICT一致）  |
| RESTRICT  | 当在父表中删除/更新对应记录时，首先检查该记录是否有对应外键，如果有则不允许删除/更新（与NO ACTION一致）  |
| CASCADE  | 当在父表中删除/更新对应记录时，首先检查该记录是否有对应外键，如果有则也删除/更新外键在子表中的记录  |
| SET NULL  | 当在父表中删除/更新对应记录时，首先检查该记录是否有对应外键，如果有则设置子表中该外键值为null（要求该外键允许为null）  |
| SET DEFAULT  | 父表有变更时，子表将外键设为一个默认值（Innodb不支持）  |

## 多表查询
### 多表关系
提升数据质量，实体完整性和建立表联系后的参照完整性，都能提高数据质量。

#### 一对多（多对一）
**部门与员工**，一个部门对应多个员工，一个员工对应一个部门，在**多的一方建立外键**（员工表），指向**一的一方的主键**（部门表）。详见约束内容

![Pasted image 20230731200652](attachments/Pasted%20image%2020230731200652.png)

#### 多对多
**学生与课程**，一个学生可以选多门课程，一门课程也可以供多个学生选修，**建立第三张中间表**，中间表至少包含两个外键，分别关联两方主键。

![Pasted image 20230731200820](attachments/Pasted%20image%2020230731200820.png)

```MySQL
create table student_course(
	id int auto_increment primary key comment '主键ID' ,
	studentid int not null comment '学生ID',
	courseid  int not null comment '课程ID',
	constraint fk_courseid foreign key (courseid) references course (id),
	constraint fk_studentid foreign key (studentid) references student (id)
)comment '学生课程中间表';

insert into student course values (null,1,1),(null,1,2),(null,1,3),(null,2,2),(null,2,3),(null,3,4);
```

#### 一对一
用户与用户详情，一对一关系，多用于**单表拆分**，将一张表的基础字段放在一张表中，其他详情字段放在另一张表中，以提升操作效率。**在任意一方加入外键，关联另外一方的主键**，并且**设置外键为唯一的（UNIQUE）**，从而使外键不重复，区分一对多的i情况。

![Pasted image 20230731222434](attachments/Pasted%20image%2020230731222434.png)

```MySQL
create table tb_user(
	id int auto_increment primary key comment '主键ID',
	name varchar(10) comment '姓名'，
	age int comment '年龄'，
	gender char(1) comment '1: 男 ，2: 女'
	phone char(11) comment '手机号'
) comment '用户基本信息表';

create table tb_user_edu(
	id int auto_increment primary key comment '主键ID',
	degree varchar(20) comment '学历'，
	major varchar(50) comment'专业',
	primaryschool varchar(5) comment '小学',
	middleschool varchar(50) comment '中学',
	university varchar(50) comment '大学',
	userid int unique comment '用户ID',
	constraint fk_tb_user_edu_userid foreign key (userid) references tb_user(id)
)comment '用户教育信息表';
```

### 多表查询
区别之前的DQL单表查询，在多张表上进行查询。
**笛卡尔积**：两个集合A集合和B集合的所有组合情况（在多表查询时，需要消除无效的笛卡尔积）。  

```MySQL
合并查询，笛卡尔积，会展示所有组合结果
select * from employee, dept;

消除无效笛卡尔积：  
select * from employee, dept where employee.dept = dept.id;
```

![300](attachments/Pasted%20image%2020230802124643.png)

![300](attachments/Pasted%20image%2020230802074123.png)
#### 连接查询
将目光聚焦在`连接字段上`来理解笛卡尔积，再扩展到字段所在的行就是结果！
##### 内连接查询
查询的是两张表**交集的部分**。存在隐式内连接和显示内连接两种形式，形式上表现为表的连接形式和条件表现形式的差异，**显式性能更高**。

如果**只需要交积**上的数据，取交积比外积的效率更高些！

```mysql
1，隐式内连接：
SELECT 字段列表 FROM 表1, 表2 WHERE 条件 ...;
2，显式内连接：
SELECT 字段列表 FROM 表1 [ INNER ] JOIN 表2 ON 连接条件 ...;


-- 查询员工姓名，及关联的部门的名称
-- 隐式
select e.name, d.name 
from employee as e, dept as d
where e.dept = d.id;
-- 显式:能额外再增加其他筛选条件
select e.name, d.name
from employee as e
[inner] join dept as d
on e.dept = d.id;
```

简化表名，起别名！起了别名，表名便失效了，符合执行顺序！
##### 外连接查询
```mysql
1，左外连接
查询左表所有数据，以及两张表交集部分数据。相当于查询表1的所有数据，包含表1和表2交集部分数据  
SELECT 字段列表 FROM 表1 LEFT [ OUTER ] JOIN 表2 ON 条件 ...; 

2，右外连接  
查询右表所有数据，以及两张表交集部分数据。  
SELECT 字段列表 FROM 表1 RIGHT [ OUTER ] JOIN 表2 ON 条件 ...; 

-- 左
select e.*, d.name from employee as e left [outer] join dept as d on e.dept = d.id;  
select d.name, e.* from dept d left [outer] join emp e on e.dept = d.id;  -- 这条语句与下面的语句效果一样  
-- 右
select d.name, e.* from employee as e right [outer] join dept as d on e.dept = d.id;  
```

##### 自连接查询
当前表与自身的连接查询，自连接**必须使用表别名**。  看成**两张表**实行内连接，外连接！

```mysql  
自连接查询，可以是内连接查询，也可以是外连接查询
SELECT 字段列表 FROM 表A 别名A JOIN 表A 别名B ON 条件 ...; 
  

-- 查询员工及其所属领导的名字  
select a.name, b.name from employee a, employee b where a.manager = b.id;  
-- 没有领导的也查询出来  
select a.name, b.name from employee a left join employee b on a.manager = b.id;  
```

![Pasted image 20230802130401](attachments/Pasted%20image%2020230802130401.png)

#### 联合查询
把**多次查询的结果合并**，形成一个新的查询集，用的较少！

```mysql
SELECT 字段列表 FROM 表A ...
UNION [ALL]
SELECT 字段列表 FROM 表B ...

select * from emp where salary < 5000
union all
select * from emp where age > 50;

```

- UNION ALL 会有**重复结果**，UNION 不会

- 多张表的字段名、类型、数量必须一致才行

- 联合查询比使用or**效率高**，不会使索引失效

![Pasted image 20230802131023](attachments/Pasted%20image%2020230802131023.png)

#### 子查询
SQL语句中**嵌套SELECT语句**，称谓嵌套查询，又称子查询。子查询外部的语句可以是 **INSERT / UPDATE / DELETE / SELECT** 的任何一个。 

```MySQL
SELECT * FROM t1 WHERE column1 = ( SELECT column1 FROM t2);
```

根据子查询结果可以分为：

- 标量子查询（子查询结果为**单个值**）

- 列子查询（子查询结果为**一列**）

- 行子查询（子查询结果为**一行**）

- 表子查询（子查询结果为**多行多列**）

根据子查询位置可分为：

- WHERE 之后

- FROM 之后

- SELECT 之后
##### 标量子查询
子查询返回的结果是**单个值**（数字、字符串、日期等）。  

常用操作符：**- < > > >= < <=**  

```mysql
-- 查询销售部所有员工
select id from dept where name = '销售部';
-- 根据销售部部门ID，查询员工信息
select * from employee where dept = 4;
-- 合并（子查询）  
select * from employee where dept = (select id from dept where name = '销售部');  

-- 查询xxx入职之后的员工信息  
select * from employee where entrydate > (select entrydate from employee where name = 'xxx');  
```

##### 列子查询

| 操作符  | 描述  |
| ------------ | ------------ |
| IN  | 在指定的集合范围内，多选一。因为结果不是一个，所以不是=号  |
| NOT IN  | 不在指定的集合范围内  |
| ANY  | 子查询返回列表中，有**任意一个**满足即可  |
| SOME  | 与**ANY等同**，使用SOME的地方都可以使用ANY  |
| ALL  | 子查询返回列表的**所有值**都必须满足  |

```mysql  
-- 查询销售部和市场部的所有员工信息  
select * from employee where dept in (select id from dept where name = '销售部' or name = '市场部');
-- 查询比研发部 任意一人 工资高的员工信息
select * from employee where salary > any (select salary from employee where dept = (select id from dept where name = '研发部'));
-- 查询比财务部 所有人 工资都高的员工信息
select * from employee where salary > all (select salary from employee where dept = (select id from dept where name = '财务部'));

```

##### 行子查询 
常用操作符：**=, <, >, IN, NOT IN**

```mysql
select * from employee where salary = 12500 and manager =  1; 

-- 查询与xxx的薪资及直属领导相同的员工信息  
select * from employee where (salary, manager) = (12500, 1);  
select * from employee where (salary, manager) = (select salary, manager from employee where name = 'xxx');  
```

##### 表子查询
常用操作符：**IN**  ，常在from之后
```mysql
-- 查询与xxx1，xxx2的职位和薪资相同的员工
select * from employee where (job, salary) in (select job, salary from employee where name = 'xxx1' or name = 'xxx2');
-- 查询入职日期是2006-01-01之后的员工，及其部门信息
select e.*, d.* from (select * from employee where entrydate > '2006-01-01') as e left join dept as d on e.dept = d.id;
```

## 事务
事务是**一组操作的集合**，事务会把所有操作作为一个整体**一起**向系统提交或撤销操作请求，即这些操作要么**同时成功**，要么**同时失败**。

```mysql
-- 1. 查询张三账户余额
select * from account where name = '张三';
-- 2. 将张三账户余额-1000
update account set money = money - 1000 where name = '张三';
-- 此语句出错后张三钱减少但是李四钱没有增加
模拟sql语句错误
-- 3. 将李四账户余额+1000
update account set money = money + 1000 where name = '李四';

-- 查看事务提交方式
SELECT @@AUTOCOMMIT;
-- 设置事务提交方式，1为自动提交，0为手动提交，该设置只对当前会话有效
SET @@AUTOCOMMIT = 0;
-- 提交事务
COMMIT;
-- 回滚事务
ROLLBACK;

-- 设置手动提交后上面代码改为：
select * from account where name = '张三';  
update account set money = money - 1000 where name = '张三';  
update account set money = money + 1000 where name = '李四';  
commit;  
```

操作方式二：

开启事务：

`START TRANSACTION 或 BEGIN TRANSACTION;`

提交事务：

`COMMIT;`

回滚事务：

`ROLLBACK;`

```mysql
start transaction; 
select * from account where name = '张三';
update account set money = money - 1000 where name = '张三';
update account set money = money + 1000 where name = '李四';
commit;
```

开启事务后，只有手动提交才会改变数据库中的数据。  
### 四大特性ACID
- 原子性(Atomicity)：事务是不可分割的最小操作但愿，要么全部成功，要么全部失败

- 一致性(Consistency)：事务完成时，必须使所有数据都保持一致状态

- 隔离性(Isolation)：数据库系统提供的隔离机制，保证事务在不受外部并发操作影响的独立环境下运行

- 持久性(Durability)：事务一旦提交或回滚，它对数据库中的数据的改变就是永久的

### 并发事务

| 问题  | 描述  |
| ------------ | ------------ |
| 脏读  | 一个事务读到另一个事务还没提交的数据  |
| 不可重复读  | 一个事务先后读取同一条记录，但两次读取的数据不同  |
| 幻读  | 一个事务按照条件查询数据时，没有对应的数据行，但是再插入数据时，又发现这行数据已经存在  |

> 这三个问题的详细演示：https://www.bilibili.com/video/BV1Kr4y1i7ru?p=55cd 

并发事务隔离级别：

| 隔离级别  | 脏读  | 不可重复读  | 幻读  |
| ------------ | ------------ | ------------ | ------------ |
| Read uncommitted  | √  | √  | √  |
| Read committed  | ×  | √  | √  |
| Repeatable Read(默认)  | ×  | ×  | √  |
| Serializable  | ×  | ×  | ×  |

- √表示在当前隔离级别下该问题会出现

- Serializable 性能最低；Read uncommitted 性能最高，数据安全性最差

查看事务隔离级别：  

`SELECT @@TRANSACTION_ISOLATION;`  

设置事务隔离级别：  

`SET [ SESSION | GLOBAL ] TRANSACTION ISOLATION LEVEL {READ UNCOMMITTED | READ COMMITTED | REPEATABLE READ | SERIALIZABLE };  `

SESSION 是会话级别，表示只针对当前会话有效，GLOBAL 表示对所有会话有效  

---

# 进阶篇
推荐看推荐的黑马程序猿的MySQL教程。