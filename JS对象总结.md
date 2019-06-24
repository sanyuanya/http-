##### JS对象总结

##### 1. window对象

`javascrip`t可以获取浏览器提供的很多对象进行操作

`window`对象不但充当`全局作用域`，而且表示`浏览器窗口`

`windows`对象有`innerHeight`和`innerWidth`属性，可以获取浏览器窗口的内部宽高，内部宽高是指除去菜单栏、工具栏、边框等占位元素后，用于显示网页的净宽高。

> window.innerHeight    //高
>
> window.innerWeight   //宽

对应的，还有一个outerWidth和outerHeight属性，可以获取浏览器窗口的整个宽高。

##### 2. navigator对象

可以获取浏览器的信息

> navigator.appName       //浏览器名称
>
> navigator.appVersion    //浏览器版本
>
> navigator.language       //浏览器设置的语言
>
> navigator.platform       //操作系统类型
>
> navigator.userAgent     //浏览器设定的User-Agent 字符串
>
> navigator.appCodeName  //浏览器的代码名。 

##### 3. screen 对象

`screen`对象表示屏幕的信息，常用的属性有：

> screen.width：屏幕宽度，以像素为单位；
>
> screen.height：屏幕高度，以像素为单位；
>
> screen.colorDepth：返回颜色位数，如8、16、24。

##### 4. location 对象

`location`对象表示当前页面的URL信息,列如，一个完整的url

```
http://www.example.com:8080/path/index.html?a=1&b=2#TOP
```

可以用`location.href`获取。要获得URL各个部分的值，可以这么写：

```
location.protocol; // 'http'
location.host; // 'www.example.com'
location.port; // '8080'
location.pathname; // '/path/index.html'
location.search; // '?a=1&b=2'
location.hash; // 'TO
```

要加载一个新页面，可以调用location.assign()。如果要重新加载当前页面，调用location.reload()方法非常方便。

`location`对象属性：

|   属性   |                   描述                    |
| :------: | :---------------------------------------: |
|   hash   |   设置或返回从井号（#）开始的URL（锚）    |
|   host   |    设置或返回主机名和当前的URL的端口号    |
| hostname |        设置或返回当前的URL的主机名        |
|   href   |            设置或返回完整的URL            |
| pathname |        设置或返回当前URL的路径部分        |
|   port   |        设置或返回当前的URL的端口号        |
| protocol |          设置或返回当前URL的协议          |
|  search  | 设置或返回从问号（？）开始的URL(查询部分) |

`location`对象的方法

| 属性      | 描述                   |
| --------- | ---------------------- |
| assign()  | 加载新的文档           |
| reload()  | 重新加载当前文档       |
| replace() | 用新的文档替换当前文档 |

##### document

`document`对象表示当前页面。由于HTML在浏览器中以DOM形式表示为树形结构，document就是整个DOM树的根节点。

##### 什么是DOM?

DOM是文档对象模型（Document Object  Model） 的简称，它的基本思想是把结构化文档（比如HTML 和XML）解析成一系列的节点，再由这些节点组成一个数状结构（DOM Tree）,所有的节点和最终的数状结构，都有规范的对外接口，以达到编程语言操作文档的作用 ，所以，DOM可以理解成文档（HTML文档，XML文档）的编程语言。DOM 不属于 JavaScript，但是操作 DOM 是 JavaScript 最常见的任务，而 JavaScript 也是最常用于 DOM 操作的语言。

##### 节点与节点树

节点与节点树的概念

HTML 文档中的每项内容都是一个节点，包括 HTML标签、标签属性、文本内容、注释、空格或tab 等。

HTML 文档中的所有节点组成了一个节点树（或文档树）。HTML 文档中的每个元素、属性、文本等都代表着树中的一个节点。树起始于文档节点，并由此继续伸出枝条，直到处于这棵树最低级别的所有文本节点为止。

节点与节点的关系

