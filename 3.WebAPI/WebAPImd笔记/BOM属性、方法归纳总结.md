# JSDOM/BOM属性、方法归纳总结

## BOM方法

### 定时器

- 一次性定时器

	- 一次性定时器：
setTimeout(函数，延迟的毫秒数)；1s = 1000ms
第一个参数：等待一定时间后执行的函数
第二个参数：设置等待多久毫秒数再执行
例如：var timer = setTimeout(function(){
	console.log(3);
},3000);---------等待3秒后执行，在控制台输出3.只执行一次

- 永久性定时器

	- 永久性定时器：
setInterval(函数，时间间隔数毫秒)；
var timer = setInterval(function(){
	每等待3秒后执行函数
},3000);------但是第一次打印的时候也是要等待3秒后再每隔三秒执行一次函数

- 清除定时器方法：

	- 清除一次性定时器：
clearTimeout(timer);
	- 清除永久性定时器：
clearInterval(timer);

### 本地存储localStorage的方法
应用场景：把一些数据真实存在本地（本地：这个本地指的是浏览器）

- 通过localStorage方式将数据存放到本地（浏览器）中，有个特点：当存储完之后，即使删掉存储的代码，再次运行代码的时候，之前存放的数据还会依然存在浏览器中，数据不会因为代码的注销或者浏览器的关闭而消失，可以把这个过程理解为把数据真真实实存放到了U盘中，长期存在于本地，只要不手动删除数据就一直会存在本地（浏览器）中
- 数据的存储，获取、删除和清空

	- 存储

		- 存数据：
localStorage.setItem(参数一，参数二);
参数一：key----键（键是字符串类型）
参数二：值，是我们要存入的值，这个值只能是简单数据类型，不能存放复杂数据类型。
如果localStorage需要存放复杂数据类型，就要先将复杂数据转成JOSN类型的字符串。

	- 获取

		- 获取存储的数据：
localStorage.getItem("键key");-----括号中传入的类型是字符串类型，返回的值是字符串类型String，获取存储的数据的时候，这里的这个键名一定要和存放的时候的键名保持一致，如果不保持一致，将不会获取到自己想要的数据。

	- 删除

		- 删除本地存储的数据
localStorage.removeItem(键key);------括号中传入的类型是字符串类型

	- 清空

		- 清空全部存储的数据：一次性全部清空本地数据
localStorage.clear();-------括号中不需要传入任何参数

### JSON格式字符串
（首先它是字符串儿类型，其次是有一定格式的字符串儿）

- 那么什么样的字符串属于JSON格式的字符串儿？
如果在一个字符串中有[]中括号{}花括号这个字符，那么这个字符串就是JSON格式的字符串
- 数据本地化的原因：
1.浏览器一刷新，数据就没了。
2.这是一个操作过程，用户留下的数据，真实的将数据存了起来。
3.本地存储，为了演示把数据真实存下来。
- 复杂数据类型与JSON类型之间的互转

	- 复杂数据类型转JSON

		- JSON.stringify(复杂数据类型);
返回值是一个JSON格式的字符串

	- JSON转复杂数据类型

		- JSON.parse(JSON字符串);---->小括号中传入一个JSON格式的字符串
这个方法的返回值是一个数组（对象类型），可以使用for()循环或者forEarch()来对这个数组进行遍历。

### 获取DOM节点上的所有的样式，这是个DOM方法

- getComputedStyle(DOM节点);
返回DOM节点上的所有的样式的集合，不管行内样式还是外联式样式，使用这个方法都能获取到。

	- 例如：
getComputedStyle(DOM节点).width------>获取元素宽度
getComputedStyle(DOM节点).color----->获取颜色

## JS方法（DOM方法）

### 获取对象节点的方法

