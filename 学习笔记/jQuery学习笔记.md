# jQuery

### JavaScript库的概念

JavaScript开发的过程中，处理浏览器的兼容很复杂而且很耗时，于是一些封装了这些操作的库应运而生。这些库还会把一些常用的代码进行封装。

jQuery其实就是一个js文件，里面封装了一大堆的方法方便我们的开发，其实就是一个加强版的common.js，因此我们学习jQuery，其实就是学习jQuery这个js文件中封装的一大堆方法。

优点

````js
jQuery设计的宗旨是'Write Less，Do More'，即倡导写更少的代码，做更多的事情。它封装JavaScript常用的功能代码，提供一种简便的操作，优化HTML文档操作、事件处理、动画设计和Ajax交互。
jQuery的核心特性可以总结为：具有独特的链式语法和短小清晰的多功能接口；具有高效灵活的css选择器，并且可对CSS选择器进行扩展；拥有便捷的插件扩展机制和丰富的插件。jQuery兼容各种主流浏览器。
极大地简化了 JavaScript 编程。
````

## jQuery中顶级对象

jQuery中的顶级对象是$或jQuery

```javascript
获取jQuery对象
入口函数
高级功能
```

注意：jQuery中的$和JQuery关键字本身为同一对象；

## jQuery中页面加载事件

###### 使用jQuery的三个步骤：

```javascript
引入jQuery文件
入口函数
功能实现
```

###### 关于jQuery的入口函数：

```javascript
// 第一种写法
$(document).ready(function() {
	
});
// 第二种写法
$(function() {
	
});
```

###### jQuery入口函数与window.onload的对比

```javascript
JavaScript的入口函数要等到页面中所有资源（包括图片、文件）加载完成才开始执行。
jQuery的入口函数只会等待文档树加载完成就开始执行，并不会等待图片、文件的加载。
```

## jQuery对象和DOM对象的比较



* 通过原生js获取的打印的标签时DOM对象
* jQuery获取的是一个伪数组，可以用数组的方法

#### 两者之间的转换

* ###### 将jQuery对象转换成DOM对象

  ```js
  jQuery对象转换成DOM对象：   
  	jQuery对象.get(索引值); 
  	jQuery对象[索引值] 
      	jQuery对象是包装集(集合)，从集合中取数据可以使用索引的方式
  DOM对象转换成jQuery对象：   
  	$(DOM对象) 只有这一种方法;
  ```

  

## 获取页面中的元素

### jQuery基本选择器

**$("选择器")**,必须加双引号jQuery基本选择器

| 名称       | 用法               | 描述                                     |
| ---------- | ------------------ | :--------------------------------------- |
| ID选择器   | $('#id');          | 获取指定ID的元素                         |
| 类选择器   | $('.class');       | 获取同一类class的元素                    |
| 标签选择器 | $('div');          | 获取同一类标签的所有元素                 |
| 并集选择器 | $('div,p,li');     | 使用**逗号分隔**，只要符合条件之一就可。 |
| 交集选择器 | $('div.redClass'); | 获取class为redClass的div元素             |

- 总结：跟css的选择器用法一模一样。

### jQuery层级选择器

| 名称       | 用法          | 描述                                                         |
| ---------- | ------------- | :----------------------------------------------------------- |
| 子代选择器 | $('ul > li'); | 使用**-号**，获取儿子层级的元素，注意，并不会获取孙子层级的元素 |
| 后代选择器 | $('ul li');   | 使用**空格**，代表后代选择器，获取ul下的所有li元素，包括孙子等 |

- 跟CSS的选择器一模一样。



### jQuery过滤选择器

- 这类选择器都带冒号:

| 名称         | 用法                               | 描述                                                         |
| ------------ | ---------------------------------- | :----------------------------------------------------------- |
| :eq（index） | $('li:eq(2)').css('color', 'red'); | 获取到的li元素中，选择索引号为2的元素，index（**索引号**）从0开始。 |
| :odd         | $('li:odd').css('color', 'red');   | 获取到的li元素中，选择索引号为**奇数**的元素                 |
| :even        | $('li:even').css('color', 'red');  | 获取到的li元素中，选择索引号为**偶数**的元素                 |



