# day02

### 1  linux学习什么?

常用的命令(背会)

软件安装(熟练)

系统的服务(熟悉)

服务器的架构(了解)

### 2  linux该如何学习?

- 前期不要问那么的为什么？后期懒得问了
- 一个知识点先尝试理解下来，实在不行就背会
- 一个知识点记不住，记十遍

### 3  操作系统的介绍

- 定义：严格来讲操作系统就是一个内核，是一套管理硬件的软件组件
- 常识：平常所说的操作系统其实是发行版，包含（内核，桌面环境，常用软件）
- 内核：
  - windows :  nt
  - linux:linux


- 发行版：
  - ​	桌面版本：windows desktop, ubuntu desktop(ubuntu kylin|deepin),mac os
  - ​    服务器版本：windows server , Linux(ubuntu, centos,redhat)系列，unix系列
  - ​    移动端：Android,IOS, Symbian,windows phone, ali os

### 4  linux系统介绍

- 经历了5大支柱
  - 基于unix操作系统
  - 参考了minix操作系统
  - GNU计划
  - POSIX标准
  - 互联网的发展
- Linux发行版
  - 桌面版本：ubuntu,linux  mint, debian,redhat,open suse
  - 服务器：redhat, centos,debian,ubuntu

### 5  终端的使用

- 启动
  - 在任意地方，打开终端
  - ctrl + atl + t
  - 搜索应用点击启动
  - 锁定到启动器，直接打开即可
- 配置
  - 放大：ctrl +
  - 缩小：ctrl -

### 6  常识命令

- ~  加目录
- ls:查看指定目录下面的内容
- pwd:查看当前目录路径( print work directory)
- cd: 切换工作目录(change  directory)
- alphabetically   (阿法白体口瑞)  按字母顺序排序

### 7  获取帮助的命令(最好不要用,百度就可以)

- help使用
  - 说明：大多命令都有--help,可以用来查看帮助信息
  - 示例：ls --help
  - ls [选项]... [文件]...
- man使用
  - man是一个命令，manual的缩写，查看系统中标准的文档（比help更好）
  - 使用：man ls

| 命令     | 说明     |
| -------- | -------- |
| q        | 退出查看 |
| 空客     | 下一页   |
| pageup   | 上翻一页 |
| pagedown | 下翻一页 |

### 8  文件系统

- 说明：

  文件系统就是操作磁盘或者分区的上的文件的方法和数据结构，也就是存储设备上面的组织文件的形式，

  操作系统中管理和存储文件的的软件管理机构称为文件管理系统，简称文件系统

- 常见的文件系统：

  - fat16(ms-dos16.x), 最大分区为2G
  - fat32(windows 95),单个文件最大为4G，性能比较弱，容易产生碎片
  - ntfs(windows nt),没有最大的4g限制，比fat32更加稳定
  - ext4(linux),扩展性的日志文件系统（重点）
  - hfs[+])(mac),苹果设备文件的系统
  - exfat(mac/wind),支持大于4g的单个文件，适合闪存

### 9  根目录的结构

- 说明:   /   linux和windows的文件系统是不一样的,目录结构的差别非常大,顶层是没有c/d等盘符,而是从/开始,只有/,没有上级目录,它处于目录结构的最顶端
- 根目录

| 目录        | 说明                                              |
| ----------- | ------------------------------------------------- |
| /bin        | 大多数的操作命令都在这个里面(binary)              |
| /boot       | 系统启动的相关文件                                |
| /cdrom      | 挂载光盘的目录                                    |
| /dev        | 设备文件(一切设备皆文件)                          |
| /etc        | 配置文件目录(重要)                                |
| /home       | 普通用户的家目录,一个用户应该对应一个文件夹       |
| /lib        | 库文件                                            |
| /lib64      | 64位的库文件                                      |
| /lost+found | 系统出现异常时候保存的信息,以便恢复               |
| /media      | 自动识别设备的挂载点                              |
| /mnt        | mount,专门手动挂载的目录                          |
| /opt        | option,通常安装可选的软件                         |
| /proc       | 虚拟文件系统,用来映射硬件信息                     |
| /root       | 超级用户的rootde家目录                            |
| /run        | 系统运行的文件,比如:进程文件                      |
| /sbin       | 超级用户使用的命令                                |
| /snap       | ubuntu 自己搞的软件包管理目录                     |
| /srv        | service,本机提供的数据或者服务存放的目录          |
| /sys        | 类似于proc,映射内核的信息                         |
| /tmp        | 保存随时可以销毁的临时文件                        |
| /usr        | 之前和/home一样,现在安装软件 unix system resource |
| /var        | 存放系统产生的不可销毁的文件,比如:日志文件        |

