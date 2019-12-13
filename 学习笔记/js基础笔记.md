# JS

JavaScript：一门脚本语言

 作用于交互，给骨架设计一系列响应用户的动作，能和用户交流互动

### 命名

 	1.不能用数字命名变量

​         2.关键词也不能做变量名

​        **命名：驼峰命名法,第一个，第二个单词首字母大写**

转义符：

![](D:\黑马\黑马学习\就业班练习\就业班笔记\自己笔记\学习笔记\images\1498289626813.png)

###  输入和输出

​	1.输入： 引导用户，可以使用单双引号

```css
prompt("请输入密码");
```

​	2.输出： 弹出框，弹出信息，告诉用户一些信息

```css
alert('我最帅');
```

​	3.控制台查看，用于开发调试时，可以多个输出，用逗号隔开

```js
console.log('我又帅了');
```

​	4.弹出框，有两个选项，确定或取消，返回值：true/false

````js
confirm('我又帅了');
````



### 变量	作用 用于存储数据

```js
//用法：先声明一个变量然后使用
        // 1.声明变量
        var num1=10;
        var num2=10;
        console.log(num1+num2);

        // 2.变量赋值，声明后可以再次赋值
         var num=10;
           num=40;
           alert(num);
        // 3.声明复制后，变量参加运算，在复值给本身
            var b=10;
                b=b+20;
            alert(b);
```

### 	数据类型

基本类型：

​	1，数字类型Number：	NaN泛指不确定的数字

​	2.string类型：字符串，必须加单双引号

​	3.布尔（boolean)类型 存在（true）或不存在（false）

​	4.null（值）类型	null表示不存在的类型

​	5.undefined即是类型又是值，如果变量没有赋值，就是undefined

​	6.typeof查看变量类型

###### 数据类型的转换

1.字符串里是数字时，number转换为数字，不是数值时，会转换成NaN

2.string   字符串类型

3.parseInt（）可以转换整数

```js
		var num1 = parseInt("12.3abc");
        // 返回12，如果第一个字符是数字会解析直到遇到非数字结束
        var num2 = parseInt("abc123");
        // 返回NaN，如果第一个字符不是数字或者符号就返回NaN    
        console.log(rst);
```

4.parseFloat() 把字符串转换成浮点数

```js
 // parseFloat()和parseInt非常相似，不同之处在与
 // parseFloat会解析第一个. 遇到第二个.或者非数字结束
// 如果解析的内容里只有整数，解析成整数
```

# 三元表达式

```js
var b=prompt("请输入数字"),a=prompt("请输入数字");
// 表达式1？表达式2：表达式3
// 先执行表达式1，如果执行结果是true，那么把表达式2给返回。如果是false，那么执行表达式3为返回值
var sum=a>b?a:b;
alert('这是最大值'+sum);
```

### 分支结构

#### 1.if语句

```js
var res=prompt('请输入性别');
    // if结构：单个if结构，解决一个分支的判断问题
    if(res==='男'){
        // 如果判断成立，那么执行下面的内容
        console.log('这是个男人');
        alert('这是个男人，去男厕所');
    }
    // 当表达式的结果为false时，执行else的代码
    else if(res==='女'){
        console.log('这是个女士');
        alert('这是个女人，去女厕所');

    }
    // 当多个表达式都是false时，执行此表达式
    else{
        alert('这是个男女不分的人，不能上厕所');
    }
```

2. ###### switch-case 结构

```js
// switch-case：只能适用于多个固定判断，进行===的判断
    switch (prompt('请输入星期天数')){
        case '星期一':
            alert('今天开始学习语文');
            break;
        case '星期二':
            alert('今天开始学习数学');
            break;
        case '星期三':
            alert('今天开始学习英语');
            break;
        case '星期四':
            alert('今天学习历史');
            break;
        case '星期五':
            alert('今天学习政治');
            break
        case '星期六':
            alert('今天玩耍');
            break;
        case '星期日':
            alert('今天睡觉');
            break;
            // 当上面都不执行时，执行此代码（当输入错误的时候，提示用户）
        default:
            alert('输入错误，请输入正确的天数');
            break;
        
        
    }
```

### 布尔类型的隐式转换

流程控制语句会把后面的值隐式转换成布尔类型

```
转换为true   非空字符串  非0数字  true 任何对象
转换成false  空字符串  0  false  null  undefined
```

