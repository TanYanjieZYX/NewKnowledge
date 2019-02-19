# 1.React的介绍、yarn npx、用React脚手架create-react-app搭建React环境  运行React项目
### 为什么要学react?
看几个招聘信息...
大前端技术体系以及薪资介绍：
前端必备：Html5+Css3+js+（es5）+Jquery          PC 、移动web                 6k-10k
前端必备：Es6 、Es7、TypeScript、Angular 、 Vue  、React 、 小程序           三大框架只会一个 8k-13k                   三大框架都会  13+
混合app开发：  Ionic   ReactNative   Cordova+vue   Cordova+React   Weex      15k+
后台全栈：Nodejs  Express/Koa   Egg.js    Mongodb  Mysql Redis                       15+        20k+
电脑软件：Electron跨平台混合软件开发
其他技术.....
全栈 20k+

### React的介绍：
* React来自于Facebook公司的开源项目
* React 可以开发单页面应用       spa（单页面应用）
* react 组件化模块化  开发模式
* React通过对DOM的模拟(虚拟dom)，最大限度地减少与DOM的交互（数据绑定）
* react灵活  React可以与已知的库或框架很好地配合。
* react 基于jsx的语法，JSX是React的核心组成部分，它使用XML标记的方式去直接声明界面，  html  js混写模式

### 搭建React开发环境之前的准备工作。
1、必须安装nodejs      注意：安装nodejs稳定版本
2、安装cnpm用cnpm替代npm
		地址：http://npm.taobao.org/
		安装cnpm:
			`npm install -g cnpm --registry=https://registry.npm.taobao.org`

3、用yarn替代npm
		yarn的安装：
			第一种方法：参考官方文档https://yarn.bootcss.com/
			第二种方法：`cnpm install -g yarn  或者 npm install -g yarn`


#### 搭建React开发环境的第一种方法（老-现在推荐）：

	https://reactjs.org/docs/create-a-new-react-app.html
1. 必须要安装nodejs
注意：安装nodejs稳定版本
2. 安装脚手架工具   （单文件组件项目生成工具）   只需要安装一次
`npm install -g create-react-app   /  cnpm install -g create-react-app`
3. 创建项目   （可能创建多次）
```
找到项目要创建的目录：
		create-react-app reactdemo
```
4. cd  到项目里面
```
cd  reactdemo
npm start             yarn start运行项目
npm run build         yarn build 生成项目
```
#### 搭建React的开发环境的第二种方法（新-未来推荐）：

	https://reactjs.org/docs/create-a-new-react-app.html
1、必须要安装nodejs
2.安装脚手架工具并创建项目
```
找到项目要创建的目录执行：

		npx create-react-app reactdemo
```
4.cd  到项目里面
```
		cd  reactdemo
		npm start  运行项目（调试）
		npm run build 生成项目（发布）
```
### npx介绍：

npm v5.2.0引入的一条命令（npx），引入这个命令的目的是为了提升开发者使用包内提供的命令行工具的体验。

详情：
	http://www.phonegap100.com/thread-4910-1-1.html

npx create-react-app reactdemo这条命令会临时安装 create-react-app 包，命令完成后create-react-app 会删掉，不会出现在 global 中。下次再执行，还是会重新临时安装。
npx 会帮你执行依赖包里的二进制文件。

再比如 npx http-server 可以一句话帮你开启一个静态服务器

# 2.React目录结构  React创建组件、 ReactJSX语法、 React绑定数据 React绑定对象 、React绑定属性( 绑定class  绑定style 图片)
#### manifest.json 文件简介：
	https://lavas.baidu.com/mip/doc/engage-retain-users/add-to-home-screen/introduction
允许将站点添加至主屏幕，是 PWA 提供的一项重要功能，当前 manifest.json 的标准仍属于草案阶段，Chrome 和 Firefox 已经实现了这个功能，微软正努力在 Edge 浏览器上实现，Apple 目前仍在考虑中

#### super关键字：
参考：http://www.phonegap100.com/thread-4911-1-1.html

Es6中的super可以用在类的继承中，super关键字，它指代父类的实例（即父类的this对象）。子类必须在constructor方法中调用super方法，否则新建实例时会报错。这是因为子类没有自己的this对象，而是继承父类的this对象，然后对其进行加工。如果不调用super方法，子类就得不到this对象。
```
	class Person {
 	 	constructor (name) {
  	  		this.name = name;
  		}
	}

	class Student extends Person {
  		constructor (name, age) {
    			super(); // 用在构造函数中，必须在使用this之前调用
    			this.age = age;
 		 }
	}
```
##### 为什么官方的列子里面写个super(props)：
只有一个理由需要传递props作为super()的参数，那就是你需要在构造函数内使用this.props
那官方提供学习的例子中都是写成super(props)，所以说写成super(props)是完全没问题的，也建议就直接这样写。

