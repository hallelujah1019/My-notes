# AJAX技术点学习三天

## 第一天

### 0.前奏了解

- 自己浏览器访问服务器的时候，服务器响应回来的是一些标签给到浏览器，浏览器对
返回来的标签进行解析，我们就看到了想要看到的页面。
- ajax的补充

	- ajax字面意思：
Asynchronous Javascript And XML--->Asynchronous是异步的意思
异步的javaScript和XML
	- 使用ajax的好处

		- 局部更新，提升用户体验，提升性能
		- 分离开发，提高开发效率。

	- 新增两种在jQuery中使用ajax中方法

		- $.get(url,[请求参数],[请求成功后的 回调函数],[响应数据类型])

			- 例如：
$.get('/common/time',function(res){
    console.log(res);
})

		- $.post(url,[请求参数],[请求成功后的 回调函数],[响应数据类型])

			- 例如：
$.post('/common/time',{id:id}/'id=1&age=2'function(res){
    console.log(res);
})--->post方式中的传参是可以使用对象的形式，也可以使用字符串的形式。

	- jQuery中的ajax的封装库axios

		- //   使用axios来发送请求
    axios.get('/message/getMsg').then(function(res) {
      // res是个对象类型，data是res中的一个属性，并且这个属性的值是一个数组类型
      console.log(res.data);
      var str = template('text', {
        mesg: res.data,
      });
      $('ul').html(str);
    }, 'json');
		- gei带参数
axios.get('/common/get', { params: { id: 123, name: 'jake' } }).then(function(res) {
    // res 就是本次请求的信息
    console.info(res);
    // 获取 从服务器返回的数据
    console.info(res.data);
});
		- // post请求，不带参数
axios.post('/common/post').then(function(res) {
    console.info(res.data);
});
		- // post请求，带参数
axios.post('/common/post', { id: 123, name: 'jake' }).then(function(res) {
    console.info(res.data);
});

	- 模板引擎
把分离的HTML代码和js代码融合到一起的工具，一个库。

		- 需要加载template-web.js文件
<script>./assets/template-web.js</script>

			- 模板引擎的使用：
<!-- 需要整合的HTML标签不要乱放，需要放到script标签的内部告诉浏览器，js标签中放的是HTML代码 -->
<script type="text/html" id="test">--->这个script中的type必须写上text/html这个值，表明这个script标签中时HTML代码，还要必须给这个script给定一个id值，因为后面要使用这个id值获取到这个模板id。
  <!-- 双大括号 -->
  <h2>{{title}}</h2>
  <p>{{age}}</p>
  <ul>
    <li>{{heroes[0]}}</li>
    <li>{{heroes[1]}}</li>
    <li>{{heroes[2]}}</li>
    <li>{{heroes[3]}}</li>
  </ul>
</script>
<script>
  // 这个数据模拟的，相当于ajax请求之后，响应后的数据
  var data = {
      title: '模板引擎练习',
      age: 20,
      heroes: ['曹操', '刘备', '李逵', '西门庆']
    }
    //调用template函数
    /* 返回值就是一个整合好的一个结果
        var str = template(模板的id，数据);--->这个里面的数据一定是js对象的格式，也就是说必须是键值对的格式
     */
    //  利用模板引擎将HTML标签和js标签整合到一起
  var str = template('test', data);
  console.log(str);
</script>
			- <script type="text/html" id="text">
  <!-- name: "dfsdf", content: "sdfdsf", created: "2019-10-14 09:39:40" -->
  {{each mesg}}--->each是模板引擎中的方法   mesg和下面template方法中的mesg那个键相对应
  <!-- 模板引擎中数组中的元素使用$value表示，下标使用$index表示 -->
  <li>
    <div class="info"><img src="images/03.jpg"><span>{{$value.name}}</span>
      <p>发布于：{{$value.created}}</p>
    </div>
    <div class="content">{{$value.content}}</div>
  </li>
  {{/each}}
</script>

success: function(result) {
        // result是数组类型
        console.log(result);
        // 调用template()方法，这个方法中需要传入两个参数，第一个参数是模板id值，这个模板id值表示的是放有HTML代码的内个script标签的id的值，第二个参数是在服务器获取到的参数，这里传的这个参数必须是js对象格式的参数，因为这里获取到的result的类型是数组的类型，所以我们要将这个数组放到大花括号中，将数组放到大花括号中需要有一个键的名字与这个数组相对应，组成一个键值对，template中传的参数必须是js对象类型的参数
        var str = template('text', {
          mesg: result,
        });--->template中传的参数必须是js对象类型的参数
        $('ul').html(str);
      }