### 10 vim编辑器

- 简介:  vi是linux自带的终端编辑器,后来出现一个加强版vim,被誉为"终端编辑器之神"

- 安装: sudo apt-get install vim

- 说明:所有操纵都是在终端完成的,需要切换不同的工作模式来完成不同的操作

- 工作模式:

  - 正常模式(命令模式)

    | 命令            | 说明                                       |
    | --------------- | ------------------------------------------ |
    | vim  filename   | 打开/新建一个文件夹                        |
    | ESC按键         | 从插入模式切换到正常模式                   |
    | !v              | 打开使用vim最后的文件                      |
    | 光标定位        |                                            |
    | vim filename +n | 打开文件,将光标定位到n行,若不写n定位到行尾 |
    | ngg             | 定位到n行,若不写n定位到首行                |
    | G               | 直接定位到尾行行首                         |
    | ctrl+f          | 下翻一屏                                   |
    | ctrl+b          | 上翻一屏                                   |
    | ctrl+d          | 下翻半屏                                   |
    | ctrl+u          | 上翻半屏                                   |
    | 0               | 定位到行首                                 |
    | ^(抑扬符)       | 定位到第一个非空白符                       |
    | $               | 定位到行尾                                 |
    | k               | ↑                                          |
    | j               | ↓                                          |
    | h               | ←                                          |
    | l               | →                                          |
    | 内容操作        |                                            |
    | nx              | 向右删除n个字符,若不写n则删除一个字符      |
    | nX              | 向左删除n个字符,若不写n则删除一个字符      |
    | ndd             | 剪切光标开始的n行,若不写n则剪切是一行      |
    | p               | 粘贴                                       |
    | nyy             | 复制光标开始的n行,若不写n则是一行          |
    | u               | 撤销                                       |
    | ctrl+r          | 反撤销                                     |


  - 插入模式(输入模式)

    | 命令 | 说明                          |
    | ---- | ----------------------------- |
    | i    | 在光标的位置插入数据(常用)    |
    | I    | 在光标所在的行首插入          |
    | a    | 在光标前一个字符插入数据      |
    | A    | 在行尾插入数据                |
    | o    | 在光标的下一行插入一个空行    |
    | O    | 在光标的上一行插入一行        |
    | s    | 删除光标所在字符,开始插入数据 |
    | S    | 删除光标所在的行,开始插入数据 |

  - 单行模式(编辑模式):完成整体文件操作以后的保存,输入":"

    | 命令                | 说明                                            |
    | ------------------- | ----------------------------------------------- |
    | shift+z+z           | 保存退出的快捷键                                |
    | :q                  | 退出                                            |
    | :wq                 | 保存并退出                                      |
    | :w filename         | 另存为                                          |
    | :q!                 | 强制退出不保存修改                              |
    | :w!                 | 强制保存                                        |
    | :e!                 | 回到上一次保存状态                              |
    | 光标定位            |                                                 |
    | :n                  | 将光标定位到第n行                               |
    | 内容查找            | :                                               |
    | /内容               | 查找指定内容,之后,n表示下翻,N上翻               |
    | ?内容               | 查找指定内容,n表示下翻,N上翻                    |
    | 内容替换            |                                                 |
    | :%s/原内容/新内容/g | 使用新内容替换原内容,g不加的时候,每行只替换一个 |
    | :s/a1/a2/g          | 将当前光标所在行中的所有a1用a2替换              |
    | :n1,n2s/a1/a2/g     | 将文件中n1到n2行中所有a1都用a2替换              |
    | :g/a1/a2/g          | 将文件中所有的a1都用a2替换                      |
    | vim配置             |                                                 |
    | :set  nu[mber]      | 显示行号设置                                    |
    | :set nonu[mber]     | 隐藏行号                                        |
    | :set  tabstop=4     | 一个tab相当于4个空客                            |
    | :set  mouse=a       | 启动鼠标得点击功能                              |
    |                     |                                                 |
    |                     |                                                 |
    |                     |                                                 |

    - vim配置得使用

      配置:如果使用在本编辑器中写上面四个命令的话,只会对当前文件生效,关闭这个文件后就失效了,可以永久的配置vim的配置

      - 在用户的家目录下面创建一个 .vimrc

      - 添加配置内容即可

        ```
        set number
        set tabstop=4
        set mouse=a
        ```

        非法关闭的时候,再次打开会出现问题

        会产生一个.swp交换文件,是一个隐藏文件,不想要这个警告的话,可以删除.swp文件

