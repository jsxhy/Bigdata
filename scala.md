## 第1章 Scala入门

### **1.1 概述**

#### **1.1.1 为什么学习 Scala**

1. Spark—新一代内存级大数据计算框架，是大数据的重要内容。
2. Spark就是使用Scala编写的。因此为了更好的学习Spark, 需要掌握Scala这门语言。
3. Spark的兴起，带动Scala语言的发展！

#### **1.1.2 Scala 发展历史**

联邦理工学院的马丁·奥德斯基（Martin Odersky）于2001年开始设计Scala。

马丁·奥德斯基是编译器及编程的狂热爱好者，长时间的编程之后，希望发明一种

语言，能够让写程序这样的基础工作变得高效，简单。所以当接触到JAVA语言后，对

JAVA这门便携式，运行在网络，且存在垃圾回收的语言产生了极大的兴趣，所以决定

将函数式编程语言的特点融合到JAVA中，由此发明了两种语言（Pizza & Scala）。

Pizza和Scala极大地推动了Java编程语言的发展。

- JDK5.0 的**泛8型、增强for循 环、自动类型转换**等，都是从Pizza引入的新特性。
-  JDK8.0 的**类型推断、Lambda表达式**就是从Scala引入的特性。

JDK5.0和JDK8.0的编辑器就是马丁·奥德斯基写的，因此马丁·奥德斯基一个人的
战斗力抵得上一个Java开发团队。

#### **1.1.3 Scala 和 Java 关系**

![Scala和Java及JVM关系图](./img/scala%E5%92%8CJava%E5%8F%8AJVM%E5%85%B3%E7%B3%BB%E5%9B%BE.png)

#### **1.1.4 Scala 语言特点**

cala是一门以Java虚拟机（JVM）为运行环境并将面向对象和函数式编程的最佳特性结合在一起的

静态类型编程语言（静态语言需要提前编译的如：Java、c、c++等，动态语言如：js）。

1. Scala是一门多范式的编程语言，Scala支持面向对象和函数式编程。（多范式，就是多种编程方
法的意思。有面向过程、面向对象、泛型、函数式四种程序设计方法。）

2. Scala源代码（.scala）会被编译成Java字节码（.class），然后运行于JVM之上，并可以调用现有
的Java类库，实现两种语言的无缝对接。

3. Scala单作为一门语言来看，非常的简洁高效。

4. Scala在设计时，马丁·奥德斯基是参考了Java的设计思想，可以说Scala是源于Java，同时马丁·奥
德斯基也加入了自己的思想，将函数式编程语言的特点融合到JAVA中, 因此，对于学习过Java的同学，
只要在学习Scala的过程中，搞清楚Scala和Java相同点和不同点，就可以快速的掌握Scala这门语言。

#### **1.2.1 class和object说明**

![class和object说明](./img/class%E5%92%8Cobject%E8%AF%B4%E6%98%8E1.png)

![class和object说明](./img/class%E5%92%8Cobject%E8%AF%B4%E6%98%8E2.png)

---

## 第 2 章 变量和数据类型

### 2.1 注释

Scala 注释使用和 Java 完全一样。

注释是一个程序员必须要具有的良好编程习惯。将自己的思想通过注释先整理出来，再
用代码去体现。

- 基本语法
1. 单行注释：`//`
2. 多行注释：`/* */`
3. 文档注释：`/** */`

- 代码规范
1. 使用一次 tab 操作，实现缩进，默认整体向右边移动，用 shift+tab 整体向左移
2. 或者使用 ctrl + alt + L 来进行格式化
3. 运算符两边习惯性各加一个空格。比如：2 + 4 * 5。
4. 一行最长不超过 80 个字符，超过的请使用换行展示，尽量保持格式优雅

### 2.2 变量和常量（重点）

常量：在程序执行的过程中，其值不会被改变的变量

- 回顾：Java 变量和常量语法

变量类型 变量名称 = 初始值 int a = 10

final 常量类型 常量名称 = 初始值 final int b = 20
- 基本语法

var 变量名 [: 变量类型] = 初始值 var i:Int = 10

val 常量名 [: 常量类型] = 初始值 val j:Int = 20

注意：能用常量的地方不用变量

- 案例实操
1. 声明变量时，类型可以省略，编译器自动推导，即类型推导
2. 类型确定后，就不能修改，说明 Scala 是**强数据类型语言**。
3. 变量声明时，必须要有**初始值**
4. 在声明/定义一个变量时，可以使用 `var` 或者 `val` 来修饰，**var 修饰的变量可改变，**
**val 修饰的变量不可改。**
5. **var 修饰的对象引用可以改变**，**val 修饰的对象则不可改变**，但对象的状态（值）
却是可以改变的。（比如：自定义对象、数组、集合等等）

### 2.3 标识符的命名规范
Scala 对各种变量、方法、函数等命名时使用的字符序列称为标识符。即：凡是自己可
以起名字的地方都叫标识符。
- 命名规则
Scala 中的标识符声明，基本和 Java 是一致的，但是细节上会有所变化，有以下三种规
则：
1. 以字母或者下划线开头，后接字母、数字、下划线