- 细化上网的过程

	- 客户端（cline）

		- 向服务器发送请求的一个工具
最常见的客户端工具就是浏览器

	- 服务器（sever）：

		- 本质上，也是一个电脑
		- 服务器的作用：

			- 可以存储网页，开发好的页面都应该放到服务器上。
			- 提供服务，可以把客户端请求的页面返回给客户端。

	- 请求（request）

		- 客户端向服务器索要页面的动作。

	- 响应Response

		- 响应即回应
服务器为客户端提供页面的过程。

	- 资源

		- 服务器上存储的各种文件都叫做资源，比如HTML文件、CSS文件、JS文件、图片、音频、视频都叫做资源。

- 浏览器工具，浏览器点击F12键就可以找到这个浏览器工具Network

	- Response：是响应的意思
	- request：是请求的意思

### 1.服务器软件使用规范

- 1.软件使用要求，服务器上的资源不能随便乱放，必须放到public文件夹中
但是为什么所有的文件都要放到public文件夹中呢，因为使用域名或者IP地址访问服务器的时候，是直接去找服务器上的public文件夹中的文件，所以所有的CSS,JS,img图片等等的文件都要放到public的文件夹中，否则的话，用户拿不到服务器响应的结果。
因为localhost:4000直接找的就是public文件夹
- 2.软件使用要求，服务器上的资源不能直接打开，必须使用浏览器(客户端)，输入网址(IP域名)向服务器发送请求的方式访问服务器上的资源。

### 2.关于本机的IP地址和域名的说明

- 自己计算机的IP地址：永远不会变的一个IP地址，甭管你计算机跟哪儿，这个IP地址是不会变滴，这个IP永远指向自己的计算机，这个地址叫做本地回环地址。
127.0.0.1:4000
在浏览器中输入这个   127.0.0.1:4000   IP地址，浏览器就会访问到public文件中的HTML文件
- 自己计算机的域名：永远不会变的一个域名localhost:4000
localhost:4000
在浏览器中输入这个     localhost:4000   域名 ，浏览器就会访问到public文件中的HTML文件

### 3.如果vscode编辑器出现了问题，不能在终端中开启服务的话，使用Win+R，弹出运行窗口，输入cmd就打开了黑窗口；
第一步：输入盘符：比如：f：回车
第二步：cd F:\MyselfObject\3.就业班的练习代码\6.AJAX知识点练习\1\ajax 回车
第三步：F:\MyselfObject\3.就业班的练习代码\6.AJAX知识点练习\1\ajax>node app.js 回车
显示：开始监听：4000   --->就说明服务器已开启
第四步：Ctrl+cc 回车--->是关闭服务器，两个c回车
在vscode中关闭服务器是Ctrl+c  回车（一个c回车）

- 开启本地服务器步骤

### 4.注意事项：

- 1.服务器不能重复开启，即不能多次开启服务器 node app.js
- 2.关闭服务器，在终端中，按下Ctrl+c
- 3.vscode中打开终端的快捷方式：Ctrl+~，这个飘的符号在Esc键的下边儿
- 4.关闭终端面板，并不表示关闭了服务器，关闭服务器必须手动关闭服务器Ctrl+c

### 5.初识AJAX技术

- 什么是AJAX？
通过一段js代码的运行，这段js代码也可以向服务器发送请求，也可以接受服务器响应的返回结果，这就是AJAX技术。
- 在Network浏览器工具中的type下的xhr表示的就是通过ajax技术进行请求的文件
- ajax基本语法：
<!-- 引用jQuery文件 -->
  <script src="./assets/jquery.js"></script>
  <script>
    $.ajax({
      // 属性：值
      // url这个键值对是一定要写的，url这个值是要发送的是需要访问文件的地址，请求的地址
      // url: 'http://localhost:4000/test.txt',
      //url: '/test.txt',    //http://localhost:4000/可以省略，但是建议斜杠保留/
      url: '/common/abc',--->这种方式是通过接口访问后端数据，起的作用其实就是一个网址。
      // 服务器做出响应，通过success这个属性可以接受服务器做出的响应，我们使用一个匿名函数来接收这个返回的结果，结果传到这个匿名函数中，所以这个匿名函数需要有一个形参，我们来打印一下这个形参         
      success: function(result) {
        console.log(result);
        document.write(result);
      }
    });
