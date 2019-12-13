# 原生的AJax请求

* ## 上网的过程

  打开 浏览器

  地址栏，输入网址

  回车

  最终，看到页面

  ## 了解上网的过程

  ![1570928350667](D:/黑马/黑马资料/黑马资料/就业班/Ajax上课资料/01ajax介绍和简单使用，会员，留言板案例/笔记/课堂笔记.assets/1570928350667.png)

  

  ## 细化上网的过程

  ![1570928833607](D:/黑马/黑马资料/黑马资料/就业班/Ajax上课资料/01ajax介绍和简单使用，会员，留言板案例/笔记/课堂笔记.assets/1570928833607.png)

  - 客户端（client）
    - 向服务器发送请求的一个工具
    - 最常见的客户端工具就是浏览器。后面没有特殊说明，老师所说的客户端就是浏览器，浏览器就是客户端
  - 服务器（server）
    - 本质上，也是一个电脑
    - 作用
      - 存储网页。开发好的网页都应该放到服务器上
      - 提供服务，可以把客户端请求的页面返回给客户端
  - 请求
    - 客户端向服务器“索要”页面的动作。
  - 响应
    - 即回应，服务器为客户端提供页面的过程
  - 资源
    - 服务器上存储的各种文件都叫做资源（比如，HTML文件、css文件、图片文件、音频视频文件等等）

  

  ## 浏览器工具

  单词：

  request：请求

  response：响应

  

  ![1570929616284](D:/黑马/黑马资料/黑马资料/就业班/Ajax上课资料/01ajax介绍和简单使用，会员，留言板案例/笔记/课堂笔记.assets/1570929616284.png)

  ## 了解服务器

  Web服务器的作用：

  - 存储Web资源，资源的概念很广，这里先理解为服务器上的html文件、css文件、js文件、图片文件等等。
  - 提供Web服务，理解为能够接收并处理客户端的请求，并做出回应

  Web服务器和普通计算机的区别

  - 除了硬件设施的区别之外，`Web服务器 === 普通计算机 + 服务器软件`

  ### 服务器软件

  - Apache
  - IIS
  - Nginx
  - ...
  - 自己编写一个软件或程序（上课使用的就是老师写的一个程序）

  ## 搭建web服务器

  - ![b-1568615934932](D:/黑马/黑马资料/黑马资料/就业班/Ajax上课资料/01ajax介绍和简单使用，会员，留言板案例/笔记/课堂笔记.assets/b-1568615934932.gif)

  注意事项：

  1. 服务不能重复开启，即不能多次执行 `node app.js` 
  2. 关闭服务器，在终端中，按 `Ctrl + C`
  3. 快捷键 `Ctrl + ~` 可以快速打开关闭终端
  4. 关闭终端面板，并不表示关闭服务器

  ## 服务器软件使用规范

  1. 服务器上的文件不能随便放
     - 必须放到 `ajax/public` 文件夹里面
  2. 通过域名或IP找服务器
     1. IP也叫做IP地址。
     2. IP永远不会重复，它表示网络中的计算机的位置
     3. 域名和IP的作用相同，都可以找到网络中的计算机。域名比IP只是好记。

  3. 如何访问自己的服务器
     1. 飞秋上看自己的IP（不推荐）
     2. 使用通用的IP地址，`127.0.0.1` ，它永远指向自己的计算机
     3. 使用通用的域名，`localhost`，它永远指向自己的计算机

  ## 初识Ajax

  Ajax是一门技术，可以实现客户端和服务器交互的技术。简单来说，可以实现发送请求，也可以接收服务器响应的结果。

  Ajax是通过执行一段JS代码来发送请求，并接收响应结果的技术。

  ## 接口介绍

  - 是什么？
    - 就是一个网址
  - 有什么用？
    - 发送ajax请求的时候，可以为url添接口地址
    - 方便获取数据的一个网址
  - 哪里来的？
    - 后端同学提供的，前端同学目前来说，不用关心。
  - 有哪些接口可用
    - 后端同学设计完接口之后，会提供给我们一个接口文档。具体看文档

  ## 接口文档

  ```js
  $.ajax({
      type: '请求方式',
      url: '接口地址',
      data: '请求参数',
      dataType: '响应数据格式',
      success: function (result) {
          // result 表示服务器返回的结果
      }
  });
  ```

  请求参数的写法：

  - 字符串

  ```js
  data: '参数=值&参数=值....'
  ```

  - 对象

  ```js
  data: {参数: '值', 参数: '值', ...}
  ```

  ## 验证用户名

  实现过程分析：

  - 不再是刷新页面就发送Ajax请求了，应该在input失去焦点时，发送验证用户名的Ajax请求
  - 需要验证的用户名不能写死，应该是用户在文本框中输入的值
  - 服务器返回的结果，不应该直接console.log了，应该判断后，在页面中给出提示

  具体代码：

  ```html
  <input type="text" id="username">
  <span></span>
  
  <script src="./assets/jquery.js"></script>
  <script>
      // 1. 注册 input的失去焦点事件
      $('input').blur(function () {
          var uname = $(this).val(); // 获取输入框中的值
          // 2. 发送ajax请求，验证用户名
          $.ajax({
              type: 'GET',
              url: '/common/checkUser',
              data: {username: uname},
              // data: 'username=' + uname, // username=xxx
              dataType: 'json',
              success: function (result) {
                  console.log(result);
                  // 3. 在span标签中给出提示
                  $('span').text(result.msg);
              }
          });
      });
  </script>
  ```

  执行过程：

  ![1570940243806](D:/黑马/黑马资料/黑马资料/就业班/Ajax上课资料/01ajax介绍和简单使用，会员，留言板案例/笔记/课堂笔记.assets/1570940243806.png)

  

