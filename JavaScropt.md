# JavaScropt

## JavaScropt简介

### JavaScropt是什么？

>   是一种运行在客户端(浏览器)的编程语言,实现人机交互效果

### 作用

-   >   网页特效(监听用户一些行为让网页做出相应反馈)

*   >   表单验证(针对表单数据的合法性进行判断)

+   >   数据交互(获取后台数据渲染到前端)

-   >   服务端编程(node.js)

### 组成

#### ECMAScript

> 规定了js基础语法的核心

#### WeB APIs
-   >   DOM 操作文档

*   >   BOM 操作浏览器

### JS

#### 内部js

>   在<boby>标签最后书写,如`<script>alert("你好,JS");</script>`

#### 外部js

>   代码写在以js结尾的文件里,如：`<script src = "my.js"></script>`

#### 内联js

>   代码书写在标签内部,如：`<button onclick="alert('你好')"></button>`

#### 注释
>   -   单行注释    `//`

>   -   多行注释    `/* */`

### 变量

**变量命名规则**

>   -   不能使用关键字
>
>   -   是能使用下划线、字母、数字、$组成，且不能以数字开头
>
>   -   字母严格区分大小写

**变量命名规范**

>   -   起名要有意义
>   
>   -   遵循小驼峰命名法

*声明变量*

>   `let age`

*变量赋值*

>   `age = 18`

**常量**

-   *使用const命名的变量称为常量*

-   命名规范:和变量一样

-   常量不允许重新赋值，声明的时候必须赋值

>   -   声明方式:   const 变量名 = 值   如:`const pi = 3.14`

**数组**

*将一组数据存储在单个变量名下，索引从零开始*

声明语法:  
-   let 变量名 = [数据1,数据2,数据3,....]  如: `let arr = [1,2]`
-   `let arr = new Array(数据1,数据2..数据n)`

取值语法:  

-   变量名[下标] 如:`arr[0]`

求长度:
-   变量名.length   如:`arr.length`

新增

-   添加到数组末尾  语法: `数组.push(元素1，元素2....元素n)`  会返回新数组的长度

-   添加到数组头部  语法: `数组.unshift(元素1，元素2....元素n)` 会返回新数组的长度

删除

-   删除数组最后一个元素,并返回该元素的值   语法: `数组.pop()`

-   删除数组第一个元素,并返回该元素的值     语法: `数组.shift()`

-   删除指定元素  语法: `数组.splice(start,delectCount)`
-   start 起始位置:指定修改的开始位置(从0开始)  delectCount 表示要移除元素的个数 可选，如果忽略则从指定起始位置删除到最后  

#### **函数**

-   执行特定任务的代码块

>   语法:
>   -   `function 函数名(形参) {函数体}`

-   `return`    返回值

-   实参多于形参    剩下的实参不参与运算

-   实参少于形参    会自动填上`undefined`

*匿名函数*

-   没有名字的函数，无法直接使用

-   使用方式:

-   1.  函数表达式
-   -   >   `let 名字 = function (形参){函数体}`

-   2.  直接使用
-   -   1.   `(function (形参) {函数体})(实参);`
-   -   2.   `(function(形参){函数体}(实参))`
>   命名规范:
>   - can 判断是否可执行某个动作
>   - has 判断是否含有某个值
>   - is  判断是否为某个值
>   - get 获取某个值
>   - set 设置某个值
>   - load 加载某些数据

### 数据类型

**数字类型**

-    整数、小数，负数统称为数字类型

**字符串类型**

-    通过单引号('')、双引号("")包裹起来的数据都叫字符串类型

    可以通过转义符\,输出单引号或双引号，+可以拼接字符串

*模板字符串*

>   语法:   用反引号包裹，内容拼接变量时，用${}包裹变量

>   例如:   document.write(`我今年${age}岁了`)

**布尔型**

    只有真(true)、假(flase)两个字面量

**null(空类型)**

    什么都没有、空的、值未知

### 数据转换

**隐式数据转换**

**显示数据转换**

-   Number()    转数字类型

>   如果字符串里有非数字，转换失败时结果为NaN即不是一个数字

>    例如:   `let num = Number('123')`

-   parseInt()  转为整数

>   语法:   `parseInt('字符串')`

-   parseFloat()    转为浮点数

>   语法：  `parseFloat('字符串')`

-   Boolean()   转换Boolean型

-   -   语法:   Boolean(内容)

#### **if分支语句**

>   语法:   `if (条件){`
>    `条件成立执行的语句`
>    `} else if (条件){`
>        `条件成立执行的语句`
>    `}  else if (条件){`
>        `条件成立执行的语句`
>    `}  ....`
>    `else {`
>        `上面条件都不成立，执行这里的语句`
>    `}`

#### **三元运算符**

>   语法:   条件?条件为真执行的代码块   :   条件为假执行的代码块

#### **switch分支语句**

>   语法: `switch (数据){case 值1:代码块1 case 值2:代码块2 default:代码块n}`
>
>   若小括号里的数据和值全等,则执行里面对应的代码块,
>   若没有全等的则执行default里的代码块

#### **while循环基本语句**

>   `while (循环条件){`
>
>    `循环体(要执行的代码)`
>
>    `}`

>   `continue`  停止当前循环,开始下一次循环

>   `break`     停止循环

#### **for循环**

>   语法:
>
>   `for (变量起始值;终止条件;变量变化量){`
>
>    `循环体`
>
>    `}`

>   `continue`  停止当前循环,开始下一次循环

>   `break`     停止循环

#### **对象**

**对象的定义:**

1.  对象(object):JavaScrips里的一种数据类型

2.  可以理解为一种无序的数据集合，注意数组是有序的数据集合

3.  用来描述某个事物，例如描述一个人

**对象的使用:**

1.  对象声明语法

>   `let 对象名 = {}`
>
>   `let 对象名 = new Object()`

2.  对象有属性和方法组成

>   属性:   信息或叫特征(名词)

>   方法:   功能或叫行为(动词)

3.  属性

>   属性都是成对出现的，包括属性名和值，它们之间使用英文逗号分隔
>
>   多属性之间使用英文逗号分隔
>
>   属性就是依附在对象上的变量(外面是变量，对象内是属性)
>
>   属性名可以使用 "" 或 '' ，一般情况下省略，除非名称遇到特殊符号如空格、中横线等

4.  增删改查

    1.  属性-查:    语法:   `对象名.属性名` 或  `对象名['属性名']`

    2.  属性-改:    语法：  `对象名.属性 = 新值`

    3.  属性-改:    语法：  `对象名.属性 = 新值`

    4.  属性-删:    语法:   `delete 对象名.属性`

**遍历对象:**

>   语法: 
>   `for (let 变量名 in 对象){}`    

>   -   这里遍历出的变量会加上单引号，可以通过`对象[变量]`来取值

**内置对象:**

JavaScrips内部提供的对象，包含各种属性和方法给开发者调用

---

**alert()**

*页面弹出警示框*

>   `alert("你好")`

**document.write()**

*文档输出内容*，如果输出的的内容是标签，则会被解析成网页元素

>   `document.write("我是div标签")`
>
>   `document.write("<h1>div</h1>")`

**console.log()**

*控制台打印给程序员*

>   `console.log("kafka")`

**prompt()**

*输入语句*

>   `prompt("请输入你的年龄")`
