# 1.课程介绍
#### Babel 的插件 Plugins 和 Presets
@ 符号 decorators 编译不通过的原因，及如何解决
为何总是要上头部导入 @babel/polyfill
技术基础——打包工具、编译文件（将不能识别的程序可以识别）
# 2.zero config
构建前端项目 编译
# 3.Mode
模式默认为production 可以更改为none、development
Possible values for mode are:
* None：默认不使用任何参数
* development：开发环境（本地电脑使用的）大小内存不在意
* production(default):生产环境模式（使用线上的环境，有ip地址）保证内存小
开启插件也不一样！！！
# 4.命令行指定入口文件 直接在后面接
编译文件输出
webpack --mode=development ./src/hello.js –output ./build/main.js
包装命令：
npm init -y自动生成
在package.json写入
```
"scripts": {
    "dev": "webpack --mode=development"
  },
$ npm run dev
```
# 5.npx解决全局安装:
create-react-app脚手架的新的安装方法：
```
npx create-react-app my-app
cd my-app
npm start
```
# 6.配置文件webpack.config.js
```
const path = require('path');

module.exports = {
  entry: "./src/index.js",
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: "app.bundle.js"
  },
  mode: 'development'
}
```
# 7.配置多入口文件 Entry Points
# 8.Babel
不同版本的es语法有些许不同，浏览器发展没有跟上潮流
Babel JavaScript的编译器，可以将低版本的es语法转换为高版本的
能把你的es6源码或react的jsx语法源码转成浏览器或node能执行的代码。
安装：`npm install -g babel-cli`
可能需要安装插件：`npm install --save-dev babel-preset-env`
# 9.babel-loader 的介绍与安装
安装一些库
`npm install --save-dev @babel/core @babel/cli @babel/preset-env`
`npm install --save @babel/polyfill`
（新的安装方式加了@ 一些库放在同一文件夹，同一地方，集成起来，方便管理）
安装babel-loader: `npm install -D babel-loader`
# 10.Babel Plugins - plugin-transform-arrow-functions（更改函数箭头的）
加入插件
1、	找到插件的官方文档，安装插件
2、	在package.js引入插件 或者新建. babelrc文件引入