```javascript
// 结果是什么？
var a = !!'123';
```

## 循环结构

> 在javascript中，循环语句有三种，while、do..while、for循环。

### while语句

基本语法：

```js
// 当循环条件为true时，执行循环体，
// 当循环条件为false时，结束循环。
while (循环条件) {
  //循环体
}
```

案例：

```js
    // var a=0;
    var a = Number(prompt('请输入开始的数字'));
    var res = prompt('请输入结束的数字');
    var sum = 0;
    // 当循环体的判断为true时，执行循环体，否则为false，结束循环体
    while (a <= res) {
        sum = sum + a;
        a++;
    }
    alert(sum);
```

### do...while语句

> do..while循环和while循环非常像，二者经常可以相互替代，但是do..while的特点是不管条件成不成立，都会执行一次。

基础语法：

```javascript
do {
  // 循环体;
} while (循环条件);
```

### for语句

> while和do...while一般用来解决无法确认次数的循环。for循环一般在循环次数确定的时候比较方便

for循环语法：

```javascript
    // for循环的表达式之间用的是;分隔的，千万不要写成,
    for (初始化表达式1; 判断表达式2; 自增表达式3) {
      // 循环体4
    }
```

执行顺序：1243  ----  243   -----243(直到循环条件变成false)

1. 初始化表达式
2. 判断表达式
3. 自增表达式
4. 循环体

案例：

```js
    // 先设置变量，然后判断是否是偶数，然后进入分支执行偶数，然后
    // 定义一个变量，把偶数的和赋予变量，然后再输出变量
    var sum = 0;
    for (var i = 1; i <= 10; i++) {
        if (i % 2 == 0) {
            // 偶数
            console.log('这是偶数' + i);

            // 所有偶数的和
            sum = sum + i;

        }
        // console.log('这是偶数的和'+sum);

    }
    console.log('这是偶数的和' + sum);

```

### 关键字

### continue和break

> break:立即跳出整个循环，即循环结束，开始执行循环后面的内容（直接跳到大括号）
>
> continue:立即跳出当前循环，继续下一次循环（跳到i++的地方）

# 数组

1.数组的特性，数组就是把多个元素，集合在一起，放在一个元素内，的数据集合。

2.数组的声明

```js
// 先声明一个数组，字面量的形式
var arr = [];

// 输出 []  这是一个没有数据在里面的数组，称为空数组
console.log(arr,typeof arr); 
```

3.对数组进行存值

```js
// 自动填入数组
    var arr = new Array();
    for (i = 0; i < 3; i++) {
        arr[i] = Number(prompt('请输入数字'));
    }
    console.log(arr);
```

###### 4.取值

- 把数据取出来，得知道你要取哪个位置上的数据把。

- 数据取值同样使用**索引**取。

- ```js
  // 拿到索引为0，顺序上第一个位置上的数据；// 把 数组[索引] 格式当成一个变量使用就行；console.log(arr[0]);​// 数组求和：班里的成绩总和var sum = arr[0] + arr[1] + arr[2] + arr[3] + arr[4];console.log(sum); // 输出370
  ```

  案例：遍历循环数组

  ```js
  // 先声明数组
      var arr = [80, 20, 40, 50, 45, 69, 40];
      // 然后假设声明的变量为最大值
      var max_i = 3;
      var max = arr[max_i];
      // 然后循环遍历数组，
      for (i = 0; i < arr.length; i++) {
          // 判断假设的数组，是否是数组内的最大值
          if (max < arr[i]) {
              // 如果不是，就把大的值重新赋给max,把最大值的坐标付给max_i
              max = arr[i];
              max_i = i;
          }
      }
      // 输出最大值
      console.log(max, max_i);
  
  
  
      // 先声明数组
      var arr = [80, 20, 40, 50, 45, 69, 40];
      // 然后假设声明的变量为最小值
      var max_i = 3;
      var min = arr[max_i];
      // 然后循环遍历数组，
      for (i = 0; i < arr.length; i++) {
          // 判断假设的数组，是否是数组内的最小值
          if (min > arr[i]) {
              // 如果不是，就把小的值重新赋给min,把最小值的坐标重新赋给max_i
              max_i = i;
              min = arr[i];
          }
      }
      // 输出最小值
      console.log(min, max_i);
      // 最大值
      var arr = [80, 20, 40, 50, 45, 69, 40];
      var max = Math.max.apply(null, arr);
      console.log(max);
      // 最小值
      var min = Math.min.apply(null, arr);
      console.log(min);
  ```

  ###### 数组的构造函数

  - 数组在JS中还可以使用另一种方式创建，这个方式我们称为 ： 构造函数
  - 构造函数：能构造一个你需要的东西（对象）

