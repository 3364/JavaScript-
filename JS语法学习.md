# JavaScrip高级程序设计(第三版)
====

# 什么是JavaScript

JS 是一种基于对象和事件驱动的客户端脚本语言，最初设计是为了检验HTML表单输入的正确性，起源于Netscape公司的LiveScript语言。

# JS的发展历史
让用户填写表单，点了提交按钮。最终服务器返回了一个信息。
Netscape开发了一种语言用于验证。

交互能力。
能够处理复杂的交互

完整JS根据
ECMA+DOM+BOM组成

# JS基本语法
<script type="text/javascript"></script>

语法中，ECMAScript大量借鉴了C及其他C语言的语法

- ECMAScript中的一切都区分大小写。
按照惯例，ECMAScript标识采用驼峰大小写格式。
不要把关键字、保留字、true、false和null用作标识符

注释方面按照
`// 单行注释`
`/*
*/
多行注释`


# 语句
在ECMAS中的语句以一个分号结尾;

`var sum=a+b //即使没有分号也是有效的语句——不推荐`
`var diff=a-b; //有效的语句——推荐`

可以使用C风格的语法把多条语句组合在一个代码块中，即使代码块以
``
{
	}
``

ex:
``
if(test){
	alert(test);
}
``

# 关键字和保留字
>JavaScript高级程序设计(第3版) P22

# 变量
ECMAS的变量是松散类型，也就是说每一个变量仅仅是保存值的占位符。
定义变量时要使用var 操作符，后跟变量名：
`
var message
`
这行代码定义了一个名为message的变量,该变量可以保存任何值
例如
`
var message="hi";
`
可以在修改变量值的同时修改值的类型。


## 局部变量
即使使用var操作定义变量将成为定义该定义该变量的作用域中的局部变量。
   那么这个变量在函数退出时就会被销毁。
例如
```
function test(){
	var message = "hi"  //局部变量
}
test():
alert(message);//错误！
```

## 全局变量
``
function test（）{
	message= "hi"; //全局变量	
}
test():
alert(message);//"hi"
``

> 虽然省略var操作符可以定义全局变量，但是不建议这么操作，因为局部作用于中定义的全局变量很难维护，而且如果有意忽略了var操作符，也会由于相应变量不会马上就有定义二导致不必要的婚礼

可以用一条定义语句来定义多个变量，用逗号隔开即可:
```
var message ="hi",
	found = false,
	age =age;
```

# 数据类型
ECMAS中有5中简单的数据类型，分别是undefined，null，boolean，number和string。还有object。
其中object本质上是由无序的名值组成。

# typeof操作符
typeof用来检测变量的数据类型

```
var massage = "some string";
alert(typeof message);//"string"
alert(typeof(message));//"string"
alert(typeof 95);//"number"
```

# undefined 类型

Underfined 类型只有一个值，在使用var声明变量但未赋值时，这个变量的值为undefined
```
var message;
alert (message==undefined);//ture
```

# Null类型
Null表示一个空对象，使用typeof检测时返回object。

# Boolean类型
Boolean是ECMAS中使用最多的一种类型，该类型只有两个字面值：true和false。
这啷个值与数字值不是一回事。

Boolean类型的字面值true和false是区分大小写的。

```
var message="hello world";
var messageAsBoolean = Boolean(message);
```

# Number类型
最基本的数值字面格式是十进制整数，十进制整数可以如下面这样直接在代码中输入
```
var intNum=55 //整数
```

除了十进制，还可以通过八进制，十六进制。八进制第一位必须是0
```
var octalNum= 070;
var octalNum2=079
```

十六进制包括从0~9及A~F。其中字母部分部分大小写

`var hexNum1= 0xA;`
`var hexNum2= 0x1f;`

浮点数，数值中必须包含一个小数点，并且小数点后面必须至少以为数字。

`var floatNum1= 1.1;`
`var floatnum2= 0.1;`

对于极大或者极小的数字，可以用e表示（科学计数法）等于e前面的数值乘以10的指数次幂。
`var floatNum=3.125e7//31250000`

