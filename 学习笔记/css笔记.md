# css基本链接样式

### 1.行内样式

```html
<p style="color:red; font-size:30px;">....</p>
```

​		不推荐使用，样式和结构相混，容易搞混

### 2.内嵌样式

```html
<head>
    <style>
     div{
         font-size:30px;
         color:blue;
        }
    </style>
</head>
<body>
    <div>
    我又来了
	</div>
</body>

```

 	内嵌样式：一般都控制当前页面的标签，当写一个页面时可以使用，样式不太多时

### 3.外链样式

```html
<head>
  <link href="CSS文件的路径"  rel="stylesheet" />
</head>
```

外链样式：都是结构和样式分离，控制整个站点，推荐使用

# 选择器

### 1.标签选择器

例如：

```html
div,p,hr,span.....
```

### 2.类选择器

```html
<head>
    <style>
        .box{
            color:red;
            font-size:40px;
        }
    </style>
</head>
<body>
    <div calss="box">
        我是类选择器
    </div>
</body>
```

类选择器：

1.可以被多个标签使用，一对多， 也可在一个标签内多次使用

2.谁调用，谁生效，

3.命名规范：不能用数字或以数字开头来命名，也不推荐使用中文命名，也不能使用特殊字符命名，		**（-_）**可以当做链接符使用

### 3.id选择器

```html
<head>
    <style>
        #box{
            color:red;
            font-size:30px;
        }
    </style>
</head>
<body>
    <div class="box">
        w我又来了
    </div>
</body>
```

### 4.通配符  

```html
<style>
    *{
        color:red;
    }
</style>
```

# 字体样式

### 1.字体大小

```html
font-size:30px;
```

### 2.字体

```html
font-family:字体名字;
```

1.中文字体使用单引号

2.多字体时，用逗号隔开，英语字体应该写在中文字体前面

###### 3.Unicode编码

1.在网页内使用f12，打开控制台（console），然后输入escape("中文字体名称")，然后回车，得到编码

2.然后把%u替换成\,最终得到Unicode编码，使用单引号

### 3.字体

```html
font-wight:bold;
```

字体默认值：100-900

normal   不加粗			加粗	bold

### 4.文字风格

```html
<style>
 font-style:italic;
</style>
```

###### 常用字体样式设置font-style: italic

兼容各大浏览器

normal : 正常的字体(默认字体样式，可用于去掉html i斜体标签默认斜体样式)

italic : 斜体。对于没有斜体变量的特殊字体，将应用oblique

oblique : 倾斜的字体

### 5.字（母）与字（母）之间的距离或单词之间的距离

####  letter-spacing:			word-spacing

#### 6.line-hegith：行间距

设置行与行之间的间距

### 7.综合设置

```html
选择器{font: font-style  font-weight  font-size/line-height  font-family;}
```

# css外观属性

### 1.color：文本颜色

  1.16进制，如#FF6600   0-900

 2.rgb()  红蓝绿基本颜色组合

### 2.首行缩进

```html
text-indent：2em;
```

### 3.水平对齐方式

```html
text-align:left(默认值）|right（向右）|center（水平居中）;
```

只能让盒子里的内容水平居中，不能让盒子居中，对盒子不起作用

## text-decoration 文本的装饰

text-decoration   通常我们用于给链接修改装饰效果

| 值           | 描述                                          |
| ------------ | --------------------------------------------- |
| none         | 默认。定义标准的文本。 取消下划线             |
| underline    | 定义文本下的一条线。下划线 也是我们链接自带的 |
| overline     | 定义文本上的一条线。                          |
| line-through | 定义穿过文本下的一条线。                      |
|              |                                               |

# css复合选择器  

### 后代选择器

```html
.box p span{
			color: blue;
			font-style: italic;
		}
```

*后代选择器 ，发生前提是嵌套关系
		1.父元素在前，子元素在后，用空格链接
		2.可以为限制的隔代选择
		3.只要代表父元素，子元素，后代选择器可以是任意选择器的组合
	*/

### 子代选择器

```html
.box > span{
			color: red;
			font-size: 30px;
		}
```

/*子代选择器
			选择的是父元素的亲儿子，对他的无效，用 > 链接在一起，父在前，子在后，可以是任意选择器的组合
		*/

