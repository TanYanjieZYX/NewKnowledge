# MarkDown的基础知识
## 1. 介绍
Markdown是一种轻量级的标记语言，Markdown的目标是实现易读易写，成为一种适用于网络的书写语言。如果你要写网络文档，情况可能更糟，如果需要呈现一个列表，您需要使用`<ul><li>`等若干多的标签实现；我们的写作思路经常会被各种各样的排版操作而打断，使我们不能专注于写作。可以轻松转换成html格式、pdf格式
### Markdown优点
1. 专注内容
使作者可以更加关注文章内容、更加关注写作本身。
2. 易学易写易读
语法简单，容易学习。操作简单，容易书写。格式简洁大方，可读性强。
3. 兼容性强
纯文本内容，兼容几乎所有的文本编辑器和html编辑器。
4. 格式转换方便
可以轻松导出为HTML格式、PDF格式、MD格式，便于实现文章内容的存储和传播，例如将博客转存为电子书，例如将博客发布到hexo博客系统等。
5. 功能强大
兼容html语法、特殊字符自动转换、轻松绘制表格、公式、流程图等。
### Markdown的缺点
1. 格式难于自定义
因为Markdown更加关注内容、更加关注写作本身，因此Markdown在格式自定义方面有所欠缺，例如Markdown默认链接在新页面打开，更改起来比较麻烦，需要编写额外代码实现功能。
2. 需要额外编译器
浏览器不会默认编译Markdown，需要额外的编译器进行编译。
## 2. MD基本语法
文本格式化
**图片**

|      Markdown代码      |                  HTML代码                  |
|:----------------------:|:------------------------------------------:|
|      `*斜体文字*	`      |            `<em>斜体文字</em>`             |
|     `**加粗文字**`     |        `<strong>加粗文字</strong>`         |
| `***加粗的斜体文字***	` | `<strong><em>加粗的斜体文字</em></strong>` |
| `~~添加删除线的文字~~	` |       `<del>添加删除线的文字</del>`        |
|   `> 这里是一段引用	`   | ` <blockquote>这里是一段引用</blockquote>` |

Markdown 支持两种标题的语法，_类 Setext_ 和_类 atx 形式_。类Atx形式则是在行首插入1到6个#，对应到标题1到标题6.

Markdown通过在引用的文字之前添加”>”标记达到引用的效果，引用段落的时候可以偷懒只在整个段落的第一行最前面加上 >。引用里面可以使用强调、链接等其他语法。
引用可以嵌套，使用不同数量的“>”表示层次

使用反引号``包含实现行内代码。
如果需要在代码内插入反引号，需要多个反引号开始和结束一段代码。
如果需要代码块和语法高亮，可以采用三个反引号的方式，同时可以注明语言类型。

### 无序列表使用星号、加号或是减号作为列表标记，如果不按列表显示，前面记得加一空行。
使用数字接着一个英文句点表示一个有序列表，注意前面的数字对列表没有影响。
列表可以嵌套，添加tab缩进表示层次。
列表项里可以包含多个段落，每个项目下的段落都必须缩进 4 个空格或是 1 个制表符

你可以在一行中用三个以上的星号、减号、底线来建立一个分隔线，行内不能有其他东西。你也可以在星号或是减号中间插入空格。

Markdown 可以利用反斜杠来实现转义， 支持以下这些符号前面加上反斜杠来帮助插入普通的符号：
**图片**

### 链接地址
Markdown 支持两种形式的链接语法： 行内式和参考式两种形式

首先来看行内式，只要在方块括号后面紧接着圆括号并插入网址链接即可，如果你还想要加上链接的 title 文字，只要在网址后面，用双引号把 title 文字包起来即可。
EX：`欢迎大家访问我的[博客](http://blog.csdn.net/whqet/ "博客")。`
对应的HTML代码：
`欢迎大家访问我的<a href="http://blog.csdn.net/whqet/" title="博客">博客</a>。`

参考式链接需要进行链接内容定义，然后引用该定义设置链接。
链接内容定义格式为：
```
[链接名]: 链接地址 "链接title"
[链接名]: 空格(或tab) 链接地址 空格 "链接地址"(可省略)
```
设置链接的格式为
```
[链接文字][链接名称]
EX：请大家访问我的[博客][blog],获取更多信息。
[blog]: http://blog.csdn.net/whqet "我的CSDN博客"
```
对应的HTML代码：
```
请大家访问我的<a href="http://blog.csdn.net/whqet" title="我的CSDN博客">博客</a>,获取更多信息。
```
### 图片
Markdown 使用一种和链接很相似的语法来标记图片，同样也允许两种样式： 行内式和参考式。
#### 行内式图片如下所示：
```
![Alt text](/path/to/img.jpg)
![Alt text](/path/to/img.jpg "Optional title")
```
#### 参考式图片如下所示：
```
![Alt text][id]
[id]: url/to/image  "Optional title attribute"
```
Markdown 还没有办法指定图片的宽高，如果你需要的话，你可以使用普通的  标签。
注意：CSDN图片如果大于显示区域，则图片宽度自适应，如果图片较小则以原始尺寸显示。

