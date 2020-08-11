## parseInt 函数　

**parseInt**是把小数转化成整数。它取整的机制是从要取整数据的左边读取，当碰到非数字则自动结束，相当于截取到前面已读到的数字。代码如下:

```html
<html>

<head>
<title></title>
</head>
    <script>
        var a=11.1
        var b='12as12'
        var c='a12'
        alert(parseInt(a))         //结果为11
        alert(parseInt(b))         //结果为12
        alert(parseInt(c))        //结果为NaN
    </script>
<body>
    
</body>

</html>
```