# day03

### 1.使用命令

- 命令格式

```
命令 [选项] [参数]

[]:代表可有可无
命令,选项,参数,都是以空格分开的
```
- 示列

  ```
  ls -l /etc
  ```

- ls:查看指定目录下面的文件,如果不指定参数的话,默认查看当前目录的内容

  - 常用的选项

    | 选项 | 说明                        |
    | ---- | --------------------------- |
    | -l   | 列表显示详细信息            |
    | -a   | 显示所有的文件,包括隐藏文件 |
    | -h   | 人性化显示文件大小          |

### 2. -l选项显示结果介绍

```
类型和权限  引用数  用户  用户组  大小  月  日  年份(近的话显示具体时间)  名称
```

#### 1对文件类型进行解释

| 类型 | 说明         |
| ---- | ------------ |
| -    | 普通文件     |
| d    | 目录文件     |
| l    | 链接文件     |
| c    | 字符设备文件 |
| b    | 块设备文件   |
| s    | 套接文件     |
| p    | 管道文件     |
|      |              |

#### 2 cd:切换目录,tab可以自动补全

| 符号 | 说明               |
| ---- | ------------------ |
| .    | 当前目录           |
| ..   | 上一级目录         |
| /    | 根目录             |
| ~    | 家目录             |
| -    | 上次切换之前的目录 |
|      |                    |
|      |                    |

#### 3  clear:  清空屏幕

| 组合   | 说明                       |
| ------ | -------------------------- |
| ctrl+l | 清除屏幕,clear快捷键       |
| ctrl+a | 将光标定位到输入命令的开头 |
| ctrl+e | 将光标定位到输入命令的末尾 |
| ctrl+c | 结束当前的程序             |
|        |                            |

#### 4  alias:别名操作

| 操作             | 说明                 |
| ---------------- | -------------------- |
| alias            | 查看所有命令的别名   |
| alias  ll        | 查看指定别名的命令   |
| type xx          | 查看xx是否是有效命令 |
| alias  xx="命令" | 给命令起个别名叫xx   |
| unalias  xx      | 取消别名是xx的命令   |

#### 5 history:查看历史的命令

| 操作        | 说明               |
| ----------- | ------------------ |
| history     | 查看历史命令       |
| history  n  | 查看最近n条命令    |
| history  -c | 清空所有的历史命令 |
| ↑↓          | 可以翻看历史命令   |

- 说明

  - 查看历史命令保存的文件:   .bash_history          <br>用 sudo    echo  $HISTFILE命令查看

  - 该文件记录的是本次登入之前的命令,登入之后的命令在缓冲区,注销以后,把这次登录保存到历史文件中

  - 配置文件: ~/.bashrc

    HISTSIZE:缓冲区最大命令数

    HISTFILESIZE:文件保存最大命令数

### 3 文件操作相关的命令(重要)

#### 1 查看文件命令

