# WebAPI技术学习笔记

## WebAPI第一天

### 01-JavarScript组成部分

- ECMAScript 核心语法
- BOM 浏览器对象模型
- DOM 文档对象模型

### 02-API和WebAPI

- API

	- 专业：应用程序接口-------已经封装好的对象上属性和方法
	- 通俗一点说：其实就是一个工具（这个工具是第三方给的，这里说的第三方主要指的是插件）

- WebAPI

	- 浏览器所提供给开发操作网页和浏览器的工具库

		- DOM----->文档对象模型
		- BOM----->浏览器对象模型

### 03-DOM（文档对象模型）

- 01-什么是DOM

	- 文档对象模型（ document（文档） object（对象） model（模型））把整个页面当做一个对象，我们学习这个对象上的属性和方法。
	- 文档：一个html文件

		- html文件中有标签、文本、标签的属性

	- 对象模型：浏览器去加载网页时，会把整个html文件以及文件里的标签、标签属性，文件统一转换成对象，以树状的结构存放到内存里。
	- 节点对象：文档树上的一个分支。标签就是DOM节点
	- 元素：所看到的标签就是一个元素（只要是标签都是元素）
	- 文本：标签中的内容就是文本；比如：<a href="#">百度</a>  百度就是文本
	- 属性：就是标签的属性  比如：<a href="#">百度</a>   href就是标签的属性
	- 为什么叫文档对象模型：需要把文档document看成一个对象对象封装好多方法在里面，学习别人封装了什么方法，怎么用，能帮助我们做什么效果，不需要考虑内部怎么实现的，更高效的关注于我们的业务。
	- 标准属性：属性有特定功能，管理各自的功能，比如：img标签上的src属性，src属相只能填写图片地址。

- 02.获取节点对象

	- document.getElementById();通过节点上ID值，获取DOM节点，返回值是一个DOM节点，返回值的类型也是一个对象。-------注意：如果没有获取到想要获取的节点ID，浏览器会返回一个null，没有获取到相应的节点。
	- 获取body对象-----document.body;---这里的body是document的一个属性。
因为在页面中body只有一个，通过body这个属性进行获取的

- 03.注册事件  click事件（左键点击一次）

	- 事件对象注册给谁？  注册给元素对象（DOM节点）
	- 给对象节点注册事件的时候，需要问自己三个问题

		- 事件注册给哪个DOM节点
		- 注册的是什么事件

			- onclick---->单击事件（鼠标左键）------>只要鼠标左键按下就会触发事件
			- 鼠标事件

				- mousedown---->鼠标按下事件
				- mousemove---->鼠标移动事件
				- mouseup------->鼠标弹起事件

			- input框中的事件

				- onfocus--->获取焦点（光标）事件
				- onblur--->失去焦点（光标）事件

		- 事件发生后产生了什么效果

			- 具体逻辑和功能实现的代码

	- 注册目的：为了和用户产生交流互动
	- 给节点对象注入一个鼠标单击事件

		- 对象节点.onclick = function(){-----这个匿名函数的目的是为了响应点击后的效果
匿名函数中写的是点击之后的行为。
}

	- 对象.style;  返回值是也是一个对象类型，只要返回的是对象类型，这个对象下边就有一系列的属性和方法。
style是对象下的一个属性。这个方式只能获取行内样式

		- 对象.style.width:获取style对象上的属性（width），返回的是width的值。
		- 对象.style.width = "200px";
对象.style.height = "200px";

			- 后面的值一定要是字符串类型，不要忘记加上引号

	- 节点对象.value=内容；  改变DOM节点的value值。
节点对象.value；----->只能是获取有光标输入的内容，可以使用value属性进行获取，
比如：可以获取textarea(多行文本输入框)中的内容
	- onfocus---获取光标事件   聚焦  获取光标的时候会触发
	- onblur----失去光标事件   模糊  失去光标的时候会触发

- 04.DOM类样式---------className 返回值是一个字符串（String类型）使用这种方法设置类名的时候不是很友好

	- 获取DOM节点的类名就是使用className获取。这个属性可以获取和设置类名。
	- 单独设置className的时候，会把原来的类名进行覆盖掉，使用这种方法设置类名不是很友好