# 3.React 创建组件、绑定属性( 绑定class  绑定style)、引入图片  循环数组渲染数据
1、所有的模板要被一个根节点包含起来

2、模板元素不要加引号

3、{}绑定数据      state数据

4、绑定属性注意：
class 要变成 className
for 要变成  htmlFor
style属性和以前的写法有些不一样
```
   		<div style={{'color':'blue'}}>{this.state.title}</div>


                <div style={{'color':this.state.color}}>{this.state.title}</div>
```
5、循环数据要加key

6、组件的构造函数中一定要注意 super

  子类必须在constructor方法中调用super方法，否则新建实例时会报错。这是因为子类没有自己的this对象，而是继承父类的this对象，然后对其进行加工。如果不调用super方法，子类就得不到this对象
```
  constructor(props){
        super(props);  /*用于父子组件传值  固定写法*/

        this.state={

            userinfo:'张三'
        }
    }
```
7、组件名称首字母大写、组件类名称首字母大写
# 4.React事件 方法、 React定义方法的几种方式 获取数据 改变数据 执行方法传值
在以类继承的方式定义的组件中，为了能方便地调用当前组件的其他成员方法或属性（如：this.state），通常需要将事件处理函数运行时的 this 指向当前组件实例。

### 绑定事件处理函数this的几种方法：

#### 第一种方法：
```
  	run(){

        	alert(this.state.name)
  	}
  	<button onClick={this.run.bind(this)}>按钮</button>
```
#### 第二种方法：

	构造函数中改变
```
	this.run = this.run.bind(this);


 	run(){

        	alert(this.state.name)
 	 }
 	<button onClick={this.run>按钮</button>
```
第三种方法：
```
	 run=()=> {
    		alert(this.state.name)
 	 }

	<button onClick={this.run>按钮</button>
```
# 5.React 键盘事件 表单事件 事件对象以及React中的ref获取dom节点 、React实现类似Vue的双向数据绑定

**事件对象：触发DOM上的某个事件，回产生一个事件对象event，对象包括所有与事件有关的信息**

##### alert(event.target);  获取执行事件的dom节点

#### 获取表单的值
1.监听表单的改变事件          `onChange`
2.在改变的事件里面获取表单输入的值     ` 事件对象`
3.把表单输入的值赋值给username    `this.setState({})`
4.点击按钮的时候获取state里面的username    `this.state.user`

#### ref方法：
#### 获取dom节点：
1.给元素定义ref属性 ` <input ref="username"  />`
2.通过`this.refs.username `获取dom节点

键盘事件：`KeyUp=KeyDown`
# 6.React表单详解 约束性和非约束性组件 input text checkbox radio  select  textarea  以及获取表单的内容
MVVM   {/*model改变影响view view改变反过来影响model  */}
主要用于表单中
#### React不是MVVM框架

value 与 defaultValue 的区别
#### 约束性组件与非约束性组件：

##### 非约束性组件：
`<input type="text" defaultValue=“a” /> `
这个defaultValue是原生DOM中的value属性，这样写出来，就是用户输入的内容，react完全不管理输入的过程

#### 约束性组件
`<input type="text" value={this.state.myuser} onChange={this.handleUsername} />`
这里 value不是一个写死的值 是由函数方法负责管理 这时的value不是用户输入的内容，是事件触发之后的this.setState的重新渲染，React会优化这个

select框
checkbox 多个值获取
# 7.React实现Todolist练习 （上）
### 用this时需要考虑指向！！！
# 9.React的模块化以及封装Storage实现todolist 待办事项 已经完成事项 以及实现数据持久化（下）

数据缓存功能

localStorage.setItem

生命周期函数

封装缓存功能

# 10.React中的组件、父子组件、React props父组件给子组件传值、子组件给父组件传值、父组件中通过refs获取子组件属性和方法

模块化组件化共用

不同组件调入相同组件，但是显示不同的内容

React中的组件: 解决html 标签构建应用的不足。


使用组件的好处：把公共的功能单独抽离成一个文件作为一个组件，哪里里使用哪里引入。

父子组件：组件的相互调用中，我们把调用者称为父组件，被调用者称为子组件

### 父子组件传值：（react父子组件通信）

#### 父组件给子组件传值