### 交集选择器，

```html
p.box{
			color: red;
		}
```

/*交集选择器，既有标签又有类选择器*/

### 并集选择器

```html
.box,p,h3{
			font-size: 34px;
			font-style: italic;
		}
```

/*并集选择器
			样式全部相同，或部分样式相同的选择器，可以通过逗号连在一起，进行集体的声明

# 	

# css显示样式与伪类元素

### 2.块级元素

典型代表：div，p ,ul,dl,ol,li,form,h1-h6....等

###### 块级元素特点：

1.可以设置宽和高

2.不设置宽时，默认继承父元素的宽，不设置高时，一般默认为0，当里面有内容时，会被内容给撑高

3.独占一行



### 3.行内元素

典型代表： a,p,span,em,del,ins...等

###### 行内元素特点

1.不可以设置宽和高

2.在一行内显示

3.行内元素的宽和高一般默认为零，但里面有内容时会撑开行内元素

4.当行内元素代码换行时，会产生缝隙

### 4.行内块级元素

典型代表：img，input , textarea...等

###### 行内块元素特点

1.在一行内显示

2.可以设置宽和高

3.当代码换行时，也会产生空隙

### 5.块级，行内，行内块元素的转换	display:..;

1.行内转化为块级元素		block

2.块级元素转化为行内元素	inline

3.块级，行内转化为行内块级元素	inline-block

### 6.伪类元素

：link		一般为默认		可以不写

：visited	超链接访问之后的状态	

：hover	鼠标悬停在目标元素上的变化

：active	鼠标停留在目标上之后，按住鼠标左键不动显示的状态

一般下面不设置宽和高时，下面会自动继承上面的

###### 鼠标样式改变：

```js
cursor其他取值  
auto                    ：标准光标  
default                 ：标准箭头  
pointer, hand                   ：手形光标  
wait                     ：等待光标  
text                      ：I形光标  
vertical-text          ：水平I形光标  
no-drop                ：不可拖动光标  
not-allowed           ：无效光标  
help                     ：帮助光标  
all-scroll         ：三角方向标  
move                     ：移动标  
crosshair           ：十字标  
e-resize  
n-resize  
nw-resize  
w-resize  
s-resize  
se-resize  
sw-resize
```

### 7.背景	background:

1.背景颜色		background-color:

2.背景图片		background-image：url("背景图片的路径")

3.背景平铺		background-repeat：

​	1.默认值  	repeat  铺满盒子（沿着x轴和y轴）

​	2.repeat-x	沿着x轴（水平方向）平铺

​	3.repeat-y	沿着y轴(垂直方向)平铺

​	4.no-repeat	不平铺	

4.背景的定位	background-position：

​	1.方位词	left 	center	right	top(上)	bottom（下）

​		1.当写方位词时，水平（垂直）和水平（垂直）不能写在一起	水平和			垂直可以随意组合	

​		2.当写一个方位词时，另一个方位词默认为center

​		3.当写数值时，是以x和y轴排布的，当写一个数值时，另一个数值默认为      			center

​		4.数值和方位词混合时，

​			1.当第一个写方位词时，是以水平方向为准，也只能写水平方向的方			位词，right，left，center

​			2.当 第二个写方位词时，是以垂直方向为准的，也只能写垂直方向词			top ，bottom ，center

5.背景的附着和属性的连写

背景覆着	background-attachment

   1.默认值	scroll   背景图不会跟着滚动条滚动

   2.背景图像固定	fixed 	将背景图片固定，不会跟着文字的滚动而滚动

  3.注意，当使用固定（fixed）时，定位时，所参照的对象，不是父盒子，而是整个浏览器的位置

6.背景属性的连写

​     background：背景颜色  背景路径  背景是(否)平铺	背景滚动	背景的位置；

```
background: #ccc url(images/3.jpg) no-repeat scroll center center;
```

# 标签的嵌套规范

1.块级元素可以嵌套任意元素，可以嵌套行内元素，行内块级元素	div可以嵌套任意元素，但注意一点，

2.p标签不能嵌套块级元素，但可以嵌套行内元素，行内块级元素

3.标题不推荐嵌套块级元素，但可以嵌套，行内元素，行内块级元素

4.行内元素可以嵌套，行内元素，不能嵌套块级元素，行内块级元，

5.行内块级元素可以嵌套行内元素，行内块元素，不能嵌套块级元素

6.a标签不能嵌套a标签

# css的三大特性

### 1.css层叠性

多个样式作用与统一样式时，如果发生冲突，前提是权重相同时，后面的样式给覆盖掉，使用就近原则，和样式的顺序无关

### 2.css的继承性

子元素会继承父元素的一些相应样式(text- ,font- ,line- 这些元素开头的都可以继承，以及color属性)	文字类

但a标签不会继承颜色

标题不会继承父元素的文字大小

### 3.css的优先级

优先级是一种解决样式冲突的能力，权重大的先执行，优先级低的不执行

权重的比较

标签（0,0,0,1）<  类选择器（0,0,1,0）<  id选择器（0,1，0，0）<   行内样式（1,0，0，0）   <  ！important（无穷大）

### 权重的叠加

继承的权重是0

1.如果子元素没有样式的时候，会继承父元素的样式，子元素和父元素发生冲突时，永远执行子元素自身的样式

2.从父元素继承来的样式权重是零，但如果选择器（样式）继承在元素的本身时，权重会叠加的

3.如果选择器的（样式），作用到父元素时，对于元素本身来说，权重就是为零的

### 总结：权重是优先级的算法，层叠是优先级的表现

# 盒子模型

盒子模型由	外边距（margin），内边距（padding），内容  边框组成

### 1.边框	border

​	1.边框的线性	solid   实线

​					dashed	虚线

​					double	双实线

​					dotted	点线

######       2.边框的连写 	border：像素 线性  颜色； 

```html
border : border-width || border-style || border-color ;
```

###### 	3.表格边框的合并	

```html
border-collapse: cellapse;
```

​          1.只适用于表格，用于边框的合并   border-collapse

  	2.高度剩余法，给外面的盒子设置高度，盒子里的内容默认为左顶对齐，盒子		剩下的高度，就是内容与下面内容的垂直高度

             3.   ：focus     伪类，要和input配合使用，作用，当获取焦点时，背景色的改变
             4.   清除边框    border:none(0);             清除轮廓线        outline:none(0);

### 2.内边距     padding     内容区域距边框的距离

###### 1.padding   的连写   

```html
padding：20px；
```

 	1. 写一个值 ，代表上下左右
 	2. 写两个值，第一个值代表上下，第二个值代表左右
 	3. 写三个值 ，第一个值代表上，第二个值代表左右，第三个值代表下 
 	4. 写四个值，分别代表上下左右

###### 2.padding不撑大盒子的问题

​	1.块级元素如果不设置宽度的时候，给其设置左右内边距，则不会撑开盒子宽度

​       2.块级元素设置了宽度，设置左右内边距，则必然会撑开盒子

​	3.行内元素，行内块元素，只要设置内外边距，就必然会撑开盒子

​	4.只要设置上下内边距，则必然会撑开盒子

注意   行内元素，只能设置左右的内外边距，不能设置上下的内外边距

### 3.外边距   margin    盒子距父元素的距离

​	1.外边距实现元素居中，  margin（只对设置宽度的块元素起作用，）    块元素只有在设置宽度的时候，使用margin：0 auto；水平居中（对脱离标准流的元素不起作用）

###### 4.text-align和margin的区别

​	1.*text-align: center; 可以使块级元素里的内容（文字，行内元素，行内块元素）水平居中*/
​			/*text-align: center; 可以使行内块级元素里的内容（文字，行内元素，行内块元素）水平居中*/
​			/*text-align: center;  对行内元素无效*/