```js
// 使用 构造函数 创建数组
var arr = new Array();
// 存储数据
arr[0] = 10;
arr[1] = 20;
console.log(arr);

var arr = new Array(10,20);
console.log(arr);
```

案例：插入数组

```js
// 使用 构造函数 创建数组
    // var arr = new Array(prompt('请输入数字'));
    // 存储数据
    // arr[0] = 10;
    // arr[1] = 20;
    // console.log(arr);

    // var arr = new Array(10, 20);
    // console.log(arr);

    // 自动填入数组
    var arr = new Array();
    for (i = 0; i < 3; i++) {
        arr[i] = Number(prompt('请输入数字'));
    }
    console.log(arr);
```

###### 能够说出Math对象的3个方法 

```js
Math.random()  0-1，不包括1；
Math.floor();  向下取整；
// 
Math.ceil();   向上取整；
```

# js函数

## 介绍

- 函数：我们**把一段相对独立的具有特定功能的代码块封装起来**，形成一个**独立实体**，起个名字（函数名），在后续开发中可以**随时反复调用**。
- 作用：**封装（包起来）一段代码，将来可以随时拿来使用。**
- **封装：功能要单一；**

## 语法

```js
// function 关键字 用于声明函数
// tellStroy 函数名
function tellStroy(){
  // 里面叫函数体：我们封装，我们想随时随地拿来使用的东西；
  console.log("从前有座山，山里有座庙");
  console.log("庙里有个在给小和尚讲故事");
  console.log("讲的是什么呢？");
  console.log("老和尚对小和尚说：");
}
```

- 调用：声明的函数，知识一段代码被包起来；需要被调用，才能执行当前的函数；

```js
tellStroy(); //此时在控制台中就会输出一个故事

// 如果想输出多次，就可以调用多次这个函数
tellStroy(); 
tellStroy(); 
tellStroy(); 
```

- 起名字重名，会覆盖；和变量一样；

  

## 参数

参数：对于函数来讲，就是函数内部的变量

### 参数不赋值

- 变量：函数内部的变量，没有赋值，默认为undefined；和我们的变量一模一样；



### 形参与实参的区别



##### 参数

可以配置多个

函数内部的变量

###### 形参

形式上的参数，函数内部声明的变量，只能在内部使用，用与参与逻辑过程

实参：调用函数时，真实参与运算的数据，可以传数据，也可以传变量

#### 相互不影响

传入简单值类型，互不影响

```js
ar a = 10;
var b = 20;

function fn(x,y){
  x = x + y;
  console.log(x,y);
}

// 传入实参a b，相当于是变量a的值，赋值给了函数内部变量x，
// x再以后的运算和a没有任何关系；
// 输出 30，20
fnm(a,b); 

// 输出 10,20 a的值并没有受到x的变化影响
console.log(a,b);
```

### 返回值

函数的返回值：函数执行完毕，会得到一个结果，这个结果就是函数的返回值

### 修改返回值

- **`return`作用1**：修改函数的返回值，若后面有值，则返回，若没有值；默认还是undefined
- **`return`作用2**：终止函数的执行；

### arguments

- 目标：无论输入多少个参数，都可以参加运算；
- arguments：获取所有实参的对象，**函数内部的变量（不是我们声明的，也不需要我们声明）**
- **

```javascript
function fn(){
  console.log(arguments);
}
fn(1); // 输出 [1]
fn(1,2) // 输出 [1,2]
fn(1,2,3,4,5) // 输出 [1,2,3,4,5]
```

- arguments 这个东西看起来**样子像数组**，但是其实不是一个数组，我们管它叫 `伪数组`。它具有数组的长度和顺序等特征。本质为对象，
- arguments 伪数组可以**循环遍历**；

```javascript
function getSum(){
  var sum = 0;
  for(var i = 0; i < arguments.length ; i++){
    sum += arguments[i];
  }
  return sum;
}

getSum(1,2,3);// 输出 6
getSum(1,2,3,4,5); // 输出15
```