## 原生的Ajax请求

### 基本语法

- GET

  ```js
  // 原生的Ajax请求，使用的是 XMLHttpRequest 对象提供的API（属性和方法）
  
  // 1. 实例化 XMLHttpRequest 对象，request单词的意思是请求
  var xhr = new XMLHttpRequest();
  // 2. 调用open方法，设置请求的方式和url
  xhr.open('GET', '/common/time');
  // 3. 调用send方法，发送请求   ---> 到这一步，才表示发送ajax请求
  xhr.send();
  // 4. 当请求响应过程结束，然后接收服务器响应的结果
  xhr.onload = function () {
      console.log(xhr.response);
  }
  ```

  - 如果有请求参数

    - 请求参数要拼接到url后面即可

      ```js
      xhr.open('GET', '/common/checkUser?username=lisi');
      ```

      

- POST

  ```js
  // 1. 创建xhr对象
  var xhr = new XMLHttpRequest();
  // 2. 调用open方法，设置请求方式和url
  xhr.open('POST', '/message/addMsg');
  // 3. 设置一个请求头，固定的一行代码
  xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');   
  // 4. 调用send，发送请求
  xhr.send('name=xxx&content=xxx');
  // 5. 设置onload事件，接收服务器相应的结果
  xhr.onload = function () {
      console.log(this.response);
  }
  ```

  

### GET和POST的区别

- 意义
  - GET：请求一般用于获取服务器上的资源，这种请求不会改变服务器上的资源
  - POST：一般用于提交数据给服务器，这种请求有可能会改变服务器上的资源
- 写法
  - 请求参数位置不同
  - POST请求多了一行代码

### 小案例

接口中的请求参数id，和下图中的文件名是一个意思。

- id = 0 ,表示获取所有的省
- id = 105 ，表示获取河北省下属的市
- id = 105001， 表示获取石家庄市下属的县

![1571020189620](D:/黑马/黑马资料/黑马资料/就业班/Ajax上课资料/02原生Ajax，省市县三级案例，同步异步/笔记/笔记.assets/1571020189620.png)





### 浏览器的问题

#### readyState和onreadystatechange

xhr.onload 事件，属于XHR对象新增的一个属性，IE6、IE7、IE8不支持onload。低版本的浏览器可以使用onreadystatechange事件来代替。