DOM节点之间都有等级关系，包括父节点、子节点、兄弟节点（同辈节点）、后代、父辈 等。

```
<html>
<head>
    <title>DOM节点之间的关系</title>
</head>
<body>
    <h1>这是标题</h1>
    <p>这是内容</p>
</body>
</html>
```

从上面的代码可以看出：

**除文档节点（根节点）之外的每个节点都有父节点。**
例如，<head> 和 <body> 的父节点是 <html> 节点，文本节点“ 这是内容 ”的父节点是 <p> 节点。

**大部分元素节点都有子节点。**
例如，<head> 节点有一个子节点：<title> 节点；<title> 节点也有一个子节点：文本节点“ 这是标题 ”。

**当节点拥有共同的父节点时，它们就是兄弟节点（同辈节点）。**
例如，<h1> 和 <p>是兄弟节点，它们的父节点均是 <body> 节点。

**节点也可以拥有后代，后代指某个节点的所有子节点，或者这些子节点的子节点，以此类推。**
例如，所有的文本节点都是 <html>节点的后代，而第一个文本节点是 <head> 节点的后代。

**节点也可以拥有先辈。先辈是某个节点的父节点，或者父节点的父节点，以此类推。**
例如，所有的文本节点都可把 <html> 节点作为先辈节点。

##### Javascript获取DOM节点

**getElementById( )方法**

根据HTML标签的id属性来获取DOM节点请使用 getElementById( ) 方法。该方法返回一个节点对象。

语法：   document.getElementById(id)；



**getElementsByTagName( )方法**

根据HTML标签名称来获取DOM节点请使用 getElementsByTagName( ) 方法。该方法将得到的元素节点作为一个数组返回。
语法：
    nodeObject.getElementsByTagName(tagName)
其中，nodeObject 为元素节点，tagName 为HTML标签的名称。
注意：getElementsByTagName() 方法既可以查找整个 HTML 文档中的所有节点，也可以查找某个节点的子节点，使用时必须要指定查找范围，即指明 nodeObject 。
例如，获得HTML文档中所有的<div>标签：

document.getElementsByTagName("div");

获得id="demo"的标签内部的所有<div>标签：

document.getElementById("demo").getElementsByTagName("div");

##### JavaScript获取节点类型、节点名称和节点值

 DOM节点中，每个节点都拥有不同的类型。

W3C规范中常用的 DOM节点类型有以下几种：  

| 节点类型 |                          说明                           | 值   |
| :------: | :-----------------------------------------------------: | ---- |
| 元素节点 | 每一个HTML标签都是一个元素节点，如 <div> 、<p>、<ul> 等 | 1    |
| 属性节点 |         (HTML标签)的属性，如id 、class、那么等          | 2    |
| 文本节点 |              元素节点或属性节点的文本内容               | 3    |
| 注释节点 |        表示文档注释，形式为 <!--comment text -->        | 8    |
| 文档节点 |        表示整个文档（DOM树的根节点，即document）        | 9    |

例如，获取id="demo"的<div>标签的节点类型`nodeType`：

```
document.getElementById("demo").nodeType;//返回1
```

节点名称就是DOM节点的名字，不同类型的节点对应不同的节点名称。

| 节点类型 | 节点名称             |
| -------- | -------------------- |
| 元素节点 | HTML标签名称（大写） |
| 属性节点 | 属性的名称           |
| 文本节点 | #text                |
| 文档节点 | #document            |

##### 获取节点名称的类型：

```
    nodeObject.nodeType
```

##### 获取节点名称的语法：

```
    nodeObject.nodeName
```

##### 获取节点值的语法：

```
 nodeObject.nodeValue
```

##### javascript parentNode  ：获取父节点

```
 document.parentNode
```

##### 获取子节点

```
 document.chindren  ||document.chindNodes     //获取所有的子节点
```

##### 获取子节点的个数

