# 1.Node.js核心内容

* NodeJS 就是一个 没有界面的 可以 运行 JS代码的 软件
  + 内置了 谷歌 的 V8引擎 -- 高效率的 执行 JS代码
  + 内置 模块 - 就是 写好的 JS代码 --类似于 jquery.js

![](D:\黑马\黑马学习\就业班练习\就业班笔记\自己笔记\学习笔记\images\1568023622167.png)

## 4. 服务端.js & 客户端.js



### 4.1 客户端.js（浏览器中的js）

+ **浏览器端** JS分 三个部分：
  + ECMAScript ：语法 -- 声明变量，条件语句，循环语句，函数，对象，数组，自定义类型
  + DOM：操作页面上的 元素(标签对象)  document.getElementById('div1');
  + BOM：操作 浏览器  window.open('')     window.close();.....

### 4.2 服务端.js（Node.js）

+ **服务端** JS 只有 ECMAScript (ES5 , ES6)

## 5. Node.js 程序运行

>  执行方式 有两种： REPL环境 （很少使用）  和  直接执行JS文件

## Node.js基本概念

> 基于chrome v8引擎的 javascript运行环境
>
> 服务端的js

官网: https://nodejs.org/en/ 

中文网: http://nodejs.cn/ 

1. 浏览器中 有一个可以解析 js的 解析器
   1. 解析器:(翻译官)
      1. 把编程语言  翻译为计算机可以识别的 二进制
      2. js---(翻译官v8引擎)->计算机执行
   2. chrome的js解析器(翻译官),v8引擎 目前世界上最快的,js解析器
2. js运行环境:
   1. 通过`node.js`也可以直接运行`js`代码
3. 这个阶段的js代码很大一部分,不需要通过浏览器运行,直接敲命令即可

## Node.js安装

下载地址: https://nodejs.org/en/ 



一直下一步:即可

打开黑窗 

```bash
node -v
```

## js组成

1. 浏览器端:
   1. ECMAScript:js语法,for循环,if else,var...
   2. DOM(文档对象模型):
      1. 约定了操纵dom元素的语法
      2. `dom.style.width`样式中的宽度
      3. `dom.onclick`事件绑定
      4. `dom.appendChild`追加后代
      5. ....
   3. BOM(浏览器对象模型):
      1. 操纵浏览器的语法
      2. `window.alert()`
      3. `window.location.href`
      4. `window.setTimeout`
      5. ....
2. 服务器端(没有浏览器):
   1. ECMAScript:js基础语法,for循环,if else,var....
   2. 学习了bom语法中的一些常用api
      1. `定时器,console 等等`
   3. 模块(类似于之前用的jQ,swiper...)
      1. 内置模块:自带的
      2. 第三方模块:别人写的,下载才可以使用

## Node.js 基本使用-REPL(了解)

1. 打开黑窗
2. 输入`node`回车
3. 写`js代码` 回车运行
4. 循环`步骤3`

REPL

read(读取) eval(解析) print(打印) loop(循环)

用的不多,了解即可,跑一些简单的代码

## Node.js 基本使用-执行js文件

1. 写好一个`js文件`
2. 内部有`node.js`支持的代码
3. 打开黑窗输入`node 文件名` 回车
4. 运行



注意

1. 文件名不能写错,写错提示找不到
2. 文件名不需要打全,写个开头 +`tab`自动提示
3. 黑窗打开的位置 和`js`在一个文件夹下
4. 语法不要写错
5. 路径确保和js文件一致
6. 文件名不要叫`node.js`
7. 报错查看 

在vscode中打开终端

右键文件->在终端中打开->输入命令运行即可

关闭终端的快捷键

ctrl+`   1左边的那个按钮

# ES6

### var的缺点：

* 变量提升
* 没有块级作用域{
* 可以重复声明

### let:变量，var的替代品，使用方法基本和var相同

* 没有变量提升了
* 有块级作用域，只用{}就可以让其变成块级作用域
* 不能重复声明

````js
//a.么有变量提升
console.log(lover); // lover is not defined
let lover = 'Linda';

//b.不能重复声明 同名 变量
let a = 1;
let a = 2; // 报错：Identifier 'a' has already been declared
console.log(a);

//c.有 块级作用域
if(true){
   let num = 100;
}
````



### const常量

* const 声明 常量 -- 主要用来 保存一些 程序的初始信息，程序启动后 不允许修改

* 特点：
  + 常量无法重新赋值 -- 一旦声明并设置好初始值，之后就不能够被改动
  + 常量只能也必须在 创建时赋值（常量初始化）
  + 无法变量提升
  + 有块级作用域
  + 无法重复声明
* 常量 应用场景
  + a.保存 整个程序的 核心配置 数据，一般 使用 常量来保存 -- 因为程序 无法修改
  + b.在 nodejs 中  加载 模块时，一般 使用 常量来保存 模块对象
* 小结：凡是 在程序中 不需要 经常修改的 数据，就应该使用 常量 -- 圆周率

* 常量命名规范
  + 所有字母用大写

````js
const MAX_REQUEST = 100;
// 1. 常量无法重新赋值
// const age1 = 100;
// age1 = 101; // 常量 一旦赋值，不能改变！
// console.log(age1);

// 2. 常量只能也必须在 创建时赋值
// const age2; //报错： Missing initializer in const declaration
// console.log(age2);

// 3. 无法变量提升
// console.log(age3); // 报错： age is not defined
// const age3 = 1;

// 4.有 块级作用域
// if(true){
//   const num4 = 100;
// }
// console.log(num4); // 报错：   num is not defined

// 5.无法重复声明
// const num5 = 1;
// const num5 = 2; // Identifier 'num' has already been declared
````



const和let   **注意：**能用const ，不用let,能用let 不用var 

### 对象属性的简化写法：

###### 注意：属性名要和值的名相同

语法：

````js
const name='xioa';
const obj={
    name,
    jum(){
        console.log('系哦啊可爱');
        
    }
};
console.log(obj.name);
obj.jum();
````

### 模板字符串

* 注意：轻量级模板引擎，原生支持，不用导包
* 可以换行，定义时使用``
* 语法${`表达式`}
* 简单的可以使用，复杂的还是要有模板引擎的

语法：

````js
const name='小老鼠';
const age={
    name:'小老鼠',
    chaodai:'现代'
}
const obj=`
  打油诗    
  作者${age.name}
  来自${age.chaodai}
