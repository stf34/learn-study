```html
<!DOCTYPE html>
```

<!-- 声明文档类型 ，告诉浏览器按照那个版本的html解析内容-->

```html
<html lang="en">
```

<!-- lang="en" 给搜索引擎观看 -->

```html
<meta charset="UTF-8">
```

charset:字符集，utf-8：是目前最常用的字符集编码，包含所有国家需要用到的所有字符

### **命名规则：**  

头：header

  内容：content/container

  尾：footer

  导航：nav

  侧栏：sidebar

  栏目：column

  页面外围控制整体布局宽度：wrapper

  左右中：left right center

  登录条：loginbar

  标志：logo

  广告：banner

  页面主体：main

  热点：hot

  新闻：news

  下载：download

  子导航：subnav

  菜单：menu

  子菜单：submenu

  搜索：search

  友情链接：friendlink

  页脚：footer

  版权：copyright

  滚动：scroll

  内容：content

  标签页：tab

  文章列表：list

  提示信息：msg

  小技巧：tips

  栏目标题：title

  加入：joinus

  指南：guild

  服务：service

  注册：regsiter

  状态：status

  投票：vote

  合作伙伴：partner

(二)注释的写法:

  /* Footer */

  内容区

  /* End Footer */

(三)id的命名:

  (1)页面结构

  容器: container

  页头：header

  内容：content/container

  页面主体：main

  页尾：footer

  导航：nav

  侧栏：sidebar

  栏目：column

  页面外围控制整体布局宽度：wrapper

  左右中：left right center

 

  (2)导航

  导航：nav

  主导航：mainbav

  子导航：subnav

  顶导航：topnav

  边导航：sidebar

  左导航：leftsidebar

  右导航：rightsidebar

  菜单：menu

  子菜单：submenu

  标题: title

  摘要: summary

 

  (3)功能

  标志：logo

  广告：banner

  登陆：login

  登录条：loginbar

  注册：regsiter

  搜索：search

  功能区：shop

  标题：title

  加入：joinus

  状态：status

  按钮：btn

  滚动：scroll

  标签页：tab

  文章列表：list

  提示信息：msg

  当前的: current

  小技巧：tips

  图标: icon

  注释：note

  指南：guild

  服务：service

  热点：hot

  新闻：news

  下载：download

  投票：vote

  合作伙伴：partner

  友情链接：link

  版权：copyright\

## sublime常用快捷键

tab    补全代码

ctrl+shift+d         快速复制一行

ctrl+shift+k          快速删除一行

crlt+shift+↑(↓)       快速上移（下移）一行

ctrl+k+b                  隐藏(显示)侧边栏

ctrl+L                     快速选中一行

ctrl+h                         查找替换

ctrl+f                            查找

ctrl+鼠标单击                集体编辑

# HTML常用标签

##### h1标签

h1,h2,h3,h4,h5,h6,

###### 使用方法

```html
<hn>标题</hn>
```

h1:标签只能在一个页面内使用一次，不能多次使用，多次使用不符合w3c规范标准，而且不利于搜索引擎优化

## p标签内

#### 对段落样式进行改变的标签

###### 1.字体加粗    strong：使内容加粗

```html
<strong>使字体加粗</strong>
```



###### 2.字体倾斜     em：是内容倾斜

```
<em>使字体内容倾斜</em>
```



###### 3.删除字体     del：使内容删除

```
<del>将内容给删除</del>
```



###### 4.下划线        ins：对内容进行下划线

```html
<ins>对所在内容</ins>
```



###### 5.上标          sup：上标标签

```
5<sup>2</sup>
```



###### 6.下标           sub：小标标签

```html
ch<sub>2</sub>oh        
```



#### 常用标签

###### br:换行标签

```html
<br/>
```



###### hr:一条直线

```html
<hr/>
```



#### 图片标签

```html
<img src="images/gt.jpg" alt="" title="光头强" width="100" border="10" />
```



###### src="图片所在路径"

###### alt="当图片不能正常显示时显示的提示文字"

###### title="当鼠标悬停在图片上时显示的文字"

***width：***宽

###### hight：高

***当修改图片的宽和高时，只修改图片的宽和高的任意一方时，图片的大小和宽高会跟随改变的一方进行自适应的改变***

### 超链接

```html
<a href="...">...</a>
```



###### href="所跳转目标的路径或id属性"

###### target="默认值（在当前页面打开，关闭原页面）"

###### target="_blank"

###### blank   属性意思：打开一个新的页面，原窗口页面不会关闭

###### 当**base** 标签写在header里时，代表当前页面内所有超链接的使用都会打开一个新的页面，原窗口页面不会关闭

### 锚点定位

```html
<a href="index.html#top">.......</a>
```



###### 在同一页面内使用超链接通过id名的属性名跳到相应目标的位置

##### 前提锚点相对路径要正确

###### 当在跳转在别的页面时，应先跳出当前文件夹，然后寻找目标所在文件夹，然后找到目标所在文件（或目标所在文件内的锚点）方法：href="文件夹名字/文件名/页面.html#锚点名"