1.在调用子组件的时候定义一个属性`  <Header msg='首页'></Header>`

2.子组件里面 this.props.msg


说明：父组件不仅可以给子组件传值，还可以给子组件传方法,以及把整个父组件传给子组件。可以让子组件给父组件传值
以及把整个父组件传给子组件——用不了，提示找不到函数` {this}`

#### 父组件主动获取子组件的数据

  1、调用子组件的时候指定ref的值 `   <Header ref='header'></Header>`

  2、通过`this.refs.header  `获取整个子组件实例
  （dom（组件）加载完成以后获取）

# 11.React  propTypes  defaultProps
父组件给子组件传值：
defaultProps:父子组件传值中，如果父组件调用子组件的时候不给子组件传值，则可以在子组件中使用defaultProps定义的默认值

propTypes:验证父组件传值的类型
1. 引入` import PropTypes from ‘prop-types’;`

2.
```
类.propTypes={
          name:PropTypes.string
       };
```
应用 子组件中

# 12.React 获取服务器数据 axios插件 fetch-jsonp插件的使用
react获取服务器API接口的数据：
react中没有提供专门的请求数据的模块，可以使用任何第三方请求数据模块实现请求数据

### axios
axios作者认为jsonp不太友好，推荐使用CORS方式更为干净（后端运行跨域）
1.安装模块` npm install axios --save`
2.项目引入` import axios from 'axios'`
3.看文档使用
```
  var api='http://www.phonegap100.com/appapi.php?a=getPortalList&catid=20';
  axios.get(api)
  .then(function (response) {
    console.log(response.data.result);
  })
  .catch(function (error) {
    console.log(error);
  });
```
用this要注意指向

### fetch-jsonp
1.安装` npm install fetch-jsonp --save`
2.引入` import FetchJsonp from ‘fetch-jsonp’`
3.看文档
```
fetchJsonp('/users.jsonp')
  .then(function(response) {
    return response.json()
  }).then(function(json) {
    console.log('parsed json', json)
  }).catch(function(ex) {
    console.log('parsing failed', ex)
  })
```
#### 其他请求数据的方法也可以。。自己封装模块用原生js实现数据请求也可以

远程测试API接口：
get请求：
http://www.phonegap100.com/appapi.php?a=getPortalList&catid=20
jsonp请求：
http://www.phonegap100.com/appapi.php?a=getPortalList&catid=20&callback=?（callback后面参数随意，如果返回说明可以用jsonp）

# 13.React 生命周期函数
#### React生命周期函数：
  组件加载之前，组件加载完成，以及组件更新数据，组件销毁
  触发的一系列的方法，这就是组件的生命周期函数

#### 组件加载的时候触发的函数：
constructor、componentWillMount、render、componentDidMount（DOM操作）

#### 组件数据更新的时候触发的生命周期函数：
shouldComponentUpdate（需要返回值true）、componentWillUpdate、render、componentDidUpdate

你在父组件里面改变props传值的时候触发的：
componentWillReceiveProps

组件销毁的时候触发的：销毁哪个组件就写在哪里，然后再子组件监听
componentWillUnmount

**加载的时候：componentWillMount、render、componentDidMount**
**更新的时候：componentWillUpdate、render、componentDidUpdate**
**销毁的时候：componentWillUnmount**

# 14.React路由 react-router4.x的基本配置
### react-router  ——使根组件动态挂载不同子组件
根据用户访问的地址动态的加载不同的组件

1.官方文档：https://github.com/ReactTraining/react-router
web引用路由
2.安装：·npm install react-router-dom --save
3.找到项目根组件引入react-router-dom
引入：
`import { BrowserRouter as Router, Route, Link } from "react-router-dom";`
4.复制官网文档根组件里面的内容进行修改（加载的组件需要提前引入）
匹配路径里面有个 exact表示严格匹配

Link——用来做页面切换
```
<Router>
      <div>
        <Link to="/">Home</Link>
        <Link to="/news">News</Link>
       <Link to="/product">Product</Link>

        <Route exact path="/" component={Home} />
        <Route path="/news" component={News} />
        <Route path="/product" component={Product} />
      </div>
  </Router>
```
# 15.React路由 react-router4.x 动态路由以及get传值 React中使用url模块
一个页面跳转到另一个页面进行传值

1.get传值
解析地址——npm 搜索url——node.js的模块
?去掉 然后切割分组