床前明月光，
阿超喝鸡汤。
喝了几大碗，
半夜尿一床。
`;
console.log(obj);
````

###    函数默认值

* 参数=默认值
* 不传递参数直接使用默认值，如果传递就使用传递的参数 

````js
// es6中的默认值
// 参数=默认值
// 不传递参数直接使用默认值,传递了参数使用传递的值
function sayHi(name='路飞',skill='橡胶果实') {
    console.log(name,skill);
}
// sayHi();
sayHi('索隆','迷路');
````



### 对象解构`使用频率挺高的`

````js
// 定义对象
const person = {
    name:"食戬(jian)之灵",
    desc:"美食番,教你做饭",
    spec:"食物越好吃,衣服就越少"
}
// const name = person.name;
// const desc = person.desc;
// const spec = person.spec;

// 解构赋值
// skill undefined 上面没有定义
// const par={name,desc,spec,skill} = person;
//console.log(par);
// 也可以只获取某一些
const {name} = person;
````



### 对象解构结合函数

* 如果参数很多，一般建议通过对象的方式传递

1. 函数的参数解构
   1. ![1571803973215](D:/黑马/黑马资料/黑马资料/就业班/node.js上课资料/Node.js-Day01/01-教学资料/assets/1571803973215.png)
   2. 实际调用时会有更多的提示
2. 函数的参数解构结合默认值

```javascript
function eatFood({food1="西兰花炒蛋",food2="西红柿炒蛋",food3="韭菜炒蛋",food4="黄瓜炒蛋"}) {
    console.log(food1,food2,food3,food4);
}
```



### 数组解构

* 获取的顺序，和数组的元素对应关系是一致的
* 数组大部分时候都是通过下标获取某一个的

````js
// 数组
const cartoonArr = ['喜洋洋','熊出没','铁甲小宝','天线宝宝','海绵宝宝','中华小当家'];

// 取值
// const c1 = cartoonArr[0];
// const c2 = cartoonArr[1];
// console.log(c1,c2);

// 解构
// 获取的顺序 和数组的的元素的对应关系是一致
// 数组大部分时候都是通过下标获取某一个
// 数组的解构用的 不多 了解即可
const [c1,c2,c3,c4,c5,c6] = cartoonArr;

console.log(c1,c2,c3,c4);
````



终端

* 多个终端的区别
  * 终端可以理解为是一个没有界面的软件，通过输入内容让他干事情
  * `cmd`微软早期推出的，功能最少，不太好用
  * `git bash` 安装了`git`之后自带的,功能强大,支持很多`cmd`没有的命令,`linux`的命令也基本上都支持
  * `power shell`:微软后续退出的终端,功能牛逼很多,但是还是比`git bash `支持的命令少一些

### 对象展开

###### 写在前面的同名属性会被覆盖

* 结合运算符`...`可以吧方法给整个带过来

````js
const obj={
    name:'牛肉',
    name1:"狗肉",
    name2:"羊肉",
    name3:"驴肉"
}
const obj1={
    name:"鸡肉",
    ...obj
}
console.log(obj1);
````



### 数组展开

````js
const obj=['牛肉','羊肉','狗肉','驴肉'];
const obj1=['鸡肉',...obj];
console.log(obj1);

````

* 数组不会出现覆盖问题,索引会依次向后

### 箭头函数

* 省略function变为=>
* 如果形参`只有一个`，可以省略`小括号`
* 如果函数体`只有一行`，可以`省略大括号`
* 如果函数体`只有一行`，并且有`返回值`
  * `省略大括号`的同时，必须省略`return`

````js
// 普通函数
// const obj=function (){
//     console.log('你好吗，小老鼠');

// }
// obj();
// 省略函数
// // 省略function
// const obj= () =>{
//     console.log('你好吗，小老鼠');

// }
// obj();
// // 省略小括号
// const obj = name => {
//     console.log('你好吗，小老鼠');

// }
// obj('猫咪');
// 省略大括号
const obj = name => console.log('你好吗，小老鼠');

obj('猫咪');

// 省略return
const obj = name => name+'你好吗，小老鼠';


const res=obj('猫咪');
console.log(res);
````

###### 注意：普通函数，无法用箭头函数的方式化简，箭头函数用来化简匿名函数

### 箭头函数中的this

* 指向，在创建时就确定了。是上下文（和他平级的环境中）的this

  ![1571964810782](D:\黑马\黑马学习\就业班练习\就业班笔记\自己笔记\学习笔记\images\1571964810782.png)

1. 可以通过 `babel`的工具把高级的js代码翻译成低版本的js,查看内部的实现套路
2. babel传送门: https://www.babeljs.cn/ 



## Node.js - 内置模块

> 脱离了浏览器的限制,通过内置模块可以实现很多在浏览器中干不了的事情哦

官方文档: http://nodejs.cn/ 

## Node.js - fs模块基本使用

文档地址: http://nodejs.cn/api/fs.html 

1. 文件基本读写会用即可
2. `const fs = require('fs')`
3. `fs.readFile`
4. `fs.writeFile`，有三个参数，1.路径，编码，回调函数

````js
const fs = require('fs');
//读文件 readFile  有三个参数
//第一个参数: 要读取文件的路径
//第二个参数: 编码格式
//第三个参数: 回调函数
//回调函数里也有2个参数
//err 错误信息, 没有错误是null
//data就是读取的内容
````



## Node.js - 第三方模块

1. 官方的网站(包,模块管家的搜索界面): https://www.npmjs.com/ 
2. 找包 官方的包检索网站`npm`
3. 下包:模板的网页中有命令`npm i xxx`
4. 导包:文档中也有
5. 用包
6. 文档中都可以找到



## 终端命令

* 清屏的命令在小黑窗中输入`cls`

* 用来切换路径

  ````bash
  cd 路径
  cd ../
  cd 文件夹
  ````

  

## Node.js中的相对路径

````js
// console.log("我是代码");

// 导入fs require： 需求
const fs = require('fs');

// 读取文件
// node.js中的相对路径 相对的谁
// 1. 当前这个js文件
// 2. 终端中的路径 小黑窗中所处的路径

fs.readFile('./novel/01.txt','utf-8', (err,data)=>{ 
    if(err==null){
        console.log(data);
    }else{
        console.log('错啦');
        console.log(err);
    }
 })
````

### 两个与路径相关的全局变量

* 结合这两个全局变量就可以动态的生成绝对的路径，避免把路径给写死
* 也是node.js的推荐写法
* 全局变量不需要定义，直接就可以使用,**不用加引号**

````js
__dirname  //js文件所在文件夹的绝对路径
__filename  //js文件的绝对路径
````

## Pata模块基本使用

* 作用：专门用来处理路径的模块
* 文档传送门:http://nodejs.cn/api/path.html

````js
path.extname('info/nal/01.txt');   //获取文件的扩展名 .txt
path.dirname('info/nal/01.txt');   //获取路径中文件夹的部分info/
path.join(路径1,路径2,路径3....);    //把多个路径拼接到一起，保证格式正确
````

​	**重点**：`path.join`

````js
// 导入模块 fs require 需求
const fs = require("fs");
// 导入模块 path
const path = require("path");
// __dirname 文件所在文件夹的绝对路径
const fullpath = path.join(__dirname, './noval/1.text');
// console.log(fullpath);
// 读取文件
fs.readFile(fullpath, 'utf-8', (err, data) => {
    if (err == null) {
        console.log(data);
    }else{
        console.log(err);
        console.log('错了');
        
    }
})
````

1. `\`转义符 需要注意
2. `path.join(路径1,路径2)`不要写成 字符串拼接`+`
3. 使用绝对路径的目的是`保证一定可以获取到文件`

## http模块创建服务器

* 作用：通过他的几行代码就可以创建服务器了
* 使用步骤
  * 导包（内置模块，http）
  * 调用`createServer`的方法创建服务器对象
  * 开启服务器（监听端口）listen

概念解释:

` http://192.168.156.95:8848/ `