# 11.装饰器语法
![webpack1](https://github.com/TanYanjieZYX/NewKnowledge/blob/master/pic/webpack1.png)      
# 12.presets（预设）—不用每次使用插件的时候再来安装
Es5语法转换为Es6语法的插件添加进来就好了
预设添加`   "presets": ["@babel/preset-env"],`

# 13.devtool false 让编译后的代码（bundle.js代码）可读性强一些
在webpack package中设置

# 14.babel/polyfill——浏览器版本不支持高版本的语法（增强）
babel只负责语法转换，比如将ES6的语法转换成ES5。但如果有些对象、方法，浏览器本身不支持，比如：
* 全局对象：Promise、WeakMap 等。
* 全局静态函数：Array.from、Object.assign 等。
* 实例方法：比如 Array.prototype.includes 等。

此时，需要引入babel-polyfill来模拟实现这些对象、方法。
除了在 webpack.config.js 中的 entry 引入` @babel/polyfill` 之外，在需要的 src/index.js 等 js 文件最顶部引入` import '@babel/polyfill' `也是一样的。
注意：
**能转化新的语法，但是转化不了新的API,要用特别的方法来处理**
其他的polyfill如何使用——fetch方法
安装增强版本的：`npm install whatwg-fetch --save`
配置文件中添加：`entry: ['whatwg-fetch', ...]`

##### webpack使用polyfill的方法：——全局替换
1、	webpack.package.js文件
```
module.exports = {
entry: ["@babel/polyfill", "./app/js"],
};
```
2、/babel-preset-env#usebuiltins
"usage" | "entry" | false, defaults to false.
更改babelrc的内容，添加：
`"presets": [["@babel/preset-env",{"debug":true,"useBuiltIns": "entry"}]],`
在需要更改的js文件头部引用：`import '@babel/polyfill'`

**Polyfill的缺点——全局变量污染，不知道是哪个库；prototype污染**
引入babel-polyfill会有一定副作用，比如：
* 引入了新的全局对象：比如Promise、WeakMap等。
* 修改现有的全局对象：比如修改了Array、String的原型链等。

在应用开发中，上述行为问题不大，基本可控。但如果在库、工具的开发中引入babel-polyfill，则会带来潜在的问题。
举个例子，项目中定义了跟规范不一致的Array.from()函数（别管我为什么不一样，就是这么任性），同时引入了一个库（依赖babel-polyfill），此时，这个库可能覆盖了自定义的Array.from()函数，导致出错。
这就是babel-runtime存在的原因。它将开发者依赖的全局内置对象等，抽取成单独的模块，并通过模块导入的方式引入，避免了对全局作用域的修改（污染）。

Runtime——避免污染，没有全局替换
```
$ npm install --save @babel/runtime
$ npm install --save-dev @babel/plugin-transform-runtime
$ npm install --save @babel/runtime-corejs2
```
# 14.打造react环境
最新版本的npm不需要加—save 也可以发挥作用
识别不了react代码——`@babel/preset-react`
```
$ npm install react react-dom
$ npm install --save-dev @babel/preset-react
更改babelrc文件——    ["@babel/preset-react", { "development": true }]
```
# 15.html-webpack-plugin插件——解决手写的html文件的问题，自动获取hash值
Plugin——扩展功能
Loader——转化文件
js,css文件命名带有字母和数字的是hash（MD5）值，有利于服务器cache缓存
chunkhash contenthash
安装+webpack.package添加路径
# 16.配置多个单页面应用——页面的入口文件
![webpack2](https://github.com/TanYanjieZYX/NewKnowledge/blob/master/pic/webpack2.png)    
# 17.使用loader来处理css样式
两个配合使用
Css-loader:将处理的结果交给style
Style-loader:
# 18.使用 loader 来处理 Sass 和 Less 文件
Sass:另一种方法来写css，比如继承、嵌套
Less: It's CSS, with just a little more.
sass-loader:看文档
less-loader：看文档
# 19.用 mini-css-extract-plugin 把 CSS 分离成文件，js代码释放
不要空白
# 20.启动服务器并实时刷新 webpack-dev-server
改配置文件时，自动刷新页面（相当于本地服务器）
# 21.用 clean-webpack-plugin 来清除文件——留下有用的文件
# 22.如何打包图片（包含规划编译出的文件的目录结构）
file-loader：处理引用图片，本地图片
url-loader：url-loader works like file-loader, but can return a DataURL if the file is smaller than a byte limit.
# 23.压缩图片image-webpack-loader
Minify PNG, JPEG, GIF, SVG and WEBP images with imagemin
（体积变小，运行速度变快）
`ls -lh`查看文件大小
# 24.构建开发和生产环境-分离配置文件
分离线上文件和线下文件
如何处理开发和线上环境的配置的差异性问题，之前我们是用一个环境变量 `NODE_ENV=production,`这个环境变量是放在命令行中，作为命令行的一部分，比如` NODE_ENV=production webpack -p`,传入到配置文件webpack.config.js 中，由它通过` process.env.NODE_ENV `这样来引用，从而来判断是开发环境或生产环境。

我们始终使用的是同一个配置文件，即 webpack.config.js，区别不同的环境是通过变量。主要是开发和生产环境的差异性比较大，比如我们开发环境需要一个 webpack-dev-server 而生产环境不需要，生产环境只需要保证编译出来的文件体积足够小，性能足够好就可以，开发环境也不需要压缩文件，不压缩反而能看得清楚编译后的源码，而生产环境就要保证体积小，所以要压缩编译后的文件。

首先把 webpack.config.js 一分为二，开发环境的配置文件叫 webpack.dev.js，而生产环境的叫 webpack.prod.js，除此之外，还要多加一个文件，就是把他们共同的部分抽出来，单独成一个文件，叫 webpack.common.js，这样 webpack.dev.js 和 webpack.prod.js 就不会有太多相同或重复的内容，只要写出他们不同的部分就好了，这样也好维护啊。

common不存在开发环境使用的、线上环境使用的、判断的
dev引入`const merge = require('webpack-merge')`;
引入common文件prod引入

# 25.显示打包进度条——webpackbar

# 26.调整配置 - 在浏览器显示 DevServer 的 编译错误的信息
devServer.overlay
devServer.quiet——不显示一些不必要的

# 27.devtool——管理源代码
This option controls if and how source maps are generated.
选择可以根据速度
示例：
![webpack3](https://github.com/TanYanjieZYX/NewKnowledge/blob/master/pic/webpack3.png)    
运行代码出错和编译出错是两码事：
线上环境不需要开启代码——source_map（代价大，占用内存）

# 28.解决开发环境和生产环境打包不一致的情况
mini-css-extract-plugin

# 29.打包优化 - 深入探索 mode、Optimization、terser-webpack-plugin、UglifyjsWebpackPlugin
terser——terser is a fork of uglify-es that retains API and CLI compatibility with uglify-es and uglify-js@3.
terser-webpack-plugin——This plugin uses terser to minify your JavaScript.
UglifyJS2——UglifyJS is a JavaScript parser, minifier, compressor and beautifier toolkit
uglifyjs-webpack-plugin——This plugin uses uglify-js to minify your JavaScript.
 
# 程序TIPS:
## 1.前端模拟 API 的最佳选择 json-server
json-server——获取API的库
Start JSON Server
`json-server --watch db.json`
增删改查
本地开一个服务
自定义 api
以中间件的形式与 express 结合
高级的查询功能
查询命令：
http://localhost:3000/users?firstName=rails365&firstName=tony
http://localhost:3000/users?q=rails
http://localhost:3000/users?_page=1&_limit=2
http://localhost:3000/users?_sort=age
http://localhost:3000/users?_sort=age&_order=desc

postman——浏览器插件来增加数据
faker.js——产生随机的数据、内容
## 2.从零开始使用 Webpack 4 和 Babel 7 搭建 React 开发环境
新增目录src，放源代码
`npm init -y`初始化
安装webpack的库
` npm install webpack webpack-cli –save-dev`（如果出现命令找不到，就全局安装webpack npm install -g webpack）
更改package.json下的script
`“dev”:”webpack –mode=development”,`运行命令npm run dev
安装babel(es6语法转换为es5语法，浏览器可以识别)
`npm install @babel/core babel-loader @babel/preset-env @babel/preset-react –save-dev`(安装时加的@符号是为了安装都在babel目录下)
编辑.babelrc文件——知道使用那些babel插件
编辑webpack.config.js——知道怎么转换语法
安装react的库 `npm install react react-dom`
新建组件components目录来管理组件文件
安装npx `npm install npx -g`

## 3.如何在 React (componentDidMount Async) 使用 Async Await 和 fetch
(发送请求，生命周期相关内容)
入口文件：index.js
api地址：https://api.coinmarketcap.com/v1/ticker/?limit=10
从network那里看数据的类型和相关信息
fetch：浏览器使用，程序nodejs使用不适用
同构版本来解决——isomorphic-fetch
安装polyfill来解决问题
async——promise
![webpack4](https://github.com/TanYanjieZYX/NewKnowledge/blob/master/pic/webpack4.png)    
## 4.从 fetch 和 promise 入手来聊聊 polyfills 和 ponyfills 以及同构
发送请求——之前是XMLHttpRequest（浏览器对象）
jQUery——封装发送请求，使用更方便
浏览器自动带的方法——fetch(不用安装任何库就能支持的)
cURL是一个利用URL语法在命令行下工作的文件传输工具——Nodejs可以支持
同构版本的fetch——cross-fetch
fetch库的使用方式:
1、polyfill (全局对象的添加，没有全局对象的污染)
promise-polyfill——Lightweight ES6 Promise polyfill for the browser and node. A+ Compliant
es6-promise——A polyfill for ES6-style Promises

## 5.探索前端项目或 Node.js 项目的环境变量和配置文件以及安全问题
命令env查看环境变量（环境变量里面可以防止密码等敏感信息，写在代码里面有安全问题）
脚手架react-app搭建的识别两种环境变量：
1. NODE_ENV
2. REACT_APP

set "REACT_APP_SECRET_CODE=abcdef" && npm start
cross-env——Cross platform setting of environment scripts
不同命令传入不同的环境变量
node-config——Node.js Application Configuration
dotenv——Loads environment variables from .env for nodejs projects.
.gitgnore 客户端不提交的内容放着

## 6.create-react-app 的 “坑” - 默认情况下线上环境能看到源代码
开启了source-map，所以可以查看线上的源代码
1、编译的时候去掉source-map: `export GENERATE_SOURCEMAP=false`
2、改配置
释放配置——`yarn run eject`
生产环境使用的配置文件：webpack.config.prod.js

## 以上知识看随风大神的webpack4视频积累的
