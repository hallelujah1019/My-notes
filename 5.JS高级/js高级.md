# JS高级

## 两大编程思想

### 1.面向过程

* 面向过程:POP(Process-oriented programming )
* 面向过程就是分析出解决问题所需要的步骤,然后用函数把这些步骤一步一步实现,使用的时候再一个一个的一次调用就可以了

**面向过程: 过程就是步骤,   小项目**

### 2.面向对象

* 面向对象:OOP(Object Oriented Programming)
* 面向对象是把事物分解成为一个个对象,然后由对象之间分工与合作
* 大象,冰箱:都看成对象功能

**面向对象: 多人合作大项目**

#### 面向过程和面向对象的区别

**面向过程: 过程就是步骤,   小项目**

**面向对象: 多人合作大项目**

#### 面向对象三大特征

* 封装性:可以封装(封装函数)
* 继承性:可以继承
* 多态性:功能/用途比较多

#### 面向对象和过程优缺点

* 面向过程:
  * 优点:性能比面向对象高(目的性强),步骤练习紧密
  * 缺点:不好维护,不易多次使用及扩展
* 面向对象:
  * 优点:易维护,可复用,可扩展,灵活性高
  * 缺点:性能没有面向过程高

**总结:简单程序面向过程,复杂程序用面向对象**

### ES6中的类和对象

* ES5: 没有类,ES6:类  版本不同

* ES:ECMAscript
* js包含: ES DOM BOM

#### 类: 泛指一类  **抽象**    

* 类模拟抽象的,泛指的,对象是具体的

* 面向对象模拟现实世界,更贴近实际生活,生活照分为抽象事物和具体事物

  比如:手机[两层含义:具体哪个手机,,,和笼统的概念的手机]

  1. 抽取,把对象的属性和行为封装成一个类
  2. 对类进行实例化,获取类的对象

  例如:人有身高,体重等,但是具体的某个人也有这个属性

```js
//语法:创建类
class Star{}
//实例化对象
var obj=new Star();

// 对象 instanceof 构造函数
// obj是object类型的数据
// console.log(obj instanceof Object);

var wahaha=new Star();
console.log(wahaha)
```



#### 对象: 具体  

##### 类中的**具体**的某个实例  [ 属性和方法的集合体]

##### 对象是由属性和方法组成的

现实生活中:万物皆对象,对象是一个具体的事物,看得见摸得着的实物.例如,一本书,一辆汽车/一个人可以是'对象

在JavaScript中,对象是一组 无序的相关属性和方法的集合,所有的事物都是对象,例如 字符串/数组/数值/函数等



```js
//属性:指对象有什么? [访问] [语法:对象.属性]
Star.uname
Star.age
//属性:事物的特征,在对象中用属性来表示(常用名词)
```

```js
//方法:指对象做什么? [执行] [语法:对象.方法()]
Star.say()
Star.tiao()
//方法:事物的行为,在对象中用方法来表示(常用动词)
```

#### 面向对象的思维特点:

1.抽取(抽象)对象共有的属性和方法 组织(封装)成一个类(模板)

2.对类进行实例化,获取类的对象

## 类class

在ES6中新增加了类的概念,可以使用class关键字声明一个类,之后以这个类来实例化对象..[构造函数实例化对象]

* 类抽象了对象的公共部分,它泛指某一大类(class)

### 创建类

* 语法:class 类名{属性和方法} 【类就是构造函数的语法】
* 注意:类名首字母必须是大写
* 类要抽取公共属性方法,定义一个类

```js
语法: class 类名{
   //属性和方法
}
//类名首字母必须是大写

 // 创建类
  class Star {}
  //   // 实例化对象
  //   //   var obj = new Star();
  //   // 对象 instanceof 构造函数
  //   // obj是object类型的数据
  // console.log(obj instanceof Object);  //输出 true

  var wahaha = new Star();
  console.log(wahaha); //输出 wahaha {}
```

### 类constructor  构造函数

```js
	class Star {
				// 属性
				constructor (uname, age) {
					this.uname = uname;
					this.age = age;
				// new的时候就会执行构造函数
				}
        //属性:放到constructor构造函数里面
```

##### **构造函数就是为了添加属性的**

* 属性:放到constructor,构造函数里面
* 注意:类里面的方法不带function,直接写即可
* 类里面要有属性方法,属性方法要是想放到类里面,我们用constructor构造器
* 构造函数作用:接收参数,返回实例对象,new的时候主动执行,主要放一些公共的属性 
* constructor()方法是类的构造函数(默认方法),用于传递参数,返回实例对象,通过new命令生成对象实例时,自动调用该方法
* 注意:每个类里面一定有构造函数,如果没有显示定义,类内部会自动给我们创建一个constructor()

##### 构造函数里面,this代表当前实例化对象,new谁 就代表谁

##### 对象里面,this代表当前调用者

### 类添加方法

语法:注意方法和方法之间不能加任何符合

```js
class Star {
     constructor (){}

     sing(){}

     tiao(){}
}

class 类名{ constructor(){}  方法名(){}  }
注意:类中定义属性,调用方法都得用this
```

##### 注意:类中定义属性,调用方法都得用this

方法之间不能加逗号分隔,同时方法不需要添加function关键字

**总结:类有对象的公共属性和方法,用class创建,class里面包含constructor和方法, 我们把公共属性放到constructor里面,把公共方法直接往后写即可,但是主要不要加任何符号**

### 类的继承

##### extends 

```js
语法:
class Father {}
class Son extends Father {}
注意:是子类继承父类
```

##### super关键字

* 我们应用的过程中会遇到父类子类都有的属性,此时,没必要再写一次,可以直接调用父类的方法就可以了
* super关键字用于访问和调用对象父类上的函数,可以调用父类的构造函数,也可以调用父类的普通函数
* 当子类没有constructor的时候 可以随意用父类的,但是如果子类也含有的话,constructor会返回实例,this的指向不用,不可以在直接使用父类的东西

### 放到对象里面:元素.insertAdjacentHTML('beforeend',添加的标签名)

双标签选择 元素.innerHTML=' '; 对象清空

###### 调用父类构造函数

```js
案例:
  class Father {
      constructor(uname, age) {
        this.uname = uname;
        this.age = age;
      }
      qian() {
        console.log('赚他一个亿');
      }
    }
    class Son extends Father {
      //   因为this指向不同
      constructor(uname, age, score) {
        // super:可以调用父类的构造函数和方法
        super(uname, age);
      }
    }

注意:子类在构造函数中使用super,必须放到this前面(必须先调用父类的构造方法,在使用子类构造方法)
```