2. 以操作符开头，且只包含操作符（+ - * / # !等）
3. 用反引号\`....\`包括的任意字符串，即使是 Scala 关键字（39 个）也可以
- package, import, class, object, trait, extends, with, type, for
- private, protected, abstract, sealed, final, implicit, lazy, override
- try, catch, finally, throw 
- if, else, match, case, do, while, for, return, yield
- def, val, var 
- this, super
- new
- true, false, null


### 2.4 字符串输出

- 基本语法
1. 字符串，通过+号连接
2. printf 用法：字符串，通过`%`传值。
3. 字符串模板（插值字符串）：通过`$`获取变量值,如果需要对变量进行运算，那么可以加`${}`
4. 多行字符串，在 Scala中，利用三个双引号包围多行字符串就可以实现。
输入的内容，带有空格、\t 之类，导致每一行的开始位置不能整洁对齐。
应用 scala 的 stripMargin 方法，在 scala 中 stripMargin 默认
是“|”作为连接符，//在多行换行的行头前面加一个“|”符号即可

### 2.5 键盘输入
在编程中，需要接收用户输入的数据，就可以使用键盘输入语句来获取。
- 基本语法

`StdIn.readLine()、StdIn.readShort()、StdIn.readDouble()`

### 2.6 数据类型（重点）

![](./img/%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B1.png)

### 2.7 整数类型（Byte、Short、Int、Long）

- 整型分类

|数据类型|描述|
|:---|:---|
|Byte [1]|8 位有符号补码整数。数值区间为 -128 到 127|
|Short [2]|16 位有符号补码整数。数值区间为 -32768 到 32767|
|Int [4]|32 位有符号补码整数。数值区间为 -2147483648 到 2147483647|
|Long [8]|64 位有符号补码整数。数值区间为 -9223372036854775808 到9223372036854775807 = 2 的(64-1)次方-1|

1. Scala 各整数类型有固定的表示范围和字段长度，不受具体操作的影响，以保证
Scala 程序的可移植性。
2. Scala 的整型，默认为 Int 型，声明 Long 型，须后加`l`或`L`

3. Scala 程序中变量常声明为 Int 型，除非不足以表示大数，才使用 Long

### 2.8 浮点类型（Float、Double）

- 浮点型分类

|数据类型|描述|
|:---|:---|
|Float [4]|32 位, IEEE 754 标准的单精度浮点数|
|Double [8]|64 位 IEEE 754 标准的双精度浮点数|

Scala 的浮点型常量默认为 Double 型，声明 Float 型常量，须后加`f`或`F`

### 2.9 字符类型（Char）

- 基本说明

1. 字符常量是用单引号 ' ' 括起来的单个字符。
2. \t ：一个制表位，实现对齐的功能
3. \n ：换行符
4. `\\` ：表示\
4. \" ：表示"

### 2.10 布尔类型：Boolean
- 基本说明

1. 布尔类型也叫 Boolean 类型，Booolean 类型数据只允许取值 true 和 false
2. boolean 类型占 1 个字节。

### 2.11 Unit 类型、Null 类型和 Nothing 类型（重点）
- 基本说明

|数据类型|描述|
|:---|:---|
|Unit|表示无值，和其他语言中 void 等同。用作不返回任何结果的方法的结果类型。<br/>Unit 只有一个实例值，写成()。|
|Null|null , Null 类型只有一个实例值 null|
|Nothing|Nothing 类型在 Scala 的类层级最低端；它是任何其他类型的子类型。<br/>当一个函数，我们确定没有正常的返回值，可以用 Nothing 来指定返回类型，<br/>这样有一个好处，就是我们可以把返回的值（异常）赋给其它的函数或者变量（兼容性）|

### 2.12 类型转换

#### 2.12.1 数值类型自动转换
当 Scala 程序在进行赋值或者运算时，精度小的类型自动转换为精度大的数值类型，这
个就是自动类型转换（隐式转换）。数据类型按精度（容量）大小排序为：

![数据精度排序](./img/%E6%95%B0%E6%8D%AE%E7%B2%BE%E5%BA%A6%E6%8E%92%E5%BA%8F.png)

- 基本说明

1. 自动提升原则：有多种类型的数据混合运算时，系统首先自动将所有数据转换成
精度大的那种数据类型，然后再进行计算。
2. 把精度大的数值类型赋值给精度小的数值类型时，就会报错，反之就会进行自动
类型转换。
3. (byte，short)和 char 之间不会相互自动转换。
4. byte，short，char 他们三者可以计算，在计算时首先转换为 int 类型。

#### 2.12.2 强制类型转换

- 基本说明

自动类型转换的逆过程，将精度大的数值类型转换为精度小的数值类型。使用时要加上
强制转函数，但可能造成精度降低或溢出，格外要注意。

例如: 
> Java : int num = (int)2.5
>
> Scala : var num : Int = 2.7.toInt

#### 2.12.3 数值类型和 String 类型间转换

- 基本说明
在程序开发中，我们经常需要将基本数值类型转成 String 类型。或者将 String 类型转成
基本数值类型。
1. 基本类型转 String 类型（语法：将基本类型的值+"" 即可）
2. String 类型转基本数值类型（语法：s1.toInt、s1.toFloat、s1.toDouble、s1.toByte、s1.toLong、s1.toShort）

- 注意事项

在将 String 类型转成基本数值类型时，要确保 String 类型能够转成有效的数据，比如我们可以把"123"，转成一个整数，但是不能把"hello"转成一个整数。

例如:

var n5:Int = "12.6".toInt 会出现 NumberFormatException 异常。

---

## 第 3 章 运算符

### 3.1 算术运算符

- 基本语法

|运算符|运算|范例|结果|
|:---|:---|:---|:---|
|+|正号|+3|3
|-|负号|b=4;|-b|-4|
|+|加|5+5|10|
|-|减|6-4|2|
|\*|乘|3\*4|12|
|/|除|5/5|1|
|%|取模(取余)|7%5|2|
|+|字符串相加|“He”+”llo”|“Hello”|

1. 对于除号“/”，它的整数除和小数除是有区别的：整数之间做除法时，只保留整
数部分而舍弃小数部分。
2. 对一个数取模 a%b，和 Java 的取模规则一样。


### 3.2 关系运算符（比较运算符）

- 基本语法

|运算符|运算|范例|结果|
|:---|:---|:---|:---|
|==|相等于|4==3|false|
|!=|不等于|4！=3|true|
|<|小于|4<3|false|
|>|大于|4>3|true|
|<=|小于等于|4<=3|false|
|>=|大于等于|4>=3|true|

**Java 和 Scala 中关于==的区别**

1. **Java：**

- ==比较两个变量本身的值，即两个对象在内存中的首地址；
- equals 比较字符串中所包含的内容是否相同。

2. **scala**

- ==在Scala中，是类中定义的方法，其底层调用时，调用的是此类的equals方法。
- String的equals方法是重写过的，比较的是两个对象的具体的值。
- eq方法比较的是两个对象的地址，其底层调用的是Java中的==比较运算符。

### 3.3 逻辑运算符

基本语法

用于连接多个条件（一般来讲就是关系表达式），最终的结果也是一个 Boolean 值。

假定：变量 A 为 true，B 为 false

|运算符|描述|实例|
|:---|:---|:---|
|&&|逻辑与(A && B)|运算结果为 false|
|\|\||逻辑或(A \|\| B)|运算结果为 true|
|!|逻辑非!(A && B)| 运算结果为 true|

### 3.4 赋值运算符

赋值运算符就是将某个运算后的值，赋给指定的变量。

|运算符|描述|实例|
|:---|:---|:---|
|=|简单的赋值运算符，将一个表达式的值赋给一个左值<br/>C = A + B|将 A + B 表达式结果赋值给 C|
|+=|相加后再赋值<br/>C += A|等于 C = C + A|
|-= |相减后再赋值 <br/>C -= A |等于 C = C - A|
|*=|相乘后再赋值 <br/>C *= A|等于 C = C * A|
|/= |相除后再赋值 <br/>C /= A |等于 C = C / A|
|%= |求余后再赋值<br/> C %= A |等于 C = C % A|
|<<= |左移后赋值<br/>C <<= 2 |等于 C = C << 2|
|>>=|右移后赋值<br/>C >>= 2 |等于 C = C >> 2|
|&= |按位与后赋值<br/>C &= 2|等于 C = C & 2|
|^=|按位异或后赋值<br/>C ^= 2|等于 C = C ^ 2|
|\|= |按位或后赋值<br/>C |= 2|等于 C = C | 2|

注意：Scala 中没有++、--操作符，可以通过+=、-=来实现同样的效果；

### 3.5位运算符

下表中变量 a 为 60，b 为 13。

|运算符| 描述| 实例|
|:---|:---|:---|
|&| 按位与运算符 (a & b)|输出结果 12 ，二进制解释： 0000 1100|
|\| | 按位或运算符 (a \| b) |输出结果 61 ，二进制解释： 0011 1101|
|^|按位异或运算符 (a ^ b)| 输出结果 49 ，二进制解释： 0011 0001|
|~ |按位取反运算符 (~a ) |输出结果 -61 ，二进制解释： 1100 0011，<br/> 在一个有符号二进制数的补码形式。|
|<<|左移动运算符 a << 2| 输出结果 240 ，二进制解释： 0011 0000|
|>> |右移动运算符 a >> 2 |输出结果 15 ，二进制解释： 0000 1111|
|>>>|无符号右移 a >>>2 |输出结果 15, 二进制解释: 0000 1111|

### 3.6 Scala 运算符本质

在 Scala 中其实是没有运算符的，所有运算符都是方法。

1. 当调用对象的方法时，点.可以省略
2. 如果函数参数只有一个，或者没有参数，()可以省略

> 标准的加法运算
> `val i:Int = 1.+(1)`

>  当调用对象的方法时，.可以省略
> `val j:Int = 1 + (1)`

> 如果函数参数只有一个，或者没有参数，()可以省略
> `val k:Int = 1 + 1`

---

## 第4章 流程控制

### 4.1 分支控制 if-else

让程序有选择的的执行，分支控制有三种：单分支、双分支、多分支

#### 4.1.1 单分支

基本语法

> `if (条件表达式) {`
>
> `代码块`
>
> `}`

说明：当条件表达式为`ture`时，就会执行{代码块}的代码。

#### 4.1.2 双分支

基本语法

> `if (条件表达式) {`
>
> `执行代码块 1`
>
> `} else {`
>
> `执行代码块 2`
>
>`}`

#### 4.1.3 多分支

基本语法

> `if (条件表达式 1) {`
>
> `执行代码块 1`
> `}`
>
> `else if (条件表达式 2) {`
>
> `执行代码块 2`
>
> `}`
>
> `……`
>
> `else {`
>
> `执行代码块 n`
>
> `}`

**Scala 中 if else 表达式其实是有返回值的，具体返回值取决于满足条件的代码体的最后一行内容。**

### 4.2 嵌套分支

在一个分支结构中又完整的嵌套了另一个完整的分支结构，里面的分支的结构称为内层。分支外面的分支结构称为外层分支。嵌套分支**建议不要超过3层。**

基本语法

> `if(){`
>
>   `if(){`
>
>    `}else{`
>
>   `}`
>
> `}`

### 4.3 Switch 分支语句

在 Scala 中没有 Switch，而是使用模式匹配来处理

### For 循环控制

Scala 也为 for 循环这一常见的控制结构提供了非常多的特性，这些 for 循环的特性被称为 for 推导式或 for 表达式。

#### 4.4.1 范围数据循环(To)

基本语法

> `for(i <- 1 to 3){`
>
> `代码块`
>
> `}`

**说明**

1. i 表示循环的变量，<- 规定 to
2. i 将会从 1-3 循环，前后闭合

#### 4.4.2 范围数据循环（Until）

> `for(i <- 1 until 3){`
>
> `代码块`
>
> `}`

**说明**

1. 这种方式和前面的区别在于 i 是从 1 到 3-1
2. 即使前闭合后开的范围

#### 4.4.3 循环守卫

> `for(i <- 1 to 3 if i != 2){`
>
> `代码块`
>
> `}`

**说明**

循环守卫，即循环保护式（也称条件判断式，守卫）。保护式为 `true` 则进入循环体内部，为 `false` 则跳过，类似于 `continue`。

#### 4.4.4 循环步长

> `for(i <- 1 until 3 by 2){`
>
> `代码块`
>
> `}`

**说明**

`by`表示步长

#### 4.4.5 嵌套循环

> `for(i <- 1 to 3; j <- 1 to 3) {`
>
>  `代码块`
>
> `}`

**说明**

没有关键字，所以范围后一定要加；来隔断逻辑

#### 4.4.6 引入变量

> `for(i <- 1 to 3; j = 4 - i) {`
>
>  `代码块`
>
> `}`

**说明**

1. for 推导式一行中有多个表达式时，所以要加 ; 来隔断逻辑
2. for 推导式有一个不成文的约定：当 for 推导式仅包含单一表达式时使用圆括号，
3. 当包含多个表达式时，一般每行一个表达式，并用花括号代替圆括号。

#### 4.4.7 循环返回值

> `val res = for(i <- 1 to 10) yield i`

**说明**

将遍历过程中处理的结果返回到一个新 Vector 集合中，使用 yield 关键字。

#### 4.4.8 倒序打印

> `for(i <- 1 to 10 reverse){`
>
> `println(i)`
>
> `}`

**说明**

如果想倒序打印一组数据，可以用 reverse。

### 4.5 While 和 do..While 循环控制

While 和 do..While 的使用和 Java 语言中用法相同。

#### 4.5.1 While 循环控制

> `循环变量初始化`
>
> `while (循环条件) {`
>
>  `循环体(语句)`
>  
> `}`

**说明**

1. 循环条件是返回一个布尔值的表达式
2. while 循环是先判断再执行语句
3. 与 for 语句不同，while 语句没有返回值，即整个 while 语句的结果是 Unit 类型()
4. 因为 while 中没有返回值，所以当要用该语句来计算并返回结果时，就不可避免的使用变量，而变量需要声明在 while 
循环的外部，那么就等同于**循环的内部对外部的变量造成了影响。**
5. 不推荐使用，而是推荐使用 for 循环。

#### 4.5.2 do..while 循环控制

> `do{`
>
> `循环体(语句)`
>
> `循环变量迭代`
> `} while(循环条件)`

说明

1. 循环条件是返回一个布尔值的表达式
2. do..while 循环是先执行，再判断

### 4.6 循环中断

Scala 内置控制结构特地去掉了 `break` 和 `continue`，是为了更好的适应函数式编程，推
荐使用**函数式**的风格解决`break`和`continue`的功能，**而不是一个关键字**。

Scala中使用`breakable``控制结构来实现 break 和 continue 功能。`

**方式一**

采用异常的方式退出循环

> `try {`
>
>    `循环条件`
>
>    **条件判断** `throw new RuntimeException`
>
>`} catch{`
> `case _:Exception =>` 
> `}`

**说明**

`throw new RuntimeException` 抛出一个异常退出循环，然后，对异常进行模式匹配，什么也不做

**方式二**

采用 Scala 自带的函数，退出循环

> `import scala.util.control.Breaks`
>
> `Breaks.breakable(`
>
>   `循环体`
> `Breaks.break()`
>
> `)`

**方式三**

对 break 进行省略

> `import scala.util.control.Breaks._`
>
> `breakable(`
>
>   `循环体`
> `break`
>
> `)`

### 4.7 多重循环

**基本说明**

1. 将一个循环放在另一个循环体内，就形成了嵌套循环。其中，for，while，do…while
均可以作为外层循环和内层循环。【建议一般使用两层，最多不要超过 3 层】
2. 设外层循环次数为 m 次，内层为 n 次，则内层循环体实际上需要执行 m*n 次。

## 第 5 章 函数式编程

**面向对象编程**

解决问题，分解对象，行为，属性，然后通过对象的关系以及行为的调用来解决问题。

对象：用户

行为：登录、连接 JDBC、读取数据库

属性：用户名、密码

Scala 语言是一个完全面向对象编程语言。万物皆对象

对象的本质：**对数据和行为的一个封装**

**函数式编程**

解决问题时，将问题分解成一个一个的步骤，将每个步骤进行封装（函数），通过调用

这些封装好的步骤，解决问题。

例如：请求->用户名、密码->连接 JDBC->读取数据库

Scala 语言是一个完全函数式编程语言。万物皆函数。

函数的本质：**函数可以当做一个值进行传递**

在 Scala 中函数式编程和面向对象编程完美融合在一起了

### 5.1 函数基础

#### 5.1.1 函数基本语法

**基本语法**

> `def 函数名(参数:参数类型):返回值类型 = {`
>     `函数体`
> `}`

#### 5.1.2 函数和方法的区别

**核心概念**

1. 为完成某一功能的程序语句的集合，称为函数。
2. 类中的函数称之方法。
3. Scala 语言可以在任何的语法结构中声明任何的语法
4. 函数没有重载和重写的概念；方法可以进行重载和重写
5. Scala 中函数可以嵌套定义

#### 5.1.3 函数参数

**概念**

1. 可变参数
2. 如果参数列表中存在多个参数，那么可变参数一般放置在最后
3. 参数默认值，一般将有默认值的参数放置在参数列表的后面
4. 带名参数

**可变参数**

> `def 函数名(参数:参数类型*) : 返回值类型 = {函数体}`

**默认值参数**

> `def 函数名(参数:参数类型 = 默认值) : 返回值类型 = {函数体}` 

**带名参数**

> `函数名(参数 = 值)`   调用函数时使用

#### 5.1.4 函数至简原则

**至简原则细节**

1. return 可以省略，Scala 会使用函数体的最后一行代码作为返回值
2. 如果函数体只有一行代码，可以省略花括号
3. 返回值类型如果能够推断出来，那么可以省略（:和返回值类型一起省略）
4. 如果有 return，则不能省略返回值类型，必须指定
5. 如果函数明确声明 unit，那么即使函数体中使用 return 关键字也不起作用
6. Scala 如果期望是无返回值类型，可以省略等号
7. 如果函数无参，但是声明了参数列表，那么调用时，小括号，可加可不加
8. 如果函数没有参数列表，那么小括号可以省略，调用时小括号必须省略
9. 如果不关心名称，只关心逻辑处理，那么函数名（def）可以省略

### 5.2 函数高级

#### 5.2.1 函数高阶

##### 1. 函数可以作为值进行传递

**调用函数把值返回变量**

> `val 变量 = 函数名()`

**在被调用函数后面加 _ 相当于把函数作为一个整体，传递给变量**

> `val 变量 = 函数名 _`

**如果明确变量类型，那么不使用下划线也可以将函数作为整体传递给变量**

> `val 变量:() => 返回值类型 = 函数名`

##### 2. 函数可以作为参数进行传递

> `def 函数名(函数参数:(参数类型) => 返回值类型) :返回值类型 = {函数体} `

可以传递匿名参数

##### 3. 函数可以作为函数返回值返回

> `def f1() = {`
>
> `def f2() = { }`
>
> `f2 _`
>
> `}`
>
> `f1()()`  调用函数

#### 5.2.2 匿名函数

**说明**

没有名字的函数就是匿名函数

> `(参数:参数类型) => {函数体}`

递匿名函数至简原则：

1. 参数的类型可以省略，会根据形参进行自动的推导
2. 类型省略之后，发现只有一个参数，则圆括号可以省略；其他情况：没有参数和参数超过 1 的永远不能省略圆括号。
2. 匿名函数如果只有一行，则大括号也可以省略
3. 如果参数只出现一次，则参数省略且后面参数可以用_代替

#### 5.2.3 函数柯里化&闭包

闭包：如果一个函数，访问到了它的外部（局部）变量的值，那么这个函数和他所处的环境，称为闭包

```
def f1() = { 
    var a:Int = 10
    def f2(b:Int) = {a + b }
f2 _
}

