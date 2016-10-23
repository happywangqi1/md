# 前后端小demo

## axios 实现前后端交互的原理

- 新建文件夹并且里面有2个文件夹一个控制前端一个来控制后台

- 分别在俩个文件夹里建json文件

```
echo {}>package.json
```
- 分别在前端跟后台新建文件index.js

- 前端 下载 axios

```
npm install --save axios
```
- index.js里

```
var axios = require('axios')

var data={
  title:'mytitle',
  content:'mycontent'
}
axios.post('http://localhost:3000/posts',data)

```
- 后端

- 装包 express

```
npm install --save express body-parser
```
- index.js里

```
var express = require('express');
var  app = express();

var bodyParser = require('body-parser');
// 用于支持express的发送
app.use(bodyParser.json());
// 加了app.use(bodyParser.json());上面的bodyParser才能用；有

app.post('/posts',function(req,res){
  // 有上面引入的express才有这个app
  console.log(req.body);
  // 有下面两句才能用req.body
  // var bodyParser = require('body-parser');
  // app.use(bodyParser.json());
})

app.listen(3000, function() {
  // 监听事件和回调函数
console.log('running on port 3000')
})

```
- 前端后台直接分别在命令行里执行,后台1就会出现要打印的json数据

```
node inex.js
```
## 客户端得到数据（用react来搭建）

- 搭建 react 基础开发环境

#### webpack