###### 调用父类普通函数

```js
class Father {
      constructor(uname, age) {
        this.uname = uname;
        this.age = age;
      }
      qian() {
        console.log('赚他一个亿');
      }
    }
    class Son extends Father {
      //   因为this指向不同
      constructor(uname, age, score) {
        // super:可以调用父类的构造函数和方法
        super(uname, age);
        this.score = score;
      }
      qian() {
        super.qian();
        console.log('赚他两个亿');
      }
    }
注意:如果子类也有相同的方法,优先指向子类,就近原则
```

**总结:super调用父类的属性和方法,那么查找属性和方法的原则就近原则**

```js
    class Father {
      constructor(uname, age) {
        this.uname = uname;
        this.age = age;
      }
      qian() {
        console.log('赚他一个亿');
      }
    }
    class Son extends Father {
      //   因为this指向不同
   constructor(uname, age, score) {
     // super:可以调用父类的构造函数和方法
        super(uname, age);
        this.score = score;
      }
      qian() {
        super.qian();
        console.log('赚他两个亿');
      }
    }
    var obj = new Son('李寻欢', 22, 98);
    console.log(obj);
    obj.qian();
```

### 三个注意点:

##### 1.在ES6中类没有变量提升,所以必须先定义类,才能通过类再实例化对象

##### 2.在类里面调用属性或者方法一定要用this调

##### 3.this指向:

###### 	构造函数里面的this指向当前实例化对象

###### 	方法里面的this指向当前调用者

```js
  // 把标签也可以当成属性
    // 写一个类,构造函数接收一个参数,通过这个参数获取一个元素,让这个元素当做属性
    class Anniu {
      // 构造函数里面的this是实例对象
constructor(val) {
this.btn = document.querySelector(val);
          
        // 添加事件
        // 注意:给元素添加处理程序,这个函数不准带括号
        this.btn.onclick = this.cli;
      }
      cli() {
     //   this不一样:方法里面的this,调用者
        console.log(123);
      }
    }
    // 这个按钮给这个obj当属性
    var obj = new Anniu('#btn1');
    console.log(obj);

    // 构造函数里面的this   指向的是 new出来的实例对象
    // 方法(普通函数): this指向调用者(谁调用这个方法,this就指向谁)

```

## tab栏案例

this执行==》构造函数，new的对象，方法：this,调用者

**面向对象版tab 栏切换**

```js
1.tab栏切换的主要思路是：

2.点击当前li 添加liactive 类其余li移除类

3.根据当前li 的索引号当前section 添加类，其余section 删除类

4.这里可以把添加放入切换函数里面

5.新增一个清除类函数，专门移除其余li和section 类

6.注意里面this 指向问题
```

**面向对象版tab 栏切换添加功能**

```
1.点击+ 可以实现添加新的选项卡和内容

2.第一步: 创建新的选项卡li 和新的内容section

3.第二步: 把创建的两个元素追加到对应的父元素中.

4.以前的做法:  动态创建元素createElement, 但是元素里面内容较多, 需要innerHTML赋值,在appendChild追加到父元素里面.

5.现在高级做法:   利用insertAdjacentHTML() 可以直接把字符串格式元素添加到父元素中

6.appendChild不支持追加字符串的子元素, insertAdjacentHTML支持追加字符串的元素
7.insertAdjacentHTML(追加的位置,‘要追加的字符串元素’)  

8.追加的位置有: beforeend插入元素内部的最后一个子节点之后

9.该方法地址:  https://developer.mozilla.org/zh-CN/docs/Web/API/Element/insertAdjacentHTML
```



Tab栏案例  v1  实现切换效果

```js
	var that;
// 定义一个类,切换tab栏
    class Tab {
      // 构造函数 要操作的tab栏
		constructor(id) {
    //构造函数:this指向实例对象,that也是实例对象
        that = this;
    //根据id 获取这个tab栏
this.main = document.querySelector(id);
        // 获取li 
this.lis = this.main.querySelectorAll('li');
    //获取section  
this.sections = this.main.querySelectorAll('section');
   
    //调用方法init
        this.init();
      }
      // 专门创建一个方法,只用来添加事件
      //init():这个用来添加事件
      init() {
          //遍历li
          for (var i = 0; i < this.lis.length; i++) {
              //直接在DOM树上添加
            this.lis[i].index = i;
              //   给li创建点击事件 调用切换效果
            this.lis[i].onclick = this.toggleTab;
          }

        }
        // 添加一个方法,这个方法用来做切换tab栏效果
        //toggleTab:这个方法用来切换效果
      toggleTab() {
          //this:当前事件源
        this.className = 'liactive';
          //给section添加类名
          //给对应下标的section
        that.sections[this.index].className = 'conactive';
      }
    }

    new Tab('#tab');
```

tab栏案例. v2 排他思想,点击谁,其他值为空

```js
   //   切换tab栏效果
      toggleTab() {
        // this：因为这个方法li调用，this代表的是li元素，而不是实例对象，所以我们用that
        // 清除className
        that.clearClass();
        // li，sections
        // this：当前事件源
        this.className = 'liactive';
        // 给section添加类名
        // 给对应下标的section
        that.sections[this.index].className = 'conactive';
      }

      clearClass() {
        for (var i = 0; i < this.lis.length; i++) {
          // this：that调用的这个方法，that是实例对象所以这个方法里面的this也是实例对象
          this.lis[i].className = '';
          this.sections[i].className = '';

        }
      }
```

tab栏案例 v3 点击添加事件+最终效果