val f = f1()    在调用时，f1 函数执行完毕后，局部变量 a 应该随着栈空间释放掉

print(f(3))      但是在此处，变量a其实并没有释放，而是包含在了f2函数的内部，形成了闭合的效果
```

函数柯里化：把一个参数列表的多个参数，变成**多个参数列表**。

函数柯里化，其实就是将复杂的参数逻辑变得简单化,函数柯里化一定存在闭包

> `def f1(a:Int)(b:Int){ a + b }`
>
> `println(f1(10)(3))`


#### 5.2.4 递归

递归算法
 
1. 方法调用自身
2. 方法必须要有跳出的逻辑
3. 方法调用自身时，传递的参数应该有规律
4. scala 中的递归必须声明函数返回值类型

#### 5.2.5 控制抽象

**值调用：把计算后的值传递过去**

```
def f():Int = {
    println("f....")
    10
}
def foo(a:Int):Unit={
    println(1)
    println(a)
    println(a)
}
foo(f())
```

结果:
```
f....
1
10
10
```

**名调用：把代码传递过去**

```
def f():Int = {
    println("f....")
    10
}
def foo(a: => Int):Unit={
    println(1)
    println(a)
    println(a)
}
foo(f())
```

结果:
```
1
f....
10
f....
10
```

#### 5.2.6 惰性加载

当函数返回值被声明为 lazy 时，函数的执行将被推迟，直到我们首次对此取值，该函数才会执行。这种函数我们称之为惰性函数

注意：lazy 不能修饰 var 类型的变量

```
      lazy val r = sum(3,4)
      def sum(a:Int,b:Int):Int = a + b
      println("-------")
      println(r)
