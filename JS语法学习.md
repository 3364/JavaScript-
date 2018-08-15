# JavaScrip高级程序设计(第三版)
====
# 第一章 JavaScript简介
# 什么是JavaScript

JS 是一种基于对象和事件驱动的客户端脚本语言，最初设计是为了检验HTML表单输入的正确性，起源于Netscape公司的LiveScript语言。

# JS的发展历史
让用户填写表单，点了提交按钮。最终服务器返回了一个信息。
Netscape开发了一种语言用于验证。

交互能力。
能够处理复杂的交互

完整JS根据
ECMA+DOM+BOM组成

# 第三章 基本概念
# JS基本语法
```
<script type="text/javascript">
	
</script>
```
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

确定两个变量是否相等是编程中的一个非常重要的操作。
在比较字符串，数值和布尔值的相等性时，问题还比较简单。但在涉及到对象的比较时，问题就变得复杂了。
ECMAS的解决方案就是提供两组操作符：*相等*和*不相等*—--—先转换再比较，全等和不全等----仅比较而不转换。

## 相等和不相等
ECMAS中的相等操作符由两个等号`(==)`表示，如果两个操作数相等，则返回true。
不相等操作符由感叹号后跟等于号`(!=)`表现，如果两个操作数不相等，则返回true。

在转换不同的数据类型时，相等和不相等操作符遵循下列基本规则：
- 如果一个操作符是布尔值，则比较相等性之前先将其转换为数值——false转换为0，而true转换为1；
- 如果一个操作数是字符串，另一个操作数是数值，在比较相等性之前先将字符串转换为数值；
- 如果是个操作数是对象，另一个操作数不是，则调用valueOf()方法，用得到的基本类型值按照前面的规则进行比较

- null和underfined是相等的
- 要比较相等性之前，不能将null和undefined转换成其他任何值。
- 如果一个操作数是NaN，则相等操作符返回false，而不相等操作符返回true。
	即使两个操作数都是NaN，相等操作符也返回false;因为按照规则，NaN不等于NaN。
- 如果两个操作数都是对象，则比较它们是不是同一个对象。如果两个操作数都指向同一个对象，则相等操作符返回true；否则，返回false。

## 全等和不全等
>P52 <br>
全等操作符由3个等于号`===`表示，它只在两个操作符未经转换就相等的情况下返回true：
` var result1=("55"==55);//true,因为转换后相等`
` var result2=("55"===55);//false,因为数据类型不相等`

不全等操作符由一个叹号后跟两个等于号`(!==)`表示
` var result1=("55"!=55);//false,因为转换后相等`
` var result2=("55"!==55);//true,因为数据类型不相等`

## 条件操作符
>p53 <br>

条件操作符算ECMAS中最灵活的一种操作符
`variable=boolean_expression?true_value:false_value;`
这行代码的含义就是基于对`boolean_expression`求值的结果，决定给变量`variable`赋什么值。如果求值结果为true，则为变量`variable`赋`true_value`值；

`var max=(num1 >num2)?num1:num2;`

在这个例子中，如果num1大于num2，则将num1的值赋给max；如果num1小于或等于num2，则num2的值赋给max。

## 赋值操作值
>p53 <br>

简单的赋值操作符由等于号`=`表示，其作用就是把右侧的值赋给左侧的变量：
` var num = 10;`

如果等于号前面再添加乘性操作符、加性操作符或位操作符，就可以完全复合赋值操作。这种符合赋值操作相当于如下的简写：

`var num = 10;`
`num = num + 10;`
`num +=10;`

## 逗号操作符
>p54 <br>
使用逗号操作符可以在一句语句中执行多个操作，如下面：
` var num1=1,num2=2,num3=3;`

逗号操作符多用于声明多个变量；但除此之外，逗号操作还可以用于赋值。
`var num=(5,1,4,8,0);//num的值为0`
由于0是表达式中的最后一项，因此num的值就是0.

这种赋值的方式比较少见

# 语句
>p54 <br>

## if语句
`if(condition) {statement1} else {statement2}`

例如：
```
if(i>25){
	alert("Greater than 25.")
};
else
{
	alert("Less than or equal to 25.");
}
```

## do-while语句

do-while语句是一种后测试循环语句，即只有在循环体重的代码执行之后，才会测试出口条件。换句话说，在对条件表达式求值之前，循环体内的代码至少会被执行一次。
```
语法：
	do{
		statement
}	while(expression);
```
```
var i=0;
do{
	i+=2;
}while(i<10);
alert(i);
```

## while语句
while语句属于前测试循环语句，也就是循环体内的代码有可能永远不会被执行。

`while(expression){statement};`
示例
```
var i=0;
while(i<10){
	i+=2;
}
```

## for语句
for语句也是一种前测试循环语句，但它具有执行循环之前初始化变量和定义循环后要执行的代码的能力。
`for(initialization;expression;post-loop-expression)statement`
例子
`var count=10;`
`for(var i=0; i<count;i++){`
`	alert(i);`
`}`

这个for循环语句与下面的while语句的功能相同：

