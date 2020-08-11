# ajax技术学习笔记

**所有现代浏览器（IE7+、Firefox、Chrome、Safari 以及 Opera）均内建 XMLHttpRequest 对象。 ****创建 XMLHttpRequest 对象的语法：**
***variable*=new XMLHttpRequest();**
**老版本的 Internet Explorer （IE5 和 IE6）使用 ActiveX 对象：**
***variable*=new ActiveXObject("Microsoft.XMLHTTP");**

XMLHttpRequest 对象用于和服务器交换数据。

| 属性               | 描述                                                         |
| :----------------- | :----------------------------------------------------------- |
| onreadystatechange | 存储函数（或函数名），每当 readyState 属性改变时，就会调用该函数。 |
| readyState         | 存有 XMLHttpRequest 的状态。从 0 到 4 发生变化。  0: 请求未初始化 1: 服务器连接已建立 2: 请求已接收 3: 请求处理中 4: 请求已完成，且响应已就绪 |
| status             | 200: "OK"404: 未找到页面                                     |

在 onreadystatechange 事件中，我们规定当服务器响应已做好被处理的准备时所执行的任务。



当 readyState 等于 4 且状态为 200 时，表示响应已就绪：



```js
xmlhttp.onreadystatechange=function()
  {
  if (xmlhttp.readyState==4 && xmlhttp.status==200)
    {
    document.getElementById("myDiv").innerHTML=xmlhttp.responseText;
    }
  }
```

## GET 还是 POST？

与 POST 相比，GET 更简单也更快，并且在大部分情况下都能用。

然而，在以下情况中，请使用 POST 请求：

- 无法使用缓存文件（更新服务器上的文件或数据库）
- 向服务器发送大量数据（POST 没有数据量限制）
- 发送包含未知字符的用户输入时，POST 比 GET 更稳定也更可靠

## POST 请求

一个简单 POST 请求：

## 实例

xmlhttp.open("POST","/try/ajax/demo_post.php",true); xmlhttp.send();

如果需要像 HTML 表单那样 POST 数据，请使用 setRequestHeader() 来添加 HTTP 头。然后在 send() 方法中规定您希望发送的数据：

## 实例

xmlhttp.open("POST","/try/ajax/demo_post2.php",true); xmlhttp.setRequestHeader("Content-type","application/x-www-form-urlencoded"); xmlhttp.send("fname=Henry&lname=Ford");

| 属性         | 描述                       |
| :----------- | :------------------------- |
| responseText | 获得字符串形式的响应数据。 |
| responseXML  | 获得 XML 形式的响应数据。  |

# json

JSON: **J**ava**S**cript **O**bject **N**otation(JavaScript 对象表示法)

JSON 是存储和交换文本信息的语法。类似 XML。

JSON 比 XML 更小、更快，更易解析。

JavaScript 程序能够使用内建的 eval() 函数，用 JSON 数据来生成原生的 JavaScript 对象。

----

异步  客户端不需要等待服务器的响应，在服务器处理请求的过程中，客户端可以进行其他的操作。

![image-20200207172636314](C:\Users\17540\AppData\Roaming\Typora\typora-user-images\image-20200207172636314.png)

![image-20200207190348068](C:\Users\17540\AppData\Roaming\Typora\typora-user-images\image-20200207190348068.png)

![image-20200207192818177](C:\Users\17540\AppData\Roaming\Typora\typora-user-images\image-20200207192818177.png)

success: function (data){}   // data 为响应后返回结果

datatype： 服务器反应结果的类型默认为text,也就是string

$.get 方法

![image-20200207193353313](C:\Users\17540\AppData\Roaming\Typora\typora-user-images\image-20200207193353313.png)

$.post 方法
![image-20200207193714450](C:\Users\17540\AppData\Roaming\Typora\typora-user-images\image-20200207193714450.png)

json  意思是JavaScript对象表示法

![image-20200207210810947](C:\Users\17540\AppData\Roaming\Typora\typora-user-images\image-20200207210810947.png)

![image-20200207212438215](C:\Users\17540\AppData\Roaming\Typora\typora-user-images\image-20200207212438215.png)![image-20200207212438402](C:\Users\17540\AppData\Roaming\Typora\typora-user-images\image-20200207212438402.png)

### 出现乱码问题的解决方法

![image-20200207224005443](C:\Users\17540\AppData\Roaming\Typora\typora-user-images\image-20200207224005443.png)

![image-20200207224353542](C:\Users\17540\AppData\Roaming\Typora\typora-user-images\image-20200207224353542.png)