```

结果:
```
-------
7
```

## 第6章 面向对象

### 6.1 包

基本语法

`package 包名`

Scala 包的三大作用（和 Java 一样）

1. 区分相同名字的类
2. 当类很多时，可以很好的管理类
3. 控制访问范围

#### 6.1 包的命名

**命名规则**

只能包含数字、字母、下划线、小圆点.，但不能用数字开头，也不要使用关键字。

**命名规范**

一般是小写字母+小圆点

com.公司名.项目名.业务模块名

#### 6.1.2 包说明（包语句）

**说明**

Scala 有两种包的管理风格，一种方式和 Java 的包管理风格相同，每个源文件一个包（包
名和源文件所在路径不要求必须一致），包名用“.”进行分隔以表示包的层级关系，如
`com.atguigu.scala`。另一种风格，通过嵌套的风格表示层级关系，如下

```
package com{
    package atguigu{
        package scala{

        }
    }
}
```
第二种风格有以下特点：

1. 一个源文件中可以声明多个 package
2. 子包中的类可以直接访问父包中的内容，而无需导包

#### 6.1.3 包对象

在Scala 中可以为每个包定义一个同名的包对象，定义在包对象中的成员，作为其对应包下所有`class`和`object`的共享变量，可以被直接访问。

**定义**

```
package object 包名{
    val f = "xhy"
    def j(){}
}
```

**说明**

1. 若使用 Java 的包管理风格，则包对象一般定义在其对应包下的 package.scala
文件中，包对象名与包名保持一致。
2. 如采用嵌套方式管理包，则包对象可与包定义在同一文件中，但是要保证包对象
与包声明在同一作用域中。

```
package com{

}
package object com{

}
```

#### 6.1.4 导包说明

1. 和 Java 一样，可以在顶部使用 import 导入，在这个文件中的所有类都可以使用。
2. 局部导入：什么时候使用，什么时候导入。在其作用范围内都可以使用
3. 通配符导入：import java.util._
4. 给类起名：import java.util.{ArrayList=>JL}
5. 导入相同包的多个类：import java.util.{HashSet, ArrayList}
6. 屏蔽类：import java.util.{ArrayList =>_,_}
7. 导入包的绝对路径：new _root_.java.util.HashMap

说明

|操作|解释|
|:---|:---|
|import com.atguigu.Fruit|引入 com.atguigu 包下 Fruit（class 和 object）|
|import com.atguigu._ |引入 com.atguigu 下的所有成员|
|import com.atguigu.Fruit._|引入 Fruit(object)的所有成员|
|import com.atguigu.{Fruit,Vegetable}|引入 com.atguigu 下的 Fruit 和 Vegetable|
|import com.atguigu.{Fruit=>Shuiguo}|引入 com.atguigu 包下的 Fruit 并更名为 Shuiguo|
|import com.atguigu.{Fruit=>Shuiguo,_}|引入 com.atguigu 包下的所有成员，并将 Fruit 更名为 Shuiguo|
|import com.atguigu.{Fruit=>_,_}|引入 com.atguigu 包下屏蔽 Fruit 类|
|new _root_.java.util.HashMap|引入的 Java 的绝对路径|

注意

Scala 中的三个默认导入分别是

import java.lang._

import scala._

import scala.Predef._

#### 6.1.5 访问权限

**说明**

在 Java 中，访问权限分为：public，private，protected 和默认。在 Scala 中，你可以通
过类似的修饰符达到同样的效果。但是使用上有区别。

1. Scala 中属性和方法的默认访问权限为 public，但 Scala 中无 public 关键字。
2. private 为私有权限，只在类的内部和伴生对象中可用。
3. protected 为受保护权限，Scala 中受保护权限比 Java 中更严格，同类、子类可以
访问，同包无法访问。
4. private[包名]增加包访问权限，包名下的其他类也可以使用

### 6.2 类和对象

类：可以看成一个模板

对象：表示具体的事物

#### 6.2.1 定义类

基本语法

```
[修饰符] class 类名 {
 类体
}
```

说明

1. Scala 语法中，类并不声明为 public，所有这些类都具有公有可见性（即默认就是public）
2. 一个 Scala 源文件可以包含多个类

#### 6.2.2 属性

属性是类的一个组成部分

**基本语法**

`[修饰符] var|val 属性名称 [：类型] = 属性值`

#### 6.2.3 方法

**基本语法**

```
def 方法名(参数列表) [:返回值类型] = {
    方法体
}
```

#### 6.2.4 创建对象

**基本语法**

`   val | var 对象名 [：类型] = new 类型()`

val 修饰对象，不能改变对象的引用（即：内存地址），可以改变对象属性的值。

var 修饰对象，可以修改对象的引用和修改对象的属性值

自动推导变量类型不能多态，所以多态需要显示声明

#### 6.2.5 构造器

Scala 类的构造器包括：主构造器和辅助构造器

**基本语法**

```
class 类名(形参列表) { // 主构造器
 类体
 def this(形参列表) { // 辅助构造器

 }
 def this(形参列表) { //辅助构造器可以有多个...
 
 }
}
```

**说明**

1. 辅助构造器，函数的名称 this，可以有多个，编译器通过参数的个数及类型来区分。
2. 辅助构造方法不能直接构建对象，必须直接或者间接调用主构造方法。

说明：

1. 辅助构造器，函数的名称 this，可以有多个，编译器通过参数的个数及类型来区分。
2. 辅助构造方法不能直接构建对象，必须直接或者间接调用主构造方法。
3. 构造器调用其他另外的构造器，要求被调用构造器必须提前声明构造器调用其他另外的构造器，要求被调用构造器必须提前声明。

#### 6.2.6 构造器参数

Scala 类的主构造器函数的形参包括三种类型：未用任何修饰、var 修饰、val 修饰

1. 未用任何修饰符修饰，这个参数就是一个局部变量
2. var 修饰参数，作为类的成员属性使用，可以修改
3. val 修饰参数，作为类只读属性使用，不能修改

### 6.3 封装

封装就是把抽象出的数据和对数据的操作封装在一起，数据被保护在内部，程序的其它
部分只有通过被授权的操作（成员方法），才能对数据进行操作。

Scala 中的 public 属性，底层实际为 private，并通过 get 方法（obj.field()）和 set 方法
（obj.field_=(value)）对其进行操作。所以 Scala 并不推荐将属性设为 private，再为其设置

public 的 get 和 set 方法的做法。但由于很多 Java 框架都利用反射调用 getXXX 和 setXXX 方
法，有时候为了和这些框架兼容，也会为 Scala 的属性设置 getXXX 和 setXXX 方法（通过

@BeanProperty 注解实现）。

### 6.4 继承和多态

**基本语法**

`class 子类名 extends 父类名 { 类体 }`

1. 子类继承父类的属性和方法
2. scala 是单继承
3. 继承的调用顺序：父类构造器 -> 子类构造器

**动态绑定**

Scala 中属性和方法都是动态绑定

```
package lx {
  object hello {
    class person{
      val name = "person"
      def hello() = println("hello")

      (s" = ")
    }
    class teacher extends person{
      override val name = "teacher"
      override def hello()= println("hello teacher")
    }
    def main(args: Array[String]): Unit = {
      val te:teacher = new teacher()
      println(te.name)
      te.hello()
      val t1:person = new teacher()
      println(t1.name)
      t1.hello()
    }
  }
}
```

结果:
```
teacher
hello teacher
teacher
hello teacher
```

### 6.5 抽象类

#### 6.5.1 抽象属性和抽象方法

**基本语法**

1. 定义抽象类：`abstract class Person{}`  //通过 abstract 关键字标记抽象类
2. 定义抽象属性：`val|var name:String` //一个属性没有初始化，就是抽象属性
3. 定义抽象方法：`def hello():String` //只声明而没有实现的方法，就是抽象方法

**继承&重写**

1. 如果父类为抽象类，那么子类需要将抽象的属性和方法实现，否则子类也需声明
为抽象类
2. 重写非抽象方法需要用 override 修饰，重写抽象方法则可以不加 override。
3. 子类中调用父类的方法使用 super 关键字
4. 子类对抽象属性进行实现，父类抽象属性可以用 var 修饰；

子类对非抽象属性重写，父类非抽象属性只支持 val 类型，而不支持 var。

因为 var 修饰的为可变变量，子类继承之后就可以直接使用，没有必要重写

#### 6.5.2 匿名子类

**说明**

和 Java 一样，可以通过包含带有定义或重写的代码块的方式创建一个匿名的子类。

```
abstract class Person {
 val name: String
 def hello(): Unit
}
object Test {
 def main(args: Array[String]): Unit = {
 val person = new Person {
 
 override val name: String = "teacher"
 override def hello(): Unit = println("hello teacher")
 
 }
 }
}
```

### 6.6 单例对象（伴生对象）

#### 6.6.1 单例对象语法

Scala语言是**完全面向对象**的语言，所以并**没有**静态的操作（即在Scala中没有静态的概

念）。但是为了能够和Java语言**交互**（因为Java中有静态概念），就产生了一种特殊的对象

来**模拟类对象**，**该对象为单例对象**。若**单例对象名与类名一致**，则称该单例对象这个类的伴

生对象，这个类的所有“静态”内容都可以放置在它的伴生对象中声明。

**基本语法**

```
object 类名{
    
}
```

**说明**

1. 单例对象采用 object 关键字声明
2. 单例对象对应的类称之为伴生类，伴生对象的名称应该和伴生类名一致。
3. 单例对象中的属性和方法都可以通过伴生对象名（类名）直接调用访问。

#### 6.6.2 apply 方法

**说明**

1. 通过伴生对象的 apply 方法，实现不使用 new 方法创建对象。
2. 如果想让主构造器变成私有的，可以在()之前加上 private。
3. apply 方法可以重载。
4. Scala 中 obj(arg)的语句实际是在调用该对象的 apply 方法，即 obj.apply(arg)。用
以统一面向对象编程和函数式编程的风格。
5. 当使用 new 关键字构建对象时，调用的其实是类的构造方法，当直接使用类名构
建对象时，调用的其实时伴生对象的 apply 方法。
6. 注意：也可以创建其它类型对象，并不一定是伴生类对象

```
package lx {
  class person private(sname: String) {
    var name: String = sname
  }
  object person {
    def apply(): person = {
      println("appply空参被调用")
      new person("ss")
    }
    def apply(name: String): person = {
      println("apply有参被调用")
      new person(name)
    }
  }
  object hello {
    def main(args: Array[String]): Unit = {
      val p1 = person("fga")
      println(p1.name)
      val p2 = person()
      println(p2.name)
    }
  }
}
```

### 6.7 特质（Trait）

Scala 语言中，采用特质 trait（特征）来代替接口的概念，也就是说，多个类具有相同
的特质（特征）时，就可以将这个特质（特征）独立出来，采用关键字 trait 声明。

Scala 中的 trait 中即可以有抽象属性和方法，也可以有具体的属性和方法，一个类可
以混入（mixin）多个特质。这种感觉类似于 Java 中的抽象类。

#### 6.7.1 特质声明

**基本语法**

```
trait 特质名{
     主体
}
```

#### 6.7.2 特质基本语法

一个类具有某种特质（特征），就意味着这个类满足了这个特质（特征）的所有要素，
所以在使用时，也采用了 extends 关键字，如果有多个特质或存在父类，那么需要采用 with
关键字连接

基本语法：
```
没有父类：class 类名 extends 特质 1 with 特质 2 with 特质 3 …

