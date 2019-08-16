# day08

### 数据控制语言（DCL）

- 查看授权

  - 格式：show grants [for 'user'@'localhost']
  - 示例：show grants [for 'root'@'localhost']
  - 说明：查看指定的用户权限，若不指定用户，则查看的是当前登录的用户

- 创建用户

  - 格式：create user 'user'@'host' identified by 'password'        host 主机名
  - 示例：create user 'user'@'10.20.159.%'  identified by '123456'
  - 自己 create user 'li'@'10.20.159.233'  identified by '123456'
  - 说明：%是通配符

- 用户授权

  - 格式：grant   权限  privilages  on 库.表 to "user"@'host' identified by 'password'
  - 示例： grant all privileges on test.user to 'user'@'10.20.159.%' identified by '123456‘
  - 说明：
    - 权限可以是：insert,delete,update,select, all是所有的权限
    - %表示的是任意主机
    - *表示的是所有的库和表

- 刷新权限：flush privileges

- 取消权限

  - 格式：revoke  权限 privileges on 库.表 from 'user'@'host'

  - 示例：revoke all privileges on test.* from 'user'@'10.20.159.%';


- 删除用户

  - 格式：drop  user 'user'@'localhost'
  - 示例：drop user 'user'@'10.20.159.%';

### 备份和恢复

- 备份：
  - 将数据库中的数据保存到文件中
  - 示例：mysqldump   -u root -p test > test.sql
  - navicate:右键->转储sql文件的

- 恢复：

  - 从保存的sql、文件中，解析执行sql语句

  - 示例：mysql -u root -p test2 < test.sql

    就是练习

### python操作mysql数据库

```python
import pymysql
#pip install pymysql

#1.连接数据库服务器   mysql -h localhost -u root -p 123456
db = pymysql.connect(host="localhost", user="root", password="123456")
print(db)

#2.选择数据库 use test

db.select_db("test")
#3。设置字符集
db.set_charset("utf8")

#3.1创建游标对象，
cursor = db.cursor(cursor=pymysql.cursors.DictCursor)
#4.准备sql语句
sql = 'select id,name,age from star'
#5.执行sql语句
rowcount = cursor.execute(sql)
#结果集中的数量
print(rowcount)
print(cursor.rowcount)
print(cursor.rownumber)
#获取所有的数据(默认的是元祖)
#print(cursor.fetchall())

#获取一条数据
#print(cursor.fetchone())
print(cursor.fetchmany(1))


#关闭游标对象     https://blog.csdn.net/gx864102252/article/details/73017989
cursor.close()
#关闭数据库的链接
db.close()
```

- 事务代码

  ```python
  import pymysql

  db = pymysql.connect(host="localhost", user="root", password="123456")

  db.select_db("test")

  db.set_charset("utf8")

  cursor = db.cursor()

  #开启事务
  db.begin()
  try:
      sql = "insert into user (username) values('goudan')"
      #对于DML:返回一个收影响的行数
      rowcount = cursor.execute(sql)
  except Exception as e:
      print(e)
      #操作回滚
      db.rollback()

  else:
      #开始真正的提交事务
      db.commit()
      print(rowcount)
      #最后插入数据的自增的id
      print(cursor.lastrowid)

  cursor.close()
  db.close()



  请写出使用pymysql操作MySQL进行转账的操作，要求id为1的用户向id为2的用户转账200元，如果转账过程发生异常，则回滚转账 操作
  import pymysql 
   conn = pymysql.Connect(
      host='10.12.153.39', 
      port=3306,
      user='root',
      password='123456',
      database='mydb',
      charset='utf8', 
  ) 
   cursor = conn.cursor()
    # 获取游标对象 
  sql1 = "update account set balance=balance-200 where id=%d" 
  sql2 = "update account set balance=balance+200 where id=%d" 
  try:
      cursor.execute(sql1%1)    
      # 5 / 0
      cursor.execute(sql2%2)
      conn.commit()
      print("转账成功！") 
  except:
      conn.rollback()
      print("由于ATM机故障，转账失败~~~") 
  finally:
      cursor.close()
      conn.close()

      
  请写出注册用户、登录的代码，要求使用pymysql操作MySQL
  import pymysql 
   def getConn():
     # 获取连接的函数
      conn = pymysql.connect(
          host='localhost',
          port=3306,
          user='root',
          password='123456',
          database='mydb', 
          charset='utf8'
      )
      return conn 

   def register(username,password):
     # 注册函数
      conn = getConn()
      cursor = conn.cursor()
      try:
          sql = "insert into user(username,password)values('{}','{}')".format(username,password)
          cursor.execute(sql)
          conn.commit()
          print("注册成功！")
      except Exception as e:
          conn.rollback()
          print("注册失败，失败原因：",e)
      finally: 
          cursor.close()
          conn.close()
   def login(username,password): 
    # 登录函数
      conn = getConn()
      cursor = conn.cursor()
      try:
          sql = "select username from user where username='{}' and password='{}'".format(username,password)
          cursor.execute(sql)
          item = cursor.fetchone()
          conn.commit()
          if item: 
              print("恭喜",item[0],"登录成功！")
          else:
              print("用户名或密码错误！")
      except Exception as e:
          conn.rollback()
          print("登录发生异常，异常原因：",e)
      finally:
          cursor.close()
          conn.close()

     

  ```