```
 getChildNodes(this);      //元素子节点的个数为
```

##### 获取第一个子节点：

```
    nodeObject.firstChind
```

##### 获取最后一个子节点：

```
    nodeObject.lastChind   
```

##### 判断子节点是否存在：

```
 nodeObject.hasChindNodes()
```

##### javascript  获取兄弟节点

过 previousSibling 来获取上一个节点。

```
    nodeObject.previousSibling    //nodeObject 为节点对象（元素节点）
```

#####  **获取下一个节点**

```
    nodeObject.nextSibling    //nodeObject 为节点对象（元素节点）
```

#####   Javascript创建节点

下面列出常用的创建节点的方法：

| 方法                     | 说明             |
| ------------------------ | ---------------- |
| createElement()          | 创建元素节点     |
| createTextNode()         | 创建文本节点     |
| createComment()          | 创建文本节点     |
| createDocumentFragment() | 创建文档碎片节点 |

以上四种方法都是 document 对象的方法。

**createElement()**

createElement()用来创建一个元素节点，即 nodeType=1 的节点。

语法：

```
    document.createElement(tagName)
```

其中，tagName 为HTML标签的名称，并将返回一个节点对象。

例如，创建<div>标签和<p>标签的语句如下：

var ele_div   =  document.createElement("div");

**createTextNode()**

createTextNode()用来创建一个文本节点，即 nodeType=3 的节点。

语法：

```
    document.createTextNode(text)
```


其中，text 为文本节点的内容，并将返回一个节点对象。

例如，创建一个文本节点，内容为“ 这是文本节点 ”：

```
var ele_text=document.createTextNode(" 这是文本节点 ");
```

**createComment()**

createComment()用来创建一个注释节点，即 nodeType=8 的节点。

语法：

```
    document.createComment(comment)
```

其中，comment 为注释的内容，并将返回一个节点对象。

例如，创建一个注释节点，内容为“ 这是一个注释节点 ”：

```
var ele_comment=document.createComment(" 这是一个注释节点 ");
```

**createDocumentFragment()**

createDocumentFragment() 用来创建文档碎片节点。

文档碎片节点是若干DOM节点的集合，可以包括各种类型的节点，如 元素节点、文本节点、注释节点 等。文档碎片节点在创建之初是空的，需要向它添加节点。

语法：

```
     document.createDocumentFragment();
```

例如，创建一个文档碎片节点，并将它赋值给变量：

```
var ele_fragment=document.createDocumentFragment();
```

##### javascript 添加节点

上节中，我们讲解了如何创建新节点。创建的新节点如果想发挥作用，必需添加到DOM（HTML文档）。

| 方法           | 说明                         |
| -------------- | ---------------------------- |
| insertBefore() | 在指定的节点前面插入新节点   |
| appendChild()  | 在指定节点的最后插入新的节点 |

**insertBefore()**

insertBefore() 方法可以在指定节点的前面插入新节点。

语法：
    parentNode.insertBefore(newNode , thisNode)
参数/返回值说明：

| 参数/返回值 | 说明                            |
| ----------- | ------------------------------- |
| parentNode  | 父节点                          |
| newNode     | 将要添加的新节点                |
| thisNode    | 当前节点（指定节点）            |
| 返回值      | 插入成功返回true，失败返回false |

注意：insertBefore() 是当前节点的父节点的一个方法，添加节点时，不但要知道当前节点，还要知道当前节点的父节点。一般情况下，可以通过 thisNode.parentNode 来获取父节点。

##### appendChild()

 appendChild() 可以向指定节点添加新的子节点，并将添加的节点放在最后。

语法：
    parentNode.appendChild(newNode)
参数/返回值说明：  

| 参数/返回值 | 说明                           |
| ----------- | ------------------------------ |
| parentNode  | 父节点                         |
| newNode     | 将要添加的新节点               |
| 返回值      | 插入成功返回true,失败返回false |