### jQue ry筛选选择器(方法)

- 筛选选择器的功能与过滤选择器有点类似，但是用法不一样，筛选选择器主要是方法。

| 名称               | 用法                           | 描述                                                         |
| ------------------ | ------------------------------ | :----------------------------------------------------------- |
| eq(index)          | $('li').eq(2);                 | 相当于$('li:eq(2)'),index从0开始                             |
| children(selector) | $('ul').children('li')         | 相当于$('ul-li')，子类选择器，所有亲儿子                     |
| find(selector)     | $('ul').find('li');            | 相当于$('ul li'),后代选择器，包括了所有符合条件的子元素      |
| parent()           | $('#first').parent();          | 查找父元素                                                   |
| parents()          | $('#first').parents('选择器'); | 查找所有的父辈元素，选择器，获取所有父辈元素的某个指定的父元素 |
| siblings(selector) | $('#first').siblings('li');    | 查找兄弟节点，不包括自己本身。                               |
| hasClass（'类名'） |                                | 获取当前元素是否有某个类名，返回布尔类型的结果               |
| next()             | $('li').next()                 | 找下一个兄弟                                                 |
| prev()             | $('li').prev()                 | 找上一次兄弟                                                 |

## jQuery操作样式

* **隐式迭代**：偷偷的遍历，在jQuery中将数组进行遍历，不需要手动写for循环了，会自动进行遍历。

#### class操作

- 添加样式类   addClass('类名')

```javascript
// name：需要添加的样式类名，注意参数不要带点.,
$obj.addClass(name);
// 例子,给所有的div添加one的样式。
$('div').addClass('one');  //可以添加多个类名，中间用空格隔开
```

- 移除样式类  removeClass('类名')

```javascript
// name:需要移除的样式类名
$obj.removeClass('name');
// 例子，移除div中one的样式类名
$('div').removeClass('one'); //当里面不写类名时，把样式全清掉
```

- 判断是否有某个样式类

```javascript
// name:用于判断的样式类名，返回值为true false
$obj.hasClass(name)
// 例子，判断第一个div是否有one的样式类
$('div').hasClass('one');
```

- 切换样式类  toggleClass('类名')3  

````js
// name:需要切换的样式类名，如果有，移除该样式，如果没有，添加该样式。
$obj.toggleClass(name);
// 例子
$('div').toggleClass('one');
````

## jQuery动画

* ###### 1.元素的显示和隐藏 显示(show)与隐藏(hide)是一组动画：


````js
语法：
//显示(show)
☞show([speed, [easing], [fn]])   --->参数可以省略
        	1. speed : 设置动画速度（slow,normal,fast,自定义时间）
        	2. easing: 设置切换效果（默认是swing）,linear
        	3. fn ： 回调函数，在动画执行完以后执行的函数
   //隐藏(hide)
☞hide([speed, [easing], [fn]])   --->参数可以省略
        	1. speed : 设置动画速度（slow,normal,fast,自定义时间）
        	2. easing: 设置切换效果（默认是swing）,linear
        	3. fn ： 回调函数，在动画执行时候执行的函数
  //切换(toggle)    
☞toggle([speed, [easing], [fn]])   --->参数可以省略
        	1. speed : 设置动画速度（slow,normal,fast,自定义时间）
        	2. easing: 设置切换效果（默认是swing）,linear
        	3. fn ： 回调函数，在动画执行时候执行的函数
````

* ###### 滑入(slideUp)与滑出(slideDown)与切换(slideToggle)，效果与卷帘门类似

````js
//滑出(slideDown)
☞ slideDown([speed, easing, fn])
    	1. speed : 设置动画速度（slow,normal,fast,自定义时间）
        2. easing: 设置切换效果（默认是swing）,linear
        3. fn ： 回调函数，在动画执行时候执行的函数
  //滑入(slideUp)
