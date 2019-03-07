### 带领你轻松走进 Nodejs 的世界，前端程序员也能轻松驾驭后端。
# 1 课程介绍与开发环境搭建
## 基本有什么~
NodeJS基础知识——全局对象，回调函数，事件，模块，流，文件系统，广告，web服务器，异步，同步，阻塞，非阻塞
购物车、restful api、前栈开发（react angular）
## 简介
Node.js® is a JavaScript runtime built on Chrome's V8 JavaScript engine.用C++写的
服务端的JavaScript，将JS语言转换为机器语言
Nginx 高性能异步服务器——c语言写模块
## 好处
Npm包直接下载
JavaScript运行环境——操作文件（grunt,gulp,webpack）——操作数据库
写api、小工具、聊天室、web开发

# 2 全局对象
Es6独有的箭头函数！！！
## 举例
全局对象
console.log()
setTimeout()——设置多少时间后函数触发
setInterval()——设置每隔多少时间函数触发，不断循环输出
clearInterval（）——清除函数间隔触发
```
var time = 0;

var timer = setInterval(function() {
    time += 2;
    console.log(time + " seconds have passed");
    if (time > 5) {
        clearInterval(timer);
    }
}, 2000);
```
__dirname——显示当前目录（两个下划线）
__filename——输出代码当前文件
require exports

#3 回调函数
```
function callFunction(fun, name) {
    fun(name);
}

callFunction(function(name) {
    console.log(name + ' Bye');
}, 'rails365');
```
回调函数可以传参、也可以不传

#4 模块
一个文件就是一个模块
* 暴露模块 `module.exports = counter;`
还可以这样写
```
module.exports.counter = counter;
module.exports.adder=adder;
module.exports.pi=pi;
```
或者
```
module.exports = {
  counter:counter,
  adder:adder,
  pi:pi
}
```
也可以直接将函数导出
```
module.exports = {
    counter: function(arr) {
        return "There are " + arr.length + " elements in the array";
    },
    adder: adder
}
```
* 引入模块 `var counter = require('./count');`
`var pi = require('./count').pi;`——引入模块其中的一个对象

# 5 事件——核心
### 点击之后发生的事件
element是一个DOM元素；
```
element.on('click',function(){
  console.log('clicked');
})
```
简单的事件调用：
```
var events = require('events');
var myEmitter = new events.EventEmitter();//新增事件
//绑定的监听函数
myEmitter.on('someEvent', function(message) {
    console.log(message);
})

myEmitter.emit('someEvent', 'the event was emitted');  //直接用事件的名称来触发事件
```

类继承类，也具有他的属性
对象具有绑定事件的属性——继承库就好utils
```

var events = require('events');  //引入事件
var util = require('util');   //工具库，核心库之一
//JS语法新建类
var Person = function(name) {
    this.name = name
}

util.inherits(Person, events.EventEmitter);//继承 或者用extends，person继承了后面的类，对象绑定了事件的属性

var xiaoming = new Person('xiaoming');
var lili = new Person('lili');
var lucy = new Person('lucy');

var person = [xiaoming, lili, lucy];
// 给每个人绑定一个事件
person.forEach(function(person) {
    person.on('speak', function(message) {
        console.log(person.name + " said: " + message);
    })
})
// 触发事件：
xiaoming.emit('speak', 'hi');
lucy.emit('speak', 'I want a curry');
```

# 6 读写文件（同步，异步）
NodeJS单线程运行 js 代码。——I/O操作，数据库连接比较费时，所以一般使用异步执行
读文件
```
fs.readFileSync("读取的文件名"，"编码方法"); //同步读取文件、一行一行执行程序
```
写文件
```
fs.writeFileSync("写入的文件名"，"写入的内容");
```
**异步方法都要加回调函数**
```
var fs = require('fs');//文件系统的库
//异步事件，事件队列存储费时的数据，再开另一个线程，再通知主线程
var readMeOne = fs.readFile("readMe.txt", "utf8", function(err, data) {
    var waitTill = new Date(new Date().getTime() + 2 * 1000);
    while (waitTill > new Date()) {}
    console.log("first async");
});//参数——文件名、编码、回调函数（data是文件的内容）

var readMeTwo = fs.readFile("readMe.txt", "utf8", function(err, data) {
    var waitTill = new Date(new Date().getTime() + 2 * 1000);
    while (waitTill > new Date()) {}
    console.log("second async");
});

console.log("finished");
```
读取文件再写入新的文件
```
var fs = require('fs');

var readMe = fs.readFile("readMe.txt", "utf8", function(err, data) {
    fs.writeFile('writeMe.txt', data, function() {
        console.log('writeMe has finished');
    })
});

// var waitTill = new Date(new Date().getTime() + 4 * 1000);
// while (waitTill > new Date()) {}

console.log("finished");
```

 # 7 创建和删除目录