`var count=10;`
`var i=0;`
`while(i<count){`
`	alert(i);`
`	i++;`
`}`

使用while循环做不到的，使用for循环同样也做不得。也就是说，for循环只是把循环有关的代码集中在了一个位置。
有必要指出的是，在for循环的变量初始化表达式中，也可以不适用var关键字。
```
var count=10;
var i'
for (i=0;i<count;i++){
	alert(i);
}
```

循环外部可以访问到循环内部的i

for循环初始化的状态是一个无限循环
for(;;){
	doSomething();
}

for语句存在极大的灵活性，也是ECMAS中最常用的一个语句

## for-in语句
>P57 <br>
for-in语句是一种精准的迭代语句，可以用来枚举对象的属性。
`for (property in expression) statement`
下面是一个示例：

```
for （var propName in window){
	document.write(propName);
}
```
在这个例子中，我们使用for-in 循环来显示BOM中window对象的所有属性。
每次执行循环时，都会将window对象中存在的一个属性名复制给变量propName。
这个过程会一直持续到对象中的所有属性都被枚举一遍为止。
与for语句类似，这里控制语句中的var操作符也不是必需的。

## label语句
使用label语句可以在代码中添加标签，以便将来使用。
label语句的语法：
`label:statement`

示例：
```
start:for(var i=0; i<count; i++){
	alert(i);
}
```
这里用start标签定可以在将来由break或continue语句中引用。加标签的语句一般都与for语句等循环语句配合使用

## break和continue语句

break和continue语句用于在循环中精确控制代码的执行。
break语句会立即退出循环，强制执行循环后面的语句。
continue语句虽然也是立即退出循环，但退出循环后会从循环的顶部继续执行。

```
var num=0;

for (var i=1;i<10;i++){
	if(i%5==0){
		break;
	}
	num++;
}
alert(num);//4
```
在这个例子中，i由1递增至10。在循环体内，有一个if语句检查i的值是否可以被5整除。如果是，则执行break语句退出循环。
另一方面，变量num从0开始，用于记录循环的次数。
在执行break语句之后，要执行下一行代码是alert函数，结果显示4.也就是说，在变量i等于5时，循环总共执行了4次；
因为break语句的执行，导致了循环在num再次递增之前就退出了。
如果这里将break换成continue的话，就是另外一个情况：

```
var num=0;
for (var i=1;i<10;i++){
	if(i%5==0){
		continue;
	}
	num++;
}
alert(num);//8
```
这里显示为8，说明执行了8次循环。当i等于5时，循环会在num再次递增之前退出。但是会接下来执行下一次循环，即i的值等于6的循环。于是循环继续，直到i等于10时自然介绍。而num的最终值之所以为8是因为continue语句导致少了一次。

break与continue的语句都可以与label语句联合使用，从而返回代码中特定的位置。这种联合使用的情况多发生在循环嵌套中，例如：
```
var num=0;

outermost:
for(var i=0;i<10;i++){
	for(var j=0;j<10;j++){
		if(i==5 && j==5){
			break outermost;
		}
		num++;
	}
}
alert(num);//55
```
如果每个循环正常执行10次，则num++语句会正常执行100次。
内部循环break语句带了一个参数，**添加这个标签的结果将导致break语句不仅会退出内部的for循环，也会退出外部的for循环。**为此，当i和j都等于5时，num的值正好是55.

```
var num=0;

outermost:
for(var i=0;i<10;i++){
	for(var j=0;j<10;j++){
		if(i==5 && j==5){
			continue outermost;
		}
		num++;
	}
}
alert(num);//95
```
**continue语句会强制继续执行，退出内部循环，但是执行外部循环。**也就是失去了当j是5后面的5次。


## with语句
>P60 <br>
with语句的作用是将代码段额作用域设置在一个特定的对象中。with语句的语法如下：
`with(expression)statement;`

定义with语句的目的主要是为了简化多次编写同一个对象的工作。
```
var qs=location.search.substring(1);
var hostName =location.hostname;
var url=location.href;
```

上面几行代码都包含了location的对象，如果使用with语句的话可以改写成：
```
with(location){
	var qs =search.substring(1);
	var hostName=hostname;
	var url=href;
}
```
使用with语句关联了location对象。这意味着在with语句的代码快内部，每个变量首先被认为是一个局部变量。
大量使用with会导致性能下降，也会给调试带来麻烦。
**不建议使用with**

## switch语句
>P60 <br>
switch语句与if语句的关系最为密切，而且也是在其他语言中普遍使用的一种流控制语句。
```
switch(expression){
	case value:statement
		break;
	case value:statement
		break;
	case value:statement
		break;
	default:statement
}

```
switch语句中的每一种情形的含义是：如果表达式等于这个值(value)，则执行后面的语句（statement）。而break的关键字会导致代码执行留跳出该语句。如果省略break关键字，会导致执行完当前case后，继续执行下一个case。最后的default关键字用于子啊表达式不匹配前面任何一种情形的时候，执行机动代码。