☞ slideUp([speed, easing, fn])
    	1. speed : 设置动画速度（slow,normal,fast,自定义时间）
        2. easing: 设置切换效果（默认是swing）,linear
        3. fn ： 回调函数，在动画执行时候执行的函数
  //切换(slideToggle)
☞ slideToggle([speed, easing, fn])
    	1. speed : 设置动画速度（slow,normal,fast,自定义时间）
        2. easing: 设置切换效果（默认是swing）,linear
        3. fn ： 回调函数，在动画执行时候执行的函数
````

````
☞ 事件切换：hover(fn(), fu())
      	1. 第一个回调函数代表鼠标进入时候触发的事件（相当于mouseenter）
      	2. 第二个回调函数代表鼠标离开时候触发的事件（相当于mouseleave）
	注意：
		✔ 如果只写一个fn，那么代表同时触发鼠标进入和离开
		
☞ 动画排队效果（多次进入离开）

☞ 停止排队（stop()）: 必须写到动画前面
````

* ###### 淡入(fadeIn)与淡出(fadeOut)与切换(fadeToggle)

````js
 //淡入(fadeIn)
fadeIn([speed, easing, fn])
    	1. speed : 设置动画速度（slow,normal,fast,自定义时间）
        2. easing: 设置切换效果（默认是swing）,linear
        3. fn ： 回调函数，在动画执行时候执行的函数
  //淡出(fadeOut)
☞ fadeOut([speed, easing, fn])
    	1. speed : 设置动画速度（slow,normal,fast,自定义时间）
        2. easing: 设置切换效果（默认是swing）,linear
        3. fn ： 回调函数，在动画执行时候执行的函数
  //切换(fadeToggle)
☞ fadeToggle([speed, easing, fn])
    	1. speed : 设置动画速度（slow,normal,fast,自定义时间）
        2. easing: 设置切换效果（默认是swing）,linear
        3. fn ： 回调函数，在动画执行时候执行的函数
  
☞ fadeTo([speed, opacity, easing, fn])
    	1. speed : 设置动画速度（slow,normal,fast,自定义时间） 【必须写】
    	2. opacity: 设置透明度0-1之间  【必须写】
        3. easing: 设置切换效果（默认是swing）,linear
        4. fn ： 回调函数，在动画执行时候执行的函数
````

* ### animate: 自定义动画

````js
☞animate(params,[speed],[easing],[fn])
      1. params：要设置动画的CSS属性	【要以对象的形式设置CSS样式】
      2. speed： 动画速度("slow","normal", or "fast")或表示动画时长的毫秒数值(如：1000) 
      3. easing: 动画切换效果"linear" 和 "swing".
      4. fn: 动画完成后执行的一个回调函数
````

### 动画排队 

* stop（）让动画执行之前使用
  * 注意：以后再使用jQuery动画时，在动画前面一定要加stop（）

````js
// stop方法：停止动画效果
stop(clearQueue, jumpToEnd);
// 第一个参数：是否清除队列
// 第二个参数：是否跳转到最终效果
````



## jQuery方式操作标签的属性

###### 1.prop操作,

* 对于checked、selected、disabled这类boolean类型的属性来说，不能用attr方法，只能用prop方法。**不能获取自定义属性**

````js
// 设置属性
$(':checked').prop('checked',true);
$('div').prop('class',123);
// 获取属性
$(':checked').prop('checked');// 返回true或者false
````

###### 2.attr

* 设置一个属性

````js

// 第一个参数：需要设置的属性名
// 第二个参数：对应的属性值
$obj.attr(name, value);
// 用法举例
$('img').attr('title','哎哟，不错哦');
$('img').attr('alt','哎哟，不错哦');
// 参数是一个对象，包含了需要设置的属性名和属性值，设置多个属性，要加单双引号
$('img').attr({
    title:'哎哟，不错哦',
    alt:'哎哟，不错哦',
    style:'opacity:.5'
});
// 传需要获取的属性名称，