| 命令          | 说明                                                |
| ------------- | --------------------------------------------------- |
| cat  + 文件名 | 从上到下显示文件的全部内容,(在文件目录下查看)       |
| nl            | 从上到下显示文件的全部内容,会显示行号               |
| tac           | 从下到上显示显示文件的全部内容                      |
| head          | 查看开头指定的行数(默认的是10行),如head -5 filename |
| tail          | 查看末尾指定的行数(默认的是10行),如head -5 filename |
| wc            | 统计文件内容,   行数,单词,字符数,文件名字           |
| more          | 一点一点的查看文件内容                              |
| less          | 一点一点的查看文件内容                              |

#### 2 more  和 less  使用:

- 显示一屏就会停止
- q可以退出查看
- enter可以下翻一页
- 空格可以下翻一页
- 查看使用的more,完毕以后自动退出,less不会自动退出
- less可以使用↑↓键进行查看,more不可以
- 后面有几个管道需要使用:   ls/etc |more

### 4文件及目录

##### 相关命令

| 命令      | 说明                                                         |
| --------- | ------------------------------------------------------------ |
| touch     | 新建文件,可以一次性创建多个                                  |
| rm  [-i]  | 删除文件或者目录,也可以一次性删除多个,-i会显示提示信息 , -r表示的是递归删除,  删除的时候一定要注意,写删除的时候一定要看好参数和选型(-i,-r,-f)<br>可以删除非空目录 |
| cp        | copy的是文件和目录,可以一次性copy多个,copy目录 一定要加-r  <>     语法:  cp   文件名   路径/新文件名 |
| mv        | 移动文件,可以一次性移动多个                                  |
| mkdir     | 新建目录,可以一次性创建多个,<br>mkdir  aaa  bbb  ccc         |
| mkdir  -p | 递归创建目录<br>mkdir  a/b/c  -p                             |
| rmdir     | 删除目录,也可以删除多个,不可以删除非空目录                   |

- 说明:
  - -r : 表示递归操作,用于目录操作
  - -p:(mkdir)表示创建中间目录
  - -f: 表示强制操作,常用于删除操作
  - -i :显示提示信息

### 5用户及用户组的

说明:linux是一个多用户的操作系统,

例如:4个用户,分别是root,www,ftp,mysql在同一时间root用户可以查看日志,管理系统.www用户修改自己的网页程序,ftp用户上传软件到服务器.mysql用户在执行自己的SQL语句

#### 1相关命令

| 命令     | 说明                                                         |
| -------- | ------------------------------------------------------------ |
| whoami   | 查看当前用户的用户名                                         |
| useradd  | 创建用户   -d指定他的家目录,  -m创建家目录,-s  shell的登录<br>sudo  useradd  -d   /home/新用户名   -m    新用户名 |
| userdel  | 删除用户,坑,-r(邮件池)                                       |
| passwd   | 设置指定用户的密码,不指定的时候,设置的当前用户密码<br>sudo  passwd  用户名 |
| su-      | 切换指定的用户,不指定的话,直接切换到root用户,-连带环境一起切换    exit 退出<br>su -  用户名 |
| sudo     | 以root身份去执行命令<br>sudo  vim  /etc/sudoers     <br>sudo update-alternatives  --config |
| groupadd | 创建组的                                                     |
| groupdel | 删除组                                                       |

作业:用户组和用户的关系

#### 2涉及到文件的

| 文件        | 说明                                            |
| ----------- | ----------------------------------------------- |
| /etc/passwd | 系统中所有的用户信息<br>cat  /etc/passwd        |
| /etc/shadow | 系统中用户的密码信息<br>sudo tail   /etc/shadow |
| /etc/group  | 系统中用户组的信息                              |

### 6文件权限(重要)

- 说明:在linux下面,所有文件都会涉及到权限,分为三组,所有者,所属组,其它用户

- 权限:  所有权限分为三种,分别是可读(r),  可写(w)  ,可执行(x),  -没有权限

- 查看:ls -l        结果集中第一页,除去文件类型的部分,三个为一组,分别对应所有者,所属组,其它用户

