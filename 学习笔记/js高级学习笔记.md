# JavaScript面向对象

## 两大编程思想：

### 	1，面向对象

* 就是把事件分成一个个对象，然后分工合作

###         2，面向过程

* 就是完成事件所需要的步骤

**注意：两者的区别**

* 面向过程：相对来说是针对于小项目的
* 面向对象：是多人合作的大项目

###         3，面向对象的三大特性

* 封装性：将方法封装好，然后直接调用就行（就是把我们抽象出来的属性和方法写在类的定义中，称之为封装）
* 继承性：可以被继承（子类获得父类的属性和方法）
* 多态性：可以被多人调用，不同的对象使用不同的效果

###        4，面向对象和过程的优缺点

###### 		1，面向过程：

​			优点：性能比面向对象高，步骤紧密

​			缺点：不好维护，不能多次使用

###### 		2，面向对象

​			优点：易维护，可复用，可扩展，灵活性高

​			缺点：性能没有面向过程高

# ES6中的类和对象

###### 只有ES6里面有类，而ES5里面却没有类

类：泛指所有的对象， eg(手机)

对象：指具体的事物，是由属性和方法组成，代表类里面的某个实例  ，属性指：事物的特征（对象有什么），方法是：事物的行为（对象去做什么）eg（小米）

###### 面向对象的思维特点：

对象：有自己的独有的方法和属性

**对象是由属性和方法组成的：**

​	属性：对象有什么【访问】【语法：对象.属性】

​	方法：对象做什么【执行】【语法：对象.方法()】

###### 一定要记住：在类里面调用属性或者方法：【对象.属性|||对象.方法()】

## 类Class

* 对象共有的属性和方法组合成的就是类（也叫模板）

## 创建类

````js
语法：class 类名 {
    这里是属性和方法
}
注意：类名一般首字符都是大写
````

## 类constructor构造函数

````js
class star{
    constructor(){
        this.name=name;
    }
}
//属性：放到constructor，构造函数里面


//注意：类里面的方法不带function，直接写就可以
//类里面要有属性方法，属性方法要是放到类里面,我们要在constructor里调用
构造函数作用：接收参数，返回实例对象，new的时候知道执行，主要放置一些公共的属性
````

> constructor() 方法是类的构造函数(默认方法)，用于传递参数,返回实例对象，通过new命令生成对象实例时，自动调用该方法。
>
> 注意：每个类里面一定有构造函数，如果没有显示定义, 类内部会自动给我们创建一个constructor() ，
>
> 注意：this代表当前实力化对象，谁new就代表谁

------

## 类添加方法

注意：方法与方法之间不能添加逗号,方法前面不用再写关键字  function

````js
class Star {

	constructor () {}

	sing () {}

	tiao () {}

}
注意：类中定义属性，调用方法都得用this
class 类名 {
    construnctor () {}
    方法名（）{}
}
````

###### 总结：类有公共属性和方法，用class创建，class里面包含constructor和方法，我们把共属性放到constructor里面，把公共方法直接直接在后面写即可，但要注意的是方法与方法之间不要加逗号

## 类的继承

* ###### **extends**关键字：子类继承父类

````js
语法：
class father {}
class son extends father{}
````

* ###### super关键字

**super关键字**用于访问和调用父类对象上的函数，可以调用父类的构造函数

````js
注意：当子类没有构造函数时，就可以随意的调用父类的属性和方法，但当子类也有自己的构造函数和方法时，那么这时this的指向就不同了，所以这是就需要//关键字super了

//调用父类构造函数
class F { 
    constructor(name, age){
        this.name=name;
    
}
}

class S extends F { 
    constructor (name, age) {
        //调用父元素的属性
        super(name,age); 
        this.xio=sio;
        this.name=name;
    } 
    //调用父元素的方法
     super.say() }
}