- onreadystatechange事件
  - 会触发多次
  - 触发时机
    - 当readyState属性值（ajax的状态）改变的时候（0-->1、 1-->2 ....），会触发
    - 接收的数据量发生变化了，也会触发
- readyState属性
  - 表示ajax的执行状态，值分别是0/1/2/3/4 ，共计5个值

![1571022320588](D:/黑马/黑马资料/黑马资料/就业班/Ajax上课资料/02原生Ajax，省市县三级案例，同步异步/笔记/笔记.assets/1571022320588.png)

#### IE缓存问题

- 产生原因
  - 两次或多次ajax的GET请求，url地址完全一致
- 解决办法
  - 让每次请求的url不一致

### 其他API

#### 创建xhr对象的兼容写法

- var xhr = new XMLHttpRequest();
- var xhr = new ActiveXObject('Microsoft.XMLHTTP');   // IE6 IE7 的写法

#### responseType属性

类似于 $.ajax() 中的 dataType。

指定该属性，会把JSON等格式的数据转成JS数据（对象、数组等）



### 原生Ajax小结

至此，我们学习了很多 XHR 对象的 属性和方法 （统称API）。其实这些API分属不同的XHR版本。

- XHR 1 版 API -- 最初的XHR对象提供的API，基本上兼容所有的浏览器
  - open -- 设置请求方式、请求url、同步或异步
  - send -- 发送请求
  - readyState -- ajax的状态，值（0，1，2，3，4）
  - onreadystatechange -- 当readyState的值改变的时候，或当接收的数据发生改变的时候都会触发
  - responseText：-- 用于接收服务器返回的 `文本类型` 的结果
- XHR 2.0 新增API，基本上不再支持IE6、IE7、IE8
  - onload（2014年新增） -- 当请求响应成功了，会触发
  - onprogress -- 当响应的数据，正在接收中，会触发。数据量比较大的话，可能会触发多次，可以使用它做一个进度条
  - onloadstart -- 当请求开始的时候，会触发
  - onloadend -- 当请求结束的时候，会触发
  - response ：可以接收任何的响应结果
  - responseType（2012年新增）：配合response使用的一个属性

> 实际开发中，原生的Ajax使用的概率非常少。一般都使用封装好的库，比如 jQuery中的 $.ajax()

## 同步和异步

### 异步

==所以异步操作的**本质**是同一个时间点，有多个操作同时执行了；耗时操作（定时器）并不会阻塞后面代码的执行。==

- 同一个时间点，执行了多个操作
- 耗时操作不会阻塞后续代码的执行

### 同步

同一个时间点，只能执行一个操作。前面的代码没有执行完毕，后续代码都不能执行。

## 封装

```js
/*
type: 请求方式
url: 请求接口地址
data: 请求参数
cb: 用于处理服务器响应结果的回调函数。cb取自单词 callback
*/
function ajax (type, url, data, cb) {
    var xhr = new XMLHttpRequest();

    var params = null;
    // 判断是否是GET方式
    if (type === 'GET') {
        // 把url和data拼接到一起，形成 /common/checkUser?username=xxx
        url = url + '?' + data;
    }
    xhr.open(type, url);

    // 判断是GET还是POST请求
    if (type === 'POST') {
        xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');
        // 重置 aaaaa = data
        params = data;
    }

    xhr.send(params);

    xhr.onload = function () {
        // console.log(this.response)
        cb(this.response);
    }
}

/* function chuli (res) {
            console.log(res);
        } */

ajax(
    'POST', 
    '/message/addMsg', 
    'name=xxx&content=yyy', 
    function (res) {
        console.log(res);
    }
);
```



回调函数是处理异步请求结果的最佳方案。

## 小结

- 原生的Ajax写法
  - GET （4个步骤）
  - POST（5个步骤）
  - GET和POST写法上的区别
    - POST多了一行代码
    - 请求参数的位置不一样