- 修改:  chmod,命令格式   chmod

  | 选项 | 说明             |
  | ---- | ---------------- |
  | 身份 |                  |
  | u    | 所有者(user)     |
  | g    | 所属组(group)    |
  | o    | 其他用户(others) |
  | a    | 所有身份(all)    |
  | 操作 |                  |
  | +    | 添加权限         |
  | -    | 取消权限         |
  | =    | 设置权限         |
  | 权限 |                  |
  | r    | 可读             |
  | w    | 可写             |
  | x    | 可执行           |

  给2.c的文件所有者添加可执行的权限

  sudo  chmod   u+x  2.c(不推荐)

- 本质:  使用了一组八进制的来表示的,  如:  0755,  展开如下转为二进制:  0755====>>  0b   111      101     101<br>                                所有者     所属组      其他用户

  简化:   sudo    chmod   0777  2.c


- 掩码:   创建文件的默认权限  (扩展)

  - umask:查看

  - umak: 0022  修改

  - 说明:  目录文件的权限直接就是掩码取反,普通文件

    0002==>ob  000   000   010====>取反    111  111  101   775

### 7连接文件

- 查看:ls -l   如果第一列的文件类型是l的话就是一个连接文件
- 命令: ln
- 作用:   创建一个文件或者目录的连接
- 格式:  ln  [-s]  原文件   链接文件
- 分类:   
  - 硬链接:   (几乎不用)不可以给目录创建,不可以夸文件系统
  - 软连接(重要):   创建要加-s  ,相当于windows的快捷方式
    - 可以给目录创建
    - 可以夸文件系统


# day04

### 1压缩和解压

- zip/unzip,   文件后缀.zip

```shell
touch  1.text  2.text  3.text    #创建文件
zip   新文件名.zip   要压缩的文件
zip   1.zip   1.text   #压缩

unzip  1.zip   #zip解压
zip  123.zip   *.text   #压缩所有文件
```

- gzip/gunzip  ,文件后缀.gz    只能压缩单个文件,不能是多个或者是目录

  ```shell
  gzip  1.text  #压缩1.text为  1.text.gz  原文件会消失
  gzip  -c  2.text >  2.text.gz   #原文件会保留

  gunzip 1.text.gz    #解压
  gunzip  -c  1.text.gz  >  1.text   #功能同上,原文件保留

  gzip  -d   1.text.gz  #也可以进行解压
  ```

- bzip2/bunzip2, 文件后缀bz2 ,也只能是压缩单个文件,不能是多个或者是目录

  ```shell
  bzip2  3.text   #压缩3.text  但是原文件会消失
  bzip2  -c  2.text >  2.text.bz2  #功能同上,原文件保留

  bunzip2  3.text.bz2  #解压3.text.bz2   原文件会消失
  bunzip2  -c  1.text.bz2  >  1.text   #功能同上,原文件保留

  ```

- tar  用于打包和解包,后缀为.tar

  | 选项      | 说明                           |
  | --------- | ------------------------------ |
  | -c        | 创建新的包                     |
  | -x        | 解包                           |
  | -t        | 检查包(不解包)                 |
  | -f        | 指定操作文件                   |
  | -v        | 显示相关信息                   |
  | -z        | 调用gzip/gunzip进行压缩或解压  |
  | -j        | 调用bzip2/bunzip进行压缩或解压 |
  | -C        | 指定压缩位置                   |
  | --exclude | 排除指定文件                   |

  基本使用:

  ```shell
  tar -cvf  123.tar   *.text  #将所有的text文件打包成123.tar
  tar -tf  123.tar            #查看包中的文件
  tar  -xvf  123.tar          #解包
  tar  -zcvf   123.tar.gz  *.text  --exclude 3.text #打包并解压排除3.text
  tar  -zxvf   123.tar.gz   #解压解包
  ```

### 2 网络服务#

- ping:  检查网络的连通性 ,  -c 可以指定发送测试数据包的数量<br>ping  www.baidu.com  -c  5 