###       外边距的合并

###### 	1.垂直方向相邻外边距的合并

​		但两个相邻块元素相遇时，当同时使用外边距时，那么两个盒子之间垂直的距离，取最大值来确定 ，也就是相邻块元素的垂直外边距的合并

###### 	2.嵌套块级元素垂直外边距得合并

​		对于两个嵌套元素来说，如果父元素没有内边距或边框，则父元素会和子元素的外边距发生合并，合并后取最大值，作用与父元素上

######                 解决方法:

​		1.可以给父元素加一像素的边框或一像素的内边距

​		2.给父元素加上 overflow：hidden；（溢出隐藏）触发BFC，块级格式化上下文，使父元素成为独立的布局区域，不会受外部因素的干扰

### 边框的圆角      border-radius

当连写时，他的取值范围是和内外边距的取值顺序相同的

### 盒子的阴影     box-shadow

###### 阴影的连写       box-shadow：0,0,0,0，#red;

​	1.第1个值，阴影的水平偏移，正值向右，负值向左

​	2.第2个值，阴影的垂直偏移   正值向下   ，负值向上

​       3.第3个值，阴影的模糊范围

​	4.第4个值，阴影的大小

​	5.第5个值，阴影的颜色

###### 注意：阴影默认值是外阴影	在一面加inset是内阴影