```js
    // 给tab栏创建类
    // 获取li 给li创建点击事件
    var that;
    class Tab {
      // 构造函数
      // 对象.属性

      constructor(id) {
        that = this;
        this.main = document.querySelector(id);
        //   获取li
        // this.lis = this.main.querySelectorAll('li');
        // this.sections = this.main.querySelectorAll('section');

        this.tabadd = this.main.querySelector('.tabadd');
        this.tabscon = this.main.querySelector('.tabscon');
        this.ul = this.main.querySelector('ul');
        this.init();
      }

      // 专门创建一个方法,注册事件用
      init() {
          //   给li创建点击事件
          this.lis = this.main.querySelectorAll('li');
          this.sections = this.main.querySelectorAll('section');

          for (var i = 0; i < this.lis.length; i++) {
            this.lis[i].index = i;
            this.lis[i].onclick = this.toggleTab;
          }
          // 给tabadd添加点击事件
          this.tabadd.onclick = this.tabAdd;

        }
        //   切换tab栏效果
      toggleTab() {
        // this：因为这个方法li调用，this代表的是li元素，而不是实例对象，所以我们用that
        // 清除className
        that.clearClass();
        // li，sections
        // this：当前事件源
        this.className = 'liactive';
        // 给section添加类名
        // 给对应下标的section
        that.sections[this.index].className = 'conactive';
      }
      clearClass() {
          this.lis = this.main.querySelectorAll('li');
          this.sections = this.main.querySelectorAll('section');
          for (var i = 0; i < this.lis.length; i++) {
            // this：that调用的这个方法，that是实例对象所以这个方法里面的this也是实例对象
            this.lis[i].className = '';
            this.sections[i].className = '';
          }
        }
        //   点击添加方法
      tabAdd() {
        // 清除类
        that.clearClass();

        var li = '<li class="liactive"><span>标题</span><span class="iconfont icon-guanbi"></span ></li>'
        that.ul.insertAdjacentHTML('beforeend', li);

        var section = '<section class="conactive">内容</section>';
        that.tabscon.insertAdjacentHTML('beforeend', section);

        that.init();
      }
    }
    new Tab('#tab');
```

### 创建对象的三种方式

* 对象字面量
* new Object() [构造函数]
* 自定义构造函数

```js
 1.通过字面量创建对象
    var obj = {
        name: '张三丰',
        age: 22,
        sex: '男',
        taiji: function() {
          console.log('太极哈哈哈');;
       }
    }
    //   // 属性和方法都可以打印,不同的时候方法可以调用
    console.log(obj.taiji);
```

```js
2.通过构造函数创建对象 Object
    var obj = new Object()
      // console.log(obj);
    obj.uname = '张三丰';
    obj.age = 24;
    obj.chuohao = '二狗子';
    obj.taiji = function() {
      alert('打太极');
    }
    console.log(obj);
    // **给元素添加事件,就是给这个元素添加方法
    var btn = document.querySelector('input');
    console.dir(btn);
    obj.taiji = function() {
      alert('打太极');
    }
    btn.onclick = function() {
      alert('打太极');
    }
```

```js
3.自定义构造函数
    // 构造函数名 要首字母大写
    function Fn(uname, age) {
      this.uname = uname;
      this.age = age;
    }
    var obj = new Fn('张三丰', 22);
    console.log(obj);
    var obj1 = new Fn('李寻欢', 23)
    console.log(obj1);

    // function Dog() {};
    // function Maomi() {};
```

### 构造函数和原型

```
构造函数是一种特殊的函数,主要用来初始化对象,即为对象成员变量赋初始值,它总与new一起使用.我们可以把对象中一些公共的属性和方法抽取出来,然后封装到这个函数里面
function Fn() {}
```

##### 在js中,使用构造函数时要注意以下两点:

* 构造函数用于创建某一类对象,其首字母要大写
* 构造函数要和new一起使用才有意义

##### 区分普通函数和构造函数

```js
    // 区分普通函数和构造函数
    function wahaha() {}

    //普通函数
    wahaha();

    //构造函数 (与new在一起才有意义)
    var obj = new wahaha()
  </script>
```

##### new在执行时会做四件事情

1.在内存创建一个新的空对象   (开空间)

2.让this指向这个新的对象  (this指向)

# 3.执行构造函数里面的代码,给这新对象添加属性和方法 (执行代码)

4.返回这个新对象(所以构造函数里面不需要return)    (返回这个对象)

什么是成员: 构成函数对象中的属性和方法

##### 区分静态成员和实例成员

javaScript的构造函数中可以添加一些成员.,可以在构造函数本身上添加,也可以在构造函数内容的this 上添加,通过这两种方式添加成员,就分别称为静态成员和实例成员

```js
静态成员:在构造函数身上的成员叫静态成员,静态成员只能由构造函数访问
实例成员:在构造函数内部的成员叫实例成员,实例成员只能由实例对象访问

// js:看谁都是对象
    function Person(uname, age) {
      this.uname = uname;
      this.age = age;

      this.chang = function() {
        console.log('唱歌');
      }
    }
    var obj = new Person('李寻欢', 22);
    console.log(obj.uname);

    // 万物皆对象,构造函数也可以是对象
    Person.sex = '男';
    console.log(Person.sex);

```

##### 构造函数小问题:

```
当实例化对象的时候,属性好理解,属性名属性值,那么方法是函数,函数是复杂数据类型
那么保存的时候是保存地址,又指向函数,而每创建一个对象,都会有一个函数,每个函数都得开辟一个内存空间,此时浪费了内存了,那么如何节省内存呢,我们需要用到原型方法放到构造函数里面,如果多次实例化,会浪费内存
```

```js
// 构造函数小问题:浪费内存
    function Star(uname, age) {
      this.uname = uname;
      this.age = age;
      this.sing = function() {
        console.log('唱歌');
      }
      this.tiao = function() {
        console.log('跳舞');
      }
    }
    var obj = new Star('李寻欢', 22);
    console.log(obj);
    obj.sing();
    obj.tiao();
```

#### 构造函数原型prototype,指向构造函数

* 什么是原型对象:就是一个属性,是构造函数的属性,这个属性是一个对象,我们也称呼prototype为原型对象
* 每一个构造函数都有一个原型对象:prototype
* 作用:为了共享方法,从而达到节省内存
* **注意:每一个构造函数都有prototype属性**

```
构造函数通过原型分配的函数是所有对象所共享的
JavaScript规定,每一个构造函数都有一个
prototype属性,指向另一个对象.注意这个prototype就是一个对象,这个对象的所有属性和方法,都会被构造函数所拥有.我们可以把那些不变的方法,直接定义在prototype上,这样所有对象的实例就可以共享这个方法.
```

```js
 function Star(uname, age) {
      this.uname = uname;
      this.age = age;
    }
    Star.prototype.sing = function() {
      console.log('唱歌');
    }
    Star.prototype.tiao = function() {
      console.log('跳舞');
    }
    var obj = new Star('成龙', 23);
    // console.log(Star.prototype);
    console.log(obj)
      // console.log(obj.__proto__ == Star.prototype);//输出true
    obj.sing();
    obj.tiao();
```

**总结:所有的公共属性写到构造函数里面,所有的公共方法写到原型对象里面**

