# mongodb 数据库

## mongodb 是什么

MongoDB是一个基于分布式文件存储的开源数据库系统

MongoDB 将数据存储为一个文档，数据结构由键值(key=>value)对组成。MongoDB 文档类似于 JSON 对象。字段值可以包含其他文档，数组及文档数组。

##  安装

官网：http://www.mongoing.com/

0.在home下 建一个文件data
```
mkdir data

```

1.进入中文手册；

2.进入instllation

3.进入第一个 install MongoDB Coommunity  Edition;

4.再进入install on linux

5.进入 install on Ubuntu

6.按步骤操作

1.
```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv EA312927
```
2.
```
echo "deb http://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list
```
3.
```
sudo apt-get update
```
4.
```
sudo apt-get install -y mongodb-org
```

## mongodb启动与连接

1. windows启动服务器端

```
mongod --dbpath=./data
```
- 如果出现waiting for connections on port 27017就表示启动成功,已经在27017端口上监听了客户端的请求
- 注意：--dbpath后的值表示数据库文件的存储路径,而且后面的路径必须事先创建好，必须已经存在，否则服务开启失败
- 注意：这个命令窗体绝对不能关,关闭这个窗口就相当于停止了mongodb服务
- 也可以在命令后面加上参数 --port 27017 来指定端口

2.查看数据库

- 先进 mongo

-

```
use person use + 数据库名
```

- 创建集合

```
db.createCollection('posts')
```
- 查看集合

```
show collections
```
- 插入数据

1.
```
db.person.save({name:"sdjs",age:13})
```

2.
```
db.person.insert({name:"zhangSan",age:30}
```
注：person 在这是数据库的1一个集合，集合里面是数据，

- 查看数据

```
db.文件名.find()

```
- 查看制定数据：

```
db.文件名.find({age:10})
```


```
show dbs
```
- 显示当前数据库

```
db 或 db.getName()
```
备注: 我们刚创建的数据库person 如果不在列表内， 要显示它，我们需要向 person 数据库插入一些数据 db.person.insert({name:"zhangSan",age:30})

- 删除数据库
语法

```
db.dropDatabase()
```
- save 有更新作用（覆盖作用）
