

# WebAPI

介绍：学习BOM和DOM的属性和方法

* API:封装好的对象属性和方法
* BOM:浏览器对象模型，把整个浏览器看成一个对象

###### 01--DOM:文档对象模型，把整个页面看成一个对象

* 获取DOM节点

* Element:元素节点

* ById:通过节点上的ID获取DOM节点

* onclick：响应用户点击的行为

* 匿名函数：用户点击后的效果

  ```js
   // var btn = document.getElementById("btn").onclick = function() {
      //     alert("我被点了");
      // };
      // body 因为页面中只有一个，所以可以直接点击
      // var stn = document.body;
      // style 获取到对象
      // 业务逻辑
      // 点击的是谁?
      // 发生什么行为？
      // 点击之后发生什么？
      var btn = document.getElementById("btn").onclick = function() {
          document.body.style.backgroundColor = "#333";
      };
  ```

  # 操作属性-style

**style属性：**

- ###### style属性里面的内容其实是多个**键值对**，js帮我们把它们以对象的方式管理起来；
- ###### 获取：只需要  `元素对象.style.样式属性名` ；如果样式属性名是多个单词的，需要把样式属性的`-` 去掉，修改为驼峰命名；

### 02--注册事件 focus聚焦，blur模糊

语法：

````js
ipt.onfocus = function(){
  // 当你想要让鼠标光标在输入框里面的时候要做什么事，就使用这个事件即可
}

ipt.onblur =  function(){
  //当你希望处理鼠标光标失去的时候所做的事情，就在这里做
}
````

事件类型：

* 有光标时：获得光标焦点 focus
* 无光标时：失去光标焦点 blur

### 案例：搜索区显示隐藏

- 业务：
  - 有光标时，搜索区显示
  - 无光标时，搜索区隐藏
- 步骤：
  - 获取元素：文本框
  - 注册事件：focus blur
  - 事件后：搜索区的显示隐藏；

```js
// 1 获取元素
var search = document.getElementById('search');
var list = document.getElementById('list');
// 2 注册获得焦点的事件
search.onfocus = function(){
  // 把搜索历史显示 - 通过修改display属性 - 元素.style.display = 'block';
  list.style.display = 'block';
}

// 2 注册失去焦点事件
search.onblur = function(){
  // 把搜索历史隐藏 - 修改display为none
  list.style.display = 'none';
}
```

### 03-操作类样式-

###### 1.className 

* 效果：可以修改或添加我们已经写好的类名；更快的更换样式

````js
// 获取节点类名，用className，将原来的类名覆盖改变
        // box.className = box.className + " bg-red";
````

###### 2.classList 

DOM元素对象的一个对象属性，有多个方法进行操作，比**className**能更好的解决上面的覆盖问题

* add：给元素对象添加一个或多个类名，不会影响原来的类名

````js
//参数：多个类名用逗号隔开
        box.classList.add("bg-red");
````

* remove：给元素删除一个或多个类名

````js
//参数：多个类名用逗号隔开
        box.classList.remove("bg-red");
````

* toggle：切换类名,

````js
//如果有相同类名就删除，没有就添加
box.classList.toggle("bg-red");
````

## 04---获取元素对象 ByTagName

* 根据标签名获取元素

````js
//参数：tagname-标签名-必须是字符串（加双引号）
///返回值：一个数组（伪数组），里面包含所有满足条件的元素
//因为是伪数组所以可以循环遍历
document.getElementsByTagName(tagname);
````

## 05--获取元素对象 		ByClassName

- 根据类名获取元素

```js
//参数：classname-标签名-必须是字符串（加双引号）
///返回值：一个数组（伪数组），里面包含所有满足条件的元素
//因为是伪数组所以可以循环遍历
document.getElementsByClassName(classname)
```

## 06---操作自定义属性

* 标准属性：html标准中出现的，有特殊功能的属性：id，class，href,src,title,value...;
* 自定义属性：开发者根据自己需求，把数据写在标签上时使用的属性。可以自己命名