- 接口介绍

	- 什么是接口？
其实就是一个网址
	- 有什么作用？
发送ajax请求的时候，可以为url添接口地址；
方便获取数据的一个网址。
	- 接口是哪里来的？
后端同学提供的
	- 有哪些接口可用呢？
后端同学设计完接口之后，会提供给我们一个接口文档。

- 接口文档

	- $.ajax{(
  type:'请求方式'，--->get/post，get方式不是很安全，加入用户密码的时候密码就能在后台看到；post方式相对来说安全些，但是也不是特别安全；
  url:'接口地址',
  data：'请求参数',--->如果没有请求参数的话，data这个键值对可以不写。
  //data的写法：'参数=值&参数=值&参数=值',
  //data以对象的方式写：data:{参数:'值'，参数：'值'，......}
  dateType:'响应数据格式',
  success:function(result){
    console.log(result);
    console.log($(this));--->ajax中的this指向的是ajax这个对象本身。
   }
)}
	- 例如：
$.ajax{(
  type:'GET',
  url:'/common/time',
  data：'',--->请求数据的意思
  dateType:'text',
  success:function(result){
    console.log(result);
   }
)}

- $.ajax()方法中键的讲解

	- type:  type有一个默认值，默认值是GET方式请求，如果不写的话，那么就是默认值GET方式请求。
表示请求的方式或方法，现在常用的就是get和post

		- GET
		- POST

	- data

		- 意义：向接口发送请求的时候，携带的数据，也就是接口文档中的请求参数
		- data的写法

			- 字符串的形式
username = xxx&pag = xxx;
			- 对象的形式
例如：data:  {
   username:  name,
}

	- dataType

		- 服务器响应数据的格式
		- 指定该项，jQuery会自动将服务器响应的数据处理成JS数据（数组，对象，字符串，布尔值）
		- dataType的常用值：
json--->json格式是最常见的服务器响应格式
text--->表示服务器返回的是文本类型的数据
xml--->表示服务器返回的是xml格式的数据，现在已经很少用它了，作为了解即可
jsonp/script/html--->也很少用。

	- beforeSend

		- 意义：
在发送ajax请求开始之前，允许我们做一些事情
		- 语法：
$.ajax({
  beforeSend:function(){
  
  }
});

	- complete

		- 意义
在请求响应完成后允许做的什么事儿，无论请求成功还是失败，都会触发这个函数
		- 语法：
$.ajax({
  complete:function(){
  
  }
});

	- contentType：false；--->意思是告诉浏览器不添加请求头     不设置类型
	- processData：false；--->意思是告诉浏览器不需要处理formData数据。

## 第二天

### 1.原生的ajax的使用
(就是不使用jQuery文件发送ajax请求)

- 1.GET和POST请求方式的区别

### 2.原生ajax请求，使用的是XMLHTTPRequest()对象提供的属性和方法
new = XMLHTTRequest();--->返回是一个对象类型request是请求的意思

- GET请求方式

	- 第一步先实例化一个XMLHTTPRequest对象
这个对象是原生的js底层对象。

		- var xhr = new XMLHTTPRequest();

	- 第二步，调用open()方法
设置请求的方式和url
open('参数1','参数2')中有两个参数，都是字符串类型的，
参数1：表示的是请求方式GET/POST方式
参数2：表示的是url的请求地址。

		- xhr.open('GET/POST','/common/time');

	- 第三步调用send()方法，发送请求，到第三步，才表示发送了ajax请求

		- 就这一句代码，不需要传任何参数，这个方法的作用就是发送ajax请求。
xhr.send();

	- 第四步，当请求响应过程结束，
然后接收服务器响应的结果

		- xhr.onload = function(){
   xhr.responceTest--->只可以接受文本类型的结果
   xhr.responce--->可以接受任何类型的结果，所以我们经常会使用这个属性用来接收服务器返回的结果。
   console.log(xhr.responce);
}

	- 如果有请求参数的话要这样写，请求参数直接用？问号拼接到url后面即可，请求参数使用键值对的方式进行传递。
