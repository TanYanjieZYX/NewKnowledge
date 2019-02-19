# 1.无人点餐 无人收银系统 多用户点餐 智能打单 在线支付系统介绍
## 项目介绍：
无人点餐、无人收银系统是一个颠覆传统行业的智能点单系统。无人点单、手机支付、免收银员、免点餐员、免硬件、免布线的一套智能管理系统。
## 项目功能介绍：
扫码点餐，让每一个桌码都成为您的点餐、收银通道。微信/支付宝扫一扫，不用排队，上桌点餐，多人点餐，自动收银，解放老板娘，减少开支。
## 无人点餐、无人收银系统主要功能介绍：
1.用VUE和Angular两种语言分别开发，方便不同公司、学员学习使用
2.支持微信、支付宝、浏览器多种扫码工具扫码点餐、
3.系统支持多人扫码点餐，点餐信息通过websocket同步（解决传统点餐的尴尬场景）
4.下单无线打印小票，后厨、服务员同时收到订单信息
5.微信、支付宝在线支付，自动收银，方便大数据分析
## 适用场景——餐饮店以及KTV
传统中西餐、快餐店、奶茶店、火锅店、咖啡店、甜品店、大排档、酒吧、小吃店、KTV
# 2.Vue的介绍 Vue环境搭建  运行项目
前端技术薪资介绍
*	Html5+Css3+Jquery   PC端  移动端静态页面     6k-8k
*	Angular 、 Vue  、React             10k+
*	Nodejs                              13+
*	混合app开发  Ionic   ReactNative     15k+

Vue和Angular、React都是前端框架
1. 单页面框架
2. 基于模块化组件化的开发模式

中国人开发很重要——Vue简单 灵活 高效   国内的中小企业里面用的非常多
### cnpm——下载包的速度更快一些。
	地址：http://npm.taobao.org/

	安装cnpm:

	npm install -g cnpm --registry=https://registry.npm.taobao.org
### 搭建vue的开发环境：

	https://cn.vuejs.org/v2/guide/installation.html

1. 必须要安装nodejs

2. 搭建vue的开发环境 ，安装vue的脚手架工具   官方命令行工具

      npm install --global vue-cli/cnpm install --global vue-cli
			（此命令只需要执行一次）

3. 创建项目   必须cd到对应的一个项目里面

		vue init webpack vue-demo01（创建的时候ESLint选择no,是一个代码检查器）

		cd  vue-demo01

		cnpm install   /  npm install    如果创建项目的时候没有报错，这一步可以省略。
		如果报错了  cd到项目里面运行  cnpm install   /  npm install

		npm run dev

4. 另一种创建项目的方式   （推荐）  ***

		vue init webpack-simple vuedemo02

		cd  vuedemo02

		cnpm install   /  npm install

		npm run dev

# 3.Vue目录结构分析  绑定数据 绑定对象 循环数组渲染数据
1. cd 到demo里面
2. 安装依赖： cnpm install
3. 运行项目   npm run dev

* node_modules 项目需要的各种模块
* src 配置的各种资源
* index.html   html的入口文件
* package.json 项目配置文件
* readme.md 项目介绍文件
* webpack.config  webpack的配置文件

`<template> `html代码
`<script> `业务逻辑，JS代码
`<style> `css代码

实例化VUE
VUE的模板里面 所有的内容需要被一个根节点包含起来
所有东西都在`<template>`中的`<div>`里面

业务逻辑：
data()——业务逻辑里面定义的数据
绑定数据——{{msg}}
绑定对象——{{obj.name}}
绑定数组——数据渲染，数组嵌套

### 代码示例：
```
list:['111','222','333'],
　　list1:[
　　　　{'title':'111'},
　　　　{'title':'222'},
　　　　{'title':'333'},
　　　　{'title':'444'}
　　　　],
　　　　list2:[
　　　　  {
           "cate":"国内新闻",
           "list":[
              {'title':'国内新闻111'},
              {'title':'国内新闻222'}
           ]
          },
          {
           "cate":"国际新闻",
           "list":[
              {'title':'国际新闻111'},
              {'title':'国际新闻222'}
           ]
          }
      ]

<ul id="example-1">
         <li v-for="item in list">
            {{ item }}
         </li>
    </ul>
    <br />
    <hr />
    <ul id="example-2">
         <li v-for="item1 in list1">
            {{ item1.title }}
         </li>
    </ul>
    <br />
    <hr />
    <ul id="example-3">
         <li v-for="item2 in list2">
            {{ item2.cate }}
            <ol>
               <li v-for="news in item2.list">
                   {{ news.title}}
               </li>
            </ol>
         </li>
    </ul>`