````js
  // 自定义属性：开发者按照自己的需要，把一些数据写在标签内，属性名
 // 自定义属性的命名规范：date—属性名（自己命的名字）
 // 使用场景：把数据与数据之间---的对应关系，写入自定义属性里
 // 获取：以 data- 开头的自定义属性，都存储在了 元素.dataset 这个对象里面
  img.src = this.dataset.src;
````

## 07--操作标准属性-checked

* 开关属性：checked/selected/disabled(禁用)，这种只有两种状态的属性；

* 赋值：两个状态的值，布尔类型；


## 08---获取元素对象 选择器 ！！！

* 语法：
  * query-查询
  * Selector-选择器
  * All-所有-全部

* document.querySelector(css选择器)；
  * 作用：根据指定的选择器获取一个元素
  * 参数：css选择器
  * 返回值：根据选择器得到第一个满足条件的元素，如果有就是元素，如果没有 就是null

````js
 // css选择器（id名，css名，类名）来选择对象，中间以逗号隔开
    var btn = document.querySelector(".cv");
````

* document.querySelectorAll("选择器1"，"选择器2"，..)
  * 功能：根据选择器获取所有满足条件的元素
  * 参数：多个选择器中间用逗号隔开，（都是字符串）
  * 返回值：为伪数组。可以循环遍历，获取所有符合条件的对象

````js
var stn=document.querySelectorAll("li");
````

## 09---操作属性的方法

* ###### 元素.getAttribute（属性名）

  * 作用：根据属性名获取属性值
  * 参数：要获取的属性名
  * 返回值：字符串，就是你想要获取的属性的值

````js 
box.getAttribute("box");
````



* 元素.setAttribute(属性名，属性值)
  * 作用：添加或者修改属性的值
  * 参数：属性名，属性值

````js
box.setAttribute("xa",34);
````

* 元素.removeAttribute(属性名)
  * 作用：删除某个**属性***

````js
box.removeAttribute("sd");
````

## 10---注册事件  addEventListenner

* 元素.addEventListenner(事件类型，事件处理程序)
  * 作用：注册事件--注册事件有很多种说法：绑定事件，监听事件，添加事件句柄....
  * 参数：事件类型-字符串       事件处理程序-function       返回值：undefined

````js
    // 先获取按钮
    var btn = document.getElementById("btn");
    btn.addEventListener("click", function() {
        console.log(123);

    })
    btn.addEventListener("click", function() {
        console.log(345);

    })
````

## 11---事件对象

* 什么是事件对象？根据面向对象的思想——万物皆对象，把一次事件也看成对象——什么是对象？属性和方法的集合

* 事件对象：就是一个对象，里面还有方法和属性 就是要学习这个对象里面的方法和属性

* 要使用事件对象，先得到

  * 得到事件对象的方式：

  *  在事件处理程序里面写一个形参，就可以得到事件对象

  *  事件源.on+事件类型 = function(事件对象){   }
  * 事件源.addEventListener(事件类型,function(事件对象){});

````js
// 获取时间对象
事件源.on+事件类型 = function(事件对象){   }

事件源.addEventListener(事件类型,function(事件对象){});
````



* #### 鼠标事件

  * click：点击
  * mousedown：当鼠标的按键被点下的时候触发
  * mousemove：鼠标在某个元素上移动时触发
  * mouseup：当鼠标的按键弹起时松开时触发

###### 事件对象属性：

```js
/ 鼠标位置

// 可视区域坐标系 - 以浏览器的可视区域的左上角为原点的
// 可视区域：就是元素用来显示内容的区域
事件对象.clientX
事件对象.clientY

// 页面坐标系  -  以body(页面）的左上角作为原点
事件对象.pageX
事件对象.pageY


// 事件的目标对象，用户点击到谁上面了；
事件对象.target
//： nodeName （就是获取父元素里面的所有子元素）里面就是 大写的标签名
//当获取的子元素的符合条件时，执行代码
    if(e.target.nodeName === 'li'){
      // 点击的就是li - 就执行代码
      console.log('li被点击了');
    }
// 事件的绑定对象，就是是绑定在哪个DOM节点上 和 this一样
// 前面说的事件源
e.currentTarget==this -----> true
//阻止
// 阻止冒泡
事件对象.stopPropagation();

// 阻止默认行为；
事件对象.preventDefault();


```

## 12---获取元素位置