疑问:为何创建一个对象,都可以自动的跑到原型对象上找方法??

* 因为每一个对象都有一个属性,对象原型,执行原型对象

为什么实例对象可以用原型对象??? 因为有对象原型

#### 对象原型:____proto____,指向原型对象

**主要作用:指向原型对象prototype**

构造函数和原型对象都会有一个属性____proto____指向构造函数的prototype原型对象,之所以我们对象可以使用构造函数prototype 原型对象的属性和方法,就是因为对象有____proto____原型的存在

* 注意对象原型 也是一个属性  是一个非标准属性,不可以拿来赋值或者设置[只读属性]  

```
1.____proto____对象原型和原型对象prototype是等价的
2.____proto____对象原型的意义在于为对象的查找机制提供一个方向,或者说一条路线,但是他是一个非标准属性,因此实际开发中,不可以使用这个属性,他只是内部指向原型对象的prototype
```



```js
每一个构造函数都有一个原型对象(prototype)
每一个实例对象都有一个对象原型(__proto__)

console.log(obj.__proto__ == Star.prototype);//输出true
```

##### 每一个构造函数都有一个原型对象(prototype)

##### 每一个实例对象都有一个对象原型(____proto____)

统一称呼:____proto____原型

​				prototype成为原型对象

#### constructor 构造函数,指回构造函数本身

##### constructor: 指回构造函数本身

**记录是哪个构造函数创建出来的**

```
原型(__proto__)和构造函数(prototype)原型对象里面都有一个属性constructor属性,constructor我们成为构造函数,因为它指回构造函数本身.constructor主要用于记录该对象引用于哪个构造函数,他可以让原型对象重新指向原来的构造函数.一般情况下,对象的方法都在构造函数的原型对象中设置.如果有多个对象的方法,我们可以给原型对象采取对象形式赋值,但是这样就会覆盖构造函数原型对象原来的内容,这样修改后的原型对象constructor就不在指向当前构造函数了.此时,我们可以在修改后的原型对象中,添加一个constructor指向原来的构造函数.
```

**原型对象:prototype,方法**

**对象原型:proto,指向原型对象**

**构造函数: constructor:指回构造函数**

## 构造函数 实例 原型对象三者关系

思考:如果传入一个对象给原型对象添加方法呢?

```
Star.prototype={
	sing:function(){};
	dance:function(){}
}
此时会覆盖原先prototype中的内容,传入一个新的对象,那么此时就不知道构造函数是哪个了,所以我们要指回构造函数:constructor:构造函数
```

上午回顾：

​		构造函数，原型对象，对象原型

​		创建对象：字g面量【{}】，构造函数Object，自定义构造函数

​		静态成员，实例成员

​		把属性都放到构造函数中

​		原型对象：prototype，构造函数的一个属性，把放到都放到原型对象

​		实例对象：对象原型____proto____，指向原型对象

​		构造函数：constructor，指回构造函数

### 原型链

* 作用:提供一个成员的查找机制,或者查找规则

##### javaScript 的成员查找机制(规则)

```
当访问一个对象的属性(包括方法)时,首先查找这个对象自身有没有该属性.
如果没有就查找它的原型(也就是__proto__指向的prototype原型对象).
如果还没有就查找原型对象的原型(object的原型对象)
以此类推一直找到object为止(null)
__proto__对象原型的意义就在于为对象成员查找机制提供一个方向,或者说一条路线.
console.log(Star.prototype.__proto__.__proto__);
console.log(Object.prototype)
```

### 扩展内置对象

* 可以通过原型对象,对原来的内置对象进行扩展自定义的方法.比如数组增加自定义求偶数和的功能

```js
扩展数组求最大值的方法
    // 扩展数组求和的方法
    var arr = [3, 1, 4, 2]
    Array.prototype.sum = function() {
      var sum = 0;
      for (var i = 0; i < this.length; i++) {
        sum = sum + this[i];
      }
      return sum;
    }
    console.log(arr.sum());
```

### 继承(组合继承=构造函数+原型对象)

* ES6之前并没有给我们提供extends 继承.我们可以通过构造函数+原型对象模拟实现继承,被称为组合继承
* call()
  * 调用这个函数,并且修改函数运行时的this指向

```js
    function Father(uname, age) {
      this.uname = uname;
      this.age = age
    }
    Father.prototype.say = function() {
      console.log('唱歌');

    }

    function Son(uname, age, score) {
        //father.call(this,参数1,参数2);call把父类的this指向子类
        //thisArg:当前调用函数this的指向对象
      Father.call(this, uname, age);
      this.score = score;
    }

    var obj = new Son('李寻欢', 22, 98);

    console.log(obj);
```

**利用构造函数实现子类的继承**

### 属性的继承

```js
  function Father(uname, age) {
      this.uname = uname;
      this.age = age
    }
    Father.prototype.say = function() {
      console.log('唱歌');

    }

    function Son(uname, age, score) {
      Father.call(this, uname, age);
      this.score = score;
    }

    var obj = new Son('李寻欢', 22, 98);

    console.log(obj);
```

### 方法的继承(原型对象:子类的原型对象=父类的实例对象)

* **实现方法把父类的实例对象保存给子类的原型对象**

```
一般情况下,对象的方法都在构造函数的原型对象中设置,通过构造函数无法继承父类方法.核心原理:
1.将子类所共享的方法提取出来,让子类的prototype原型对象=new 父亲()
2.本质:子类原型对象等于是实例化父亲,因为父类实例化之后另外开辟空间,就不会影响原来父类原型对象
3.将子类的constructor
把父类的实例对象赋值给子类的原型
```

```	js

function Father () {

		}
		Father.prototype.chang = function () {
			console.log('唱歌');
		}

		function Son () {

		}
		// Son.prototype = Father.prototype;
		Son.prototype = new Father();
		var obj = new Son();
		obj.chang();

		Son.prototype.score = function () {
			console.log('考试');
		}

		// obj.score();
		// console.log(Son.prototype);
		console.log(Father.prototype);
```

**注意:一定要让Son指回构造函数**

```
实现继承后,让Son指回原构造函数
Son.prototype= new Father();
Son.prototype.constructor=Son;
```

##### 总结:用构造函数实现属性继承,用原型对象实现方法继承

 把父类的实例对象赋值给子类的原型对象,(此时会出现原型覆盖,所以)把子类的原型对象指回构造函数constructor

Son.prototype=new Father();

赋值时会将constructor覆盖,要手动指回去

