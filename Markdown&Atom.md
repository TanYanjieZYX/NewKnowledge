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
**文本格式化**
![M1](https://github.com/TanYanjieZYX/NewKnowledge/blob/master/pic/markdown1.png)

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
![M2](https://github.com/TanYanjieZYX/NewKnowledge/blob/master/pic/markdown2.png)

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
![M3](https://github.com/TanYanjieZYX/NewKnowledge/blob/master/pic/markdown3.jpg)

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
![M4](https://github.com/TanYanjieZYX/NewKnowledge/blob/master/pic/markdown4.png)

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
**可以使用Chromium提供的开发工具来调试它. 呼出开发工具的快捷键为`Ctrl+Shift+I`.**
## 2.设置窗口
你可以使用下面三种方法来打开设置窗口
1. 主菜单Edit->Preferences
2. 在命令面板中输入命令Settings View:Open. 因为命令窗口支持模糊查询, 因此只需要输入svo, 就可以了
3. 使用快捷键Ctrl+,
**在设置窗口中可以设置和管理各种编辑器行为, 键盘快捷键, 插件, 主题等内容**
## 3.ATOM插件安装
### 1.直接安装
Settings—Install Packages---Install
* Ctrl+Shift+P: 打开面板
* 输入：install packages选择install Packages Themes
* 输入要安装的插件名字emmet
### 2.命令行下载
第一种方法——直接命令下载
使用`apm `命令来安装管理插件
```
# 显示apm命令的使用帮助
# 通过这个命令可以获得apm提供的所有子命令
apm help
# 显示apm命令的install子命令的使用帮助
apm help install
# 安装一个插件的最新版本
apm install <package_name>
# 安装一个特定版本的插件
apm install <package_name>@<package_version>
# 比如要安装0.1.5版的Emmet
apm install emmet@0.1.5
# 搜索插件名包含coffee的插件
apm search coffee
# 显示git-grep插件的详细信息
apm view git-grep
```
第二种方法——github网站下载
* Ctrl+Shift+P: 打开面板
* 输入：install packages选择install Packages Themes
* 输入要安装的插件名字emmet
* 点入插件介绍 找到github地址
* 打开git切换到 C:\Users\erdou.atom\packages
* git clone https://github.com/emmetio/emmet-atom
* 切换到安装的插件文件夹cd emmet-atom
* npm install
* 重启Atom

### 插件
#### 前端开发必用
* Emmet——基于Emmet语法产生HTML
* color-picker——取色器
* file-icons——为不同类型的文件添加一个漂亮的小图标
* Linter Jshint——编写专业的js代码
* pigments——在atom里面所有颜色的色值，它会自动加上背景色
* atom-beautify——支持html,css,js,php...等的格式美化
* simplified-chinese-menu——ATOM的汉化插件
* language-JavaScript-jsx——支持JSX语法
* atom-html-preview——实时预览HTML页面
* atom-minify——css、js代码压缩
* atom-ternjs——js,nodejs,es6补全，高度定制化
* jshint——验证js和jsx语法是否正确
* csslint——验证css语法是否正确
* autoprefixer——自动为 CSS 属性添加特定的前缀
* less-autocompile——less文件编译为css文件
* autoclose-html——闭合html标签
* open in browser——将HTML代码一键在浏览器中打开
* highlight-line——高亮所选中的行
#### React插件
* react——语法支持
* atom-react-native-autocomplete——React Native代码补全
* nuclide—facebook——基于atom开发的进行react开发的IDE
* language-babel——支持JSX语法
#### Markdown插件
* markdown-preview-plus——增强预览
* markdown-scroll-sync——同步滚动
* language-markdown——代码着色，快捷的代码片段生成
* markdown-image-paste——图片粘贴
* markdown-table-editor——表格编辑
* pdf-view——pdf导出预览
## 4.快捷的文本编辑
### 对文件的操作
| 英文       | 中文         | 快捷键           | 功能       |
| :--------: | :------------: | :----------------: | :----------: |
| New Window | 新建界面窗口 | Ctrl + Shift + N | 如中文意思 |
| New File  |新建文件   |Ctrl + N  |如中文意思
| Open File  | 打开文件  | Ctrl + O  | 如中文意思
| Open Folder  | 打开文件夹  | Ctrl + Shift + O  | 如中文意思
| Add Project Folder  | 加载项目目录  | Ctrl + Alt + O  | 如中文意思
| Reopen Last Item  | 重新加载上次项目  | Ctrl + Shift + T |  如中文意思
| Save  | 保存文件  | Ctrl + S |  如中文意思
| Save As  | 另存为 |  Ctrl + Shift +S  | 如中文意思
| Close Tab  | 关闭当前编辑文档 |  Ctrl + W |  如中文意思
| Close Window  | 关闭编辑器 |  Ctrl + Shift + W  | 如中文意思

### 对内容的操作
| 英文 | 中文 | 快捷键 | 功能 |
|:----:|:----:|:------:|:----:|
| Undo  | 撤销  | Ctrl + Z  | 如中文意思
| Redo  | 重做  | Ctrl + Y  | 如中文意思
| Cut  | 剪切  | Shift + Delete  | 如中文意思
| Copy  | 复制  | Ctrl + Insert  | 如中文意思
| Copy Path  | 复制文档路径  | Ctrl + Shift + C  | 如中文意思
| Paste  | 粘贴  | Shift + Insert  | 如中文意思
| Select All  | 全选  | Ctrl + A |  如中文意思
| Select Encoding  | 选择编码  | Ctrl + Shift +U  | 就是设置文件的编码
| Go to Line  | 跳转到某行  | Ctrl + G  | 支持行列搜索,Row:Column
| Slect Grammar  | 语法选择  | Ctrl + Shift + L |  和Sublime的Syntax设置功能一样
| Reload  | 重载  | Ctrl+ Alt +R  | 重新载入当前编辑的文档
| Toggle Full Screen  | 全屏  | F11  | 如中文意思
| Increase Font Size  | 增大字体  | Ctrl + Shift + “+”  | Sublime的Ctrl + 也能生效
| Decrease Font Size |  减小字体 |  Ctrl + Shift + “-“  | Sublime的Ctrl - 也能生效
| Toggle Tree View  | 展示隐藏目录树  | Ctrl + （竖杠）  | Ctrl+b可以隐藏不能展示
| Toggle Commadn palette  | 全局搜索面板  | Ctrl + Shift + P  | 和Sublime的大同小异
| Select Line  | 选定一行 |  Ctrl + L  | 如中文意思

### 查找与光标的移动
| 英文 | 中文 | 快捷键 | 功能 |
|:----:|:----:|:------:|:----:|
| Select First Character of Line  | 选定光标至行首  | Shift + Home  | 如中文意思
| Select End of Line  | 选定光标至行尾  | Shift + End  | 如中文意思
| Select to Top  | 选定光标处至文档首行  | Ctrl + Shift + Home  | 就是光标处作为分割线,取文档上部分
| Select to Bottom  | 选定光标处至文档尾行  | Ctrl + Shfit + End  | 就是光标处作为分割线,取文档下部分
| Find in Buffer  | 从缓存器搜索  | Ctrl + F  | 与Sublime一致
| Replace in Buffer  | 高级替换  | Ctrl + Shift + F  | 与Sublime一致
| Select Next |  匹配选定下一个  | Ctrl + D  | 和Sublime一模一样有木有
| Select All  | 匹配选定所有  | Alt + F3  | 和Sublime一模一样有木有
| Find File  | 查询文件,选定打开  | Ctrl + P  | 与Sublime不一样
| Delte End of Word  | 删除光标处至词尾 |  Ctrl + Del  | 如中文意思
| Duplicate Line  | 复制行 |  Ctrl + Shift + D | 复制光标所在行自动换行
| Delete Line  | 删除一行  | Ctrl + Shift + K  | 如中文意思
| Toggle Comment  | 启用注释 |  Ctrl + /  | 与Sublime一致

### 剩下的快捷键
| 英文 | 中文 | 快捷键 | 功能 |
|:----:|:----:|:------:|:----:|
| Toggle developer tools  | 打开Chrome调试器  | Ctrl + Alt + I  | 挺神奇的
| Indent  | 增加缩进  | Ctrl + [  | 向右缩进
| Outdent  | 减少缩进  | Ctrl + ]  | 向左缩进
| Move Line Up  | 行向上移动 |  Ctrl + up  | 如字面意思
| Move Line Down  | 行向下移动  | Ctrl + Down  | 如字面意思
| Join Lines  | 行链接 |  Ctrl + J  | 追加
| newline-below  | 光标之下增加一行 |  Ctrl + Enter |  与sublime 一致
| editor:newline-above  | 光标之上增加一行 |  Ctrl + Shift + Enter  | 与sublime 一致
| pane:show-next-item  | 切换编辑的标签页  | Ctrl + Tab  | 如中文意思
| Fuzzy Finder  | 文件跳转面板  | Ctrl + T |  如字面意思
| Select Line Move above  | 选中行上移  | Ctrl + up  | 如中文意思
| Select Line Move below |  选中行下移  | Ctrl + down  | 如中文意思
| Symbol-view  | 进入变量、函数跳转面板。 |  Ctrl + R |  如中文意思
## 5.代码片段(Snippets)
Snippets是一种在代码中快捷插入代码块的方式,下面是维基百科中对Snippet的解释
>片段（Snippet）是一个编程用语，指的是源代码、机器码、文本中可重复使用的小区块。通常它们是有正式定义的执行单位，以纳入更大的编程模块。片段经常用来明晰其他“凌乱”函式的功用，或尽量减少使用与其他函式共用的重复代码。
>片段管理是某些文本编辑器、程式源代码编辑器、IDE、与相关软件的其中一项功能。其使得使用者能够在反复的编辑作业中保持和使用这些片段。
这就是Snippets,它让你可以很方便地通过一个关键词来插入一段代码块,并且还能通过`tab键`在这段代码块的输入点之间移动光标,达到快速编码的目的
不同类型的文件有不同的Snippets,你可以通过快捷键`Alt+Shift+S`来列出当前文件所提供的所有的Snippets
### 自定义Snippets
Atom中有很多插件都提供了对某个特定文件中Snippets的支持,比如上面的html-Snippets,就来自language-html插件。
当然我们也可以定义自己的Snippets,这样可以在编码的过程中更加灵活地使用这个特性 。
* 在Atom的配置目录(如果是Linux系统,这个目录是~/.atom)下包含一个名为snippets.cson的文件,这个文件就负责保存我们的自定义Snippets.
* 你可以通过主菜单Edit->Open Your Snippets来方便地打开这个文件.
* 打开 snippets.cson 文件，windows 平台的路径为 C:\Users\用户名\.atom\snippets.cson。
* 输入snip，回车，就得到一个 snippet 模板。
#### 模板
```
'.source.js':
  'Snippet Name':
    'prefix': 'Snippet Trigger'
    'body': 'Hello World!'
```
```
'.source.js' 目标文件类型为 .js
'Snippet Name' 要新建的 snippet 的名称
'prefix' 触发当前 snippet 的代码
'body' 要填充的代码
```
① 最左边的键是选择器，表明这些代码段在哪些文件中才能生效。要想知道这个键的值，最简单的方法就是：进入代码段语言所对应的语言包中，查看 Scope 字符串。（注意：键值就是` . + Scope`）
② 下一层的键是代码段名称，用于在代码段菜单中以一种更加易读的方式描述代码段。你可以自由命名。
③ 代码段名称之后，便是 可以出发代码段的 prefix 和 当代码段被触发时将要插入的代码 body
④ 每一个带有数字的``就是一个 tab 键驻留位置。只要代码段被触发，便可以通过 Tab 键遍历这些 tab 驻留位置

## 6.Git支持
如果你的代码托管在GitHub上,掌握下列命令可以让你更方便地工作
* Alt+G O 在GitHub上打开当前文件
* Alt+G B 在GitHub上用Blame方式打开当前文件
* Alt+G H 在GitHub上用History方式打开当前文件
* Alt+G C 将当前文件在GitHub上的URL复制到剪切板
* Alt+G R 在GitHub上比较分支

## 7.Markdown支持
### 拼写检查
当我们编辑文本时(包括纯文本文档,Markdown,Git提交信息等), Atom会自动尝试做拼写检查.
如果某个词拼写错误, Atom会将其高亮.
在这个时候你可以使用Ctrl+Shift+;或右键菜单(或命令面板)中的Correct Spelling来弹出一个包含修改参考项的菜单来进行拼写错误的修改.
#### Markdown-Writer插件
Markdown-Writer提供了大量的快捷键和命令来增强md文件的编辑体验.
要启用这些快捷键, 需要执行命令`Markdown Writer: Create Default Keymaps. `
该命令会自动将Markdown-Writer的默认热键添加到keymap.cson中. 这些热键包括插入链接, 图片, 切换各种字体样式.
```
".platform-linux atom-text-editor:not([mini])":
  "shift-ctrl-K": "markdown-writer:insert-link"
  "shift-ctrl-I": "markdown-writer:insert-image"
  "ctrl-i":       "markdown-writer:toggle-italic-text"
  "ctrl-b":       "markdown-writer:toggle-bold-text"
  "ctrl-'":       "markdown-writer:toggle-code-text"
  "ctrl-h":       "markdown-writer:toggle-strikethrough-text"
  "ctrl-1":       "markdown-writer:toggle-h1"
  "ctrl-2":       "markdown-writer:toggle-h2"
  "ctrl-3":       "markdown-writer:toggle-h3"
  "ctrl-4":       "markdown-writer:toggle-h4"
  "ctrl-5":       "markdown-writer:toggle-h5"
```
#### Markdown Preview Enhanced插件
1. 预览md的快捷键任然为Ctrl+Shift+M
2. 编辑预览同步滚动
3. 命令Create Toc可以在当前位置生成md文件的toc
4. md文件导出为PDF, PNG, JPEG等文件
5. 命令Insert Table用于插入表格
6. 在预览窗口右键可以选择在浏览器中打开预览
7. 支持GitHub Flavored Markdown样式的TODO List
插件配置：
```
"*":
  "markdown-preview-enhanced":
    breakOnSingleNewline: true
    useGitHubStyle: false
    useGitHubSyntaxTheme: false
```
## 8.编辑配置文件
### CSON
CSON(CoffeeScript Object Notation)是Atom配置文件的文件格式, 它使用键值对的格式来存储数据.
```
key:
    key: value
    key: value
    key: [value, value]
```
跟Python类似, CSON使用缩进来标识语句块.

CSON的key的名字不能重复, 如果CSON中包含了多个同名的key, 那么最后的那个key的值会覆盖之前同名的key.
因此**不能**这样配置
```
# 只有第二个snippet会被载入
'.source.js':
  'console.log':
    'prefix': 'log'
    'body': 'console.log(${1:"crash"});$2'
'.source.js':
  'console.error':
    'prefix': 'error'
    'body': 'console.error(${1:"crash"});$2'

```
而应该这样配置,value可以是字符串, 数字, 对象, 布尔值, null, 或数组.

```
# 两个snippets都会被载入
'.source.js':
  'console.log':
    'prefix': 'log'
    'body': 'console.log(${1:"crash"});$2'
  'console.error':
    'prefix': 'error'
    'body': 'console.error(${1:"crash"});$2'
```
### 样式微调
有这样一个场景, 我们想对一个主题中的某个元素的style进行一点点修改, 但又不想(或是不会)创建一个完整的主题包, 这个时候我们就可以通过编辑**styles.less**文件来达到目的. 这个文件位于~/.atom目录下, 是一个Less语言(一个CSS的预处理程序)的源文件.
我们可以使用Atom来打开并编辑这个文件, 也可以通过主菜单Edit->Stylesheet来更方便地打开它.

举个例子, 如果我们想要改变状态栏的颜色, 可以在styles.less中加入
```
.status-bar {
  color: white;
  background-color: black;
}
```
### 配置热键
在Atom中热键的配置方式与主题类似, 举个例子:
```
'atom-text-editor':
  'enter': 'editor:newline'

'atom-text-editor[mini] input':
  'enter': 'core:confirm'
```
上面的代码定义了**Enter键**在不同环境中的不同表现. 在**正常的编辑窗口**中按enter键触发editor:newline命令, 也即是普通的回车. 而当在一个**编辑框**中键入enter时, 则会触发core:confirm命令.

在默认情况下, 当Atom启动时会加载**keymap.cson**文件来获取**自定义热键**, 并且keymap.cson是最后被加载的配置文件, 这样可以保证我们配置的热键可以覆盖Atom自身或其插件定义的热键. 这个文件同样位于~/.atom目录下, 当然也可以通过主菜单Edit->Keymap...来直接编辑这个文件.

我们也可以在**设置窗口的Keybindings页面**查看当前所有的快捷键.

Atom还提供了一个窗口来帮助我们调试热键的设置, 可以使用Ctrl+.或命令Key Binding Resolver: Toggle来呼出该窗口. 此窗口可以实时显示我们按下的热键所对应的处理方法.
### 自定义语言
假如我想Atom将扩展名为foo的文件识别为CoffeeScript, 那么可以在config.cson文件中这样设置:
```
'*':
  core:
    customFileTypes:
      'source.coffee': [
        'foo'
      ]
```

### 部分转载自https://blog.csdn.net/u010494080/article/details/53547485
### 作者：PeterHo
