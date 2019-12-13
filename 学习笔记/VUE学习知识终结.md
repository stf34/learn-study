# VUE

Vue 其实就是一个封装了大量逻辑的 Javascript 文 件。

有多种方式可以获取 vue:

1. [下载](https://cn.vuejs.org/js/vue.js)
2. CDN https://cdn.jsdelivr.net/npm/vue/dist/vue.js
3. npm 仓库

```html
<body>
<p v-show='false'>你好啊，vue</p>
</body>
<script src="./libs/vue.min.js"></script>
<script>

    /*
           当引入vue之后，会的到一个全新的构造函数
            需要对这个构造函数进行实例化
            接收一个对象作为参数
            通股票vue自定义的属性可以控制元素，将标签隐藏

    
    
    
    */
    new Vue({//Vue的v大写
        // 指定vue的管辖范围，可以是css标签，也可以是DOM节点,建议使用id选择器
        //如果标签同样，那么只对第一个生效
        el:'p'
    })
</script>
```

我们都知道 `input`被隐藏是因为 `type=hidden` ，那 `h2` 隐藏是因为什么呢？细心的你应该发现了，`h2`标签上多了一个 `v-if` 的东西，这是什么东东？

​		**其实从 html 语法角度来看，写在开始标签上的都可以称为标签属性， 所以 `v-if` 其实就是一个属性而已！！！这个属性并不是 W3C 的标准属性，它是由 Vue 提供的，通过 `v-if` 可以控制元素是否显示。**

#### 视图

​		通过上述示例，我们知道了通过 vue 提供的属性，如 `v-if` ，可以丰富页面的逻辑控制，**但是它只能在一定的“范围”才可以生效，我们称这部分为View，即视图层 。** 

​		**注：将 el 指定的区域称为视图并不严禁，准确一点儿应该叫模板，不过初学者不必细究。****Vue** **可以与其它前端技术整合**。

```html
<body>
    <!-- 属性值为布尔类型，如果不写值默认为true 如果你不写值，默认为false-->
    <div id="btn">

        <p v-show='true'>你好啊，vue</p>

        
    </div>
</body>
<script src="./libs/vue.min.js"></script>
<script>

    /*
           当引入vue之后，会的到一个全新的构造函数
            需要对这个构造函数进行实例化
            接收一个对象作为参数
            通股票vue自定义的属性可以控制元素，将标签隐藏

    
    
    
    */
    new Vue({//Vue的v大写
        // 指定vue的管辖范围，可以是css标签，也可以是DOM节点,建议使用id选择器
        //如果标签同样，那么只对第一个生效
        el: '#btn',//el所对应的元素不可以是HTML或body,必须写的属性
    })
</script>
```

#### 模型

​		一个**网页的核心是数据**，html 和 css 只是负责将这些数据以较为美观的形式展示，**Vue 可以对页面所承载的数据进行管理，我们称之为 Model，即模型。**

* 当data中定义了和methods中相同的属性时。以data为准，methods不允许重复

```html
<body>
    <!-- 属性值为布尔类型，如果不写值默认为true 如果你不写值，默认为false-->
    <div id="btn">

        <p v-show='true'>你好啊，vue</p>
        <!-- v-text` 一般认为是 `{{}}` 的另一种写法，相当于原生 DOM 中的  `innerTex -->
        <p v-text='msg'></p>
        <!-- 通过{{}}我们可以将vue的初始数据渲染出来 -->
        <p>{{msg}}</p>
        
    </div>
</body>
<script src="./libs/vue.min.js"></script>
<script>

    /*
           当引入vue之后，会的到一个全新的构造函数
            需要对这个构造函数进行实例化
            接收一个对象作为参数
            通股票vue自定义的属性可以控制元素，将标签隐藏

    
    
    
    */
    new Vue({//Vue的v大写
        // 指定vue的管辖范围，可以是css标签，也可以是DOM节点,建议使用id选择器
        //如果标签同样，那么只对第一个生效
        el: '#btn',//el所对应的元素不可以是HTML或body,必须写的属性
        data: {//通过 `data` 可以为 `el` 所对应的 DOM 初始数据
            msg: '我又来了'
        }
    })
</script>
```

 		实例化 Vue 时，通过 `data` 可以为 `el` 所对应的 DOM 初始数据，其中数据类型可以为任意合法的 Javascript 数据类型。

​		`{{}}` 是 Vue 中特殊的语法符号，用于将 `data` 中的数据插入到视图层元素的内容区域（innerHTML）。

# 数据绑定

​		数据绑定是 vue 中非常高级的特性，它是指将**视图层DOM元素与模型层中的数据建立一一对应的联系**，将这种联系称为数据绑定。

​		DOM 元素一般包含**属性节点**和**文本节点**，所以 vue 中实现数据绑定主要体验在两个方面：

- 属性节点绑定
  1. `v-bind:属性名` 是实现属性节点绑定的语法格式。
  2. `class` 和 `style` 是DOM元素中比较重要的两个属性。
  3. `v-bind:属性名` 可以被简写为 `:属性名`
  4. 支持 Javascript 表达式

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>数据绑定</title>
    <style>
    .domo{
        color: yellow;
        background: #ccc;
    }
    .tel{
        color: red;
        background-color: #333;
    }
    </style>
</head>
<body>
       <div id="btn">
           <!-- 在vue中对(html有的属性)属性进行数据绑定时，用法v-bind:属性名='值' -->
        <p v-bind:title="tel">你好</p>
        <!-- v-bind:style  语法比较特殊 可以接受一个对象类型，
            只不过内容是css的代码 因为是在对象里写，所以值加上引号
            如果本身是个对象，直接写对象名就行
        -->
        <p v-bind:style="objclss">你好</p>
        <!-- v-bind:class  语法比较特殊 可以接受一个对象类型数据，
            对象的属性类名，要真实存在
            对象的值为布尔类型
            如果为true，这添加相应属性的类名
            如果为false，则不添加
        -->
        <p v-bind:class="{domo:true,tel:false}">你好</p>
       </div>
    
    </body>
    <script src="./libs/vue.min.js"></script>
    <script>
        new Vue({//Vue的v大写
            // 指定vue的管辖范围，可以是css标签，也可以是DOM节点,建议使用id选择器
            //如果标签同样，那么只对第一个生效
            el: '#btn',//el所对应的元素不可以是HTML或body,必须写的属性
            data: {//通过 `data` 可以为 `el` 所对应的 DOM 初始数据
                tel: '我又来了',
                objclss:{
                    color:'red',
                    background: "#ccc"
                }
            }
        })
        
    </script>
</html>
```

#### 文本节点绑定

* `{{}}`是实现文本节点绑定的语法格式
* `v-text`一般认为是`{{}}`的另一种写法，相当于DOM中的`innerext`
* `v-html`在渲染时能够解析文本的HTML标签，相当于DOM中的`innerext`

```html
<body>
    <div id="btn">

        <p v-text='tel'>你好</p>
        <!-- v-html` 在渲染时能够解析文本的 `html` 标签，相当于原生 DOM 中的 `innerHTML` -->
        <p v-html='htmltext'>你好</p>
        <!-- 支持访问[]数组单元 如果不加[]的话是选择全部 -->
        <p>{{list[0]}}</p>
        <!-- 支持 . 或 对象["key"] 来访问对象的属性 -->
        <p>{{user.name}}</p>

    </div>

</body>
<script src="./libs/vue.min.js"></script>
<script>
    new Vue({//Vue的v大写
        // 指定vue的管辖范围，可以是css标签，也可以是DOM节点,建议使用id选择器
        //如果标签同样，那么只对第一个生效
        el: '#btn',//el所对应的元素不可以是HTML或body,必须写的属性
        data: {//通过 `data` 可以为 `el` 所对应的 DOM 初始数据
            tel: '我又来了',
            htmltext: '<span>带着标签的文本</span>',
            list: ['123', '12', '23'],
            user: {
                name: '小明',
                age: 23
            }
        },

    })

</script>
```

#### 事件绑定

* 事件可以认为DOM元素的属性，但由于其特殊的含义vue中将它与其他属性区别对待
* `v-on:事件名='回调函数'`是为添加事件监听的用法，可以简写为`@事件名='回调函数'`，$event作为参数传递时具有特殊含义，可以用它获得事件对象
* 回调函数一般都定义在vue专门提供的方法中了，另外methods中不许使用箭头函数

```html
<body>
       <div id="btn">
         <!-- vue 中添加事件监听的语法： v-on:原生事件名称='回调函数' 简写：@原生事件名称 -->
         <!-- $event 做为参数传递时具有特殊含义，用它获得事件对象 -->
        <a href="JavaScript:;" v-on:click="clicked($event)">点击</a>
        <input type="text" @focus='focus'>
       </div>
    
    </body>
    <script src="./libs/vue.min.js"></script>
    <script>
        new Vue({//Vue的v大写
            // 指定vue的管辖范围，可以是css标签，也可以是DOM节点,建议使用id选择器
            //如果标签同样，那么只对第一个生效
            el: '#btn',//el所对应的元素不可以是HTML或body,必须写的属性
            data:{},
            // methods vue提供的专门定义方法的参数
            // 可以定义事件的回调
            // methods中定义的方法，不允许使用箭头函数
            methods:{
                // 事件回调
                clicked:function(ev){
                    // 事件被触发，回调就被执行
                    console.log("w我被触发了");
                    // console.log(ev);
                    // ev.target  为原生DOM对象
                    ev.target.style.color='red';
                    
                },
                focus:function(){
                    console.log('小楷书');
                    
                }
            }
        })
        
    </script>
```

* v-on:事件名.修饰符="回调函数"` 通过添加修饰符来实现事件的特殊处理，如事件冒泡,键盘事件等

```html
<body>
       <div id="btn">
           <!-- 在vue 通过修饰符来解决事件执行时的一些特殊逻辑问题问题时 
                如 阻止冒泡，获取按键信息等
                语法格式：在事件的名称后， . 符号 即是修饰符
                v-on:事件名.修饰符="函数"
               @事件名.修饰符="函数"
        
        -->
        <div class="parent" @click="parent">
            <!-- .stop 阻止冒泡 -->
            <div class="child" @click.stop='child'></div>
        </div>

        <input type="text" @keyup="send">

        <input type="text" @keyup.13="send">
        <!-- 可以多个按键连写 -->
        <input type="text" @keyup.shift.enter="send">
 
       </div>
    
    </body>
    <script src="./libs/vue.min.js"></script>
    <script>
        new Vue({//Vue的v大写
            // 指定vue的管辖范围，可以是css标签，也可以是DOM节点,建议使用id选择器
            //如果标签同样，那么只对第一个生效
            el: '#btn',//el所对应的元素不可以是HTML或body,必须写的属性
            data: {//通过 `data` 可以为 `el` 所对应的 DOM 初始数据

            },
            methods:{
                // 事件回调
                parent:function(){
                    console.log('父盒子');
                    
                },
                child:function(){
                    console.log('子盒子');
                    
                },
                send:function(){
                    console.log('小楷书');   
                }
            }
        })
        
    </script>c
```

* 响应式数据绑定

  * 数据绑定有单向和双向之分，具体是指数据的流向。

    ​	单向，模型 ------> 视图

    ​	双向，模型 <------> 视图

  * 单向响应式一种自动机制，即一方发生改变，立案一方也相应最初改变

```html

<body>
    <div id="btn">
        <!-- 单向响应 -->
        <h1>{{msg}}</h1>
        <button @click='changedata'>点击改变视图</button>
    </div>
</body>
<script src="./libs/vue.min.js"></script>
<script>
    // 实例化对象可以直接访问模型中的（data）数据
    // 还可以直接访问methods中的方法
    // 语法：VM.属性名
    var vm = new Vue({//Vue的v大写
        // 指定vue的管辖范围，可以是css标签，也可以是DOM节点,建议使用id选择器
        //如果标签同样，那么只对第一个生效
        el: '#btn',//el所对应的元素不可以是HTML或body,必须写的属性
        data: {//通过 `data` 可以为 `el` 所对应的 DOM 初始数据
            msg: '我是个标签体'
        },
        // 当data中定义了和methods中相同的属性时。以data为准，methods不允许重复
        methods: {
            // methods中定义的方法，不允许使用箭头函数
            changedata:function(){
                // this 指向实例对象
                // 访问模型中的（data）数据
                this.msg='我是新来的'
                // 访问methods中的方法
                this.demo();
            },
            demo:function(){
                console.log('我是安其拉');
                
            }
            
        }
    })

</script>

```



​	双向响应式

- 表单元素在 html 中具体特殊意义，它的主要作用并不是展示数据，更多的是收集用户填写的数据，因此表单元素也就成为了数据的提供方了，通过修改表单中的内容，实现模型中 data 数据的变化。
- 为表单元素添加 `v-model` 可以实现数据的双向绑定。

```html
<body>
    <div id="btn">
       <!-- 数据的双向绑定 -->
       <h3>{{txt}}</h3>
        <input type="text" v-model='txt'>
        <button @click="checkdata">查看是否改变数据</button>
    </div>
</body>
<script src="./libs/vue.min.js"></script>
<script>
    // 实例化对象可以直接访问模型中的（data）数据
    // 还可以直接访问methods中的方法
    // 语法：VM.属性名
    var vm = new Vue({//Vue的v大写
        // 指定vue的管辖范围，可以是css标签，也可以是DOM节点,建议使用id选择器
        //如果标签同样，那么只对第一个生效
        el: '#btn',//el所对应的元素不可以是HTML或body,必须写的属性
        data: {//通过 `data` 可以为 `el` 所对应的 DOM 初始数据
            txt:'',
        },
        // 当data中定义了和methods中相同的属性时。以data为准，methods不允许重复
        methods: {
            // methods中定义的方法，不允许使用箭头函数
            checkdata:function(){
                console.log(this.txt);
                //  console.log(vm.txt);
                 
            },
    })

</script>
```

#### 结构

​		动态网站的页面结构是根据数据展示的需要动态创建的，**vue 具备动态创建页面结构的能力。**

- 条件控制

  1. `v-if和v-show的区别`

     1. 两者在视觉上并没有什么区别，都是显示和隐藏

     2. 但`v-if`是通过添加或移除DOM节点来实现的，v-if会导致DOM树中的节点的数量变化，开销比较大

     3. `v-show`是通过css的display属性值的（block/none）实现的，开销比较大

        注意：对于操作较为频繁的显示/隐藏操作，建议使用 `v-show`，相反建议使用 `v-if`

        另外 `v-if` 是惰性的，如果其值为假，则内部所有元素都不会被渲染。

```html
<body>
    <!-- 属性值为布尔类型，如果不写值默认为true 如果你不写值，默认为false-->
    <div id="btn">
        <!-- v-if: 隐藏时，是直接将整个节点删除 
             适合只点击一次的场景
         -->
        <p v-if='searn' @click='btn'>{{msg}}</p>
        <!-- v-show 隐藏是通过样式来进行隐藏 
            适合多次点击显示或隐藏 
        -->
        <p v-show='searn' @click='btn'>{{msg}}</p>
    </div>
</body>
<script src="./libs/vue.min.js"></script>
<script>



    new Vue({//Vue的v大写
        // 指定vue的管辖范围，可以是css标签，也可以是DOM节点,建议使用id选择器
        //如果标签同样，那么只对第一个生效
        el: '#btn',//el所对应的元素不可以是HTML或body,必须写的属性
        data: {//通过 `data` 可以为 `el` 所对应的 DOM 初始数据
            msg: '我又来了',
            searn: true,
        },
        methods: {
            btn: function () {
                this.searn = false;
            }
        }
    })
</script>
```

* v-if和v-else的使用

```html
body>
    <!-- 属性值为布尔类型，如果不写值默认为true 如果你不写值，默认为false-->
    <div id="btn">
       
        <p>我叫{{name}},今年{{age}}
            <span v-if="age >= 18">成年了</span>
            <!-- 条件判断 -->
            <span v-else>未年了</span>
            <br>
            <!-- 双向响应 -->
            <input type="text" v-model='age'>
        </p>
    </div>
</body>
<script src="./libs/vue.min.js"></script>
<script>



    new Vue({//Vue的v大写
        // 指定vue的管辖范围，可以是css标签，也可以是DOM节点,建议使用id选择器
        //如果标签同样，那么只对第一个生效
        el: '#btn',//el所对应的元素不可以是HTML或body,必须写的属性
        data: {//通过 `data` 可以为 `el` 所对应的 DOM 初始数据 
            name: '小明',
            age: "14"
        },
    })
</script>
```

* v-if和v-else-if和v-else的使用

```html
<body>
    <!-- 属性值为布尔类型，如果不写值默认为true 如果你不写值，默认为false-->
    <div id="btn">
        <!-- v-if和v-else-if和v-if的使用 -->
        <p>成绩{{sect}}
            <span v-if="sect >= 90">优秀</span>
            <!-- 条件判断 -->
            <span v-else-if='sect>=70'>良好</span>
            <span v-else>差</span>
            <br>
            <!-- 双向响应 -->
            请输入成绩：<input type="text" v-model='sect'>
        </p>
    </div>
</body>
<script src="./libs/vue.min.js"></script>
<script>



    new Vue({//Vue的v大写
        // 指定vue的管辖范围，可以是css标签，也可以是DOM节点,建议使用id选择器
        //如果标签同样，那么只对第一个生效
        el: '#btn',//el所对应的元素不可以是HTML或body,必须写的属性
        data: {//通过 `data` 可以为 `el` 所对应的 DOM 初始数据
  
            sect:90
        },
    })
</script>
```

* v-for循环遍历数组

```html
<body>
    <!-- 属性值为布尔类型，如果不写值默认为true 如果你不写值，默认为false-->
    <div id="btn">
        <ul>
            <!-- 遍历数组 -->
            <li v-for="item in list">{{item}}</li>
        </ul>
            <!-- 遍历对象 -->
        <p>
            <span v-for='item in user'>{{item}}</span>
        </p>
    </div>
</body>
<script src="./libs/vue.min.js"></script>
<script>



    new Vue({//Vue的v大写
        // 指定vue的管辖范围，可以是css标签，也可以是DOM节点,建议使用id选择器
        //如果标签同样，那么只对第一个生效
        el: '#btn',//el所对应的元素不可以是HTML或body,必须写的属性
        data: {//通过 `data` 可以为 `el` 所对应的 DOM 初始数据
            list:['牛肉','羊肉','狗肉'],
            user:{
              name:'小明',
              sge:23  
            }
            
        },
    })
</script>
```

* key的使用
  * `vue`中在进行模板渲染是，为了提高性能，它并不是每次都生成新的节点的，它会选择复用原来已经有的
  * 所以我们可以通过`key`来强制高数vue DOM要重新创建生成

```js
<body>
    <div id="app">
        <button @click='publish'>添加</button>
        <ul>
                <!-- Vue 中在进行模板渲染时，为了提升性能，它并不是每次都
                创建生成新的节点，它会选择复用（如果已经有）
            
                通过 key 属性可以强制告诉 vue dom 节点重新创建生成 -->
            <li :key='item.id' v-for='item in list'>
                {{item.name}} {{item.age}} {{item.gender}}
            </li>
        </ul>
    </div>
</body>
<script src="./libs/vue.min.js"></script>
<script>
    // 先实例化对象
    new Vue({
        // 视图 可以在视图的范围内进行相应的操作
        el: '#app',
        // 模板。也可亦称之为数据
        data: {
            // 创建空数组，存储每次添加的数据
            list: [
                { id: 324, name: '小明', age: 18, gender: '男' },
                { id: 42, name: '小红', age: 16, gender: '女' },
                { id: 23, name: '小刚', age: 17, gender: '男' },
                { id: 41, name: '小丽', age: 18, gender: '女' },
                { id: 56, name: '小李', age: 19, gender: '男' }
            ],
            // 创建属性，接收输入的数据
            msg: ''
        },
        methods: {
            // 点击添加
            publish: function () {
                console.log(this.msg);
                console.log(this.list);
                // 将每次添加的数据放入数组中
                // this.list.push({ id: 324, name: '小明名', age: 18, gender: '男' });
                this.list.unshift({ id: 324, name: '小明名', age: 18, gender: '男' });
            },
        },
        mounted: function () {
            // console.log('页面加载了...');
            document.querySelector('li:nth-child(2)').style.color = 'red';
        }

    })

</script>
```

# 指令

* ## v-once

  * 只渲染一次，渲染之后，就不能再次使用了

```js
<body>
    <div id="app">
        <p>{{msg}}</p>
        <!-- v-once 只渲染一次 相当于禁用了单向响应-->
        <p v-once v-c>{{msg}}</p>
        <button @click='btn'>切换</button>
    </div>
</body>
<script src="./libs/vue.min.js"></script>
<script>
    // 先实例化对象
    new Vue({
        // 视图 可以在视图的范围内进行相应的操作
        el: '#app',
        // 模板。也可亦称之为数据
        data: {
            // 创建属性，接收输入的数据
            msg: '你又来了'
        },
        methods: {
            btn:function(){
                this.msg='nih-'
            }
        }
        
    })

</script>
```

* ## v-cloak

  * 解决vue渲染时的闪烁问题
  * 由于代码是自上到下执行的，所以vue来不及渲染时，就被浏览器显示出来，容易闪烁，
  * 所以我们可以通过v-cloak配合[v-cloak] {display: none;} 来解决，当然v-text 也是可以避免这个问题的，因为v-text是一个属性，即使是被浏览器解析也不会显示到页面

```js
<style>
    [v-cloak] {
        display: none;
    }
</style>

<body>
    <div id="app">
        <!-- v-once 只渲染一次 相当于禁用了响应式-->
        <p v-once>{{msg}}</p>
        <button @click='btn'>切换</button>

        <!--
	        由于代码自上向下解析执行，Vue 来不及渲染而导致 {{text}} 被浏览器显示出来
	        当 Vue 被执行后，才会将 {{text}} 解析并渲染
         -->
        <p v-cloak>{{msg}}</p>
        <!--
	        1. 通过 v-text 是可以避免这个问题的，原因是 v-text 是一个属性，即使被浏览器解析也不会显示到页面
	        2. 还可以通过 v-cloak 配合 [v-cloak] {display: none;} 来解决
        -->



    </div>
</body>
<script src="./libs/vue.min.js"></script>
<script>
    // 先实例化对象
    new Vue({
        // 视图 可以在视图的范围内进行相应的操作
        el: '#app',
        // 模板。也可亦称之为数据
        data: {
            // 创建属性，接收输入的数据
            msg: '你又来了'
        },
        methods: {
            btn: function () {
                this.msg = 'nih-'
            }
        }

    })

</script>
```

* ## v-model

  #### 修饰符

  ` .lazy `修饰符可以吧默认的input事件更改为change事件，可以在某种程度上节省性能，双向联动时可以在失焦后显示结果

```js
<!-- .lazy 修饰符可以把默认的input事件更改为change事件，
                    某种层度上可以节省性能 双向联动后是失焦出现结果-->

  <li>姓名: <input type="text" v-model.lazy='username'/></li>
```

* `.trim`修饰符可以去除两边的空格

```js
 <!-- .trim 修饰符可以去除两边空格 -->

 <li>密码: <input type="password" v-model.trim='pass' /></li>
```

* `.number`修饰符可以把值转换成数字类型（前提是能转）

```js
      <!-- .number 修饰符可以把值转换成数字类型，（前提是能转） -->

      <li>年龄: <input type="text" /></li>
```

```js
<!-- 
                    value 不可以省略 可以有checked或name(前提结合v-model使用)的作用 
                    结合v-model使用，获取的就是value里的值 提交的也是value里的值,会自动放入一个数组内
                -->
                <li>
                    爱好:

                    <input type="checkbox" value="睡大觉" v-model='hobby' /> 睡大觉
                    <input type="checkbox" value="写代码" v-model='hobby' /> 写代码
                </li>
                <li>
                    籍贯:
                    <!-- 在下拉列表内，value可以不写，但不建议省略 -->
                
                    <!-- 
                        如果指定的 value v-model 是以 value 为参照
                        如果不指定 value v-model 是以 option 文本为参照
                    -->
                    <select v-model.number='home'>
                        <option value="">请选择</option>
                        <option value="1">北京市</option>
                        <option value="2">河北省</option>
                        <option value="3">河南省</option>
                    </select>
                </li>
```

## 计算属性

* 字面上可以理解为，计算属性就是经过计算（一些逻辑）而得到的值
* 通过**计算属性**非常方便的解决了"不确定数据"的获取，而且计算属性也是响应式的。
* 如果使用计算属性时，数据是会有缓存的，某种程度上是有利于提升性能。

```js
<style>
    [v-cloak] {
        display: nonex;
    }
</style>

<body>
    <div id="app">
        <input type="text" v-model='val'>
        <button @click='findStudent'>查找</button>
        <div v-cloak v-if='student'>
            <!-- <div v-cloak v-if='student.length'> -->
            <!-- <span>{{student[0].name}} {{student[0].age}} {{student[0].gender}}</span> -->
            <span>{{student.name}} {{student.age}} {{student.gender}}</span>

        </div>
        <div v-cloak v-else>没有找到该学生的信息</div>
    </div>
</body>
<script src="./libs/vue.min.js"></script>
<script>
    // 先实例化对象
    var vm = new Vue({
        // 视图 可以在视图的范围内进行相应的操作
        el: '#app',
        // 模板。也可亦称之为数据
        data: {
            list: [
                { id: 324, name: '小明', age: 18, gender: '男' },
                { id: 42, name: '小红', age: 16, gender: '女' },
                { id: 23, name: '小刚', age: 17, gender: '男' },
                { id: 41, name: '小丽', age: 18, gender: '女' },
                { id: 56, name: '小李', age: 19, gender: '男' }
            ],
            val: "",
        },
        // 计算属性的选项
        computed: {
            // 字面上可以理解，计算属性就是经过计算（一些逻辑）而得到的值
            student: function () {
                // 该函数返回的值即为计算属性的值
                return this.list.filter((item) => {
                    // console.log(item.name);
                    return item.name == this.val;
                })[0]
            }
        },
        methods: {
            // 查找函数
            findStudent: function () {

            }

        }
    })

</script>

```

## 侦听器

* 在 Vue 中数据的变化是响应式的，这一切都由 Vue 内部自动处理，给开发者带来了极大的方便，然而某些复杂的场景（数据校验、异步请求等）**需要开发者能够监听到数据的变化并执行特定的逻辑。**

```js

<body>
    <div id="btn">
        <h1>{{msg1}}</h1>
        <input type="text" name="" id="" v-model='msg'>
        年龄：<input type="text" name="" id="" v-model='age'>

    </div>

</body>
<script src="./libs/vue.min.js"></script>
<script>
    new Vue({//Vue的v大写
        // 指定vue的管辖范围，可以是css标签，也可以是DOM节点,建议使用id选择器
        //如果标签同样，那么只对第一个生效
        el: '#btn',//el所对应的元素不可以是HTML或body,必须写的属性
        data: {//通过 `data` 可以为 `el` 所对应的 DOM 初始数据
            msg: '',
            msg1: '',
            age: '12',
        },
        // 对data里的数据进行监听
        watch: {
            msg: function (newdata, olddata) {
                // oldValue 是修改前的值
                // newValue 是修改后的值
                // 数据颠倒
                this.msg1 = olddata.split('').reverse().join('');
            },
            age: function (newage, oldage) {

                // if(newage != '') 

                if (newage != '' && !Number(newage)) {
                    this.age = oldage;
                }
            }
        }
    })

</script>
```

-[ ] 