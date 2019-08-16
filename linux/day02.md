# day02

### 数据操作语言（DML）Data Manipulation Language 

- 说明：在大多数操作数据库中都是增删改

- 准备：一张用于测试的表

  ```sql
   create table star(
   id int auto_increment,
   name varchar(20) not null,
   money float not null,
   province varchar(20) default null,
   age tinyint unsigned not null,
   sex tinyint not null,
   primary key(id)
   )engine=innodb default charset=utf8;
  ```

  

- 插入数据

  - 方式1：不指定字段,添加数据的时候需要指定所有的字段值，

    ```sql
    insert into star values(1,'蒋龙',2556783,'湖南',22,0)
    ```

    [^可以一次性插入多个，每条数据都必须使用()扩起来，使用之间使用逗号隔开]: 
    [^]: 

  - 方式2：指定字段，只需要传递指定字段值，通常使用这个方式，如：

    ```sql
    insert into star (name, money, age, sex, province)
    values("周杰伦", 78278278, 42, 0, "台湾"),
    ("胡歌", 72636633,39,0,"上海");
    ```

    注释：插入数据字段的顺序，与前面指定一定要一致，与数据库里面的字顺序无关。

  - 说明：插入数据不用传值的字段
    - 自增的字段
    - 有默认值
    - 可以为空

- 修改数据：
  - 示例：update star set money=888 where id=3;
  - 警告：修改的时候，一定不要忘了添加条件，否则后果自负

- 删除数据：
  - 示例：delete from star where name="胡歌";
  - 警告：删除操作一定不要了忘了加条件，后果很严重
  - 说明：在真实的项目中，不会真的删除，大多使用逻辑删除

### 数据查询语言（DQL）

- 基本查询：select * from star;
- 指定字段查询：select name, money FROM STAR;
- 过滤重复的记录：select distinct province from star;
  - 说明：使用distinct 指定的额字段不能重复，指定多个字段

- 条件查询：

  - 条件

    | 条件                   | 说明                    |
    | ---------------------- | ----------------------- |
    | >                      | 大于                    |
    | <                      | 小于                    |
    | >=                     | 大于等于                |
    | <=                     | 小于等于                |
    | =                      | 等于                    |
    | ！=或 <>               | 不等于                  |
    | and                    | 并且                    |
    | or                     | 或者                    |
    | [not]  between m and n | [不]在[m,n]的区间       |
    | [not] in ()            | [不]在指定的集合中      |
    | [not] like 条件        | 模糊匹配，%表示任意字符 |
    | is  [not]  NULL        | 是否为空                |

  - 示例：

    ```sql
    select * from star where id > 2;
    select * from star where id >5 and age >30;
    select * from star where age between 30 and 40;
    select * from star where id in (2,4,6);
    select * from star where province like "湖%";
    select * from star where province is null;
    ```

- 结果集排序（order by）

  ```sql
  select name, money from star order by money desc;
  select name, money, age from star order by age asc,money desc;
  ```

  - 说明:
    - 默认是升序asc，降序desc
    - 多个字段进行排序的时候，先安排第一个排序，相同的话再按照第二个进行排序

- 限制结果集（limit）

  ```sql
   select * from star limit 3;#提取3条数据
   select * from star limit 3 offset 2;#跳过两条提取3条数据
   select * from star limit 2,3;#同上
  ```

  - 分页：

    ```sql
    每页 pagesize=10,page表示页码数，请写出对应的查询语句
    第一页：limit 0,10
    d第二页：limit 10,10
    第三页：limit 20,10
    第4页：limit 30,10
    
    page页：limit (page - 1)*pagesize,pagesize
    ```

- 常用的聚合函数

  | 函数  | 说明     |
  | ----- | -------- |
  | count | 统计个数 |
  | sum   | 求和     |
  | max   | 最大值   |
  | min   | 最小值   |
  | avg   | 平均值   |
  |       |          |

  - 示例：

    ```
    
    select count(*)  as c from star;    #可以给查询的字段起别名
    select max(money) as max_money from star;
    ```

- 分组及过滤（重要）（group  by）

  ```sql
  select sex from star group by sex;    #以性别进行分组
  select count(*) as c, sex from star group by sex;#分组以后并统计
  select count(*) as c, province from star group by province having c=1;#分组统计以后过滤
  
  ```

### - ### 多表联合查询,,- 

```
https://blog.csdn.net/huaxiawudi/article/details/82288044      作业     
```

- 创建两张表

  ```sql
  create table user (
  id int(11) not null auto_increment,
  username varchar(20) default null,
  gid int(11) ,
  primary key(id));
  
  
  create table goods (
  id int(11) not null auto_increment,
  name varchar(40) default null,
  price float default null,
  category varchar(20) default null,
  primary key(id));
  ```

- 隐式内连接
  - 说明：查询哪个用户购买了什么商品
  - 示例： select username,name from user,goods where user.gid =goods.id;

- 显示内连接
  - 说明：功能和隐式内连接一样，使用的关键字是join，一定要注意不是where，是on。
  - 示例：select username,name from user join goods on user.gid=goods.id;

- 左外连接

  - 说明：以左边的表为主，主要显示左边的表，右边的表有对应的数据就显示，没有话就显示null
  - 示例：select username,name from user left join goods on user.gid=goods.id;

- 右外连接

  - 说明：会显示右边的所有数据，左表有对应的数据的话就显示，没有的话就是null
  - 示例：select username,name from user right join goods on user.gid=goods.id;

- 记录联合

  - 格式：select 语句1 union select 语句2

  - 示例：select username,name from user right join goods on user.gid=goods.id union

    select username,name from user left join goods on user.gid=goods.id;

  - union all:将两边的查询结果直接拼接到一起

  - union:去重之后进行拼接

    

- 联合更新

  - 示例： update user u, goods g set u.gid=3,g.price=g.price+0.1 where u.gid=g.id and u.id=2;

- 子（嵌套）查询

  - select * from user where gid in (select id from goods);
  - 说明：条件是一个sql语句

  

### 数据事务语言（DTL）

- 说明：用于测试的表他的存储引擎必须是InnoDB

- K开启事务：禁止自动提交

  ```sql
  set autocommit = 0;
  
  ```

  sql

- 提交事务：整个事务过程没有出现问题

  ```sql
  commit;
  ```

- 操作回滚：事务出现了问题，然后进行回滚，事务开始之前的状态

  ```sql
  rollback;
  ```

- **代码**

  ```
  #开启事务
  try:
  #执行相关的操作
  except  Exception as e:
  #操作回滚
  else:
  #提交事务
  ```

  