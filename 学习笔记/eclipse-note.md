# eclipse常用设置

### 一、自动补全代码

#### 问题描述:
一个字符为输入完全时自动弹出补全提醒，提高编程效率

#### 解决方案:
1. Window
2. Preference
3. Java
3. Editor
4. Content Assist
5. Auto activation tiggers for java


### 二、字体大小修改

#### 问题描述：
修改.java文件代码字体大小

#### 解决方案：
1. Window
2. Preference
3. general
4. appearance
5. color and fonts
6. basic
7. Text Font

 >大小设置成小四比较适中。

### 三、新建类自动添加注释

 #### 方法一：Eclipse中设置在创建新类时自动生成注释

  1. windows–>preference
  2. Java–>Code Style–>Code Templates
  3. code–>new Java files
  4. 编辑

  ```java
    ${filecomment}
    ${package_declaration}
    /**
    * @author 作者 E-mail:
    * @version 创建时间：${date} ${time}
    * 类说明
    */
    ${typecomment}
    ${type_declaration}
  ```

  [参考文献](https://blog.csdn.net/xyw591238/article/details/50978162)

### 四、jsp字符编码默认值

#### 修改为utf-8

#### 解决方法

1. window
2. Web
3. jsp files
4. Encoding

### 五、显示空白符，如空格、制表符、换行符

1. windows–>preference
2. general
3. editors
4. text editors
5. show whitespace characters

### 六、使用空格代替tab

1. windows–>preference
2. general
3. editors
4. text editors
5. insert space for tabs(displayed tab width :4)



1. windows–>preference
2. java
3. code style
4. formatter
5. new
6. space only



快捷键

Alt+Shift+L 返回值对象快捷键