Son.prototype.constructor=Son

### 组合继承:构造函数+原型对象

属性:子类 Father.call(this,参数);

方法:子类的原型对象=父类实例对象;把子类的原型对象指回构造函数constructor

# 类的本质 :function

```js
    // ES6 (部分支持ES6)
    class Star {};
    var obj = new Star();

    // ES5
    function Star() {};
    var obj = new Star();

    console.log(typeof Star);
    console.log(Star.prototype);
    console.log(obj.__proto__);
	
	i=i+1; //语法盐
	i++; //语法糖
```

```
class本质还是function

类的所有方法都定义在类的prototype属性上

类创建的实例,里面也有____proto____指向类的prototype原型对象

所以ES6的类它的绝大部分功能,ES5都可以做到,新的class写法只是让对象原型的写法更加清晰/更像面向对象编程的语法而已.

所以ES6的类其实就是语法糖.

语法糖:语法糖就是一种便捷写法.简单理解,有两种方法可以实现同样的功能,但是一种写法更加清晰/方便,那么这个方法就是语法糖
```

## ES5中的新增方法

```
ES5中给我们新增了一些方法,可以很方便的操作数组或者字符串,这些方法主要包括:
数组方法
字符串方法
```

## 遍历数组的方法

```js
1.for循环的方式 遍历数组
    var arr = [{
      name: '张三丰'
    }, {
      name: '李寻欢'
    }, {
      name: '阿飞'
    }];
    for (var i = 0; i < arr.length; i++) {
      console.log(arr[i].name);
    }

2.forEach() 遍历数组  遍历谁 谁调用
  var arr = ['red', 'blue', 'yellow']
  arr.forEach(function(val, i, shuzu) {
    //   第一个参数:当前项
    // 第二个参数:当前项的索引值
    // 第三个参数:当前数组本身  一般情况下不写
    console.log(val, i, shuzu);
  })

3.filter遍历数组  除了遍历 还可以筛选 返回值是 一个新的数组

  var arr = [123, 456, 789, 66, 99, 88]

  //   筛选:筛选后返回一个新数组  找个变量 newArr接收
  var newArr = arr.filter(function(val, i, shuzu) {
    console.log(val, i, shuzu);
    return val % 2 == 0;
  })
  console.log(newArr);
//输出  [456,66,88]

4.some()遍历数组  
方法用于检测数组中的元素是否满足指定条件. 通俗点查找数组中是否有满足条件的元素

注意它返回值是布尔值, 如果查找到这个元素, 就返回true , 如果查找不到就返回false.

如果找到第一个满足条件的元素,则终止循环. 不在继续查找.

val: 数组当前项的值
i：数组当前项的索引
n:数组对象本身

  var arr = [123, 78, 99, 456, 29, 40]
    //查找某个值是否在数组里面
  var newArr = arr.some(function(val, i, n) {
    console.log(val, index, n);
    return val == 100;
  })
  console.log(newArr);
  //输出false
//取值
 var arr = [123, 78, 99, 456, 29, 40]
    //查找某个值是否在数组里面
  var jieshou = [];
  var newArr = arr.some(function(val, i, n) {
    // console.log(val, i, n);
    // return val == 100;
    if (val == 99) {
      jieshou.push(val);
      return true;
    }
  })
  console.log(jieshou); //输出 [99]
5.every() 
6.map()
```

# 查询商品



## 字符串方法

str.trim() 清除字符串两侧的空白

trim:删除字符串两侧的空白符

## 函数进阶 

### 函数的定义(命名函数/匿名函数)和调用

```js
1.命名函数
  function fn() {
    //this
    console.log(this);

  }
  fn();

2.匿名函数  函数遇到()  就好执行
  // 第一种
  var fun = function() {
    console.log('wahaha');

  };
  console.log(fun);
  fun();

  // 第二种  自调用函数
  (function(形参) {
    console.log(123);

  })(实参)
3.实例化对象的形式的函数  基本不用
  var obj = new Function('a', 'b', "console.log(a+b)");
  obj(1, 2);
```

### 函数调用

 1.普通函数: *function* () {  } fn();

2. 对象的方法[对象.方法()];

3. 构造函数[new Fn()]

4. 绑定事件函数[obj.onclick=*function*(){}]

5. 定时器函数[window.setInterval(*function*(){},1000)]

  6.立即执行函数[(*function*(){}())]]

### this指向

this:当前调用者

普通函数调用      window

构造函数调用      实例对象 原型对象里面的方法也指向实例对象

对象方法调用       该方法所属对象(调用者)

事件绑定程序       事件源(绑定事件对象)

定时器函数           window

立即执行函数       window

### 改变函数内部this的指向  函数里面才会有this

* javaScript 为我们专门提供了一些函数方法来帮我们更优雅的处理函数内部this的指向问题,常用的bind() call() apply() 三种方式

#### call方法 (主要运用到继承)

* call()方法调用一个对象.简单理解为调用函数的方式,但是它可以改变函数的this指向
* fun.call(this指向的值,参数1,参数2..)
* 返回值就是函数的返回值,因为它就是调用函数
* 因此当我们想改变this指向,同时想调用这个函数的时候,可以使用call:比如继承

```js
 function Father(){this}
function Son(){Father.call(this,1,2)}

var n = {
    name: '李寻欢',
    feidao: function() {
      console.log(this);

    }
  }
// 改变this指向
  var obj = {
    name: '阿飞'
  };
  n.feidao.call(obj);
```

#### apply方法  (主要运用到数组)

* fun.apply(this值,[传递的值,必须包含在数组里面]):调用函数
* 返回值就是函数的返回值
* 因此apply主要跟数组有关系,比如使用Math.max() 求数组的最大值

```js
apply 第一个位置改变对象,第二个位置是数组
  function fn(a, b) {
    console.log(this);

  }
  var obj = {
    name: '娃哈哈'
  }
  fn.apply(obj, [1, 34]);
//第二个参数 是数组
  var arr = [3, 4, 39, 20, 20, 38, 39]
  console.log(Math.max(3, 4, 39, 20, 20, 38, 39));
  Math.max.apply(arr.arr);
```

#### bind() 不调用函数,但是还想改变this指向,比如改变定时器内部的this指向

```js
  function fn(a, b) {
    console.log(this, a, b);
  }
  var obj = {
    name: '假冰冰'
  };
  var newFn = fn.bind(obj, 123, 23);
  newFn();
比如定时器内部的this指向  
  //disabled  按钮禁用
  var btn = document.querySelector('input')
  btn.onclick = function() {
    this.disabled = true;
    window.setTimeout(function() {
      this.disabled = false;
    }.bind(this), 1000)
  }
```