##### javascript  removeChind()  删除节点

removeChild()方法用来删除父节点的一个子节点。

parent.removeChild(thisNode) 

| 参数     | 说明                                    |
| -------- | --------------------------------------- |
| thisNode | 当前节点，即要删除的节点                |
| parent   | 当前节点的父节点，即thisNode.parentNode |

##### javascript  cloneNode(): 克隆节点

nodeObject.cloneNode(boolean);

参数/返回值说明：

| 参数       | 语法                                                         |
| ---------- | ------------------------------------------------------------ |
| nodeObject | 节点对象，即要克隆的节点                                     |
| boolean    | 布尔值，是否完全克隆。  true :完全克隆，false :只克隆当前节点，不克隆任何子节点 |

##### JavaScript获取CSS样式

语法：

nodeObject.style.cssProperty;

其中nodeObject为节点对象，cssProperty为css属性

> 注意：对于“-”分隔的属性，要去掉“-”,并将“-”后的第一个字母大写，javascript不会到<style>标签或者css文件中获取相应的样式，只能获取style属性定义的样式

##### javascript 事件源

事件源是作为event对象的属性存在的。在W3C规范中，这个属性是 target ；但是 IE8.0 及其以下版本不支持该属性，它使用 srcElement 属性来获取事件源。

##### JavaScript 获取鼠标坐标

鼠标的坐标包括X坐标、Y坐标、相对于客户端的坐标、相对于屏幕的坐标

javascript  中，鼠标坐标是作为event对象的属性存在的

event对象中有关鼠标坐标的属性。

​                                                     W3C规范所规定的属性

| 属性    | 描述                                             |
| ------- | ------------------------------------------------ |
| clientX | 鼠标指针相对客户端（即浏览器文档区域）的水平坐标 |
| clientY | 鼠标指针相对客户端（即浏览器文档区域）的垂直坐标 |
| screenX | 鼠标指针相对计算机屏幕的水平坐标                 |
| screenY | 鼠标指针相对计算机屏幕的垂直坐标                 |

##### 	JavaScript event对象：当前事件

在 W3C 规范中，event 对象是随事件处理函数传入的，Chrome、FireFox、Opera、Safari、IE9.0及其以上版本都支持这种方式；但是对于 IE8.0 及其以下版本，event 对象必须作为 window 对象的一个属性。

◆ 在遵循 W3C 规范的浏览器中，event 对象通过事件处理函数的参数传入。

语法：

```
elementObject.OnXXX=function(e){
    var eve=e; // 声明一个变量来接收 event 对象
}
```

##### JavaScript绑定事件的方法

一. 在DOM元素中直接绑定

```
<input  onclick="alert('谢谢支持')"  type="button"  value="点击我，弹出警告框" />
```

二. 在JavaScript代码中绑定

```
elementObject.onXXX=function(){
    // 事件处理代码
}
```

三. 绑定事件监听函数

绑定事件的另一种是用addEventListener()或attachEvent()来绑定事件监听函数

addEventListener() 函数语法：

elementObject.addEventListener(eventName,handle,useCapture);

| 参数          | 说明                                                        |
| ------------- | ----------------------------------------------------------- |
| elementObject | DOM对象（即DOM元素）                                        |
| eventName     | 事件名称，事件名称不加“on”                                  |
| handle        | 事件句柄函数，即用来处理事件的函数                          |
| useCapture    | Boolean类型，是否使用捕获，一般使用false,涉及到事件流的概念 |

attachEvent()函数语法：

elementObject.attachEvent(eventName,handle);

| 参数          | 说明                               |
| ------------- | ---------------------------------- |
| elementObject | DOM对象（即DOM元素）               |
| eventName     | 事件名称，事件名称不加“on”         |
| handle        | 事件句柄函数，即用来处理事件的函数 |

> 注意：事件句柄函数是指“函数名”，不能带小括号





