```
挂载组件

# 4.Vue绑定属性 绑定Html  绑定class  绑定style
数据绑定到属性上去
```
    <div v-bind:title="title">鼠标喵上去看一下</div>
     <img :src="url" />——简写，动态绑定数据
```
绑定html-让浏览器解析html代码
```
<div v-html="h"></div>
其中——h:'<h2>我是h2</h2>',
```
绑定数据另一种方式
```
    <div v-text="msg"></div>
```
绑定Class与Style
```
<v-bind:class   :class的使用>
 <!-- 循环数据 第一个数据高亮 -->
<ul id="example-5">
      <li v-for="(item,key) in list" :class="{'red':key==0,'blue':key==1}">
          {{key}}--{{ item }}
      </li>
</ul>

<v-bind:style   :style的使用>
 <div class="box"  v-bind:style="{width:boxWidth + 'px' }">
      我是一个Div
 </div>
```
style css里面要写东西
```
<style lang="scss">
.red{
    color:red;
  }

.blue{
    color:blue;
  }

.box{
  height:100px;
  width:100px;
  background: red;
}
</style>
```
# 5.Vue 及双向数据绑定 Vue事件介绍 以及Vue中的ref获取dom节点
#### 自定义方法要放在export default里面
双向数据绑定 MVVM vue是一个MVVM框架
Model改变会影响View View改变反过来影响Model
借鉴Angular
双向数据绑定必须在表单中——input、select
```
 <input type="text" v-model='msg' />
  <button v-on:click="getMsg()">获取表单里面的数据</button>
  <button v-on:click="setMsg()">设置表单里面的数据</button>
```
#### 获取表单数据——DOM节点
`<hr>`横线
`<br>`换行

ref获取DOM节点
```
    <input type="text" ref="userinfo" />
   <div ref="box">我是一个box</div>
    <button v-on:click="getInputValue()">获取第二个表单里面的数据</button>
    getInputValue(){
       //获取ref定义的dom节点
      console.log(this.$refs.userinfo);
 this.$refs.box.style.background='red';
      alert(this.$refs.userinfo.value);
}
```
# 6.Vue事件 定义方法 执行方法  获取数据 改变数据 执行方法传值 以及事件对象
#### 事件对象——可以获取DOM节点
```
 <button @click="eventFn('$event') ">事件对象</button>
e.srcElement
```
```
<br />
    <hr />
    <button v-on:click="run1()">执行方法的第一种写法</button>

    <button @click="run2()">执行方法的第一种写法</button>
    <br />
    <hr />
    <button @click="getMsg()">获取数据-data里面的msg</button>
    <br />
    <hr />
    <button @click="setMsg()">设置数据-data里面的msg</button>
    <br />
    <hr />
    <button @click="setMsg()">设置数据-data里面的msg</button>
    <br />
    <hr />
    <button @click="requestData()">请求数据-data里面的msg</button>
    <br />
    <hr />
    <ul>
      <li v-for="(item,key) in list">
           {{key}}----{{item}}
      </li>
    </ul>
    <br />
    <hr />
    <button @click="deleteData('111') ">执行方法传值</button>
    <br />
    <hr />
    <button data-aid="123" @click="eventFn($event) ">事件对象</button>
```
#### 方法函数：
```
 getMsg() {
        alert(this.msg);
        //小程序 获取数据——this.data.msg
        //React 获取数据——this.state.msg
    },
    setMsg(){
       this.msg='我将数据改变了';
    },
    requestData(){
      for(var i=0;i<10;i++){
        this.list.push('我是第'+i+'条数据');
      }
    },
    deleteData(val){
      alert(val);

    },
    eventFn(e){
      console.log(e);
      e.srcElement.style.background='red';

      console.log(e.srcElement.dataset.aid);   /*获取自定义属性的值*/

}
```
# 7.Vue 事件结合双向数据绑定实现todolist
#### addData()
1. 获取文本框输入的值
2. 把文本框的值push到list里面
```
   addData(){
       this.list.push(this.todo);
       this.todo='';
    }
