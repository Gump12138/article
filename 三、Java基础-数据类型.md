# 三、Java基础-数据类型

[TOC]

## (一)基础数据类型

- 整数型

| 整数型 | 大小 | 封装类  | 默认值 | 数据库类型                      |
| :----: | :--: | :-----: | :----: | ------------------------------- |
|  byte  |  8   |  Byte   |   0    | byte[]——blob                    |
| short  |  16  |  Short  |   0    |                                 |
|  int   |  32  | Integer |   0    | tinyint，smallint，mediuminnt， |
|  long  |  64  |  Long   |   0    | integer                         |

- 浮点型

| 浮点型 | 大小 | 封装类 | 默认值 | 数据库类型 |
| ------ | ---- | ------ | ------ | ---------- |
| float  | 32   | Float  | 0.0    | FLOAT      |
| double | 64   | Double | 0.0    | DOUBLE     |



- 字符型

| 字符型 | 大小 | 封装类    | 默认值 | 数据库类型 |
| ------ | ---- | --------- | ------ | ---------- |
| char   | 16   | Character | 空     | char[1]    |



- 布尔型

| 布尔型  | 大小 | 封装类  | 默认值 | 数据库类型 |
| ------- | ---- | ------- | ------ | ---------- |
| boolean | 8    | Boolean | false  | bit        |



## (二)引用数据类型

引用类型是除了基本类型之外的所有类型

如String，Student A=new Student()等



## (三)Java值传递

​	当我们在方法中声明一个 int i = 0，或者 Object obj = null 时，仅仅涉及stack，不影响到heap，当我们 new Object() 时，会在heap中开辟一段内存并初始化Object对象。当我们将这个对象赋予obj变量时，仅仅是stack中代表obj的那4个字节变更为这个对象的地址。

```
public class TestMain {

	public static void main(String[] args) {
		List<Integer> list = new ArrayList<Integer>();
		for (int i = 0; i < 10; i++) {
			list.add(i);
		}
		add(list);
		for (Integer j : list) {
			System.err.print(j+",");;
		}
		System.err.println("");
		System.err.println("*********************");
		String a="A";
		append(a);
		System.err.println(a);
		int num = 5;
		addNum(num);
		System.err.println(num);
	}
	
	static void add(List<Integer> list){
		list.add(100);
	}
	
	static void append(String str){
		str+="is a";
	}
	static void addNum(int a){
		a=a+10;
	}
}

0,1,2,3,4,5,6,7,8,9,100
*********************
A
5

```

```
第一个例子：基本类型
void foo(int value) {
    value = 100;
}
foo(num); // num 没有被改变

第二个例子：没有提供改变自身方法的引用类型
void foo(String text) {
    text = "windows";
}
foo(str); // str 也没有被改变

第三个例子：提供了改变自身方法的引用类型
StringBuilder sb = new StringBuilder("iphone");
void foo(StringBuilder builder) {
    builder.append("4");
}
foo(sb); // sb 被改变了，变成了"iphone4"。

第四个例子：提供了改变自身方法的引用类型，但是不使用，而是使用赋值运算符。
StringBuilder sb = new StringBuilder("iphone");
void foo(StringBuilder builder) {
    builder = new StringBuilder("ipad");
}
foo(sb); // sb 没有被改变，还是 "iphone"。
```

下面是第三个例子的图解：

![img](https://pic4.zhimg.com/d8b82e07ea21375ca6b300f9162aa95f_b.jpg)



builder.append("4")之后

![img](https://pic4.zhimg.com/80/ff2ede9c6c55568d42425561f25a0fd7_hd.jpg)

> 作者：Intopass
>
> 链接：https://www.zhihu.com/question/31203609/answer/50992895
>
> 来源：知乎
>
> 著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。



> 无论你传入的参数是什么,传过去的都仅仅是一个副本而已,这个副本作为方法的局部变量保存在栈中。
>
>
> 假设传的是基本数据类型,改动这个值并不会影响作为參数传进来的那个变量,由于你改动的是方法的局部变量,是一个副本。
> 假设传的是一个对象的引用,也是一样的,也是一个副本,可是这个副本和作为參数传进来的那个引用指向的是内存中的同一个对象,所以你通过这个副本也能够操作那个对象。可是假设你改动这个引用本身,比方让他指向内存中的另外一个对象,原来作为參数传进来的那个引用不会受到影响。



