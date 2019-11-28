# 天津调查措施 文件传输系统 

## 序言

文件传输系统告一段落，作为开发，首次独立开发一个项目。从开发到测试发版，投入12人天。

麻雀虽小，五脏俱全。

## 使用组件

### 公司组件

1. Artery6
2. TCS Client
3. sqlfx
4. ArteryBase

### 开源组件

1. Minio
2. Springboot 集成SSM
3. Jenkins 及 Sonar
4. lombok

### 集成插件

1. spring-boot-devtools 实现热部署？
2. pagehelper-spring-boot-starter 实现后端分页
3. maven-compiler-plugin 编译
4. spring-boot-maven-plugin 打包



## 组件记录

### 1. 前端上传文件及取消上传的ajax请求

#### 1）发送文件

```javascript
// 模拟一个表单
var formData = new FormData();
// 添加数据
formData.append('file', this.file)
// 创建请求
this.fileXHR = new XMLHttpRequest(),
method = "POST",
// window.location 里有很多东西，有时间可以去看一下。
url = window.location.origin + "/filetransfer/file"
// 打开连接
this.fileXHR.open(method,url,true);
// 上传进度条
this.fileXHR.upload.onprogress = function (event) {
	_this.percent = parseInt((event.loaded/event.total)*100)
}
// 发送表单
this.fileXHR.send(formData);
// 回调函数
this.fileXHR.onreadystatechange = function (response) {
	if (_this.fileXHR.readyState === 4 && _this.fileXHR.status === 200) {             			_this.notice(JSON.parse(response.target.response).sqid,_this.fileData.recever)
	}
}
```

#### 2）取消请求

```javascript
this.fileXHR.abort();
```

### 2.文件随表单上传

​	

前端核心：

```javascript
// 修改请求头
headers: {
	'Content-Type': 'multipart/form-data',
	'charset': 'UTF-8'
},
// 使用它模拟表单数据
let formData = new FormData();
// 将表单数据全部转为json格式，文件不动
JSON.stringify
```

后端接收：

使用注解

```java
@RequestParam
```



查看@RequestParam 注解时，查看到其源码中的三种注解

```java
// 注解使用的位置 ，此处为“参数”中
@Target(ElementType.PARAMETER)
// 作用范围
@Retention(RetentionPolicy.RUNTIME)
// 写入文档
@Documented
```

| 注解         | @RequestParam                     | **@RequestBody**                                             |
| ------------ | --------------------------------- | ------------------------------------------------------------ |
| 参数来源     | requestHeader，请求头             | requestBody，请求体                                          |
| Content-Type | application/x-www-form-urlencoded | 非application/x-www-form-urlencoded，如:<br>application/json <br> application/xml |

参考资料：

https://cloud.tencent.com/developer/article/1414464



下载文件（不打开页面）

前端

```javascript
var wjUrl = "file" + "?" + "id=" + encodeURI(id);
var link = document.createElement('a');
link.setAttribute("download", "");
link.href = wjUrl;
link.click();
```



后端

```java
        try {
            fileName = URLEncoder.encode(fileName, "utf-8");
        } catch (UnsupportedEncodingException e) {
            logger.error("文件名转码失败",e);
        }
        response.setHeader("contentType", "application/octet-stream");
        response.setHeader("Content-Disposition", "attachment; filename=\"" + fileName + "\";filename*=UTF-8''" + fileName);
        response.setContentType("application/octet-stream");
        try(InputStream in = (iStoreService.getInputStream(storagePath));
            OutputStream out = response.getOutputStream()) {
            ByteStreams.copy(in, out);
        } catch (StorageException|IOException e) {
            logger.error("下载审批表过程出错",e);
        }
```





变量随表单加载时加载。





想用未用的组件：

mybatis-generater 根据库表自动生成 javabean及mapper文件

mybatis-tk 通用mapper，减少单表的sql语句编写。

编写.sh脚本，方便部署后的项目调试。

## 踩过的坑

javabean中用包装类代替基础类。防止基础类的默认值导致问题。

Artery的登录页面存在bug，升级版本后修复。

mybatis mapper文件扫描配置。