### 浮动的特点

```html
1.浮动会脱离标准流的控制，不在占据原来的位置
	2.浮动可以使（块）元素在一行内显示
	3.浮动只能浮动到父元素的左边或右边，受到父元素内边距的控制
	4.浮动元素顶对齐，代码换行，没有缝隙
	5.浮动元素不会影响上边的标准流里的块元素，只会影响下边的
	6.浮动元素有了行内块的显示特点，
		1.块元素浮动之后，不会默认父元素的宽度了。默认高为零，内容撑开盒子
		2.行内元素浮动之后，就可以设置宽高了
	7.当文字，行内元素，行内块元素，遇到浮动元素时，不会跑到浮动元素下面，只会环绕浮动元素	
	8.浮动的元素掉下来，是因为子元素的宽度相加，超过了父元素的宽度
	   浮动的子元素不设置宽度，被里面的内容撑开，不会超过父元素的宽度
```



# 清除浮动

为什么要清除浮动：

######      清除浮动就是为了解决父元素不能设置高度, 浮动的子元素撑不开父元素高度的问题

###### 额外标签法

```html
<div style="clear=both;>
    
</div>
```

在浮动元素的末尾添加一个空的标签

缺点：添加许多无意义的标签，结构化较差，不推荐使用

###### 添加overflow属性方法

可以通过触发BFC的方式，实现清除浮动的效果

优点：代码简介，但缺点是内容增多时，不会换行，会把溢出的内容给隐藏掉

###### 使用伪元素清除定位      before和after双伪元素   给浮动的父元素添加 清除浮动

：：before前伪元素

```css
.clearfix:after {  content: ""; display: block; height: 0; clear: both; visibility: hidden;  }   

 .clearfix {*zoom: 1;}   /* IE6、7 专有 */
```

::after后伪元素

```css
.clearfix:before,.clearfix:after { 
  content:"";
  display:table;  
}
.clearfix:after {
 clear:both;
}
.clearfix {
  *zoom:1;
}
```

# 定位

### 相对定位   position:relative;

特点：

1.相对定位，不会脱离标准流，还会占据原来的位置

2.相对定位的偏移对象是相对于自身的

### 绝对定位  position：absolute；

特点：

1.脱离标准流，不占据原来的位置，

2.绝对定位，如果父元素没有定位，那么元素的偏移位置是基于浏览器的

3.如果父元素有定位的话，那么元素的偏移对象是基于离自己最近的父元素的

4.绝对定位有了行内块的显示特点

  1.不会继承父元素的宽高，默认宽高会变成零，但如果里面有内容，内容会撑开盒子

2.行内元素可以设置宽和高，

###### 注意：遵守   子绝父相

​	1.子元素绝对定位，父元素相对定位，那么子元素的偏移是基于父元素，父元素不脱标，还占据原来的位置，下面的盒子顶不上来，所以布局正常

### 固定定位 position：fixed;

1.完全脱标，不占位置  (如果不设置top和left值的，会在原来的位置进行脱标)

2.固定定位的元素位置偏移基于浏览器的可视窗口

3.固定定位的元素有了行内块元素的显示特点

​	固定定位的块元素不会默认父元素的宽度，高度也会默认为零，当然内容会撑开盒子，当然固定定位的行内元素就可以设置宽和高了（当设置百分百的宽度时，这个宽度，这个宽度是默认浏览器的可视窗口的宽度）

### 定位元素的堆叠顺序

z-index的特性如下

1.属性值：可为正数，负数，0 ，不能为小数，数值越大，层级越高