- ifconfig :  查看或者设置网卡信息的
  - if config  网卡名称  up|down     关闭或开启网卡

### 3 资源监测#

- free:  查看内存使用情况
  - free  -h :人性化显示内存情况
  - swap: 交换分区
- df: 查看磁盘使用情况
- netstat: 网络端口使用情况
- w: 正在做的事情
- top: 是w的详细信息


### 4 进程管理

- ps:查看进程状态的信息

  | 选项 | 说明                         |
  | ---- | ---------------------------- |
  | -e   | 显示所有进程                 |
  | -f   | 显示完整的格式               |
  | a    | 显示所有进程                 |
  | u    | 以用户为主进行显示           |
  | x    | 结合a一起使用,现实完整的信息 |

  ​	ps  -ef         #显示所有进程

  ​	ps  -ef |  grep    ssh     #正则刷选进程(重点)

  ​	kill:  用来结束进程的

  ​	sudo  kill    进程pid       #关闭进程

  ​	sudo kill   -9   进程的pid   #强制杀掉这个进程

  ​	出现什么情况才杀死进程:当你启动软件的时候,报错了,端口被占用了的时候

### 5 软件安装

#### 1 方式一: 

-  专门的命令进行安装,无需考虑软件包的依赖关系

  - debain:  apt-get

  - redhat系列:  yum(centos)

  - 常用的操作

    | 操作    | 说明                 |
    | ------- | -------------------- |
    | install | 安装软件包           |
    | remove  | 移除软件包           |
    | update  | 更新软件包的列表信息 |
    | upgrade | 进行一次系统更新     |

    openssh-server   远程服务连接软件

  - 安装实列:  sudo  apt-get   install  openssh-server

  - sudo apt-get upgrade       #安装包全部更新

  - 使用:  sudo service  sshd     start|stop 连接:  ssh  用户名@ip地址



- 更改为阿里源操作:

  https://opsx.alibaba.com/mirror

  阿里云镜像

  ```ini
  deb http://mirrors.aliyun.com/ubuntu/ xenial main
  deb-src http://mirrors.aliyun.com/ubuntu/ xenial main

  deb http://mirrors.aliyun.com/ubuntu/ xenial-updates main
  deb-src http://mirrors.aliyun.com/ubuntu/ xenial-updates main

  deb http://mirrors.aliyun.com/ubuntu/ xenial universe
  deb-src http://mirrors.aliyun.com/ubuntu/ xenial universe
  deb http://mirrors.aliyun.com/ubuntu/ xenial-updates universe
  deb-src http://mirrors.aliyun.com/ubuntu/ xenial-updates universe

  deb http://mirrors.aliyun.com/ubuntu/ xenial-security main
  deb-src http://mirrors.aliyun.com/ubuntu/ xenial-security main
  deb http://mirrors.aliyun.com/ubuntu/ xenial-security universe
  deb-src http://mirrors.aliyun.com/ubuntu/ xenial-security universe

  ```

  - 备份文件：sudo mv /etc/apt/sources.list  /etc/apt/sources.list.bak
  - 新建软件：sudo vim /etc/apt/sources.list      
  - 更新软件包的列表信息：sudo apt-get update

  ####  方式二:

    使用特定的安装包命令来进行安装,考虑包的依赖

  - debain:dpkg的命令,  要安装的软件必须是后缀为.deb

  - redhat:rpm的命令 ,   软件后缀是.rpm

  - 常用选项

    | 命令 | 说明               |
    | ---- | ------------------ |
    | -i   | 安装               |
    | -r   | 卸载               |
    | -l   | 查看软件信息       |
    | -L   | 查看软件的安装目录 |

    ```shell
    sudo dpkg -i wps-office_10.1.0.5672~a21_amd64.deb 

    sudo unzip wps_symbol_fonts.zip -d /usr/share/fonts/

    ```

    -    查看所有已安装的软件： dpkg -l
    - 按关键字查看：dpkg -l |grep *<软件的关键字>* 

  - 使用:sudo  dpkg  -i   软件包名 

  - sodo  unzip   软件包名.zip  -d  /usr/share/fonts/

  - dpkg: 无法恢复的致命错误，中止：
     fork 失败: 无法分配内存

  #### 3方式三: 