```
var fs = require('fs'); //还是要引入fs模块
//创建目录，现有的文件改名成另一个文件并且放进新目录中
fs.mkdir('stuff', function() {
    fs.readFile('readMe.txt', 'utf8', function(err, data) {
        fs.writeFile('./stuff/writeMe.txt', data, function() {
            console.log('copy successfully');
        })
    })
});
//删除目录就是rmdir函数
//同步方法删除文件
// fs.unlink("writeMe.txt", function() {
//     console.log("delete writeMe.txt file");
// })
```

# 8 流和管道
### stream——对输出信息进行处理
`ls | grep app `——查找输出信息的关键字
这个命令在 linux 或 mac 才适合，或者 windows 的 git bash 也可以的。
如果是 windows 的命令提示符，对应的查找文件的命令应该是： `dir | findstr app`
**Linux的标准输入输出就是流**
>流（stream）是 Node.js 中处理流式数据的抽象接口。 stream 模块用于构建实现了流接口的对象。Node.js 提供了多种流对象。 例如，HTTP 服务器的请求和 process.stdout 都是流的实例。流可以是可读的、可写的、或者可读可写的。 所有的流都是 EventEmitter 的实例。(类似事件一样处理，绑定监听函数)

HTTP 服务器的请求响应时处理数据、webpack、gulp、文件打包压缩
处理数据、提高性能（大文件读写，把文件放在buffer中）
```
var fs = require('fs');

var myReadStream = fs.createReadStream(__dirname + 'readMe.txt', 'utf8'); //读写的文件放入一个流、创建读的流
//myReadStream.setEncoding('utf8');可以这样写来设置编码格式
var myWriteStream = fs.createWriteStream(__dirname + '/writeMe.txt');  //读写的文件放入一个流、创建写的流
//管道方法 前面是读的流、后面是写的流
myReadStream.pipe(myWriteStream);

//定义内容
var writeData = "hello world";
myWriteStream.write(writeData,'utf8');//第一个参数是数据
myWriteStream.end();
myWriteStream.on('finish', function() {
    console.log('finished');
})


var data = "";
//分段处理文件 分成很多buffer
//接收数据时的监听函数
myReadStream.on('data',function(chunk){
    // data +=chunk;
    // console.log('new chunk received');
    // console.log(chunk);
    myWriteStream.write(chunk);
})
//结束时成功的监听函数
myReadStream.on('end',function( ){
//    console.log(data);
})
```
管道的使用实例

```
//管道实例
// 解压
var crypto = require('crypto');  //加密的库
var fs = require('fs');
var zlib = require('zlib');  //压缩的库

var password = new Buffer(process.env.PASS || 'password');
var decryptStream = crypto.createDecipher('aes-256-cbc', password);

var gzip = zlib.createGunzip();
var readStream = fs.createReadStream(__dirname + '/out.gz');  //读的流

readStream // reads current file
    .pipe(gzip) // uncompresses
    .pipe(decryptStream) // decrypts
    .pipe(process.stdout) // writes to terminal 标准输出
    .on('finish', function() { // finished
        console.log('done');
    });

// 压缩
var crypto = require('crypto');
var fs = require('fs');
var zlib = require('zlib');

var password = new Buffer(process.env.PASS || 'password');
var encryptStream = crypto.createCipher('aes-256-cbc', password);

var gzip = zlib.createGzip();
var readStream = fs.createReadStream(__dirname + "/readMe.txt"); // current file
var writeStream = fs.createWriteStream(__dirname + '/out.gz');  //写入的流
//管道的方法
readStream // reads current file
    .pipe(encryptStream) // encrypts
    .pipe(gzip) // compresses
    .pipe(writeStream) // writes to out file
    .on('finish', function() { // all done
        console.log('done');
    });
```

 # 9 web 服务器 part 1 介绍
###  Web服务器是一台主机，浏览器就是一个客户端
request请求给web服务器很多头信息
如：接收数据的内容、接收的编码、语言、cookie
```
var http = require('http');//引入模块
//两个参数、请求-响应
//流的实例，类似流来操作
var onRequest = function(request, response) {
    console.log('Request received');
    response.writeHead(200, { 'Content-Type': 'text/plain' });//HTTP状态码：成功 传入的类型
    // response.write('Hello from out application');
    response.end('Hello from out application'); //响应纯文本给浏览器
}

var server = http.createServer(onRequest);

server.listen(3000, '127.0.0.1');  //监听端口，本地IP地址
console.log('Server started on localhost port 3000');
```
**response.write 是可以写多个的。**
```
response.write('<html>');
response.write('<body>');
response.write('<h1>Hello, World!</h1>');
response.write('</body>');
response.write('</html>');
response.end();
```

