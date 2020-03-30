# Node.js技术点学习

## 第一天

### 1.nodejs的重点

- 了解后台开发干的事情
- 能够写出简单的接口，基本的增删改查
- 能够npm装包，引包，用包
- MySQL的学习增删改查

### 2.node.js的基本概念

- 基于Chrome v8引擎的JavaScript运行环境
- 服务端的js
- Chrome的js解析器叫v8引擎

### 3.运行环境

- 通过node.js也可以直接运行js代码，不需要通过浏览器运行，直接敲命令即可。

### 4.js的组成

- 浏览器端

	- ECMAScript：js语法，for循环/if/esle,var
	- DOM文档对象模型

		- 约定了操纵dome元素的语法

	- BOM浏览器对象模型

		- 操纵浏览器的语法
		- window.alert(); 打印弹出框
		- window.location.href设置浏览器地址
		- window.setTimeout一次性定时器

- 服务器端

	- ECMAScript：js基础语法，for循环，ifelse var
	- BOM语法中的一些常用api

		- 定时器，console。。。

	- 模块 （类似于之前用的jQuery、swiper轮播图插件）模块就是各种插件
下载才可以使用
node.js也有自带的模块，但是开发中一般用第三方中的多一些

### 5.node.js的基本使用
REPL read(读取)eval(解析)print(打印)loop(循环)

- lowB写法

	- 打开黑窗
	- 输入node回车
	- 写js代码回车运行
	- 循环步骤

- 工作用法

	- 创建一个.js文件
	- 内部有node.js支持的代码
	- 打开黑窗输入node 文件名 回车
	- 运行

- 注意：node 文件名  不允许写错
          node	文件名  文件名不需要全部手打，直接Tab就可以啦。
- 在vscode中也可以打开，Ctrl+~号，就可以打开终端

### 6.ES6基本概念

- ECMAScript 2015
- 2015年推出的新的语法规范
- 简称ES6
- ES6变化最大，新功能最多

### 7.声明变量的改变

- var关键字的缺点

	- 变量的提升：会把变量的声明提升到当前作用域的最顶端
	- 没有块级作用域概念
{
  var name = '张三'
}
console.log(name);//张三
在大括号的外部依然能访问到变量，也就是说使用var声明的变量没有块级作用域。
	- var声明的变量可以重复声明
var name = '张三';
var name = '李四';
var name = '王五';
console.log(name);--->王五
下面声明的同名变量会把上面声明的同名变量的值给覆盖掉。

- let  变量

	- 可以理解为var的替代者，学了let之后可以和var说拜拜了。。
	- let name = ‘Jack’；
console.log(name);
	- 没有变量的提升了。
	- 有块级作用域

		- {
   let skill = '不如跳舞';
}
console.log(skill);--->undefined

	- let声明的变量不能重复声明
	- let声明的变量可以改变值
例如：let name = '周杰伦';
          name = '杜国章';
console.log(name);--->杜国章

- const  常量

	- const  常量名 = xxx
	- 变量名在当前作用域不会提升
	- 有块级作用域
{
  const name = '周杰伦''
}
console.log(name);-->同样访问不到块级作用域中const声明的变量
	- 也不能重复声明同名变量
const name = '周杰伦';
const name = '杜国章';
这种方法是不对的。
	- 必须在声明变量是就要给变量赋值

- const和let的选择

	- 能用const不用let，能用let不用var
	- const是常量声明之后，不能重复修改，性能更高
	- 能用let不用const，能用const不用var
	- 工作中基本上是用const比较多的
let用的很少
var基本不用

### 8.终端命令

- cls  清屏  clear

### 9.ES6对象的简化写法

- 属性名要和键名一致才能简写
- const name = 'jack';
const age = 18;
const skill = '跳舞';
const person = {
  name：name,可以写成name
  name,
  age,
  skill,
  平时写法：
  jump:function(){
      console.log('扑通。。跳');
   }
  在ES6中是将function去除了
  jump() {
    console.log('扑通。。吧唧。。');
  }
}

### 10.ES6的模板字符串

- 格式：`${}`
- const smoke = '黑岩'
const data = {
  name: '李白',
  chaodai: '唐朝',
}
const temStr = `
        ${data.name}来自于${data.chaodai}
        疑是银河落${smoke}
        疑是银河落九天
        疑是银河落九天
        疑是银河落九天`;
console.log(temStr);
- 模板字符串可以换行，简单的内容可以直接使用模板字符串

### 11.函数默认值

- 早期使用的是短路运算来实现默认值的设置

	- // function hello(name, skill) {