```
http://  协议: http模块开启的服务是http服务访问的时候带上 `http://`
192.168.156.65:ip地址,电脑在当前这个局域网中的ip地址 
打开黑窗 输入 ipconfig 
:8848  端口号
```

端口:

​	电脑和外部通讯的一个通道

1. 物理端口:
   1. usb口
   2. 网线口
   3. 耳机口
   4. hdmi(显示器,投影仪)
   5. ...
2. 虚拟端口:电脑中的软件和外部通讯的通道
   1. 只要和外部通讯的软件,都会使用某一个虚拟端口
   2. 一个号而已`0开始递增`
   3. 虚拟端口很多
   4. 前`10000`很多都被用了 
   5. 靠后的一般都可以使用,一些比较另类的也没有使用
   6. `8848,8888,4399,3000`
   7. 端口一次只能被一个程序使用

## http模块-服务器交互流程

````js
// 导包  http
const http=require('http');
// 创建服务器   request 需求，请求  response 响应 反应
const server=http.createServer(function(request,response){
    response.end('nice to meet you'); //什么都不加，只能响应英文
})
// 开启服务器      listen 监听
// 参数1 端口号
// 参数2 监听的地址 省略的话就是本机,
// 参数3 开启之后的回调函数
server.listen(8886,function(err){
    if (err==null) {
        console.log('开启成功了');
        
    }else{
        console.log('一不小心失败了');
````

#### 响应中文需要额外设置响应头，在`response.end`之前调用

* `response.setHeader`设置编码格式，这样浏览器就可以解析中文了

````js
// 导包  http );
    // content-type 内容类型
    // text/plain 普通模本  
    // charset=utf-8' 编码格式
    response.end('你好啊，小老鼠');
})
// 开启服务器      listen 监听
server.listen(8886,function(err){
    if (err==null) {
        console.log('开启成功了');
        
    }else{
        console.log('一不小心失败了');
        
    }
})
````

**注意**：

* 设置header的代码不能乱写
* 每次改变内容都要从开终端，可以输入`Ctrl+c`,不要选择内容

http模块--请求url

* 请求可以携带信息，那么怎么获取这些呢、
* 可以在回调函数中通过`request.url`获取在url中的信息
* request请求的意思
  * 可以把请求的信息都保留在这个对象中
  * url就是请求的地址

* 如果url中有中文，可以通过`decodeURL()`进行转码

````js
// 导包  http
const http=require('http');
// 创建服务器   request 需求，请求  response 响应 反应
const server=http.createServer(function(request,response){
    // 打印获取的内容
    console.log(decodeURI(request.url));
    // 中文解码
    decodeURI(request.url)
    // 解决中文乱码
    response.setHeader('content-type','text/plain;charset=utf-8');
    // content-type 内容类型
    // text/plain 普通模本  
    // charset=utf-8' 编码格式
    response.end('你好啊，小老鼠');
})
// 开启服务器      listen 监听
server.listen(8886,function(err){
    if (err==null) {
        console.log('开启成功了');
        
    }else{
        console.log('一不小心失败了');
        
    }
})

````

## http模块--根据url响应不同的内容

* 将写死的内容，写活，可以根据url响应的不同而返回不同的结果

* 好处：如果想要修改用户看到的页面，只需要修改也免得代码即可

* 也不需要从新开启服务器

  

## http模块 - 静态资源服务器

作用

1. 开启服务之后，可以通过浏览器输入`http://地址:端口`访问
2. 如果输入的地址后面还更有网页，可以读取对应的文件并返回
3. 如果请求的是`css`,`js`,`img`也可以正常返回
4. 读取文件是，不要设置编码格式为`utf-8`