# 10 web 服务器 part 2 响应JSON给客户端
将响应头更改，然后再定义JSON
JSON formatter Chrome插件——显示JSON格式
JSON.stringify()——JSON.stringify() 方法用于将 JavaScript 值转换为 JSON 字符串。（容易传输）
序列化与反序列化
JSON对象变成字符串 `JSON.stringify(myObj)`
怎么取值就反序列化 `JSON.parse(JSON.stringify(myObj))`
```
var http = require('http');

var onRequest = function(request, response) {
    console.log('Request received');
    response.writeHead(200, { 'Content-Type': 'application/json' });//JSON响应头
    // response.write('Hello from out application');
    //字符串类的JSON 序列化的
    var myObj = {
        name: "hfpp2012",
        job: "programmer",
        age: 27
    };//JSON对象作为响应内容
    response.end(JSON.stringify(myObj));
}

var server = http.createServer(onRequest);

server.listen(3001, '127.0.0.1');
console.log('Server started on localhost port 3001');
```

 # 11 web 服务器 part 3 响应 HTML 页面
```
var http = require('http');
var fs = require('fs');

var onRequest = function(request, response) {
    console.log('Request received');
    response.writeHead(200, { 'Content-Type': 'text/html' });
    //直接加入HTML片段,用加号连接
    // var htmlFile = '<!DOCTYPE html>' +
    // '<html lang="en">' +

    // '<head>' +
    //     '<meta charset="UTF-8">' +
    //     '<meta name="viewport" content="width=device-width, initial-scale=1.0">' +
    //     '<meta http-equiv="X-UA-Compatible" content="ie=edge">' +
    //     '<title>Document</title>' +
    // '</head>' +

    // '<body>' +
    //  'hello world' +
    // '</body>' +

    // '</html>';
    // response.end(htmlFile);
    //利用文件流来输出导入,本地有index.html文件
    var myReadStream = fs.createReadStream(__dirname + '/index.html', 'utf8');
    // response.write('Hello from out application');
    myReadStream.pipe(response);
}

var server = http.createServer(onRequest);

server.listen(3000, '127.0.0.1');
console.log('Server started on localhost port 3000');
```

# 12 web 服务器 part 4 用模块化思想组织代码
exports+require
**exports.startServer = startServer;等同于module.exports.startServer = startServer;**
### server.js——模块好的文件
```
var http = require('http');
var fs = require('fs');

function startServer() {
    var onRequest = function(request, response) {
        console.log('Request received');
        response.writeHead(200, { 'Content-Type': 'text/html' });
        var myReadStream = fs.createReadStream(__dirname + '/index.html', 'utf8');
        // response.write('Hello from out application');
        myReadStream.pipe(response);
    }

    var server = http.createServer(onRequest);

    server.listen(3000, '127.0.0.1');
    console.log('Server started on localhost port 3000');
}

exports.startServer = startServer;
```

### app.js——入口文件
```
var server = require('./server');

server.startServer();
```

# 13 web 服务器 part 5 路由
链接后缀不同，不同路由请求不同资源显示不同页面
路由不存在显示404页面
```
var http = require('http');
var fs = require('fs');

function startServer() {
    var onRequest = function(request, response) {
        //request——客户端请求信息
        console.log('Request received ' + request.url);
        //request.url 判断响应路由
        if (request.url === '/' || request.url === '/home') {
            response.writeHead(200, { 'Content-Type': 'text/html' });
            fs.createReadStream(__dirname + '/index.html', 'utf8').pipe(response);
        } else if (request.url === '/review') {
            response.writeHead(200, { 'Content-Type': 'text/html' });
            fs.createReadStream(__dirname + '/review.html', 'utf8').pipe(response);
        } else if (request.url === '/api/v1/records') {
            //显示JSON
            response.writeHead(200, { 'Content-Type': 'application/json' });
            var jsonObj = {
                name: "yanjie1995"
            };
            response.end(JSON.stringify(jsonObj));
        } else {
            //注意状态码 响应404页面
            response.writeHead(404, { 'Content-Type': 'text/html' });
            fs.createReadStream(__dirname + '/404.html', 'utf8').pipe(response);
        }
    }

    var server = http.createServer(onRequest);

    server.listen(3000, '127.0.0.1');
    console.log('Server started on localhost port 3000');
}

exports.startServer = startServer;
```

