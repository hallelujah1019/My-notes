# Vue.JS基础部分学习

## 第一天

### 1.初识Vue

- 1.Vue是什么

	-  构建用户界面的JavaScript渐进式框架
	- 模仿angular框架开发的
类似于angular
	-  可以用来构建SPA应用程序
SPA （Single web application） 
单页面应用程序  说白了就是网页不刷新
	- CDN：加速  缓存技术
	- Vue本身只是用于数据驱动视图更新的一个库

- 2.Vue的特点

	- MVVM

		- 特点：数据驱动视图的方式
		- Model  数据
		- View  视图
		- ViewModel   数据驱动视图   数据一变化，视图也就跟着变化
		- 面向数据式编程

	- 组件化

		- 通过组件化开发极大的提高了开发的效率和可维护行

- 3.Vue的优缺点

	- 上手简单
	- 简单的API
	- 轻量高效
	- 灵活的组件系统
	- 强大的生态系统 

		-  Vue Router
		- Vues
		- 等等一系列的系统

	- 开源
	- 号称屌丝福音

- 4.可以做什么

	-  一切和Web用户界面相关的都可以使用Vue来做
	- 对SEO没要求的应用
	- 更加侧重于单页面应用程序(SPA)开发
	- 单产品型的应用程序
	-  桌面应用程序
和其他技术想配合
纯Vue是写不出来的
	-  管理系统
	- 混合APP
	- 移动APP

- 5.一些资源

	- 官方文档
	- 官方仓库
	- 不要买书
	- 分支主题

- 6.Vue可以和jQuery库和其他类库使用

### 2.安装Vue

- 下包
npm  i  vue
在用 Vue 构建大型应用时推荐使用 NPM 安装
Vue的核心只关注视图层 el部分就是视图层，视图层也叫模板层
data叫数据或者叫模板
- 初识Vue

	- 第一步：npm i  Vue

		- 第二步：script标签引进来
<script src="../node_modules/vue/dist/vue.js"></script>
		- 第三步：每一个Vue程序都是以new Vue()开始的
<div id="app">
    <h1>{{ 1 + 1 }}</h1>
    <h1>{{ foo }}</h1>
  </div>
<script>
     new Vue({
	    //   el告诉Vue的启动入口节点在哪里或者理解成哪一部分归Vue管
	    el: '#app',
	    data: {
	       foo: 'bar',
	      }
      })
</script>
		- 第四步：每一个Vue实例都是接收一个选项对象用来配置Vue应用
		- 第五步：选项的el属性，用来告诉Vue的启动入口节点
凡是入口节点中的所有节点就可以使用Vue的语法了可以理解成Vue是高级的模板引擎
		- 第六步：Vue中的模板对象数据是通过data选项来指定
		- 注意：el不能挂载到html和body元素，只能是挂载一个普通元素，所以一般我们的页面一开始就来一个div#app  el的值可以是CSS选择器，但是建议选择id选择器，如果选中了多个标签，那么只对第一个生效，el的值也可以是DOM节点，例如：
el:document.querySelectorAll('div')[1];
只不过这种方式很少用

	- Vue中的属性值如果是布尔值时，一般如果不写的话，那么默认为true，但是v-show这个属性有些特殊，v-show的默认值是false
例如：<p v-show/v-show="">看着路世界真滴大</p>--->默认值是false
所以一般在工作中，我们不应该过渡依赖默认值，所以我们使用属性的时候都要给定值。
	- 要想将数据展示到标签内部我们可以使用v-text和{{mag}}这两种方式都可以
v-text其实封装的是js中的innertext属性，v-text是专门对文本进行绑定的
<p v-text="msg"></p>--->浏览器不闪，为什么这么写不闪呢，因为这个v-text是写到标签中的属性，所以浏览器不会闪一下。
或者
<p id="pp">{{msg}}</p>--->加载的时候浏览器会闪烁一下，因为浏览器是从上到下记性加载的，先指向HTML标签中的内容，在执行Vue中的逻辑代码。所以才会浏览器加载的时候会闪一下。
js：
new Vue = ({
   el:'#dd',---视图
   data:{
       msg:'我是一个p标签',
   }
})
标签中的属性值是通过Vue对象中的data属性进行操作的。
	- el只能是挂载单一节点
	- el data completed methods watch 等等这些都是实例选项，不同选项具有不同的作用
	- data中的数据不是普通数据，这种数据我们称之为响应式数据，用来驱动视图更新的数据

### 3.数据绑定

- data中几种数据类型初始化的几种方式：
数字：num:0,  数字的初始化为一个0
字符串：str:'',  字符串的初始化为一个空字符串
布尔值：isSeen：false， 布尔值的初始化为false
数组：arr:[],  数组的初始化为一个空数组
对象：obj:{}  /  obj:null;   对象的初始化为一个空对象或者是一个null
对于对象的修改：
1.没有初始化的对象成员如果修改不会更新视图
2.也有方式可以动态添加未初始化的数据成员并且能更新视图（稍后讲）
3.直接对对象进行重新赋值可以实现视图的更新。例如  app.obj={a:123};
   对于对象中不存在的成员，浏览器不会报错儿，会是undefined，已经初始化的都可以正常更新，没有初始化的不能直接修改数据更新视图。
那怎么可以对没有初始化的成员动态更新到视图上呢？
Vue.set(参数1，参数二，参数3)；
参数一：app下的对象  例如： app.user
参数2：需要添加的属性名   'gender'
参数3：新添加的属性名的属性值
- 什么是数据绑定：
模型中的数据与视图的对应关系就是数据绑定。
- v-bind是专门对属性进行绑定的
v-text是专门对文本进行绑定的
- Vue只关注v-开头的属性，不是以v-开头的就默认是标签固有的标准属性，不归Vue管理
- v-bind:title='title'--->v-bind是对属性的绑定
例如：<p v-bind:title="title">{{title}}</p>
new Vue({
    el: '#app',
    data: {
      title: '我是一只小青龙',
    }
  })
F12中显示的是：
<p title="我是一只小青龙">我是一只小青龙</p>
title起到的作用是鼠标放上去显示对内容的解释
- v-bind:style = "{}"--->v-bind：style这个数据绑定比较特殊，接收的是一个  对象类型
<p v-bind:style="{color:'red,height:123px,'}">这是一段带文字的段落</p>
属性和属性之间用逗号分开，但是我们很少使用这种方式写
- 我们一般使用这种方式
<p v-bind:style="styleObject">这是一段带文字的段落</p>  
new Vue({
   data:{
        styleObject:{  --->一定要写到data中，因为data是管理数据的
                      color:'red',
                      background：'blue',
              }
    }
})
- v-bind:class 语法也是比较特殊的，同样接收一个   对象类型   ，对象的属性为真实存在的类名，对象的值为布尔类型 如果为true则添加属性对应的类名，如果为false，则不添加属性。这里的这个dome就是一个真实存在的一个类名例如：                              style中写.dome{color:pink}
<p v-bind:class="{dome:false/true}">这是一段带文字的段落</p>
<p :class="{dome:false/true}">这是一段带文字的段落</p>--->还可以简写
将v-bind省略掉
font-size,background-color这种有中横线的我们要写成fontSize，backgroundColor
- 样式也可以使用数组的形式书写，作为了解
<style>
     .act {
      color: blue;
    }
    .err {
      font-size: 50px;
    }
</style>
<div :class="[active,error]">下个路口再见吧</div>
data:{
   active: 'act',
      error: 'err',
}
- 总结：
:class
:style
这两个属性后面接收的都是一个对象类型  ：冒号是v-bind的简写
- p{{list[0]}}p
data:{
   list:[html,css,js]
}
- p{{user.name}}{{user.age}}p或者p{{user['my-sex']}}p
data:{
  user:{
    name:'小明',
    age:18,
    my-sex:'男'
  }
}
- 在浏览器控制台中可以获取到data中数据
vm.name或vm.$data.name

### 4.事件的绑定

- 语法：v-on:click="回调函数"
v-on：click、change、blur、fouce
- new Vue({
  //Vue提供的专门定义方法的参数  methods
  //也可以定义事件函数的回调
  methods:{
      clicked：function(){},
   },--->方法和方法之间用逗号隔开
   in:function(){}
})
- v-on可以删掉用@符号代替
@事件名称=“回调函数”
-  // 回调函数写到methods里面，里面还是可以传参数的，js中参数怎样传，这里面就怎样传
<input type="text" @focus="fac" @blur='blu' />
methods: {
      fac: function() {
        console.log('获取到了焦点');
      },
      blu: function(me) {
        console.log(me + '失去了焦点');
      }
    }