url模块解析url地址
使用url模块需要安装`  cnpm install url --save`
```
1.获取
       console.log(this.props.location.search);
       console.log(url.parse(this.props.location.search,true));
       var aid=url.parse(this.props.location.search,true).query.aid;
       console.log(aid);
 <Link to={`/productcontent?aid=${value.aid}` }> {value.title}</Link>
2.动态路由
     1.根组件配置路由
      <Route path="/content/:aid" component={Content} />
     2.对应的动态路由加载的组件里面获取传值
     console.log(this.props.match.params);

注意跳转页面： <Link to={`/content/${value.aid}`}> {value.title}</Link>
3.Localstorage
```
# 16.React【无人点餐无人收银系统案例】路由配置、菜品列表制作、请求数据渲染二维数组、 动态路由传值【基础项目】
列表：http://a.itying.com/api/productlist
本地图片直接写
远程图片模块化引入
详情：http://a.itying.com/api/productcontent?id=5ac1a22011f48140d0002955

三列布局：
1.flex布局
父元素：`display:flex`
       `  flex-wrap:wrap`
每个子元素宽度 33%

2.react渲染二维数组
# 17.React【无人点餐无人收银系统案例】菜品详情请求api渲染数据 以及解析Html【基础项目】
#### VUE解析html  通过v-html
#### React解析html 看文档

# 18.React 渲染数据注意事项、以及react-router4.x中使用js跳转路由
##### 实现js跳转路由：
1.引入Redirect
```
import {
  BrowserRouter as Router,
  Route,
  Link,
  Redirect,
  withRouter
} from "react-router-dom";
```
2.定义一个flag
```
        this.state = {
            loginFlag:false
        };
```
3.执行判断loginFlag来决定是否跳转
render里面
```
        if(this.state.loginFlag){
            return <Redirect to={{pathname: "/"}} />;
        }
```
4.要执行js跳转
通过js改变loginFlag的状态
改变以后从新render就可以通过Redirect自己来跳转

# 19.React  react-router4.x路由的嵌套
路由嵌套
上边不变、右边不变、中间页面跟着按钮走

# 20.React react-router4.x中实现路由模块化、以及嵌套路由父子组件传值
路由路径是一个数组
路由模块化

# 21.React UI框架Antd(Ant Design)的使用 以及react Antd的使用 button组件 Icon组件 Layout组件 DatePicker日期组件
1.antd官网：

	https://ant.design/docs/react/introduce-cn
2、React中使用Antd
```
1、安装antd   npm install antd --save /yarn add antd /cnpm install antd --save
2、在您的react项目的css文件中引入 Antd的css

		@import '~antd/dist/antd.css';

3、看文档使用：

如使用Button：

	1、在对应的组件中引入Antd        import { Button } from 'antd';

	2、<Button type="primary">Primary</Button>
```
# 22.React UI框架 Antd (Ant Design)配置react-app-rewired按需加载Antd的css
3、React中使用Antd高级配置，按需引入css样式

我们现在已经把组件成功运行起来了，但是在实际开发过程中还有很多问题，例如上面的例子实际上加载了全部的 antd 组件的样式（对前端性能是个隐患）。
```
1、安装antd         npm install antd --save

2、安装（react-app-rewired）一个对 create-react-app 进行自定义配置的社区解决方案
	   yarn add react-app-rewired    /  cnpm install  react-app-rewired --save

3、修改 package.json

	react-scripts 需改为react-app-rewired

  	"scripts": {
    		"start": "react-app-rewired start",
    		"build": "react-app-rewired build",
    		"test": "react-app-rewired test --env=jsdom",
    		"eject": "react-app-rewired eject"
 	 }

4、在项目根目录创建一个 config-overrides.js 用于修改默认配置
	module.exports = function override(config, env) {
 		 // do stuff with the webpack config...
 	 return config;
	};
5、安装babel-plugin-import   babel-plugin-import是一个用于按需加载组件代码和样式的 babel 插件

		yarn add babel-plugin-import   /  cnpm install babel-plugin-import --save

6、修改 config-overrides.js

	const { injectBabelPlugin } = require('react-app-rewired');

  	module.exports = function override(config, env) {
   	 config = injectBabelPlugin(
     		   ['import', { libraryName: 'antd', libraryDirectory: 'es', style: 'css' }],
        	   config,
  	  );
   	 return config;
 	 };

7、然后移除前面在 src/App.css 里全量添加的 @import '~antd/dist/antd.css'; 直接引入组件使用就会有对应的css

		import { Button } from 'antd';

		<Button type="primary">Primary</Button>
```
高级配置：css按需引入

### 本React基础知识是看大地老师视频学习的！！！