2.如果属性相同，则按照书写顺序，后来居上

3，数字后面没有单位

###### 注意：z-index 只能应用于相对定位，绝对定位，固定定位，对其他标准流，浮动和静态定位无效

### 元素的显示和隐藏

display：none；  隐藏对象之后，不会占据原来的位置

visibility:hidden;	对象隐藏，隐藏之后还会占据原来位置

###### overflow：溢出处理

1.visible  溢出可见

2.scroll   不管内容是否溢出都会生成滚动条

3.auto  内容溢出生成滚条，不溢出则不生成

4.hidden 溢出隐藏

###### 禁止文本域拖拽	resize:none;

###### 单行文本省略号的实现			共分三步

1.white-space：nowrap；		强制文本在一行内显示

2.overflow：hidden；溢出隐藏

3.text-overflow：ellipsis;   溢出省略号

###### 清除图片与文字的缝隙	vertical-align:middle;

1.top  顶对齐

2.middle  垂直居中对齐

3.bottom 底对齐

###### 占位符

placeholder   占位符，当输入内容时，占位符消失，删除输入的内容，占位符出现

# 过渡

语法：transition: 要过渡的属性  花费时间  运动曲线  何时开始;
如果有多组属性变化，还是用逗号隔开。

| 属性                       | 描述                                         | CSS  |
| -------------------------- | -------------------------------------------- | ---- |
| transition                 | 简写属性，用于在一个属性中设置四个过渡属性。 | 3    |
| transition-property        | 规定应用过渡的 CSS 属性的名称。              | 3    |
| transition-duration        | 定义过渡效果花费的时间。默认是 0。           | 3    |
| transition-timing-function | 规定过渡效果的时间曲线。默认是 "ease"。      | 3    |
| transition-delay           | 规定过渡效果何时开始。默认是 0。             | 3    |

如果想要所有的属性都变化过渡， 写一个all 就可以

transition-duration  花费时间  单位是  秒     s    比如 0.5s    这个s单位必须写      ms 毫秒

运动曲线   默认是 ease

 何时开始  默认是 0s  立马开始

```css
div {
			width: 200px;
			height: 100px;
			background-color: pink;
			/* transition: 要过渡的属性  花费时间  运动曲线  何时开始; */
			transition: width 0.6s ease 0s, height 0.3s ease-in 1s;
			/* transtion 过渡的意思  这句话写到div里面而不是 hover里面 */
  
			
}
div:hover {  /* 鼠标经过盒子，我们的宽度变为400 */

			width: 600px;
			height: 300px
}

transition: all 0.6s;  /* 所有属性都变化用all 就可以了  后面俩个属性可以省略 */
```



# 2D动画

###### transform   变换转换的意思，可以实现元素的位移，旋转，倾斜，缩放甚至也可以支持矩阵方式，配合过渡和动画使用

######  translate（x,y)   移动元素	移动平移的意思

​	1.translate可以使文字或图像水平方向和垂直方向分别移动

​	2.x,y的值可以是正值或负值

​	3.translatex	仅水平方向移动（沿着x轴移动）

​	4.translatey	仅垂直方向移动（沿着y轴移动）

```css
/**数值单位：可以是像素，也可以是百分数**/
translate（50px,50px);
```

###  让定位的盒子水平居中

```css
.box {
  width: 499.9999px;
  height: 400px;
  background: pink;
  position: absolute;
  left:50%;
  top:50%;
  transform:translate(-50%,-50%);  /* 走的自己的一半 */
}
```

###### 缩放scale（x,y)	transform:scale(x,y) 里面是倍数

​	默认值 为1 当倍数为小于1 的小数时，是缩小，当大于1时，是让元素扩大

旋转  rotate（数值deg）	deg(角度）正值为顺时针，负值为逆时针

###### transform-origin	可以调整元素转换的原点

1，可以用数值，也可以用方位名词

倾斜 skew（deg,deg) 	可以让元素按一定角度进行倾斜，可为负值，当只写一个参数时，另一个参数默认为0

# 3D旋转	transform

1.坐标方位

 x左边是负的，右边是正的

y 上面是负的， 下面是正的

z 里面是负的， 外面是正的

###### 2.rotate  旋转