- 当事件被触发时，可以将事件对象以参数形式传递，$event在vue中是具有特殊函数的内容，在这里表示事件对象$event表示事件对象
<input type="text" @focus="fac($event)" />

	- <div id="app">
    <input type="text" @focus="click(a,$event)">
    <a href="#" @click="clicks(b,$event)">来吧点我一下</a>
  </div>
</body>
<script src="./js/vue.js"></script>
<script>
  new Vue({
    el: '#app',
    data: {
      a: 10,
      b: 20,
    },
    methods: {
      click: function(a, e) {
        console.log('我是一只小青龙');
        console.log(a, e);
      },
      clicks: function(b, e) {
        console.log("我被点了");
        console.log(e, b);
        // 超链接点击之后，改变当前被点击的DOM节点的颜色
        e.target.style.background = 'blue';
        e.target.style.color = 'yellow';
      }
    }
  });
</script>

- Vue中的冒泡机制

	- 在vue中通过修饰符来解决事件执行时的一些特殊逻辑问题，如组织冒泡
如获取按键信息，这些都是通过事件修饰符来获取；
	- 语法是：
在事件名称后添加一个   .    点，即为修饰符
v-on:事件名. 修饰符=“函数”;
@click.stop = "函数";--->阻止冒泡机制的语法
	- @keyup.13 = "send"/@keyup.shift.enter = "send"
回车的keycode是13   .shift.enter是回车+shift同时按下

- 在Vue中，有且只有v-bind和v-on有简写，其他的属性都没有简写
v-bind简写为   ：  冒号
v-on简写为   @   艾特
- var vm= new Vue({})
事件处理函数中的this指向的是Vue的实例对象，也就是vm。
- 注意：事件处理函数不能使用箭头函数定义，因为在methods中的this指向的是window
- 当处理函数的代码只有一句的时候，我们可以直接写到模板中：注意这里不需要加this。
例如：
 <h1>{{message}}</h1>
<button @click="message='hello'">测试</button>
如果想改变h1中的内容时，我们就直接在button中写逻辑即可
- 属性格式
- 以下几点：都会触发表达提交行为：
点击type=submit的input
点击表单中的普通按钮
在文本框汇总敲回车
更建议的是使用form的submit事件来注册表单提交处理函数
例如：  阻止了按钮的默认行为，将事件注册给form标签中
<form @submit.prevent="onSubmit"></form>
- 按键修饰符：
@keydown.enter    回车
@keydown.tab    tab键
@keydown.delete   删除键
@keydown.esc   取消键
@keydown.up   
@keydown.left
@keydown.right
@keydown.space
@keydown.up
@keydown.down
@keydown.ctrl
@keydown.alt
@keydown.shift
@keydown.meta---windows键盘中指的是alt键旁边的田字键

### 5.响应式的数据绑定

- 实例化对象  可以直接访问模型中的数据
var vm  = new Vue({
  data:{
    msg:'数据初始化',
   }
});
console.log(vm.msg);
- methods:中的this指向的是Vue实例（实例对象）
- 实例对象vm不但可以直接访问模型(data)中的数据，还可以访问methods中的方法
- 注意：以下两种情况都不会更新视图：
  1.当你利用索引值直接设置一个数组项时，不会更新视图  例如：vm.items[index] = newValue;   
解决方案：Vue.set(参数一，参数二，参数三)；
参数1：实例数组；
参数二：索引值；
参数三：你要修改的那个数组新值
  2.当你修改数组长度的时候，也不会更新视图--->了解即可

### 6.双向数据绑定(比较重要)

- 要实现数据双向绑定，必须要有form表单元素相结合
- <input type="text" v-model="text">
v-model就能获取到用户输入的信息

	- <div id="app">
    <input type="text" v-model="text">
    <h1>{{text}}</h1>
  </div>
</body>
<script src="./js/vue.js"></script>
<script>
  var vm = new Vue({
    el: '#app',
    data: {
      text: '',
    },
  });
</script>

- data中定义了属性，methods中就不能定义与data中的属性相同的方法
- methods中定义的方法不允许使用箭头函数
- v-model是将视图的数据流向模型
v-text，v-html是将模型中的数据流向视图
- v-model如果作用到输入框中时，在vue底层中其实就是监听的是input事件

### 7.条件渲染  结构

- v-if 是根据绑定数据的真假来决定是否渲染（在视图中展示）这个元素
v-if是真正的条件渲染。
- v-if  先写
v-else-if  再写
v-else  最后写
这三个必须是同级，必须得配对儿
v-if和v-else之间不能出现其他标签，否则会报错儿
这个其他标签指的是不带v-if/v-else的标签，如果v-if和v-else之间出现了其他的v-if/v-else的标签，浏览器是可以解析的

	- <p v-if="age<18">我小于18</p>
    <p v-else-if="age>18">我大于18</p>
    <p v-else>我等于18</p>  --->最后这个v-else不需要再写值了
	- 错误示范：
<p v-if="1===1">hello</p>
<p>哈哈哈</p>
<p v-else>world</p>
	- 正确示范：
<p v-if="seen">hello</p>
   <p v-if="1===1">哈哈哈哈</p>
   <p v-else>456</p>
<p v-else>world</p>

- v-show我们叫条件显示
工作中使用v-show而不使用v-if
如果使用频率一直是显示隐藏显示隐藏，那么我们就使用v-show 这个方法是在标签中加了属性 display=none  所以节点还是在的
如果将dom节点删掉再也不出现，那么我们就使用v-if
- v-show不能结合v-else使用，v-if只能和v-else结合使用
- v-if和v-show的区别：
v-if条件渲染，如果条件为false，则不渲染元素
    true渲染DOM
    false不渲染DOM
v-show条件显示，无论条件的真假始终都渲染元素
    true渲染DOM
    false渲染DOM，不显示(disply:none)
    不能和v-else、v-else-if结合使用
- 遍历数组
v-for=“key in arr”
<li v-for="key in arr">key</li>
<li v-for="（item,name,index） in arr">{{index}}-{{item}}</li>
这里的name表示的是对象中的键名

### 8.input事件

- 只要一输入内容的时候就触发了这个事件，输入内容的过程中就是一直在触发这个事件

### 9.关键字

- in
- delete

### 10.Key的使用（重要）

- key是vue提供的一个特殊属性
key的数据类型必须是数字或者字符串儿
key的值不能是数组或对象或者布尔值。
- Vue中在进行模板渲染时，为了提升性能，它并不是每次都有创建成新的节点，它会复用已经创建的DOM节点
- key是用来区分标签名一样的DOM节点
- 通过key属性可以强制告诉vue DOM节点重新创建生成一个DOM节点
- v-for都要加上key，但是key的值不能是数组中的索引值，我们一般使用id值。
key是一个唯一的值。
- v-for是否重新渲染取决于key的值是否是变动的，如果是不变的，那么就不重新渲染
如果key的值也是变的，那么就需要重新渲染。

### 11.当需要遍历多个元素而又不想添加额外的元素节点的时候我们就使用
<template v-for="item in todos/i in 10">
   <p :key="item.id">id:{{item.id}}</p>
   <p :key="item.id">title:{{item.title}}</p>
</template>
注意：template中不能添加key，需要将key添加到真实的DOM节点上  
template这个标签在浏览器中是渲染不出来的，不把template这个标签当做一个DOM节点来解析  template这个标签是Vue提供的一个标签，浏览器并不会解析这个标签 template是Vue中特殊提供的一个元素。

- template与v-if相结合
当想要控制多个同级元素的渲染的时候，如果不想增加额外的DOM节点，我们就使用template这个标签
- 注意：在template中使用v-show是无效的，只能是使用v-if和v-for才能有作用

### 12.表单输入绑定

- v-model最常用的需求就是提交表单
问题：如何获取表单数据
- 对于普通文本框：
v-model文本框：
1.它会把数据绑定到input的value属性中
2.当input中输入改变的时候，它会自动把数据重新赋值给data中响应的参数。

### 13.绑定复选框

- 复选框一般是绑定一个布尔值来决定是否选中，true是选中，false是没有选中
<input type="checkbox" v-model="check">
data:{
  check=true,
}

### 14.绑定单选框

- 单选按钮，它会把value===数据的radio设置为被选中状态
视图改变的时候，它会把用户选中的radio的value同步到data中的数据中。
<input type="radio" name="gender" value="男" v-model="gender">男
<input type="radio" name="gender"  value="女" v-model="gender">女
data:{
  gender:'男',
}

