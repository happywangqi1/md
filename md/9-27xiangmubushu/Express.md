# Express

官网：https://expressjs.com/

Express是一个简洁、灵活的node.js Web应用开发框架, 它提供一系列强大的功能，比如：模板解析、静态文件服务、中间件、路由控制等等,并且还可以使用插件或整合其他模块来帮助你创建各种 Web和移动设备应用,是目前最流行的基于Node.js的Web开发框架，并且支持Ejs、jade等多种模板，可以快速地搭建一个具有完整功能的网站。

1.Node.js  web  application framework.(node.js的外部开发框架)；React：是前段开发框架；Express:是最简单的后台框架；

2.作用：相当于一个数据库

3.使用：

- 安装
```
$ npm install express
```
- 写代码

- 先转化成node.js的项目（先创建npm init目的是更好的保存管信息）
```
npm init
```
获取、引用
通过变量`app`我们就可以调用`express`的各种方法
```
var express = require('express');
var app = express();
app.listen(3000);
```

## get请求
根据请求路径来处理客户端发出的GET请求
语法
```javascript
app.get(path,function(request, response));
```
- 第一个参数`path`为请求的路径
- 第二个参数为处理请求的回调函数，有两个参数分别是
    - request 代表请求信息
    - response 代表响应信息

```javascript
var express = require('express');
var app = express();
app.get('/',function(req,res){
    res.end('welcome to  homepage');
});
app.get('/about',function(req,res){
 res.end('welcome to about page');
})
app.get("*",function(req,res){
 res.end("404");
})
app.listen(3000);
```

##  all
app.all()函数可以匹配所有的HTTP动词
语法
```
app.all(path,function(request, response));
```

示例
```
var express = require('express');//引入express
var app = express();
app.all("*",function(req,res){
 res.send("404");
})
app.listen(3000);
```

##  中间件
中间件就是处理HTTP请求的函数，用来完成各种特定的任务
比如检查用户是否登录、检测用户是否有权限访问等，它的特点是:
- 一个中间件处理完请求和响应可以把相应数据再传递给下一个中间件
- 回调函数的`next`参数,表示接受其他中间件的调用，函数体中的next(),表示将请求数据传递给下一个中间件
- 还可以根据路径来区分进行返回执行不同的中间件

```javascript
var express = require('express');
var app = express();
var path = require('path');
function filter(req,res,next){
 console.log('filter');
 next();
}
app.use('/',filter);

app.listen(3000);
```

## 获取参数
- req.host 返回请求头里取的主机名(不包含端口号)
- req.path 返回请求的URL的路径名

```javascript
app.get('/',function(req,res){
   res.end('欢迎来到首页'+req.host+" "+req.path);
});
```

## 获得查询字符串
```javascript
//http://localhost:3000/?a=1&b=2&c=3
app.get('/',function(req,res){
   res.send(req.query);
});
```

##  params
req.params可以用来获取请求URL中的参数值

```javascript
app.get('/:id/:name',function(req,res){
   res.send(req.params.id+" "+req.params.name);
});
```

##  send
`send`方法向浏览器发送一个响应信息，并可以智能处理不同类型的数据
并在输出响应时会自动进行一些设置，比如HEAD信息、HTTP缓存支持等等。
语法
```javascript
res.send([body|status], [body])
```
示例
1.当参数为一个String时，Content-Type默认设置为"text/html"。
```javascript
res.send('Hello World'); //Hello World
```

2.当参数为Array或Object时，Express会返回一个JSON
```javascript
res.send({ user: 'tobi' }); //{"user":"tobi"}
res.send([1,2,3]); //[1,2,3]
```

3.当参数为一个Number时，并且没有上面提到的任何一条在响应体里，Express会帮你设置一个响应体，比如：200会返回字符"OK"
```javascript
res.send(200); // OK
res.send(404); // Not Found
res.send(500); // Internal Server Error
```