1.rotateX（）沿着X轴旋转

2.rotateY（）沿着Y轴旋转

3.rotateZ（）沿着Z轴旋转

###### 3.透视	perspective	透视原理： 近大远小 。 值越小反应就越激烈

1.perspective 一般设置给body，作用与所有元素，当不给body设置，给上下级设置时，那么只控制设置元素的亲儿子

###### 4.translate3d(x,y,z) 

1.[注意]其中，x和y可以是长度值，也可以是百分比，百分比是相对于其本身元素水平方向的宽度和垂直方向的高度和；z只能设置长度值

###### 5.backface-visibility  定义当元素不面向屏幕时是否可见

# 动画	animation

语法格式：

```css
animation:动画名称 动画时间 运动曲线  何时开始  播放次数  是否反方向;
```

### 动画的实现：

```css
@keyframes 动画名称 {
  from{ 开始位置 }  0%
  to{  结束  }  100%
}
```

# css布局

## 样式初始化

- 国产移动浏览器基本以 webkit 内核为主，因此我们就考虑webkit兼容性问题。
- normalize.css：
  - http://necolas.github.io/normalize.css/
  - 保护了有价值的默认值；
  - 修复了浏览器的bug；

###### 1.盒子模型

```css
/*传统模式：盒子的宽度=css的内容区域+border+padding*/
box-sizing:content-box;
/*css3盒子模型：盒子宽度：就是设置的宽度，不会受到padding和border的影响，且这个宽度也包含了padding值和border值*/
box-sizing:border-box;
```

​    使用场景：一般适用于一边宽度固定，另一边随意拉伸的布局

### 1.流式布局

  	使用百分比进行布局，使用的场景比较传统，可以通过百分比来控制盒子的宽度

## 语法	适配

```html
<meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
```

###### 	width=device-width***：让HTML的宽度 = 屏幕的宽度；

### 流式布局-backgroud-size

语法：

```css
      /* 1.两个参数控制背景图的大小 :按照设置进行显示，有可能失去比例*/
      /* background-size: 500px 100px; */
      /* 2.一个参数:高度省略，会自适应 */
      /* background-size: 200px; */
      /* 百分数： 相对于当前盒子的宽度*/
      /* background-size: 100%; */


      /* cover: 覆盖，绝对不留白 */
      /* background-size: cover; */

      /* contain：包含，绝对把图显示全*/
      /* background-size: contain; */
```



# flex布局

###### 1.display:flex;布局，

只要使用flex布局，那么不管子元素是否是块级元素，都可以设置宽和高了，另外flex布局只对亲儿子有效

###### 2.flex-direction:row;	确认主轴的排列方式，	沿着主轴方向排列

​	1.默认值为	row 选择水平方向，从左到右排布

​	2.row-reverse	选择水平方向	从右到左排布

​	3.column（常用属性）	选择垂直方向 	从上到下排列（行排布变列排布）

​	4.column-reverse	选择垂直方向 	从下到上排列（行排布变列排布）

###### 3.justify-content	整理版面	控制主轴元素的对齐方式

​	1.默认值	flex-start	从头步开始排布

​	2.flex-end   	从尾部开始排布

​	3.content	居中排布（如果主轴是X轴，水平排布，否则垂直）

​	4.space-around	平分空间，剩余空间围绕子元素周围排布

​	5.space-between	先两边贴边对齐，然后平分剩余的空间

###### 4.控制主轴上的元素是否换行	flew-wrap  默认值	nowrap不换行

​	1.如果不换行，那么就算在主轴上排布的子元素再多，也只会进行合理的压缩排布

​	2.wrap	换行	子元素的宽度大于父元素时，就会换行显示

###### 5.flex-flow  	复合属性：设置主轴与换行

###### 6.align-items 	该属性是控制子项在 侧轴上的排列方式，在子项为单项（单行）的时候使用

​	1.flex-start	默认值 从侧轴的开头对齐

​	2.flex-end	从尾部开始对齐

​	3.center	垂直居中对齐

​	4.stretch	拉伸	只能在侧轴上拉伸，前提（子元素的宽或高不做设置，才能拉伸）

###### 7.align-content 设置侧轴子元素多行的排列方式，前提是要先换行