有父类：class 类名 extends 父类 with 特质 1 with 特质 2 with 特质 3…
```

**说明**

1. 类和特质的关系：使用继承的关系。
2. 当一个类去继承特质时，第一个连接词是 extends，后面是 with。
3. 如果一个类在同时继承特质和父类时，应当把父类写在 extends 后
4. 特质可以同时拥有抽象方法和具体方法
5. 一个类可以混入（mixin）多个特质
6. 所有的 Java 接口都可以当做 Scala 特质使用
7. 动态混入：可灵活的扩展类的功能
8. 动态混入：创建对象时混入 trait，而无需使类混入该 trait
9. 如果混入的 trait 中有未实现的方法，则需要实现

#### 6.7.3 特质叠加

由于一个类可以混入（mixin）多个 trait，且 trait 中可以有具体的属性和方法，若混入
的特质中具有相同的方法（方法名，参数列表，返回值均相同），必然会出现继承冲突问题。
冲突分为以下两种:

第一种，一个类（Sub）混入的两个 trait（TraitA，TraitB）中具有相同的具体方法，且
两个 trait 之间没有任何关系，解决这类冲突问题，直接在类（Sub）中**重写冲突方法**。

第二种，一个类（Sub）混入的两个 trait（TraitA，TraitB）中具有相同的具体方法，且
两个 trait 继承自相同的 trait（TraitC），及所谓的“钻石问题”，解决这类冲突问题，Scala
采用了特质叠加的策略。

#### 6.7.4 特质叠加执行顺序

**思考**:super.describe()调用的是父 trait 中的方法吗？

当一个类混入多个特质的时候，scala 会对所有的特质及其父特质按照一定的顺序进行
排序，而 super.describe()调用的实际上是排好序后的下一个特质中的 describe()
方法。排序规则如下：

![特质叠加顺序](./img/%E7%89%B9%E8%B4%A8%E5%8F%A0%E5%8A%A0%E9%A1%BA%E5%BA%8F.png)

**结论:**

1. 案例中的 super，不是表示其父特质对象，而是表示上述叠加顺序中的下一个特质，
即，MyClass 中的 super 指代 Color，Color 中的 super 指代 Category，Category 中的 super
指代 Ball。

2. 如果想要调用某个指定的混入特质中的方法，可以增加约束：super[]，例如 super[Category].describe()。

#### 6.7.5 特质自身类型

**说明**

自身类型可实现依赖注入的功能。

```
class User(val name: String, val age: Int)
trait Dao {
 def insert(user: User) = {
 println("insert into database :" + user.name)
 }
}
trait APP {
 _: Dao =>
 def login(user: User): Unit = {
 println("login :" + user.name)
 insert(user)
 }
}
object MyApp extends APP with Dao {
 def main(args: Array[String]): Unit = {
 login(new User("bobo", 11))
 }
}
```

#### 6.7.6 特质和抽象类的区别

1. 优先使用特质。一个类扩展多个特质是很方便的，但却只能扩展一个抽象类。

2. 如果你需要构造函数参数，使用抽象类。因为抽象类可以定义带参数的构造函数，
而特质不行（有无参构造）。

### 6.8 扩展

### 6.8.1 类型检查和转换

**说明**

1. obj.isInstanceOf[T]：判断 obj 是不是 T 类型。
2. obj.asInstanceOf[T]：将 obj 强转成 T 类型。
3. classOf 获取对象的类名

#### 6.8.2 枚举类和应用类

**说明**

枚举类：需要继承 Enumeration

应用类：需要继承 App

#### 6.8.3 Type 定义新类型

**说明**

使用 type 关键字可以定义新的数据数据类型名称，本质上就是类型的一个别名

```
type s = String
var v:S="abc"
def test():S="xyz"
```

## 第 7 章 集合

### 7.1 集合简介

1. Scala 的集合有三大类：序列 Seq、集 Set、映射 Map，所有的集合都扩展自 Iterable
特质。
2. 对于几乎所有的集合类，Scala 都同时提供了可变和不可变的版本，分别位于以下两
个包
```
不可变集合：scala.collection.immutable
可变集合： scala.collection.mutable
```
3. Scala 不可变集合，就是指该集合对象不可修改，每次修改就会返回一个新对象，而
不会对原对象进行修改。类似于 java 中的 String 对象
4. 可变集合，就是这个集合可以直接对原对象进行修改，而不会返回新的对象。类似
于 java 中 StringBuilder 对象

#### 7.1.1 不可变集合继承图

![不可变集合继承图](./img/%E4%B8%8D%E5%8F%AF%E5%8F%98%E9%9B%86%E5%90%88%E7%BB%A7%E6%89%BF%E5%9B%BE.png)

1. Set、Map 是 Java 中也有的集合
2. Seq 是 Java 没有的，我们发现 List 归属到 Seq 了，因此这里的 List 就和 Java 不是同一个
概念了
3. 我们前面的 for 循环有一个 1 to 3，就是 IndexedSeq 下的 Range
4. String 也是属于 IndexedSeq
5. 我们发现经典的数据结构比如 Queue 和 Stack 被归属到 LinearSeq(线性序列)
6. 大家注意 Scala 中的 Map 体系有一个 SortedMap，说明 Scala 的 Map 可以支持排序
<dl><dt>IndexedSeq 和 LinearSeq 的区别：</td>
<dd>IndexedSeq 是通过索引来查找和定位，因此速度快，比如 String 就是一个索引集合，通过索引即可定位</dd>
<dd>LinearSeq 是线型的，即有头尾的概念，这种数据结构一般是通过遍历来查找</dd>
</dl>

#### 7.1.2 可变集合继承图

![可变集合继承图](./img/%E5%8F%AF%E5%8F%98%E9%9B%86%E5%90%88%E7%BB%A7%E6%89%BF%E5%9B%BE.png)

### 7.2 数组

#### 7.2.1 不可变数组

定义:

1. `val arr1 = new Array[Int](10)`

2. 用半生对象的apply方法 `val arr2 :Array[Int] = Array(1,2,3,4,5)`

1. new 是关键字
2. [Int]是指定可以存放的数据类型，如果希望存放任意数据类型，则指定 Any
3. (10)，表示数组的大小，确定后就不可以变化
4. 在定义数组时，直接赋初始值
5. 使用 apply 方法创建数组对象

**修改:**

1. `arr1[下标] = 值`

2. `arr1.update(下标,值)`

**向数组中添加元素:**

```
    //生成一个新的数组，原数组不变
  val newArr1:Array[Int] = arr2.:+(20)

  val newArr2:Array[Int] = arr2.+:(0)

    val newArr3 = arr1 :+ 39

    //:在后面的话是从右往左调用

    //val newArr3 = arr1 +: 15

    val newArr4 = 15 +: arr1