- 源码安装,  需要对源码进行编译进行安装

  - 安装步骤
    - 配置configure

      ./configure --prefix=/usr/local/nginx/

    - 编译:make

    - 安装:make install

  - 使用实列:安装nginx

    ```shell
    tar -zxvf nginx-1.13.7.tar.gz #解压
    cd nginx-1.13.7/#解压之后会有一个详细的文件夹，进入到文件夹
    ./configure --prefix=/usr/local/nginx/#配置到这个地方
    make#编译
    sudo make install #安装
    cd  /usr/local/nginx/sbin/
    sudo ./nginx     #启动nginx
    ```


    #如果端口被占用，
    ps -ef | grep nginx
    sudo kill -9 pid
    
    ​```
    示列:安装nginx

# day05

### 1 shell

- shell 是一个用c语言编写的程序,他是用户使用linux的桥梁,shell即是一个命令语言也是程序涉及语言,是一种服务器语言,
- shell脚本:  是一种shell编写的脚本程序
- shell解析器类型:
  - ash,csh,bash等
  - 查看可用的shell:  cat   /etc/shell         
  - 查看当前:  echo    $SHELL
- shell脚本
  - 指定shell解释器执行当前脚本
    - 创建一个1.sh文件,添加内容echo"hello  shell"
    - 执行bash  1.sh,  脚本的权限不需要可执行的权限
  - 自解析的shellj脚本
    - 创建一个2.sh,在开头加#!  /bin/bash/,后面写shell的内容
    - 执行的时候会出现权限不够,chmod  0777  2.sh  或 chmod 0755  2.sh  或chmod +x  2.sh
    - 执行./2.sh

### 2 变量的定义  

- 变量的定义: name="xxx" , =两边不能有空格
- 打印变量: echo  $name或者echo    ${name}
- 销毁变量: unset  name ,   销毁以后,变量就不会再使用了
- 定义常量: readonly  pi=3.14    修改常量会报错

### 3 变量分类

- 本地变量:只使用于本地当前脚本的变量

- 环境变量: (重点) 通常整个系统都可以使用的变量叫环境变量,一般都是大写的

  - 查看系统的环境变量:env

  - 查看指定的环境变量:echo $PATH

  - 想要让一个脚本在哪里都可以执行,一般将脚本所在的目录,放到PATH

    - 临时:export  PATH=$PATH:当前脚本脚本路径
    - 永久:
      - 系统:/etc/profile
      - 用户:在家目录下面有一个.bashrc隐藏文件,
      - vim  .bashrc   将export  PATH=$PATH:当前脚本脚本路径   放在脚本的末尾
      - 让所有的文件都生效: source  ~/.profile

    ​

- 位置变量:

  - $0: 表示脚本的名字
  - $1-9: 表示传递脚本的参数
  - $*:匹配所有的参数

- 特殊变量:

  - $#: 传递给参数的个数
  - $?:  上次执行命令的结果,0代表成功,错误会有对应的数字来表示

### 4 #元字符

| 元字符  | 作 用                                                        |
| ------- | ------------------------------------------------------------ |
| *       | 前一个字符匹配 0 次或任意多次                                |
| .       | 匹配除换行符外的任意一个字符                                 |
| ^       | 匹配行首。例如，^hello 会匹配以 hello 开头的行               |
| $       | 匹配行尾。例如，hello& 会匹配以 hello 结尾的行               |
| []      | 匹配屮柄号屮指定的任意一个字符，而且只匹配一个字符。例如.[aoeiu]匹配任意一个元音字母， [0-9] 匹配任意一位数字，[a-z][0-9] 匹配由小写字母和一位数字构成的两位字符 |
| [^]     | 匹配除中括号中的字符以外的任意一个字符。例如，[^0-9] 匹配任意一位非数字字符，[^a-z] 匹配任意一位非小写字母 |
| \       | 转义符，用于取消特殊符号的含义                               |
| \{n\}   | 表示其前面的字符恰好出现 n 次。例如，[0-9]\{4\} 匹配4位数字，[1][3-8][0-9]\{9\} 匹配手机号码 |
| \(n,\}  | 表示其前面的字符出现不少于 n 次。例如，[0-9]\{2,\} 匹配两位及以上的数字 |
| \{n,m\} | 表示其前面的字符至少出现 n 次，最多出现 m 次。例如，[a-z]\{6,8\} 匹配 6〜8 位的小写字母 |

### 5 数字类型

- 定义变量或者赋值,默认的都是普通的字符,即使你是数字或者运算符

- 若想要进行运算的时候,前面需要加  let

- 示列

  ```shell
  a=1
  let a=a+2
  echo $a
  ```

### 6 字符串类型

- 单引号:字符都会保存原样,不会被解析
- 双引号:其中变量会被解析,特殊字符不会被解析($,",  \  )
- 反引号:其中作为命令来执行
- 长度的统计:  echo  ${#name}
- 字符串提取:echo ${name:2:3}   从下标2开始提取三个字符


### 7 数组类型

- 定义:a=(1 2 3)
- 成员访问:  echo   ${a[1]}
- 所有成员:  echo   ${a[*]}
- 个数统计:   echo   ${#a[@]}

###  8 各种运算

- test: 测试真假

  ```shell
  if test 1 -lt 2;then      #lt小于
  	echo "ok"
  fi

  if [ 1 -lt 2 ];then
  	echo "True"
  fi

  ```

  | 符号 | 说明     |
  | ---- | -------- |
  | -lt  | 小于     |
  | -le  | 小于等于 |
  | -gt  | 大于     |
  | -ge  | 大于等于 |
  | -eq  | 等于     |
  | -ne  | 不等于   |

- 逻辑判断

  | 符号 | 说明                                 |
  | ---- | ------------------------------------ |
  | -a   | 逻辑与(and),  也可以使用两个&&来代替 |
  | -o   | 逻辑或(or),  也可以用两个\|\|代替    |
  | !    | 逻辑非(not)                          |

  ```shell
  if [ 1 -lt 3 -a 2 -lt 3 ];then
  	echo "ok"
  fi

  if [ 1 -lt 3 ] && [ 2 -lt 3 ];then
  	echo "ok"
  fi

  if [ ! 1 -gt 3 ];then
  	echo "ok"
  fi
  ```

### 9 分支结构

- if -elif-else-fi     如下

  ```shell
  if [ 1 -gt 2 ];then
  	echo "xx"
  elif [3 -gt 2 ];then
  	echo "xxx"
  else
  	echo "tt"
  fi
  ```

- case -in-esac

  ```shell
  read -p "please input a character:" ch

  case $ch in
  	[a-z])
  		echo "xxx"
  	;;
  	[0-9]
  		echo "number"
  	;;
  	*)
  		echo "other"
  	;;
  esac
  ```

### 10 循环结构

- for-in及for

  ```shell
  a=(1 2 3)
  for x in ${a[*]}
  #for x in 1 2 3
  #for x in /etc/*       #遍历目录
  #for x in {1..10}       #遍历1到10

  do
  	echo $x
  done

  for ((i=0;i<${#a[@]};i++))
  do
  	echo ${a[$i]}
  done

    for i in {1..100}
    do
    	let j+=$i
    done
    echo $j
    
    
  #!/bin/bash

  从 1 加到100

    s=0
    for(( i=1;i<=100;i=i+1))
  定义循环100次
    do
    s=((s+$i))
  每次循环给变量s赋值
    done
    echo "The sum of 1+2+..+100 is : $s"
   输出从1加到100的和

  ```


- while循环


  ```shell

  i=1
  while [ $i -le 10 ]
  do
  	echo $i
  	#((i++))
  	let i++
  done
  	
  ```

### 11 函数

```shell
demo ()
{
	echo "this is a function"
}
demo

args ()
{
	echo $1
}
args "11"

```