//   // 早期对参数 的判断
//   // ||逻辑或，任何一个为真，就为真
//   // 
//   name = name || 'jack',
//     skill = skill || '跳水',
//     console.log(name + '你好！', skill);
// }
// hello();

- // es6中的默认值
// 参数=参数值

	- function hello(name = '路飞', skil = '橡胶果实') {
  console.log(name, skil);
}
hello('我爱罗', '后又跟');

### 12.ES6中的对象解构

- // 定义对象
const person = {
    name: '食欲之灵',
    desc: '教你做饭',
    spec: '事物越好吃，衣服越少',
  }
//   ES6中可以简写成
  //   快速获取对象的属性
  // 需要和对象中的属性名要同名
  // 没有想要的值的时候，会出现undefined
const { name, desc, spec } = person;
console.log(name, desc, spec);
- 对象的解构，使用频率挺高的。
- // 形参传一个对象类型
// 结合默认值，如果调用方法的时候不给方法传参，那么就使用默认值
function eat({ food1 = '黄瓜', food2 = '萝卜', food3 = '炒肝儿', food4 = '豆汁' }) {
  console.log(food1, food2, food3, food4);
}
// eat({
//   food1: '肉',
//   food2: '西蓝花',
//   food3: '蛋',
//   food4: '面条'
// });--->传了形参打印的就是传入的实参的值。
eat({});--->不传实参的话，输出的就是默认值

### 13.数组的解构

- 语法：
 const arr = ['喜洋洋', '灰太狼'];
// 数组的解构，获取的顺序，和数组的元素的对应关系是一致的
// 数组大部分时候都是通过下标来获取的
// 数组的解构用的不多，了解即可
const [c1, c2] = arr;
console.log(c1, c2);
- 用到的不多，了解即可

### 14.ES6-对象展开运算符  ...三个点儿

- // 对象
const person = {
  skill: '跳水',
  habbit: '抗冻',
}
const student = {
  sleep: '呼噜',
}
const son = {
  // 写到前面的同名属性会被下边儿的覆盖掉
  //   可以对多个对象进行赋值
  ...person,
  ...student,
  skill: '游泳',
}
console.log(son);

### 15.ES6-数组展开符

- // 直接将...数组放到新数组中即可         数组不会出现覆盖的问题，索引会依次向后增加，一直在后面追加
- const arr = ['跑步', '游泳', '跳水', '玩儿板', '滑板'];
const arr1 = ['长跑', '跑马拉松', '跑全马', '跑半马']
const sport = [...arr, ...arr1];
console.log(sport);
数组展开符中若有对个数组的话，并且数组中的元素会有重复元素的话，相同的元素并不会覆盖掉，而是依次向后添加。

### 16.箭头函数
今天的重点

- 普通函数简化箭头函数的规则：
省略function，变为'=>' 
如果形参只有一个，可以省略小括号，
如果函数体，只有一行，可以省略大括号，
如果函数体只有一行，并且有返回值，省略大括号的同时，必须省略return
- 普通函数无法用箭头函数的方式化简
- 箭头函数只能化简匿名函数
- const exam =a=>a这种写法其实是这种写法的语法糖
const exam = function(a){
  return a;
}

### 17.箭头中的this

- 箭头函数中的this，在创建箭头函数的时候就确定了，
this指向的是上下文(和他平级的环境中)中的this
箭头函数在创建的时候就已经确定了。
- // 箭头函数中的this指向的是谁
  const person = {
    name: '海尔兄弟',
    skill: '抗冻',
    jump() {
      // 指向的是对象person
      //   console.log(this);
      //   定时器中函数中的this指向的是window
      //   如果想要获取到person对象的话，需要在外边将this保存一下
      //   var that = this;
      //   window.setTimeout(function() {
      //     console.log(that);
      //   }, 1000)
      //   简写成箭头函数
      //   箭头函数中的this指向的是和它平级的环境中this，那么怎么理解这个平级环境呢，可以这么理解，就是在箭头函数上一行打印一下console.log(this)，这个this指向的谁，那么箭头函数中的this指向的就是谁
      //   所以，在这里，console.log(this)指向的是person，所以，箭头函数中的this指向的就是person
      console.log(this);---->this指向的是person
      window.setTimeout(() => console.log(this), 100);
    }
  }
  person.jump();

### 18.ES6中的内置模块

- fs模块

	- // 声明一个常量fs
// require('fs')意思：导入fs模块，赋值给常量fs
const fs = require('fs');
// 声明一个常量fs
// require('fs')意思：导入fs模块，赋值给常量fs
	- 读文件
// 声明一个常量fs
// require('fs')意思：导入fs模块，赋值给常量fs
// data:是读取的结果
// err：如果读取失败，保存的是错误信息
const fs = require('fs');
fs.readFile('./lai.txt', 'utf-8', (err, data) => {
  console.log(err);
  console.log(data);
})
	- 写文件