```
#### deleteData()
数组索引获取，再删除
```
    deleteData(key){
          this.list.splice(key,1);
    }
```
# 8.Vue 事件结合双向数据绑定实现todolist 待办事项 已经完成 和进行中
# 9.Vue 中的模块化以及封装Storage实现todolist 待办事项 已经完成 和进行中持久化
生命周期函数与methods、data同级关系
```
 /*生命周期函数，vue页面刷新就会触发*/
      mounted(){
            var list=storage.get('list');
            if(list){   /*注意判断传过来的值是否为空 */
              this.list=list;
            }
      }
```
# 10.Vue中创建单文件组件 注册组件  以及组件的使用
#### App.vue---根组件
1. 引入组件
import Home from './components/Home.vue';
2. 挂载组件
前面的组件名称不可以和html标签一样
```
 components:{
        'v-home':Home
  }
```
3. 模板中使用

style引用——父组件同时也会变
//作用域定义使用的地方
1. 加一个辨识符 id
2. scoped——css局部作用域

# 11.Vue中组件的生命周期函数
生命周期函数（生命周期钩子）：
组件挂载、组件更新、组件销毁的时候触发的一系列的方法 这些方法叫做生命周期函数
```
 beforeCreate(){
        console.log('01实例刚刚被创建');
    },
    Create(){
        console.log('02实例创建完成');
    },
    beforeMount(){
        console.log('03模板编译之前');
    },
    mounted(){   请求数据、操作DOM放在这个里面 必须记住
        console.log('04模板编译完成');
    },
    beforeUpdate(){
        console.log('05数据更新之前');
    },
    updated(){
        console.log('06数据更新完毕');
    },
    beforeDestroy(){   页面销毁的时候要保存一些数据，可以监听这个销毁的生命周期函数
        console.log('07实例销毁之前');
    },
    destroyed(){
     console.log('08实例销毁完成');
}
```
# 12.Vue vue-resource 请求数据
## VUE请求数据：
### 官方：vue-resource 官方插件
1. 安装vue-resourse
进入项目目录安装
cnpm install vue-resource --save(会配置好package)
2. main.js引入
```
import VueResource from 'vue-resource';
Vue.use(VueResource);
```
3. 在组件里面使用
```
{
  // GET /someUrl
  this.$http.get('/someUrl').then(response => {

    // get body data
    this.someData = response.body;

  }, response => {
    // error callback
  });
}
```
### 非官方也可以使用的插件
axios
fetch-jsonp

# 13.Axios  fetchJsonp请求数据
### axios使用：
1. cnpm install axios --save
2. 哪里用哪里引用
import Axios from 'axios';
3. 使用代码
```
var api='http://www.phonegap100.com/appapi.php?a=getPortalList&catid=20';
 getData(){
              var api='http://www.phonegap100.com/appapi.php?a=getPortalList&catid=20';
              Axios.get(api).then(response=> {
                    // handle success
                    console.log(response);
                    this.list1 = response.data.result;
                }) .catch(error=>{
                    // handle error
                    console.log(error);
                });
         }
```

# 14.Vue父组件给子组件传值 Vue父组件给子组件传方法  Vue父组件把整个实例传给子组件
### 父组件给子组件传值：
1. 父组件文件下——调用子组件时动态绑定属性
   `<v-header :title="title" />`
2. 子组件接收父组件传过来的数据 props
    ` props:['title'] （与methods同级）`

父组件给子组件传方法：
```
   <v-header :title="title" :run="run" />
   props:['title','run']
```
父组件给子组件传方法（方法中带参数）：

父组件传整个传过去
```
   <v-header :title="title" :run="run" :home="this" />
     getParent(){
        // alert(this.title); ——————无效
        // alert(this.home.title);
        this.home.run('123');
     }
```
props合法性验证：
接收数据是一个对象

# 15.父组件主动获取子组件的数据和方法   子组件主动获取父组件的数据和方法
父组件主动获取子组件的数据和方法
1. 调用子组件的时候定义一个ref
  `<v-header ref="header" />`
2. 在父组件里面通过
```
   this.$refs.header.属性
   this.$refs.header.方法