# NaN
NaN即非数值（Not a Number）是一个特殊的数值，用于表示一个本来要返回数值的操作数未返回数值的情况。

NaN有两个特点：
1.任何涉及NaN的操作都会返回NaN
2.NaN和任何值都不相等，包括NaN本身

针对这个问题ECMA制定了 `isNaN()`函数。这个函数接受一个参数，该参数可以是任何类型，而函数会帮我们确定这个参数是不是数值。

# 数值转换
有3个函数可以把非数值转化为数值：`Number()`、`parseInt()`和`parseFloat()`。第一个函数，即转型函数Number()可以用于任何数据类型，而另两个函数则专门用于吧字符串转换成为数值。

## Number()函数转换规则如下。
- 如果是Boolean值，true和false将分别被转换为1和0.
- 如果是数值，只是简单的传入和返回。
- 如果是null值，返回0。
- 如果是underfined，返回NaN
- 如果是字符，数字转换为数字，空值为0，除此之外，则转换为NaN
- 如果是对象，则调用调用对象的 valueOf()方法。如果转换为NaN，怎调用对象toString()方法，然后再次依照前面的规则转换返回的字符串值。

## parseInt()与parseFloat()
`parseInt(A,B)`
其中A用于填写转化的对象，B默认为10，用于填写A对象目前是多少进制的。


# String类型  P32
String 类型用于表示由零或多个16位Unicode字符组成的字符序列，即字符串。字符串可以由双引号或者单引号表示。

下面两种都是有效的：
	`var firstName="Nicholas";`
	`var lastName='Zakas'`

双引号开头必须以双引号结尾，单引号同理。

## 字符字面量
String数据类型中包含了一些特殊的字符字面量，叫转义序列，用于表示非打印字符。
其中包括<br>
`\n`	转行<br>
`\t`	制表<br>
`\b`   空格<br>
`\r`	回车<br>
`\f`	进纸<br>
`\\`	斜杠<br>
`\'`		<br>
`\"`		<br>
\xnn	十六机制，例如\x41表示A
\unnnn	十六进制Unicode字符。

`var text="This is the letter sigma: \u03a3."`
在text中有28个字符，其中6个字符场的转义序列表示1个字符。
`alert（text.length);//输出为28.`

## 字符串的特点
ECMAS中的字符串是不可变的，也就是说，字符串一旦创建，他们的值就不能改变。要改变某个变量保存的字符串，需要先销毁原来的字符串，然后再创立一个新的值来填充该变量。
例如：
`var lang="Java";`
`lang=lang+"Script";`

//目前负责的销毁+重构的问题已经解决了。所以目前没有这一系列的问题了

## 转换为字符串
要把一个值转换为一个字符串有两种方法。
第一种是机会每个值都有的`toString()`方法。

`var age=11;`
`var ageAsString=age.toString();//字符串为”11“`
`var found= true;`
`var foundAsString= found.toString();//字符串为”true“`


除了null和undefined值没有这个方法。

一般情况toString()函数不需要传入参数，特殊情况下可以传入一个数值表示二进制、八进制、十进制、十六进制。

在不确定要转换的值是不是null或undefined情况下，还可以使用转型函数String()，这个函数能够将任何值转换为字符串。

- 如果值有toString()的方法，则调用该方法
- 如果值是null，返回"null"
- 如果值是undefined，则返回"undefined"。

# Object类型	 P35
对象其实就是一组数据和功能的集合。对象可以通过执行new操作符后要创建的对象类型的名称来创建。而创建Object类型的实例并为其添加属性和方法，可以创建自定义对象，
`var o = new Object()；`


Object的每个实例都具有一列属性和方法
- `constructor`: 保存着用于创建当前对象的函数。
- `hasOwnProperty(propertyName)`:用于检查传入的对象是否是另一个对象的原型。
- 
...


# 操作符 
>P36

## 一元操作符
只能操作一个值的操作符叫做一元操作符。是ECMAS最简单的操作符。

1. 递增和递减操作符