```

#### 7.2.2 可变数组

**定义变长数组**

定义:

`val arr01 = ArrayBuffer[Any](3, 2, 5)`

`var arr1:ArrayBuffer[Int] = new ArrayBuffer[Int]()`

`val arr2 = ArrayBuffer(2,3,4)`

1. [Any]存放任意数据类型
2. (3, 2, 5)初始化好的三个元素
3. ArrayBuffer 需要引入 scala.collection.mutable.ArrayBuffer
4. ArrayBuffer 是有序的集合

**值调用:**

```
 //array必须mkstring，这个不用，因为底层又索引
 
    println(arr1) 
 
    //ArrayBuffer()
```

**数组元素调用**

```
 println(arr2(2))

//通过下标进行访问
```

**元素的修改**

```
//底层同样是update方法

    arr2(0) = 12
```

**元素的添加**

1. 强行使用,不推荐 代码:  `arr1 :+ 200`
2. 最好使用的是英文表示 `arr1.append(1,2,2,2,2,3)`
3. 往前加 `arr1.prepend(0)`
4. 往任意位置添加   `arr1.insert(1,100000000,200000000)`
5. 增加另一个数组的所有元素 `arr2.appendAll( ArrayBuffer(27,47,80) )`

**元素的删除**

1. `val a = arr2.remove(2)`  按索引位置删除
2. 符号的删除方法，按值删除 `arr2 -= 2`


#### 7.2.3 不可变数组与可变数组的转换

**说明**

*不可变数组转可变数组*

定义:`数组.toBuffer`

*可变数组转不可变数组*

定义:`数组.toArray` 

1. `数组.toArray` 返回结果才是一个不可变数组，数组本身没有变化
2. `数组.toBuffer` 返回结果才是一个可变数组，数组本身没有变化

#### 7.2.4 多维数组

**多维数组定义**

定义: `val arr = Array.ofDim[Double](3,4)`

说明: 二维数组中有三个一维数组，每个一维数组中有四个元素

### 7.3 列表 List

有序 的意思并不是排序, 而是指 元素的存入顺序和取出顺序是一致的 .

可重复 的意思是 列表中可以添加重复元素

#### 7.3.1 不可变 List


语法：

1. 通过 小括号 直接初始化.
`val/var 变量名 = List(元素1, 元素2, 元素3…)`
2. 通过 Nil 创建一个空列表.
`val/var 变量名 = Nil`
3. 使用 :: 方法实现.
`val/var 变量名 = 元素1 :: 元素2 :: Nil`

注意: 使用::拼接方式来创建列表，必须在最后添加一个Nil

**特点**

列表的元素、长度都是不可变的。


#### 7.3.2 可变 ListBuffer


**特点**

可变列表指的是列表的元素、长度都是可变的.

**语法**

1. 要使用可变列表, 必须先导包.
`import scala.collection.mutable.ListBuffer`

2. 格式一: 创建空的可变列表.
`val/var 变量名 = ListBuffer[数据类型]()`

3. 格式二: 通过 小括号 直接初始化.
`val/var 变量名 = ListBuffer(元素1，元素2，元素3…)`

小技巧: 可变集合都在 mutable 包中, 不可变集合都在 immutable 包中（默认导入）.

##### 可变列表的常用操作

|格式|功能|
|:---|:---|
|列表名(索引)|根据索引(索引从0开始), 获取列表中的指定元素.|
|列表名(索引) = 值	|修改元素值|
|+=|	往列表中添加单个元素|
|++=	|往列表中追加一个列表|
|-=|删除列表中的某个指定元素|
|–=	|以列表的形式, 删除列表中的多个元素.|
|toList|	将可变列表(ListBuffer)转换为不可变列表(List)|
|toArray	|将可变列表(ListBuffer)转换为数组|

##### 列表的常用操作

|格式|	功能|
|:---|:---|
|isEmpty|	判断列表是否为空|
|++	|拼接两个列表, 返回一个新的列表|
|head|	获取列表的首个元素|
|tail	|获取列表中除首个元素之外, 其他所有的元素|
|reverse|	对列表进行反转, 返回一个新的列表|
|take	|获取列表中的前缀元素(具体个数可以自定义)|
|drop|	获取列表中的后缀元素(具体个数可以自定义)|
|flatten	|对列表进行扁平化操作, 返回一个新的列表|
|zip|	对列表进行拉链操作, 即: 将两个列表合并成一个列表|
|unzip	|对列表进行拉开操作, 即: 将一个列表拆解成两个列表|
|toString	|将列表转换成其对应的默认字符串形式|
|mkString	|将列表转换成其对应的指定字符串形式|
|union|	获取两个列表的并集元素, 并返回一个新的列表|
|intersect	|获取两个列表的交集元素, 并返回一个新的列表|
|diff	|获取两个列表的差集元素, 并返回一个新的列表|

### 7.4 Set 集合

默认情况下，Scala 使用的是不可变集合，如果你想使用可变集合，需要引用
scala.collection.mutable.Set 包

** Set 集合基本操作**

|操作|说明|
|:---|:---|
|set.head|返回set第一个元素|
|set.tail|返回一个集合，包含除了set第一元素之外的其他元素|
|set.isEmpty|在set为空时返回true|

#### 7.4.1 不可变 Set

定义: `val set = Set(1,2,3,4,5)`

#### 7.4.2 可变 mutable.Set

定义: `val set = mutable.Set(1,2,3,4,5,6)`

### 7.5 Map 集合

Scala 中的 Map 和 Java 类似，也是一个散列表，它存储的内容也是键值对（key-value）
映射

**Map 基本操作**

|函数|说明|
|:---|:---|
|keys|返回 Map 所有的键(key)|
|values|返回 Map 所有的值(value)|
|isEmpty|在 Map 为空时返回true|
|get|返回指定 key 的值|
|iterator|创建新的迭代器，并输出 key/value| 
|apply|返回指定键的值，如果不存在返回 Map 的默认方法|
|remove|移除指定 key|


#### 7.5.1 不可变 Map

定义: `val map = Map("a" -> 1,"b" -> 2,"c" -> 3)`

#### 7.5.2 可变 Map

定义: `val map = mutable.Map("a" -> 1,"b" -> 2,"c" -> 3)`

### 7.6 元组

元组也是可以理解为一个容器，可以存放各种相同或不同类型的数据。说的简单点，就
是将多个无关的数据封装为一个整体，称为元组。

**注意：元组中最大只能有 22 个元素。**

声明: `val tuple:(Int,String,Boolean) = (40,"sdfa",true)`

### 7.7 集合常用函数

#### 7.7.1 基本属性和常用操作

|方法|描述|
|:---|:---|
|set + set1|为集合添加新元素，x并创建一个新的集合，除非元素已存在|
|set - 4|移除集合中的元素，并创建一个新的集合|
|contains|如果元素在集合中存在，返回 true，否则返回 false。|
|&|返回两个集合的交集|
|&~|返回两个集合的差集|
|++|合并两个集合|
|-|通过移除传入指定集合的元素创建一个新的不可变集合|
|apply(elem: A)|检测集合中是否包含指定元素|
|count|计算满足指定条件的集合元素个数|
|copyToArray|复制不可变集合元素到数组|
|diff|比较两个集合的差集|
|drop|返回丢弃前n个元素新集合|
|dropRight|返回丢弃最后n个元素新集合|
|dropWhile|从左向右丢弃元素，直到条件p不成立|
|equals|equals 方法可用于任意序列。用于比较系列是否相等。|
|exists|判断不可变集合中指定条件的元素是否存在。|
|filter|输出符合指定条件的所有不可变集合元素。|
|find|查找不可变集合中满足指定条件的第一个元素|
|forall|查找指定条件是否适用于此集合的所有元素|
|init|返回所有元素，除了最后一个|
|intersect|计算两个集合的交集|
|isEmpty|判断集合是否为空|
|iterator|创建一个新的迭代器来迭代元素|
|last|返回最后一个元素|
|map|通过给定的方法将所有元素重新计算|
|max|查找最大元素|
|min|查找最小元素|
|mkString|集合所有元素作为字符串显示,可以设置分隔符|
|subsetOf|如果集合中含有子集返回 true，否则返回false|
|take|返回前 n 个元素|
|takeRight|返回后 n 个元素|
|toArray|将集合转换为数组|
|toString|返回一个字符串，以对象来表示|
|addString|将不可变集合的所有元素添加到字符串缓冲区,并添加分隔符|
|toBuffer|返回缓冲区，包含了不可变集合的所有元素|
|toList|返回 List，包含了不可变集合的所有元素|
|toMap|返回 Map，包含了不可变集合的所有元素|
|toSeq|返回 Seq，包含了不可变集合的所有元素|
|sum|返回不可变集合中所有数字元素之和|
|tail|返回一个不可变集合中除了第一元素之外的其他元素|
|product|返回不可变集合中数字元素的积。|
|size|返回不可变集合元素的数量|
|splitAt|把不可变集合拆分为两个容器，第一个由前 n 个元素组成，第二个由剩下的元素组成|
|foreach|将函数应用到不可变集合的所有元素|
|head|获取不可变集合的第一个元素|


**获取集合长度**

```
println(list.length)
```

**获取集合大小,等同于 length**

```
println(list.size)
```

**循环遍历**

```
list.foreach(println)
```

**迭代器**

```
for (elem <- list.iterator){
  println(elem)
}
```

**生成字符串**

```
println(list.mkString(","))
```

**是否包含**

```
println(list.contains(数值))
```

#### 7.7.2 衍生集合

##### 获取集合的头

```
println(list.head)
```

##### 获取集合的尾 (不是头就是尾)

```
println(list.tail)
```

##### 集合最后一个元素

```
println(list.last)
```

##### 集合初始元素 (不包含最后一个)

```
println(list.init)
```

##### 反转

```
println(list.reverse)
```

##### 取前（后）n 个元素

```
println(list.take(n))
println(list.takeRight(n))
```

##### 去掉前（后）n 个元素

```
println(list.drop(n))
println(list.dropRight(n))
```

##### 并集

```
println(list.union(list1))
```

##### 交集

```
println(list.intersect(list1))
```

##### 差集

```
println(list.diff(list1))
```

##### 拉链   注:如果两个集合的元素个数不相等，那么会将同等数量的数据进行拉链，多余的数据省略不用

```
println(list.zip(list1))
```

##### 滑窗

```
list.sliding(2,5).foreach(println)
```

#### 7.7.3 集合计算简单函数

##### 求和

```
println(list.sum)
```

##### 求乘积

```
println(list.product)
```

##### 最大值

```
println(list.max)
```

##### 最小值

```
println(list.min)
```

##### 排序

1. sorted
对一个集合进行自然排序，通过传递隐式的 Ordering
2. sortBy
对一个属性或多个属性进行排序，通过它的类型。
3. sortWith
基于函数的排序，通过一个 comparator 函数，实现自定义排序的逻辑。


###### 按照元素大小排序

```
println(list.sortBy(x => x))
```

###### 按照元素的绝对值大小排序

```
println(list.sortBy(x => x.abs))
```

###### 按元素大小升序排序

```
println(list.sortWith((x, y) => x < y))
```

###### 按元素大小降序排序

```
println(list.sortWith((x, y) => x > y))
```

#### 7.7.4 集合计算高级函数

##### 过滤

```
println(list.filter(x => x % 2 == 0))
```

##### 转化/映射

```
println(list.map(x => x + 1))
```

##### 扁平化

```
println(list.map(x => x + 1))
```

##### 扁平化+映射 

```
println(wordList.flatMap(x => x.split(" ")))
```

注：flatMap 相当于先进行 map 操作，在进行 flatten操作

##### 分组

```
println(list.groupBy(x => x % 2))
```

##### Reduce方法

Reduce 简化（归约） ：通过指定的逻辑将集合中的数据进行聚合，从而减少数据，最
终获取结果。

```
 val list = List(1,2,3,4)
         // 将数据两两结合，实现运算规则
         //(1-2-3-4)
 val i: Int = list.reduce( (x,y) => x-y )
 println("i = " + i)
        // 从源码的角度，reduce 底层调用的其实就是 reduceLeft
 val i1 = list.reduceLeft((x,y) => x-y)
 // ((4-3)-2-1) = -2
 val i2 = list.reduceRight((x,y) => x-y)
 println(i2)
