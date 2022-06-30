## SQL

### 数据定义

```sql
# 创建数据库
create database NAME

# 创建表
create table NAME (
    A date primary key,
    B varchar(32) not null references F(B),
    C char(32) unique,
    D int default (0),
    E numeric(8, 2),    # 小数点前 8 位，小数点后 2 位
    [constraint PK] primary key (A, B),
    [constraint FK] foreign key (B) references F(B),
    [constraint CK] check (A < 2)
)

# 修改表
alter table NAME
    add | change | modify | rename
    column NAME | constraint

# 删除表
drop table NAME

```



### 数据查询

```sql
# 基本语句
select [distinct] ... [as ...]
    # sum, ave, max, min, count
from ...
	# 派生表: (select ...) NAME
where ...
    # 不等于: <>
    # 范围: between and
    # 集合: [not] in, [not] exist
    # 字符匹配: like "%" [escape '\']
    # 空值: is [not] null, ifnull(...)
    # 逻辑运算: and, or
group by ...
having ...
order by [asc | desc] [limit n];

# 连接
A [left] join B on A.x = B.x
    # 等价: select * from A, B where A.x = B.x

```



### 数据更新

```sql
# 插入
insert NAME [(col1, col2, ...)] values (val1, val2, ...) [, (), ...]
insert NAME [(col1, col2, ...)] select ...

# 修改
update NAME
set col1 = <expr> [, col1 = <expr>, ...]
[from ...]    # 与 select 类似
[where ...]

# 删除
delete from NAME
[where ...]

```



### 视图

```sql
# 创建视图
create view NAME
    [(col1, col2, ...)]
as select ...
[with check option]    # 更新的行需要满足 select 的条件

# 删除视图
drop view NAME

# 更新视图
(insert | update | delete from) NAME

```



### 安全

```sql
# 授予权限
grant ... [, ...]
    # alter, insert, delete, select, update
    # create database, create table
    # all privileges
    # role
on <table | view>
to <role | user>
[with grant option]    # 转授权限
[with admin option]    # 转授角色

# 创建/删除角色
create role NAME
drop role NAME

# 收回权限
revoke ... [, ...]
on <table | view>
from <role | user>

# 所有用户: public

```