```
获取子组件的数据和方法
子组件主动获取夫组件的数据和方法
```
this.$parent.数据
this.$parent.方法
```
# 16.Vue非父子组件传值
#### 非父子组件传值：
1. 借助父子组件来，直到找到有关系的那一层
2. 空的VUE实例作为事件总线
```
var bus= new Vue();
//触发组件A中的事件
bus.$emit('id-selectes',1)
//在组件B创建的钩子中监听事件
bus.$on('id-selected',function(id){

})
```
#### 复杂情况考虑专门的状态管理模式

1. 新建一个js文件 引入vue 实例化vue 暴露实例
```
import Vue from 'vue'
var VueEvent = new Vue()
export default VueEvent;
```
2. 在需要广播的地方引入刚才定义的实例
import VueEvent from '../model/VueEvent';

3. 通过
```
         emitHome(){
            VueEvent.$emit('to-home',this.msg);
         }
注意'to-home'是有标识性的
```
4. 在接收数据的地方通过`$on`接收广播的数据
```
mounted(){
        VueEvent.$on('to-news',function(data){
            console.log(data);
        })
}
```
# 17.Vue中的路由 以及默认路由跳转
https://router.vuejs.org/
vue路由配置：
1. 安装
	npm install vue-router  --save   / cnpm install vue-router  --save

2. 引入并 `Vue.use(VueRouter)   (main.js)`
```
		import VueRouter from 'vue-router'
		Vue.use(VueRouter)
```

3. 配置路由
```
1、创建组件 引入组件

2、定义路由  （建议复制s）

			const routes = [
			  { path: '/foo', component: Foo },
			  { path: '/bar', component: Bar },
			  { path: '*', redirect: '/home' }   /*默认跳转路由*/
			]
3、实例化VueRouter
			const router = new VueRouter({
			  routes // （缩写）相当于 routes: routes
			})

4、挂载
		new Vue({
		  el: '#app',
		  router，
		  render: h => h(App)
		})

5 、根组件的模板里面放上这句话   <router-view></router-view>

6、路由跳转
		<router-link to="/foo">Go to Foo</router-link>
	  <router-link to="/bar">Go to Bar</router-link>
```
# 18.Vue动态路由 Get传值
#### 路由之间的传值：动态路由：
1.配置动态路由
```
const routes = [
  { path: '/home', component: Home },
  { path: '/news', component: News },
  { path: '/content/:aid', component: Content },   /*动态路由*/
  { path: '*', redirect: '/home' }   /*默认跳转路由*/
]
```
2.对应页面获取动态路由的值
```
   mounted(){
        console.log(this.$route.params); /*获取动态路由传值 */
    }

    <ul>
        <li v-for="(item,key) in list">
          <router-link :to="'/content/'+key"> {{key}}----{{item}}</router-link>
        </li>
    </ul>
```
路由之间的传值：get传值
路由跟普通路由一样  `{ path: '/pcontent', component: Pcontent },`
```
mounted(){
       //get传值
       console.log(this.$route.query);
    }
  <ul>
      <li v-for="(item,key) in list">
        <router-link :to="'/pcontent?aid='+key"> {{key}}----{{item}}</router-link>
      </li>
  </ul>
```
# 19.Vue路由结合请求数据 实现新闻列表 新闻详情数据渲染
新闻列表接口：

	http://www.phonegap100.com/appapi.php?a=getPortalList&catid=20&page=1

新闻详情接口：
```
	 http://www.phonegap100.com/appapi.php?a=getPortalArticle&aid=488

 methods:{
      requestData(){
        //jsonp请求的话 后台api需要支持jsonp
        var api='http://www.phonegap100.com/appapi.php?a=getPortalList&catid=20&page=1';
         this.$http.jsonp(api).then(function(response){
             console.log(response);
         },function(err){
            console.log(err);
         })
      }
    },
    mounted(){//执行请求数据方法
      this.requestData();
    }
```
解析后台传过来的html代码
```
   <div v-html="list.content">

   </div>
```
加样式、视口  到index.html里面加

# 20.Vue路由编程式的导航  以及vue路由History 模式 hash 模式
编程式导航
JS来跳转页面（路由跳转）——登录页面成功来确定
官方文档有错误
```
      goNews(){
        对象
        this.$router.push({path:'news'});
        this.$router.push({path:'content/495'});
        命名路由
       this.$router.push（{name:'user',params:{userId:123}}）

        { path: '/news', component: News, name:'news' },
          this.$router.push({name:'news'});
      }