注意: 子类在构造函数中使用super, 必须放到this 前面(必须先调用父类的构造方法,在使用子类构造方法
````

###### 总结：如果没用关键字super，那么查找属性和方法的原则就近原则，super调用父类的属性和方法，

## 三个注意点

- 在ES6中类没有变量提升，所以必须先定义类，才能通过类实例化对象.
- 类里面的共有属性和方法一定要加this使用.【this，对象调用属性和方法】按钮练习
- 类里面的this指向问题. 
- constructor 里面的this指向实例对象, 方法里面的this 指向这个方法的调用者

## 类里面的this指向

* 构造函数的this指向为实例对象
* 当在普通函数里面时，那么this就是，谁调用，this就是谁

# ES5：

## 创建对象有三种方式

* 对象字面量
* new Object() [构造函数]
* 自定义构造函数

# 构造函数和原型

构造函数：一种特殊的函数，主要用来初始化对象，即对象成员赋初始值，与new结合使用，把对象公共的属性和方法抽取出来封装到一个函数内（和ES6里面的类差不多）

使用构造函数要注意两点：

* 构造函数用于创建某一对象，首字母要大写
* 构造函数要和new一起使用才有意义

## 普通函数和构造函数的区别：

在命名规则上，构造函数一般是首字母大写，普通函数遵照小驼峰式命名法。

在函数调用的时候：

````js
function fn() { }
````

######      构造函数：new fn( )

​                     2 .构造函数内部会创建一个新的对象，即f的实例

​                     3. 函数内部的this指向 新创建的f的实例

​                     4. 默认的返回值是f的实例

######      普通函数： fn( )

​                     2. 在调用函数的内部不会创建新的对象

​                     3. 函数内部的this指向调用函数的对象（如果没有对象调用，默认是window）

​                     4. 返回值由return语句决定

 

######  构造函数的返回值：

​     有一个默认的返回值，新创建的对象（实例）；

​     当手动添加返回值后（return语句）：

​          1. 返回值是基本数据类型-->真正的返回值还是那个新创建的对象（实例）

​          2. 返回值是复杂数据类型（对象）-->真正的返回值是这个对象

**new在执行时会做四件事情**

​	1，在内存中创建一个新的空对象

​	2，让this指向这个新的空对象

​	3，执行构造函数里面的代码，给这个新对象添加属性和方法

​	4，返回这个新对象（所以构造函数里面不需要return）

## 静态成员和实例对象

* 静态对象：在构造函数上添加的成员称为静态成员，只能构造函数本身访问

  ````js
  Person.hobby = 'running'
  Person.clim = function(){
      console.log('Clim...')
  }
  //上述的hobby和climb就是静态成员
  
  ````

  

* 实例成员：在构造函数内部创建的对象成员称为实例成员，只能由实例化的对象访问(**构造函数中this上添加的成员**)

````
function Person(uname,age){
    this.uname = name ;
    this.age = age;
    this.sayHi = function(){
    console.log('Hello...')
    }
    //上述的name\age\sayHi就是实例成员
}
````

## 构造函数原型prototype

​	prototype是构造函数的一个属性，也称之为原型对象

​		**每一个构造函数都有一个属性**：**prototype**

​		**作用**：是为了共享方法，从而达到节省内存

> 构造函数通过原型分配的函数是所有对象所共享的。
>
> JavaScript 规定，每一个构造函数都有一个prototype 属性，指向另一个对象。注意这个prototype 就是一个对象，这个对象的所有属性和方法，都会被构造函数所拥有。我们可以把那些不变的方法，直接定义在prototype 象上，这样所有对象的实例就可以共享这些方法。

​	**总结**：**所有的公共属性都写在构造函数内**，**所有的公共方法都写在原型对象里面**

## 对象原型：______proto______

​	**主要作用**：指向prototype

​	构造函数和原型对象都有一个属性__proto__指向构造函数的prototype原型对象

​	**注意**：____proto____是一个非标准属性，不可以拿来赋值或者设置【只读属性】

````
1.____proto____对象原型和原型对象prototype 是等价的

2.____proto____对象原型的意义就在于为对象的查找机制提供一个方向，或者说一条路线，但是它是一个非标准属性，因此实际开发中，不可以使用这个属性，它只是内部指向原型对象prototype
````

##  constructor	构造函数

​	**主要作用可以指回原来的构造函数**

## 构造函数、实例、原型对象三者之间的关系

![](D:\黑马\黑马学习\就业班练习\就业班笔记\自己笔记\学习笔记\images\构造函数，原型对象，对象实例关系.jpg)

## 原型链

```
作用：提供一个成员的查找机制，或者查找规则
```

![](D:\黑马\黑马学习\就业班练习\就业班笔记\自己笔记\学习笔记\images\原型链.jpg)



## JavaScript 的成员查找机制(规则)

```
当访问一个对象的属性（包括方法）时，首先查找这个对象自身有没有该属性。

如果没有就查找它的原型（也就是__proto__指向的prototype 原型对象）。

如果还没有就查找原型对象的原型（Object的原型对象）。

依此类推一直找到Object 为止（null）。

__proto__对象原型的意义就在于为对象成员查找机制提供一个方向，或者说一条路线。

// console.log(Star.prototype.__proto__.__proto__);
// console.log(Object.prototype);
```

## 扩展内置对象

```
可以通过原型对象，对原来的内置对象进行扩展自定义的方法。比如给数组增加自定义求偶数和的功能。
```

```
console.log( Array.prototype );
	// 添加求和方法
	Array.prototype.sum = function () {
		var sum = 0;
		for (var i = 0; i < this.length; i++) {
			sum += this[i];
		}
		return sum;
	}

	var arr = [1,2,3];
	console.log( arr.sum() );

	var newArr = [6,7,8,9];
	console.log( newArr.sum() );
```

# 继承

因为没有ES6提供的extends 继承，我们可以通过构造函数+原型对象模拟实现继承，称为组合继承

**属性的继承**

````
call()

调用这个函数, 并且修改函数运行时的this 指向

fun.call(thisArg, arg1, arg2, ...);call把父类的this指向子类

thisArg ：当前调用函数this 的指向对象

arg1，arg2：传递的其他参数
````

## **方法的继承：**

​	**实现方法把父类的实例对象保存给子类的原型对象**，**就是把父类的实例	化对象赋予给子类的原型对象**

```
一般情况下，对象的方法都在构造函数的原型对象中设置，通过构造函数无法继承父类方法。核心原理：

①将子类所共享的方法提取出来，让子类的prototype 原型对象= new 父类()  

②本质：子类原型对象等于是实例化父类，因为父类实例化之后另外开辟空间，就不会影响原来父类原型对象

③将子类的constructor 

把父类的实例对象赋值给子类的原型
```

**注意**：**实现继承后**，**一定要子类（constructor）指回构造函数**

**用构造函数实线属性继承**，**用原型对象实线方法继承**

# 函数进阶

## 函数的定义和调用

* 函数声明方式function关键字（命名函数）
* 函数表达式（匿名函数）【自调函数】

````js
new Function()   var fn = new Function('参数1','参数2'..., '函数体')

var fn = new Function('a','b','console.log(a,b);');
  
fn(123,456);
````

* function里面参数都必须是字符串格式
* 第三种方式执行效率低，也不方便书写，因此较少使用
* 所有的函数都是function的实例对象，函数也属于对象

## 函数的调用方式

* 普通函数
* 对象的方法
* 构造函数
* 绑定事件函数
* 定时器函数
* 立即执行函数

### this的指向

* this：当前调用者

![](D:\黑马\黑马学习\就业班练习\就业班笔记\自己笔记\学习笔记\images\this.bmp)

### 改变函数内部this指向

* JavaScript为我们提供了一些函数方法来帮我们更好的处理函数内部this的指向问题，常用的有：bind()，call()，apply(),三种方法

  

#### call方法

* call() 方法调用一个对象，简单理解为调用函数的方式，但是它可以改变函数的this指向

````js
fun.call(thisArg, arg1, arg2, ...)
thisArg：在fun 函数运行时指定的this 值

arg1，arg2：传递的其他参数

返回值就是函数的返回值，因为它就是调用函数
 //语法：
 function Father () {this}
function Son () { Father.call(this,1,2) }
````

* 注意:当我们想改变this指向，同时想调用这个函数时，就可以使用call
* 应用场景：方法的继承

#### apply方法

````js
fun.apply(thisArg, [argsArray]):调用函数

thisArg：在fun函数运行时指定的this值

argsArray：传递的值，//必须包含在数组里面

返回值就是函数的返回值，因为它就是调用函数
//语法：
var obj = {name : '张三丰'}
	function fn (arr) {
		console.log(this);
		console.log(arr);
		console.log(arr2);
	}


	//#################################################
	var arr = [23,45,56,23,54];

	var n = Math.max.apply(null,arr);

	console.log(n);
````

* 应用场景：因为apply主要和数组有关，所以大部分使用Math.max() 求数组的最大值

#### bind方法

* 只改变this的指向，并不调用函数

````js
bind() 方法不会调用函数。但是能改变函数内部this 指向

fun.bind(thisArg, arg1, arg2, ...)

thisArg：在fun 函数运行时指定的this 值

arg1，arg2：传递的其他参数

//返回由指定的this 值和初始化参数改造的原函数拷贝
````

* 应用场景：当我们想改变this指向时，但又不想调用函数时，就可以使用bind

## call  apply  bind 区别

* **相同点**:
  * 都可以改变函数内部this指向
  * call和apply	在改变函数内部this指向时，都调用了函数
* **区别点**:
  * call和apply	传递的参数不一样，call  传递的参数是 arue1,arue2....形式的，而apply传递的参数，必须是数组
  * bind     改变函数内部this指向时，不会调用函数

* **应用场景**：
  * call 经常用于继承
  * apply  因与数组有关，所以经常用于求数组的最大值和最小值
  * bind   不调用函数，因此，当想改变this指向，又不想调用函数时，可以使用，比如改变定时器内部的this指向

# 严格模式

###### js:有两种模式

​	1，正常模式

​	2，严格模式

````
什么是严格模式

JavaScript 除了提供正常模式外，还提供了严格模式（strictmode）。ES5 的严格模式是采用具有限制性JavaScript 变体的一种方式，即在严格的条件下运行JS 代码。
严格模式在IE10 以上版本的浏览器中才会被支持，旧版本浏览器中会被忽略。
严格模式对正常的JavaScript 语义做了一些更改：

1.消除了Javascript语法的一些不合理、不严谨之处，减少了一些怪异行为。【例如变量，不声明就报错】
2.消除代码运行的一些不安全之处，保证代码运行的安全。
3.提高编译器效率，增加运行速度。
4.禁用了在ECMAScript的未来版本中可能会定义的一些语法，为未来新版本的Javascript做好铺垫。比如一些保留字如：class, enum, export, extends, import, super 不能做变量名
````

#### 开启严格模式

开启严格模式："use strict"

````js
<script>"use strict"</script>//：脚本开启严格模式
	<script>function fn () {"use strict"}</script>//为函数开启严格模式
````

* 严格模式可以应用到整个脚本或个别函数内，所以在使用时，我们将严格模式分为脚本开启和函数开启两种情况

为脚本开启严格模式**

```
为整个脚本文件开启严格模式，需要在所有语句之前放一个特定语句“use strict”;（或‘use strict’;）。

<script>
	"use strict";
	console.log("这是严格模式。");
</script>

因为"use strict"加了引号，所以老版本的浏览器会把它当作一行普通字符串而忽略。
```

**为函数开启严格模式**

```
要给某个函数开启严格模式，需要把“use strict”;  (或'use strict'; ) 声明放在函数体所有语句之前。

function fn(){"use strict";return "这是严格模式。";}

将"use strict"放在函数体的第一行，则整个函数以"严格模式"运行。
```

## 严格模式中的变化

*变量规定**

​	**********变量申明必须加var，而且不准删除变量

```
在正常模式中，如果一个变量没有声明就赋值，默认是全局变量。严格模式禁止这种用法，变量都必须先用var命令声明，然后再使用。
n = 3;
严禁删除已经声明变量。例如，delete x; 语法是错误的。
```

**严格模式下this 指向问题**

​	*********：严格模式下，普通函数this是undefined

```
以前在全局作用域函数中的this 指向window 对象。
严格模式下全局作用域中函数中的this是undefined。

其他的没有变化：
以前构造函数时不加new也可以调用,当普通函数，this 指向全局对象
严格模式下,如果构造函数不加new调用, this 指向的是undefined 如果给他赋值则会报错
new 实例化的构造函数指向创建的对象实例。
定时器this 还是指向window 。
事件、对象还是指向调用者。
```

**函数变化**

​	参数不能重名

```
函数不能有重名的参数。

函数必须声明在顶层.新版本的JavaScript 会引入“块级作用域”（ES6 中已引入）。为了与新版本接轨，不允许在非函数的代码块内声明函数。【if，for等里面定义函数也不可以，但是现在不可以】

更多严格模式要求参考：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Strict_mode

错误写法:
function fn (a,a) {console.log(a+a);}
fn(1,2);

```

# 高阶函数

* 高阶函数是对其他函数进行操作的函数，他可以接收函数作为参数或将函数作为返回值输出

````js
//函数也是一种数据类型，同样可以作为参数，传递给另外一个参数使用。最典型的就是作为回调函数。

同理函数也可以作为返回值传递回来

<script>
	function fn(callback){
		callback&&callback();
	}
	fn(function(){
		alert('hi')
	})
</script>


<script>
	function fn(){
		return function() {}
	}
	fn();
</script>
````

# 闭包

## 变量作用域

* 变量根据在不同的作用域：被分为，全局变量。局部变量
  * 函数内部可以使用全局变量
  * 局部只能函数内部使用，函数外部不可以使用
  * 当函数执行完毕之后，本作用域的局部变量就会销毁

## 什么是闭包

* 闭包作用：延伸变量的作用范围
* 闭包指有权访问另一个函数作用域中变量的函数，简单来说就是，一个作用域有权访问另一个函数内部的局部变量

````js
<script>
	function fn1(){
		// fn1 就是闭包函数
		var num = 10;
		function fn2(){
			console.log(num); // 10
		}
		fn2()
	}
	fn1();
</script>
````



# 类的本质

类的本质还是函数

累的所有方法都定义在类的原型对象（prototype）属性上

````
类创建的实例,里面也有__proto__ 指向类的prototype原型对象
````

所以ES6的类它绝大部分的功能，ES5也是可以做到的，只是类的写法让对象原型更加清晰，更加面向对象编程的语法而已

###### 简单理解, 有两种方法可以实现同样的功能, 但是一种写法更加清晰、方便,

# ES5中的新增的方法

## 数组的方法

- ###### 迭代（遍历）方法;forEach()，map()，filter()，some()，every()

- 都是遍历数组的方法

### forEach（）

```js
array.forEach(function(currentValue, index, arr))

currentValue：数组当前项的值
index：数组当前项的索引
arr：数组对象本身
//遍历数组
语法：
var arr = ['red','blue','yellow','orange'];

arr.forEach(function (elm,i,arrAbc) {
	console.log(elm,i,arrAbc);
});
```

### filter()

- filter() 方法遍历的数组，是新的数组不在是原来的数组了，新数组的元素是通过检查指定数组中符号条件的所有元素，主要主要作用是筛选元素

```js
array.filter(function(currentValue, index, arr))
currentValue: 数组当前项的值

index：数组当前项的索引

arr：数组对象本身回调函数里面添加return添加返回条件
语法：
var arr = [100,66,99,123,333,33,44,66];
	var reArr = arr.filter(function (elm, a, n) {

	// console.log(elm,a, n);
	return elm % 2 == 0;

	});

	console.log(reArr);
```

### some()

- ###### some()	用于检测数组中的元素是否满足指定条件，查找数组中是否满足条件的元素

```js
array.some(function(currentValue, index, arr)) 【注意：找到或者满足条件立刻停止】
 currentValue: 数组当前项的值index：数组当前项的索引

 arr：数组对象本身
 注意它返回值是布尔值, 如果查找到这个元素, 就返回true , 如果查找不到就返回false.

如果找到满足条件的元素，则终止循环，不在继续查找

语法：
var arr = [100,200,300,400];
var re = arr.some(function (elm,i,arr) {
		// console.log(elm,i,arr);
		console.log(i);
		return elm >= 200;
	});
console.log(re);
```

### every(）

every():所有都符合符合条件，返回：true 一个不符合就返回：false

```js
		isCheckAll () {
			// every 方法：
			// 遍历数组，对每一个元素执行 todo.done === true 条件判定
			// 如果条件判定为 false，则停止遍历，返回 false
			// 如果直到遍历结束，都符合 todo.done === true 条件，every 方法返回 true
			// 说白了就是只有所有元素都满足 todo.done === true 才返回true，
			// 但凡有一个不满足就返回 false
			// 与 some 正好相反
			const ret = this.todos.every(function (todo) {
			  return todo.done === true
			})

			return ret
		}
```



## 字符串方法

###### trim:删除字符串两册的空白符

```js
str.trim()
```

# 递归

* 递归：如果一个函数在内部可以调用其本身，那么这个函数就是递归函数，简单来说，就是函数内部就是自己调用自己，这个函数就是递归函数
* 注意：递归函数的作用和循环效果一样,由于递归很容易发生`栈溢出`，错误（stack overflow），所以必须要加退出条件return。

## 练习：

```
利用递归求1~n的阶乘

//利用递归函数求1~n的阶乘 1 * 2 * 3 * 4 * ..n
 function fn(n) {
     if (n == 1) { //结束条件
       return 1;
     }
     return n * fn(n - 1);
 }
 console.log(fn(3));
```

```
利用递归求斐波那契数列

// 利用递归函数求斐波那契数列(兔子序列)  1、1、2、3、5、8、13、21...
// 用户输入一个数字 n 就可以求出 这个数字对应的兔子序列值
// 我们只需要知道用户输入的n 的前面两项(n-1 n-2)就可以计算出n 对应的序列值
function fb(n) {
  if (n === 1 || n === 2) {
        return 1;
  }
  return fb(n - 1) + fb(n - 2);
}
console.log(fb(3));


思考题羊村：50人家，每户一只羊
	每户只能看别人家的羊有木有病
	每户只能杀自己家的羊
	第一天，第二天 ,第三天，砰砰砰几声枪响，问杀了几只羊
```

```
利用递归遍历数据

		var data = [
			{
				id : 1,
				name : '家电'
			},
			{
				id : 2,
				name : '服饰'
			}
		];


var data = [{
   id: 1,
   name: '家电',
   goods: [{
     id: 11,
     gname: '冰箱',
     goods: [{
       id: 111,
       gname: '海尔'
     }, {
       id: 112,
       gname: '美的'
     },

            ]

   }, {
     id: 12,
     gname: '洗衣机'
   }]
 }, {
   id: 2,
   name: '服饰'
}];
//1.利用 forEach 去遍历里面的每一个对象
 function getID(json, id) {
   var o = {};
   json.forEach(function(item) {
     // console.log(item); // 2个数组元素
     if (item.id == id) {
       // console.log(item);
       o = item;
  
       // 2. 我们想要得里层的数据 11 12 可以利用递归函数
       // 里面应该有goods这个数组并且数组的长度不为 0 
     } else if (item.goods && item.goods.length > 0) {
       o = getID(item.goods, id);
     }
   });
   return o;
}
```

## 深拷贝和浅拷贝

拷贝不能直接赋值，对象赋值的是地址

````js
var obj = {
		name : '张三丰',
		age : 22
	};
var newObj = obj;
console.log(newObj);
````

浅拷贝：只拷贝最外面的一层

````js
var obj = {
			name : '张三丰',
			age : 22
		};

		var newObj = {};
		for (key in obj) {
			newObj[key] = obj[key];
		}

		console.log(newObj);
		
es6：新方法

Object.assign(target, sources);

console.log(newObj);
````

# 正则表达式

* 正则表达式是用于匹配字符串中字符组合的模式，正则表达式也是对象
* 作用：检索关键字，过滤敏感字符 表单验证
* 应用场景：用来检索、替换那些符合某个模式（规则）的文本，例如验证表单：用户名表单只能输入英文字母、数字或者下划线， 昵称输入框中可以输入中文(匹配)。此外，正则表达式还常用于过滤掉页面内容中的一些敏感词(替换)，或从字符串中获取我们想要的特定部分(提取)等 。

## 正则表达式特点

* 灵活性，逻辑性和功能性非常强
* 可以迅速地用极简单的方式达到字符串的复杂控制
* 对于刚接触的人来说，比较晦涩难懂
* 实际开发,一般都是直接复制写好的正则表达式. 但是要求会使用正则表达式并且根据实际情况修改正则表达式.   比如用户名:   /^[a-z0-9_-]{3,16}$/

## 正则表达式在js中的使用

创建正则表达式**

```
在 JavaScript 中，可以通过两种方式创建一个正则表达式。

方式一：通过调用RegExp对象的构造函数创建 

    var regexp = new RegExp(/123/);
    console.log(regexp);

方式二：利用字面量创建 正则表达式

     var reg = /abc/; 含义：只要包含abc就可以
     


```

## 测试正则表达式 

```
test() 正则对象方法，用于检测字符串是否符合该规则，该对象会返回 true 或 false，其参数是测试字符串

注意正则里面没有引号
regexObj.test(str);
regexObj：正则表达式
str：用户输入字符串

var rg = /123/;
console.log(rg.test(123));//匹配字符中是否出现123  出现结果为true
console.log(rg.test('abc'));//匹配字符中是否出现123 未出现结果为false
```

## 正则表达式中的特殊字符

### 正则表达式的组成

```
个正则表达式可以由简单的字符构成，比如 /abc/，也可以是简单和特殊字符的组合，比如 /ab*c/ 。其中特殊字符也被称为元字符，在正则表达式中是具有特殊意义的专用符号，如 ^ 、$ 、+ 等。

正则表达式：简单字符 和 特殊字符【元字符】

特殊字符非常多，可以参考： 

MDN：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Regular_Expressions


jQuery 手册：正则表达式部分

正则测试工具 ： http://tool.oschina.net/regex

```

正则：匹配字符串

​	1、创建珍珠铬【new RegExp(/abc/)，var str = /abc/;】

​	2、测试【reg.test(str)】

​	3、表达式：简单字符和特殊字符





创建正则：1、new RegExp(/abc/);2、var reg = /abc/;

reg.test(字符串)

var reg = /abc/;

简单字符，特殊字符【元字符】

# 边界符



```
正则表达式中的边界符（位置符）用来提示字符所处的位置，主要有两个字符

^ : 表示匹配行首的文本（以谁开始）【/^abc/：以abc为开头】

$：表示匹配行尾的文本（以谁结束）【/^abc$/：只能是abc】

```

**如果 ^和 $ 在一起，表示必须是精确匹配。**

```
var rg = /abc/; // 正则表达式里面不需要加引号 不管是数字型还是字符串型
// /abc/ 只要包含有abc这个字符串返回的都是true
console.log(rg.test('abc'));
console.log(rg.test('abcd'));
console.log(rg.test('aabcd'));
console.log('---------------------------');
var reg = /^abc/;
console.log(reg.test('abc')); // true
console.log(reg.test('abcd')); // true
console.log(reg.test('aabcd')); // false
console.log('---------------------------');
var reg1 = /^abc$/; // 精确匹配 要求必须是 abc字符串才符合规范
console.log(reg1.test('abc')); // true
console.log(reg1.test('abcd')); // false
console.log(reg1.test('aabcd')); // false
console.log(reg1.test('abcabc')); // false
```

# 字符类

> ```
> 符类表示有一系列字符可供选择，只要匹配其中一个就可以了。所有可供选择的字符都放在方括号内。
> ```

##  [] 方括号

```
表示有一系列字符可供选择，只要匹配其中一个就可以了【多选1】

var rg = /[abc]/; // 只要包含有a 或者 包含有b 或者包含有c 都返回为true
console.log(rg.test('andy'));//true
console.log(rg.test('baby'));//true
console.log(rg.test('color'));//true
console.log(rg.test('red'));//false
var rg1 = /^[abc]$/; // 三选一 只有是a 或者是 b  或者是c 这三个字母才返回 true
console.log(rg1.test('aa'));//false
console.log(rg1.test('a'));//true
console.log(rg1.test('b'));//true
console.log(rg1.test('c'));//true
console.log(rg1.test('abc'));//true
----------------------------------------------------------------------------------
var reg = /^[a-z]$/ //26个英文字母任何一个字母返回 true  - 表示的是a 到z 的范围  
console.log(reg.test('a'));//true
console.log(reg.test('z'));//true
console.log(reg.test('A'));//false
-----------------------------------------------------------------------------------
//字符组合
var reg1 = /^[a-zA-Z0-9]$/; // 26个英文字母(大写和小写都可以)任何一个字母返回 true  
------------------------------------------------------------------------------------
//取反 方括号内部加上 ^ 表示取反，只要包含方括号内的字符，都返回 false 。
var reg2 = /^[^a-zA-Z0-9]$/;
console.log(reg2.test('a'));//false
console.log(reg2.test('B'));//false
console.log(reg2.test(8));//false
console.log(reg2.test('!'));//true

/^[^a-z]$/：两个^，括号外面的是便边界，括号里面的是取反的含义
```

##  符

> ```
> 词符用来设定某个模式出现的次数。
> ```

```
量词		说明

*		重复0次或更多次【>=0次】/^[a-z]*$/

+		重复1次或更多次【>=1次】【/^[a-z]+$/】

?		重复0次或1次

{n}		重复n次

{n,}	重复n次或更多次

{n,m}	重复n到m次
注意：{n,m}n和m之间不准有空格

边界符：^，$
中括号：[]：被中括号包含的东西只能选1个
量词符：*，+，?，{n,m}

```

## 用户名表单验证

功能需求:

1. 如果用户名输入合法, 则后面提示信息为:  用户名合法,并且颜色为绿色
2. 如果用户名输入不合法, 则后面提示信息为:  用户名不符合规范, 并且颜色为红色

```
var input = document.querySelector('input');
		var span = document.querySelector('span');

		var reg = /^[a-zA-Z0-9_-]{6,16}$/;

		input.onblur = function () {

			if (reg.test(this.value)) {
				span.innerHTML = '输入正确';
				span.className = 'right';
			}else {
				span.innerHTML = '错误内容';
				span.className = 'error';
			}
}
```

## 括号总结



```
1.大括号  量词符.  里面表示重复次数

2.中括号 字符集合。匹配方括号中的任意字符. 

3.小括号表示优先级

正则表达式在线测试 ： https://c.runoob.com
```

# 预定义类

```
预定义类指的是某些常见模式的简写方式.
```

<img src="D:/黑马/黑马资料/黑马资料/就业班/js高级上课资料/04_递归，拷贝，正则/笔记4/img3.png">

## 验证案例：

**手机验证**

	var tel = document.getElementById('tel');
	var regtel = /^[1][3|4|5|7|8][0-9]{9}$/;
	tel.onblur = function () {
	
		if (regtel.test(tel.value)) {
			this.nextElementSibling.className = 'success';
			this.nextElementSibling.innerHTML = '手机输入正确<i class="success_icon"></i>';
			console.log(123);
		} else {
			tel.nextElementSibling.className = 'error';
			tel.nextElementSibling.innerHTML = '手机输入错误<i class="error_icon"></i>';
			console.log(456)
		}
	
	}

**QQ验证：**

```
var regqq = /^[1-9][0-9]{4,}$/;

var regtel = /^1[3|4|5|7|8][0-9]{9}$/;
	var regqq = /^[1-9][0-9]{4,}$/;
	

	function jiance (obj, reg) {
		obj.onblur = function () {
			if (reg.test(this.value)) {
				this.nextElementSibling.className = 'success';
				this.nextElementSibling.innerHTML = '<i class="success_icon"></i> 手机输入正确';
			} else {
				this.nextElementSibling.className = 'error';
				this.nextElementSibling.innerHTML = '<i class="error_icon"></i> 手机输入错误';
			}
		}
	}

	jiance(tel,regtel);
	jiance(qq,regqq);
```

**昵称验证：**

```
var nikName = /^[\u4e00-\u9fa5]{2,8}$/;
```

**短信验证：**

```
var regmsg = /^[0-9]{6}$/;
```

## replace替换：



/表达式/[修饰符]

g：全局匹配

i：忽略大小写

gi：全局+忽略

屏蔽敏感字符