## 静态资源服务器 - 访问注意

1. 保证 js文件同级目录下有一个`web`文件夹，内部有网页
2. vscode每次 右键打开终端，会新建一个小黑窗
3. 快速访问自己的服务器
   1. http://localhost    本机
   2. http://127.0.0.1     本地回环地址
4. 让同局域网的人访问必须通过本机`ip`才可以

## http模块 - 获取请求的方法

1. `request.method`获取请求方法
2. 结合请求地址的判断，可以自行不同的逻辑
3. 更为复杂的逻辑，不太适合用原生的编写，比较繁琐

## express - post数据获取（普通文本）

> 通过express的`中间件` 获取post提交的文本数据

传送门: https://www.npmjs.com/package/body-parser 

1. 中间件是一个特殊的第三方模块
2. 必须结合`express`才可以使用
3. 类比为`jQuery`插件

![1572075812290](D:/%E9%BB%91%E9%A9%AC/%E9%BB%91%E9%A9%AC%E8%B5%84%E6%96%99/%E9%BB%91%E9%A9%AC%E8%B5%84%E6%96%99/%E5%B0%B1%E4%B8%9A%E7%8F%AD/node.js%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/03express%E5%9F%BA%E6%9C%AC%E4%BD%BF%E7%94%A8/01-%E6%95%99%E5%AD%A6%E8%B5%84%E6%96%99/assets/1572075812290.png)

使用步骤·

1. 下包
2. 导包
3. 用包

```javascript
// 导入express
const express = require('express');
// 导入body-parser 第三方模块（中间件）
const bodyParser = require('body-parser')

// 创建服务器对象
const app = express();

// parse application/x-www-form-urlencoded
// 解析 application/x-www-form-urlencoded 这种格式的数据
app.use(bodyParser.urlencoded({ extended: false }))

// 注册路由
app.post('/add',(request,response)=>{
    console.log(request);
    response.send("/add  你通过post请求的哦@");
})

// 开启监听
app.listen(4399,(err)=>{
    if(!err){
        console.log('服务器跑起来了哦，这个地址就可以访问了哦 http://192.168.156.65:4399');
    }
})

```

## api - 用户名验证接口

> 用户注册之前，咱们先验证一下这个用户名是否已经被注册了

![1572076135271](D:/%E9%BB%91%E9%A9%AC/%E9%BB%91%E9%A9%AC%E8%B5%84%E6%96%99/%E9%BB%91%E9%A9%AC%E8%B5%84%E6%96%99/%E5%B0%B1%E4%B8%9A%E7%8F%AD/node.js%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/03express%E5%9F%BA%E6%9C%AC%E4%BD%BF%E7%94%A8/01-%E6%95%99%E5%AD%A6%E8%B5%84%E6%96%99/assets/1572076135271.png)

- 请求地址：/checkUsername
- 请求方法：post
- 请求参数：username
- 响应内容：

```
{
	msg:可以注册 或 已被注册,
	code:200 或 400
}
```

实现步骤：

1. 下载`body-parser`中间件
2. 导入中间件
3. 使用中间件
4. 注册路由`app.post('/checkUsername')`
5. 回调函数中 
   1. 获取用户名`request.body.username`
   2. 定义一个用来模拟所有用户的数组`userArr=['a','b','c']`
   3. 判断是否存在
      1. indexOf: -1不存在
      2. some:false不存在
   4. 返回信息
      1. 可以注册
      2. 不可以注册

注意

1. 用户主动的数据提交，用`post`
2. 约定好了数据的名字之后，不要胡乱提交
3. 数据比约定的要多，服务器可以不处理，
4. 如果比约定的要少，可能逻辑就会有问题

## express - post文件提交

> express通过第三方中间件来获取上传的文件

传送门: https://www.npmjs.com/package/express-fileupload 

1. 下包
2. 导包
3. 用包
   1. `request.files` 保存了所有文件信息
   2. `request.files.xxx` 获取 key为`xxx`的文件信息
   3. `request.files.xxx.mv（路径，回调函数）`把文件移动到某个地方

```javascript
// 导入express
const express = require('express');
// 导入 express-fileupload
const fileUpload = require('express-fileupload');

// 导入
const path = require('path');

// 创建服务器对象
const app = express();

// 使用中间件 接收文件
app.use(fileUpload());

// 上传
app.post('/upload',(request,response)=>{
    // console.log(request);
    // 使用了 中间件之后 可以通过 request.files获取文件信息
    // console.log(request.files);
    // files中用对象属性的方式 保存了上传的文件信息
    console.log(request.files.icon);
    // 通过 文件属性的.mv方法 移动文件到某个地方
    // 获取文件名
    const fileName = request.files.icon.name;
    // 生成路径
    const fullPath = path.join(__dirname,'./files/',fileName);
    request.files.icon.mv(fullPath,(err)=>{
        if(!err){
            console.log('哎哟，文件上传过来了哦');
        }
    })
    response.send("/upload");
})




// 开启监听
app.listen(4399,(err)=>{
    if(!err){
        console.log('服务器跑起来了哦，这个地址就可以访问了哦 http://192.168.156.65:4399');
    }
})

```



## 中间件

