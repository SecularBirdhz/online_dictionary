# 在线词典

### 一.需求分析  -->  客户端怎么应用
**客户端 : 发送请求 得到结果**

### 二.确定并发方案,确定套接字使用,确定细节
1. 并发 : 多进程
2. 套接字 tcp套接字
3. 细节 : 使用数据库处理数据,注册成功进入二级界面
        历史只记录前10条,注册信息,用户名,密码
### 三.技术点

1. 数据存储 dict 其他数据表
    1. 单词表 : words (查单词)
    2. 用户表 : user (注册,登录)
        - id name password
        - 
    3. 历史记录 : hist (查历史记录)
        1. uid wid time
            - create table hist1 (uid int,wid int,primary key(uid,wid),`time` datetime default now());
        2. id name word
            - create table hist2(id int primary key auto_increment,name varchar(30) not null,word varchar(30),`time` datetime default now());

2. 二级界面 两个界面怎么跳转

内层循环再嵌套一个内层循环
   
   
### 四.结构设计

**是用什么封装,分成几个模块**
1. 客户端          函数
2. 服务端逻辑      函数
3. 服务端数据处理   类
---

### 五.功能划分 和 通信协议设计
1. 网络通信
2. 注册
3. 登录
4. 查单词
5. 历史记录

### 六.具体每个功能干什么
1. 网络通信

2. 注册
- 客户端 : 
    1. 请求 R name passwd
- 服务端 :
    1. 验证能否注册
    2. 插入数据库
    


3. 登录

4. 查单词
    - 客户端: 请求
    - 服务端: 查询单词 插入历史记录
5. 历史记录
    - 客户端: 发送请求   循环接受历史记录
    
### cookie :
- import getpass 
- getpass.getpass()  
功能: 同input,但是隐藏输入内容(输入密码的选择)
    
 ## 补充：
 1. 如果你使用这个代码，你需要使用MySQL数据库，并且创建一个dict库，再在库下创建三个表user，user_words,words.(简单说你需要掌握一定的数据库知识,因为涉及到服务端与数据库的交互)
 