* 上面学习的鼠标的位置，通过事件对象
* 元素对象的位置：获取到的是数值

````js
// 得到的是某个元素距离他的offsetParent元素的水平距离
// 元素.offsetLeft = marginLeft + left
元素.offsetLeft 

// 得到的是某个元素距离他的offsetParent元素的垂直距离
// 元素.offsetTop = marginTop + top
元素.offsetTop 

// 找到一个有定位的父亲元素，如果亲生父亲没有定位，会一直往上找，直到找打有定位的父亲，或者body；
元素的offsetParent
````

## 13--解绑事件

- 事件解绑：事件无效；
  - 希望曾经注册了的事件，在触发之后，无法执行对应的事件处理程序了；
  - 事件触发的时候，把事件解绑。那么下次你再次点击的时候，就无效了。

```javascript
var btn = document.getElementById('btn');
btn.onclick = function(){
  btn.onclick = null;
  console.log('谢谢惠顾');
}

var btn = document.getElementById('btn');
btn.addEventListener('click',function fn(){
  // 解绑 当前的函数
  btn.removeEventListener('click',fn);
  console.log('抽奖了');
})
```



## 14---创建节点

* ###### 属性：innerHTML，可以获取标签内的HTML结构，也可以设置HTML结构

````js
  var ul = document.querySelector('ul');
  var btn = document.getElementById('btn');
  btn.onclick = function () {
    // 给ul添加新的元素
    var old = ul.innerHTML;
    old += '<li>新的li</li>'
    ul.innerHTML = old;
  }
````

###### innerText 获取或设置DOM节点内的文本信息，不具备解析HTML结构；获取标签类的，表单（带光标的不能获取）

* document.write();

* value 属性可设置或者返回文本域的 value 属性值。

* document.createElement();          根据指定的标签，创建的DOM节点，只是在js里面显示，但不在页面里显示，是需要手动添加的

  ````js
   var li = document.createElement("li");
      // 从后面添加DOM节点，要先指定一个父级DOM，然后传入
      ul.appendChild(li);
  ````

## 15---添加DOM节点

* appendChild:给一个父元素，追加子元素，作为最后一个元素，从后面添加
* insertBefore 在某个子元素之前，添加新的元素

````js
    // 从后面添加DOM节点，要先指定一个父级DOM，然后传入
    ul.appendChild(li);
    // 从前面添加，需要指定在谁前面添加
    // 参数：第一个是添加的节点，第二个参数是在谁前面添加
    ul.insertBefore(属性1，, 属性1);
````

## 16---根据DOM节点 获取 DOM节点

* 父元素.children	获取父元素下的所有子元素，组成一个集合（伪数组）
* 元素.parentNode     获取父元素
* 提取兄弟元素
  * 元素.nextElementSibling----得到下一个兄弟元素
  * 元素.previousElementSibling----得到上一个兄弟元素

## 17---删除DOM节点

````js
// 父元素.removeChild(要删除的子元素);

var first = ul.children[0];
// 调用方法，移除
ul.removeChild(first);
````



## 冒泡排序

## 18---事件三个阶段

### 捕获与冒泡

- 事件发生的时候，存在这三个传播的阶段：**捕获、到达目标、冒泡；**

- **客观存在事情：**需要记住

  - 捕获：从根部节点往目标DOM节点上，一层一层的找，捕获到用户点击了那个DOM节点；
  - 冒泡：从目标节点到根节点；
  - 冒泡阶段执行：**事件默认是在冒泡阶段执行；**当我们目标DOM节点注册了事件，冒泡往上的DOM节点也注册了同样的事件话，也会执行；

  ![img](E:\学习文件\黑马\黑马学习\就业班练习\就业班笔记\自己笔记\学习笔记\images\1557457360104.png)

- 语法设置：控制事件的执行阶段：

````js
// 捕获阶段执行
  yeye.addEventListener('click', function() {
    console.log('我是你爷爷');
  }, true);
  baba.addEventListener('click', function() {
    console.log('我是你爸爸');
  }, true);

  erzi.addEventListener('click', function() {
    console.log('我是你儿子');
  }, true);


  // 冒泡阶段执行
  yeye.addEventListener('click', function() {
    console.log('我是你爷爷');
  }, false);
  baba.addEventListener('click', function() {
    console.log('我是你爸爸');
  }, false);
  erzi.addEventListener('click', function() {
    console.log('我是你儿子');
  }, false);