1. 就是一个特殊的第三方模块
2. 依赖于express
3. 起了一个牛逼的名字

## 课外阅读 - 原生http模块 - get参数获取

> 解析在url中参数

- 在http协议中，一个完整的url路径如下图
  - 通过下图我们可以得知，get请求的参数是直接在url路径中显示。
  - get的请求参数在path资源路径的后面添加，以`?`表示参数的开始，以`key=value`表示参数的键值对，多个参数以`&`符号分割
  - hash部分表示的是资源定位符（滚动网页可视区域），由浏览器自动解析处理，它的作用是跳转到对应id的标签的位置

![1571414438199](D:/%E9%BB%91%E9%A9%AC/%E9%BB%91%E9%A9%AC%E8%B5%84%E6%96%99/%E9%BB%91%E9%A9%AC%E8%B5%84%E6%96%99/%E5%B0%B1%E4%B8%9A%E7%8F%AD/node.js%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/03express%E5%9F%BA%E6%9C%AC%E4%BD%BF%E7%94%A8/01-%E6%95%99%E5%AD%A6%E8%B5%84%E6%96%99/assets/1571414438199.png)



```javascript
//1.导入模块
const http = require('http');
//url模块：解析url路径得到url协议中的每一部分
const url = require('url');

//2.创建服务器
let server = http.createServer((req,res)=>{
    //req.url:获取整个请求url  包含路径和参数
    console.log(req.url);
    //decodeURI():了解即可，默认情况下url中的中文会进行URI编码，使用decodeURI解码可以得到中文
    console.log(decodeURI(req.url));

    /*1.使用url模块解析get请求 
    第一个参数：要解析的url
    第二个参数: 布尔类型  true：推荐使用，得到的参数是一个对象   false：得到参数是字符串
    返回值：对象类型：将url中的每一部分作为对象的属性
     */
    let urlObjc = url.parse(req.url,true);
    console.log(urlObjc);

    //2.获取请求的路径
    let urlPath = urlObjc.pathname;
    console.log(urlPath);
    //3.获取请求的参数
    let query = urlObjc.query;
    console.log(query);

    //响应客户端请求
    //服务端不能直接响应js对象，需要转成json对象（后台具有跨平台性，不是只为前端服务）
    res.end(JSON.stringify({
        code:10000,
        list:[10,20,30]
    }));
   /*
   {
  protocol: null,//协议名
  slashes: null,//表示 //到第一个/之间都是host
  auth: null,//认证
  host: null,//主机名+ 端口号  hosetname+port
  port: null,//端口号
  hostname: null,//主机名  ip地址
  hash: null,//资源定位符
  search: '?name=OldFe&age=18',
  query: { name: 'OldFe', age: '18' },//get请求的参数对象
  pathname: '/getRequest',//路径
  path: '/getRequest?name=OldFe&age=18',//路径+请求参数
  href: '/getRequest?name=OldFe&age=18' }
   */
   //console.log(urlObjc);

});

//3.开启服务器
server.listen(3000,()=>{
    console.log('success');
});
```



## 第三方模块使用步骤

1. 新建文件夹(不要中文)
2. 初始化  打开终端输入:`npm init -y`或者`npm init` 自行输入
   1. 生成一个`package.json`文件
   2. 文件保存了项目的信息，比如版本，名字，使用的第三方模块名...
   3. `npm init `自行输入每一项（初期用的不多）
3. `npm网站`找包
4. 根据提示 下包 `npm i 包名`
   1. `package.json`中 增加一个`dependencies`把下载的包名，记录进去，和版本信息
   2. 文件夹下多
      1. `node_modules`所有下载的第三方模块都会在里面
      2. `package-lock.json`：模块名，版本号，在线地址等。。
         1. 为了让我们第二次下载的时候速度更快
5. 根据提示 导包
6. 根据提示 用包



第二次下载

1. 保存`package.json`及`package-lock.json`有之前下载的模块名
2. 直接输入`npm i`自动读取用到的模块，并下载

## express 基本使用

* 相对于原生http模块，开发速度更快的wed开发框架
  * 只要框架流行，基本都会有中文网
  * express是`node.js`中的一个`web开发框架`
  * 特点：静态资源托管
* 使用步骤：

1. 创建文件夹:
   1. 不要叫`express`和模块同名
2. 初始化:`npm init -y`
3. 下载express:`npm i express`
4. 导入`express`
   1. c+v
5. 使用`express`
   1. c+v
   2. http模块的方法都可以用，但是更建议用`express`的

````js

// 导包
const express=require('express');
// 创建服务器对象 和http.createServer类似
const app = express();
app.get('/',(request,response)=>{
    response.send('你好啊');
})
// 开启服务器
app.listen(8886, err =>{
if (err==null) {
    console.log('一不小心开启成功了');
    
}else{
    console.log('哎呀，开启失败了');
    
}
})
````

## express - 托管静态资源

> 一行代码让外部可以访问指定的文件夹

传送门: http://www.expressjs.com.cn/starter/static-files.html 

![1572055329726](D:/黑马/黑马资料/黑马资料/就业班/node.js上课资料/03express基本使用/01-教学资料/assets/1572055329726.png)

```javascript
// public文件夹下的文件就可以被访问了
app.use(express.static('public'))
```

1. public 建议和js文件统计
2. 重复打开需要关闭之前的那个
3. 初期花姐强烈建议`c+v`
4. `ip地址`每天是会变的 用`localhost`或者`127.0.0.1`

# 跨域