### 三种方式的区别

*  相同点:都可以改变函数内部的this指向
* 不同点:
  1. call和apply会调用函数,并且改变函数内部this指向
  2. call和apply传递的参数不一样,call传递参数是 参数1,参数2...形式   apply必须数组形式[参数]
  3. bind 不会调用函数,可以改变函数内部this指向
* 主要应用场景:
  1. call经常做继承
  2. apply经常跟数组有关系,比如借助于数学对象实现数组最大值最小值
  3. bind 不调用函数,但是还想改变this指向  比如改变定时器内部的this指向

## JS两种模式

正常模式

### 严格模式

```
什么是严格模式

JavaScript 除了提供正常模式外，还提供了严格模式（strictmode）。ES5 的严格模式是采用具有限制性JavaScript 变体的一种方式，即在严格的条件下运行JS 代码。
严格模式在IE10 以上版本的浏览器中才会被支持，旧版本浏览器中会被忽略。
严格模式对正常的JavaScript 语义做了一些更改：

1.消除了Javascript语法的一些不合理、不严谨之处，减少了一些怪异行为。【例如变量，不声明就报错】
2.消除代码运行的一些不安全之处，保证代码运行的安全。
3.提高编译器效率，增加运行速度。
4.禁用了在ECMAScript的未来版本中可能会定义的一些语法，为未来新版本的Javascript做好铺垫。比如一些保留字如：class, enum, export, extends, import, super 不能做变量名
```

### 开启严格模式

* 开启严格模式:"use strict"
* 为脚本开启严格模式
* 为函数开启严格模式

```js
<script>"use strict"</script>：脚本开启严格模式
	<script>function fn () {"use strict"}</script>为函数开启严格模式

严格模式可以应用到整个脚本或个别函数中。因此在使用时，我们可以将严格模式分为为脚本开启严格模式和为函数开启严格模式两种情况。
```

### 严格模式中的变化

* 严格模式对JavaScript的语法和行为,都做了一些改变

#### 变量规定

* 变量申明必须加var,,而且不准删除变量
* 在正常模式中,如果一个变量没有声明就赋值,默认是全局变量.严格模式禁止这种用法,变量都必须先用var命令声明,然后在使用
* n=3 严禁删除已经声明变量.例如 delete x; 语法是错误的

#### 严格模式下this指向问题

严格模式下,普通函数this是undefined

```
以前在全局作用域函数中的this 指向window 对象。
严格模式下全局作用域中函数中的this是undefined。

其他的没有变化：
以前构造函数时不加new也可以调用,当普通函数，this 指向全局对象
严格模式下,如果构造函数不加new调用, this 指向的是undefined 如果给他赋值则会报错
new 实例化的构造函数指向创建的对象实例。
定时器this 还是指向window 。
事件、对象还是指向调用者。
```

#### 函数变化

参数不能重名

```
函数不能有重名的参数。

函数必须声明在顶层.新版本的JavaScript 会引入“块级作用域”（ES6 中已引入）。为了与新版本接轨，不允许在非函数的代码块内声明函数。【if，for等里面定义函数也不可以，但是现在不可以】

更多严格模式要求参考：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Strict_mode

错误写法:
function fn (a,a) {console.log(a+a);}
fn(1,2);
```



## 高阶函数

* 把函数当做参数传递或者把函数当做返回值返回的函数，叫做高阶函数
* 函数也是一种数据类型,同样可以作为参数,传递给另外一个参数使用.最典型的就是作为回调函数
* 同理函数也可以作为返回值传递回来

````js
    // 函数 return 后面没有值,返回undefined
    // return:如果后面有值,把这个值返回到调用位置
    // 如果return后面不写值,默认的相当于返回undefined
    // 如果不写return,也相当于返回undefined
````

```js
// 把函数当做参数传递或者把函数当做返回值返回的函数，叫做高阶函数
		
		// function fn (n) {
		// 	// 0，''，null，undefiend，NaN
		// 	// console.log(n);
		// 	// if (n) {
		// 	// 	n();
		// 	// }
		// 	n && n();
		// }
		// var m = function () {console.log(123);};
		// fn(m);

		function fn (n) {
			// n = m;
			conbsole.log(n);// n = function () {console.log(123)};
			n();
		}
		var m = function () {console.log(123)};
		fn(m);
		// var k = function () {}

```



# 函数不调用不执行

# 闭包

## 变量作用域

```
变量根据作用域的不同分为两种：全局变量和局部变量。

1. 函数内部可以使用全局变量。
2. 函数外部不可以使用局部变量。
3. 当函数执行完毕，本作用域内的局部变量会销毁。
```

## **什么是闭包**

**闭包作用：延伸变量的作用范围。**

```
闭包（closure）指有权访问另一个函数作用域中变量的函数。【很多种解释，都并不权威】

简单理解就是，一个作用域可以访问另外一个函数内部的局部变量。

<script>
	function fn1(){
		// fn1 就是闭包函数
		var num = 10;
		function fn2(){
			console.log(num); // 10
		}
		fn2()
	}
	fn1();
</script>
```

**思考：如何再函数外面访问到函数内部的变量**

```
function fn () {

		var i = 7;
		return function () {
			console.log(i);
		}
		// function fn1 () {
		// 	console.log(i);
		// }
		// fn1();
	}
	var n = fn();
n();
```

**练习：**

```
注册事件练习：打印索引值
var lis = document.querySelectorAll('li');

	for (var i = 0; i < lis.length; i++) {

		(function (index) {
			lis[index].onclick = function () {
				console.log(index);
			}
		})(i);

}




思考题：
var name = "The Window";
   var object = {
     name: "My Object",
     getNameFunc: function() {
     return function() {
     return this.name;
     };
   }
 };
console.log(object.getNameFunc()())
----------------------------------------------------------------------------------------
var name = "The Window";　　
  var object = {　　　　
    name: "My Object",
    getNameFunc: function() {
    var that = this;
    return function() {
    return that.name;
    };
  }
};
console.log(object.getNameFunc()())
```



课程回顾：

​	数组方法：forEach，filter，some

​	字符串方法：trim

​	this：指向调用者

​	改变this指向：call，apply，bind

​	严格模式（"use strict"），正常模式

