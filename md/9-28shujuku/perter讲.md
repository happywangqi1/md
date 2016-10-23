![](https://github.com/happywangqi1/imags/blob/master/3A63C5B3-2DD5-5330-D2036168F8AC.png?raw=true)
# mongo

##  启动数据库

  ```
    mkdir -p data/db

mongod --dbpath=./data
  ```

- "-p"同步建立子文件夹

## 启动操作界面

-  用户图形接口 **GUI**
-  命令行接口
-  对于mongodb我哦们使用mongo shell 来1操作
   启动mongo shell 的形式是

```
//进入
$  mongo
//创建和
$ use name
//创建集合
$ db.ccreateCollection('post')
//插入1数据记录，
db.posts.inster({title:'mytitle',content:'mycontent'})
```
- 修改一条记录

```

```
相应的curl命令测试

```
curl --request POST localhost:3000/posts
```
如果可以运行node index.js 的位置看到hello表示我们这一步成功完成。

### 安装mongoose

```
npm install --save monngoose
```
#### 在js代码中导入mongoose

#### 进行数据库的链接

#### 定义数据概要Schema

#### 创建数据模型model

#### 实例化对象model得到数据对象

#### 对象之上呼叫 save()

#### 保存成功