// 参数：需要移除的属性名，
$('img').removeAttr('title');
````

###### 3.数据缓存data（）

````js
通过该方法可以在元素身上获取值和保存值，不会修改html结构，但是如果刷新页面，之前的数据会被移除

语法：
	 jq对象.data('属性名')   		---> 获取

	 jq对象.data('属性名','值')      ---> 设置

注意：
	 如果通过data()方法获取元素的自定义属性值的时候，自定义属性名前面的 'data-'省略不写
````



#### 获取标签中的值      

* ###### 1.获取/设置表单控件中的值

  * **jQ对象.val()**   是方法   不加值是获取，加值是获取

* ###### 2.获取非表单的内容

  * **jQ对象.text()**  获取标签中的内容---->和原生js中的innerText的特点用法一样，不加值是获取，加值是设置

    ````js
    语法：
    	jQ对象.text()  		 ---> 获取标签中的文本内容，不包括html标签
    
    	jQ对象.text('值')	    ---> 设置标签中的文本内容，不包括html标签
    
    
    总结：
    	 text() 相当于原生js中的  innerText
    ````

    

  * **jQ对象.html()**  获取标签中的内容---->和原生js中的innerHTML的特点用法一样，不加值是获取，加值是设置

````js
语法：
	jQ对象.html()      ---> 获取标签中的所有内容，包括html标签
	jQ对象.html('值')  ---> 设置标签中的内容，包括html标签

总结：
	html() 相当于原生js中的  innerHtml
````

###### 3.获取和设置表单控件中的值

````js
语法：
	 jQ对象.val()			  ---> 获取表单控件中的值
	 
	 jQ对象.val('值')		 ---> 设置表单控件中的值

总结：
	 val()  相当于原生js中的   value
````



jQ对象.toFixed()  保留小数

````js
 通过  toFixed(number) 可以返回指定位数的小数，如果要保留2位小数就写2
   
````

3. 表单控件中的值发生修改，触发 change事件,获取相同的类标签        

              $(".ck1").change(function{          })

###### 遍历元素

jQ对象.each(funcution(i,item){

形参 i：代表每一个对象对应的索引值

形参 item：代表每个DOM对象

})    遍历jQuery获取的值

````js
注意： jq中默认的隐式迭代只能给元素设置相同的样式，如果需要设置不同样式需要通过遍历的方式实现

语法1：
	jQ对象.each(function(index, domElement){ });

备注：
   	1. 第一个参数代表每一个元素的索引值
       2. 第二个参数代表的是一个dom对象，不是jq对象
       3. 如果要使用jq中的方法，必须要将对象转化为jq对象
````

## jQuery节点操作

###### 创建节点

```js
// htmlStr：html格式的字符串
$('<span-这是一个span元素</span>');
```



#### 添加元素(节点)

* ###### 添加子元素 (节点)

````js
$("父元素").append(创建的元素)----->将创建的元素从末尾开始添加
$("父元素").prepend(创建的元素)----->将创建的元素从前开始添加
````

###### 添加兄弟元素(节点)

###### 元素对象.after（创建的元素）

````js
$('元素').after(创建的元素)	---将创建的元素添加到目标元素的后面
````

###### 元素对象.before（创建的元素）

````js
$('元素').before(创建的元素)  ---将创建的元素添加到目标元素的前面
````

###### 删除元素(节点)

````js
$('元素').remove()     ---- 将元素自己删除掉
    $('元素').empty()      ---- 将该元素中的所有子元素移除掉
    $('元素').html('')     ---- 将该元素中的所有子元素移除掉
    
    remove：相比于empty，自身也删除（自杀）
````

###### 克隆节点

* 作用：赋值匹配的元素

````js
// 复制$(selector)所匹配到的元素（深度复制）
// cloneNode(true)
// 返回值为复制的新元素，和原来的元素没有任何关系了。即修改新元素，不会影响到原来的元素。
$(selector).clone();
````