## 3. 表格和公式
### 目录
`[toc]`生成目录

### 脚注
先定义再使用
`[^name]: +空格后面加脚注的内容`

### 表格
Markdown使用管线图的方式实现表格，表格里面可以使用强调、链接等行内格式。
表头下面的虚线为了更好的分隔表头和表格内容，长度随意。

表格对齐：英文状态下的冒号： 默认是左对齐，居中对齐两边都加上冒号
`|:--------|---------:|:-------:|`

### 公式
通过使用MathJax，我们可以让Markdown解析LaTeX数学表达式，通常情况下，我们需要引入MathJax插件才可能工作。
`<script type="text/javascript" src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS_HTML"></script>`

CSDN已经内置了这个插件，我们就不需要手动插入了，可以直接写数学公式了。

使用`$...$`的方式来包含行内公式
陈列公式使用`$$...$$`来表示

#### MathJax语法
1.	使用`\alpha、\beta、\gamma`表示希腊字母`α、β、γ`， 使用\Gamma表示大写希腊字母Γ等
2.	利用{}实现优先级
3.	常用数学运算符表示如下

## 4. UML图
### 序列图
所有的序列图代码需要放在一个语法类型为sequence的代码块中
**图片**
1. 设置title，采用title: message。
2. 设置participant，采用participant: actor
3. 设置note
左侧note： note left of actor： message
右侧note： note right of actor: message,
覆盖note： note over actor: message
4. 设置会话，
实线实箭头： actor->actor: message
虚线实箭头： actor–>actor:message
实线虚箭头： actor->>actor:message
虚线虚箭头： actor–>>actor:message

#### 流程图
所有的流程图代码需要放在一个语法类型为flow的代码块中
流程图绘制包括两部分：节点定义和节点连接
节点定义
节点名称=>节点类型: 提示文本
节点名称可随意起，甚至支持中文。提示文本可以为英文，可以为中文，也可以为空使用默认值
节点类型有start、operation、condition、end等
* start=>start: 开始
* login=>operation: 登陆
* isLogin=>condition: 是否已登陆？
* test=>operation: 进行测试
* end=>end: 结束

节点连接
一般节点连接：
    节点->节点
条件判断节点连接：
条件节点(yes)->正确应答节点
条件节点(no)->错误应答节点

无需任何插件的在线绘制UML的Gravizo

## 5. CSDN MarkDown快捷入手
尽量少用工具栏，少用鼠标，尽量使用手写语法格式，可以适度使用快捷键。
**图片**
分割线直接输入，不建议使用快捷键
大家可以直接使用CSDN Markdown实现离线写作，浏览器会自动存储大家的写作进度，也可以使用其他Markdown编辑工具（例如window平台下的markdown pad、mac平台下Mou等）写作完毕，再导入到CSDN Markdown里。

使用CSDN Markdown的好处在于，可以一步到位地编辑文章，包括图片的上传和部署，文章摘要、文章参数的设置。
使用客户端编辑工具的好处在于， 文章写作操作的稳定性。

# ATOM使用诀窍：
## 1.安装---配置环境变量
由于我们安装插件需要用到apm这里命令，这里需要将其添加到环境变量里面，如图。
在桌面Atom图标→右击→属性→查看安装位置。
我的安装位置是在：C:\Users\erdou\AppData\Local\atom。
现在配置环境变量：在用户变量---PATH后面添加

打开命令窗口看是否可以使用apm
Win+R → cmd → apm ls
查看安装了哪些包

## 2.ATOM插件安装
### 1.直接安装
Settings—Install Packages---Install
### 2.从github网站上下载
Ctrl+Shift+P: 打开面板
输入：install packages选择install Packages Themes
输入要安装的插件名字emmet
点入插件介绍 找到github地址
打开git切换到 C:\Users\erdou.atom\packages
git clone https://github.com/emmetio/emmet-atom
切换到安装的插件文件夹cd emmet-atom
npm install
重启Atom

### 插件
#### 增强预览(markdown-preview-plus)
Atom自带的Markdown预览插件markdown-preview功能比较简单，markdown-preview-plus对其做了功能扩展和增强。

支持预览实时渲染。(Ctrl + Shift + M)
支持Latex公式。(Ctrl + Shift + X)
使用该插件前，需要先禁用markdown-preview。