- 05.classList是管理类名，返回值个对象，classList下面有属性和方法，以后操作类名就使用classList()这个方法。

	- 添加类名的方法：DOM节点.classList.add();-----如果多次添加的类名一样，则只添加一次，多次添加无效
	- 删除类名的方法：DOM节点.classList.remove(类名1,类名2....);---删除指定的类名
	- 这个方法，如果有括号中的类名就将这个类名删掉，如果没有这个类名就将这个类名添加上。如果有这个类名就删除，如果没有这个类名就添加：DOM节点.classList.toggle(类名1,类名2....);---toggle()这个属性还是比较友好的。这个方法还是比较友好的。

- 06.获取元素对象的另一种方法（一般这两种方式获取的是多个DOM节点，优先使用这两种方式）

	- getElemtntsByTagName('标签名');   ---------  获取多个同名标签   
	- getElemtntsByClassName('类名');------可以获取多个相同类名的标签
	- 即使页面元素只有一个，那么他获取的也是元素只有一个的伪数组。

- 07.自定义属性：开发者，按照自己的需要，把一些数据写在标签内，属性名，随便起。
自定义属性场景：在DOM节点标签内设置自己需要的属性。

	- 自定义属性的命名方式：data-名字（名字前面必须要加上data-）
	- 获取自定义属性：div.dataset;-------返回一个对象
	- 例如：div.dataset.src-----后面的src是自定义给到的。
	- 自定义属性的名字是随便取的。

- 08.函数内部有一个关键字：this；原则：当前你点击的是哪个DOM节点，this就是指谁。---this也可以理解为函数中的一个指针，指向当前获取到的DOM节点。

	- for循环的执行顺序
	- 在循环里面获取当前点击对象就使用this来表示当前对象

- 09.DOM属性----checked

	- <button disabled=true></button>   disabled属性是按钮禁用的意思，disable是标签中的一个属性，并不在style属性中
	- 开关属性：只有两种状态，要么开，要么关。  

- 10.开关思想：可以回顾一下判断一个数是否是质数案例或者回顾一下全选反选和不选案例。先设置一个开关：var key = true;通过业务逻辑来改变开关这变量的值，这个变量只有两个值，一个true一个false

## WebAPI第二天（重要）

### js属性和方法如何记忆

- js属性和方法记忆方法

### 操作属性

- 获取节点对象：
document.querySelector('css选择器');----括号中的css选择器也是以字符串的形式传入，返回的是一个节点对象，并不是多个节点对象

	- 如果是传入的是ID选择器一定要加上#号 ------#id值
	- 如果传入的是类名选择器一定要加上. （英文点...） -------.类名

- document.querySelectorAll('css选择器');  -----返回的是一个伪数组。
可以用for循环进行遍历；
但是这个方法可以使用forEarch()循环遍历，虽然这个伪数组有forEarch()方法，但它还是一个伪数组，并不是一个真数组。
- 操作自定义属性：
DOM节点对象.getAttribute(属性名);-----获取自定义的属性名或者标准属性名，返回值就是需要查的属性值，一般情况下是获取自定义的属性名的值，返回值是一个字符串类型（String）

	- 设置自定义的属性值：
DOM节点对象.setAttribute('自定义属性名'，属性值);
	- 删除自定义属性
DOM节点对象.removeAttribute('属性名');----括号中传入的是要删除的属性名（自定义的属性名）

### 注册事件！！！（重要）

- 多人合作，注册的事件可能会被覆盖掉，使用addEventListener()这种方式给同一个事件源注册多个事件的时候，事件不会被覆盖掉，但是使用onclick()的方式会将事件覆盖掉。
- DOM节点对象.addEventListener('click',function(){
	点击之后执行的函数；
},第三个参数（默认值是false，默认在冒泡阶段执行）)；----这个方式多次注册事件不会被覆盖；
第一个参数是：事件名   click（单击事件）
第二个参数是：点击之后执行的函数。
第三个参数是：事件执行阶段，默认值是false（默认在冒泡阶段执行），若将值改为true（将事件改为在捕获阶段执行）如果父节点注册了和目标节点同样的事件，那么父节点的事件也会执行。