```
HTML5 History模式
hash模式转换为history模式
```
const router = new VueRouter({
  mode: 'history',
  routes: [...]
})
```
要结合后台服务器端配合
# 21.Vue中路由的嵌套
路由的嵌套
1. 配置路由
```
 { path: '/user',
    component: User,
    children:[
      {
        path: 'useradd',
        component: UserAdd
      },
      {
        path: 'userlist',
        component: UserList
      }
    ]
  },
```
2. 父路由里面配置子路由显示的地方
`  <router-view></router-view>`
# 22.Vue UI框架Mint UI的使用  button  索引列表  ActionSheet等
基于Vue的Ui框架

	饿了么公司基于vue开的的vue的Ui组件库

		Element Ui    基于vue  pc端的UI框架

		MintUi         基于vue 移动端的ui框架

http://element.eleme.io/

http://mint-ui.github.io/#!/en

mintUI的使用：

1. 找官网
2. 安装   npm install mint-ui -S         -S表示  --save
3. 引入mint Ui的css 和 插件——main.js
```
		import Mint from 'mint-ui';
		Vue.use(Mint);
		import 'mint-ui/lib/style.css'
```
4.看文档直接使用。

在mintUi组件上面执行事件的写法
```
@click.native
<mt-button @click.native="sheetVisible = true" size="large">点击上拉 action sheet</mt-button>
```
style
创建项目的时候必须选**SCSS**
# 23.Vue UI框架Mint Ui  infinite-scroll结合api接口实现真实上拉分页加载更多
**Infinite scroll
无限滚动指令。**

1. 上拉分页加载更多
```
    <ul
    v-infinite-scroll="loadMore"
    infinite-scroll-disabled="loading"
    infinite-scroll-distance="10" class="list">
         <li v-for="item in list">{{ item }}</li>
    </ul>

j为全局变量——j=0
      loadMore(){
           for(var i=0;i<20;i++,this.j++){
               this.list.push('第'+this.j+'条');
           }
           console.log('Yes');
     }
```
2. 真实的api数据
```
loadMore(){
         this.requestData();
     },
requestData(){
        this.loading=true;   /*请求数据的开关 */

        var api='http://www.phonegap100.com/appapi.php?a=getPortalList&catid=20&page='+this.page;

        this.$http.get(api).then((response)=>{
            console.log(response);
            this.list=this.list.concat(response.body.result);
            ++this.page;   /*每次请求完成page++ */
            this.loading=false;    /*请求数据的开关 */

            /*判断最后一页是否有数据 */
            if(response.body.result.length<20){
                 this.loading=true;    /*终止请求 */
            }else{
                this.loading=false;   /*继续请求 */
            }
        },(err)=>{
             console.log(err);
        })
     }
```
# 24.Vue UI框架 ElementUi的使用 以及webpack.config.js配置
http://element.eleme.io/

element UI的使用：
1. 找官网  http://element.eleme.io/#/zh-CN/component/quickstart
2. 安装  cnpm i element-ui -S         -S表示  --save
3. 引入element UI的css 和 插件
```
		import ElementUI from 'element-ui';
		import 'element-ui/lib/theme-chalk/index.css';
		Vue.use(ElementUI);
```
4. *webpack.config.js  配置file_loader
	http://element.eleme.io/1.4/#/zh-CN/component/quickstart
```
		  {
			test: /\.(eot|svg|ttf|woff|woff2)(\?\S*)?$/,
			loader: 'file-loader'
	          }
```
5. 看文档直接使用。

##### element UI组件的单独使用（第一种方法）：
1. cnpm install babel-plugin-component -D


2. 找到.babelrc 配置文件
```
		{
		  "presets": [
		    ["env", { "modules": false }],
		    "stage-3"
		  ]
		}

		改为  注意：

		{
		  "presets": [["env", { "modules": false }]],
		  "plugins": [
		    [
		      "component",
		      {
			"libraryName": "element-ui",
			"styleLibraryName": "theme-chalk"
		      }
		    ]
		  ]
		}
```
3.
```
	import { Button, Select } from 'element-ui';
	Vue.use(Button)
	Vue.use(Select)
