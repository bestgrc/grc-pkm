# AJAX

## what

- AJAX = Asynchronous JavaScript and XML（异步的 JavaScript 和 XML）。

- AJAX 不是新的编程语言，而是一种使用现有标准的新方法。

- AJAX 是与服务器交换数据并更新部分网页的艺术，在不重新加载整个页面的情况下。



## XMLHttpRequest 

**XMLHttpRequest 是 AJAX 的基础。**

所有现代浏览器均支持 XMLHttpRequest 对象（IE5 和 IE6 使用 ActiveXObject）。

### 请求

| 方法                               | 概述                                                         |
| ---------------------------------- | ------------------------------------------------------------ |
| variable=new XMLHttpRequest();     | 创建                                                         |
| open(*method*,*url*,*async*)       | 规定请求的类型、URL 以及是否异步处理请求。<br>method：请求的类型；GET 或 POST将请求发送到服务器。<br> *url*：文件在服务器上的位置 <br>*async*：true（异步）或 false（同步） |
| send(*string*)                     | *string*：仅用于 POST 请求                                   |
| setRequestHeader(*header*,*value*) | 向请求添加 HTTP 头。<br>*header*: 规定头的名称<br> *value*: 规定头的值 |

### 响应

| 属性         | 概述                       |
| ------------ | -------------------------- |
| responseText | 获得字符串形式的响应数据。 |
| responseXML  | 获得 XML 形式的响应数据。  |

### onreadystatechange 事件

当请求被发送到服务器时，我们需要执行一些基于响应的任务。

每当 readyState 改变时，就会触发 onreadystatechange 事件。

readyState 属性存有 XMLHttpRequest 的状态信息。

下面是 XMLHttpRequest 对象的三个重要的属性：

| 属性               | 概述                                                         |
| ------------------ | ------------------------------------------------------------ |
| onreadystatechange | 存储函数（或函数名），每当 readyState 属性改变时，就会调用该函数。 |
| readyState         | 存有 XMLHttpRequest 的状态。从 0 到 4 发生变化。<br>0: 请求未初始化<br>1: 服务器连接已建立<br>2: 请求已接收<br>3: 请求处理中<br>4: 请求已完成，且响应已就绪 |
| status             | 200: "OK"<br>404: 未找到页面                                 |

当 readyState 等于 4 且状态为 200 时，表示响应已就绪

## 参考资料：

[w3cschool AJAX 教程](<https://www.w3school.com.cn/ajax/index.asp>)



# JSON

## WHAT

- JSON 指的是 JavaScript 对象表示法（*J*ava*S*cript *O*bject *N*otation）
- JSON 是轻量级的文本数据交换格式
- JSON 独立于语言 *
- JSON 具有自我描述性，更易理解

## JSON - 转换为 JavaScript 对象

JSON 文本格式在语法上与创建 JavaScript 对象的代码相同。

由于这种相似性，无需解析器，JavaScript 程序能够使用内建的 [eval() 函数](https://www.w3school.com.cn/jsref/jsref_eval.asp)，用 JSON 数据来生成原生的 JavaScript 对象。

## JSON 语法  

JSON 语法是 JavaScript 语法的子集。

## JSON 值

- 数字（整数或浮点数）
- 字符串（在双引号中）
- 逻辑值（true 或 false）
- 数组（在方括号中）
- 对象（在花括号中）
- null

```javascript
var txt = '{ "employees" : [' +
'{ "firstName":"Bill" , "lastName":"Gates" },' +
'{ "firstName":"George" , "lastName":"Bush" },' +
'{ "firstName":"Thomas" , "lastName":"Carter" } ]}';

var obj = eval ("(" + txt + ")");
```



## JSON 解析器

提示：eval() 函数可编译并执行任何 JavaScript 代码。这隐藏了一个潜在的安全问题。

使用 JSON 解析器将 JSON 转换为 JavaScript 对象是更安全的做法。JSON 解析器只能识别 JSON 文本，而不会编译脚本。

在浏览器中，这提供了原生的 JSON 支持，而且 JSON 解析器的速度更快。

较新的浏览器和最新的 ECMAScript (JavaScript) 标准中均包含了原生的对 JSON 的支持。



参考资料：

[JSON 教程]（<https://www.w3school.com.cn/json/index.asp>）



2、JS中将JSON对象解析为字符串的方法：

var jsonStr = JSON.stringify(json);

3、JS解析JSON对象或者字符串的方法：

var objs = eval(json);或者var objs = eval(jsonStr);



4、页面中Json对象与Json字符串互转(4种转换方式)：

1>jQuery插件支持的转换方式：
$.parseJSON( jsonstr ); //jQuery.parseJSON(jsonstr),可以将json字符串转换成json对象

2>浏览器支持的转换方式(Firefox，chrome，opera，safari，ie9，ie8)等浏览器：

JSON.parse(jsonstr); //可以将json字符串转换成json对象

JSON.stringify(jsonobj); //可以将json对象转换成json对符串

第二个参数可加字符串或数组或方法，过滤出想要的数据。

第三个参数可加数字或字符串，代表缩进所用的空格数或者字符串



json对象可包含一个toJSON方法，序列化的顺序如下：

(1)如果存在toJSON()方法而且能通过它取得有效的值，则调用该方法。否则，按默认顺序执行序列化

​      (2)如果提供了第二个参数，应用这个函数过滤器，传入的函数过滤器的值是第(1)步返回的值。

​      (3)对第(2)步 返回的每个值进行相应的序列化。

​      (4)如果提供了第三个参数，执行相应的格式化操作。





注：ie8(兼容模式),ie7和ie6没有JSON对象，推荐采用JSON官方的方式，引入json.js。
3>Javascript支持的转换方式：
eval('(' + jsonstr + ')'); //可以将json字符串转换成json对象,注意需要在json字符外包裹一对小括号

包小括号是因为js会将大括号解析为代码块，因而产生错误。



注：ie8(兼容模式),ie7和ie6也可以使用eval()将字符串转为JSON对象，但不推荐这些方式，这种方式不安全eval会执行json串中的表达式。
4>JSON官方的转换方式：
<http://www.json.org/>提供了一个json.js,这样ie8(兼容模式),ie7和ie6就可以支持JSON对象以及其stringify()和parse()方法；
可以在<https://github.com/douglascrockford/JSON-js>上获取到这个js，一般现在用json2.js。



参考资料：

[JS中生成和解析JSON](https://www.cnblogs.com/jiangyy/p/3531150.html)

[js 对象 toJSON 方法](https://www.cnblogs.com/keyi/p/11058558.html)

[深入理解JSON对象](https://www.cnblogs.com/xiaohuochai/p/5887754.html)