​	高阶函数：函数作为参数传递或者作为返回值返回

​	闭包：一个作用域访问另外一个函数内部局部变量，闭包，延长shen变量的作用范围

递归，正则



# 递归

## 什么是递归

```
递归：**如果一个函数在内部可以调用其本身，那么这个函数就是递归函数。简单理解:函数内部自己调用自己, 这个函数就是递归函数

函数的递归，递归函数

递归：函数调用函数其本身

**注意：**递归函数的作用和循环效果一样，由于递归很容易发生“栈溢出”错误（stack overflow），所以必须要加退出条件return。
```

## 练习：

```
利用递归求1~n的阶乘

//利用递归函数求1~n的阶乘 1 * 2 * 3 * 4 * ..n
 function fn(n) {
     if (n == 1) { //结束条件
       return 1;
     }
     return n * fn(n - 1);
 }
 console.log(fn(3));
```

```
利用递归求斐波那契数列

// 利用递归函数求斐波那契数列(兔子序列)  1、1、2、3、5、8、13、21...
// 用户输入一个数字 n 就可以求出 这个数字对应的兔子序列值
// 我们只需要知道用户输入的n 的前面两项(n-1 n-2)就可以计算出n 对应的序列值
function fb(n) {
  if (n === 1 || n === 2) {
        return 1;
  }
  return fb(n - 1) + fb(n - 2);
}
console.log(fb(3));


思考题羊村：50人家，每户一只羊
	每户只能看别人家的羊有木有病
	每户只能杀自己家的羊
	第一天，第二天 ,第三天，砰砰砰几声枪响，问杀了几只羊
```

```
利用递归遍历数据

		var data = [
			{
				id : 1,
				name : '家电'
			},
			{
				id : 2,
				name : '服饰'
			}
		];


var data = [{
   id: 1,
   name: '家电',
   goods: [{
     id: 11,
     gname: '冰箱',
     goods: [{
       id: 111,
       gname: '海尔'
     }, {
       id: 112,
       gname: '美的'
     },

            ]

   }, {
     id: 12,
     gname: '洗衣机'
   }]
 }, {
   id: 2,
   name: '服饰'
}];
//1.利用 forEach 去遍历里面的每一个对象
 function getID(json, id) {
   var o = {};
   json.forEach(function(item) {
     // console.log(item); // 2个数组元素
     if (item.id == id) {
       // console.log(item);
       o = item;
  
       // 2. 我们想要得里层的数据 11 12 可以利用递归函数
       // 里面应该有goods这个数组并且数组的长度不为 0 
     } else if (item.goods && item.goods.length > 0) {
       o = getID(item.goods, id);
     }
   });
   return o;
}
```



## 深拷贝和浅拷贝

​	**拷贝不能直接赋值，对象赋值的是地址**

```
var obj = {
		name : '张三丰',
		age : 22
	};
var newObj = obj;
console.log(newObj);
```

### 浅拷贝：

> 只拷贝最外面一层

```
var obj = {
			name : '张三丰',
			age : 22
		};

		var newObj = {};
		for (key in obj) {
			newObj[key] = obj[key];
		}

		console.log(newObj);
		
es6：新方法

Object.assign(target, sources);

console.log(newObj);

```

### 深拷贝

```
var obj = {
			name : '1张三丰',
			age : 22,
			messige : {
				sex : '男',
				score : 16
			},
			color : ['red','purple','qing']

		}

		var newObj = {};


		function kaobei (newObj,obj) {

			for (key in obj) {

				if (obj[key] instanceof Array) {
					newObj[key] = [];
					kaobei(newObj[key],obj[key]);
				} else if (obj[key] instanceof Object) {
					newObj[key] = {};
					kaobei(newObj[key],obj[key])
				} else {
					newObj[key] = obj[key];
				}

			}

		}
		obj.messige.sex = 99;
		kaobei(newObj,obj);
		console.log(newObj);
```





# 正则表达式概述

## 什么是正则表达式

```
正则表达式（ Regular Expression ）是用于匹配字符串中字符组合的模式。在JavaScript中，正则表达式也是对象。


作用：检索关键字，过滤敏感字符，表单验证

正则表通常被用来检索、替换那些符合某个模式（规则）的文本，例如验证表单：用户名表单只能输入英文字母、数字或者下划线， 昵称输入框中可以输入中文(匹配)。此外，正则表达式还常用于过滤掉页面内容中的一些敏感词(替换)，或从字符串中获取我们想要的特定部分(提取)等 。

其他语言也会使用正则表达式，本阶段我们主要是利用JavaScript 正则表达式完成表单验证。


```

## 正则表达式的特点

```
1. 灵活性、逻辑性和功能性非常的强。
2. 可以迅速地用极简单的方式达到字符串的复杂控制。
3. 对于刚接触的人来说，比较晦涩难懂。比如：^\w+([-+.]\w+)@\w+([-.]\w+).\w+([-.]\w+)*$
4. 实际开发,一般都是直接复制写好的正则表达式. 但是要求会使用正则表达式并且根据实际情况修改正则表达式.   比如用户名:   /^[a-z0-9_-]{3,16}$/

```

## 正则表达式在js中的使用

**创建正则表达式**

```
在 JavaScript 中，可以通过两种方式创建一个正则表达式。

方式一：通过调用RegExp对象的构造函数创建 

    var regexp = new RegExp(/123/);
    console.log(regexp);

方式二：利用字面量创建 正则表达式

     var reg = /abc/; 含义：只要包含abc就可以
     


```

## 测试正则表达式 

```
test() 正则对象方法，用于检测字符串是否符合该规则，该对象会返回 true 或 false，其参数是测试字符串

注意正则里面没有引号
regexObj.test(str);
regexObj：正则表达式
str：用户输入字符串

var rg = /123/;
console.log(rg.test(123));//匹配字符中是否出现123  出现结果为true
console.log(rg.test('abc'));//匹配字符中是否出现123 未出现结果为false
```

## 正则表达式中的特殊字符

### 正则表达式的组成

```
个正则表达式可以由简单的字符构成，比如 /abc/，也可以是简单和特殊字符的组合，比如 /ab*c/ 。其中特殊字符也被称为元字符，在正则表达式中是具有特殊意义的专用符号，如 ^ 、$ 、+ 等。

正则表达式：简单字符 和 特殊字符【元字符】

特殊字符非常多，可以参考： 

MDN：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Regular_Expressions


jQuery 手册：正则表达式部分

正则测试工具 ： http://tool.oschina.net/regex

```