这是为了让开发不会写类似
```
if(i==25){
	alert("25");
} else if(i==35){
	alert("35");
} else if(i==45){
	alert("45");
} else {
	alert("Other");
}
```

而是写出等价的switch语句：
```
switch(i){
	case 25:
	alert("25");
	break;
	case 35:
	alert("35");
	break;
	case 45:
	alert("45");
	break;
	default:
	alert("Other");
}
```
**switch 语句的比较采用的是全等操作符，因此不会发生类型转移。**

## 函数 
>P62 <br>
函数是核心的概念，通过函数可以封装任意多条语句，而且可以在任何地方，任何时候调用执行。ECMAS中的函数使用function关键字来声明，后跟一组参数以及函数体。
基本语法如下所示：

```
function functionName(arg,arg1,...,argN){
	statements
}
```
实例：
```
funciton sayHi(name,message){
	alert("Hello"+ name +","+message);
}
```
这个函数可以通过函数名来调用，后面还加上了一堆圆括号和参数。调用sayHi()函数的代码如下所示：
`sayHi("Nicolas","how are you today?");`

任何函数在任何时候都可以通过return语句后跟着返回值来实现返回。
`function sum(num1,num2){
	return num1+num2;
}
`
这个sum()翻书的作用是将两个值相加。除了return语句外没有任何声明表示该函数会返回一个值。
调用该函数如下
`var result=sum(5,10);`

**当执行完return语句之后停止并立即退出，也就是位于return后面的任何代码都将永远不会执行**

return语句也可以不带任何返回值。但是这样的情况下函数将会返回undefined。

**推荐的做法是让函数始终有一个返回值，要么永远都不要返回值。否则如果函数有时候返回，有时候不返还，会给调试代码很不方便**

## 理解参数 
>P65 <br>
ECMAS中命名参数只提供便利，但不是必须。对于传入的多个元素会以arguments对象来访问这个参数组，从而获取传递给函数的每一个参数。

另外，arguments对象可以与命名参数一起使用。
比如:
```
funciton doAdd(num1,num2){
	if(arguments.length==1){
	alert(num1+10);
}
	if(arguments.length==2){
	alert(argument[0]+num2);
}
}
```
关于arguments的行为，还有一个点，他的值永远对应命名参数保持同步。
命名参数不会改变arguments中对应的值。


## 没有重载
>P66 <br>

如果在ECMAS中定义了两个名字的函数，则名字只属于后面定义的函数。

---

# 第四章 变量、作用域和内存问题
>P68 <br>

### 本章内容
- 理解基本类型和引用类型的值
- 理解执行环境
- 理解垃圾收集

# 4.1 基本类型和引用类型的值

ECMAS变量包含两种不同数据类型的值：**基本类型值**和**引用类型值**
**基本类型值**指的是简单的数据段
**引用类型值**指那些可能有多个值构成的对象

# 4.1.1 动态的属性
定义基本类型值和引用类型值的方法是类似的:创建一个变量并未该变量赋值。但是当这个值保存到变量中以后，对不同类型可以值得的操作则大相径庭。

```
var person=new Object();
person.name="Nicolas";
alert(person.name);//"Nicolas"
```

以上代码创建了一个对象并将其保存在了变量person中。然后我们为该对象添加了一个名为name的属性，并将“Nicolas”赋给了这个属性。接着用alert()函数访问了这个新属性。

我们不能给基本类型的值添加属性
```
var name="Nicolas";
name.age=27;
alert(name.age);//undefined
```
在这个例子中，我们为字符串name定义了一个名为age的属性，并为该属性赋值27.但是在下一行访问时，发现该属性不见了。这说明只能给引用类型动态地添加属性。


## 4.1.2 复制变量值

从一个变量向另一个变量复制基本类型值和引用类型值时，也存在不同。
如果从一个变量向另一个变量复制基本类型的值，会在变量对象上创建一个新值，然后把该值复制到信的变量分配的位置上。这两个变量可以参与任何操作，但是不互相影响。

但是当一个变量向另一个变量复制引用类型的值时，同样也会将存储在变量对象中的值复制一份放到为新变量分配的空间中。
不同的是，这个值的副本实际上是一个指针，而这个指针针对存储在堆中的一个对象。
**两个变量实际上将引用同一个对象。因此改变其中一个变量，另一个也会受到影响**

```
var obj1=new Object();
var obj2=obj1;
obj1.name="Nicolas";
alert(obj2.name);//"Nicolas"
```

## 4.1.3 传递参数
EMCAS所有的函数的参数都是按值传递的。也就是说，把函数外部的值复制给函数内部的参数，就和吧值从给一个比那辆复制到另一个变量一样。

在向参数传递基本类型的值时，被传递的值会被复制给一个局部变量。在向参数传递引用类型的值时，会把这个值在内存中的地址复制给一个局部变量，因此这个局部变量的变化会反应在函数的外部。
例子：
```
function addTen(num){
	num+=10;
	return num;
}
var count=20;
var result=addTen(count);
alert(count);//20,没有变化
alert(result);//30
```