const noval = `
    静夜思
锄禾日当午
汗滴禾下土
谁知盘中餐
粒粒皆辛苦
`;
const fs = require('fs');
// writeFile()中的参数 1：地址 2:写入的内容  3.选项，可选的参数  4.回调函数
 参数1：是需要写入的文件
    参数2：是需要写入的内容
    参数3：默认值是utf-8
    参数4：回调函数
fs.writeFile('./go.txt', noval, err => {
  console.log(err);
});

### 19.node.js第三方模块

-  npm 官方下包网站
- 找包
- 下包
- 引包
- 用包
- fivicon错误是浏览器再找图标

## 第二天

### 1.补充的终端的命令： cd ../  跳出当前文件夹
cd ./文件夹  进入文件夹
mkdir 文件名
这是一个命令，创建文件夹的命令

### 2.nodejs读取文件：
node.js中的相对路径是相对的是： 终端中的路径或者小黑窗中所处的路径

### 3.为了避免终端找不到路径，我们可以使用绝对路径来解决这个问题，但是不提倡使用绝对路径。

### 4.nodejs中的绝对路径中的全局变量，这里是两个下划线_ _
__dirname--->定义到当前这个js文件所处的文件夹的绝对路径
__filename--->定义到当前这个js文件的绝对路径

### 5.Path模块基本使用（也是内置模块）

- path.join([...paths])--->括号中必须是字符串
把多个路径拼接到一起，保证正确
const filepath = path.join('info','novel','01.txt');
info\novel\01.txt
- const filepath = path.join(__dirname,'./novel/01.txt');
- path与文件fs模块结合使用

	- // 导入路径包
const path = require('path');
// 导入文件包
const file = require('fs');
// 生成路径
const fallpath = path.join(__dirname, './files/01.du.txt');
// 读取文件
file.readFile(fallpath, 'utf-8', (erro, data) => {
  if (erro == null) {
    console.log(data);
  } else {
    console.log(erro);
  }
});

- 路径拼写的时候不要写错，一定是这种/斜杠，多个路径之间的拼接用逗号“，”分割

### 6.http模块--创建服务器
也是内置模块
关闭服务器是Ctrl+c
这种服务器统一叫静态资源服务器

- 导包
const http = require('http');
- 创建服务器对象
const server = http.createServer(function(request,response){
    //  content-type内容类型
    //  text/plain 普通文本
    //  text/html  HTML结构
    //  charset=utf-8编码格式
    response.setHeader('content-type','text/plain;charset=utf-8');
   //返回内容
   response.end('how old are you!');--->响应英文的话直接写就行
   response.end('在你面前他平时总是乐乐呵呵');
});
- 开启服务器  开启监听
参数1：端口号
参数2：监听地址，省略的话就是本机
参数3：开启之后的回调函数
server.listen(8848,function(err){
   if(err==null){
      console.log('服务已开启!');
   }else{
      console.log('哎呀失败了');
    }
});
- 概念解释

	- 端口

		- 物理端口

			- usb口
			- 网线口
			- 耳机口
			- hdmi显示器，投影仪接口

		- 虚拟端口

			- 电脑中的软件和外部通讯的通道
			- 只要和外部通讯的软件，都会使用某一个虚拟端口
			- 一个号而已，0开始递增
			- 虚拟端口很多
			- 前10000端口号一般有很多被占用了

	- 子主题 2

### 7.http模块获取用户请求的url地址

- 创建服务器对象
const server = http.createServer(function(request,response){
    //content-type内容类型
    //text/plain 普通文本
    //charset=utf-8编码格式
    response.setHeader('content-type','text/plain;charset=utf-8');
   //返回内容
   response.end('how old are you!');--->响应英文的话直接写就行
   response.end('在你面前他平时总是乐乐呵呵');
   console.log(request.url);--->可以获取用户请求的地址后面的请求参数英文
   console.log(decodeURI(request.url));--->可以获取请求参数中的汉字
});

### 8.根据不同的url来做不一样的逻辑

### 9.http模块--读取HTML文件并返回

- 导入模块http开启服务器
导入模块 fs 读取服务
导入模块 path 生成路径 
- 开启服务
http.createServer(request,response)=>{

})
- 开启监听

### 10.如果静态资源中图片格式的话，那么就不要设置编码格式了utf-8了

### 11.http://localhost
     http://127.0.0.1
这两种方式都是访问的是自己电脑，只能是自己访问自己电脑的时候可以简写这种ip地址

### 12.用户发送的请求时git还是post请求

- request：请求
request.method--->获取用户的请求方式GET/POST
request.url--->获取用户的请求参数