- 浏览器问题
  - onreadystatechange事件配合readyState，完成获取响应结果的任务，代替onload事件
  - IE缓存问题（产生原因、解决办法）
- API小结
  - XHR1.0 版本
    - open
    - send
    - onreadystatechange
    - readyState
    - responseText
  - XHR2.0新增
    - onload
    - responseType
    - response
    - onprogress/onloadstart/onloadend ....

- 同步和异步
  - 异步：同一个时间点，可以执行多个操作。耗时操作不会阻塞后续代码的执行。
  - 同步：同一个时间点，只能执行一个操作。耗时操作肯定会阻塞后续代码的执行。

- 封装
  - 把需要变化的位置，设置为形参即可
  - 处理异步请求的结果，必须使用回调函数。



## FormData

- 有form表单

  ```js
  // 使用FormData步骤1： 找到form表单，找表单的dom对象
  var fm = document.getElementById('fm');
  // 使用FormData步骤2： 实例化FormData，并传递表单即可，得到的对象里面包含了所有的值
  var formdata = new FormData(fm);
  
  ....
  ....
  xhr.send(formdata);
  ....
  ```

- 请求头的设置

  - 如果提交的数据是纯文件，没有文件上传。需要设置请求头
  - ==使用FormData的时候，不需要自己设置请求头==

- 注意事项

  - 不能让表单提交
    - 设置按钮为button类型
    - JS代码中，通过事件对象阻止表单提交的这种默认行为
  - 表单中各项必须有name属性，因为FormData收集表单数据的时候，就是根据name属性获取的

- 关于文件域的补充

  - 标签的属性
    - multiple  --  设置后，表示允许选择多个文件
    - accept -- 可以上传文件的类型，写法有 `.jpg,.png,.gif` 或 `image/png` 或 `image/*`

  - JS代码中，如果找到文件对象
    - `document.getElementById(文件域的id).files[0]`

- FormData 中的 append方法

  - 作用是，向FormData对象中追加一些值
  - 用法： 
    - `formdata.append('pwd', 'hello');`
    - `formdata.append('pic', document.getElementById('pic').files[0]);`

## 模板引擎



## 综合案例

### 删除

==接口代码有误：将 `ajax/router/members.js` 中的第85的`query`改成`body`。保存之后，重启服务即可。==

关键点：

- 删除的接口，需要会员的id。
  - 在渲染页面的时候，就应该把id渲染到页面中
  - id不应该直接显示出来，所以把id当做 Delete 标签的属性值
- 注册事件的时候，必须使用==事件委托==的方案
- confirm() 是一个提示框。用户点击确定，返回true；用户点击取消，返回false
- 移除元素的时候，注意this指向问题

### 查看详情

- 超链接跳转属于GET请求，如果传递参数，需要在url后面拼接  `detail.html?id=23`

- 获取地址栏的参数：`location.search`

### 预览图片

1. 找到文件对象，==必须通过DOM对象找文件对象==；  
2. 通过 `URL.createObjectURL(文件对象)` 可以得到一个用于访问图片的临时的url
3. 设置预览图片的src属性即可。

### 添加会员

- 注意：一定要按接口写代码
- 表单各项（每个input）的name属性必须设置，因为FormData收集表单数据的时候，是根据name属性获取的
- 表单各项的name属性，必须和接口要求的请求参数一致
- jQuery+FormData的使用
  - 必须加入 `contentType: false` ，目的是不需要设置Content-Type，浏览器会自行处理
  - 必须加入 `processData: false`， 目的是不需要处理formdata数据。

### 懒加载

- 思路

  - 找到何时该去加载下一页的数据

    ![1571126953761](D:/黑马/黑马资料/黑马资料/就业班/Ajax上课资料/03FormData使用方式，会员管理案例/笔记/笔记.assets/1571126953761.png)

  - 如何加载下一页的数据

    - 调用 `/member/list-page` 接口，只不过让请求参数 `page` 的值加 `1` 

