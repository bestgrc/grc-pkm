# 表单验证之拒绝特殊字符

- 解决方案：正则匹配

[参考资料](https://blog.csdn.net/myslife/article/details/18035415?utm_source=copy )

```javascript
function ValidateSpecialCharacter() {   
    var code;    
    //获取代码
    if (document.all) { //判断是否是IE浏览器    
    code = window.event.keyCode;    
    } else {     
        code = arguments.callee.caller.arguments[0].which;    
    }    
    var character = String.fromCharCode(code);   
    var txt=new RegExp("[            ,\\`,\\~,\\!,\\@,\#,\\$,\\%,\\^,\\+,\\*,\\&,\\\\,\\/,\\?,\\|,\\:,\\.,\\<,\\>,\\{,\\},\\(,\\),\\'',\\;,\\=,\"]");    //特殊字符正则表达式   
    if (txt.test(character)) {    //test() 方法用于检测一个字符串是否匹配某个模式.
        if (document.all) {      
            window.event.returnValue = false;     
        } else {  
            arguments.callee.caller.arguments[0].preventDefault();   
        }    
    }
```

>### 在 IE 中 document.all 的布尔值是 true ，其他浏览器都是 false。
>
>- 参考资料
>  - [document.all 在各浏览器中的支持不同](https://blog.csdn.net/fengweifree/article/details/16862495)







### 同步交互：

- 指发送一个请求,需要等待返回,然后才能够发送下一个请求，有个等待过程；

### 异步交互：

- 指发送一个请求,不需要等待返回,随时可以再发送下一个请求，即不需要等待。 区别：一个需要等待，一个不需要等待，在部分情况下，我们的项目开发中都会优先选择不需要等待的异步交互方式。