- document.getElementById();--->括号中传入的参数是只能是标签的ID值，返回值是一个节点对象，返回值的类型是一个对象类型，只要是对象类型，这个对虾干下面就有一定的属性和方法。
- getElemtntsByTagName('标签名');   ---------  获取多个同名标签   
- getElemtntsByClassName('类名');------可以获取多个相同类名的标签
- document.querySelector('css选择器');----括号中的css选择器也是以字符串的形式传入，返回的是一个节点对象，并不是多个节点对象，可以是类选择器（不要忘记写英文的点儿”.“），可以使id选择器(不要忘记写井号“#”)，也可以使结构选择器，只要是CSS的选择器都可以
- document.querySelectorAll('css选择器');  -----返回的是一个伪数组。
可以用for循环进行遍历；
但是这个方法可以使用forEarch()循环遍历，虽然这个伪数组有forEarch()方法，但它还是一个伪数组，并不是一个真数组。

### 获取自定义属性的方法

- DOM节点对象.getAttribute(自定义属性名);-----获取自定义的属性名或者标准属性名，返回值就是需要查的属性值，一般情况下是获取自定义的属性名的值，返回值是一个字符串类型（String）
使用：console.log(btn.getAttribute("data-md"));
- 设置自定义的属性值：
DOM节点.setAttribute('自定义属性名','属性值');--->两个参数都是字符串类型
使用：
btn.setAttribute('data-md', 'jdkkfdj');
- 删除自定义属性：
DOM节点.removeAttribute('自定义属性');---->括号中写的是要删除的自定义的属性名儿
使用：
btn.removeAttribute('data-md');

### 这里有个特殊的属性：body是document下面的一个属性，body在页面中只有一个。
就是获取body对象------->document.body

### 各种事件

- 鼠标事件：

	- onclick：单击（鼠标左键单击）事件；
	- mousedown：鼠标按下事件
	- mousemove：鼠标移动事件
	- mouseup：鼠标弹起事件
	- mouseover：鼠标移入事件
	- mouseout：鼠标移出事件
	- mouseenter：鼠标移入事件
	- mouseleave：鼠标移出事件

- 内容改动事件onchange事件

	- 当表单标签(input select下拉列表 textarea文本域。。。)中的内容改变的时候，就会触发该事件

- input框事件：

	- onfocus：获取光标焦点事件
	- onblur：失去光标焦点事件

- 键盘事件

	- 键盘按下事件

		- keydown键盘按下事件，
只要按下键盘上的键，就能触发事件

	- 键盘弹起事件

		- keyup键盘弹起事件
只要是键盘弹起，就能触发事件

- 动画/过渡执行完毕后触发事件

	- transitionend--->过渡完毕后触发的事件
	- animationend--->动画完毕后触发的事件

- 滚动事件

	- onscroll
（只要盒子出现滚动条，就可以注册这个滚动事件）overflow：auto；（这个是CSS样式属性给节点添加滚动条）

		- 对应的属性scrollTop是卷入的高度，返回值是number类型
这个属性的应用场景是：判断当盒子卷入多高时，来实现什么场景。

### 注册事件的方法

- 第一种方法：DOM对象节点.事件名儿 = function(){}
- 第二种方法：
DOM节点对象.addEventListener('click',function(){
	点击之后执行的函数；
},第三个参数（默认值是false，默认在冒泡阶段执行）)；----这个方式多次注册事件不会被覆盖；
第一个参数是：事件名   click（单击事件）
第二个参数是：点击之后执行的函数。
第三个参数是：事件执行阶段，默认值是false（默认在冒泡阶段执行），若将值改为true（将事件改为在捕获阶段执行）如果父节点注册了和目标节点同样的事件，那么父节点的事件也会执行。

### 管理DOM节点类名的方法

- classList()，这个方法返回值是一个对象，classList()方法下面有各种的属性和方法，以后操作类名就要使用classList()这个方法，尽量不要使用className属性来操作节点的类名。这个方法下面有三个常用的方法

	- 添加类名
classList.add();------->括号中填入的类名类型是字符串类型
使用这个方法给DOM节点对象添加类名的时候，如果第二次与第一添加的类名是一样的，那么这个方法只会添加一次类名，并不会同样的类名进行重复进行添加。
	- 删除类名：------->括号中填入的类名类型是字符串类型
classList.remove();
	- 添加/删除类名：------->括号中填入的类名类型是字符串类型
classList.toggle();-------->这个方法在一定情况下还是比较友好的。
使用toggle()方法进行添加类名的时候，这个方法会判断当前的这个DOM节点是否存在要添加的类名，如果已经存在了要添加的类名，那么这个方法会将已经存在的类名进行删除，如果经这个方法判断DOM节点中没有将要添加的类名，那么这个方法就会将类名添加到DOM节点中，简单来讲就是：如果有类名就删除，如果没有类名就添加。

### 阻止冒泡的方法

- DOM节点对象.addEventListener('click',function(e){
//传入一个形参e，e被称为事件对象
e.stopPropagation();--->阻止冒泡的方法
}

### 对象事件下的方法

- 阻止默认行为方法（注意：这里是个方法）  preventDefault()
返回值是undefined，为嘛是undefined，我也不知道

	- document.oncontextmenu = function(e) {
    e.preventDefault();----prevent(阻止)Default(违约)
  }   给document对象阻止默认行为，这个时候再点击右键，右键就不会出现点击框了

### 事件解绑，这是一个方法

- 解绑事件其实就是将事件给注销掉
- DOM节点对象.removeEventListener('参数1',参数2);
参数1：需要注销的时间类型，要记得带上双/单引号
参数2：需要注销的函数名

### 给父节点最后面添加一个子节点的方法

- var li = document.createElement('li');--------这种方法返回的是一个标签字符串（<li></li>）但是这种方式只是在js中创建了一个子标签，并没有自动加到页面结构上。
- 要想将创建好的节点添加到父节点中还需要这个方法：
父节点对象.addChild(li);------>这个方法是将新创建的子节点作为最后一个元素在父元素的最后出入的。

### 在父节点的子元素中任意位置添加一个元素的方法

-  父节点.insertBefore(新的子节点,旧的子节点)
var second = document.querySelector('.dasha');-----以获取类名的形式获取子对象节点
ul.insertBefore(li, second);
第一个参数是：需要新添加的DOM节点
第二个参数是：需要在哪个子节点前面进行添加（第二个参数是子节点对象）

### 删除父节点中的子节点的方法

- 父节点.removeChild(要删除的子节点);
括号中直接写入子节点对象。不要加引号

## JS属性（DOM属性）

### DOM节点.style---->返回值是一个对象，是对象，下面就有各种属性和方法，一般css的各种样式都在style.设置。
style是对象下的一个属性
只要是涉及到DOM节点的样式属性，都在对象的style属性下面。使用这个方法只能获取行内样式表中的样式，外联式和内嵌式样式这个方法是获取不到的。

- 我们也可以通过这个属性进行对节点对象的样式进行设置，例如：
btn.style.height = '200px';-->后面的值一定是个字符串类型

### DOM节点.value---->返回值是一个字符串

- 注意：这个方法只能是获取有光标输入的字符串内容
- 也可以通过这个属性对节点内容进行设置。
DOM节点.value = '长沙的满哥';

### DOM节点.className----->返回值是一个字符串

- 可以获取
console.log(it.className);
- 可以设置
it.className = 'iiiiiiii';
注意：在设置节点对象的类名的时候，会将节点对象原有的类名进行覆盖，这个属性其实并不是很友好。

### 给DOM节点设置自定义属性时

- 自定义属性的命名方式：data-名字（名字前面必须要加上data-）
例如：这里的 data-md="id"就是自定义属性
<button id="btn" data-md="id">按钮</button>
- 获取自定义属性
DOM节点.dataset----->返回值是一个对象
DOM节点.dataset.md---->就能将自定的属性值获取到，
解释：这里的md就是在标签中写的data-md，data-后面的名字随便取，获取的时候只要保持这两个值是一样，就能获取到自定义的属性值。

### 关键字：this

- 函数内部有一个关键字：this；原则：当前你点击的是哪个DOM节点，this就是指谁。---this也可以理解为函数中的一个指针，指向当前获取到的DOM节点。
- 在循环里面获取当前点击对象就使用this来表示当前对象

### 开关属性checked

- DOM节点.checked---->这个属性只有两个值，一个是true一个是false；
DOM节点.checked = true/false;

### 按钮的禁用属性

- DOM节点.disabled
- 如果是在html标签中使用disabled则这样使用：
<button disabled=true></button>
disabled只有两个值，一个true一个false，当为true时则表示禁用打开，按钮就不能进行点击了，当为false时表示禁用关闭，按钮可以点击，默认值是false。

### 对象事件中的属性

- e：--->event，通常表示对象事件
- client属性  返回值是number类型

	- e.clientX
	- e.clientY

- page属性   返回值是number类型

	- e.pageX
	- e.pageY

- target属性   返回值是一个节点对象，是DOM节点对象就有属性和方法

	- e.target

		- 鼠标点击的是谁就是谁

- currentTarget属性   返回值是object类型

	- e.currentTarget

		- 事件注册给谁就是谁

- e.keyCode;----->可以知道点的是键盘上的内个键盘，每一个按键对应一个数值，这个数值我们叫做键盘码
返回值是一个number类型，返回的是一个键盘码

	- 回车的键盘码是：13
空格的键盘码是32
Ctrl键的键盘码是17

- e.ctrlKey;
判断是否按下了Ctrl键

### 获取元素位置的属性

- DOM节点.offsetLeft------->返回的值是left+marginleft的和，
- DOM节点.offsetTop------->返回的值是top+margintop的和
- DOM节点.offsetWidth--->返回值是内容宽度+padding+border的总和
- DOM节点.offsetHeight--->返回值是内容高度+padding+border的总和

### 事件委托中学到的属性

- DOM节点.innerHTML属性
这个属性可以获取节点对象的HTML结构，返回值是String类型

	- 也可以设置这个属性的值：
DOM节点.innerHTML = '<li>长河</li>'；
不过使用这种方法添加标签会将父标签下的所有子标签进行覆盖。

- DOM节点.nodeName;属性
返回的是一个大写的标签名，返回值类型是
String类型

	- e.target.nodeName;--->点击的是谁就返回谁的大写标签名

### 获取父节点的内容属性

- DOM节点.innerText；
返回值是字符串，返回的是父字符串下的文本内容
这个属性不具备解析HTML节点的功能
- 也可以通过这个属性设置父节点下的内容：
DOM节点.innerText = 'aaaaa';
不过通过这个方法设置父节点下的内容，就将父节点下的之前存在的内容进行了覆盖（也可以理解成替换）；通过这种方式设置父节点的内容不是特别友好

### 通过父节点获取所有的子节点，这是一个属性

- 这是一个属性，不是一个方法：
父节点.children;------返回值是一个所有亲生子节点的集合（伪数组）

### 通过子节点获取父节点   也是一个属性

- 子节点.parentNode;-----返回值是一个父亲节点object对象类型（绝对上下级的父亲节点）

### 通过子节点获取子节点的上一个和下一个兄弟节点

- 子节点的下一个兄弟节点：
节点对象.nextElementSibling
- 子节点的上一个兄弟节点：
节点对象.previousElementSibling

### 子主题 15

## BOM属性（祖宗是window）

### onlode属性：这个属性前面要加上window.
这个属性的作用是，当HTML页面中的图片、css文件、js文件这些静态资源都加载完毕后，我再执行函数中的逻辑代码，所有的逻辑代码都可以写到这个匿名函数中。
window.onlode = function(){
	逻辑代码
}

### location属性：

- 主要记住location下面有一个href属性：这个属性可以指定页面跳转路径，
location.href = "http://www.baidu.com"；---->URL地址

### 获取实际显示的宽和高

- 获取宽

	- DOM节点.offsetWidth---->返回的盒子实际的显示宽度  
返回值的宽度 = width+padding+content+border

- 获取高

	- DOM节点.offsetHeight------>返回的是盒子实际高度
返回值的高度 = height+padding+content+border

*XMind: ZEN - Trial Version*