## jQuery大小和位置操作

###### 1.获取元素大小   设置值的时候不需要带单位

| 语法                                  | 用法                                             |
| :------------------------------------ | :----------------------------------------------- |
| width() \| height()                   | 获取元素的宽度和高度                             |
| innerWidth() \| innerHeight()         | 获取元素的宽度和高度，包含padding值              |
| outerWidth()\| outerHeight()          | 获取元素的宽度和高度，包含padding值和border值    |
| outerWidth(true) \| outerHeight(true) | 获取元素的宽度和高度，包含padding，border,margin |

###### 2.获取元素的位置

* ###### 元素对象.offset（) 

````js
语法：
  	$('元素').offset()
  
  	$('元素').offset({left: 值, top: 值})  给当前元素设置位置
  总结：
     	1. offset()是用来获取当前元素距离文档的距离，与父元素无关。
        2. offset()返回的是一个对象
````

* ###### position() 

````js
语法：
  	$('元素').position()
  
  总结：
     1. position() 返回被选元素相对于带有定位的父级偏移坐标，如果父级都没有定位，则以文档为准
     2. position() 只能获取值，不能设置值
````

## jQuery事件注册

* ###### 1.单个事件注册	缺点：不能同时注册多个事件

```js
click(handler)			//单击事件
mouseenter(handler)		//鼠标进入事件
mouseleave(handler)		//鼠标离开事件
```

* ###### 2.bind方式注册事件	缺点：不支持动态事件绑定

````js
// 第一个参数：事件类型
// 第二个参数：事件处理程序
$('p').bind('click mouseenter', function(){
    // 事件响应方法
});
````

* ###### delegate注册委托事件	缺点：只能注册委托事件，因此注册事件需要记得方法太多

````js
// 第一个参数：selector，要绑定事件的元素
// 第二个参数：事件类型
// 第三个参数：事件处理函数
$('.parentBox').delegate('p', 'click', function(){
    // 为 .parentBox下面的所有的p标签绑定事件
});
````

#### on注册事件(重点）

最现代的方式，兼容zepto(移动端类似jQuery的一个库)，强烈建议使用。

````js
// 第一个参数：events，绑定事件的名称可以是由空格分隔的多个事件（标准事件或者自定义事件）
// 第二个参数：selector, 执行事件的后代元素（可选），如果没有后代元素，那么事件将有自己执行。
// 第三个参数：data，传递给处理函数的数据，事件触发的时候通过event.data来使用（不常使用）
// 第四个参数：handler，事件处理函数
$(selector).on(events[,selector][,data],handler);
````



###### 总结:使用on给元素注册事件的有点

1，可以通过on的方式给元素注册一个事件,

2，通过on的方式给元素注册多个事件

3，通过on的方式注册事件可以实现委托的效果

````js
语法：
	$('元素').on(事件名称, function(){});   ---注册一个事件

	$('元素').on({
          事件名称: function() {},
          事件名称: function() {},
          事件名称: function() {}
    })
    ---元素注册多个事件
绑定事件，并且由自己触发，不支持动态绑定。
注意：
	如果注册的事件处理程序相同，那么可以合写：
    $('元素').on('click  mouseenter mouseleave', function(){
      // 代表当前元素在执行 click， mouseenter ， mouseleave 事件时候，执行的代码是一样的
    })
````

* ###### 通过on方式实现事件委派（委托）

````js
语法：
	$('元素').on('事件名称', '真正执行事件的子元素', function(){})
例如：
	//给ul注册点击事件，但是在执行的时候，是点击每一个li执行的点击事件，委托思想
	$('ul').on('click', 'li', function(){ console.log(123) });
````

* ###### 解绑事件

````js
语法：
	$('元素').off([事件名称],[执行事件委托元素])