​	1.flex-start    从侧轴头部开始对齐

​        2.flex-end    从侧轴尾部开始对齐

​        3.content    从侧轴中间开始对齐

​        4.space-around    平分侧轴上的剩余空间（空间环绕子元素）

​        5.space-between    先分布在两头，在平分侧轴上的剩余空间

# rem布局

rem布局，最为直观的效果，页面全部元素等比缩放，包括文字，盒子大小等

###### 语法：root:   1rem=HTML的font-size大小；

​	特点：绝对的唯一控制；

```css
/* 1.根html 为 15px */
html {
   font-size: 15px;
}

/* 2.此时 div 的宽就是 100px */       
div {
    width: 10rem;
}
```

# 媒体查询

- 作用：响应屏幕的变化；
- 该可以根据屏幕不同的宽，从而获得不同的样式，然后实现不同的样式显示；

## 语法

- CSS3 新语法，是一个查询屏幕的过程，通过查询当前屏幕尺寸属于**哪个范围**，从而有**哪个范围**的样式生效；
- `mediatype  (media feature)` 都是它的查询条件

```css
@media mediatype and|not|only (media feature) {
    CSS-Code;
}
```

- mediatype：媒体类型；查询不同的终端设备 ； screen最为常用：查询当前设置的屏幕；
- and|not|only：关键字；将多个条件连接在一起共同查询；
  - **and**：可以将多个媒体特性连接到一起，相当于“且”的意思；最为常用；生活中：“我既要娶白富美，又要走上人生颠覆”；
  - not：排除 某个 媒体类型，相当于“非”的意思，可以省略。生活：“我喜欢看电影，除了恐怖片”；
  - only：指定某个特定的 媒体类型，可以省略。    生活：“我这辈子非你不嫁”；
- (media feature)：媒体特性；

  - 对于屏幕 screen，屏幕的宽度就是一个特性；

- 查询条件加小括号；

- min-width/max-width：最小界值，最大界值；查询条件包含等于号；

  # less

  ## 介绍

  - Less（Leaner Style Sheets 的缩写）是一门 CSS 扩展语言，它扩展了CSS的动态特性。 CSS 预处理器。
  - 常见的CSS预处理器：Sass、Less、Stylus 。
  - **预处理器**是[程序](https://baike.baidu.com/item/%E7%A8%8B%E5%BA%8F)中处理输入数据，产生能用来输入到其他程序的数据的程序。
  - Less中文网址：[http://](http://lesscss.cn/)[less](http://lesscss.cn/)[css.cn/](http://lesscss.cn/)
  - less : 让你写更少的代码，实现相同的效果；

  ## 变量

  - 变量是指没有固定的值，可以改变的。
  - 我们CSS中的一些颜色和数值等经常使用，可以设置为变量；
  - 语法：

  ```less
  //@变量名:值;
  @bg:#333;
  .box_1 {
    background-color: @bg;
  }
  
  .box_2 {
    background-color: @bg;
  }
  ```

  - 命名规则：
    - 必须有@为前缀
    - 不能包含特殊字符~=+、不能以数字开头
    - 大小写敏感区分；

  ## 嵌套

  - 类似HTML一样写LESS结构；
  - 语法：

  ```css
  /* css 写法 */
  #header .logo {
    width: 300px;
  }
  
  /* less 写法 */
  #header {
    .logo {
        width: 300px;
    }
  }
  ```

  - 交集|伪类|伪元素选择器，语法：

  ```css
  /* css写法 */
  a:hover{
      color:red;
  }
  
  /* less写法 */
  a{
    &:hover{
        color:red;
    }
  }
  ```

  

  ## 运算

  - 任何数字、颜色或者变量都可以参与运算。
  - Less提供了加（+）、减（-）、乘（*）、除（/）算术运算。
  - 语法：

  ```less
  // 数字
  width: 200px - 50;
  
  // 颜色
  background-color: #666 - #222;
  
  // 变量
  @border: 5px;
  border: @border solid red;
  
  // 注意：运算符中间左右有个空格隔开 1px * 5
  ```

  - 单位选择：
    - 如果两个值之间只有一个值有单位，则运算结果就取该单位
    - 对于两个不同的单位的值之间的运算，运算结果的值取第一个值的单位 

  