- 解决重复加载的BUG

  - 重复加载数据，是因为滚动条不好控制，不小心就滚动多了，会多次调用loadData() 函数
  - 解决办法
    - 进入到loadData中，马上设置flag为false。（flag=false表示不允许调用loadData了）
    - 当前页的数据处理完毕，重置flag为true。

## Ajax的补充

### 是什么

- 字面意思
  - Ajax 即“Asynchronous  Javascript  And  XML”（异步的 JavaScript 和 XML）
- 深层意思
  - 是一种通过JS代码完成客户端和服务器端交互的技术

### 典型应用场景

在`不更新页面`的情况下（页面有没有更新就检查后退按钮），浏览器要从web服务器获取数据，此时就可以使用ajax技术。

先来对比更新和不更新页面，以分页为例

- 大学的公告页，没有使用AJAX：http://www.whut.edu.cn/tzgg/
- 博客园的主页,   使用了AJAX：<https://www.cnblogs.com/>

经典应用

- 博客页的注册页：<https://account.cnblogs.com/signup>
- 购物网站：http://www.smzdm.com

### AJAX技术的好处

总结如下两点好处：

1. 局部更新，提升用户体验，提升性能。
2. 分离开发，提高开发效率。
   1. 前端 调用接口
   2. 后端 开发接口

## jQuery中的ajax补充

- $.ajax();

  ```js
  $.ajax({
      type: '请求方式',
      url: '接口地址',
      data: '请求参数',
      dataType: '响应数据格式',
      success: function (res) {
          // res就是服务器返回的结果
      },
      beforeSend: function () {},
      complete: function () {},
      contentType: '设置请求头中的content-type的值',
      processData: '是否处理请求参数'
  });
  ```

  

- $.get()

  ```js
  $.get('url', [请求参数], [请求成功后的回调函数], [服务器返回数据的类型]);
  ```

  

- $.post()

  ```js
  $.post('url', [请求参数], [请求成功后的回调函数], [服务器返回数据的类型]);
  ```

  

## 其他封装库 axios （了解）

### axios库

jquery中封装了ajax功能，但是它的体积比较大。如果我们只希望使用ajax功能，而不需要dom操作的话，我们可以选择使用axios库。(fetch)

应用：

```
- 它只专注于处理http请求，比jquery的体积小的多，适用于只需要ajax请求的业务场景；
- 后期学习三大前端框架时也会用到；
```

#### 使用示例

通过官网查看其使用方法。

与jquery一样，要使用它，必须先引入这个文件。然后就可以按如下的格式去使用了。

中文网站：<http://www.axios-js.com/zh-cn/docs/

```javascript
// 获取服务器的返回值
axios.get('/common/get?id=123').then(function(res) {
    // res 就是本次请求的信息
    console.info(res);
    // 获取 从服务器返回的数据
    console.info(res.data);
});

axios.get('/common/get', { params: { id: 123, name: 'jake' } }).then(function(res) {
    // res 就是本次请求的信息
    console.info(res);
    // 获取 从服务器返回的数据
    console.info(res.data);
});

// post请求，不带参数
axios.post('/common/post').then(function(res) {
    console.info(res.data);
});
// post请求，带参数
axios.post('/common/post', { id: 123, name: 'jake' }).then(function(res) {
    console.info(res.data);
});
```



## 模板引擎

### 模板引擎介绍

客户端中拿到请求的数据过后最常见的就是把这些数据呈现到界面上。

如果数据结构简单，可以直接通过字符串操作（拼接）的方式处理，但是如果数据过于复杂，字符串拼接维护成本太大，就不推荐了。

> 模板引擎：
>
> - artTemplate：https://aui.github.io/art-template/

模板引擎实际上就是一个 API，模板引擎有很多种，使用方式大同小异，目的为了可以更容易更高效的将数据渲染到HTML字符串中。==通俗的说，模板引擎的目的就是将服务器返回的数据显示到HTML页面中==。

### 使用模板引擎步骤

1. 准备一个存放数据的盒子（不是必须的，使用body也可以）

2. 引入template-web.js文件

