# Java学习笔记

## 投入时间 合计：3小时37分钟

2. 23    14:26 - 18:03    3小时37分钟

**人机交互方式：**

![image-20200223143314426](http://q9ky36hj2.bkt.clouddn.com/img/image-20200223143314426.png)

![image-20200223143505332](http://q9ky36hj2.bkt.clouddn.com/img/image-20200223143505332.png)

![image-20200223145325497](http://q9ky36hj2.bkt.clouddn.com/img/image-20200223150615242.png)

通过JVM模拟到对应的操作系统

![image-20200223150615242](http://q9ky36hj2.bkt.clouddn.com/img/image-20200223150729533.png)

![image-20200223150729533](http://q9ky36hj2.bkt.clouddn.com/img/image-20200223152030864.png)

![image-20200223152030864](http://q9ky36hj2.bkt.clouddn.com/img/image-20200223145325497.png)

命令行下

- javac编译

- java运行

main函数是程序的入口

```java
public static void main(String[] args){
	System.out.print("hello world");
         }
}
```

声名为public的主类应与文件名一直，否则编译失败

![image-20200223153024809](http://q9ky36hj2.bkt.clouddn.com/img/image-20200223154926046.png)

### 变量

#### 关键字，保留字（以后的java版本可能会用到的）

![image-20200223154048492](http://q9ky36hj2.bkt.clouddn.com/img/image-20200223153024809.png)

命名规范：
![image-20200223154204527](http://q9ky36hj2.bkt.clouddn.com/img/image-20200223154204527.png)

java中变量的定义：

数据类型 变量名 = 变量的值， 例如：int i=1；

#### 使用变量注意点：

![image-20200223154739483](http://q9ky36hj2.bkt.clouddn.com/img/image-20200223155446317.png)

### 变量的数据类型

<img src="http://q9ky36hj2.bkt.clouddn.com/img/image-20200223154739483.png" alt="image-20200223154926046" style="zoom:200%;" />

#### 整形数据：

![image-20200223155446317](http://q9ky36hj2.bkt.clouddn.com/img/image-20200223155952764.png)

定义long变量类型时，要在值得后面加上一个l(小写的“L”);

#### 浮点类型：

![image-20200223155658434](http://q9ky36hj2.bkt.clouddn.com/img/image-20200223154048492.png)

#### 布尔类型：

![image-20200223155952764](http://q9ky36hj2.bkt.clouddn.com/img/image-20200223155658434.png)

```
printf主要是继承了C语言的printf的一些特性，可以进行格式化输出。
print就是一般的标准输出，但是不换行。
println和print基本没什么差别，就是最后会换行。
```

引用类型,都可以使用null作为值；

String s0 = "hello"

String s1 = "hello"；

不会再村中中存在两个“hello”,只存在一个“hello”

实际上仅仅只是引用地址。

#### 基本数据类型转换

![image-20200223163122504](http://q9ky36hj2.bkt.clouddn.com/img/image-20200223163122504.png)

强制类型转换

```java
int k = 7;
byte b0 = (byte) k;   //将k强制转换成byte数据类型
```

注意：

byte、short、char类型之间不会相互转换，都会直接变成int

而容量大的是无法自动转换成更小的。

例如