#### 



# 第二天笔记

# 列表

### 1.无序列表

###### ul   里不能放置任何东西，但可以放置  li，

**li**必须在父元素**ul**内，不能单独存在，**li**里可以放置任何元素或标签

```html
<ul>
		<!-- 列表项 -->
		<li>苹果</li>
		<li>草莓</li>
		<li>香蕉</li>
		<li>西瓜</li>
	</ul>
```

### 2.有序列表

###### ol   里不能放置任何东西，但可以放置  li，

**li**必须在父元素**ol**内，不能单独存在，**li**里可以放置任何元素或标签

```html
<ol>
     	<li>狗</li>
     	<li>猫</li>
     	<li>猪</li>
     	<li>候</li>
     </ol>
```



### 3.自定义列表

```html
<!-- 无序列表 -->
     <dl>
     	<!-- 小标题 -->
     	<dt>新闻</dt>
     	<!-- 对标题的解释说明 -->
     	<dd>文字</dd>
     	<dd>内容</dd>
     	<dd>图片</dd>
     	<dd>事件</dd>
     	
     </dl>
```

# 表格(table)

#### 表格的基本结构

#### table,tr,td	表格的基本结构，三者缺一不可，

**table**里只能放**tr,td**,	****不能放其他元素或标签，**tr**只能放在父元素**table**里，也是不能放其他元素，**td**里可以放置其他元素或标签

**thead**：表格头部          **tbody**：表格主题	**tfoot**：表格底部,三者也不是行，也不是列，只是为了使代码更加规范，符合搜索引擎优化

#### table里的属性，

border:  边框

cellspacing：	控制单元格与单元格之间的距离 	一般默认值：2

cellpadding:	控制内容与单元格的距离		一般默认值：1

align：	水平对齐方式	默认值：left

align="left(默认值)/center | right"	align如果用在table上时，只是控制整个表格的居中，不对表格里的内容起作用

align如果作用在tr(td)上时，可以使表格里的内容居中

caption:	表格的标题

```html
<caption>表格的标题</caption>
```

th:	对表格内的文字会自动加粗居中

```html
<table>
 	<thead>
 		<tr>
 			<th></th>
 			<th></th>
 			.....
 		</tr>
 	</thead>
 	<tbody>
 		<tr>
 			<td></td>
 			<td></td>
 			....
 		</tr>
 	</tbody>
 	<tfoot>
 		<tr>
 			<td></td>
 			<td></td>
 			.....
 		</tr>
 	</tfoot>
 </table>
```

###### 合并单元列：colspan 跨列合并

```
<tr>
<td colspan="合并列的数量">..</td>
</tr>
```

###### 合并单元行：rowspan：跨行合并

```
<tr>
<td rowspan="合并单元行的数量">...</td>
</tr>
```

# 表单

### 表单的基本结构

```html
<form>
  <input type="text">
</form>
```

表单域：form	是一个收集用户的信息和整理的集合即称为表单

###### from里的属性控件

```html
<form action="1.php" name="reg" method="get/post">
```

action	收集信息提交给数据库处理的一种方式

name	对表单起的一个名字，以便于在同一个页面内区分表单，有利于搜索引擎优化

method	设置传递信息方法的方式 一般默认为get（不是太安全）post（相对来说比较安全）

### 表单控件属性	

text	文本域	value="文本内默认的值"	maxlength="控制文本内可以输入的字符长度"	size="数字（决定文本框的宽度）"	checked="checked"	设置默认值

```html
<input type="text">
```

password	密码输入框

```html
<input type="password">
```

radio	单选框	想要实现单选，必选要name相同

```html
<input type="radio" name="man">男
<input type="radio" name="man">女

```

CheckBox	复选框  

```html
<input type="checkbox">
```

submit	提交按钮

```html
<input type="submit">
```

button	普通按钮	想要提交的话要配合JS使用

```html
<input type="button">
```

image	图片按钮	也是可以提交的

```html
<input type="image" src="图片的路径/图片的名字">
```

reset	重置按钮 	恢复到初始值

```html
<input type="reset" value="重新输入">
```

file	文件上传控件

```html
<input type="file" multiple accept='image/*'>
multiple 允许选择多个文件
accept（收受）允许选择的文件  image/* 选择所有图片 写法：.jpg .png
files  获取所有的文件
```

lable	当点击lable里的文字时，可以是input获得光标焦点

```
<lable for="id属性名">文字<input type="text" id="use"></lable>
```



### 下拉菜单

```html
<select>
<option>...</option>
<option>...</option>
    .....
</select>
```

select 	下拉菜单   	option	下拉菜单选项

selected="selected"	为默认选项	

textarea	文本域	多文本输入框

```html
<textarea cols="文本显示的列数" rows="文本显示的行数"></textarea>
```

# 查文档

经常查阅文档是一个非常好的学习习惯。

W3C :  http://www.w3school.com.cn/

MDN: https://developer.mozilla.org/zh-CN/