### 15.选择下拉框数据绑定

- <select v-model="city">
    <option value="上海">上海</option>
    <option value="北京">北京</option>
    <option value="天津">天津</option>
    <option value="深圳">深圳</option> 
</select>
data:{
   city:'上海'
}
- 1. 数据更新视图，它会找到option中的value=city元素项，设置选中状态
2.视图更新数据，它会把选中的那个option的value同步到数据中。

## 第二天

### 1.指令

- 指令是带有v-开头前缀的特殊特性，这里的特性就是属性
- mounted ： 在这发起后端请求，拿回数据，配合路由钩子做一些事情 （dom渲染完成 组件挂载完成 ）
- v-once  只执行一次

	- <p v-once>{{text}}</p>

- v-cloak 阻止闪烁

	- style标签中需要写：
<style>
    <--使用属性选择器-->
   [v-cloak]{
   display:none;
   }
</style>
一般我们就是将这个v-cloak放到#app的div中
 <div v-cloak id="app">
    <h1>{{msg}}</h1>--->这里说的闪烁其实就是说的就是页面加载的时候标签中的内容{{msg}}在页面上不闪烁，这里说的闪烁并不是不刷新的意思。
 </div>

- v-pre  这个指令表示的意思是，标签加了这个属性之后，表示该标签就不会被Vue程序进行解析了
- v-model  重要的一个指令
常用的三个修饰符
.lazy
.number
.trim

	- v-model.lazy---->监听的是change事件
内容改变的时候，触发change事件，加上了.lazy某种程度上可以提升性能
<h1>{{username}}</h1>
<input v-model.lazy="username"></input>
data:{
  username:'',
}
当文本输入框失去焦点的时候，就触发了.lazy事件，将v-model获取到的文本输入框中的内容添加到h1标签中，但是前提是模型中要有一个username这个数据；
	- v-model.number  将字符串的数字转成number类型
	- v-model.trim  清除两端的空格儿
密码：<input type="password" v-model.trim="pwd">
	- 如果是多选框，数据类型将定义为数组
	- 下拉框中的option的value属性不建议省略
<select>
   <option value="">请选择</option>
   <option value="1">北京市</option>
   <option value="2">天津市</option>
   <option value="3">上海市</option>
</select>
如果不指定value值，那么就以文本内容为参照
如果指定了value值，那么就以value值为参照

- 指令动态参数

	- <img v-bind:[aaa]="这是一个图片">
<p v-bind:[aaa]="msg">学习：Vue</p>
data:{
  aaa:'title',
  msg:'学习Vue.js',
}
	- 如果属性绑定的值为一个动态的（即一个变量）
那么这个变量就用中括号来包裹[  ]
	- <input @[myevent]="函数" type="text">
data:{
  myevent:'input',
}--->事件名也可以做成变量

### 2.计算属性
computed中的数据是动态的
data中的属性是静态的

- 如果页面中的数据有不确定，我们可以使用计算属性来做
计算属性是只计算一次，然后把结果缓存起来，使用的时候直接使用缓存的数据即可。
- 计算属性特点：
计算属性会把执行之后的结果缓存起来，多次使用结果的时候，就直接从缓存中获取即可。
注意：计算属性不是方法，更不能当做事件处理函数使用，只要是事件处理函数的逻辑，肯定是在methods中调用函数。计算属性一定要有返回值，返回值就是属性的值，它的值可以在函数中通过更多的自定义的代码逻辑来实现。
- 计算属性本质是方法，但是只能是当做属性来访问，不能当做方法来调用
- //计算属性的选项，和data methods平级  
computed：{
     //从字面上理解，所谓的计算属性是要经过计算
    //才能得到的值  该函数的返回值即为计算属性的值
   student:function(){

    },
}
- 一个函数的返回值当做一个变量
- 计算属性自带缓存机制，计算属性一定要有返回值。
- 初始化对象的时候我们使用null来初始化
- 只要是需要通过一段逻辑获取一个新的数据的需求，那就有优先使用计算属性

### 3.侦听器  watch：{}

- 和data平级的
data:{}
watch:{}--->侦听器
computed:{}--->计算属性
methods:{}--->函数
- watch:{
  对data中的msg进行侦听
  属性名：要监视的数据成员
  属性值是一个处理函数
  Vue会将数据改变的新值和旧值作为参数传递给处理参数
  作用：当被监视的数据发生变化的时候，它会自动调用处理函数
  注意：它不需要返回值，更不需要在模板中绑定的。
  这里的msg是data选项中的数据成员
  watch中的成员不是数据，不是用于模板绑定的，watch是一个功能特点
  msg:function(newData，oldData){
 		
  }
}
- 当需要根据数据变化执行一些特定业务逻辑的时候，可以使用watch监视来实现
- watch：{
  //watch中每当被监视的数据发生改变的时候，就会触发watch中的逻辑代码
    如果被监视的数据类型是数组的话，那么watch默认的是只监视数组中的元素的个数增加了或者减少了，如果数组中的元素内容改变了，watch默认是监视不到的，所以
    这里例如  arr   是个数组，逻辑是每当arr数组中添加了元素或者删除了元素（可以这么理解，watch默认只要是arr数组中的元素个数发生了改变，就会触发watch中的逻辑代码）就将数组arr的数据存放到本地
   arr:{
     handler(){   --->handler(){}这是固定格式
      window.localStorage.setItem('token',);
    },
    //如果需要watch监视每个元素的中的内容是否发生了改变，其实也就是需要让watch进行深度监视，不光让watch监视数组的长度，还要watch监视元素的内容是否发生了改变，我们将这种监视称为深度监视，我们使用deep，默认deep是false，如果想要watch进行数组的深度监视，需要将deep的值改为true即可，deep适合handler同级的。
      deep：true，
  }
}

### 3.过渡&动画

### 4.实例属性

### v-model用于多个复选框的使用

### 实践建议：
所有的事件名称建议都起名为
onXxxx  例如：onAdd   onDel   等等。。

### e.target.checked   触发该事件的DOME元素，原生的CheckBox有一个属性checked可以获取选中状态。

### todosMVC项目步骤

- # 使用 Git 把模板下载到本地
$ git clone https://github.com/tastejs/todomvc-app-template.git
- # 切换到 todomvc-vue 目录中，安装依赖项
cd 下载的项目中

# 模板项目把样式等文件放到了第三方包里面了，所以我们要执行 npm install 安装它的那些依赖项才能正常的预览到这个项目页面
npm install   --->下载依赖
npm i vue
- 子主题 3

## 第三天

### 回顾：
无论通过什么方式来获取checkbox改变之后的状态，都建议使用change事件，不要使用click点击事件，因为点击事件触发的时候，checkbox的状态可能还没有改变呢。
通过事件对象来获取选中状态：e.target.checked
如果只是单纯的需要获取元素的选中状态，那么通过DOM获取就足够了
如果期望checkbox受Vue动态影响，那就要给它进行数据绑定。

### 1.和服务端通信
axios  也不操作DOM也不操作视图，这个第三方库就是用来收发送请求的。

- JSON-Server工具的使用

	- JSONServer
是一个提供测试环境接口的工具，它可以帮我们快速生成一套接口服务，专门用来学习测试
	- 第一步：安装JSONServer
npm install -g json-server
	- 第二步创建一个名叫json-server的文件夹，文件夹中创建一个文件
叫db.json，着这个文件中写入一下内容
{
  "posts": [
    { "id": 1, "title": "json-server", "author": "typicode" }
  ],
  "comments": [
    { "id": 1, "body": "some comment", "postId": 1 }
  ],
  "profile": { "name": "typicode" }
}
	- 第三步  开启服务
在json-server目录下执行以下命令
      json-server --watch db.json
如果看到了以下信息，说明就开启了服务
Resources
  http://localhost:3000/posts
  http://localhost:3000/comments
  http://localhost:3000/profile

  Home
  http://localhost:3000
	- 按照这套服务的接口文档
业务    请求方式                    请求地址                                                           
增        POST         http://localhost:3000/users/
删        DELETE      http://localhost:3000/users/1--->表示的是id
改        PATCH       http://localhost:3000/users/2 --->表示的是id
查        GET            http://localhost:3000/users/
只有当删和改的时候需要在请求地址中传id，增和

- axios第三方库的使用
axios也是异步请求

	- 先下载
npm install axios
	- 增  POST请求
axios({
  method:'POST',
  url:'http://localhost:3000/users',
  data:{
    name:"张三",
    age:18,
    gender:"男"
  }
}).then(function(res){
     console.log(res);
});
	- 删