```
##### element UI组件的单独使用（第二种方法）：
```
	import { Button, Select } from 'element-ui';

	Vue.use(Button)
	Vue.use(Select)

	引入对应的css
		import 'element-ui/lib/theme-chalk/index.css';

	如果报错： webpack.config.js  配置file_loader

		  {
			test: /\.(eot|svg|ttf|woff|woff2)(\?\S*)?$/,
			loader: 'file-loader'
	          }


 <i style="font-size:40px;" class="el-icon-delete"></i>

或者加class配置图标的样式
```
# 25.Vue UI框架 ElementUi 按需引入
#### 按需引入
element UI组件的单独使用（第一种方法）：

1. cnpm install babel-plugin-component -D

2. 找到.babelrc 配置文件
```
		把
		{
		  "presets": [
		    ["env", { "modules": false }],
		    "stage-3"
		  ]
		}

		改为  注意：
		{
		  "presets": [["env", { "modules": false }]],
		  "plugins": [
		    [
		      "component",
		      {
			"libraryName": "element-ui",
			"styleLibraryName": "theme-chalk"
		      }
		    ]
		  ]
		}
```
3.
```
	import { Button, Select } from 'element-ui';

	Vue.use(Button)
	Vue.use(Select)
```
element UI组件的单独使用（第二种方法）：
```
	import { Button, Select } from 'element-ui';

	Vue.use(Button)
	Vue.use(Select)

	引入对应的css

		import 'element-ui/lib/theme-chalk/index.css';

	如果报错： webpack.config.js  配置file_loader

		  {
			test: /\.(eot|svg|ttf|woff|woff2)(\?\S*)?$/,
			loader: 'file-loader'
	     }
```
# 26.vue 路由模块化
**路由模块分离
单独一个文件**
```
//引入库
import Vue from 'vue'

import VueRouter from 'vue-router'

Vue.use(VueRouter);
```
在独立的文件route.js
1. 创建组件
```
import Home from '../components/Home.vue';
import News from '../components/News.vue';
import Content from '../components/Content.vue';
import Pcontent from '../components/Pcontent.vue';
import User from '../components/User.vue';
   import UserAdd from '../components/User/UserAdd.vue';
   import UserList from '../components/User/UserList.vue';
```
2. 配合路由
```
const routes = [
  { path: '/home', component: Home },
  { path: '/user',
    component: User,
    children:[
      {
        path: 'useradd',
        component: UserAdd
      },
      {
        path: 'userlist',
        component: UserList
      }
    ]
  },
  { path: '/news', component: News, name:'news' },
  { path: '/content/:aid', component: Content },   /*动态路由*/
  { path: '/pcontent', component: Pcontent },
  { path: '*', redirect: '/home' }   /*默认跳转路由*/
]
```
3. 实例化VueRouter 注意router与routes的区别
```
const router = new VueRouter({
  mode: 'history',
  routes
})

export default router;
```
4. 再在main.js引入router挂载

# 27.Vuex 的使用 State  Mutation  实现多个页面共享计数
Vuex 是一个专为 Vue.js 设计的状态管理模式

vuex解决了组件之间同一状态的共享问题。当我们的应用遇到多个组件共享状态时，会需要：

多个组件依赖于同一状态。传参的方法对于多层嵌套的组件将会非常繁琐，并且对于兄弟组件间的状态传递无能为力。这需要你去学习下，vue编码中多个组件之间的通讯的做法。
来自不同组件的行为需要变更同一状态。我们经常会采用父子组件直接引用或者通过事件来变更和同步状态的多份拷贝。

以上的这些模式非常脆弱，通常会导致无法维护的代码。来自官网的一句话：Vuex 是一个专为 Vue.js 应用程序开发的状态管理模式。

它采用集中式存储管理应用的所有组件的状态。这里的关键在于集中式存储管理。这意味着本来需要共享状态的更新是需要组件之间通讯的，而现在有了vuex，就组件就都和store通讯了。问题就自然解决了。

这就是为什么官网再次会提到Vuex构建大型应用的价值。如果您不打算开发大型单页应用，使用 Vuex 可能是繁琐冗余的。确实是如此——如果您的应用够简单，您最好不要使用 Vuex。


Vuex 是一个专为 Vue.js 应用程序开发的状态管理模式
  不是父子组件 也不是兄弟组件 也不是之前非父子组件一样

1. vuex解决了组件之间同一状态的共享问题  （解决了不同组件之间的数据共享）

2. 组件里面数据的持久化。
小项目用localStorage实现、SessionStorage实现数据共享
大项目就用Vuex
小项目不部建议用vuex

### vuex的使用：
1、src目录下面新建一个vuex的文件夹

2、vuex 文件夹里面新建一个store.js

3、安装vuex

		cnpm install vuex --save
4、在刚才创建的store.js引入vue  引入vuex 并且use vuex
```
		import Vue from 'vue'
		import Vuex from 'vuex'

		Vue.use(Vuex)