例如：
var xhr = new XMLHTTPRequest();--->实例化ajax实例对象
xhr.open('GET','/common/checkUser?username=lisi');
如果请求参数是一个以变量的形式进行传递的话，需要这样写
//xhr.open('GET','/common/checkUser?username='+name);，就是传递的变量和键名之间用加号进行连接。
xhr.send();
//事件可以放到send()前面也可以放到后面
xhr.onload = function(){
   console.log(xhr.responce);
}
	- 这里需要注意，其实open()方法中时有三个参数的
第一个是请求方式GET/POST
第二个是url的请求地址
第三个参数是true、false，true表示的是异步操作，false表示的是同步操作，默认值是true，默认是异步操作。

- POST请求方式

	- 创建xhr对象
 var xhr = new XMLHTTPRequest();
	- 调用open方法，设置请求方式和url()
xhr.open('POST','/message/addMsg');
	- 如果提交的数据是纯文本的数据的时候，没有文件上传，就需要设置这个请求头。
如果使用FormData的时候，不需要自己设置请求头，浏览器自动添加请求头
设置一个请求头，固定一行代码 ，这句代码的意思是告知浏览器，请求的数据的类型是这样的'application/x-www-form-urlencoded'，这种类型表示的就是'name=xxx&content=xxx'这种格式
xhr.setRequestHeader('Content-Type','application/x-www-form-urlencoded');
	- 调用send，发送请求，POST的请求参数是放到send()中的，必须以字符串的格式进行传递，不能是以对象的类型进行传递。
xhr.send('name=xxx&content=xxx');
	- 设置onload事件，接收服务器响应的结果
xhr.onload = function(){
  console.log(this.response);--->事件中的this指向的是事件源
}

### 3.浏览器问题

- xhr.onload事件，属于XHR对象新增的一个属性，IE6/7/8不支持onload，低版本的浏览器可以使用onreadystatechange事件来代替。
- onreadystatechange事件
会触发多次，如果想要只接收一次结果的话，加一个if判断就，判断readStart的值等于4时，再接收结果。这就直接受到一次啦。
触发时机：
第一种触发时机：
                  当readyState属性值(ajax的状态)改变的时候0变1,1变2，。。的时候会触发这个事件；
第二种触发时机：
                 但是当接收的数据量发生变化的时候，也会触发这个事件。
- readyStart的属性值，其实readyStart表示的就是ajax请求过程中的几个状态，它有五个值0-4。
0：表示UNSENT，XHR被创建，但尚未调用open()方法，状态UNSENT
1：表示open()方法已经被调用，建立了链接，状态OPENED；
2：send()方法毕竟被调用，并且已经可以获取状态行和响应头，
状态HEADERS_RECEIVED；
3：响应体(服务器返回的数据)下载中，responseText属性可能已经包含部分数据，状态LOADING，表示正在接收中。。
4：响应体（服务器返回的数据）下载完成，可以直接使用 `responseText`或response 获取完整的结果，状态为DONE，表示所有的响应已经接收完毕。
其实我们之关心值为4的时候。
- 例如：
var xhr = enw XMLHTTPRequest();
xhr.open('GET','/common/time');
xhr.send();
//当ajax的状态值，发生改变的时候，会触发下边的时间
xhr.onreadystatechange = function(){
   if(this.readyState===4){
       console.log(this.response);
   }
   //console.log(this.respanse);
}
- 记住：
如果服务器返回的数据量非常大，那么浏览器就是分块接收数据的。
接收中的readyState的状态值是3，因为值为3的时候，才是接收数据的状态。

### 4.IE浏览器缓存问题
也叫GET缓存，不光是IE浏览器有缓存问题，只是IE浏览器的缓存现象比较明显而已，其他的浏览器也存在缓存问题。

- IE浏览器会识别每次请求的地址，如果每次请求的地址都一样，他就会直接从缓存中返回给浏览器，这个机制不是特别友好。
- 如何解决这个问题呢？
只要保证每次请求的url地址不一样就可以啦，添加一个请求参数，这个请求参数是一个随机数，如果怕某次的随机数一样，我们再添加一个时间戳，这就肯定每次请求的url地址是不一样的了；或者加一个时间戳（Data.now()）也可以解决这个这个问题，因为每次的时间都不一样。所以每次的url地址也就不一样。
xhr.open('GET','/commen/time?data='+Math.random());