axios({
   method:'DELETE',
   url:'http://localhost:3000/users/2',
}).then(function(res){
   console.log(res);
});
	- 改
axios({
   method:'PATCH',
   url:'http://localhost:3000/users/2',
   //数据放到data中
   data:{
     name:'名字',
   }
}).then(function(res){
   console.log(res);
});
	- 获取指定条件的数据

		- 请求方式  GET
请求路径  /users
请求参数   
    Query（查询字符串参数）
     name
     age
     gender
http://localhost:3000/users?name=栗子
http://localhost:3000/users?age=18
http://localhost:3000/users?name=张三丰&age=18
		- 代码实现指定条件查询数据     get参数往params中放     post参数往data中放
  var user = {  name='栗子'，age='20'}
axios({
   method:'GET',
   //如果是有条件的查询，那么我们使用params这种方式
   //url:`http://localhost:3000/users?name=${name}&age=${age}`
   //比较推荐这一种
   params:{
     name:   user.name,
     age:   user.age,
   }
}).then(function(res){
   console.log(res);
});

	- 配置axios参数

		-  // 配置请求的基地址
  axios.defaults.baseURL = 'http://localhost:3000/';
		- 例如：// 配置请求的基地址
  axios.defaults.baseURL = 'http://localhost:3000/';
  axios({
    method: 'GET',
    url: '/users',

  }).then(function(res) {
    console.log(res);
  });

	- axios错误处理

		- localhost:3000/users/50:1 PATCH http://localhost:3000/users/50 404 (Not Found)
		- 在axios中默认只有>=200和<400  的状态码都认为是成功的
		- axios.defaults.baseURL = 'http://localhost:3000/';
  axios({
    method: 'PATCH',
    url: '/users/50',
    data: {
      name: 'www',
    }
  }).then(function(res) {
    console.log('请求结果' + res);
  }).catch(function(err) {   --->使用catch捕获一下错误，function中需要传一个参数(erro)
    console.log('请求失败了！' + err);
  });
请求失败执行catch中的代码，请求成功之后执行then中的代码
catch捕获到的错误：
       请求失败了！Error: Request failed with status code 404

	- Vue中获取表单数据的方式：
视图：我们对每个表单元素都设置v-model属性
模型：在模型中根据接口和视图抽象出来数据初始化到data中
建议表单相关的数据放到一个单独的数据对象中
data:{
   user:{
     name:'',
     age:'',
     gender:'',
  }
}
	- 补充一个Vue的实例选项  created和data平级，create就是一个函数，这个函数在页面加载完毕之后就执行，我们可以在create中访问this获取Vue实例
created(){
/**
  axios({
    method:'GET',
    url:'/users',
  }).then(res=>{---->重要：create的then中一定要使用箭头函数，因为使用了箭头函数，this.users中的thi指向的才是Vue实例。
     console.log(res.data);
     this.users=res.data
   })
**/
//调用一下loadUser()方法
this.loadUser();
}
我们不太建议在create中写大量的业务逻辑代码，我们更推荐把这些功能都封装成一个一个的函数放到methods中。
methods:{
     loadUsers(){
           axios({
       method:'GET',
       url:'/users',
       }).then(res=>{---->重要：create的then中一定要使用箭头函数，因为使用了箭头函数，this.users中的thi指向的才是Vue实例。
         console.log(res.data);
         this.users=res.data
        })
     }
  }
}

## 第四天

### 1.组件基础的学习

- 场景：
重复的结构，重复的逻辑，重复的变量 我们就可以抽取成一个组件。
- 给全局Vue对象注册一个组件  component()中有两个参数，第一个参数是组件名。
Vue.component('span-btn',{
   template:  `<div>
                         <span>{{count}}</span>
                         <button @click="changeCount">按钮</button>
                  </div>`,
                  data(){
                            return{
                                       count:0
                                       };
                            },
                  methods:{
                               changeCount(){
                                                         this.count++;
                                                      }
                                }
});--->template中的DOM有且只有一个根节点
- 全局注册组件:  全部实例共享组件
Vue=>全局对象=>Vue.component()  在Vue全局对象上注册一个全局组件
new Vue( el:'app' )
new Vue( el:'app1' )
所有的Vue实例就都可以使用这个全局组件
- 局部注册组件：只有在当前实例可以使用组件
- 组件的特点：
1.  如果是全局组件  应该写在实例化之前
2.Vue.component(组件名，组件对象);
    组件名的规范："abc单词模式"/"abc-d双词模式"    全部小写
    例如：Vue.component("eight-eight",{
    //组件对象 
    //  template中的模板中一定要注意，模板中有且只有一个根节点/根元素  template代表页面结构
    template：`<div>
                             <span>你好，组件</span>
                              <p>{{name}}</p>
                      </div>`，
                   //data是一个带返回值的函数
    data:function(){
              data中返回一个对象
              return{name:"字节跳动"};
    },
    methods:{},
    computed:{},
    monted:{},
    created:{},
    watch{},
                    
});
3.组件是一个特殊的Vue实例
- 局部组件：需要在当前实例上注册
var  vm  = new Vue({
    //compontnts和data，methods同级
    compontnts:{
        //key：value  形式
       //key表示是的组件名   value表示的是组件对象
      “abc-d”:{
               template:`<p>我最厉害</p>`
                  }
     }
});

	- 局部组件在谁的实例上注册，就只能在谁的实例上使用