````

- 为什么默认是冒泡阶段执行？
  - 用户点击一个孙子元素，站在用户的角度想，
  - 更为人性化的角度是用户看见的第一个弹窗或者反应是用户点击了当前的那个元素，
  - 至少用户知道自己点击对了；
  - 再出现其他反应，也没有关系，但至少用户知道自己第一次点击对了；
  - **上面这个事件执行过程是在冒泡阶段执行**的解释；
  - **但如果是默认是捕获阶段执行，**
  - 从根部到目标元素，一个一个元素执行注册的事件，
  - 若是从根部到目标元素有1万个节点，每个都注册事件，
  - 那用户得等很久，才能看到用户点击的那个元素，**体验不好**。
  - 所有这就是为为什么**默认是冒泡阶段执行？还是归结于用户的体验上；**



### 阻止冒泡

- 为什么要阻止继续冒泡？
  - 当父亲们辈的同样注册了相同的事件，事件默认是在冒泡阶段执行；
  - 所有注册的相同的事件都会执行；
  - 但是，**用户只想点击当前的有反应就行，上面的不需要再执行了。**
- 你希望在哪里阻止，就在哪个事件处理程序里面调用即可；**在函数里面的前后位置无所谓；**
- Propagation：传播；阻止冒泡是阻止父亲们辈的事件执行，不是阻止自己执行；

```javascript
// 要阻止冒泡，需要先得到事件对象，给处理程序添加一个形参就行
erzi.addEventListener('click',function(e){
  // 调用阻止事件冒泡的方法进行阻止
  
  // 事件对象 e 把该次点击这个行为看成一个对象
  e.stopPropagation();
  console.log('我是你儿子');
});
```

# BOM

* BOM:是把浏览器看成是一个对象，就是学习浏览器对象的各种方法和属性；
* 浏览器对象：**window对象**（顶级对象）

## window对象

* 特点：
  * 所以window对象的属性和方法，**都可以直接省略window，而直接使用**
  * 被称为**顶级对象**页面中所有的东西都是依赖于这个对象存在
  * 在js代码里面，不声明变量的话，都是隐式全局变量

## onload

* 页面加载完毕的时候执行

* 等页面所需的静态资源全部加载完毕

* 静态资源：**html文件，css文件，js文件，图片...**

  ````js
  window.onload = function(){
      // 想要获取图片的宽高，就需要等待图片加载完成后才执行后面的函数；
  }
  ````

  

## 定时器

* 一次性定时器  setTimeout    一次性定时器

  * 参数：

    * 第一个参数，是等待一段时间后执行的代码

    * 第二个参数，让等待的时间  毫秒                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           

      ````js
      var time = setTimeout(function() {
              alert("我又变帅了");
          }, 3000);
          var btn = document.querySelector("#btn");
          btn.onclick = function() {
                  clearTimeout(time);
              }
              // clearTimeout(返回值)停止定时器
      ````

      

  * setInterval：永久定时器

    ````js
    // 永久定时器
            // 参数：第一个参数，等待一定时间执行的函数体
            // 第二个参数，等待多久的时间  毫秒
        var time = setInterval(function() {
            console.log("我是小可爱");
    
        }, 1000);
        btn.onclick = function() {
            clearInterval(time);
        }
    ````


#### location

* location：负责管理浏览器地址栏相关的行为和信息的对象
* 属性：location.href :属性：该属性就是浏览器的地址栏里面，如果地址改变了，那么网页也就改变了

````js
// 如果想要使用js进行跳转，只需要 location.href = 新的地址;
location.href = 'http://www.jd.com';
````

## localStorage和JSON

* localStorage  是个对象，方法 

  * 设置本地浏览器 存储  本地：代指浏览器

  ###### setIem()；存储

