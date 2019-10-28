文件传输

前端控件：

​	<input type="file" enctype="multipart/form-data" id="fileExport" @change="handleFileChange" accept=".rar, .zip" ref="inputer">



js

```javascript
handleFileChange (e) {    
    let inputDOM = this.$refs.inputer;    
    this.fileData.file = inputDOM.files[0];    
    this.file = inputDOM.files[0];// 通过DOM取文件数据    
    let size = Math.floor(this.file.size / 1024);//计算文件的大小　    
    let formData = new FormData();//new一个formData事件   
    formData.append("file",this.file); //将file属性添加到formData里    
    formData.append("revever",this.fileData.recever);    
    let requestConfig = {        
        headers: {            
            'Content-Type': 'multipart/form-data'       
        },   
    }   
},
```







https://www.cnblogs.com/tugenhua0707/p/7599691.html

multipart/form-data 详解



https://www.cnblogs.com/tugenhua0707/p/8975121.html





```java
/**   * 上传文件   * @return   */  
@ResponseBody@PostMapping("file")  
public JSONObject addfile(MultipartFile[] file,HttpServletRequest request) {      CommonsMultipartResolver multipartResolver = new CommonsMultipartResolver();      MultipartHttpServletRequest multiReq = multipartResolver.resolveMultipart(request);      Object recever = multiReq.getAttribute("recever");     
 return fileTransferService.upload(file[0]); 
   }
```

可以解析这个request





```
handleFileChange : function(e) {    let _this = this;    let inputDOM = this.$refs.inputer;    this.fileData.file = inputDOM.files[0];    this.file = inputDOM.files[0];// 通过DOM取文件数据    let formData = new FormData();//new一个formData事件    formData.append("file",this.file); //将file属性添加到formData里    formData.append("revever",this.fileData.recever);    let requestConfig = {        headers: {            'Content-Type': 'multipart/form-data'        },    }    this.$http.post('file', formData, requestConfig).then(function (res) {        _this.notice(res.sqid,_this.fileData.recever)    })},
```