3. 定义模板（具体语法可以去官网查看），一定要指定script的id和type属性

4. 调用template函数，为模板分配数据，template函数有两个参数一个返回值

   1. 参数1：模板的id
   2. 参数2：分配的数据，必须是一个JS对象的形式
   3. 一个返回值：是数据和模板标签组合好的结果

5. 将 “拼接” 好的结果放到准备好的盒子中（不是必须的，console出来也可以看结果）

   ![1566443384929](D:/黑马/黑马资料/黑马资料/就业班/Ajax上课资料/Ajax补充/Ajax补充.assets/1566443384929.png)

```html
<script src="./assets/template-web.js"></script>

<script type="text/html" id="test">
        <h2>{{title}}</h2>
        <p>{{age}}</p>
        <ul>
            <li>{{heroes[0]}}</li>
            <li>{{heroes[1]}}</li>
            <li>{{heroes[2]}}</li>
    </ul>
</script>

<script>
    // 下面的数据是模拟的，相当于ajax请求之后，服务器返回的数据
    var data = {
        title: '模板引擎练习',
        age: 20,
        heroes: ['曹操', '刘备', '李逵', '张飞']
    };
    // 调用template函数
    /*
        var str = template(模板的id, 数据); // 数据必须是JS对象格式
        */
    var str = template('test', data);
    console.log(str);
</script>
```

> 定义模板时的script标签一定好指定id和type
>
> tempalte函数语法：var html = template(模板id,  Object);

### 模板语法

- 输出普通数据（字符串、数值等）

  ```
  // 模板写法
  {{var}}
  
  // template函数写法
  var html = template('id', {
      var: 'hello world'
  });
  ```

- 条件

  ```
  // 模板写法
  {{if age > 18}}
  	大于18
  {{else}}
  	小于18
  {{/if}}
  
  // template函数写法
  var html = template('id', {
      age: 20
  });
  ```

- 循环

  ```
  // 模板写法
  {{each arr}}
  	{{$index}} -- 数组的下标
  	{{$value}} -- 数组的值
  {{/each}}
  
  // template函数写法
  var html = template('id', {
      arr: ['apple', 'banana', 'orange']
  });
  ```

完整的代码：

```html
<script src="./assets/template-web.js"></script>

    <!-- 1. 定义模板 -->
    <script id="abc" type="text/html">
        <h1>{{name}}</h1>
        <p>我是{{nickname}}，我有一辆{{car}}，我今年{{age}}岁了</p>
        {{if age >= 18}}
            <p>欢迎来玩~</p>
        {{else}}
            <p>未成年人禁止进入</p>
        {{/if}}
        <p>我有好几个女朋友，分别是：</p>
        <ul>
            {{each girls}}
            <li>{{$index}} -- {{$value}}</li>
            {{/each}}
        </ul>
    </script>


    <script>
        // 2. 调用template函数
        var str = template('abc', {
            name: '狗哥',
            nickname: '北狗最光阴',
            car: '宝马',
            age: 31,
            girls: ['王婆', '金莲', '西门大官人', '李师师', '赛金花']
        });

        console.log(str);
        document.body.innerHTML = str;
    </script>
```



### 案例中使用模板引擎处理响应数据

下面以留言板案例为例。

```html
<!-- 引入template-web.js -->
<script src="./assets/template-web.js"></script>

<!-- 定义模板 -->
<script id="moban" type="text/html">
    {{each girls}}
    <li class="media">
      <img class="mr-3" src="avatar.png" alt="">
      <div class="media-body">
        <h4>{{$value.name}}</h4>
        <p>{{$value.content}}</p>
    </div>
    </li>
    {{/each}}
</script>
```

```js
xhr.onload = function () {
    // console.log(this.response);
    var data = JSON.parse(this.response);
    console.log(data);
    // 拼接字符串
    var str = template('moban', {
        girls: data
    });
    // 把变量后，拼接好的str放到 id为 messages 的ul中
    document.getElementById('messages').innerHTML = str;
}
```

