```js
Artery.ajax.post("api/v1/xtsyqk/pageData" , {
   params : {
      form : _this.form
   }
}).then(function(result) {
   let url = window.URL.createObjectURL(new Blob([result]))
   let link = document.createElement('a')
   link.style.display = 'none'
   link.href = url
   link.setAttribute('download', '系统使用情况.xlsx')
   document.body.appendChild(link)
   link.click()
})
```

后端将文件流写道response里



webuploder 实现文件上传，可用来做毕设的技术选型。

https://www.cnblogs.com/winteronlyme/p/7008703.html