- 应用场景：**当我们不知道我们的参数个数的时候；**

### 函数表达式

1.js中声明函数的方式不只一种，还有一种方式叫函数表达式

2.声明变量，赋值函数

```js
// 
var 函数名 = function (参数){
   //函数体
}

var getSum = function(a,b){
  return a + b;
}
getSum(10,20);
```

### 匿名函数

1.匿名函数：没有名字的函数，但在js的语法中，是不允许匿名函数单独存在的，要配合其他语法使用

```js
function(参数){
    函数体
}
var fn=function(a,b){
    return a+b;
}
```

- 自调用函数（自执行函数）：匿名函数的另外一种使用方法；很多时候，我们需要加载页面后，自动执行一个函数；

```js
// 定义之后，立刻调用，输出10
(function(){  
  console.log(10);  
})();
```

 ## 函数类型

```` js
function fn(){}
console.log(typeof fn); // 输出 字符串的  function
````



* ###### 在js中，只要是一种数据类型，都可以作为函数的参数

 ```` js
function f1(a,b){
    return a+b;
}
//数字可以作为参数，字符串也可以作为参数
 ````

## 回调函数

* 函数也是数据类型，也可以作为别的函数的参数

#  作用域

* 作用域：作用范围，能生效的范围
* 当我们写函数时，要先明白自己声明的变量在那个作用域，是全局变量，还是局部变量
* 全局：
  *   全局作用域：能在页面的任何位置都可以访问到
  * 全局变量:在全局作用域下声明的变量

* 局部：
  * 局部作用域：只能在一小部分有效果，最常见与函数内部
  * 局部变量：只能在局部作用域内使用，在其他地方不能使用

```` js
var a = 10;
function f1(){
  console.log(a);
}
f1();// 变量a在函数外定义，可以在函数内使用




function f2(){
  var b = 20;
}
// 变量b在函数内定义，在函数外无法访问，报错： b is not defined
console.log(b); 
````

# 预解析

* 在声明的变量作用域范围内，你声明的变量在任何位置都可以访问到
* 预解析：提前，解析（分析）会把初始化的声明的变量，函数，其全部提升到当前作用域的最顶端
* 也叫变量提升：从概念上来说，变量的提升意味着变量和函数的声明会在物理层面上移动到最前面
  * 只是变量声明到最前面
  * 变量的赋值和函数的调用还在原位置不动

* ###### 找到当前作用域的的顶端，提升上去

  ```` js
  fn();// 正常执行
  function f1(){
    console.log(1);
  }
  fn(); // 正常执行
  
  
  f2();// 报错 ： f2 is not a function
  var f2 = function(){
    console.log(2);
  }
  // function 关键字定义的函数，可以在定义之前使用，函数表达式的不行
  
  
  
  // ------------------------------------------------------------变量提升的演示
  // 预解析：先把你声明变量、函数先全部提升到你当前的作用域的最顶端；
  ````

  

# 对象

* 对象：一个有属性，有方法的集合， 思想：**面向对象思想、万物皆对象**

*  学习：关注对象有什么方法，可以帮我完成什么事，什么效果就好

  ```js
  // 新找到一个日期对象
  // Date 构造函数，构造出一个我们需要的工具，就是对象；
  var date = new Date();
  
  // 调用日期对象的获取年份的方法
  date.getFullYear();
  
  // Math对象
  Math是 内置对象；
  Math.floor();
  ```

  

特点：对于开发人员更友好的开发；

- **实现高效开发**：我们只要知道对象（工具）有什么属性和方法，不需要知道对象里面是如何实现的。**在别人已经提供好的方法的基础上，再次实现我们想要的效果，开发过程将大大缩短。**
- **便于维护：**因为你是单个对象（工具），我可以随时对你进行改造，修改；满足我的需要；



### 创建对象的方法

* 构造函数

  ```js 
  var obj = new Object(); // 这是一个没有属性和方法的对象
  console.log(obj);
  ```

  

* 字面量：从字面上看出数据类型

````js
var obj = {}; // 这也是一个没有属性和方法对象，其本质和构造函数创建的对象是一样的
console.log(obj,typeof obj);
````

### 对象的添加