1. Ajax请求`不同源接口的时候会出现
2. `浏览器`为了保护我们帮我们做的限制
3. 浏览器打开的页面，和调用的接口需要`同源`才可以调用

* 同源：	
  * 协议，地址，端口全部相同时，称之为同源
    * 页面地址和接口地址同源，浏览器就会做任何的限制
    * 可以自由访问

* 不同源：

  * 协议，地址，端口任何一个不相同就是不同源
  * 浏览器默认是禁止访问

  实际工作中，不可避免页面的地址和接口地址绝对同源

  * ###### 解决方法

    * `cors`：目前用的最多的
    * `jsonp`:曾经用的最多，现在越来越少用了

* 往不同源的接口发送接口请求，就称为跨域

## 跨域方案-jaonp

* 这是民间的解决方法

  * 前端：

    ````js
    $.ajax{
    
    		url:'接口地址'
    
    		type:'必须是get'
    
    		success：function（backData）{}
    
    		dataType:'jsonp'
    
    }
    ````

  * 后端：

    ````js
    response.jsonp({key:value,key2:value2})
    
    // 导包
    const express = require('express')
    // 创建服务器
    const app = express()
    
    // 注册路由
    app.get('/jsonpApi',(request,response)=>{
        // 获取get请求的参数
        console.log(request.query)
        // 响应内容 jsonp的接口 返回数据用`jsonp`
        response.jsonp({
            msg:"请求成功",
            code:200,
            info:"欢迎再来"
        })
    })
    
    // 开启服务器
    app.listen(3000,(err)=>{
        if(!err){
            console.log('success');
        }
    })
    
    ````

  注意：

  * 如果接口是`jsonp`

  * 那么前端就要做

    * dataType：jsonp

    * type:是get或者省略不写

    * 数据的发送，请求成功之后的回调函数和原来一样

      1. jsonp接口文档
         1. 请求地址: `接口地址`
         2. 请求方法：`jsonp`  （type:`get`,dataType:`jsonp`）
         3. 参数：`键值对`

      

## jsonp原理（面试点）

* 虽然这个方案用的越来越少

* ```js
  <script src="http://192.168.156.88:3000/jsonpApi?callback=doSomething">
      </script>
  ```

  1. script标签的src属性，可以发送请求，没有`同源限制`
  2. 和`Ajax`一点关系都木有：
     1. `network`中选到`xhr`分类，什么都看不到
  3. 本质是动态创建了一个`script`标签添加到页面顶部
     1. src设置的:`接口地址`+`发送的数据`+`callback=xxx`
  4. 请求成功之后会被自动移除
  5. 服务器返回了:函数的调用`函数名({对象})`
  6. 内容返回到浏览器之后会被解析为`js`，调用定义好的函数，传入了一个参数

  jQuery的jsonp

  ![1572228409990](D:/%E9%BB%91%E9%A9%AC/%E9%BB%91%E9%A9%AC%E8%B5%84%E6%96%99/%E9%BB%91%E9%A9%AC%E8%B5%84%E6%96%99/%E5%B0%B1%E4%B8%9A%E7%8F%AD/node.js%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/04jsonp%E4%BD%BF%E7%94%A8%EF%BC%8Cexpress%20-%20%E4%B8%AD%E9%97%B4%E4%BB%B6%EF%BC%8Cmysql%E6%A8%A1%E5%9D%97%E4%BD%BF%E7%94%A8/01-%E6%95%99%E5%AD%A6%E8%B5%84%E6%96%99/assets/1572228409990.png)

  自己写jsonp

  ![1572228673181](D:/%E9%BB%91%E9%A9%AC/%E9%BB%91%E9%A9%AC%E8%B5%84%E6%96%99/%E9%BB%91%E9%A9%AC%E8%B5%84%E6%96%99/%E5%B0%B1%E4%B8%9A%E7%8F%AD/node.js%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/04jsonp%E4%BD%BF%E7%94%A8%EF%BC%8Cexpress%20-%20%E4%B8%AD%E9%97%B4%E4%BB%B6%EF%BC%8Cmysql%E6%A8%A1%E5%9D%97%E4%BD%BF%E7%94%A8/01-%E6%95%99%E5%AD%A6%E8%B5%84%E6%96%99/assets/1572228673181.png)

  注意：

  1. 工作中肯定是用jQ的
  2. 自己写需要
     1. 创建标签
     2. 声明函数
     3. 可能还需要自行移除标签
     4. 这些`jQ`都帮你干好了
  3. 虽然是民间的解决方案，但是很好用，广大程序员就做好了约定
  4. 你必须发送`callback`
  5. 后端也是通过`callback`去获取方法名字
  6. 缺点:
     1. 不支持`post`请求
     2. 数据大的话，搞不定，文件上传搞不定
  7. 流行的原因:
     1. `兼容性`好到令人发指

## 跨域方案-cors(目前最为流行的方案)

* 目前使用的最多，HTML5 新推出的标准，低版本的额浏览器不支持IE
* 注意：
  1. CORS原理：
     1. 浏览器能够识别` ('Access-Control-Allow-Origin', '*');`这个header
     2. 请求发给服务器之后
     3. 服务器返回的响应头中有一个允许的标记
     4. 浏览器就认为服务器允许跨域访问，没有了跨域的错误
  2. 缺点：
     1. 兼容性比`jsonp`差一些
     2. 微软已经放弃`xp` `ie5,ie6`基本没人用
  3. 优点:
     1. get和post都支持
     2. 前端什么都不用干
  4. 无论是jsonp还是`cors`一定需要后端配合
  5. 纯前端在`正常情况下无法跨域`

## express - 中间件 设置跨域

> 通过注册一个所有请求都会执行的公共回调函数来统一设置跨域

请求和响应之间额外注册的一个`回调函数` 

1. 在这个回调函数中统一的设置允许跨域的那个头

```javascript
// 自己写 中间件 来运行跨域
app.use((request,response,next)=>{
  console.log('执行啦');
  // 设置运行跨域
  response.header('Access-Control-Allow-Origin', '*');
  // 调用next
  next();
})
```



## express - 中间件

> 刚刚额外注册的那个回调函数就是中间件哦

传送门: http://www.expressjs.com.cn/guide/writing-middleware.html 

```javascript
app.use('地址(可选)',function(request,response,next){
    // request 后续的函数共享这个request对象
    // response 后续的函数共享这个response对象
    // 执行下一个函数
    next();
})
```

1. 中间件是请求和响应之间额外注册的回调函数
2. `request`和`response`是共享的
3. 中间件中为`request`对象额外增加的属性
4. 在后续的回调函数中可以获取到
5. 中间件可以增加`任意个`
6. `next`如果不调用，卡主，浏览器接收不到数据
7. 在请求和响应之间，额外注册的回调函数
8. `请求`--`回调函数（中间件）1`---`回调函数（中间件）2`------->`响应`
9. 执行的顺序从上到下依次执行
10. 编写的位置路由的前面
11. 从上往下依次执行
12. ![1572232444359](D:/%E9%BB%91%E9%A9%AC/%E9%BB%91%E9%A9%AC%E8%B5%84%E6%96%99/%E9%BB%91%E9%A9%AC%E8%B5%84%E6%96%99/%E5%B0%B1%E4%B8%9A%E7%8F%AD/node.js%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/04jsonp%E4%BD%BF%E7%94%A8%EF%BC%8Cexpress%20-%20%E4%B8%AD%E9%97%B4%E4%BB%B6%EF%BC%8Cmysql%E6%A8%A1%E5%9D%97%E4%BD%BF%E7%94%A8/01-%E6%95%99%E5%AD%A6%E8%B5%84%E6%96%99/assets/1572232444359.png)

注意:

1. 中间件是回调函数
2. 请求和响应之间额外注册的回调函数
3. 请求和响应之间根据注册的顺序依次执行
4. `next`调用了才会继续执行
5. `请求(request)`和`响应(response)`对象`共享`

## node.js 模块化

> node.js中模块的抽取必须要遵守特殊的语法哦

传送门-`CommonJs`标准：<http://www.commonjs.org/>

- 1.世界上的编程规范有很多种，CommonJS只是其中一种
- 2.CommonJS规范不是只为Nodejs服务，有很多平台都遵循CommonJS规范，Nodejs平台只是其中之一
- 3.CommonJS规范只有三句话
  - 1.导入模块使用:`require()`
  - 2.导出模块使用:`module.exports`
  - 3.导出模块一定要使用:`module.exports`(重要是事说两遍)



注意：

1. 导入模块`require`
   1. 自己的模块写路径
   2. `.js`可以省略
2. 模块暴露`module.exports`
   1. 类似自调用函数底部`window.xxx=值`
   2. 暴露多个，用对象方式
   3. 重复为`module.exports`赋值后面的会把前面的覆盖
3. 抽取的模块不需要运行
4. 导入的时候内部的代码会自动解析
5. `module`是关键字，全局变量
6. 要用哪个属性，就点哪个属性

## 自己写计算器模块

注意

1. 写功能
2. 暴露出去`module.exports={add,sub,mul,divi}`
3. 导入模块:`computer`
4. 使用方法:`computer.add(10,7)`

## 跨域模块抽取

> 刚刚的中间件抽取为一个独立的模块，哪里都可以用哦

步骤:

1. 创建了一个文件夹`utils`
   1. 工作中`自己抽取`的功能模块，很多公司都会放在这个文件夹中
2. 创建一个文件
   1. 暴露回调函数 module.exports
3. 任意一个文件 导入`模块`
4. `app.use(模块)`

自己写的模块

```javascript
// 暴露
module.exports = 
(request, response, next) => {
  console.log('执行啦');
  // 设置运行跨域
  response.header('Access-Control-Allow-Origin', '*');
  // 调用next
  next();
};

