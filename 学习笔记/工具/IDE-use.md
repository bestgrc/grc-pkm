# idea 插件：

| 插件                   | 作用                                        | 是否在用 | 快捷键         | 评价                                                    |
| ---------------------- | ------------------------------------------- | -------- | -------------- | ------------------------------------------------------- |
| Lombok                 | javabean省去getset等板式代码                | 是       | 注解           | 开发必备                                                |
| Free Mybatis           | mapper 的xml与接口文件快速互相定位          | 是       | 页面点击       | mybatis开发必备                                         |
| Request mapping        | 快速搜到controller                          | 是       | ctrl+shift+\   | springmvc开发必备                                       |
| Key promoter           | 快捷键提醒                                  |          |                | 提高开发效率必学                                        |
| Translation            | 翻译                                        | 是       | ctrl+shift+o   | 省的去浏览器搜单词                                      |
| idea-mybatis-generator | 根据数据库表生成javaBean与mapper文件        |          | 菜单栏->plugin | 节约时间，配合mybatis kt使用，可以大大减少dao层开发时间 |
| SonarList              | 代码检查                                    |          |                | 公司技术规范，全英文，可用阿里p3c替代。                 |
| GenerateAllSetter      | 一键写出所有set方法                         |          |                |                                                         |
| Maven Helper           | 解决maven依赖冲突问题                       |          |                | 目前maven用的挺正常，这个用不上                         |
| stackoverflow          | 程序设计领域的问答网站，用于搜索问题        |          |                |                                                         |
| JRebel                 | IntelliJ IDEA 官方出的学习辅助插件          |          |                |                                                         |
| IDE Features Trainer   |                                             |          |                |                                                         |
| MyBatis Log Plugin     | 更优秀的sql日志<br>可以直接复制到数据库使用 |          |                |                                                         |
| REST Clinet plugin     | 接口调试/测试                               |          |                | https://mp.weixin.qq.com/s/J0QzkaDsKBX7ztG-aSzWKA       |
| Rainbow Brackets       | 彩虹括号                                    |          |                | 有点花，实用性不大                                      |
| Nyan progress bar      | 彩虹进度条                                  |          |                | 弄了玩                                                  |



# idea 快捷方法

| 功能           | 按键                                                         |
| -------------- | ------------------------------------------------------------ |
| BookMark       | 插入基本书签 F11<br>助记符号书签 Ctrl+F11<br>插入数字书签 Ctrl+Shift+任意数字<br>查看书签         Shift + F11<br>跳转数字书签 Ctrl+对应的标签数字 |
| 快速操作代码块 | Code --> Surround With<br>Ctrl+Alt+T                         |
| 快速定义变量   | Refactor --> Extract --> Variable<br>Ctrl+Alt+V Variable<br>Ctrl+Alt+C Constant<br/>Ctrl+Alt+F Field<br/>Ctrl+Alt+P Parameter |
|                |                                                              |
|                |                                                              |



> 菜单栏被隐藏的修复方式
>
> <https://blog.csdn.net/lqazcx55/article/details/99953762>
>
> 所有系统配置都是在xml文件里的



# eclipse常用设置

| 设置项                 | 路径                                                         |
| ---------------------- | ------------------------------------------------------------ |
| 代码补全提示           | Window-->Preference-->Java-->Editor-->Content Assist-->Auto activation tiggers for java |
| 字体大小修改           | Window-->Preference-->general-->appearance-->color and fonts-->basic-->Text Font |
| 类创建自动注释         | windows-->preference-->Java–>Code Style–>Code Templates-->code–>new Java files |
| jsp字符编码默认值      | window-->Web-->jsp files-->Encoding                          |
| 显示空白符             | windows-->preference-->general-->editors-->text editors-->show whitespace characters |
| 使用空格代替tab        | windows-->preference-->general-->editors-->text editors-->insert space for tabs(displayed tab width :4) |
| 只使用空格             | windows-->preference-->java-->code style-->formatter-->new-->space only-->--> |
| Tomcat启动时间限制调节 | server-->双击tomcat server容器进入配置文件界面-->Timeouts-->Start(in seconds) |
| 插件安装               | Help --> Install New Software<br>markdown http://winterwell.com/software/updatesite/ |
| 取消validating         | Eclispe-->Window-->Preferences-->Validation-->Suspeng all validators |
| tomcat 热部署          |                                                              |
|                        |                                                              |



类创建自动注释模板

```java
    ${filecomment}
    ${package_declaration}
    /**
    * @author 顾仁才
    * @date ${year} ${date} ${time}
    */
    ${typecomment}
    ${type_declaration}
```



# eclipse快捷键

| 功能                   | 快捷键       |
| ---------------------- | ------------ |
| 返回值对象             | Alt+Shift+L  |
| 打开资源               | Ctrl+Shift+R |
| 全局搜索               | Ctrl+H       |
| OutLine大纲视图        | Ctrl+O       |
| 切换编辑的文件         | Ctrl+E       |
| 找到变量或方法的调用处 | Ctrl+Shift+G |

