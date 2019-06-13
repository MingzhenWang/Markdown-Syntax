# Markdown-Syntax
整理自网络，目的是为了整合出一份适合自己阅读习惯的Markdown语法手册。

接触Markdown很早，真正用到是在工作后。Markdown语法主要用于写博客，现在印象笔记也支持了Markdown语法。Markdown语法简单，排版简单方便、清晰明了。
[区块引用](#anchor)

## 一、概述
Markdown是一种可以使用普通文本编辑器编写的标记语言，通过简单的标记语法，它可以使普通文本内容具有一定的格式。

Markdown具有一系列衍生版本，用于扩展Markdown的功能（如表格、脚注、内嵌HTML等等），这些功能原初的Markdown尚不具备，它们能让Markdown转换成更多的格式，例如LaTeX，Docbook。Markdown增强版中比较有名的有Markdown Extra、MultiMarkdown、 Maruku等。这些衍生版本要么基于工具，如Pandoc；要么基于网站，如GitHub和Wikipedia，在语法上基本兼容，但在一些语法和渲染效果上有改动。

区块元素是最小元素，不可跨行操作；区段元素是更高一级的元素，可以横跨数行，可以首尾相关联操作。


## 二、区块元素
### 1. 标题
Markdown支持两种标题的语法，**类Setext**和**类atx**形式。  
（1）类Setext使用底线的形式，只包含两个层级，`=`（最高阶标题）、`-`（第二阶标题），如下：  
    
    这是最高阶标题
    =============

    这是第二阶标题
    ------------  
（2）类atx形式在行首插入1到6个`#`，对应标题1到6阶，例如：  
    
    # 这是第一阶标题
    
    ## 这是第二阶标题
    
    ###### 这是第六阶标题
可以选择性地闭合类atx样式的标题，纯粹美观用，可以在行尾加上`#`，行尾的`#`数量不用和开头一样，例如：  

    ### 这是第三阶标题 ### 
 
 
### 2. 段落和换行  

换行有两种方式：`两个以上的空格+Enter` 或者使用：`<br/>`

### 3. <span id = "anchor">区块引用<span/>
Markdown中标记区块引用使用 `>` 符号，例如：  
    
    >每行都使用一个引用符号
    >可以行得通
    
    >也可以只在最开始加上引用符号
    这样也可以
区块引用可以嵌套（引用内的引用），只要根据层次加上不同数量的 `>` :

    >这是一级的引用
    >>这是二级的引用
    >这是一级的引用
    >>>这是三级的引用  
引用的区块内也可以使用其他的Markdown语法，包括标题、列表、代码区块等：
    
    >##这是一个二级标题
    >
    >1. 这是一个列表项
    


### 4. 列表  
Markdown支持有序列表和无序列表。
无序列表使用`*`（星号）、`+`（加号）或`-`（减号）作为列表标记:

    * First
    * Second
    * Third
有序列表使用 `数字+英文句点` ：  
    
    1. First
    2. Second
    3. Third
有序列表中使用的数字可以是无序的，这并不影响输出的结果，下例中的输出结果和上文一致：

    1. First
    3. Second
    2. Third
### 5. 代码区块

在Markdown中建立代码区块很简单，使用**4个空格**或者**1个制表符**就可以实现，一个代码区块会一直持续到没有缩进的那一行，如下：

        这是一个代码区块


### 6. 分割线
可以在一行中使用**三个以上**的**星号**、**减号**、**底线**（英文小下划线）来建立一个分隔符，可以在星号或者减号中间插入空格，如下：

    ***
    ---
    ___

## 三、区段元素
### 1. 链接
Markdown支持两种形式的链接语法：**行内式**和**参考式**两种形式。部分Markdown编辑器支持**锚点**，即页面内跳转。
**（1）行内式**
链接文字使用[方括号]来标记，在方括号后面紧接着英文圆括号并插入网址链接，若想加上链接的title文字，需要在网址后面+空格+用英文双引号包起来的title文字，如下：
    
    这是一个行内式[链接文字](http://example.com "title")

**（2）参考式**
参考式的链接是要在链接文字的方括号之后再加一个方括号，在第二个方括号内填入用于标识链接的标签，链接辨别标签可以有字母、数字、空白和标点符号，但是**不区分大小写**。

    这是一个参考式[链接文字][1]
接着，在文件的任意处(不能紧跟着否则无法生效)，可以把这个标记的链接内容定义出来。

    [1]: http://example.com "title"
链接内容定义的形式为：
* 方括号，里面输入链接文字
* 紧接着一个冒号
* 接着一个以上的空格或者制表符
* 接着链接的网址
* 选择性地接着title内容，可以用单引号、双引号或者括号 包着

下面三种形式作用相同：

    [1]: http://example.com 'title'
    [1]: http://example.com "title"
    [1]: http://example.com (title)

**隐式链接标记功能**可以省略指定链接标记，这种情形下，链接标记会视为等同于链接文字，要用隐式链接标记只要在链接文字后面加上一个空的方括号

    这是一个参考式[链接文字][]

    []: http://example.com "title"

**（3）锚点**
锚点由两部分组成：链接文字及链接跳转文字。
链接文字组成如下：

    [链接文字](#anchor)
链接跳转文字组成如下：

    <span id = "anchor">链接文字</span>
本文的目录跳转功能就是使用锚点来实现。
### 2. 强调
Markdown使用星号（`*`）和底线（`_`）作为标记强调字词的符号，`~~`代表删除，如下：

    *强调文字*
    _强调文字_
    ~~删除线~~
若要在文字前后直接插入普通的星号或底线，可以使用反斜线：

    \*这样文字前后可以正常显示星号，不会产生强调的效果\*

### 3. 代码
若要标记一小段行内代码，可以使用反引号（`` ` ``）把代码包起来，如下：

    使用函数`sum()`求和
如果要在代码区块内插入反引号，可以使用对个反引号来开始和结束代码区块，如下：

    ``代码区块内含有反引号（`）``

使用三个反引号包起来的代码，同时在开始的三个反引号后面紧跟语言名称，可以实现代码高亮，例如：

    ```SQL
    select * from LSWLDW
    ```
### 4. 图片
Markdown使用类似于链接的语法来标记图片，包括行内式和参考式。
（1）行内式
* 一个英文感叹号（!）
* 接着一个方括号，里面放上图片的代替文字
* 接着一个普通括号，里面放上图片的网址，最后可以用引号包住并加上选择性的title文字。  

如下所示：  

    ![图片1](/path/to/img.jpg)
    ![图片2](/path/to/img.jpg "Optional title")
    ![图片3](https://raw.githubusercontent.com/MingzhenWang/MyPictures/master/TabIcons/Coursera.jpg "Optional title")

（2）参考式

    ![图片1][id]

    [id]: /path/to/img.jpg "Optional title"

目前为止，Markdown无法指定图片的宽高，如果需要，可以使用普通的`<img>`标签。


## 四、高级功能
### 1. 自动链接
Markdown 支持以比较简短的自动链接形式来处理**网址**和**电子邮件信箱**，只要是用方括号包起来，Markdown 就会自动把它转成链接。如下：

    <http://example.com>
    <392248244@qq.com>
### 2 反斜杠
Makrdwon可以利用反斜杠来插入一些在语法中有其他意义的符号，例如：如果你想在文字两边加星号，但不想出现强调的效果，可以如下操作：
[392248244@qq.com]
    \*你好\*,这个星号会正常显示
Markdown支持以下这些符号前面加上反斜杠来帮助插入普通的符号：
    
    \ 反斜线
    ` 反引号
    * 星号
    _ 底线
    {} 花括号
    [] 方括号
    () 括弧
    # 井字号
    + 加号
    - 减号
    . 英文句点
    ! 惊叹号
Markdown中还存在通过Unicode码来输入的特殊字符，示例如下：

    &#10084;
    &#9742;
**效果图：**
&#10084;
&#9742;
还可以通过Unicode字符实现缩进。

想知道字符对应的Unicode码，可以看这个网站：https://unicode-table.com/cn/
### 3. 表格
Markdown中表格的基本写法很简单，和表格的形状很相似：

    学号|姓名|分数
    -|-|-
    1143106|小明|99
表格对齐方式：我们可以指定表格单元格的对齐方式，冒号在左边表示左对齐，右边表示有对齐，两边都有表示居中。

    学号|姓名|分数
    :-|-:|:-:
    1143106|小明1143106|99999999
**效果图：**
学号|姓名|分数
:-|-:|:-:
1143106|小明1143106|99999999
### 4. 任务列表
Markdown语法支持任务列表：
* 首先是一个减号`-`
* 紧接着一个空格
* 然后是一个方括号，括号里是`空格`表示未勾选，括号里是`x`表示勾选。  

如下：
```
    - [x] [links](), **formatting**, and ~~tags~~ supported
    - [ ] list syntax required (any unordered or ordered list supported)
    - [ ] this is a complete item
    - [x] this is an incomplete item
```
**效果图：**
- [x] [links](), **formatting**, and ~~tags~~ supported
- [ ] list syntax required (any unordered or ordered list supported)
- [ ] this is a complete item
- [x] this is an incomplete item
### 5. 脚注|注释
（1）脚注
Markdown语法使用[^]来定义脚注：

    这是一个脚注的例子[^1]
    [^1]: 这里是脚注
**效果图：**
这是一个脚注的例子[^1]
[^1]: 这里是脚注

（2）注释
注释，是给自己看的，预览时也不会出现，当然发布出去别人也不会看见。

    <!--这是注释-->
**效果图：**
<!--这是注释-->
### 6. emoji表情符号
Markdown中可以使用emoji表情符号，语法格式`:EMOJICODE:`，如下：

    :smile:
    :new_moon_with_face:
**效果图：**
:smile:
:new_moon_with_face:
详细EMOJICODE可见：
https://www.webpagefx.com/tools/emoji-cheat-sheet/


## 五、常用弥补Markdown的Html标签
有些Markdown语法不支持的功能，可以使用内置HTML的方式实现。
### 1. 字体
使用Html标签来控制文字的字体、颜色、大小，如下：

    <font face="微软雅黑" color="red" size="3">字体、颜色及大小</font>
    <font color="#0000ff">字体颜色</font>
**效果图：**
    <font face="微软雅黑" color="red" size="3">字体、颜色及大小</font>
    <font color="#0000ff">字体颜色</font>
### 2.文本对其方式
Markdown支持控制表格中的对其方式，但不支持文本的对其方式，我们可以通过HTML标签进行控制，如下：

    <p align="left">居左文本</p>
    <p align="center">居中文本</p>
    <p align="right">居右文本</p>
**效果图：**
<p align="left">居左文本</p>
<p align="center">居中文本</p>
<p align="right">居右文本</p>
### 3.下划线
下划线的HTML标签很简单，如下：

    <u>下划线文本</u>
**效果图：**
<u>下划线文本</u>
### 4.背景色
Markdown借助 table、tr、td等表格标签的 bgcolor 属性来实现背景色的功能，如下：

    <table><tr><td bgcolor=orange>背景色是：orange</td></tr></table>
**效果图：**
<table><tr><td bgcolor="orange">背景色是：orange</td></tr></table>
## 六、高级功能
### 1. LaTeX数学公式
LaTeX数学公式分为两种，行内公式和行间公式，如下：
（1）行内公式

    $行内公式$
    这是一个行内公式$\sqrt{x^{2}}$
**效果图：**
这是一个行内公式$\sqrt{x^{2}}$  
（2）行间公式

    $$行间公式$$
    这是一个行内公式$$\sqrt{x^{2}}$$
**效果图：**
这是一个行内公式$$\sqrt{x^{2}}$$
具体用法可参考如下内容：
[CSDN-markdown编辑器使用LaTex数学公式](https://blog.csdn.net/testcs_dn/article/details/44229085)
[常用数学符号的 LaTeX 表示方法](https://www.mohu.org/info/symbols/symbols.htm)

### 2. 流程图
Markdown流程图语法主要由3部分组成：流程图语块定义、流程图符号声明和流程处理。
流程图代码分两块，上面一块是**创建流程（创建元素）**，隔一行，**创建流程的走向（连接元素）**。
#### （1）创建流程（元素）：tag=>type: content:>url
* tag是流程图中的标签，在第二段连接元素时会用到。名称可以任意，一般为流程的英文缩写和数字组合。
* type用来确定标签的类型，=>后面表示类型。由于标签的名称可以任意指定，所以要依赖type来确定标签的类型。
* 标签有6中类型：start、end、operation、subroutine、condition、inputoutput。
* content是流程图文本框中的描述内容，`:`表示内容，中英文均可。（冒号和内容之间一定要有一个空格）
* url是一个链接，与框中的文本相绑定，`:>`后面就是对应的url地址，点击文本时可以通过链接跳转到url指定页面。
####（2）指向流程（连接元素）：标识（类别）->下一个标识
* 使用 `->` 来连接两个元素
* 对于condition类型，有yes和no两个分支，如示例中的cond(yes)和cond(no)
* 每个元素可以指定分支方向，默认向下，也可以用right指向右边（right、left、top、bottom），如示例中cond2(yes,right)

流程图元素：
* 开始
  `st=>start:开始`
* 操作
  `opl=>operation:操作、执行说明`
* 条件
  `cond=>condition:确认？`
* 子程序
  `sub1=>subroutine:子程序操作说明`
* 用户输入或输出
  `io1=>inputoutput:输入密码`
* 结束
  `e=>end:结束`

示例如下：

    ```flow
    st=>start: 开始 
    e=>end: 登录 
    io1=>inputoutput: 输入用户名密码 
    sub1=>subroutine: 数据库查询子类 
    cond=>condition: 是否有此用户 
    cond2=>condition: 密码是否正确 
    op=>operation: 读入用户信息

    st->io1->sub1->cond 
    cond(yes,right)->cond2 
    cond(no,right)->io1(right) 
    cond2(yes,right)->op(right)->e 
    cond2(no,right)->io1 
    ```
**效果图：**
```flow
st=>start: 开始 
e=>end: 登录 
io1=>inputoutput: 输入用户名密码 
sub1=>subroutine: 数据库查询子类 
cond=>condition: 是否有此用户 
cond2=>condition: 密码是否正确 
op=>operation: 读入用户信息

st->io1->sub1->cond 
cond(yes,right)->cond2 
cond(no,right)->io1(right) 
cond2(yes,right)->op(right)->e 
cond2(no,right)->io1 
```



### 3. 序列图

### 4. 甘特图