````js
 // 1.创建对象，属性和方法的集合
    var obj = {};
    //  添加一个属性 语法： 对象.属性名 = 属性值
    obj.name = "可爱";

    // 添加方法： 语法: 对象.方法 function() {}
    obj.name = function() {
            console.log(123);

        }
        // 2.声明对象的时候，添加属性和方法，键值对：每个键值对之间要用，隔开
    var obj_1 = {
            name: "小红",
            age: 20,
            say: function() {
                console.log("我最可爱");

            }

        }
        // 键值对：一个属性和一个值
        // 键值对的方式，添加属性或者方法
        // 语法：属性名 必须是字符串 对象[属性名]=属性值
    var obj_2 = {};
    obj["name"] = "可爱";
````

### 获取和遍历   {} for in 遍历     

````js
// 1.创建对象，属性和方法的集合
    var obj = {};
    //  添加一个属性 语法： 对象.属性名 = 属性值
    obj.name = "可爱";

    // 添加方法： 语法: 对象.方法 function() {}
    obj.name = function() {
            console.log(123);

        }
        // 2.声明对象的时候，添加属性和方法，键值对：每个键值对之间要用，隔开
    var obj_1 = {
            name: "小红",
            age: 20,
            say: function() {
                console.log("我最可爱");

            }

        }
        // 对象
        // 键值对：一个属性和一个值
        // 键值对的方式，添加属性或者方法
        // 语法：属性名 必须是字符串 对象[属性名]=属性值
    var obj_2 = {
        name: "小红",
        age: 20,
    };
    obj["name"] = "可爱";
    console.log(obj["name"]);
    // 获取：可以通过键值对的方式打印
    // 对象：遍历，可以把对象上，每个键值对里的键或值都可以拿到
    for (var key in obj_2) {
        // 在遍历内部，点的方式会把key当做obj_2的一个属性名，去获取
        // 所以要用obj_2[key]获取
        console.log(obj_2[key]);

    }
````

# 内置对象

- 对象：属性和方法的集合体；**我们关注如何使用就可以；**
- 内置：JS语法给我封装好了一些对象，里面提供了很多常用、实用的属性和方法；

###### Math

* Math.random();生成一个[0,1}的随机浮点数

* Math.floor（）把一个浮点数进行向下取整

  ````js
  // Math.random()，求随机数字
      function get_bgc(a) {
         //每次生成的浮点数都不相同
          var a = Math.random();
          a = a * 256;
          //将浮点数进行取整
          a = Math.floor(a);
          return a;
      }
  ````

* Math.round(a) 把一个浮点数进行四舍五入

````js
Math.round(a)
````

* Math.ceil(a) 将浮点数进行向上取整

  ````js
  Math.ceil(a) 
  ````

* Math.abs(a)  求一个数的绝对值，所转出的数字绝对为正数

````js
Math.abs(3)
````

* Math.max(x,y..) 求多个数字的最大值，同理Math.min()一样的

Date

语法：

````js
var date=new Date(); //设置日期对象
````

###### 时间锉

````js
var date = new Date();
//获得时间数字，这是个相对唯一的数字
console.log(date.valueOf());
console.log(date.getTime());
console.log(1*date);

console.log(Date.now());
````

# Array（数组）

* 对元素操作
* ###### push 从数组后面推入一个元素或多个元素

````js
    var arr = [1, 2, 3, 4, 5];
    // push 把元素或多个元素，从数组后面添加
    // 参数：添加的数据
    // 返回值：数组的长度
    var l = arr.push(8);
    console.log(arr, l);
````

* ###### pop 删除数组最后一个元素

````js
var arr =[1,2,3];
// 2.pop 从后面删除一个元素  返回被删除的元素
    arr.pop();
````

* ###### unshift 从数组前面添加一个或多个元素

````js

    // 把元素或多个元素，从数组前面添加
    // 参数：添加的数据
    // 返回值：数组的长度
    arr.unshift();
````

* ###### shift 用于将数组的第一个元素移除

````js
    // 从前面删除一个元素  返回被删除的元素
    arr.shift();
````

* ###### splice 可以进行数组任何位置的增删改