# 14 web 服务器 part 6 重构路由代码
更好的组织代码，代码维护性
将路由单独抽成一个文件router.js
```
var fs = require('fs');
//路径名、输出响应
function route(handle, pathname, response) {
    console.log('Routing a request for ' + pathname);
    //判断类型
    if (typeof handle[pathname] === 'function') {
        handle[pathname](response);
    } else {
        response.writeHead(404, { 'Content-Type': 'text/html' });
        fs.createReadStream(__dirname + '/404.html', 'utf8').pipe(response);
    }
}

module.exports.route = route;
```
使用handle.js来处理路由响应数据
```
//操作路由的请求方法

var fs = require('fs');

function home(response) {
    response.writeHead(200, { 'Content-Type': 'text/html' });
    fs.createReadStream(__dirname + '/index.html', 'utf8').pipe(response);
}

function review(response) {
    response.writeHead(200, { 'Content-Type': 'text/html' });
    fs.createReadStream(__dirname + '/review.html', 'utf8').pipe(response);
}

function api_records(response) {
    response.writeHead(200, { 'Content-Type': 'application/json' });
    var jsonObj = {
        name: "yanjie1995"
    };
    response.end(JSON.stringify(jsonObj));
}

module.exports = {
    home: home,
    review: review,
    api_records: api_records
}
```
服务器函数server.js
```
var http = require('http');
var fs = require('fs');

function startServer(route, handle) {
    var onRequest = function(request, response) {
        console.log('Request received ' + request.url);
        //外部传入的函数来判断路由该响应什么
        route(handle, request.url, response);
    }

    var server = http.createServer(onRequest);

    server.listen(3000, '127.0.0.1');
    console.log('Server started on localhost port 3000');
}

module.exports.startServer = startServer;
```

入口文件函数app.js
```
var server = require('./server');
var router = require('./router');
var handler = require('./handler');
//handle是一个空对象
var handle = {};
//添加路径值
//key是一个路径 value是一个函数
handle["/"] = handler.home;
handle['/home'] = handler.home;
handle['/review'] = handler.review;
handle['/api/v1/records'] = handler.api_records;

server.startServer(router.route, handle);
```

# 15 web 服务器 part 7 使用 GET 或 POST 请求发送数据
地址的参数?key=value——get方法传递数据、参数给服务器
表单——post方法
### 传递参数给NodeJS服务器
#### 地址？后面的参数会时刻变化，取前面的参数
```
var url = require('url'); //操作url的库 主机名 协议
var pathname = url.parse(request.url).pathname;
var params = url.parse(request.url, true).query;//解析，true返回得到的东西
route(handle, pathname, response, params);//params可以的得到？后面的参数、是一个JSON
```
route也应该相应加入params参数
```
var fs = require("fs");

function route(handle, pathname, response, params) {
  console.log("Routing a request for " + pathname);
  if (typeof handle[pathname] === "function") {
      handle[pathname](response,params);
   } else {
    response.writeHead(200, { "Content-Type": "text/html" });
     fs.createReadStream(__dirname + "/404.html", "utf8").pipe(response);
   }
}

module.exports.route = route;
```
#### 取表单的数据
```
    <form action="/api/v1/records" method="post">
        name: <input type="text" name="name" /> age: <input type="text" name="age" />
        <input type="submit" value="Submit">
    </form>
```

```
//继承事件的实例
var querystring = require('querystring');//引入的这个库来转化数据
request.on("error", function(err) {
            console.error(err);
        }).on("data", function(chunk) {
            data.push(chunk);
        }).on('end', function() {
            if (request.method === "POST") {
              //防止数据过大
                if (data.length > 1e6) {
                    request.connection.destroy();
                }
                data = Buffer.concat(data).toString();
                //字符串解析为JSON
                route(handle, pathname, response, querystring.parse(data));
            } else { //get方法
                var params = url.parse(request.url, true).query;
                route(handle, pathname, response, params);
            }
        });
```



# 16 包管理器 NPM
除了 npm 的官网可以找到 npm 包之外，下面两个网站也可以。

http://node-modules.com

https://npms.io
### express框架
npm install express

安装webpack 加入-g：全局的意思
npm install -g webpack 安装到系统

切换中国的源的方法：
https://github.com/Pana/nrm
nrm can help you easy and fast switch between different npm registries, now include: npm, cnpm, taobao, nj(nodejitsu).

# 17 package.json 文件
package.json——记录所有安装的包的信息与版本
所以上传项目时不需要node_modules这个大文件夹
如果重新安装的话用以下命令
看package.json里面有什么包再自行安装
```
$ npm init

$ npm install --save express

$ npm install --save-dev gulp

$ npm run start //scripts里面的，告诉别人启动命令、入口文件

$ npm install
```

# 18 nodemon (完结)
代码一改变 自动重启服务器
还可以设置其他参数，其他功能看文档
nodemon is a tool that helps develop node.js based applications by automatically restarting the node application when file changes in the directory are detected.
```
npm install -g nodemon

nodemon [your node app] //使用
```
