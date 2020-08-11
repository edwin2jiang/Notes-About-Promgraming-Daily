## 去除table的内边框 

```css
border-collapse:collapse;
```

## 将鼠标变成手的形状

```css
cursor:pointer//鼠标悬浮变"手"
```

## 刷新当前页面

```
window.location.reload();
```

## 获取对象的长度

//对象的长度不能用.length获取，用js原生的Object.keys可以获取到

```js
var obj = {'name' : 'Tom' , 'sex' : 'male' , 'age' : '14'}; 
var arr = Object.keys(obj); 
console.log(arr);  // ['name','sex','age'] 
console.log(arr.length);  //3
```

## a标签的下划线去除

```css
text-decoration:none;
color:black
```

## 判断变量是否被定义

```
typeof('xxx') == "undefined"
```

## copyright自动改变时间的写法

![版权](C:\Users\17540\Desktop\版权.jpg)

## 字符串里面包裹变量

```js
var str = "hello" + name ;
```

## JS修改css样式

```
element.style["display"] = "none";
```

## 灵活的对话框

```js
window.onbeforeunload = function (e) {
			    var e = e || window.event,
			        dialogText = '页面还未保存，确定要离开吗？';
			    // 兼容IE8和Firefox 4之前的版本
			    if (e) {
			        e.returnValue = dialogText;
			    };
			    // Chrome, Safari, Firefox 4+, Opera 12+ , IE 9+
			    return dialogText;
};
```



## line-height设置为数字

![image-20200306221036585](C:\Users\17540\AppData\Roaming\Typora\typora-user-images\image-20200306221036585.png)

### jquery下的$运算符返回的是一个数组（id、class均是）

```
var a = $("#mesNickNameInsert")[0];
console.log(a);
var b = document.getElementById("mesNickNameInsert");
console.log(b);
```

<button type="submit" id="btn">btn</button>

第一种:
$("#btn").click(function(event){

第二种:
document.getElementById('#foo').addEventListener('click', function() {
});

第三种:
html代码：
<button type="submit" id="btn" onclick="btn()">btn</button>
js代码：
function btn(){

}

第四种:
$('#btn').bind('click', function();

第五种:
$("btn").on("click",function(){});

## 万能绑定事件

html

```html
<p class="className">test</p>
```

jquery

```js
$(function(){
			$(document).on("click",".className",function(){
				alert("123");
			})
		})
```

与一般的相比优势在于可以作用于append添加进去的按钮。

1.  原生js通过innerhtml解决无法在appendchild里面写标签
2.  为 <div> 元素添加 class:

document.getElementById("myDIV").classList.add("mystyle");
7.  a标签href无值，点击刷新页面解决办法
href="javascript:" 或 href="javascript:void(0)" 

8.  为 <div> 元素添加多个类:

   document.getElementById("myDIV").classList.add("mystyle", "anotherClass", "thirdClass");

   为 <div> 元素移除一个类:

   document.getElementById("myDIV").classList.remove("mystyle"); 

   为 <div> 元素移除多个类:

   document.getElementById("myDIV").classList.remove("mystyle", "anotherClass", "thirdClass");
   
9. table是一个整体，每一列td的宽度是由其中一个最长td的宽度决定的。

   ​								每一行td的高度是由其中一个最长td的高度决定的。

   所以设置td的宽度和高度是没有用的。line-height 可以生效。

   ```kotlin
   word-wrap: break-word
   word-break: break-all
   ```

再设置百分比宽度就可以生效了

10. opacity  不透明度的设置

![image-20200210233810558](C:\Users\17540\AppData\Roaming\Typora\typora-user-images\image-20200210233810558.png)

11. 实现上下居中

将height 和 line-height 设置为同一个数值 实现 上下居中

