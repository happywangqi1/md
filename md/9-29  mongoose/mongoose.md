#  mongoose

##   mongoose是什么

mongoose是用来做express和mongo之间的连接

## 作用：

连接数据转化成js的对象。以便我们可以用Js代码来读取mongoDB的作用

看官网来操作：www.mongoosejs.com

## 使用

- 使用前先新建一个文件夹

```
mkdir mongo-t 文件名可以随意，新建一个json文件：echo {} >package.json 回车；检查一下：cat package.json;

```

- 安装

```
npm install --save mongoose

```
注意：每个项目只需要一个数据库就够了。以为一个数据库里可以有多个集合。

- 步骤

1.引入

```
var mongoose = require('mongoose');
mongoose.connect('mongodb://localhost:27017/mongo-t');

```
2.大框架

```
var db = mongoose.connection;
db.on('error', console.error.bind(console, 'connection error:'));
db.once('open', function() {
  // we're connected!
});

```
3.插入大框架的：

```
db.once('open', function() {
  var kittySchema = mongoose.Schema({
    name: String
  })
  var Kitten = mongoose.model('Kitten', kittySchema);

// Kitten1 代表一条1记录的名字
  var silence = new Kitten({ name: 'Silence' });
    console.log(silence.name); // 'Silence
  silence.save ()

  // 保存Kitten1的记录信息

```
## 建立数据 Schema

- 作用：

描述一条记录（文档）；规定该记录中有几个字段（field）每个字段的名字以及字段类型

```
mongoose.schema({
  name:String;
  weight:num;
  })

```
### model

- 数据库跟代码的中间人

MVC 当中的M,MVC 分别是模型、视图、控制器（model,view,controller）

- 作用：
model 中存放的所有和数据直接相关的代码，通常会被写成一个类。

```
var cat = mongoose.model('cat',catSchema);

```
第一个参数“"cat"”:模型对应的集合名称的单数；

第二个参数“catSchema”：一条数据记录的结构；

- 简单用数据库输出用户名，密码，年龄

```
var mongoose = require('mongoose');
mongoose.connect('mongodb://localhost:27017/mongo-t');

var db = mongoose.connection;
db.on('error', console.error.bind(console, 'connection error:'));
db.once('open', function() {
  var userSchema = mongoose.Schema({
  name:String,
  key:String,
  age:String
})
  var person = mongoose.model('person',userSchema);
  var person = new person({ name:'xiaoming',key:'qwer',age:"12"})
    console.log(person.name);
    console.log(person.key);
    console.log(person.age);
    person.save()
});
```

## 用JS 代码来增删改查

- create 增（上边的例子）

- Read 查 find(),find 括号里没有指定的参数，就是查所有；
异步函数，并行执效率高；

```
console.log(user.find());
  user.find().exec(function(err,user){
    //异步
    console.log(users);
  });

```
- updata 更新

```
/*var userSchema = mongoose.Schema({
  name:String,
  key:String,
  age:String
})
var person = mongoose.model('person',userSchema);
var xiao = new person({ name:'xiaoming',key:'qwer',age:"12"})
  // console.log(person.name);
  // console.log(person.key);s
  // console.log(person.age);
  xiao.save() */

  xiao.name = "xiaoli",
  xiao.key = "123",
  xiao.age = "13",
  xiao.save()

/*  console.log(person.find());
  person.find().exec(function(err,users){
    console.log(users);
  });
});*/

```
- 更新

```
var User = mongoose.model('user', userSchema);
 User.findById({_id: '57ecbcdf4d95146106254fe0'}, function(err, user) {
   user.name = 'rrrrrr'
   user.save(function(err){user.save(function(err){
     console.log(users);
     });
  });
})
```
- 删除

```
user.remove(function(err){
    console.log('删除了');
    Person.find().exec(function(err,users){
      console.log(users);
    })

```