````js
// splice 可以进行数组任何位置的增删改
    // 删除： 第一个参数是开始的下标， 第二个参数是删除的个数 返回值是被删除的数组
    arr.splice(3, 1);
    // 增加： 第一个参数是开始的下标， 第二个参数是删除的个数 后面的是增加的元素，返回值一个空数组
    arr.splice(3, 0, 7, 8);
    // 修改：第一个参数是开始的下标， 第二个参数是替换的个数 后面的是增加的元素，
    arr.splice(3, 1, 7);
````

* ###### reverse 将数组进行反转

  ```js
  art.reverse();
  ```

  replace对数组进行替换

###### 数组与字符串之间的互转

- ###### join 用于将数组中的多元素以指定分隔符连接成一个字符串

```js
var arr = ['刘备','关羽','张飞'];
var str = arr.join('|'); 
console.log(str);  // 刘备|关羽|张飞
```

- ###### split 字符串的方法：转数组，后面为分隔的字符

```js
// 这个方法用于将一个字符串以指定的符号分割成数组
var str = '刘备|关羽|张飞';
var arr = str.split('|');
console.log(arr);
```

# 查找元素

* indexOf:根据元素查找索引，如果这个元素在数组内，则返回下标，否则返回-1

````js
    var arr = "我爱我家";
    // 字符串特别，新组成的字符串，会放入a在内存上的空间，栈上面的空间，原来的字符串不会被覆盖，但会处于游离状态
    // 多次操作字符串，会有多个游离字符串、要减少多次操作避免内存空间减少



    // 把要查询的字符串在 整个字符串内位置下标返给你，多个字符是遇到的第一给字符的下标
    // 如果没有，返回值为：-1
    arr.indexOf("家");
````

- findIndex方法用于查找满足条件的第一个元素的索引，如果没有，则返回-1

```js
var arr = [10, 20, 30];
var res1 = arr.findIndex(function (item) {
  return item >= 20;
});
// 返回 满足条件的第一个元素的的索引
console.log(res1);  


var res2 = arr.findIndex(function (item) {
  return item >= 50;
});
// -1
console.log(res2);
```

lastIndexOf() 查询方式，从后到前

```js
    // 查询方式，从后到前
    arr.lastIndexOf("爱");
```

* charAt  查询下标，获取字符串所在的字符

````js
    // 查询下标，返回字符
    arr.charAt(3);
````

* charCodeAt

  ````js
  // 这个方法用于获取字符串中位于指定位置的字符的ASCII码
  var str = 'abcdef'
  console.log(str.charCodeAt(0));
  ````

  

  ### 遍历数组

forEach:遍历数组

````js
   //用数组forEch的方法也可以遍历数组
var arr = [1, 2, 3, 6];
    // forEach 可以用于数组的循环
    // item 数组的每个值
    // index 数组的下标
    // arr 当前循环的数组
    arr.forEach(function(item, index, arr) {

    })
````

filter 筛选出数组中满足条件的数组，**返回是一个新的数组**

````js
//filter把数组满足条件的元素，重新抽出来，形成一个新的数组
    // item 数组的每个值
    // index 数组的下标
    // arr 当前循环的数组
    arr.filter(function(item, index, arr) {

    })
````

### 拼接与截取

* concat 拼接数组，不改变原数组，重新创建一个数组返回，与原数组无关
* slice 截取数组，不对原数组操作，返回的是新的数组

````js
var arr = [1, 2, 3, 6];
    // concat 拼接数组，不改变原数组，重新组成一个数组返回
    var res = arr.concat([9, 6]);
    console.log(res);

    // slice 截取数组，不改变原数组，重新组成一个数组返回
    // 第一个参数开始的下标，第二个参数结束的下标,如果不写第二个参数，会把开始的下标后面的所有元素截取
    // 如果不写参数，会把后面的所有元素截取
    var res = arr2.slice(1, 3);
    console.log(res);
````

* substring 截取字符串，不操作原字符串;返回截取出来的字符串

````js
// 这个方法用于获取字符串中的部分字符
var str = '我爱中华人民共和国';

// 从索引2开始，到索引4结束，得到之间的字符，不包含索引4的字符
var res = str.substring(2,4);
console.log(res);
````

* substr 获取字符串中的部分字符

````js
// 这个方法用于获取字符串中的部分字符
var str = '我爱中华人民共和国';
var res = str.substr(2,2);// 人索引2开始，总共获取2个字符，第二个参数为个数
````

* replace（'查找的字符'，'替换的字符')