```

##### Fold 方法 

Fold 折叠：化简的一种特殊情况

```
val list = List(1,2,3,4)
    // fold 方法使用了函数柯里化，存在两个参数列表
    // 第一个参数列表为 ： 零值（初始值）
    // 第二个参数列表为： 简化规则
    // fold 底层其实为 foldLeft
 val i = list.foldLeft(1)((x,y)=>x-y)
 val i1 = list.foldRight(10)((x,y)=>x-y)
 println(i)
 println(i1)
```

### 7.8 队列

Scala 也提供了队列（Queue）的数据结构，队列的特点就是先进先出。进队和出队的方
法分别为 enqueue 和 dequeue。

声明: `val que = new mutable.Queue[String]()`

进队: `que.enqueue("a", "b", "c")`

出队: `println(que.dequeue())`  //删除最后一个元素，并返回该元素

### 7.9 并行集合

Scala 为了充分使用多核 CPU，提供了并行集合（有别于前面的串行集合），用于多核
环境的并行计算。

**串行集合输出当前进程的名字**
```
val result1 = (0 to 100).map{case _ => 
  Thread.currentThread.getName}
println(result1)
```

**并行集合输出当前进程的名字**
```
val result2 = (0 to 100).par.map{case _ => 
  Thread.currentThread.getName}
println(result2)
```

## 第8章 模式匹配

### 8.1 基本语法

模式匹配语法中，采用 `match` 关键字声明，每个分支采用 `case` 关键字进行声明

**例如:**

```
var result = 'b' match {
 case '+' => 1 + 2
 case '-' => 1 - 2
 case '*' => 1 * 2
 case '/' => 1 / 2
 case _ => "illegal"
}
```

**说明**

1. 如果所有 case 都不匹配，那么会执行 case _ 分支，类似于 Java 中 default 语句，
若此时没有 case _ 分支，那么会抛出 MatchError。
2. 每个 case 中，不需要使用 break 语句，自动中断 case。
3. match case 语句可以匹配任何类型，而不只是字面量。
4. => 后面的代码块，直到下一个 case 语句之前的代码是作为一个整体执行，可以
使用{}括起来，也可以不括。

### 8.2 模式守卫

如果想要表达匹配某个范围的数据，就需要在模式匹配中增加条件守卫。

```
def abs(x: Int) = x match {
 case i: Int if i >= 0 => i
 case j: Int if j < 0 => -j
 case _ => "type illegal"
 }
