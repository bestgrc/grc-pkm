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