### 5.其他问题

- IE678中怎么实例xhr对象呢？

	- var xhr = new ActiveXObject('Microsoft.XMLHTTP');--->IE6/7的写法

- responseType属性
类似于$.ajax()中的dataType属性，接收的数据格式
一般，xhr.responseType = 'json';一般都将这个数据格式设置成JSON格式，但是我们要知道，虽然将数据的接收格式设置成了JSON格式，但是浏览器接收到的是一个对象类型，是JSON直接将字符串转成了对象类型。
- var xhr = window.XMLHttpRequest?new XMLHTTPRequest():new ActiveXObject('Microsoft.XMLHTTP');
这是一行三元表达式，如果当前浏览器有XMLHTTPRequest的时候就会创建XMLHTTPRequest()这个对象，如果当前浏览器为IE6/7的时候浏览器中就没有XMLHTTPequest这个对象了，那就创建ActiveXObject('Microsoft.XMLHTTP');这个对象。
- 实际开发中，原生的ajax使用的概率是很小的，一般我们使用的是封装好的ajax，比如
$.ajax({
   
});

### 6.异步操作

- 异步特点：
同一个时间点，执行了多个操作
耗时操作并不会阻塞后续代码的执行。
异步的本质其实就是同一个时间点儿执行了多个操作。
实际开发中，大多数情况是异步开发
- 一次性定时器不会阻塞后续代码的执行。
setTimeout(function(){},2000);

	- console.log(111);
setTimeout(function(){
  console.log(333);
},2000);
console.log(222);
先输出111，在输出222，最后输出333，并且在输出222的时候也在执行定时器的操作

- 我们所说的ajax也是一个异步操作，ajax也是一个耗时操作，再快的ajax也会耗时
xhr.send()这一步骤是非常耗时的

### 7.同步操作

- 同步操作特点：
同一个时间点儿，只能执行一个操作，前面的代码没有执行完毕，后续的代码不能操作。前面的代码会阻塞后面的代码执行。
同步是send()这个方法阻塞了send()后面的代码执行。
事件要先执行，等待触发条件。
- 例如：
console.log(111);
//耗时操作，open方法的第三个参数为false，默认值是true，false表示是一个同步的ajax请求，会阻塞后续代码的执行
var xhr = new XMLHTTPRequest()
xhr.open('GET','/common/time',false);
xhr.send();
xhr.onload = function(){
    console.log(333);
}
console.log(222);

### 8.封装ajax

- 回调函数是处理返回结果的最佳方案。
- 为了更好的理解这个回调函数，我们在这里写一个小栗子，
function abc（cb）{--->这里的cb必须是函数类型，为什么是函数类型，因为我们后面需要给这个形参传参数，所以这个cb是函数类型。
    setTimeout(function(){
       var x = 1;
       cb(x);
    },1000)
}
abc(function(res){--->这个函数就是回调函数，为什么叫回调函数呢，因为这个函数当做了一个函数的形参进行了传递，所以我们叫这个函数是回调函数。
    console.log(res+2);
})
- // 3. 由死变活，把代码中写的比较“死”的地方，变得灵活一点，其实就是设置成函数的形参
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
        // ajax('GET', '/common/checkUser', 'username=zhgangs'); // 验证用户名
        ajax(
            'POST', 
            '/message/addMsg', 
            'name=xxx&content=yyy', 
            function (res) {
                console.log(res);
            }
        ); // 添加留言

## 零号回顾AJAX知识点

### 1.原生的ajax和封装的ajax，重点是封装的ajax
   axios在vue中是经常用到的。

### 2.ajax发送请求必须知道的内容
  url地址
  请求的方式
  请求参数
  success(回调函数)
     根据需求来编写
     结合模板引擎渲染页面
     跳转页面
     提示用户
例如：
    $.ajax({
    url:接口地址,
    type:  get/post,
    //请求参数
   data：{
    键：值，
}
   //data若是formdata类型，这里要注意：需要实例化一个formdata表单
  var fd = new FormData(document.querySelecter('form'));--->这里注意：括号中获取的form对象必须是一个DOM对象，千万不要是jQuery对象。
   data: formData,
   //必须添加这两个属性
   contentType:false,
   processData:false,
})

## 第三天

### 1.FormData--->表单数据