````js
// 存储 设在存上一条数据
// 后面的值 前面可以放入任何数据类型，保存后为字符串
// 注意： 如果存储的是对象之类的复杂类型，需要先把复杂类型转换为JSON格式的字符串，再存进去，因为本地存储只能存储字符串
localStorage.setItem(键,值);
 // 参数： 第一个参数是键，key
    // 第二个参数，是值
````

######                 getItem():  读取数据

````js
//读取数据
// 返回值：就是我们存入的的数据的值
localStorage.getItem(键);
 // 如何读取本地数据
    // 返回的值是字符串
    // 传入参数，就是要查询的键的名称
````

###### 		removeItem();	删除本地数据

````js
// 删除本地数据
    // 传入参数，要删除的键的名称
    // localStorage.removeItem("name");
````

###### 		clear();	全部清空

````js
// 全部清空
    localStorage.clear();
````

######     当获取不存在的键时，返回的值是null

## JSON

- 以前：我们想要存储数据到字符串里面，一般会使用这样的格式：

```js
数据1指定分隔符数据2指定分隔符...

李狗蛋|12|男&翠花|13|女&铁柱|14|男
```

- JSON格式：[] - 表示数组；{} - 对象；和JS学习的对象，数组特别的像；
  - 但是JSON是**有一定格式的字符串**
    - 所有的键必须使用双引号包起来
    - 字符串也必须是双引号
    - 只有数字和字符串两种类型
    - 只是复制记录数据的，是不具备行为的
- 方法：我们自己转json格式比较麻烦；js提供了JSON方法，里面封装好了很多跟json操作相关的方法

```js
// 将对象转换为json格式的字符串
// 返回值：一个满足json格式的 字符串
JSON.stringify(对象)

// 将json格式的字符串转换为对象
// 返回值：依赖于你的json格式字符串，可能返回数组，或者是对象....
JSON.parse(json格式字符串)
```

## 事件：onkeydown,onkeyup

* 键盘事件

  * 按键按下：keydown
  * 按键弹起：keyup

  ###### * e.keyCode==13 回车键,e.ctrlKey ctrl键

## 事件：

## 1.(鼠标移入）:onmouseover或onmouseenter，

## 2.onmouseout（鼠标移出）

````js
<div class="box" index=0></div>

// 鼠标移入时触发
var box = document.querySelector('.box');

// 对象属性，
box.a = 0;

// 鼠标移入触发：
box.onmouseover = function() {
    // 获取自定义属性
    this.getAttribute("index");
    
    // 添加节点对象属性，随便添加；
    console.log(this.a);
}

// 鼠标移除时触发
dom.onmouseout = function(){ 
}
````

#### 滚动事件：onscroll    只要出现滚动天，就会触发

* ###### scrollTop：滚动时卷入的高度

## BOM方法：获取DOM节点样式

````js
// Computed：计算后的样式
// 返回值： 当前作用在这个元素身上的所有样式的集合对象  BOM的方法；
// 属性：具体的属性 无论是行内的还是CSS样式设置的，都可以获取到；字符串
var res = window.getComputedStyle(元素对象)；
res.width 

// 只能操作行内属性；
var dom = document.getElementById('xx');
dom.style.color；
````

#### 属性：获取元素的实际宽度和高度

* ###### 元素的实际宽高=border+padding+content（width和height）

  ````js
  // 返回值：数值；
  
  // 只能进行获取；
  // 元素的实际宽度
  元素.offsetWidth 
  // 元素的实际高度
  元素.offsetHeight
  
  // 获取和设置
  dom.style.width；
  ````

  

* ###### 元素的可视区域的宽和高

  * 元素.clientWidth--可视区域的宽度
  * 元素.clientHeight--可视区域的高度

# 动画结束事件

- 动画结束事件：专门是指c3里面的动画结束会触发的事件，c3动画有两种，结束动画事件也有两个；
- transitionend：元素的过渡动画结束的时候触发；

- 

```js
var box = document.querySelector('.box');
box.addEventListener('transitionend',function(){
  console.log(123);
});
```

- animationend：会在帧动画结束的时候触发

```js
var box = document.querySelector('.box');
box.addEventListener('animationend',function(){
  console.log(123);
})
```

- 注意：
  - 不能使用on的方式注册，只能使用addEventListener的方式注册
  - 如果帧动画是无限次的，不会触发该事件