### 事件的三个阶段

- 捕获
- 达到目标DOM节点
- 冒泡

	- 事件默认是在冒泡阶段执行，若父节点和目标节点有同样的事件，
点击目标节点时，父节点的事件（与目标节点相同的事件）也会触发。

### 阻止冒泡

- DOM节点对象.addEventListener('click',function(e){
//传入一个形参e，e被称为事件对象
e.stopPropagation();---阻止冒泡
}

	- 为什么要阻止冒泡？
如果子元素不阻止冒泡，事件默认是在冒泡阶段执行，父元素如果和子元素注册了一样的事件，那么我点击子元素后，父亲注册的相同的事件也会生效，体验感不好，所以，我们要阻止冒泡这个传递的过程。

		- 为什么要阻止冒泡事件

### 事件对象

- e---->事件对象
- 事件对象.clientX
事件对象.clientY

	- 相对于页面的可视区域（针对屏幕左上角，获取坐标）

- 事件对象.pageX
事件对象.pageY

	- 相对于页面（body）的左上角的位置---->body区域，可以获取鼠标在文档中的位置

- 事件对象.target------>点到谁上面就是谁。------->返回的是一个DOM节点对象，是DOM节点对象就有属性和方法
- 事件对象.currentTarget------>事件注册给谁就是谁
事件对象.currentTarget==this（结果是true）
- 浏览器阻止右键弹窗：
document.oncontextmenu = function(e){
	e.preventDefault();-----阻止默认行为
}-----------prevent(阻止)Default(违约)

### 事件类型补充

- onclick：单击事件
- input框中的：

	- onfouce获取焦点事件
	- onblur：失去焦点事件

- 鼠标点击事件

	- mousedown：鼠标按下事件
	- mousup:鼠标弹起事件
	- mousemove：鼠标移动事件
	- mouseover：鼠标移入事件
	- mouseout: 鼠标移出事件
	- mouseenter：鼠标移入事件
	- mouseleave：鼠标移出事件

### 获取元素位置

- DOM节点.offsetLeft   ---->offsetLeft=left+marginleft得到，只能用户获取，不能设置
- DOM节点.offsetTop  ----->offsetTop=top+margintop得到，只能用于获取，同样不能设置
- position：absolute   绝对定位是相对于页面的左上角进行定位。---->pageX,pageY联用
- position：fixed   固定定位是相对于可视页面进行定位----->.clientX,clientY联用
- return是终止一个函数，终止当前函数执行，return下的代码不会再执行
- 在浏览器上的console上可以获取全局变量，也就是可以在console上设置全局变量

	- 这是一种程序bug，后期要解决这中问题。

### 事件解绑

- 事件解绑其实就是在注销事件
- DOM节点对象.removeEventListener('click', fn); 
参数1：注销的事件类型   参数2：注销的函数名

### 事件委托

- 委托事件不是给子节点注入事件，而是给父节点注册事件，那么点击子节点的时候，根据冒泡机制，父节点的事件也会跟着触发。

	- 什么是事件委托：


- DOM节点.innerHTML---返回一个字符串
- DOM节点.innerHTML可以识别html代码
DOM节点.innerHTML = '<li>我是第四个li标签</li>';-------以这种方式进行标签的添加，会将父节点下面的其他li标签覆盖掉。
console.log(DOM节点.innerHTML);------>返还的是一个字符串
- DOM节点属性.nodeName------->返回一个DOM节点的大写标签名，类型是String类型
- e.target.nodeName;--->可以分成两部分进行理解
e.target--->本身获取（返回）的就是一个节点对象，只要是一个对象，对象下面就会有属性和方法。
nodeName就是一个这个对象下面的一个属性。
- 事件委托应用场景：给新增的DOM节点注册一样的事件，就要用到事件委托。

## WebAPI第三天

### 使用innerHTML的方法在js中创建一个HTML节点：  父节点对象.innerHTML = '<li>大傻</li>'
innerHTML方法可以获取和设置BOM节点的html结构

- 使用父节点对象.innerHTML的方法，就将一个节点创建好了，不过使用这种方法就直接将父节点下面的子节点覆盖掉了。我们要使用这种方法进行添加节点：
父节点对象.innerHTML = 父节点对象.innerHTML+'<li>L4WUDU</li>';很显然，使用这种方法给父节点添加子节点是比较麻烦的。

### 获取父节点中的内容

- 父节点对象.innerText;-----------返回的是一组字符串（String类型）
但是这个属性不具备解析HTML文档结构功能，只是获取BOM节点的文本信息，不会获取HTML结构
也可以设置节点的文本信息，
例如：节点.innerText = 'aaa';----就把所有的文本信息替换成了‘aaa’；

### 我们还可以使用这种方式给父节点添加一个子节点：
var li = document.createElement('li');--------这种方法返回的是一个标签字符串（<li></li>）但是这种方式只是在js中创建了一个子标签，并不会自动加到页面结构上。

- 还需要父节点上的一个添加DOM节点的属性：父节点.appendChild(li);
这样父节点上才会加上了这个子节点。
这种方式在父节点上添加一个子节点其实是将添加的子节点作为最后一个子元素进行的添加，添加到父节点的最后。

### 我们还可以在在任意一个子节点前面添加一个子节点

- 父节点.insertBefore(新的子节点,旧的子节点)
var second = document.querySelector('.dasha');-----以获取类名的形式获取子对象节点
ul.insertBefore(li, second);
第一个参数是：需要新添加的DOM节点
第二个参数是：需要在哪个子节点前面进行添加（第二个参数是子节点对象）

### 通过父节点获取所有子节点

- 这是一个属性，不是一个方法：
父节点.children;------返回值是一个所有亲生子节点的集合（伪数组）
如果想要获取父节点下面的具体的某个子节点就可以这样写：父节点.children[下标];
例如：ul.children[0];--->就是获取第一个ul标签下的第一个li标签子节点；

### 通过子节点获取父节点（parentNode是属性）

- 子节点.parentNode;-----返回值是一个父亲节点（绝对上下级的父亲节点）

### 通过子节点获取上一个和下一个兄弟节点

- 节点对象.nextElementSibling
- 节点对象.previousElementSibling
- 补充：节点对象.offsetParent;

### 删除父节点中的子节点（方法）

- 父节点.removeChild(要删除的子节点);--------括号中直接写被删除DOM节点，不需要加引号

### 发布微博

- 发布微博1.0

	- //   需求：
  //   点击发布按钮， 把写在文本域里面的内容， 作为ul的内容存在
  //   思路：
  //   给按钮注册点击事件， 得到用户输入的内容， 创建一个新的li， 把用户输入的内容作为li的新内容， 追加到ul里面
  //   步骤：
  //   1. 获取元素 - 按钮, ul, 文本域
  //   2. 注册点击事件
  //   3. 在点击事件的处理程序里面
  //   3.1 获取文本域的内容
  //   3.2 创建一个新的li， 作为ul的子元素
  //   3.2 .1 因为原来的内容还在， 所以使用document.createElemenet创建新的li
  //   3.2 .2 新的li要有内容， 使用innerHTml设置新建的li的内容
  //   3.3 把新建的li使用insertBefore的方式插入到最前面
  //   获取DOM节点  按钮   文本域   ul
  var btn = document.querySelector('.weibo-btn');
  var text = document.querySelector('.weibo-text');
  var ul = document.querySelector('.weibo-list');
  //   给按钮注入点击事件
  btn.addEventListener('click', function() {
    // 分析：当点击按钮的时候，要首先获取到文本域中的内容，然后将获取到的文本域中的内容添加到第一个li标签的前面，还要创建一个li标签，然后将获取到的文本域中的内容添加到li标签中
    // 先获取内容，使用value是获取带有光标的输入的内容
    var content = text.value;
    // 在这里要进行判断一下，如果输入的内容为空，要进行一个友好提示
    if (content == '') {
      alert('请输入发布内容');
    } else {
      // 创建一个li标签
      var li = document.createElement('li');
      // 将获取到的内容添加到li标签中  这里要记住，innerHTML中的HTML是大写
      li.innerHTML = '<p>' + content + '</p><span>删除</span>';
      // console.log(text.value);
      // 我要在ul中的第一个li标签前面记性添加这个li标签
      // 首先先要获取ul标签中的第一个li标签
      var first = document.querySelector('ul li:first-child');
      // 再在ul中进行添加，第一个值是新创建键的节点，第二个值是在哪个节点前添加
      ul.insertBefore(li, first);
      // 最后，将文本内容进行清空
      text.value = '';
    }
  });

- 发布微博2.0

	- // 首先先要获取ul标签中的第一个li标签，这里获取ul中的第一个元素是通过方法获取的，
//   var first = document.querySelector('ul li:first-child');
//   我们要进行优化一下，我们要通过属性的方式进行获取，ul.children，使用这种方式返回的是一个伪数组，是伪数组就有下标和长度，通过伪数组的下标我们就可以获取到ul中的第一个元素
      var first = ul.children[0];

- 发布微博3.0

	- //-------------   通过事件委托来实现删除功能----------------
  //   为什么要用事件委托来实现这个删除的功能，因为当我们发布一条新的内容的时候，删除功能不能将新添加的内容进行删除，用上面的方法进行删除，只是获取到了当前页面上存在的span标签，所以我们要使用事件委托来做
  // 那么什么是事件委托呢：事件委托就是新添加的内容和之前存在的内容拥有同样的注册事件；因为文档document对象存在冒泡机制，事件默认是在冒泡阶段执行的，当我点击子节点的时候，冒泡机制开始执行，其所在的父节点如果注册了同样的事件就会被触发。
  // 所以针对冒泡机制，我们在这里要给li标签的父元素ul注册点击事件
  ul.addEventListener('click', function(e) {
    // 我们要知道鼠标具体点击的是谁，使用事件对象来获取具体点击的是谁
    /* 
        e.target-------是点击的是谁就是谁，返回的是一个节点对象，是对象就有方法和属性，nodeNome是获取点击的节点对象的标签名。
        e.currentTarget--------是事件注册给谁就是谁

     */
    if (e.target.nodeName == 'SPAN') {
      // 通过点击获取到的span标签获取span的父元素
      var li = e.target.parentNode;
      //   然后通过li的父节点ul删除父节点ul下的子节点li
      ul.removeChild(li);
    }
  });

## WebAPI第六天

### 新增事件：
触摸事件

- 手指触摸屏幕事件
touchstart ---->手指触摸到屏幕的时候开始触发事件
- 手指移动事件
touchmove--->手指在屏幕上移动的时候触发事件
- 手指离开屏幕事件
touchend--->手指离开屏幕时触发事件

### 新增事件对象e

- e.touches--->屏上的触摸点
- e.targeTouches--->元素上面的触摸点
- e.changedTouches---->变化的触摸点
可以获取到最后离开屏幕的坐标点。
- 如果获取一个对象中没有的属性，那么就会返回undefined，但是不会报错儿

### zepto类库

- 1.加载zepto.js文件
- 2.获取DOM节点
var box = $('CSS选择器');--->字符串类型
返回值是一个Zepto对象
- 3.DOM节点对象.css();--->设置各种CSS样式
- 4.获取多个DOM节点
var boxs = $('.box');---->获取多个.box节点
例如：boxs.css('width','500px');-->给所有.box添加样式
- 5.boxs.on('click(事件)',function(){});--->这就给所有的.box注册事件，移动端注册事件就是使用on的方式
- 6.DOM节点.hide();--->隐藏DOM节点
- 7.DOM节点.append();--->添加DOM节点
- 8.DOM节点.width();--->获取的是DOM节点的宽度
- 9.DOM节点.css('css属性名','属性值');

### touch.js

- 1.先引入zepto.js文件，再引入touch.js文件-->记住就行
- swipe滑动事件

	- swipeLeft--->左滑
	- swipeRight--->右滑
	- swipeUp--->上滑
	- swipeDown--->下滑

- 这里需要注意：页面调成移动端模式后首先要先将页面刷新一下，重新刷新后设置倒移动端的事件才会生效

## WebAPI第五天

### DOM属性：
clienWidth--->盒子内容区域的宽度
DOM节点.clienWidth--->返回值是一个数字类型

### DOM属性：
clienHeight--->盒子内容区域的高度
DOM节点.clienHeight--->返回值是一个数字类型

### 新增事件

- 动画执行完毕后触发的事件：animationend  
这个animationend时间只能以
box.addEventListener("animationend", function() {
    console.log(2);
  });
- 过渡完成后触发的事件：transitionend  
box.addEventListener("transitionend", function() {
  //   console.log(1);
  // });
- onscroll-----滚动事件，使用滚动事件的前提是，只要有滚动条就可以注册滚动事件
只要鼠标进行滚动，就会触发滚动事件
DOM节点.scrollTop--->返回值是一个number类型，表示的卷入高度

## WebAPI第四天

### 新增事件 

- keydown键盘按下事件，
只要按下键盘上的键，就能触发事件
- keyup键盘弹起事件
只要是键盘弹起，就能触发事件
- 鼠标事件

	- 鼠标移入事件

		- onmouseover

	- 鼠标移出事件

		- onmouseout

### 新增事件对象

- e.keyCode;----->可以知道点的是哪个键
返回值是一个number类型，返回的是一个键盘码

	- 回车的键盘码是：13；
	- 空格键盘码是：32
	- Ctrl键盘码是：17

- e.ctrlKey;
判断是否按下了Ctrl键

### 获取DOM节点的样式，方法

- BOM上的方法：
getComputedStyle(DOM节点);
返回DOM节点上的所有的样式的集合，不管行内样式还是外联式样式，使用这个方法都能获取到。

	- 例如：
getComputedStyle(DOM节点).width------获取元素宽度
getComputedStyle(DOM节点).color-----获取颜色

### 获取元素实际显示的宽高

- 宽度：
DOM节点.offsetWidth---->返回的盒子实际的显示宽度  width+padding+content+border
- 高度：
DOM节点.offsetHeight------>返回的是盒子实际高度
height+padding+content+border

## BOM学习（第三天上午讲的）

### BOM是把浏览器当做一个对象

### BOM特点

- 浏览器就是一个window，window也叫顶级对象
- window绝大部分属性和方法，用的时候都不要调用window对象
- document.querySelector==window.document.querySelector;
结果为true，window可以省略
- 自己声明的所有全局函数和全局变量都是window顶级对象上的属性和方法。
- 在js代码里面，不使用var声明的变量，都是隐式全局变量，这个方式是不推荐的，因为如果不使用var声明，是不会变量提升的；所以使用一个不存在的变量一定要写关键字var

### BOM中的属性和方法

- 1.window.onload-------等静态资源全部加载完毕后，再让浏览器执行这个方法。
window.onload = function(){}--->这个通常叫入口函数

	- 什么是静态资源？
html文件、css文件、js文件、图片...都属于静态资源
	- 使用场景：一般情况下，看到HTML结构中引入了图片，就用这个方法，再把逻辑代码写入函数中，意思就是当html中的所有图片加载完毕后，我再执行逻辑代码
window.onload = function(){
	所有的逻辑代码
}

- 2.定时器（这是个方法）

	- 一次性定时器：
setTimeout(函数，延迟的毫秒数)；1s = 1000ms
第一个参数：等待一定时间后执行的函数
第二个参数：设置等待多久毫秒数再执行
例如：var timer = setTimeout(function(){
	console.log(3);
},3000);---------等待3秒后执行，在控制台输出3.只执行一次

		- 这个方法有一个返回值，返回值是用于清除定时器的

	- 永久性定时器：
setInterval(函数，时间间隔数毫秒)；
var timer = setInterval(function(){
	每等待3秒后执行函数
},3000);------但是第一次打印的时候也是要等待3秒后再每隔三秒执行一次函数

		- 返回值也是用于清除定时器的

	- 清除永久性定时器：
clearInterval(timer);
	- 清除一次性定时器：
clearTimeout(timer);

- 3.location这是个window上的一个属性

	- location下面有一个属性叫href，
location.href = "url地址"；
这个属性可以给浏览器重新制定跳转地址，页面会跳转到一个重新制定的新地址上
	- 用法：
location.href = "http://www.baidu.com";

- 4.localStorage(本地存储)
应用场景：把一些数据真实存在本地（本地：这个本地指的是浏览器）

	- 也是window上的一个属性，返回值是一个对象
使用这种方式存储数据的时候，即使这句代码被注释掉，他也是存到浏览器当中，真正的存到了浏览器当中了。
	- 存数据：
localStorage.setItem(参数一，参数二);
参数一：key----键（键是字符串类型）
参数二：值，是我们要存入的值，这个值只能是简单数据类型，不能存放复杂数据类型。
如果localStorage需要存放复杂数据类型，就要先将复杂数据转成JOSN类型的字符串。
	- 获取存储的数据：
localStorage.getItem("键key");-----括号中传入的类型是字符串类型，返回的值是字符串类型String，获取存储的数据的时候，这里的这个键名一定要和存放的时候的键名保持一致，如果不保持一致，将不会获取到自己想要的数据。
	- 删除本地存储的数据
localStorage.removeItem(键key);------括号中传入的类型是字符串类型
	- 清空全部存储的数据：一次性全部清空本地数据
localStorage.clear();-------括号中不需要传入任何参数
	- 如果获取一个不存在的键的名称的时候返回值是null。

- 5.JSON格式的字符串（字符串，有一定的格式）

	- 如果在一个字符串中有[]中括号{}花括号这个字符，那么这个字符串就是JSON格式的字符串，JSON就是有一定格式的字符串儿，那么这个格式来自于JS内部的数组和对象的属性。
	- 将复杂数据类型转成JSON格式的字符串：JSON.stringify(复杂数据类型);
返回值是一个JSON格式的字符串。
	- JSON字符串转复杂数据类型对象类型：
JSON.parse(JSON字符串);----小括号中传入一个JSON格式的字符串
这个方法的返回值是一个数组（对象类型），可以使用for()循环或者forEarch()来对这个数组进行遍历。

- 6.将所有的信息抽象为数据，
约定：一条数据就是一个对象，多条数据存放在数组中，按钮类不需要抽象为数据，因为按钮类都一样，所以需要抽象为数据。（极其重要）

	- 一条数据的格式：
{
     info: "快来收了这九款用上就停不下来的应用吧！！",
 }----键：值；---->键值对格式
抽象出来的数据，里面的key的值随便取。
	- 抽象出来的数据有什么用：
找后台工程师（java），要求统一的数据格式，如果java工程师做好了数据格式那么就按照java工程师的要求统一数据格式（谁出的格式快就按照谁的格式来做）。
	- 把抽象出来的多条数据（对象）放到数组当中：
var obj = [
	{
     info: "快来收了这九款用上就停不下来的应用吧！！",
 },
{
	info: "超级详细的云南大理自助游攻略 2",
},
{
    info: "外国最近很火的舞蹈，舒服简单自然，太棒了！3",
},
]-------->每条数据数据之间用英文逗号‘,’进行隔开。数组中其实放的是一个一个的对象
	- 如果要将对象类型存入本地（浏览器），分成两个步骤；

		- 1.要先将数转成JSON字符串---------->var str = JSON.stringify(obj);---返回值是String类型
		- 2.然后在将转成的字符串存放到浏览器中：
localStorage.setItem("键名",str);--------->注意，这个键名并不是随便设置的，键名是根据抽象出来的对象数组中的键名来设置的，这个键名要和抽象出来的对象数组中的键名保持一致。

*XMind: ZEN - Trial Version*