- 局部组件的结构
var vm = new Vue({
    el: '#app',
    // components中是以键值对的形式放的
    components: {
      "btn-count": {
        template: `<div>
            <button @click="cat">-</button>
            <span>{{count}}</span>
            <button @click="add">+</button>
        </div>`,
        data() {
          return {
            count: 0,
          }
        },
        methods: {
          cat() {
            this.count && this.count--;
          },
          add() {
            this.count++;
          }
        },
      }
    },
- 全局组件和局部组件的区别
注册位置不同，应用范围不同，全局的作用域范围更大
- 组件的嵌套
组件嵌套 就是在组件中使用其他组件
- 组件的通信

	- 父--->子   重要

		- 给谁传就在谁的标签上写属性，属性名随便写
		- 使用props是和template同级的，用来接收父传过来的数据
props：["属性名"]  --->字符串的数组

	- 子--->父
	- 子--->兄弟子

### 单页面应用--SPA

- spa优点：
1.用户体验好，因为前段操作几乎感受不到网络的延迟
2.完全组件化开发，由于只有一个页面，所以原来属于一个个页面的工作被归类为一个个组件
- spa缺点：
1.首屏加载慢，按需求加载，不刷新页面，之请求js模块
2.不利于SEO-->服务器渲染
3.开发难度高（框架）有一些学习成本和应用成本
- SPA实现原理
- Vue-router需要下载
- 组件：一个.vue文件就是一个组件
路由：地址发生改变，切换组件，但是页面不进行刷新

### vue-router 动态路由

- 引入vue-router的js文件
- 定义导航
<router-link></router-link>
- 定义容器
<router-view></router-view>
- 实例化vue-router
var router = new VueRouter({
   routes:[
       //动态路由传参
       //定义动态路由参数  
    {
     path:"/company/:companyname",
     component:{
          template:`<div>我从黑马毕业之后想去：</div>`
        }
     }
 ]
})
- $route.params.companyname
解释：$router.params可以获取到所有动态数据传过来的集合

### vue-router  to的属性赋值

### vue-router的重定向

- 拦截谁就在谁的路由上写redirect
- redirect: '/beijing',

### vue-router编程式导航

- 导航可以不要，容器必须要
<router-view></router-view>  必须要
- push是从原纪录中推送一条数据
replace是替换一条数据，使用replace自始至终都只有一个数据
go是前进或后退一条记录  go(-1/1)  
-  methods: {
            gochaoyang() {
              // 使用replace的时候是将地址进行了替换，始终保存的是一个地址
              //   this.$router.replace("/chaoyang");
              this.$router.push("/chaoyang");
              //   this.$router.go(1);
            }
          },

### 激活路由样式

- <style>
    .router-link-active {
      font-size: 50px;
      color: aqua;
    }
  </style>
- 直接就在style标签中写.router-link-active这个类名就可以啦

### 嵌套路由

- 二级导航的导航和容器要在一级的组件中配置
- 还有children选项，这个选项中写二级导航的路由表

## 第五天

### 1.Vue-cli工具（脚手架）

- 是一个命令行工具
- 安装
npm i -g @vue/cli
查看版本
vue -V（大V）
或者
vue --version
- 安装桥接工具将2.0的功能不起到4.0的脚手架上
npm install -g @vue/cli-init
//卸载包
npm uninstall @vue/cli-init
- 解决下载包不成功的问题，因为npm的服务器在国外
在百度中输入cnpm
点开淘宝镜像 
复制npm install -g cnpm --registry=https://registry.npm.taobao.org，回车执行
以后下包的时候直接写cnpm即可
cnpm i -g @vue/cli

### 2.使用vue-cli创建项目

- vue init webpack-simple heroes       heroes是一个项目名，自定义的名
- 创建项目: 采用 cli 2.0的特性 (生成简易模板)

	- #  heroes 创建的项目名称
$ vue  init webpack-simple heroes //  webpack-simple 为模板名称 固定写法
# 切换到当前目录
$ cd  heroes 
# 安装依赖
$ cnpm install  
# 在开发模式下 启动运行项目
$ npm run dev
如果浏览器没有自动打开，也可以手动打开浏览器，在地址栏写：http://localhost:8080/  回车即可

- 在heroes文件夹下打开powerShell命令工具
安装一个bootstrap的固定版本  这个是一个运行时依赖
npm i bootstrap@3.3.7
安装完毕后需要看一下dependencies中有没有"bootstrap": "^3.3.7",如果有的话，就说明安装成功了。
"dependencies": {
    "bootstrap": "^3.3.7",
    "vue": "^2.5.11"
  },

	- 运行时依赖
npm i 包名 -S或者--save  是安装运行时依赖  -S和--save在npm中是可以省略的，但是在cnpm中是不可以省略的cnpm i 包名 -S或者 --save

开发时依赖
npm i 包名 -D或者--save--dev 是安装开发时依赖

- 安装完成bootstrap之后 ,在main.js入口处引入css文件
// 在main.js中引入bootstrap的css文件和index.css文件
import from '../node_modules/bootstrap/dist/css/bootstrap.css';
import from './style/index.css'  --->这个index.css样式在模板的静态页面中的css文件夹中放着，style文件夹是在src文件夹下新建的文件夹，专门用来放我们的样式文件
- 安装了bootstrap后会报错儿需要配置一下
{
test: /.(ttf|woff2|woff|eot)$/,
loader: "file-loader",
options: {
name: "[name].[ext]?[hash]"
}
}

- 提取一些公共的组件
头部-侧边栏-列表  并预览效果

	- 我们把头部内容单独抽成一个组件
记得要导出export default{}
	- 因为App.vue是所有组件的根组件，所以头部左侧和右侧的内容抽取成组件之后需要在App.vue中引入组件：
// 引入app-hader.vue文件
import apphader from './app-hader.vue'
// 引入app-left.vue文件
import appleft from './app-left.vue'
// 引入app-right.vue文件
import appright from './app-right.vue'
	- 引入之后需要还需要进行注册
export default {
  components:{
    // 注册头部组件
    "app-hader":apphader,
    // 注册左侧组件
    "app-left":appleft,
    // 注册右侧组件
    "app-right":appright,
  }
}
	- 以上两步做完后需要在div中写入标签
 <!-- 左侧导航 -->
        <app-left></app-left>
        <!-- 右侧导航 -->
        <app-right></app-right>

- 新建一个router.js文件
抽取路由模块

	- 因为没有vue-router这个插件我们需要先下载vue-router
	- 路由是需要安装到运行时依赖
cnpm i vue-router  -S
	- 安装完毕之后需要新建一个router.js文件这个文件就是专们放路由的代码
	- 要在这个包中先引入Vue的包
import Vue from  'vue'
	- 再在router.js中需要引入一下vue-router这个包
// 引入vue-router
import VueRouter from 'vue-router'  因为vue-router是一个包名，所以我们可以不用写路径，直接写包名即可
	- 在router.js中使用router  重要  这里的Vue是Vue中的全局对象
Vue.use(VueRouter) // 使用router  即可
	- 引入组件

		- // 因为建好了三个组件，武器组件  装备组件 英雄列表组件，我们可以引入进来
import wuqi from './app-wuqi.vue';
import zhuangbei from './app-zhuangbei.vue';
import yingxiong from './app-yinglist.vue';

	- 实例化路由

		- // 实例化一个vue-router实例
const vuerouter = new VueRouter({
  routes: [{
    path: '/heroes',
    component: yingxiong
  }, {
    path: '/wuqi',
    component: wuqi
  }, {
    path: '/zhuangbei',
    component: zhuangbei
  }]
});
导出实例
export default router;

	- 在main.js中引入router.js
// 引入router.js
import router from './router.js'
	- 在main.js中引入之后需要在Vue实例中挂载一下router
new Vue({
  el: '#app',
  render: h => h(App),
  // 挂载router
  router,
})
	- 因为router-link标签默认生成的标签是a标签，我们要改变一下默认生成的标签类型
<router-link tag="li" to="/heroes">  这个标签中有一个tag属性，默认是a标签，如果想要改变的话，就将想要生成的标签名写到里面就行啦
	- 在router.js中设置一下
// 设置一下激活样式
  linkActiveClass: 'active',
因为这个linkActiveClass的默认值是route-link-active，我们要改变一下这个值
export default new VueRouter({
  // 设置一下激活样式
  linkActiveClass: 'active',

- json-server启动接口服务器并安装axios

	- 在json文件下启动json-server
json-server --watch db.json 
	- axios是运行时依赖
cnpm i axios -S

- 列表渲染

	- 在app-yinglist组件中我们需要在data(){}中添加一个数据用来接收从服务器获取到的用户数据，data()是一个带返回值的函数
 data(){
        return {
            list:[],--->这里要知道为什么要在data中定义一个数组类型呢，因为在服务器中获取到的用户信息就是一个数组，所以我们要定义为一个空数组来接收一下用户信息。
        }
    },
	- 因为这个组件是当点击到这个页面的视乎就需要向服务器发送请求，所以我们要在created这个选项中先发送一个axios请求，这里请注意：因为当我编辑和删除的时候需要实时的看到我是否真的将用户信息进行了编辑和删除，所以我要将这个axios请求封装成methods选项中的一个方法，每当点击到用户列表页的时候，我就调用一下这个方法，当用户编辑或者删除用户信息的时候，我也调用一下这个方法，这样同样的逻辑就不用写多次了，直接调用方法即可。
这里说一下：created这个选项是当组件在页面中生成之后，就会执行created选项中的逻辑，所以我们要在这个选项中放发送请求，也就是执行（调用）以下发送axios请求的方法
	- 在methods选项中先封装一下获取所有用户信息的方法
methods:{
      loadDate(){
           //   this指向组件实例
            axios({
                method:'GET',
                url:'http://localhost:3000/user'
            }).then(res => {
                // 打印一下获取到的数据
                console.log(res.data);
                // 获取到内容之后，我们需要将获取到的内容给到data中的list
                this.list = res.data;  --->这里要知道，用户数组在返回结果中的data属性中存放，并且我们要知道data这个属性是一个数组类型，刚好，我们在data中定义的list也是一个数组类型，所以我们可以直接将返回结果res中的data直接赋值给到this.list，这里要特别注意，因为在函数中用到了this，并且我们要的这个this指向的是组件实例，所以返回结果中的函数我们要定义成一个箭头函数，因为箭头函数中this的指向是上下文中的this，这个外边的上下文中的this就是指向组件实例的，所以我们要将这个函数变成箭头函数。
                console.log(this.list);
            });
       }
}

- 删除功能

	- 删除功能就好做许多了，我们只需要注意，点击的时候，需要传一个id值，来标定这是一个唯一的值就可以了
注意：这个url地址是用的模板字符串的样式，删除信息的时候直接在user后面拼接id值即可
url:`http://localhost:3000/user/${id}`,

- 添加功能

	- 添加用户信息功能，因为添加页面是一个独立的组件，所以我们要独立新建一个.vue文件
	- 如果是二级路由，需要在一级路由的组件里面写二级路由的导航和容器
	- 这里需要注意，英雄列表的组件yingxiong需要和添加英雄组件为同级路由，如果将yingxiong组件设置为一级路由，那么添加英雄组件addying为二级路由的话，二级路由显示的时候肯定会将yingxiong列表也显示出来，所以我们要将这个两个组件都设置成一级路由，我们要在新建一个.vue文件add-container.vue组件，这是一级路由组件，这个里面什么都不写，只写一个容器<router-view></router-view>
	- 我们使用v-model来获取用户输入的用户名和公司名称
我们需要在data选项中设置一个对象用来接收从表单中获取到数据
// 设置一个对象类型，用来获取表单中的数据
        formdata:{
            name:'',
            company:'',
        }
	- 在发送请求之前我们要先引入axios这个包
// 先引入axios
import axios from 'axios';
	- 在methods中定义发送axios请求的方法
先进行一下非空判断
在发送axios请求
url:'http://localhost:3000/user',
method:'POST',
//   需要传参--->添加请求需要传参
data:this.formdata,
请求发送完毕之后，我们需要跳转到英雄类表也
//   添加成功后需要去到英雄列表页
                this.$router.push('/heroes');

- 编辑用户信息

	- id不同，但是对应的组件是相同的，这种情况下我们需要想到动态路由
{
      // 动态路由分三步，第一步，我们先定义动态路由参数，需要先写冒号再写参数名，参数名随便起就行
      path: '/heroes/editying/:heroid',
      component: editying,
    }
	- 第二步：传参数，这里传的也就是一个id值
<router-link :to="`/heroes/editying/${item.id}`">编辑</router-link>
在编辑的标签中，我们需要将获取到的id传递到编辑也  需要将to前面加上一个冒号，加上冒号之后，再使用ES6的模板字符串将地址和id值拼接到一块儿
	- 第三步是获取传过来的id值
这里我们需要知道，只要一跳到编辑页面，就要获取到当前传过来的id值，所以需要将我们要在created选项（和data()  methods:{} 同级）中获取到传过来的id值
created:{
   //$route.params  params是所有动态路由数据传过来的集合，如果想要获取到响应的内容的话，直接  .   点儿   即可
var  id =  $router.params.heroid;
}.then(res=>{
   //将获取到的用户信息赋值给到用户消息
   this.formdata.name=res.data.name;
   this.formdata.company = res.data.company;
});
	- 子主题 4

- 项目优化

	- 最后需要对引入axios进行优化，之前我们在每个需要发送axios请求的页面中都引入了import axios  from 'axios'  这样写是比较麻烦的，只要页面中使用axios就需要在页面中引入一下axios，所以，我们要记性优化
//现在main.js中引入axios
import axios from 'axios';
在入口main.js文件中引入axios,并给全局Vue对象的原型链赋值 
Vue.prototype.$http = Axios;

- 创建4.0项目模板，一定要会用vue-cli4.0创建项目

	- # 4.0下创建项目
$ vue create heroes // create(创建) 为关键字
# 切换到项目文件夹
$ cd  heroes 
# 在开发模式下 启动运行项目
$ npm run serve
	- 使用4.0版本的各种配置  后面蓝色的字体是选中的选项
	- dist打包结果（现在先了解一下，后面会讲）
src中的代码转换为浏览器能直接识别的代码

### 3.单文件入口解析

- main.js是项目入口
- App.js是所有组件的根组件
- vue文件关系图
- 路由级组件

	- 直接挂在地址上的组件就叫路由组件

- 普通组件

	- 直接在入口函数中的写自定义标签的时候写的组件

### 英雄项目

- 每一个模块就是一个组件，每一个组件就是一个.vue文件
- 导入和导出

	- export default   导出
export default vue //导出对象   vue.js
	- import  别名 from  路径  => 引入 
import vue from 'vue' 
	- Vue.use(VueRouter);  多了这一步
	- 如果 引用的包是第三方的包 可以用包名代替路径
比如：import Vue form "vue"
	- 如果想引入一个文件,并且使用,这个该文件中必须导出=  > 如果想引用一个组件,就必须先导出该组件 
import  from   =>export  default  对象

- 开启json-server
json-server --watch db.json
- cnpm        -S
是安装运行时依赖
- <router-link tag="li" to="/heroes"></router-link>
tag这个属性默认值是a，因为router-link默认值是生成一个a标签，我们可以要自定义生成的标签就要使用tag这个属性
- router-link默认激活样式是router-link-active
是可以更改的
在router.vue中可以更改
export default new VueRouter({
   linkActiveClass:"active",
})

## 第六天黑马头条第一天

### 地址：http://ttmp.research.itcast.cn/
用户名：13911111111   这个账号发表的内容是不需要审核的
密码：246810

### 黑马头条PC项目需要用到的技术

- Vue.js
- VueRouter  实现Vue项目的前端路由功能
- Vue CLI  Vue项目的脚手架工具
- axios  请求工具
- Vuex  状态共享框架
- eventBus
- ElementUI   Vue前端UI框架  特别重要极其重要   工作几乎每天都要用
- Echarts  图标插件  百度做的  功能及其强大
- nprogress  第三方进度条
- Quill   Vue第三方插件（富文本编辑器）
- Eslint   语法校验辅助工具（保证我们的代码一致性和代码语法错误）

### 重点掌握

- 需要掌握重点通过vue-cli4.0初始化项目
- 使用vue-router配置前端路由
- 使用axios进行数据请求
- 重点掌握  这是极其重要的
ElementUI在项目中的应用
没事儿就要去关注elementUI官网
https://element.eleme.cn/#/zh-CN/component/installation

### Vue插槽技术

- 先下载一个项目vue create  slot  --->项目名
webpack在4.0中进行了隐藏
- 下载完成之后，进入slot文件，运行项目
 npm run serve
在浏览器中 http://localhost:8080/展示页面
- 项目启动后先安装一个路由安装路由

	- 安装router   router属于运行时依赖
npm i  vue-router  -S  

- 在src文件夹下再新建一个router.js文件，用来引入路由的
文件建好之后先引入Vue   
import Vue from  'vue';
再引入vue-router
import VueRouter  form  'vue-router'
再注册VueRouter
Vue.use(VueRouter);
最后实例化VueRouter
new VueRouter({
    routes:[{
       //配置路由表
   }]
});

- 新建一个.vue文件
在router.js中引入这个.vue文件，需要将这个文件进行导出
再将App.vue中的内容该删掉的删掉
在main.js进行引入router.js,引入之后需要挂载到vue实例中
- yarn add axios
yarn add element-ui

	- 子主题 1

- ESlint是用来统一编写js风格的工具

	- 
"eslint.enable": true,
"eslint.autoFixOnSave": true,
"eslint.run": "onType",
"eslint.options": {
    "extensions": [".js",".vue"]
},
"eslint.validate": [
    { "language": "html", "autoFix": true },
    { "language": "javascript", "autoFix": true },
    { "language": "vue", "autoFix": true }
]

### ElementUI

- 基于Vue框架设计的组件库，jQuery是不能引入这个组件库的
- 安装
npm  i element-ui  -S
- 在main.js中引入elementui
import Element form  ‘element-ui’
Vue.use(Element);--->完成ele注册之后，预示着所有的文件都可以直接使用elementui了
引入样式
import 'element-ui/lib/theme-chalk/index.css';
  // 注册elementUI
Vue.use(ElementUI);

### 运行老师的项目，
先从GitHub中克隆一下老师的项目
安装全局依赖  cnpm  i
运行项目 npm run serve
老师的github地址
https://github.com/shuiruohanyu

### // vue-cli给我们的vue加了一个属性，是否是生产环境/开发环境，true是生产环境，false为开发环境
Vue.config.productionTip = false

## 第六天黑马头条第四天

### 1.分页

- Query参数使用params传递
在请求中需要写params选项，params选项和url，method同级
这个请求是请求所有文章列表的请求
this.$axios({
   url：'',
   method:'',
   header:{},
   //Query参数使用params传递
  params:{
    page:1,  //显示当前第几页
    per_page:20   //每页多少条数据  后端自定义最少10条数据，小于10条数据的时候默认显示10条   
   }
})
分页插件是默认向上取整
默认是一页10条数据
- loading效果
v-loading=true/false
finally是不管成功还是失败都要执行
this.$axios({}).finally(（）=>{
   //结束loading
})
- 加载过程中将分页禁止掉，请求结束后，开启分页

### 2.点击查询按钮

- 点击查询按钮再发送请求默认从第一页开始查询
@click=""
- axios有个功能，当参数为null的时候，就不会传参了
status:null;--->虽然写了这个参数，但是值为null，所以不传，这是axios的一个特性
其实不仅是null，若值为undefined的时候也是不会发送数据的。

### 3.json-bigint 这是一个第三方包
可以帮我们把json格式字符串中的超出js整数范围的数字进行反解
npm i json-bigint  下包
axios默认会把后端返回的数据使用JSON.parse转为对象给我们使用
同时他也提供了让我们自定义转换的功能
main.js中写
引入 JSonbig
import JSONbig from 'json-bigint'
也是在main.js中写如下代码
axios.defaults.transformResponse=[function(data,headers){
    //console.log('后端原始数据'，data，headers)
    return JSONbig.parse(data)
}]

### 拦截器

### 等待加载的效果loading

- 在v-tab标签中引入v-loading="loading"
- 在data中初始化loading的值为true
loading：true
- 在发送请求的方法中，先给this.loading = true 一下
在axios的.finally(()=>{
    将loading的值设置为false  设为false的意思就是将loading这个效果进行关闭
    this.loading = false;
})

## 第七天黑马头条第二天

### 简单进行分析一下：
登录页和首页都是一级路由
在views文件夹下新建两个文件夹
home（建index.vue）文件夹和login文件夹(建index.vue)
这里需要注意，文件名叫index.vue是因为当只有一个文件的时候，我们就将这个文件命名为index.vue，因为vue会默认去找index.vue文件，这样在router文件夹下中的index.js中配置路由的时候，分别引入这两个文件时就可以只写文件夹的名字，不用写文件的名字了例如：
// 引入登录页组件
import login from '../views/login'  --->只写文件夹的名字就行了
// 引入首页组件
import home from '../views/home/'--->只写文件夹的名字就行了

### 现在我们先写登录页
// 给div一个高度，可以让背景色显示出来
  height: 100vh;
  // 引入图片，当做背景图片
  background-image: url('../../assets/img/login_bg.jpg');
  // 铺满屏幕
  background-size: cover;

### 使用卡片做用户登录的信息收集
前提是要先引入element-ui  引入了element-ui所有的样式才会有效
在main.js中引入elementui
import Element form  ‘element-ui’
Vue.use(Element);--->完成ele注册之后，预示着所有的文件都可以直接使用elementui了
引入样式
import 'element-ui/lib/theme-chalk/index.css';
  // 注册elementUI
Vue.use(ElementUI);

### 在样式中添加属性long属性，让样式中可以使用less语法
<style  long="less" scoped></style>--->默认是给全局的html添加了样式，但是我们不想使用这种效果，我们可以给style标签添加一个属性，scoped，添加了这个属性之后，只对当前组件中的HTML结构起作用

### 登录页的样式
地址：background-img:url();
height：100vh；占据屏幕的100份
background-size：cover  铺满屏幕

### 表单校验
自动校验  鼠标离开的时候进行校验
手动校验  提交的时候校验
// 验证整个表单是否符合规则 this.$refs.ruleForm是获取form表单中的内容，手动点击登录进行验证  this.$refs是获取DOM节点的方法。。
      this.$refs.ruleForm.validate(res => {
        if (res) {
          console.log('登录成功')
        }
      })

### 表单校验   规则是从前往后进行判断的
required:true   --->必填项
message：‘请输入您的验证码’  --->提示信息
pattern：正则表达式属性  
validator：自定义函数   例如：  checked：[{validator：function（rule，value，callback）{}}]   rule：代表当前的规则，value 代表当前的值=>表单字段checked的值（true/false布尔值） ， callback回调函数

### 在vue中获取DOM对象
<div ref="res"></div>  这个ref属性的作用相当于id的作用，但是在vue中我们一般不使用id，我们就要用ref给标签添加一个属性
通过this.$refs.res获取DOM对象
this.$refs.res.validate();--->手动校验，点击登录的时候进行校验

### 安装axios  运行时依赖
cnpm i  axios  -S
安装完毕后需要在main.js
中引入axios
import axios from  'axios';
Vue.prototype.$axios = axios;  --->给Vue全局变量进行挂载axios，如果不挂载的话，每个组件用axios的话，每次都要引入axios，比较麻烦
//设置url的常态地址
axios.defaults.baseURL = 'http://ttapi.research.itcast.cn/mp/v1_0'

### token令牌是前后端分离时代的产物
后台不能存放前台请求信息，因为后台只有一个，前台有N多个，所以我们要将前台的请求的token值存放到浏览器本地，localStorage中或者sessionStorage中
如果不将token值存放起来，那么就会造成每请求一个页面就会进行登录一次。

- 具体这个token主要体现在两个方面：
1.验证页面的访问权限，例如有的页面没有登录的话，是不允许访问其他页面的
   我们可以判断有没有token来处理
2.有些接口需要提供token
   例如除了登录接口不需要token之外，其他的几乎都需要提供token给后台服务器。

### 登录失败的逻辑需要写在
axios的then的后面，catch中

### 去掉滚动条：
over-flow：hidden

### 判断手机号和验证码的方法
mobile: [{ required: true, message: '手机号不得为空', trigger: 'blur' }, { pattern: /^1[3456789]\d{9}$/, message: '请输入正确格式的手机号', trigger: 'blur' }],

code: [{ required: true, message: '验证码不得为空', trigger: 'blur' }, {
          pattern: /^\d{6}$/, message: '请输入正确的验证码', trigger: 'blur'
        }]

### //this.$refs是获取DOM节点的方法  后面的ruleForm是在<el-form  ref="ruleForm">  设置的一个ref属性值  通过this.$refs.ruleForm可以获取到整个form表单  validate是将获取的数据拿出来
this.$refs.ruleForm.validate(isOK=>{
  if(isOK){--->如果可以获取到数据，那么就可以发送请求
      //  发送axios请求
   }
})

### //当登录失败的时候需要在catch中进行接收错误
.catch(() => {
            // 如果手机号或密码出错了，也要给用户一个友好的提示  
            this.$message({
              message: '请输入正确的手机号及密码',
              type: 'warning'
            })

###  // 给子菜单添加一下鼠标悬停的样式  但是，这里的el-menu-item是一个标签名，为什么需要加上.点呢？加点 . 不是给类选择器吗？搞不懂了，前辈讲，在elementui中的标签名不能当做标签来使，如果要给elementui添加自定义样式，就要给标签名加  .   因为在浏览器中渲染出来的结果是普通标签，但是elementui的标签名就已经渲染成了普通标签的类名了，所以给elementui的标签添加自定义样式的时候，是用.标签名的样式来自定义样式
    .el-submenu .el-menu-item:hover{
        // 提高一下权重
        background-color: #409eff !important;
        color: #fff !important;
    }

- 浏览器渲染结果

### 使用axios的步骤

- 把经常使用的东西放到Vue.prototype中，因为每一个组件都是Vue的实例，直接this.$axios就可以直接使用axios了。
- 在prototype原型中添加成员的时候，建议使用  $.成员名  格式，主要是为了避免组件中的成员与原型中的成员名冲突，Vue中的成员名几乎都是 $.xxx 的形式，防止命名冲突 

### 补充：生命周期和钩子函数
生命周期钩子函数中的this都是表示的是Vue实例
创建   created       C
挂载   mounted    M
更新   update       U
销毁   destroy      D

- 生命周期

	- 1.实例创建前后执行的选项    鸡肋选项  很少使用
beforeCreate(){
   //不做处理
  console.log("实例创建之前执行");
}
	- 2.创建实例   经常使用  第一次可以访问到data methods中的数据和方法  或发送axios请求（最常见的就是发送请求）
created(){
  //这里一般用作查询数据，
  console.log("实例创建之后执行created");
}
	- 3.页面首次渲染（挂载）之前执行 第一次把数据替换到模板中  挂载钱DOM节点是旧的，因为此时的DOM节点还是旧的，所以这个beforeMount(){}很少用，Mounted(){}用的还是比较多的
beforeMount(){
   //可以加载数据，进行查询数据，但是这个阶段黑没有完成页面渲染
  console.log("页面渲染之前执行beforeMount");
}
	- 4.页面渲染完成之后执行   挂载后，当我们在渲染完成后需要操作DOM节点的时候可以写到mounted(){}中，DOM节点就是最新的了  因为此时的DOM节点是新的了，所以mounted(){}是用的比较多的，在Vue中获取DOM节点需要在标签中使用ref属性，使用this.$refs.ref(属性名)获取DOM节点。mounted中也是可以发送请求的，但是我们不推荐发送请求写到这个里面，因为，发送请求是越早发送出去越好，所以我们发送请求的逻辑写到created(){}中
mounted(){
  //可以加载数据，页面数据加载完成，可以获取DOM对象
  console.log("页面渲染完成之后执行");
}
	- 5.数据更新之前执行  模板中的数据是旧数据
beforeUpdate(){
   console.log("数据更新之前执行beforeUpdate");
}
	- 6.数据跟新之后执行，模板中的数据是新数据
update(){
   console.log("数据更新之前执行update");
}
	- 7.
beforeDestroy(){
   console.log("实例销毁之前执行beforeDestroy");
   //这个里面一般要在实例销毁之前销毁定时器进行销毁
   window.clearInterval(this.timer);--->销毁定时器
}
	- 8.实例销毁之后执行
destroyed(){
  console.log("实例销毁之后执行destroyed");
  window.clearInterval(this.timer);--->销毁定时器
}

## 第八天黑马头条第三天

### Vue中获取DOM的方式 这是Vue中获取DOM节点和组件的规则，在jquery中我们是
ref属性的作用：
1.获取DOM节点
2.获取组件  
this.$refs是一个对象类型，节点中的ref的值不能和其他DOM节点的ref值冲突，一旦重复，后者会覆盖前者，就不能准确的获取到自己想要的获取的DOM节点，其实ref属性就是相当于jQuery和js标签中id属性

- 通过ref获取DOM节点

	- //this.$refs是获取DOM节点的方法  后面的ruleForm是在
<el-form  ref="ruleForm">  设置的一个ref属性值  通过this.$refs.ruleForm可以获取到整个form表单  validate是将获取的数据拿出来
this.$refs.ruleForm.validate(isOK=>{
  if(isOK){--->如果可以获取到数据，那么就可以发送请求
      //  发送axios请求
   }
})

- 通过ref获取组件

	- <asd  ref="abc"></asd> 这里的asd标签就是一个组件 使用this.$refs.abc获取的时候，得到的是一个对象类型，也就是获取的是子组件实例this
通过this.$refs.ref(节点中的ref的值)来获取DOM节点

### 引入路由的一种方式
import Home from '@/views/home'--->@表示的是src目录，@符号是VueCLIh中提供的一种特殊的路径规则，注意：在VUECLI创建的项目中，无论在哪里使用@符号，它永远指向的是src目录

### 路由嵌套
{
   path:'/'
   component:Layout
   children:[
     {
       path:''  --->默认显示首页  默认子路由只能有一个
       component：Home
     }
   ]
}

### elementUI中跳转二级路由是
在el-menu标签中添加一个属性router，默认值是true
在二级菜单中写入index="/home"   index="/active"  index = "/publish"  index的作用就是跳转的路径

### 控制页面的访问权限
每次登陆的时候需要判断本地存储localStorage有没有token值

- 路由拦截器  官网叫导航守卫
路由是干啥的腻。。路由是用来跳转页面用的
拦截器的格式
router.beforeEach((to,from,next)=>{})
- 路由拦截器就是公共的页面访问门卫，也就是说所有的页面访问都要经过这里，可以在这里执行一些公共的操作，例如，校验当前组件是否拥有登录状态，也就是是否拥有token值。
- 这里的router文件夹其实就是配置路由的文件夹，只不过这项目中配置路由的文件夹叫router，所以我们这里写router，router文件夹中的index.js中写入
//路由拦截器beforeEach方法
to：表示去哪里的路由信息
from：表示来自哪里的路由信息
next：它是一个方法，用于路由放行
我们要具体要做的是：判断用户的登录状态判断本地存储是否有token值，如果有就通过，没有就返回登录页
router.beforeEach((to,from,next)=>{
   console.log('所有页面的访问都要经过这里');
   //获取用户  token
   const token = window.localStorage.getItem('token');
   //如果是非等登录页面，我们才校验登录状态，因为登录页不需要进行校验token
   //中断所有导航
   //在一些特殊情况下，终止导航，停留到当前页面next(false),不过很少使用

   //如果访问的是登录页面，就直接放行  这个path是to中的一个属性，这个属性中放的是想要跳转的路径地址
   if(to.path==='/login'){
        next();
        //停止代码往后执行  
        return
    }


    //非登录页面
   //判断是否有token 有token就通过
   if(token){
     //有，就通过
      next();  --->这个next()意思是，在如果有token的前提下，访问哪个页面，就跳转到哪个页面
    }else{
   //没有就转到登录页
   next('/login');
    }
})

	- // 使用路由拦截器
router.beforeEach((to, from, next) => {
  // 测试一下
  console.log('所有的请求都经过这里')
  // 获取一下本地token值
  const token = window.localStorage.getItem('token')
  // console.log(token)
  // 判断一下是否有token值
  // 但是除了登录页不需要token值，其他的页面都需要token值，所以我们要将登录页单独进行判断
  if (to.path === '/login') {
    // 如果请求的是登录页，就直接通过
    next()
    // 并终止代码的执行
    return
  }

  if (token) {
    // 如果有token值就直接跳转到想要去的页面，直接放行
    next()
  } else {
    // 如果没有token的话，就跳转到登录页
    next('/login')
  }
})

### 进度条的第三方库

- 使用npm方式下包
npm install --save nprogress

使用yarn方式下载
yarn add nprogress

这里需要注意：在创建项目的时候，使用哪种方式创建的项目，后面装各种包的时候，就要一致使用这种方式，我是使用npm创建项目的，所以在下包的时候就要使用npm
- 下载完成后需要在main.js文件中引入一下
import 'nprogress/nprogress.css'
注意：加载第三方包中的具体文件不需要写具体路径，直接写包名即可
- 在router文件夹中的index.js文件中
引入包  引入nprogress的js文件
import NProgress from 'nprogress'
- 在router文件夹中的index.js文件的全局前置守卫中使用开启进度条
router.afterEach((to,from,next)=>{
   NProgress.start();--->开启进度条
})
进度条有开启就要有关闭
我们在全局后置守卫中关闭进度条
router.beforeEach((to,form)=>{
   NProgress.done();--->关闭进度条
})
- 如果在登录页面并且是登录状态访问非登录页面，这里需要手动的终止进度条，否则进度条不会停止。

### 如果要给普通组件注册一个原生的js事件，我们使用.native修饰符，引入的组件库是不能直接添加原生的js事件的
<el-menu  @click.native="onLogout">退出</el-menu>

<el-button></el-button>按钮组件注册点击按钮的时候，是不需要写.native的，直接写@click="方法名"即可如果是普通组件的话，就需要写.native，例如：@click.native 

### 在黑马头条项目中除了登录页不需要token值，其他页面发送请求的时候都需要token值 ，否则后端返回401错误，后端要求把token放到请求头中 请求头也是给后端提交参数的一种形式
获取token
const token=window.localStorage.getItem('token')
this.$axios({
    //放到请求头中
    headers:{
         //这个里面的名字和值的格式都是后端规定的，直接按照后端给定的要求写就行
         名字叫Authorization
         名字：值
         注意这个值要求：token的格式要求为：Bearer  用户token
      Authorization:  `Bearer  ${token}`
    }
})

### 建议给每个组件都起一个名字
例如：name：‘active’这个name和data(){},methods:{}这些选项同级，也就是并列的意思
import default {
   name：‘active’,
   data(){},
   methods:{},
   created(){},
}

### 只有我们自己自定义表格列的时候，才会这么写


表格列默认只能渲染文本，如果想要渲染其他格式的内容比如说图片，那么就修奥自定义表格列
自定义表格列
在自定义表格列的template标签中声明
slot-scope="scope" ,然后就可以通过scope.row获取遍历项，scope.row相当于我们自己v-for的item  scope.row其实就是每一个遍历项
<template slot-scope="scope">
   <img :src="scope.row.cover.images[0]"></img>
</template>

### 调整后的src下的views下的目录结构是

- article 文件夹是发布文章页面
- content 文件夹是内容列表页面
- home 文件夹是首页
- layout 文件夹是布局页面
- login 文件夹是登录页

### ElementUI中的表格table插件是及其强大的，使用场景就是
当我们需要展示列表，列表中有好多表头的时候，我们就要想到ElementUI中的table表格插件，这个表格中的默认显示内容是文本内容，如果想要显示图片或者需要嵌套其他按钮的时候，我们需要自定义标签，使用<template></template>标签来自定义标签
<template slot-scope="scope">
        <el-popover trigger="hover" placement="top">
          <p>姓名: {{ scope.row.name }}</p>
          <p>住址: {{ scope.row.address }}</p>
          <div slot="reference" class="name-wrapper">
            <el-tag size="medium">{{ scope.row.name }}</el-tag>
          </div>
        </el-popover>
      </template>
这里需要注意几个属性：因为使用了插件table时，自动有了遍历的功能，所以scope.row相当于遍历出来的每一项，也就是相当于我们使用v-for中的item（回忆一下使用v-for的格式是  v-for="(item,index) in 对象"））这里的item表示的是遍历出来的每一项，所以scope.row表示的也是遍历出来的每一项。

### ElementUI中的询问框是比较特殊的
this.$confirm('确定要退出吗')

*XMind: ZEN - Trial Version*