### 13.第三方模块使用步骤

- 第一步：新建文件夹(不要中文)，
第二步初始化，打开终端输入：npm init -y或者npm init自行输入
第三部：npm网站找包，下包，导包，用包  npm i express

### 14.express模块框架

- 第二天会讲

### 15.补充  nodemon这是一个自动启动服务器的小工具，只要保存文档就会自动开启服务器，比较方便。
直接 npm i nodemon 安装

### 16.readFile()中的utf-8为什么可以省略？
     HTML页面中有utf-8这个字段，浏览器可以识别到
     对于非文本类的文件，浏览器绝大多数都可以自动的推断出类型，
     使用对应的方式去解析，所有当页面中图片格式的文件的时候，readFile()这个方法中的utf-8就不用写了。
     学名叫嗅探，加载之前先嗅嗅。。

### 17.在向服务器发送请求的时候，如果不要浏览器发送关于icon.ico图标的请求只需要加一个判断即可
// 搭建一个静态资源服务器
// 导包
const http = require('http');
// 创建服务器对象
const server = http.createServer((request, response) => {
   加一个判断只要判断返回值不是/favicon.ico即可
  if (request.url !== "/favicon.ico") {
   //逻辑代码
}

## 第三天

### 1.express基本使用

- 1.// 导包
const express = require('express');
// 创建服务器对象
const app = express();

//路由
app.get('/', function(req, res) {
  res.send('Hello World 你好世界')
});
// 开启服务器
app.listen(3000, err => {
  if (!err) {
    console.log('服务已开启');
  }
});

### 2.运行在小黑窗中
nodemon 文件名
nodemon这个功能只能是在gitbash环境下运行

### 3.实现静态资源托管的功能
app.use(express.static('public'));

- // 导包
const express = require('express');
// 创建服务器对象
const app = express();

// 实现静态资源托管功能代码
app.use(express.static('public'));
// 开启服务器
app.listen(3000, err => {
  if (!err) {
    console.log('服务已启动');
  }
});
- app.use(express.static('public'));
这钟方式请求的时候，不需要跟public，程序会直接去public文件夹下读取文件
例如：http://localhost:3000/index.html；
这个public也是可以动态改变的，但是一般是比较建议在代码的同级目录下边儿
添加public这个文件夹，这样是方便管理的。
app.use('/public',express.static('public'));--->这种方式进行请求的时候需要先写/public再跟想要访问的HTML文件
例如：http://localhost:3000/public/index.html

### 4.路由的概念
一句话概括一下路由：
url和后台逻辑的对应关系

- get请求

	- 语法

		- 路由是url和后台逻辑/函数的对应关系
app.get()是注册路由的步骤
app.post()
		- // get方式的请求接口书写
app.get('/login', (request, response) => {
  const arr = ['西红柿', '菜花炒肉', '花菜炒豆角'];
  response.send(arr);
});
		- 获取随机笑话
// get方式的请求接口书写
app.get('/joke', (req, res) => {
  const arr = ['我是笑话1', '我是笑话2', '我是笑话3', '我是笑话4', '我是笑话5'];
  const suiji = parseInt(Math.random() * 5);

  console.log(suiji);
  res.send(arr[suiji]);
});

	- 读取外部的一个文件

		- JSON.parse();--->JSON字符串转数组类型。
		- JSON.strfiy();--->数组类型转字符串
		- // 导包
const express = require('express');
// 导包
const fs = require('fs');
// 导包
const path = require('path');
// 创建服务器对象
const app = express();

// get方式的请求接口书写
app.get('/joke', (req, res) => {
  //   声明一个数组
  const arr = ['笑话1', '笑话2', '笑话3', '笑话4', '看着路世界真滴大', '于是啥子人都有'];
  // 获取一个随机数
  var suiji = parseInt(Math.random() * arr.length);
  //   响应一个随机笑话
  res.send(arr[suiji]);
});


// 获取随机的笑话
app.get('/suijixiaohua', (req, res) => {
  // 获取路径
  var all_path = path.join(__dirname, './data/jokes.json');
  // 读取文件
  fs.readFile(all_path, 'utf-8', (erro, data) => {
    if (erro == null) {
      // 读取成功
      // 读取出来的data的默认类型是JSON类型的字符串，我们要将这个字符串转成数组
      var arr = JSON.parse(data);
      //   获取一下随机数
      var suiji = parseInt(Math.random() * arr.length);
      //   响应请求
      res.send(arr[suiji]);
    } else {
      // 读取失败
      console.log(erro);
    }
  });
});

// 实现静态资源服务器功能
app.use(express.static('public'));
// 开启服务器
app.listen(3000, err => {
  console.log(err);
  if (!err) {
    console.log('服务已启动');
  }
});

	- get请求参数的获取

		- get请求的数据都存到了在query属性中
request.query.属性名进行获取响应的数据
并且是以对象的方式进行了存储
		- 注意：

			- 1.当涉及到参数传递时，
后台接口在实现的时候需要
接收数据
处理数据
返回数据

- post请求

	- post请求方式

		- post路由的注册方法和get类似，就是将get改成post即可
请求方式默认接不到请求数据
		- 测试的时候：
可以通过postman这个软件发送post请求
也可以使用ajax发送post请求，不过这种方式需要些一些代码，比较麻烦
推荐使用postman发送post请求。
		- 默认注册的post路由中无法获取到提交过来的参数（数据）
		- 中间件是一个特殊的第三方模块
必须结合express才能可以使用
类似和jQuery插件必须要结合jQueryjs使用
		- 中间件 body-parser  的使用步骤

			- 下包  npm i body-parser
			- 引包    // 导入中间件包
const bodyParser = require('body-parser');
			- 用包    // 解析post请求中的文本
app.use(bodyParser.urlencoded({ extended: false }))
			- // 注册post路由
app.post('/ppost', (req, resp) => {
  console.log(req.body);
  resp.send('post请求收到了');
});
			- post请求中携带的参数是存在了req.body中了

	- 通过中间件获取到上传文件

		- 也是使用中间件来获取
express-fileupload中间件叫这个
下包：npm i express-fileupload
		- 导包
const fileUpload = require('express-fileupload');
		- 使用中间件 接收文件
app.use(fileUpload());
		- 使用postman软件来测试的时候，需要选择body下的第一个form-data
		- 使用了中间件之后可以使用request.files获取到文件的信息
files中使用对象属性的方式，保存了上传的文件信息
这个files属性并且是以对象的形式将文件数据进行了存储
files对象包含了所有了文件的信息

			- app.post('/ppost', (req, resp) => {
  //   console.log(req);
  console.log(req.files.icon);--->这里的icon就是文件上传时的键名
  console.log(req.files.wje);--->这里的wje就是文件上传是的键名

  resp.send('文件已收到');
});
			- post上传时的键名

		- 把文件移动到某个文件夹中
request.files.xxx.mv(路径)

			- // 使用中间件接收文件
app.use(fileupload());
// 注册post路由
app.post('/ppost', (req, resp) => {
  //   console.log(req);
  //   现在这个文件获取到了
  console.log(req.files.icon);
  //   我们需要获取到文件名
  const filename = req.files.icon.name;
  //   打印一下这个文件名
  //   console.log(name);
  //   生成一个路径
  const allpath = path.join(__dirname, './files/', filename);
  req.files.icon.mv(allpath, err => {
    if (!err) {
      console.log('文件传过来了');
    }
  });

## 第六天

### 补充
1.箭头函数的在委托事件中的指向：
   上下文中的this

### 用户的注册

### 用户 登录

### 验证码的功能

- nmp i  svg-captcha
- 导包
require（'svg-captcha'）
- var str = 'String';
str.toLowerCase();--->转小写
str.toUperCase();--->转大写
- 前端如果要想获取验证码，我们使用img的src="/user/pac"这种方式调用接口
其实就是在HTML标签中的img标签中的src属性直接写生成验证码的接口就可以了，工作中其实也是这么获取服务器生成的验证码图片的
- 对于img标签src不变，浏览器会直接使用缓存的图片
- 避免缓存，使用在url的后面拼接上?随机值的方式
- 时间戳Data.now();
- url后面?分割的内容，
- 调用接口，密码加密

	- 使用一个比较简单的算法
md5算法：最初的设计是摘要算法，从一个数据中算出一些特征值
计算的结果无法反算，满足加密算法的特点，有一部分分用它来进行加密
	- 直接使用现成的库

- 回话技术

	- cookie技术

		- http是无状态的
		- cookie的作用：解决http不会记录客户端(用户信息)这个缺点。
		- 存数据 一个技术
		- cookie是服务器设置的
		- 浏览器用来保存
		- 容量是4kb，大数据存不了

	- session技术

		- session比cookie存到数据要大一些
session要结合cookie使用
		- 大量的数据是存放到session中，浏览器存的标记是存放到cookie中，浏览器是带着cookie中的标记去服务器中，服务器中会识别cookie中携带的标记会在session中查找用户的详细信息。
		- session中保存的位置是在服务器中，保存的格式是key:value格式
浏览器中保存了要给cookie(标记)
浏览器再次请求服务器时，自动携带标记去服务器，服务器就可以根据标记获取对应的详细信息了。

- 使用token这个技术来实现APP中存贮用户的详细信息
计算时，会用到用户的一些信息，不同用户算出来的值是不同的
计算完毕后，服务器直接返回给服务器，服务器什么都不存
对服务器的性能消耗较小
基于token的状态维持
网站可以用
app可以用
服务器不需要存东西，对服务器的消耗较小
- 面试时：
1、localStorage和sessionStorage的区别
     前者关闭浏览器数据还在
     后者关闭浏览器数据就没有了
     只能存字符串，如果要存复杂类型可以结合json.stringify
2、localStorage和sessionStorage和cookie和session的区别：
     1.cookie保存的位置是浏览器，数据是自动保存的，自动携带数据，但是容量较小，容量只有4Kb。
     2.session保存的位置是服务器，浏览器用cookie存了一个标记；
     3.服务器根据cookie携带而来的标记获取到详细的信息
     4.session消耗服务器的性能，我之前的项目用的是token。
     5.axios中可以用拦截器统一设置token
     6.在Vue中用导航守卫统一判断是否有token

### 花姐补充：
同步和异步
同步：从上到下依次执行
绝大多数是同步


异步：同时执行，某代码的执行，不会阻塞后续代码
     1.绝大多数，异步执行的函数中都有回调函数
     2.定时器和ajax都是异步机制
     3.fs.readFile(path,(err,data)=>{})--->读文件也是异步
     4.hmModel.find('',(err,result)=>{})--->访问数据库也是异步
定时器中的代码会丢到事件循环中的一个里面
等到不是定时器中的代码执行完毕后，会再向事件循环中看看，找到可以执行的事件，再将可以执行的事件执行，总之在定时器中的函数会在非定时器中的代码执行完毕后，再执行事件循环中的事件。

### Echarts的基本使用

- 常见的有柱状图，饼状图，折线图
- 网页绘图可以使用
canvas：网页中推出的一套绘图API
              画线，圆，方框
webg1:  更接近与底层的绘图API
             相比canvas性能较好
但是一般这两种方式是不用的

## 第五天

### node和nodemon的区别
使用node的时候需要自己手动重启服务器
使用nodemon的时候重启服务器比较方便，保存服务器文件时候就自动重启服务器了，注意，使用nodemon必须是在bash环境下使用。

### 英雄管理项目

- 英雄管理的第一天目标
实现英雄增删改查功能
- 端口：
一个端口与只能是被一个软件占用
数据库的端口和express的端口不能是一样的
port: '3306',     app.listen(3000,  这两个端口不能是一样的
- 步骤
1.新建文件夹heroManage
2.初始化  npm init -y
3.创建文件 index.js
4.下包 npm i express
5.c+v express的基本结构
6.c+v 今天要写的路由
7.首先需要确保你的项目已经安装了mysql
npm install mysql
安装mysql-ithm
npm install mysql-ithm

### 功能1：
英雄管理：  查询所有英雄列表

### 功能2：
英雄管理：  查询英雄详情（根据id进行查询）
这里需要注意：get请求的参数localhost:3000?id=1 这里的id=1我们该怎样获取到呢？记住：get请求的参数是存放到query属性中 request.query就可以看到get请求中的所有参数，query属性是对象类型，所以，query.id就能直接获取到传过来的id值。

### 3.英雄管理:    新增英雄
步骤：
  1.接收post提交的文本信息  插件儿body-parser  (装包，导包，用包)
用包 // 解析post请求中的文本  app.use(bodyParser.urlencoded({ extended: false }))
   2.接收post提交的文件信息  插件儿 express-fileupload  (装包，导包，用包)
    使用中间件 接收文件app.use(fileUpload());
   3.获取数据
         名字：name   request.body.name
         技能：skill    request.body.skill
         icon    request.files.icon.name  --->获取文件名
   4.移动路径
        1.‘request.files.icon.mv(路径，回调函数)’
   5.保存数据到数据库：heroModel.insert
    6.回调函数中
       1.返回结果

### mockjs库

- 导包
const Mock = require（'Mockjs'）

### 先做新增功能

### 再做修改

### 最后做删除功能

## 第四天

### 1.跨域问题

- ***ajax请求***不同源接口的时候会出现跨域问题
-    ***浏览器***为了保护我们帮我们做的限制
- 浏览器打开的页面，和调用的接口需要同源才可以调用
- url地址的组成：
http://127.0.0.1:3000/search

	- 协议：http://
	- ip地址：127.0.0.1
	- 端口：3000

### 2.浏览器同源

-  协议、ip地址、端口全部相同，称为同源
- 页面地址和接口地址同源，浏览器就不会做任何的限制，可以自由的访问。
- 协议、地址（这里的地址包括页面地址和接口地址）、端口任意一个不相同就是跨域
- url地址组成：http://127.0.0.1:3000/search

	- 协议：http://
	- ip地址：127.0.0.1
	- 端口：30000

- 什么是不同源

	- 1.对比浏览器打开页面的地址和页面向ajax调用接口的地址
这两个地址是不一样的，所以是不同源，协议，ip地址，端口号只要有一个不相同就是不同源。是要是出现了不同源额情况，浏览器就禁止访问。

- 实际工作中不可避免页面和接口地址绝对同源，肯定有解决方法

	- 第一种解决方案：cors--->用的最多
	- 第二种解决方案：jsonp--->曾经用的最多，现在用的少了，但是面试可能会问到

- 往不同源的接口发送请求，牛逼名叫跨域

### 3.第一个解决跨域的方案
jsonp

- 1.民间的解决方案，这种方法需要前端和后端相互配合
- 使用方式：

	- 前端需要做的事儿
$.ajax({
   url:  
   type:必须是get方式或者不写这个参数
   success：function(result){},
   //这个dataType必须要加上
   dataType:'jsonp',
});
后端需要做的方式：
response.jsonp({key:value});
例如：
response.jsonp({
  msg:
  
});

- 注意：
如果接口是jsonp
前端要干的事儿是
1.dataType:'jsonp',
2.type:'get'或者省略不写
数据的发送，请求成功之后的回调函数和之前完全一样
3.这个后端代码response.jsonp({key:value});不需要我们去写；
- jsonp的工作原理

	- script标签的src属性可以发送请求，没有同源限制。
jsonp跟ajax一点儿关系都木有，在network中选到XHR会发现什么都没有，
	- 本质是动态创建了一个script标签并添加到了head标签中

- jsonp的缺点：
不支持post请求，
数据大的话，搞不定，文件上传搞不定
无法进行大量数据的发送
- 描述一下jsonp
1.和ajax没有关系
2.利用的是script标签的src属性不受跨域限制
3.向不同源的服务器发送一个get请求
4.url中携带了一个callback的参数
5.服务器接收到了之后返回一个函数的调用
   xxx({name:'jack'})
6.返回浏览器之后解析成js代码。
- 使用方法：
前端：$.ajax({
   type:'get',--->设置请求方式或者不写默认是get
   dataTape:'jsonp',--->设置接收请求参数的类型
})

### 4.第二个解决跨域的方案
CORS

- CORS
corss:跨
origin：域
resource：资源
sharing:共享
- 目前解决跨域问题用的最多的方案
- H5中推出的新标准，低版本浏览器不支持ie
- 用起来很简单
前端不需要改变什么
后端只需要允许即可
在express中需要设置
响应数据之前：设置一个header
app.get('/corsPOST',(req,resp)=>{
   resp.header('Access-Control-Allow-Origin','*');
})
- 浏览器要识别
('Access-Control-Allow-Origin','*')
这个东西
请求发给服务器之后，
服务器返回的响应头中有一个允许的标记
浏览器就认为服务器允许跨域访问，没有了跨域的错误。
- 优点：
get和post都支持
前端不需要添加任何代码
无论是jsonp还是cors都需要和后端配合，
- 缺点：
兼容性比jsonp稍微差那么一点

### 5.在express 中自己写中间件来允许我们跨域，在中间件中写了允许跨域的代码之后，后面的get  post请求就不需要每次请求之后都要写这个允许跨域的代码了

- 在express中间件设置跨域
中间件其实就是一个中间件
通过注册一个所有请求都会允许跨域的代码
- app.use((request,response,next)=>{
  console.log('执行啦');
  //设置允许跨域
  response.header('Access-Control-Allow-Origin','*');
  //调用next
  next();
})

### 6.什么是中间件

- 中间件就是请求和响应(注册路由)之间额外注册的一个回调函数
中间件的顺序只能是写到路由函数的前面
- app.use((request,response,next)=>{
  console.log('我执行了');
  //执行下一个
  next();--->一定要写这个next()函数，才能执行这个中间件后面的路由的函数
});
- 这个中间件函数中的request和response这两个参数和路由中的request以及response这两个参数是共享的，中间件可以任意增加多个

### 7.CommonJs标准

- 使用CommonJs只有三句话
- 先定义一个自定义模块
自己写的模块在一个文件，在一个js文件中写自己需要调用的模块：
写变量
const userName = '牛逼';
暴露出去
//不推荐这种module.exports = userName;
  //这里的module是一个内置的全局变量，所以可以直接拿过来使用
module.exports = {
  userName,
  skill,
  sayHi(){
      console.log('看到小仙女好开森~~');
   }
}
- 在使用自定义的模块
导入模块是一个文件
require('自己写的模块路径');
require('./05.自己定义的模块.js');--->这里的.js可以省略调
- 自己抽取的功能模块一般都是放到一个叫utils的文件夹中，这个文件夹中只放自己抽取的功能模块。
- //将允许跨域的回调函数暴露出去
module.exports =(request,response,next)=>{
  console.log('执行啦');
  //设置允许跨域
  response.header('Access-Control-Allow-Origin','*');
  //调用next
  next();
}
- 补充：
工作中常见的文件名：
utils：自己抽取的功能模块
libs：下载的第三方模块（自己手动下载的）
node_modules:  npm i 模块名  自动下载的文件夹，内部保存第三方模块

### 8.MySql数据库

- 数据库分类

	- 关系型数据库

		- 类似于table表格的形式保存数据
		- 使用sql语句操纵数据
		- 常见的数据库有：MySql，Oracle，MSSql（微软自家的）

	- 非关系型数据库

		- 用类似于js对象的形式保存数据
		- 使用操纵对象的形式操纵数据
		- 常见的有Mongodb，Redis。。。

- 数据库管理员  DBA：DataBaseAdmin
- 数据库服务器：只提供数据库服务，其他的软件都不用开
- MySql特点
免费
开源，可以看到源代码
轻量级 小
作为关系型数据库的市场份额比较大
- MySql基本使用

	- 建库
	- 建表
	- 增加字段
	- 增删改查

		- 增--->了解即可
insert into 表名 （字段名1，字段名2...）  values('值1'，'值2'...);
insert into user (username,skill) values('小鹿','唱跳rap');
		- 删---> 不跟条件的话，表中的所有数据都会被删除
delete form 表名  where  条件
		- 改--->改也需要跟条件，如果不跟条件的话，就是更改所有的数据
update 表名 set 字段1=值1，字段2=值2 where 条件；
		- 查--->如果不跟条件就是查询所有
select * form 表名 条件；
例如：select * from user where id=15;

### 9.MySql模块的使用

- var mysql = require('mysql');
var connection = mysql.createConnection({
  host: 'localhost',
  user: 'root',
  password: 'root',
  database: 'db88'
});
// 链接数据库
connection.connect();
connection.query('select * from user', function(error, results, fields) {
  //    error：错误信息
  console.log(error);
  //    results：执行的结果
  console.log(results);
  //    fields: 表格的字段信息，用的不多
  console.log(fields);
});
// 关闭数据库
connection.end();

### 10.mysql-ithm模块的使用（推荐使用这种方法）

- 首先需要确保你的项目已经安装了mysql
npm install mysql
安装mysql-ithm
npm install mysql-ithm
- 剩下的就是粘贴复制就好了
- 直接去npm官网去找mysql-ithm这个插件儿就行
- 增
// 添加数据
// studentModel.insert({ name: '赵雷', age: 50 }, (err, results) => {
//   console.log(err);
//   console.log(results);
//   if (!err) console.log('增加成功');
// });
- 查
//2.1 查询所有数据
studentModel.find((err, results) => {
  console.log(results);
});
- 查询指定数据
//2.3 根据条件查询数据
// 'id=1' : 查询id为1的数据 (查询条件可以参考sql语句)
//例如 'age>10' : 查询age超过10的数据 
//例如 'name>"张三"' : 查询名字为张三的数据，注意字符串添加引号
studentModel.find('id<4', (err, results) => {
  console.log(results);
});
- 改  改所有的数据
//3.1 将数据库中所有的age字段值：修改为25
studentModel.update({ age: '25' }, (err, results) => {
  console.log(results);
});
- 改   指定条件进行修改
//3.2 将数据库中 id = 1 的数据，age修改为30
studentModel.update('id=1', { age: 30 }, (err, results) => {
  console.log(results);
});
- 删   删除表中的所有数据
//4.2 清空表中所有数据
studentModel.delete((err,results)=>{
    console.log(results);
});
- 删   删除指定条件的数据
//4.1 删除所有 age<2 的数据
studentModel.delete('id<2', (err, results) => {
  console.log(results);
});
- 执行自定义sql语句
studentModel.sql('insert into student(name,age) values("andy",20)',(err,results)=>{
    console.log(results);
});
- 删除表格   ***慎用***
studentModel.drop((err,results)=>{
    console.log(results);
});

### 补充：

- app中没有跨域
绝大数的app也需要和服务器交互
使用的技术不是ajax，但是类似
因为不是ajax，所有没有跨域问题，
如果前端使用ajax请求app的服务器，需要后端配合设置一下跨域问题

*XMind: ZEN - Trial Version*