```

### 8.3 模式匹配类型

Scala 中，模式匹配可以匹配所有的字面量，包括字符串，字符，数字，布尔值等等。

需要进行类型判断时，可以使用前文所学的 isInstanceOf[T]和 asInstanceOf[T]，也可使
用模式匹配实现同样的功能。

```
object TestMatchClass {
 def describe(x: Any) = x match {
 case i: Int => "Int"
 case s: String => "String hello"
 case m: List[_] => "List"
 case c: Array[Int] => "Array[Int]"
 case someThing => "something else " + someThing
 }
 def main(args: Array[String]): Unit = {
 //泛型擦除
 println(describe(List(1, 2, 3, 4, 5)))
 //数组例外，可保留泛型
 println(describe(Array(1, 2, 3, 4, 5, 6)))
 println(describe(Array("abc")))
 }
}
```

#### 匹配数组

```
val result = arr match {
 case Array(0) => "0"                     //匹配 Array(0) 这个数组

 case Array(x, y) => x + "," + y            //匹配有两个元素的数组，然后将将元素值赋给对应的 x,y
 
 case Array(0, _*) => "以 0 开头的数组"     //匹配以 0 开头和数组
 
 case _ => "something else"
 }
```

#### 匹配列表

**方式一**

```
val res = list match{
 case List(0) => "0"                //匹配 List(0)
 case List(x, y) => x + "," + y         //匹配有两个元素的 List
 case List(0, _*) => "0 ..."          //匹配以0开头的list
 case _ => "something else"     
 }
```

**方式二**

```
 list match {

 case first :: second :: rest => println(first + "-" + second + "-" + rest)
 //匹配至少有两个元素的列表

 case _ => println("something else")
 }
```

#### 匹配元组

```
val result = tuple match {
 case (0, _) => "0 ..."             //是第一个元素是 0 的元组
 case (y, 0) => "" + y + "0"        // 匹配后一个元素是 0 的对偶元组
 case (a, b) => "" + a + " " + b    //匹配两个元素的数组
 case _ => "something else" 
 }
```

#### 匹配类

**示例**

```
object User{
 def apply(name: String, age: Int): User = new User(name, age)
 def unapply(user: User): Option[(String, Int)] = {
 if (user == null)
 None
 else
 Some(user.name, user.age)
 }
}
object TestMatchUnapply {
 def main(args: Array[String]): Unit = {
 val user: User = User("zhangsan", 11)
 val result = user match {
 case User("zhangsan", 11) => "yes"
 case _ => "no"
 }
 println(result)
 }
}
```

**样例类语法:**

```
case class 类名 (参数)
```

**总结**

1. 样例类仍然是类，和普通类相比，只是其自动生成了伴生对象，并且伴生对象中
自动提供了一些常用的方法，如 `apply、unapply、toString、equals、hashCode 和 copy。`
2. 样例类是为模式匹配而优化的类，因为其默认提供了 `unapply` 方法，因此，样例
类可以直接使用模式匹配，而无需自己实现 unapply 方法。
3. 构造器中的每一个参数都成为 val，除非它被显式地声明为 var（不建议这样做）

####  变量声明中的模式匹配

```
case class Person(name: String, age: Int)
object TestMatchVariable {
 def main(args: Array[String]): Unit = {
 val (x, y) = (1, 2)
 println(s"x=$x,y=$y")
 val Array(first, second, _*) = Array(1, 7, 2, 9)
 println(s"first=$first,second=$second")
 val Person(name, age) = Person1("zhangsan", 16)
 println(s"name=$name,age=$age")
 }
}
```

#### for 表达式中的模式匹配

```
object TestMatchFor {
 def main(args: Array[String]): Unit = {
 val map = Map("A" -> 1, "B" -> 0, "C" -> 3)
 for ((k, v) <- map) {                          //直接将 map 中的 k-v 遍历出来
 println(k + " -> " + v) //3 个
 }
 println("----------------------")
                                                //遍历 value=0 的 k-v ,如果 v 不是 0,过滤
 for ((k, 0) <- map) {
 println(k + " --> " + 0) // B->0
 }
 println("----------------------")
                                                //if v == 0 是一个过滤的条件
 for ((k, v) <- map if v >= 1) {
 println(k + " ---> " + v) // A->1 和 c->33
 }
 }
}
```

#### 偏函数中的模式匹配(了解)

偏函数也是函数的一种，通过偏函数我们可以方便的对输入参数做更精确的检查。例如
该偏函数的输入类型为 List[Int]，而我们需要的是第一个元素是 0 的集合，这就是通过模式
匹配实现的

**定义:**

```
val 偏函数名:偏函数类型[参数类型,返回值类型] = {
  case 语句
}
```

例如:

```
val second: PartialFunction[List[Int], Option[Int]] = {
 case x :: y :: _ => Some(y)
}
```

**偏函数使用:**

偏函数不能像 second(List(1,2,3))这样直接使用，因为这样会直接调用 apply 方法，而应
该调用 applyOrElse 方法，如下

`second.applyOrElse(List(1,2,3), (_: List[Int]) => None)`

applyOrElse 方法的逻辑为 if (ifDefinedAt(list)) apply(list) else default。如果输入参数满
足条件，即 isDefinedAt 返回 true，则执行 apply 方法，否则执行 defalut 方法，default 方法
为参数不满足要求的处理逻辑。

## 第 9 章 异常

**语法:**

```
try {
  可疑代码块
} catch {
  case 语句
} finally {
  代码块
}
```

## 第 10 章 隐式转换

当编译器第一次编译失败的时候，会在当前的环境中查找能让代码编译通过的方法，用
于将类型进行转换，实现二次编译

关键字:  `implicit`

### 10.1 隐式函数

**声明:**

```
implicit def 函数名(参数:参数类型):返回值类型 = {
  代码块
}
```

### 10.2 隐式参数

普通方法或者函数中的参数可以通过 implicit 关键字声明为隐式参数，调用该方法时，
就可以传入该参数，编译器会在相应的作用域寻找符合条件的隐式值

**语法:**

```
def 函数名(implicit 参数名:参数类型) [: 返回值类型] = {
  代码块
}
```

**说明**

1. 同一个作用域中，相同类型的隐式值只能有一个
2. 编译器按照隐式参数的类型去寻找对应类型的隐式值，与隐式值的名称无关。
3. 隐式参数优先于默认参数

### 10.3 隐式类

```
[类,伴生对象,包对象]{
  
  implicit class 类名(参数:参数类型){
    类体
  }

}
```

**隐式类说明**

1. 其所带的构造参数有且只能有一个
2. 隐式类必须被定义在“类”或“伴生对象”或“包对象”里，即隐式类不能是顶
级的


### 10.4 隐式解析机制

**说明**

1. 首先会在当前代码作用域下查找隐式实体（隐式方法、隐式类、隐式对象）。（一
般是这种情况）
2. 如果第一条规则查找隐式实体失败，会继续在隐式参数的类型的作用域里查找。
类型的作用域是指与该类型相关联的全部伴生对象以及该类型所在包的包对象。


## 第 11 章 泛型

### 11.1 协变和逆变

**语法**

```
class MyList[+T]{ //协变
} 

class MyList[-T]{ //逆变
}

class MyList[T] //不变
```

**说明**

协变：Son 是 Father 的子类，则 MyList[Son] 也作为 MyList[Father]的“子类”。

逆变：Son 是 Father 的子类，则 MyList[Son]作为 MyList[Father]的“父类”。

不变：Son 是 Father 的子类，则 MyList[Father]与 MyList[Son]“无父子关系”

### 11.2 泛型上下限

**语法**

```
Class PersonList[T <: Person]{ //泛型上限
}

Class PersonList[T >: Person]{ //泛型下限
}
```

**说明**

泛型的上下限的作用是对传入的泛型进行限定。

### 11.3 上下文限定

**语法**

`def f[A : B](a: A) = println(a) `

等同于 `def f[A](a:A)(implicit arg:B[A])=println(a)`

**说明**

上下文限定是将泛型和隐式转换的结合产物，以下两者功能相同，使用上下文限定[A : 
Ordering]之后，方法内无法使用隐式参数名调用隐式参数，需要通过 `implicitly[Ordering[A]]`
获取隐式变量，如果此时无法查找到对应类型的隐式变量，会发生出错误。