- FormData
也是H5中新增的一个内置对象
var fd = new FormData();
这就创建了一个formdata实例对象
- FormData这个内置对象的作用是：
用来收集表单信息的，只能获取有name属性的表单元素的value值。
方便获取表单中各项的值，包括用户名，密码，单选，多选，上传的文件（包括图片，视频）
- 步骤

	- 1.收集用户输入的值
使用FormData步骤1：找到form表单，找表单的DOM对象
var fm = document.getelementById('fm');
	- 2.步骤2 实例化FormData，并传递表单对象fm，这个fm必须是DOM对象，不能是jQuery对象。
var formdata = new FormData(fm);
	- 3.将这些值使用ajax传递给服务器
var xhr = new XMLHTTPRequest();
xhr.open('POST','/common/fd');
xhr.send(formdata);
xhr.onload=function(){
    //接收到的数据应该死服务器响应的数据
    console.log(xhr.response);
}
	- 4.这里需要注意，如果POST提交方式提交的数据是formdata类型的话，不需要我们写请求头了
浏览器会自动添加formdata的请求头。
	- 5.注意事项：
不能让表单提交：第一个方法是将提交按钮设置成button类型，
如果input的类型是submit类型的话，需要在js代码中通过事件对象阻止表单提交的这种默认行为e.preventDefault();
表单中各项必须要有name属性，因为服务器是通过name属性来获取数据的，所以nema属性必须要有。
	- 如果FormData和ajax结合使用的时候需要必须在ajax中添加两个属性：
contentType：false；
processData：false；
这两个属性是必须添加的。
	- 6.怎样找到上传的文件呢？
获取到上传表单pic，文件的上传是传到了这个DOM节点中的files这个属性中，files是一个数组类型（对象类型），因为是一个数组，所以可以上传多个文件
var pic = document.getElementById(文件上传控件的id)；
console.dir(pic);--->查看一下这个DOM节点下的属性，就可以找到files这个属性，这个files属性是一个伪数组类型。
var filObj = pic.files[0];--->这个里面的下标是为了精确找到图片在数组中的位置。
上传多个文件的时候，需要给input标签添加multiple这个属性    
如果只允许上传图片格式的图片：那就给input框添加accept =".jpg,.png,.gif"
因为图片格式有好几种，如果要包括所有的图片那么还可以这样写
accept = "image/*"，使用*(通配符)表示所有的图片格式
accept = "image/png"
accept = "image/gif"
	- 7.如果页面中没有form表单标签的话，光有一些普通表单，那么怎样获取这些表单中的值呢

		- 没有form表单的话，
先实例化formdata对象
var fd = new FormData();
//fd.append('键名'，‘值’);--->这个方法是往没有form表单标签的情况往formdata对象中添加值，在fd对象中追加一个值
fd.append('user',document.getElementById('').value);
每一个表单都要添加一次，有几个表单控件就要添加几次
那么我们怎样获取添加的值呢？
我们使用fd.get('user');--->填写我们添加的键名，就可以访问到添加的数据

	- 8.为图片文件创建一个临时的url地址，URL也是js的一个内置对象
$('#input_avatar').change(function() {--->给一个添加文件按钮注册改变事件
     var file = this.files[0];--->获取到图片对象
    var url = URL.createObjectURL(fileObj);--->为文件对象创建一个url地址，这个url是一个临时的url，URL也是js的内置对象。  
}

	- 拓展知识点
1.询问框confirm(‘你确定要删除’);  var a = confirm('你确定要删除吗');
   这个方法有返回值，是布尔值，一个true，一个false
   这个询问框的作用和alert的作用是差不多的。
2.滚动条滚动事件，给window添加滚动事件。
$(window).scroll(function(){
   //浏览器的高度
   var winHeight = $(window).height();
   //卷曲出去的高度
   var scrollTop = $(document).scrollTop();
   //文档的高度
   var documentHeight = $(document).height();
   if(winHeight+scrollTop+100>=documentHeight){
     console.log('123');
    }
});
3.window.location.search可以获取到浏览器地址栏的请求参数
返回值是字符串类型：?name=zhangsan&age=10
  window.location.search.slice(1)--->是将问号去掉，语法含义是：从下标是1的位置开始截取，一直截取到最后，slice()这个方法是String类中的一个方法。

### 2.案例知识点

- 1.超链接的跳转是GET请求

*XMind: ZEN - Trial Version*