正则：匹配字符串

​	1、创建珍珠铬【new RegExp(/abc/)，var str = /abc/;】

​	2、测试【reg.test(str)】

​	3、表达式：简单字符和特殊字符





创建正则：1、new RegExp(/abc/);2、var reg = /abc/;

reg.test(字符串)

var reg = /abc/;

简单字符，特殊字符【元字符】

# 边界符



```
正则表达式中的边界符（位置符）用来提示字符所处的位置，主要有两个字符

^ : 表示匹配行首的文本（以谁开始）【/^abc/：以abc为开头】

$：表示匹配行尾的文本（以谁结束）【/^abc$/：只能是abc】

```

**如果 ^和 $ 在一起，表示必须是精确匹配。**

```
var rg = /abc/; // 正则表达式里面不需要加引号 不管是数字型还是字符串型
// /abc/ 只要包含有abc这个字符串返回的都是true
console.log(rg.test('abc'));
console.log(rg.test('abcd'));
console.log(rg.test('aabcd'));
console.log('---------------------------');
var reg = /^abc/;
console.log(reg.test('abc')); // true
console.log(reg.test('abcd')); // true
console.log(reg.test('aabcd')); // false
console.log('---------------------------');
var reg1 = /^abc$/; // 精确匹配 要求必须是 abc字符串才符合规范
console.log(reg1.test('abc')); // true
console.log(reg1.test('abcd')); // false
console.log(reg1.test('aabcd')); // false
console.log(reg1.test('abcabc')); // false
```

# 字符类

> ```
> 符类表示有一系列字符可供选择，只要匹配其中一个就可以了。所有可供选择的字符都放在方括号内。
> ```

## [] 方括号

```
表示有一系列字符可供选择，只要匹配其中一个就可以了【多选1】

var rg = /[abc]/; // 只要包含有a 或者 包含有b 或者包含有c 都返回为true
console.log(rg.test('andy'));//true
console.log(rg.test('baby'));//true
console.log(rg.test('color'));//true
console.log(rg.test('red'));//false
var rg1 = /^[abc]$/; // 三选一 只有是a 或者是 b  或者是c 这三个字母才返回 true
console.log(rg1.test('aa'));//false
console.log(rg1.test('a'));//true
console.log(rg1.test('b'));//true
console.log(rg1.test('c'));//true
console.log(rg1.test('abc'));//true
----------------------------------------------------------------------------------
var reg = /^[a-z]$/ //26个英文字母任何一个字母返回 true  - 表示的是a 到z 的范围  
console.log(reg.test('a'));//true
console.log(reg.test('z'));//true
console.log(reg.test('A'));//false
-----------------------------------------------------------------------------------
//字符组合
var reg1 = /^[a-zA-Z0-9]$/; // 26个英文字母(大写和小写都可以)任何一个字母返回 true  
------------------------------------------------------------------------------------
//取反 方括号内部加上 ^ 表示取反，只要包含方括号内的字符，都返回 false 。
var reg2 = /^[^a-zA-Z0-9]$/;
console.log(reg2.test('a'));//false
console.log(reg2.test('B'));//false
console.log(reg2.test(8));//false
console.log(reg2.test('!'));//true

/^[^a-z]$/：两个^，括号外面的是便边界，括号里面的是取反的含义
```

## 符

> ```
> 词符用来设定某个模式出现的次数。
> ```

```
量词		说明

*		重复0次或更多次【>=0次】/^[a-z]*$/

+		重复1次或更多次【>=1次】【/^[a-z]+$/】

?		重复0次或1次

{n}		重复n次

{n,}	重复n次或更多次

{n,m}	重复n到m次
注意：{n,m}n和m之间不准有空格

边界符：^，$
中括号：[]：被中括号包含的东西只能选1个
量词符：*，+，?，{n,m}

```

## 用户名表单验证

功能需求:

1. 如果用户名输入合法, 则后面提示信息为:  用户名合法,并且颜色为绿色
2. 如果用户名输入不合法, 则后面提示信息为:  用户名不符合规范, 并且颜色为红色

```
var input = document.querySelector('input');
		var span = document.querySelector('span');

		var reg = /^[a-zA-Z0-9_-]{6,16}$/;

		input.onblur = function () {

			if (reg.test(this.value)) {
				span.innerHTML = '输入正确';
				span.className = 'right';
			}else {
				span.innerHTML = '错误内容';
				span.className = 'error';
			}
}
```

## 括号总结



```
1.大括号  量词符.  里面表示重复次数

2.中括号 字符集合。匹配方括号中的任意字符. 

3.小括号表示优先级

正则表达式在线测试 ： https://c.runoob.com
```

# 预定义类

```
预定义类指的是某些常见模式的简写方式.
```

<img src="D:/..王谦-就业班/js高级/day4/笔记4/img3.png">

## 验证案例：

**手机验证**

```
var tel = document.getElementById('tel');
var regtel = /^[1][3|4|5|7|8][0-9]{9}$/;
tel.onblur = function () {

	if (regtel.test(tel.value)) {
		this.nextElementSibling.className = 'success';
		this.nextElementSibling.innerHTML = '手机输入正确<i class="success_icon"></i>';
		console.log(123);
	} else {
		tel.nextElementSibling.className = 'error';
		tel.nextElementSibling.innerHTML = '手机输入错误<i class="error_icon"></i>';
		console.log(456)
	}

}
```

**QQ验证：**

```
var regqq = /^[1-9][0-9]{4,}$/;

var regtel = /^1[3|4|5|7|8][0-9]{9}$/;
	var regqq = /^[1-9][0-9]{4,}$/;
	

	function jiance (obj, reg) {
		obj.onblur = function () {
			if (reg.test(this.value)) {
				this.nextElementSibling.className = 'success';
				this.nextElementSibling.innerHTML = '<i class="success_icon"></i> 手机输入正确';
			} else {
				this.nextElementSibling.className = 'error';
				this.nextElementSibling.innerHTML = '<i class="error_icon"></i> 手机输入错误';
			}
		}
	}

	jiance(tel,regtel);
	jiance(qq,regqq);
```

**昵称验证：**

```
var nikName = /^[\u4e00-\u9fa5]{2,8}$/;
```

**短信验证：**

```
var regmsg = /^[0-9]{6}$/;
```

## replace替换：



/表达式/[修饰符]

g：全局匹配

i：忽略大小写

gi：全局+忽略

屏蔽敏感字符