```

使用模块

```javascript
// 导包
const express = require('express');
// 导包 自己抽取的模块 跨域
const myCORS = require('./utils/myCORS');
// 创建服务器
const app = express();

// 自己写 中间件 来运行跨域
app.use(myCORS)

// 注册路由 - get
app.get('/corsGET', (request, response) => {

  response.send('/get');
});

// 注册路由 - post
app.post('/corsPOST', (request, response) => {

  response.send('/post');
});

// 开启服务器
app.listen(3000, err => {
  if (!err) {
    console.log('success');
  }
});


```

常见文件夹名:

1. utils：自己抽取的功能模块

2. libs:下载的第三方模块（自己手动下载）

3. node_modules:`npm i 模块名`自动下载的文件夹，内部保存了第三方模块

4. `static`：静态资源`html,css,js`

5. public:公共文件（静态资源）

6. `web`：页面(静态)

   

## 什么是数据库

> 通俗的来说就是数据的仓库，软件来的，保存数据同时，数据的安全性也得以保证

1. 数据库分类:
   1. 关系型数据库：
      1. 类似于`table`表格的形式保存数据
      2. 使用`sql`的语句操纵数据
      3. 常见的有:`MYSql`,`Oracle`,`MSSql`。。。
   2. 非关系型数据库:
      1. 用类似于`js对象`的形式保存数据
      2. 使用操纵对象的形式操纵数据
      3. 常见的有:`Mongodb`,`Redis`。。。
2. 数据库管理员:
   1. DBA:DataBase Admin
3. 数据库服务器:
   1. 只提供数据库服务，其他的都木有

## MySql基本使用

> 建库，建表，增加字段，增删改查

1. MYSql
   1. 免费，
   2. 开源，可以看到源代码，可以修改，可以定制
   3. 轻量级：小
   4. 作为关系型数据库的市场份额比较大
2. 建库（银行开户，有了一个存数据的空间）
3. 建表（一个一个的架子，excel）
4. 建字段（excel的表头）



1. 打开mysql

![1572246095078](D:/%E9%BB%91%E9%A9%AC/%E9%BB%91%E9%A9%AC%E8%B5%84%E6%96%99/%E9%BB%91%E9%A9%AC%E8%B5%84%E6%96%99/%E5%B0%B1%E4%B8%9A%E7%8F%AD/node.js%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/04jsonp%E4%BD%BF%E7%94%A8%EF%BC%8Cexpress%20-%20%E4%B8%AD%E9%97%B4%E4%BB%B6%EF%BC%8Cmysql%E6%A8%A1%E5%9D%97%E4%BD%BF%E7%94%A8/01-%E6%95%99%E5%AD%A6%E8%B5%84%E6%96%99/assets/1572246095078.png)

1. 建库:
2. ![1572246247517](D:/%E9%BB%91%E9%A9%AC/%E9%BB%91%E9%A9%AC%E8%B5%84%E6%96%99/%E9%BB%91%E9%A9%AC%E8%B5%84%E6%96%99/%E5%B0%B1%E4%B8%9A%E7%8F%AD/node.js%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/04jsonp%E4%BD%BF%E7%94%A8%EF%BC%8Cexpress%20-%20%E4%B8%AD%E9%97%B4%E4%BB%B6%EF%BC%8Cmysql%E6%A8%A1%E5%9D%97%E4%BD%BF%E7%94%A8/01-%E6%95%99%E5%AD%A6%E8%B5%84%E6%96%99/assets/1572246247517.png)
3. 建表
4. ![1572246403685](D:/%E9%BB%91%E9%A9%AC/%E9%BB%91%E9%A9%AC%E8%B5%84%E6%96%99/%E9%BB%91%E9%A9%AC%E8%B5%84%E6%96%99/%E5%B0%B1%E4%B8%9A%E7%8F%AD/node.js%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/04jsonp%E4%BD%BF%E7%94%A8%EF%BC%8Cexpress%20-%20%E4%B8%AD%E9%97%B4%E4%BB%B6%EF%BC%8Cmysql%E6%A8%A1%E5%9D%97%E4%BD%BF%E7%94%A8/01-%E6%95%99%E5%AD%A6%E8%B5%84%E6%96%99/assets/1572246403685.png)
5. 建表头
6. ![1572246595765](D:/%E9%BB%91%E9%A9%AC/%E9%BB%91%E9%A9%AC%E8%B5%84%E6%96%99/%E9%BB%91%E9%A9%AC%E8%B5%84%E6%96%99/%E5%B0%B1%E4%B8%9A%E7%8F%AD/node.js%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/04jsonp%E4%BD%BF%E7%94%A8%EF%BC%8Cexpress%20-%20%E4%B8%AD%E9%97%B4%E4%BB%B6%EF%BC%8Cmysql%E6%A8%A1%E5%9D%97%E4%BD%BF%E7%94%A8/01-%E6%95%99%E5%AD%A6%E8%B5%84%E6%96%99/assets/1572246595765.png)
7. 查看数据
8. ![1572246669197](D:/%E9%BB%91%E9%A9%AC/%E9%BB%91%E9%A9%AC%E8%B5%84%E6%96%99/%E9%BB%91%E9%A9%AC%E8%B5%84%E6%96%99/%E5%B0%B1%E4%B8%9A%E7%8F%AD/node.js%E4%B8%8A%E8%AF%BE%E8%B5%84%E6%96%99/04jsonp%E4%BD%BF%E7%94%A8%EF%BC%8Cexpress%20-%20%E4%B8%AD%E9%97%B4%E4%BB%B6%EF%BC%8Cmysql%E6%A8%A1%E5%9D%97%E4%BD%BF%E7%94%A8/01-%E6%95%99%E5%AD%A6%E8%B5%84%E6%96%99/assets/1572246669197.png)

## sql语句 - 增（insert）-了解即可

> 数据的新增，也可以叫做数据的插入

```sql
insert into 表名 （字段1，字段2，字段3...） values(值1，值2，值3...)
```

```sql
insert into user (username,skill) values('蔡*坤','唱，跳，rap');
```

## sql语句 - 删（delete）

> 数据的删除，但是正式工作中用的不多，数据可是很珍贵的哦

```sql
delete from 表名 where 条件
delete from user where id=3; 删除一条
delete from user where id <3; 删除范围
delete from user;不跟条件全部被干掉
```

1. 必须给条件，否则全部删除

## sql语句 - 改（update）

> 数据的修改，记得跟上条件

```sql
update 表名 set 字段1=值1, 字段2=值2,..... 条件
update user set username='赵四' ,skill='尬舞' where id = 22;
update user set username='葫芦娃' ,skill='救爷爷' where id > 22;
update user set username='小蝴蝶' ,skill='坑葫芦娃';
```

1. 条件不给全部改变

## sql语句 - 查（select）

> 数据的查询，通过各种条件进行数据的检索

```sql
select * from 表名 条件;
select * from user where id =26; 精确查询
select * from user where id <26;范围
select * from user ;全部
```

1. 和增删改不同，获取到数据本身
2. 增删改只能看到`几条数据`被改变了
3. 数据的基本操作分为4中，增删改    查

## mysql模块使用（了解）

> 通过node.js操纵数据库的第三方模块，了解即可

传送门:  https://www.npmjs.com/package/mysql 

1. 在Node.js中通过`MySQL`模块操纵数据库（间接操纵）数据库
2. 本质还是`sql`比较麻烦

## mysql-ithm模块使用（推荐）

> 黑马程序员开发，轻量级的`orm`( Object Relational Mapping )框架,记得好评哦

通过调用方法的方式，去间接的操纵数据

理论上来说一行`sql`都不需要写

只要会调用方法，你就可以操纵数据

用操纵对象的方式去操纵数据库

底层还是`sql`只不过不用开发人员自己写了

开发的速度更快

也是工作中绝大多数后端使用的开发方式