注意：
   	1. 如果off()中没有设置任何参数，代表将该元素身上的所有事件都解除掉
    2. 如果要解除对应的事件，可以设置off('事件名称')
   	3. 如果要解除委托事件，可以通过off('事件名称', '执行事件的元素')
	   例如：
       $('ul').on('click', 'li', function(){}) ---> 通过委托给li注册的点击事件
  	   $('ul').off('click', 'li')  ---> 解除li委托的点击事件

   	4. 如果一个元素只执行一次事件可以通过 one('事件名称', function(){})实现
````

* ###### 自动触发事件

````js
$('元素').事件名称();
$('元素').trigger('事件类型');
例如：
	$('div').mouseenter(function(){
       $(this).css('background','pink');
    })

    $('div').mouseenter();
    $('div').trigger('mouseenter')
````

#### jQuery事件对象

```js
// screenX和screenY	对应屏幕最左上角的值
// clientX和clientY	距离页面左上角的位置（忽视滚动条）
// pageX和pageY	距离页面最顶部的左上角的位置（会计算滚动条的距离）

// event.keyCode	按下的键盘代码
// event.data	存储绑定事件时传递的附加数据

// event.stopPropagation()	阻止事件冒泡行为
// event.preventDefault()	阻止浏览器默认行为
// return false:既能阻止事件冒泡，
```

* ###### 元素滚动事件scroll

  * scrollTop() 垂直距离，滚动出去的距离
  * scrollLeft（）水平距离，滚动出去的距离

````js
  语法：
  	$('元素').scrollTop()    设置|返回元素内容区域滚动出去的垂直距离
    $('元素').scrollLeft()   设置|返回元素内容区域滚动出去的水平距离
  
  总结：
     1. 元素滚动事件scroll
````

* jQuery拷贝对象

````js
希望将一个对象拷贝给另外一个对象使用
语法：
	$.extend([deep], target, object1, [objectn])
注意;
   	1. deep，默认值是false，浅拷贝。true代表深拷贝
	   浅拷贝，如果遇到复杂数据类型，是将复杂数据类型的地址拷贝给目标对象的
       深拷贝，拷贝的就是对象，没有拷贝地址
    2. target，要将对象拷贝给哪个对象
 
    3. object1,当前要被拷贝的对象
````

2. ##### jQuery多库共存

```js
为了避免其他js文件中和jQuery文件中的 '$'符号冲突

方式一：
	使用 jQuery 替代 '$'

方式二：
 用户完全自定义
var  test = jQuery.noConflict();
		 test.each()
```

3. ##### 

## 插件

### 常用插件

- 弹出层插件 layer
  - [layer插件](https://github.com/sentsin/layer)
- 放大镜插件
  - [jQuery.zoom](http://www.jacklmoore.com/zoom/)
- 轮播图插件
  - [http://sorgalla.com/jcarousel/](http://sorgalla.com/jcarousel/)
  - [https://github.com/OwlCarousel2/OwlCarousel2](https://github.com/OwlCarousel2/OwlCarousel2)
- 图片懒加载插件
  - [jQuery.lazyload](https://github.com/tuupola/jquery_lazyload)
- jQueryUI
  - 常用的2-3个功能演示
- 查看jQuery插件的源码

- artDialog](https://github.com/aui/artDialog)
- [图片放大](https://github.com/fat/zoom.js)
- [github上搜索](htt

````js
   1. 瀑布流插件   ( http://www.htmleaf.com/  )
   2. 懒加载插件: EasyLazyload (http://www.jq22.com/jquery-info11629)
   3. 全屏滚动插件 (https://browser.360.cn/ee/)
	（ gitHub： https://github.com/alvarotrigo/fullPage.js
中文翻译网站： http://www.dowebok.com/demo/2014/77/）

jQuery 插件库  http://www.jq22.com/     
````

1. ##### JSON.stringify()  转化为json格式的字符串

2. ##### JSON.parse()  将json格式的字符串转化为对象

3. ##### 删除数组中的值 ary.splice(startindex, length)；