`var age= 29;`
`++age;`
等同于
`age=age+1`<br>
在这个例子中，前置递增操作符把age的值变成了30（29+1）。

执行前置递增和递减操作时，变量的值都是在语句被求职以前改变的。

前置递增和递减操作符与后置递增递减操作符的区别：
前置在运算中自动进行了相关操作，后置在运算中不表现，但是在运算后表现。
例子：
```
var num1=2;
var num2=20;
var num3=--num1 + num2;//等于21
var num4= num1 + num2;//等于21
```

```
var num1=2;
var num2=20;
var num3= num1-- + num2;//等于22
var num4= num1 + num2;//等于21
```
## 递增递减的规则如下：
- 在应用于一个包含有效数字字符的字符串时，现将其转换为数值，在计算。
- 当字符串不包含数字时，则设为NaN
- 当布尔值为false时，先转换为0再执行
- 当布尔值为true时，先转换为1在执行
- 应用于对象时，先调用valueOf()方法已取得一个可供操作的值。然后处理上述规则。


## 一元加减操作符
会想`Number()`转型函数一样对这个值执行转换。

# 布尔操作符 
>P44

布尔操作符一共3个：NOT,AND,OR 

1. NOT
逻辑非操作符由一个叹号！表示，可以应用于ECMAS中的任何值。无论这个值是什么数据类型。这个操作符都会返回一个布尔值。
- 对象=false
- 空字符串=true
- 非空字符串=false
- 0=true
- 非0 =false
- null = true
- NaN= true
- undefined = true

2. AND
逻辑与操作符由两个和号组成(`&&`)

逻辑与属于短路操作，即如果第一个操作符能够决定结果，那么就不会再对第二个操作符求值。也就是说第一个操作符为false，将不计算第二个操作符。

不能在逻辑与操作中使用未定义的值。


3. OR
逻辑与操作符由两个竖线符号组成||

也属于短路操作，如果第一个操作符为true，将不会计算第二个操作符。

---

# 乘性操作符 
>P47

如果参与乘法计算的额某个操作值不是数值，后台会先使用`Numer()`转型函数并将其转换为数值。空值将被当做0，布尔值true将会被当做1。

## 乘法
乘法由`*`来到表示

## 除法
除法将用`/`来表示

## 求余数
求余由一个百分号`%`来表示

---

# 加性操作符 
>P48	<br>

加法与减法

如果两个操作有字符串，则拼接在一起。
```
var result1= 5+5;
alert(result1);//10
var result2= 5+"5";
alert(result2);//"55"
```
ECMAS 最容易犯的错误之一：
```
var num1 = 5;
var num2 =10;
var message1 = "The sum of 5 and 10 is "+num1+num2;
alert(message1);//"The sum of 5 and 10 is 510"
var message2 = "The sum of 5 and 10 is "+(num1+num2);
alert(message2);//"The sum of 5 and 10 is 15"
```

如果是减法，其中null将会转换为0，含数值的字符串将会转换为数值，不含数值的字符串将会成为NaN
```
var result5 = 5- "2";//3
var result6 = 5- null;//5
```

---

# 关系操作符 
>P50

`<`,`>`,`<=`,`>=`
规则：
- 如果两个都是数值，执行比较
- 如果都是字符串，比较字符串编码值
- 如果一个是字符串一个是数值，则将字符串值转换为数值比较。
- 如果是对象，则调用`valueOf()`方法，如果对象没有`valueOf()`,则调用`toString()`方法。
- 如果有布尔值，则转换为数字比较。

`var result= "Brick"<"alphabet"; //true`<br/>
因为B的字符为66，a的字符编码为97
但是都转换为小写后

`var result ="Brick".toLowerCase()<"alphabet".toLowerCase();//false`

`var result="23"<"3";//true`<br/>
因为2的字符编码小于3的字符编码

`var result= "23"<3;//false`<br/>
此时23被转化为了数值

`var result="a"<3;//false`<br/>
因为a转化成了NaN。

任何数值和NaN比较都是false

# 相等操作符 
>P51



