```
5、定义数据
```
			/*1.state在vuex中用于存储数据*/
			var state={

			    count:1
			}
```
6、定义方法	 mutations里面放的是方法，方法主要用于改变state里面的数据
```
		var mutations={

		    incCount(){

			++state.count;
		    }
		}

	暴露

		const store = new Vuex.Store({
		    state,
		    mutations
		})

		export default store;
```
### 组件里面使用vuex：
1. 引入 store store的名字不要变

			 import store from '../vuex/store.js';

2. 注册
```
 export default{
		data(){
		    return {
		       msg:'我是一个home组件',
			value1: null,

		    }
		},
		store,
		methods:{
		    incCount(){

			this.$store.commit('incCount');   /*触发 state里面的数据*/
		    }

		}
	    }
```
3. 获取state里面的数据

		 `this.$store.state.数据`

4. 触发 mutations 改变 state里面的数据

	`this.$store.commit('incCount');`


提交载荷（Payload）
你可以向 store.commit 传入额外的参数，即 mutation 的 载荷（payload）：

# 28.Vuex 的使用 State  Mutation Getter Action  以及实现不同组件新闻数据共享 以及新闻数据的持久化
Vuex 是一个专为 Vue.js 应用程序开发的状态管理模式

1. vuex解决了组件之间同一状态的共享问题  （解决了不同组件之间的数据共享）

2. 组件里面数据的持久化。

小项目不部建议用vuex

getter 与 action 一般用不上
getter ：改变数据时做一些操作
### vuex的使用：
1、src目录下面新建一个vuex的文件夹

2、vuex 文件夹里面新建一个store.js

3、安装vuex

		cnpm install vuex --save

4、在刚才创建的store.js引入vue  引入vuex 并且use vuex
```
		import Vue from 'vue'
		import Vuex from 'vuex'

		Vue.use(Vuex)
```
5、定义数据
```
			/*1.state在vuex中用于存储数据*/
			var state={

			    count:1
			}
```
6、定义方法	 mutations里面放的是方法，方法主要用于改变state里面的数据
```
		var mutations={

		    incCount(){

			++state.count;
		    }
		}
```
7、优点类似计算属性   ，  改变state里面的count数据的时候会触发 getters里面的方法 获取新的值 (基本用不到)
```
		var getters= {

		    computedCount: (state) => {
			return state.count*2
		    }
		}
```
8、 Action 基本没有用
```
		Action 类似于 mutation，不同在于：

		Action 提交的是 mutation，而不是直接变更状态。
		Action 可以包含任意异步操作。

		var actions= {
		    incMutationsCount(context) {    /*因此你可以调用 context.commit 提交一个 mutation*/


			context.commit('incCount');    /*执行 mutations 里面的incCount方法 改变state里面的数据*/


		    }
		}

	暴露

		const store = new Vuex.Store({
		    state,
		    mutations,
		    getters,
		    actions
		})

		export default store；
```
### 组件里面使用vuex：
1、 引入 store

			` import store from '../vuex/store.js';`

2、 注册
```
			 export default{
				data(){
				    return {
				       msg:'我是一个home组件',
					value1: null,

				    }
				},
				store,
				methods:{
				    incCount(){

					this.$store.commit('incCount');   /*触发 state里面的数据*/
				    }

				}
			    }
```
3、 获取state里面的数据

		`	this.$store.state.数据`

4、 触发 mutations 改变 state里面的数据

			`this.$store.commit('incCount');`

5、 触发 actions里面的方法

			`this.$store.dispatch('incCount');`

6、获取 getters里面方法返回的的数据
`{{this.$store.getters.computedCount}} `

### 本Vue基础知识是看大地老师视频学习的！！！
