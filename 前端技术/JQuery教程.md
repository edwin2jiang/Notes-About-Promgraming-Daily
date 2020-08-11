# jQuery 学习笔记

## 网页中添加 jQuery

可以通过多种方法在网页中添加 jQuery。 您可以使用以下方法：

- 从 [jquery.com](http://jquery.com/download/) 下载 jQuery 库
- 从 CDN 中载入 jQuery, 如从 Google 中加载 jQuery

百度的CDN：

```html
<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.4.1/jquery.min.js">
</script>
```

新浪的CDN:
```html
<script src="https://lib.sinaapp.com/js/jquery/2.0.2/jquery-2.0.2.min.js">
</script>			
```

BootCDN：

```html
<script src="https://cdn.bootcss.com/jquery/3.4.1/jquery.min.js"></script>
```

jQuery 语法是通过选取 HTML 元素，并对选取的元素执行某些操作。

基础语法： **$(\*selector\*).\*action\*()**

- 美元符号定义 jQuery

- 选择符（selector）"查询"和"查找" HTML 元素

- jQuery 的 action() 执行对元素的操作

  ----

- $(this).hide() - 隐藏当前元素
- $("p").hide() - 隐藏所有 <p> 元素
- $("p.test").hide() - 隐藏所有 class="test" 的 <p> 元素
- $("#test").hide() - 隐藏所有 id="test" 的元素

## 文档就绪事件

$(document).ready(function(){    // 开始写 jQuery 代码...  });

这是为了防止文档在完全加载（就绪）之前运行 jQuery 代码，即在 DOM 加载完成后才可以对 DOM 进行操作。

如果在文档没有完全加载之前就运行函数，操作可能失败。

**提示：**简洁写法（与以上写法效果相同）:

```js
$(function(){    // 开始写 jQuery 代码...  });
```

一般称之为入口函数

![20171231003829544](C:\Users\17540\Desktop\20171231003829544.jpeg)

## jQuery 选择器

基于元素的 id、类、类型、属性、属性值等"查找"（或选择）HTML 元素。

| 语法                         | 描述                                                  |
| :--------------------------- | :---------------------------------------------------- |
| $("*")                       | 选取所有元素                                          |
| $(this)                      | 选取当前 HTML 元素                                    |
| $("p.intro")                 | 选取 class 为 intro 的 <p> 元素                       |
| $("p:first")                 | 选取第一个 <p> 元素                                   |
| $("ul li:first")             | 选取第一个 <ul> 元素的第一个 <li> 元素                |
| $("ul li:first-child")       | 选取每个 <ul> 元素的第一个 <li> 元素                  |
| $("[href]")                  | 选取带有 href 属性的元素                              |
| **$("a[target='_blank']")**  | **选取所有 target 属性值等于 "_blank" 的 <a> 元素**   |
| **$("a[target!='_blank']")** | **选取所有 target 属性值不等于 "_blank" 的 <a> 元素** |

$("li[class = 'disable']")  

**中间不能用判断等于**   而是直接一个等于符号

## jQuery事件

| Event 函数                       | 绑定函数至                                     |
| :------------------------------- | :--------------------------------------------- |
| $(document).ready(function)      | 将函数绑定到文档的就绪事件（当文档完成加载时） |
| $(selector).dblclick(function)   | 鼠标左键双击事件                               |
| $(selector).mouseover(function)  | 鼠标悬停事件                                   |
| $(selector).mouseenter(function) | 鼠标经过事件                                   |
| $(selector).mouseleave(function) | 鼠标离开事件                                   |
| $(selector).focus(function)      | 被选元素的获得焦点事件                         |
| $(selector).blur(function)       | 元素失去焦点事件                               |

![image-20200214185757928](C:\Users\17540\AppData\Roaming\Typora\typora-user-images\image-20200214185757928.png)

## jQuery下实现ajax

jQuery load() 方法是简单但强大的 AJAX 方法。

其中的函数和方法允许我们在不刷新浏览器的情况下从服务器加载数据

$(selector).load(URL,data,callback);

- 必需的 *URL* 参数规定您希望加载的 URL。
- 可选的 *data* 参数规定与请求一同发送的查询字符串键/值对集合。
- 可选的 *callback* 参数是 load() 方法完成后所执行的函数名称。

回调函数可以设置不同的参数：

- *responseTxt* - 包含调用成功时的结果内容
- *statusTXT* - 包含调用的状态
- *xhr* - 包含 XMLHttpRequest 对象

两种在客户端和服务器端进行请求-响应的常用方法是：GET 和 POST。

- *GET* - 从指定的资源请求数据
- *POST* - 向指定的资源提交要处理的数据

GET 基本上用于从服务器获得（取回）数据。注释：GET 方法可能返回缓存数据。

POST 也可用于从服务器获取数据。不过，POST 方法不会缓存数据，并且常用于连同请求一起发送数据。

### $.get()方法

$.get(*URL*,*callback*);

```js
$(document).ready(function(){
	$("button").click(function(){
		$.get("/try/ajax/demo_test.php",function(data,status){
			alert("数据: " + data + "\n状态: " + status);
		});
	});
});
```

### $.post() 方法

$.post() 方法通过 HTTP POST 请求向服务器提交数据。

**语法:**

$.post(*URL,data,callback*);

```js
$("button").click(function(){
		$.post("/try/ajax/demo_test_post.php",{
			name:"菜鸟教程",
			url:"http://www.runoob.com"
		},
		function(data,status){
			alert("数据: \n" + data + "\n状态: " + status);
		});
	});
```

### **GET 和 POST 方法的区别**：

**1、发送的数据数量**

在 GET 中，只能发送有限数量的数据，因为数据是在 URL 中发送的。

在 POST 中，可以发送大量的数据，因为数据是在正文主体中发送的。

**2、安全性**

GET 方法发送的数据不受保护，因为数据在 URL 栏中公开，这增加了漏洞和黑客攻击的风险。

POST 方法发送的数据是安全的，因为数据未在 URL 栏中公开，还可以在其中使用多种编码技术，这使其具有弹性。

**3、加入书签中**

GET 查询的结果可以加入书签中，因为它以 URL 的形式存在；而 POST 查询的结果无法加入书签中。

**4、编码**

在表单中使用 GET 方法时，数据类型中只接受 ASCII 字符。

在表单提交时，POST 方法不绑定表单数据类型，并允许二进制和 ASCII 字符。

**5、可变大小**

GET 方法中的可变大小约为 2000 个字符。

POST 方法最多允许 8 Mb 的可变大小。

**6、缓存**

GET 方法的数据是可缓存的，而 POST 方法的数据是无法缓存的。

**7、主要作用**

GET 方法主要用于获取信息。而 POST 方法主要用于更新数据。