### Redis简介 

- 百科：Redis是一个开源的使用ANSI [C语言](https://baike.baidu.com/item/C%E8%AF%AD%E8%A8%80)编写、支持网络、可基于内存亦可持久化的日志型、Key-Value[数据库](https://baike.baidu.com/item/%E6%95%B0%E6%8D%AE%E5%BA%93/103728)，并提供多种语言的API。从2010年3月15日起，Redis的开发工作由VMware主持。从2013年5月开始，Redis的开发由Pivotal赞助。 
- 说明：是一个非关系型数据库，经常会用作缓存，消息中间件的操作
- 网址：www.redis.cn   中文网站 <https://www.runoob.com/redis/redis-tutorial.html>
- 优势（面试）
  - 存储既可以在内存中，也可以持久化存储
  - 数据类型非常丰富，字符串，哈希，列表,集合，有序集合等
- 端口：6379        MYSQL 3306     HTTP:80 HTTPS:443  SSH:22  FTP:21

### redis 安装

- 命令安装：sudo apt-get install redis-server,版本比较低，客户端没有提示信息

- 源码安装：可以选择哪一个版本

  ```
  https://www.cnblogs.com/mayyan/p/7717994.html
  
  ```

- windows下面启动redis

  ```
  redis-server redis.windows.conf#启动redis服务器 当前文件所在位置

  redis-server redis.windows.con 文件下设置密码  requried passswd
  ```

- 使用

  ```
  redis-cli.exe#启动客户端  当前文件所在位置
  ```


- 给大家推荐一个可视化工具

  ```
  redisplus
  ```

### redis常用命令

- 管理命令

  | 命令      | 说明                                     |
  | --------- | ---------------------------------------- |
  | ping      | 测试连接情况，默认回复一个pong           |
  | exit/quit | 退出客户端                               |
  | auth      | 身份认证                                 |
  | config    | 配置命令，用来查看选项或者设置相关配置的 |
  | info      | 查看redis服务器相关信息                  |
  | command   | 查看可用的命令                           |
  | select    | 选择库0-15,默认的是在0数据库下面         |
  | flushdb   | 清空当前的库，慎用                       |
  | flushall  | 清空所有的库，特别慎用                   |
  | save      | 前台执行持久化的时候使用(会阻塞)         |
  | bgsave    | 后台执行持久化操作（不会阻塞）           |
  |           |                                          |

- keys（键）

  | 命令    | 说明                                                         |
  | ------- | ------------------------------------------------------------ |
  | exists  | 判断指定的键是否存在，如果存在返回1，不存在返回0             |
  | keys    | 查看指定格式的键，*表示模糊匹配                              |
  | del     | 删除指定的键                                                 |
  | ttl     | 查看指定的键剩余的有效时间，-1表示永久有效，-2表示键不存在，单位为秒 |
  | expire  | 设置指定的有效时间，单位是秒（重要）                         |
  | persist | 删除指定键的有效时间，之后变成永久的                         |
  | move    | 将指定的键移动到指定的库                                     |
  | rename  | 修改指定键的名字                                             |

- 字符串

  | 命令   | 说明                                 |
  | ------ | ------------------------------------ |
  | set    | 设置键值对的数据                     |
  | get    | 通过键值获取值                       |
  | mset   | 设置多对的键值对                     |
  | mget   | 获取多对的键值对                     |
  | getset | 设置键值对，并返回原来的值           |
  | setex  | 设置键并设置过期时间                 |
  | append | 键值对追加内容，如果没有的话就设置值 |
  | strlen | 返回指定字符串的长度                 |
  | incr   | 数字值加1                            |
  | decr   | 数字值减1                            |
  | incrby | 数字值加上一个指定的数               |
  | decrby | 数字值减去一个指定的数               |






### mysql想要在windows黑打开需要设置环境变量

- 1.要找到mysql.exe的应用程序（也就是安装好的mysql），复制这个应用程序的路径

  例如（C:\Program Files\MySQL\MySQL Server 5.7\bin）

- 2.右键-》系统属性-》高级系统设置-》环境变量-》系统变量-》path在后面追加上面复制的路径
- 3.重新打开终端即可。

### 数据的结构的说明

- 结构化数据：就是表数据
- 半结构化数据：xml和json     XML常用在微信小程序开发
- 非结构化数据：图片，音频，视频