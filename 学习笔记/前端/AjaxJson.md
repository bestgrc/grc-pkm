# AJAX

- AJAX = Asynchronous JavaScript and XML（异步的 JavaScript 和 XML）。

- AJAX 不是新的编程语言，而是一种使用现有标准的新方法。

- AJAX 是与服务器交换数据并更新部分网页的艺术，在不重新加载整个页面的情况下。

## XMLHttpRequest 

**XMLHttpRequest 是 AJAX 的基础。**

所有现代浏览器均支持 XMLHttpRequest 对象（IE5 和 IE6 使用 ActiveXObject）。

### 请求

| 方法                                        | 概述                                                         |
| ------------------------------------------- | ------------------------------------------------------------ |
| var variable=new XMLHttpRequest();          | 创建                                                         |
| variable.open(*method*,*url*,*async*)       | 规定请求的类型、URL 以及是否异步处理请求。<br>method：请求的类型；GET 或 POST将请求发送到服务器。<br> *url*：文件在服务器上的位置 <br>*async*：true（异步）或 false（同步） |
| variable.send(*string*)                     | *string*：仅用于 POST 请求                                   |
| variable.setRequestHeader(*header*,*value*) | 向请求添加 HTTP 头。<br>*header*: 规定头的名称<br> *value*: 规定头的值 |

### 响应

| 属性         | 概述                       |
| ------------ | -------------------------- |
| responseText | 获得字符串形式的响应数据。 |
| responseXML  | 获得 XML 形式的响应数据。  |

#### onreadystatechange 事件

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

- JSON 指的是 JavaScript 对象表示法（*J*ava*S*cript *O*bject *N*otation）
- JSON 是轻量级的文本数据交换格式
- JSON 独立于语言
- JSON 具有自我描述性，更易理解

## JSON 语法  

JSON 语法是 JavaScript 语法的子集。

- 数据在名称/值对中
- 数据由逗号分隔
- 增删改查可参考<https://blog.csdn.net/houfengfei668/article/details/79843625>

## JSON 值

- 数字（整数或浮点数）
- 字符串（在双引号中）
- 逻辑值（true 或 false）
- 数组（在方括号中）
- 对象（在花括号中）
- null

## JSON 解析器

eval() 函数可编译并执行任何 JavaScript 代码。这潜在安全问题。

```javascript
var txt = '{ "employees" : [' +
'{ "firstName":"Bill" , "lastName":"Gates" },' +
'{ "firstName":"George" , "lastName":"Bush" },' +
'{ "firstName":"Thomas" , "lastName":"Carter" } ]}';
var obj = eval ("(" + txt + ")");
```

使用 JSON 解析器将 JSON 转换为 JavaScript 对象是更安全的做法。JSON 解析器只能识别 JSON 文本，而不会编译脚本。

在浏览器中，提供了原生的 JSON 支持，而且 JSON 解析器的速度更快。

###  JSON.stringify

将JSON对象解析为字符串的方法

| 参数     | 说明                                                         |
| -------- | ------------------------------------------------------------ |
| value    | 必需， 要转换的 JavaScript 值（通常为对象或数组）。          |
| replacer | 可选，用于转换结果的函数或数组。<br>1. 如果 replacer 为函数，则 JSON.stringify 将调用该函数，并传入每个成员的键和值。使用返回值而不是原始值。如果此函数返回 undefined，则排除成员。根对象的键是一个空字符串：""。<br>2. 如果replacer为数组，则JSON.stringify只将数组中有的key进行解析。 |
| space    | 可选，文本添加缩进、空格和换行符。<br>1. 如果 space 是一个数字，则返回值文本在每个级别缩进指定数目的空格，如果 space 大于 10，则文本缩进 10 个空格。<br>2. 如果 space 为字符串（当字符串长度超过10个字母，取其前10个字母），该字符串将被作为空格<br>3. space 也可以使用换行符：\t。 |

### JSON.parse

将字符串解析为json对象的方法

| 参数    | 说明                                                        |
| ------- | ----------------------------------------------------------- |
| value   | json字符串                                                  |
| reviver | 转换结果的函数<br>参数：key与value<br>返回值：处理后的value |

#### reviver方法

- 方法中this对象为当前属性
- 遍历顺序为从底层到顶层
- 顶层key为空字符串：“”
- 如果范围undefined，则当前属性从所属对象中删除。

## 参考资料：

JSON 教程https://www.w3school.com.cn/json/index.asp

[JS中生成和解析JSON](https://www.cnblogs.com/jiangyy/p/3531150.html)

[JSON.parse()](<https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse>)

# JSONP

- JSONP = JSON with Padding。是服务器与客户端跨源通信的常用方法。
- JSONP通过给网页添加一个<script>元素，向服务器请求json数据。服务器收到请求后，将数据放在一个指定名字的回调函数的参数位置传回来。带有src元素的标签，src需要输入完整路径，不受同源的限制。
- 优点：简单适用，兼容性好（兼容低版本IE）
- 缺点：只支持get请求，不支持post请求

## 跨域问题

- 一个请求的协议、域名、端口三者任意一个与当前网页url不同则为跨域。

- 浏览器同源策略（Sameoriginpolicy）会阻止跨域通信。

- 跨域限制内容：
  - Cookie、LocalStorage 和 IndexedDB
  - DOM
  - AJAX 请求



参考资料：

[什么是跨域？跨域解决方法](https://blog.csdn.net/qq_38128179/article/details/84956552)

[jsonp原理详解——终于搞清楚jsonp是啥了](https://blog.csdn.net/hansexploration/article/details/80314948>)