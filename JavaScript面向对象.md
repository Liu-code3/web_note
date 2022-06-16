1.面向对象编程介绍

- 面向过程
- 面向对象

## 1.1 面向过程编程POP(Process-oriented programming)

面向过程就是分析出解决问题所需要的步骤,然后用函数把这些步骤步一步实现 ,使用的时候再一个一个的依次调用就可以了。

举个栗子:将大象装进冰箱,面向过程做法。

![image-20220428170000042](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220428170000042.png)

面向过程,就是按照我们分析好了的步骤,按照步骤解决问题。

## 1.2 面向对象编程OOP (Object Oriented Programming)

面向对象是把事务分解成为-个个对象,然后由对象之间分工与合作。

举个栗子:将大象装进冰箱,面向对象做法。

先找出对象,并写出这些对象的功能:

1.大象对象

●进去

2.冰箱对象

●打开

●关闭

3.使用大象和冰箱的功能

面向对象是以对象功能来划分问题，而不是步骤。

在面向对象程序开发思想中,每- -个对象都是功能中心,具有明确分工。

面向对象编程具有灵活、代码可复用、容易维护和开发的优点,更适合多人合作的大型软件项目。

面向对象的特性:

- 封装性
- 继承性
- 多态性

![image-20220428170600593](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220428170600593.png)

## 1.3 面向过程和面向对象的对比

**面向过程**

- 优点:性能比面向对象高,适合跟硬件联系很紧密缺点:没有面向对象易维护、易复用、易扩展
- 缺点:没有面向对象易维护、易复用、易扩展

**面向对象**

- 优点:易维护、易复用、易扩展,由于面向对象有封装、继承、多态性的特性,可以设计出低耦合的系统，使系统更加灵活、更加易于维护
- 缺点: 性能比面向过程低

用面向过程的方法写出来的程序是一份蛋炒饭,而用面向对象写出来的程序是一份盖浇饭。

# 2.ES6中的类和对象

## 1.ES6对象

**面向对象**

面向对象更贴近我们的实际生活,可以使用面向对象描述现实世界事物.但是事物分为具体的事物和抽象的事物.

![image-20220428172026317](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220428172026317.png)

面向对象的思维特点:

1. 抽取(抽象)对象共用的属性和行为组织(封装)成一个类(模板)
2. 对类进行实例化， 获取类的对象

面向对象编程我们考虑的是有哪些对象,按照面向对象的思维特点,不断的创建对象使用对象指挥对象做事情.

### 1.1 对象

现实生活中: 万物皆对象，对象是一个具体的事物,看得见摸得着的实物。例如，一本书、一辆汽车、一个人可以是“对象”, 一个数据库、一张网页、一个与远程服务器的连接也可以是“对象”。

在JavaScript中,对象是一组无序的相关属性和方法的集合 ,所有的事物都是对象,例如字符串、数值、数组、函数等。

对象是由属性和方法组成的:

- 属性:事物的特征，在对象中用属性来表示(常用名词)
- 方法:事物的行为,在对象中用方法来表示(常用动词)

### 1.2 类 class

在ES6中新增加了类的概念,可以使用class关键字声明一个类,之后以这个类来实例化对象。

类抽象了对象的公共部分,它泛指某一大类( class )

对象特指某一个,通过类实例化一个具体的对象

### 1.3 创建类

**语法：**

```javascript
class name {
	// class body
}
```

创建实例：

```javascript
var xx = new name();
```

注意：类必须使用new实例化对象

### 1.4 类constructor构造函数

constructor()方法是类的构造函数(默认方法) ,用于传递参数返回实例对象,通过new命令生成对象实例时, 自动调用该方法。如果没有显示定义类内部会自动给我们创建一 个constructor()

```javascript
// 1。创建类 class 创建一个 明星类
        class Star {
            // 在我们类里面所有函数都不用加function
            // 类的共有属性放到 constructor里面
            constructor(uname, age) {
                // this指向的是创建的实例
                this.uname = uname;
            }
            sing(song) {
                console.log(this.uname + song);
            }
        }

        // 2.利用类创建对象 new
        var ldh = new Star("刘德华", 18); // 只要你加了new 就自动的调用constructor 这个函数就会执行
        var zxy = new Star("张学友", 20);
        // console.log(ldh.uname);
        // console.log(zxy.uname);
        console.log(ldh);
        console.log(zxy);
        
```

(1) 通过class 关键字创建类，类名我们还是习惯性定义首字母大写

(2) 类里面有个constructor函数,可以接受传递过来的参数,同时返回实例对象

(3) constructor函数只要new生成实例时,就会自动调用这个函数，如果我们不写这个函数,类也会自动生成这个函数

(4) 生成实例new不能省略

(5) 最后注意语法规范，创建类类名后面不要加小括号，生成实例类名后面加小括号，构造函数不需要加function

### 1.5 类中添加方法

(1) 我们类里面所有的函数不需要写function
(2) 多个函数方法之间不需要添加逗号分隔

```javascript
// 1。创建类 class 创建一个 明星类
        class Star {
            // 在我们类里面所有函数都不用加function
            // 类的共有属性放到 constructor里面
            constructor(uname, age) {
                // this指向的是创建的实例
                this.uname = uname;
            }
            sing(song) {
                console.log(this.uname + song);
            }
        }

        // 2.利用类创建对象 new
        var ldh = new Star("刘德华", 18); // 只要你加了new 就自动的调用constructor 这个函数就会执行
        var zxy = new Star("张学友", 20);
        // console.log(ldh.uname);
        // console.log(zxy.uname);
        console.log(ldh);
        console.log(zxy);
        // (1) 我们类里面所有的函数不需要写function
        // (2) 多个函数方法之间不需要添加逗号分隔
        ldh.sing('冰雨');
        zxy.sing('李香兰');
```

## 2.类的继承

### 2.1 继承

现实中的继承:子承父业,比如我们都继承了父亲的姓。

程序中的继承:子类可以继承父类的一些属性和方法。

**语法：**

```javascript
class Father { // 父类
    
}

class Son extends Father {  // 子类继承父类
     
}
```

**实例**

```javascript
class Father {
            constructor() {

            }
            money() {
                console.log(100);
            }
        }
        class Son extends Father {

        }
        var son = new Son();
        son.money();
```



### 2.2 super关键字

super关键字用于访问和调用对象父类上的函数。可以调用父类的构造函数,也可以调用父类的普通函数。

```javascript
class Father {
            constructor(x, y) {
                this.x = x;
                this.y = y;
            }
            // 父类里面的方法必须使用父类里面的数据
            sum() {
                console.log(this.x + this.y);
            }
        }

        class Son extends Father {
            constructor(x, y) {
                super(x, y); // 调用了父类中的构造函数 就把子类的constructor参数传给父类的constructor
            }
        }

        var son = new Son(1, 2);
        son.sum();
```

### 1.suer调用父类普通函数

```javascript
 class Father {
            say() {
                return '我是你爸爸';
            }
        }

        class Son extends Father {
            // say() {
            //     console.log('我是儿子');
            // }
            say() {
                console.log(super.say() + '的儿子');
                // super.say() 就是调用父类中的普通函数 say()
            }
        }

        var son = new Son();
        son.say();
		// 继承中的属性或者方法查找原则: 就近原则
        // 1.继承中，如果实例化子类输出一个方法，先看子类有没有这个方法, 如果有就先执行子类的
        // 2.继承中，如果子类里面没有，就去查找父类有没有这个方法，如果有,就执行父类的这个方法(就近原则)
```

### 2.super调用父类的构造函数

注意:子类在构造函数中使用super,必须放到this前面(必须先调用父类的构造方法，在使用子类构造方法)

# 3.三个注意点

1.在ES6 中类没有变量提升，所以必须先定义类，才能通过类实例化对象

2.类里面的共有的属性和方法一定要加this使用.

3.类里面this的指向问题

4.constructor里面的this指向实例对象,方法里面的this指向这个方法的调用者

```html
<button>点击</button>
    <script>
        var that; // 全局变量
        class Star {
            constructor(uname, age) {
                // constructor 里面的this指向的是实例化对象
                // console.log(this);
                that = this; // 让当前的实例化对象赋值给_that
                this.uname = uname;
                this.age = age;
                // this.say();
                this.sing();
                this.btn = document.querySelector("button");
                this.btn.onclick = this.say; // 这里的say方法 后面不跟括号，因为跟了括号，页面一加载就调用了这个方法。

            }
            say() {
                // 这个say方法里面的this 指向的是 btn 这个按钮，因为这个按钮调用了这个函数
                // console.log(this);
                // console.log('hi');
                console.log(this.uname); // undefined 因为button里面没有这个属性
                console.log(that.uname); // 这个that 里面存储的是constructor里面的this
            }
            sing() {
                // 这个sing里面的this 指向的是实例化对象 ldh 因为ldh调用了这个函数
                console.log(this);
            }
        }
        var ldh = new Star('刘德华', 18);

    </script>
```

# 4.面向对象的案例

## 面向对象版tab栏切换

**功能需求：**

1. 点击tab栏,可以切换效果.
2. 点击+号,可以添加tab项和内容项.
3. 点击x号,可以删除当前的tab项和内容项
4. 双击tab项文字或者内容项文字，可以修改里面的文字内容.

**抽象对象：Tab对象**

1. 该对象具有切换功能
2. 该对象具有添加功能
3. 该对象具有删除功能
4. 该对象具有修改功能

**面向对象版tab栏切换 添加功能**

1. 点击+可以实现添加新的选项卡和内容
2. 第一步:创建新的选项卡li和新的内容section
3. 第二步:把创建的两个元素追加到对应的父元素中.
4. 以前的做法:动态创建元素createElement ,但是元素里面内容较多,需要innerHTML赋值,在appendChild追加到父元素里面.
5. 现在高级做法: **利用insertAdjacentHTML(position, text)可以直接把字符串格式元素添加到父元素中**
6. appendChild不支持追加字符串的子元愫, insertAdjacentHTML支持追加字符串的元素

node.insertAdjacentHTML(position, text) node父节点 position是位置，text是需要添加的字符串

**面向对象版tab栏切换 删除功能**

1. 点击x可以删除当前的Ii选项卡和当前的section
2. X是没有索弓|号的，但是它的父亲li有索引号,这个索引号正是我们想要的索引号
3. 所以核心思路是:点击x号可以删除这个索引号对应的li和section

**面向对象版tab栏切换 编辑功能**

1. 双击选项卡li或者section里面的文字，可以实现修改功能
2. **双击事件是: ondblclick**
3. 如果双击文字,会默认选定文字,此时需要双击禁止选中文字
4. window.getSelection ? window.getSelection().removeAllRanges(): document.selection.empty(); 
5. 核心思路:双击文字的时候，在里面生成一个文本框, 当失去焦点或者按下回车然后把文本框输入的值给原先元素即可.

```javascript
 input.select(); // 文本框里面的文字处于选定状态
```

**html和css部分**

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        * {
            padding: 0;
            margin: 0;
        }

        ul li {
            list-style: none;
        }

        main {
            width: 1000px;
            margin: 100px auto;
        }


        main h3 {
            width: 100%;
            height: 60px;
            line-height: 60px;
            text-align: center;
        }

        .tabbox {
            position: relative;
            width: 100%;
            height: 362px;
            border: 1px solid lightsalmon;
        }

        nav {
            display: flex;
            justify-content: space-between;

        }

        nav ul {
            display: flex;
            overflow: hidden;
        }

        nav ul li {
            position: relative;
            width: 120px;
            height: 60px;
            line-height: 60px;
            text-align: center;
            border-right: 1px solid #CCC;
            border-bottom: 1px solid #CCC;
            cursor: pointer;

        }

        nav ul li input {
            width: 90px;
            height: 40px;
            outline: none;
        }

        nav.firstnav ul li.liactive {
            border-bottom: 2px solid #fff;
            z-index: 9;
        }

        .icon-guanbi {
            position: absolute;
            top: 0;
            right: 0;
            width: 15px;
            height: 15px;
            line-height: 12px;
            text-align: center;
            border-bottom-left-radius: 20px;
            font-size: 6px;
            color: #fff;
            background-color: #000;
        }

        .tabadd {
            width: 20px;
            height: 20px;
            margin: auto 10px;
            line-height: 20px;
            text-align: center;
            border: 1px solid #999;
            cursor: pointer;
        }

        .tabscon {
            position: absolute;
            top: 61px;
            left: 0;
            width: 100%;
            height: 300px;
            border-top: 1px solid #ccc;
        }

        .tabscon section {
            display: none;
            padding: 30px;
            position: absolute;
            top: 5px;
            left: 5px;
        }

        .tabscon section.conactive {
            display: block;
        }

        .tabscon section input {
            width: 800px;
            height: 200px;
        }
    </style>
</head>

<body>
    <main>
        <h3>JS面向对象 动态添加标签页</h3>
        <div class="tabbox" id="tab">
            <!-- tab标签 -->
            <nav class="firstnav">
                <ul>
                    <li class="liactive"><span>测试1</span><span class="iconfont icon-guanbi">x</span></li>
                    <li><span>测试2</span><span class="iconfont icon-guanbi">x</span></li>
                    <li><span>测试3</span><span class="iconfont icon-guanbi">x</span></li>
                </ul>
                <div class="tabadd">
                    <span>+</span>
                </div>
            </nav>
            <!-- tab内容 -->
            <div class="tabscon">
                <section class="conactive">测试1</section>
                <section>测试2</section>
                <section>测试3</section>
            </div>
        </div>

    </main>
    <script src="./js/tab.js"></script>
</body>

</html>
```

**js部分**

```javascript
var that;
class Tab {
    constructor(id) {
        // 获取元素
        that = this;
        this.main = document.querySelector(id);
        this.tabadd = this.main.querySelector(".tabadd");
        // li的父元素
        this.ul = this.main.querySelector(".firstnav ul");
        // section的父亲
        this.tabscon = this.main.querySelector(".tabscon");
        this.init();

    }
    // init 初始化操作让相关的元素绑定事件
    init() {
        this.updataNode(); //先获取所有的li和section 然后再循环绑定点击事件
        this.tabadd.onclick = this.addTab;
        for (var i = 0; i < this.lis.length; i++) {
            this.lis[i].index = i;
            this.lis[i].onclick = this.toggleTab;
            this.remove[i].onclick = this.removeTab;
            this.spans[i].ondblclick = this.editTab;
            this.sections[i].ondblclick = this.editTab;
        }

    }
    // 因为我们动态创建元素 需要从新获取对应元素 所以需要的时候要重新调用这个方法
    updataNode() {
        this.lis = this.main.querySelectorAll("li");
        this.sections = this.main.querySelectorAll("section");
        this.remove = this.main.querySelectorAll(".icon-guanbi");
        this.spans = this.main.querySelectorAll(".firstnav ul li span:first-child");
    }
    // 1.切换功能
    toggleTab() {
        that.clearClass(); // 排他思想 先清除样式 再留下当前的样式
        this.className = 'liactive';
        that.sections[this.index].className = 'conactive';
    }
    clearClass() {
        for (var i = 0; i < this.lis.length; i++) {
            this.lis[i].className = '';
            this.sections[i].className = '';
        }
    }
    // 2.添加功能
    addTab() {
        that.clearClass(); // 利用排他思想 先清除li和section的样式 在保留当前样式
        var random = Math.random();
        // (1) 创建li元素和section元素
        var li = '<li class="liactive"><span>测试1</span><span class="iconfont icon-guanbi">x</span></li>';
        var section = '<section class="conactive">测试' + random + '</section>';
        // (2) 把这两个元素追加到对应的父元素里面
        // 这里不能用this 因为这个this指向的是 tabadd这个按钮
        that.ul.insertAdjacentHTML('beforeend', li);
        that.tabscon.insertAdjacentHTML('beforeend', section);
        that.init(); // 当动态创建完元素后，再重新获取一下
    }
    // 3.删除功能
    removeTab(e) {
        e.stopPropagation(); // 阻止冒泡 防止触发li的 切换点击事件
        var index = this.parentNode.index;
        console.log(index);
        // 根据索引号删除对应的li 和section remove()方法可以直接删除指定的元素
        that.lis[index].remove();
        that.sections[index].remove();
        that.init(); // 删除索引号对应的元素后 再重新给剩下的元素设置对应的索引号 实时更新索引号
        // 当我们删除的不是选中状态的li 的时候，原来的选中状态li保持不变
        if (document.querySelector(".liactive")) return;
        //当我们删除了选中状态的这个li的时候， 让它的前一个li 处于选中状态
        index--;
        // 手动调用我们的点击事件 不需要鼠标触发
        // 逻辑与 当第一个为真的时候才执行第二个 
        // 当索引号为0的时候 index-- index就为-1了 第一个为假 所以直接中断程序
        that.lis[index] && that.lis[index].click();
    }
    // 4.修改功能
    editTab() {
        var str = this.innerHTML;
        // 双击禁止选定文字
        window.getSelection ? window.getSelection().removeAllRanges() : document.selection.empty();
        this.innerHTML = '<input type="text" />';
        var input = this.children[0];
        input.value = str;
        input.select(); // 文本框里面的文字处于选定状态
        // 当我们input失去焦点就把文本框里面的值给span

        input.onblur = function () {
            if (input.value == '') {
                return alert('请输入内容');
            } else {
                this.parentNode.innerHTML = this.value;
            }

        }
        // 按下回车也可以把文本框里面的值给span
        input.onkeyup = function (e) {
            if (e.keyCode === 13) {
                // 手动调用表单失去焦点事件 不需要鼠标离开操作
                this.blur();
            }
        }


    }
};
new Tab("#tab");
```

# 1.构造函数和原型

## 1.1 概述

在典型的OOP的语言中(如Java) , 都存在类的概念,类就是对象的模板,对象就是类的实例,但在ES6之前,JS中并没用引入类的概念。
ES6,全称ECMAScript6.0 , 2015.06发版。但是目前浏览器的JavaScript是ES5版本,大多数高版本的浏览器也支持ES6 ,不过只实现了ES6的部分特性和功能。
在ES6之前,对象不是基于类创建的,而是用一种称为**构造函数**的特殊函数来定义对象和它们的特征。
创建对象可以通过以下三种方式:

1. 对象字面量
2. new Object()
3. 自定义构造函数

```javascript
// 1.利用 new Object() 创建对象
        var obj = new Object();

        // 2.利用对象字面量创建对象
        var obj2 = {};

        // 3.利用构造函数创建对象
        // 构造函数名首字母大写
        function Star(uname, age) {
            this.uname = uname;
            this.age = age;
            this.sing = function () {
                console.log('刘师好');
            }
        }
        // 实例化对象
        var ldh = new Star('刘德华', 18);
        var zjl = new Star('周杰伦', 16);

        console.log(ldh.age);
        ldh.sing(); // 调用了公共的方法
```

## 1.2 构造函数

**构造函数**是一种特殊的函数,主要用来初始化对象,即为对象成员变量赋初始值,它总与new 一起使用。我们可以把对象中一些公共的属性和方法抽取出来 ,然后封装到这个函数里面。

**在JS中,使用构造函数时要注意以下两点:**

1. 构造函数用于创建某一类对象,其**首字母要大写**
2. 构造函数要**和new 一起使用**才有意义

**new在执行时会做四件事情:**

1. 在内存中创建一个新的空对象。
2. 让this指向这个新的对象。
3. 执行构造函数里面的代码,给这个新对象添加属性和方法。
4. 返回这个新对象(所以构造函数里面不需要retum )。

JavaScript的构造函数中可以添加一些成员,可以在构造函数本身上添加,也可以在构造函数内部的this上添加。通过这两种方式添加的成员,就分别称为**静态成员**和**实例成员**。

构造函数中的属性和方法我们称为成员，成员可以添加

- 静态成员:在构造函数本身上添的成员称为静态成员,只能由构造函数本身来访问
- 实例成员: 在构造函数内部创建的对象成员称为实例成员,只能由实例化的对象来访问

```javascript
// 构造函数中的属性和方法我们称为成员，成员可以添加
        function Star(uname, age) {
            this.uname = uname;
            this.age = age;
            this.sing = function () {
                console.log('我会唱歌');
            }
        }
        // 实例化对象
        var zjl = new Star('周杰伦', 16);
        // 1.实例成员就是构造函数内部通过this添加的成员 uname age sing 就是实例成员
        // 实例成员只能通过实例化的对象来访问
        console.log(ldh.age);
        ldh.sing(); // 调用了公共的方法
        // console.log(Star.age); // 不可以通过构造函数来访问实例成员
        // 2.静态成员 在构造函数本身上添加的成员
        Star.sex = '男';
        console.log(Star.sex);
        // console.log(ldh.sex); // 不可以通过实例化对象访问
```

## 1.3 构造函数的问题

构造函数方法很好用，但是**存在浪费内存的问题。**

![image-20220430175528050](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220430175528050.png)

![image-20220430191805125](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220430191805125.png)

复杂数据类型就会开辟另一个空间，指向的是地址。他们两个指向地址是不一样的。

我们希望所有的对象使用同一个函数，这样就比较节省内存，那么我们需要把这个方法放在原型对象里面。

## 1.4 构造函数原型 prototype

构造函数通过原型分配的函数是所有对象所共享的。
JavaScript规定，**每一个构造函数都有一个 prototype属性**，指向另一个对象。 注意这个prototype就是一个对象,这个对象的所有属性和方法,都会被构造函数所拥有。
我们可以把那些不变的方法,直接定义在prototype对象上,这样所有对象的实例就可以共享这些方法。

原型是一个对象，我们也称为prototype为原型对象。原型的作用是共享方法。

一般情况下，我们的公共属性(简单数据类型)定义到构造函数里面，公共的方法(复杂数据类型)我们放到原型对象身上。

![image-20220430191627756](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220430191627756.png)

```javascript
function Star(uname, age) {
            this.uname = uname;
            this.age = age;
            // this.sing = function () {
            //     console.log('我会唱歌');
            // }
        }
        // 实例化对象
        var ldh = new Star('刘德华', 18);
        var zjl = new Star('周杰伦', 16);
        Star.prototype.sing = function () {
            console.log('我会唱歌');
        }
		ldh.sing();
		zjl,sing();
        console.log(ldh.sing === zjl.sing); // true 指向的地址是一样的
```

## 1.5 对象原型 __proto__

```javascript
__proto__ (前后都是两条英文状态下的下划线)
```

**对象都会有一个属性__proto__**指向构造函数的 prototype原型对象,之所以我们对象可以使用构造函数prototype原型对象的属性和方法,就是因为对象有_ proto_ 原型的存在。

- _ proto_ 对象原型和原型对象 prototype是等价的
- _ proto_ 对象原型的意义就在于为对象的查找机制提供-个向,或者说一 条路线,但是它是一 个非标准属性，因此实际开发中,不可以使用这个属性,它只是内部指向原型对象prototype

![image-20220430195330479](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220430195330479.png)

方法的查找规则: 首先先看ldh 对象身上是否有sing方法，如果有就执行这个对象上的sing
如果没有sing这个方法，因为有_ proto__ 的存在,就去构造函数原型对象prototype身上去查找
sing这个方法

```javascript
function Star(uname, age) {
            this.uname = uname;
            this.age = age;
            // this.sing = function () {
            //     console.log('我会唱歌');
            // }
        }
        // 实例化对象
        var ldh = new Star('刘德华', 18);
        var zjl = new Star('周杰伦', 16);
        Star.prototype.sing = function () {
            console.log('我会唱歌');
        }java

        console.log(ldh.__proto__ === Star.prototype); // true
```

## 1.6 construvtor 构造函数

**对象原型(_ proto_ )** 和**构造函数( prototype )原型对象**里面都有一个属性 constructor属性, constructor我们称为构造函数,因为它指回构造函数本身。
constructor主要用于记录该对象引用于哪个构造函数,它可以让原型对象重新指向原来的构造函数。

很多情况下，我们需要手动的利用constructor 这个属性指回 原来的构造函数

如果我们修改了原来的原型对象，给原型对象赋值的是一个对象，则必须手动的利用constructor指回原来的构造函数。

```javascript
function Star(uname, age) {
            this.uname = uname;
            this.age = age;

        }

        // 采取.的形式 往这个对象里面添加 sing和movie方法
        // Star.prototype.sing = function () {
        //     console.log('我会唱歌');
        // };

        // Star.prototype.movie = function () {
        //     console.log('我会演电影');
        // }

        // 利用=的形式 把Star.prototype之前的对象全部给覆盖了 把constructor这个属性给覆盖了
        Star.prototype = {
            // 如果我们修改了原来的原型对象，给原型对象赋值的是一个对象，则必须手动的利用constructor指回原来的构造函数。
            constructor: Star,
            sing: function () {
                console.log('我会唱歌');
            },
            movie: function () {
                console.log('我会演电影');
            }
        }

        var ldh = new Star("刘德华 18 刘师好");
        console.log(Star.prototype);
        console.log(ldh.__proto__);
        // console.log(Star.prototype.constructor);
        // console.log(ldh.__proto__.constructor);
```

## 1.7 构造函数、实例、原型对象三者之间的关系

![image-20220430212650870](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220430212650870.png)

new 了Star构造函数 就会产生实例对象

## 1.8 原型链

![image-20220430221402114](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220430221402114.png)

```javascript
function Star(uname, age) {
            this.uname = uname;
            this.age = age;
        }

        Star.prototype.sing = function () {
            console.log('我会唱歌');
        }

        var ldh = new Star('刘德华', 18)
        // 1.只要是对象就有__proto__ 原型，指向原型对象
        console.log(Star.prototype);
        console.log(Star.prototype.__proto__ === Object.prototype);
        // 2.我们Star原型对象里面的 __proto__原型指向的是 Object.prototype
```

## 1.9 JavaScript的成员查找机制(规则)

- 当访问一个对象的属性(包括方法)时，首先查找这个**对象自身**有没有该属性。
- 如果没有就查找它的原型(也就是_ proto_ 指向的prototype原型对象)。
- 如果还没有就查找原型对象的原型( Object的原型对象)。
- 依此类推一直找到Object为止( null)。
- __proto__对象原型的意义就在于为对象成员查找机制提供一 个方向 , 或者说一条路线。

```javascript
function Star(uname, age) {
            this.uname = uname;
            this.age = age;
        }

        Star.prototype.sing = function () {
            console.log('我会唱歌');
        }

        var ldh = new Star('刘德华', 18);
        // 只设置Object.prototype原型身上有sex属性
        Object.prototype.sex = '男';
        // ldh.sex = '女';
        // 实例化对象照样可以输出 如果设置实例化对象有sex属性 它会输出实例化对象身上的属性值
        console.log(ldh.sex);

        // 只有 Object.prototype原型对象身上有toString方法
        console.log(Object.prototype);
        console.log(Star.prototype);
        console.log(ldh);
        // 但是实例化对象lhd一样可以调用
        console.log(ldh.toString());
```

## 1.10 原型对象this指向问题

1. 在构造函数中，this指向的是对象实例 ldh
   因为当我们new了构造函数 会创建一个空的对象 然后this就指向这个空对象 也就是指向对象实例
2. 原型对象函数里面的this 指向的是 实例对象 ldh

```javascript
var that;
        function Star(uname, age) {
            this.uname = uname;
            this.age = age;
        }

        Star.prototype.sing = function () {
            console.log('我会唱歌');
            that = this;
        }

        var ldh = new Star('刘德华', 18);
        // 1.在构造函数中，this指向的是对象实例 ldh
        // 因为当我们new了构造函数 会创建一个空的对象 然后this就指向这个空对象 也就是指向对象实例
        // 2.原型对象函数里面的this 指向的是 实例对象 ldh
        ldh.sing();
        console.log(ldh === that);
```

## 1.11 扩展内置对象

可以通过原型对象,对原来的内置对象进行扩展自定义的方法。比如给数组增加自定义求偶数和的功能。

注意:数组和字符串内置对象不能给原型对象覆盖操作Array.prototype = {} , 只能是Array.prototype.xxx = function(){}的方式。

- Array.prototype = {} 这样以对象的形式存储方法，会把之前的数组原型对象里面的方法全部覆盖掉
- Array.prototype.xxx = function(){} 采取"."的形式 这是给数组原型对象追加方法，不会覆盖之前的方法

```javascript
 Array.prototype.sum = function () {
            var sum = 0;
            for (var i = 0; i < this.length; i++) {
                sum += this[i];
            }
            return sum;
        }
        // 不能以对象的形式存储方法 会覆盖数值原型对象之前的方法
        // Array.prototype = {
        //     sum: function () {
        //         var sum = 0
        //         for (var i = 0; i < this.length; i++) {
        //             sum += this[i];
        //         }
        //         return sum;
        //     }
        // }
        console.log(Array.prototype); // 添加的对象 打印出来的颜色比较深
        var arr = [777, 555, 333];
        console.log(arr.sum());
        var arr1 = new Array(1, 2, 3);
        console.log(arr1.sum());
```

# 2.继承

ES6之前并没有给我们提供extends继承。我们可以通过**构造函数+原型对象**模拟实现继承,被称为**组合继承**。

## 2.1 call()

调用这个函数,并且修改函数运行时的this指向

```javascript
fun.call(thisArg, arg1, arg2, ...)
```

- thisArg: 当前调用函数this的指向对象
- arg1， arg2: 传递的其他参数

```javascript
function fn(x, y) {
            console.log('我想喝手摸咖啡');
            console.log(this);
            console.log(x + y);
        }
        // fn();
        // 1.call() 可以调用函数
        // fn.call();
        var o = {
            name: '周杰伦'
        }
        // 2.call() 可以改变这个函数的this指向 此时这个函数的this 就指向了o这个对象
        // 后面的是普通函数 1,2 是传给fn函数的实参 o是不参与传递的 他是改变this指向的
        fn.call(o, 1, 2);

```

## 2.2 借用构造函数继承父类型属性

核心原理：通过call() 把父类型的this指向子类型this，这样就可以实现子类型继承父类型的属性。

```javascript
// 借用父构造函数继承属性
        // 1.父构造函数
        function Father(uname, age) {
            // this 指向父构造函数的对象实例
            this.uname = uname;
            this.age = age;
        }

        // 2.子构造函数
        function Son(uname, age, score) {
            // this 指向子构造函数的对象实例
            Father.call(this, uname, age);
            this.score = score;
        }

        var ldh = new Son('刘德虎', 18, 90);
        console.log(ldh);
```

## 2.3 借用原型对象继承父类型方法

![image-20220502002328147](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220502002328147.png)

```javascript
// 借用父构造函数继承属性
        // 1.父构造函数
        function Father(uname, age) {
            // this 指向父构造函数的对象实例
            this.uname = uname;
            this.age = age;
        }

        // 2.子构造函数
        function Son(uname, age, score) {
            // this 指向子构造函数的对象实例
            Father.call(this, uname, age);
            this.score = score;
        }
        Father.prototype.money = function () {
            console.log('赚钱');
        }

        // Son.prototype = Father.prototype; // 这样直接赋值会有问题，如果修改了子原型对象，父原型对象也会跟着一起改变
        Son.prototype = new Father();
        // 如果利用对象的形式修改了原型对象，别忘了利用constructor 指回原来的构造函数
        Son.prototype.constructor = Son;
        // 这个是子构造函数专门的方法
        Son.prototype.exam = function () {
            console.log('考试');
        }

        var son = new Son('刘德虎', 18, 90);
        console.log(Son.prototype);
```

# 3.ES5 中的新增方法

## 3.1 ES5新增方法概述

ES5中给我们新增了一些方法。可以很方便的操作数组或者字符串，这些方法主要包括：

- 数组方法
- 字符串方法
- 对象方法

## 3.2 数组方法

迭代(遍历)方法: forEach()、map()、filter()、 some()、 every() ;

### 1. forEach()方法

```javascript
array.forEach(function(currentValue, index, arr) )
```

- currentValue :数组当前项的值
- index :数组当前项的索引号
- arr :数组对象本身

```javascript
		// forEach() 筛选数组
		var arr = [3, 6, 8, 9];
        var sum = 0; //声明有一个全局变量 
        arr.forEach(function (value, index, array) {
            console.log('数组当前项的值' + value);
            console.log('数组当前项的索引号' + index);
            console.log('数组对象本身' + array);
            sum += value; // 让数组里面的值相加
        });

        console.log(sum);
```

### 2. som()

如果查询数组中唯一的元素，用some方法更合适，因为它找到这个元素，就不再进行循环，效率高。

```javascript
// some 查找数组中是否有满足条件的元素
        // var arr = [20, 40, 7];
        // var flag = arr.some(function (value) {
        //     return value > 30;
        // });
        // console.log(flag);

        var arr1 = ['red', 'pink', 'skyblue'];
        var flag = arr1.some(function (value) {
            return value == 'pink';
        });
        console.log(flag);
```

- some() 方法用于检测数组中的元素是否满足指定条件，通俗点查找数组中是否有满足条件的元素
- **注意它返回值是布尔值,如果查找到这个元素,就返回true,如果查找不到就返回false.**
- 如果找到第一个满足条件的元素，则终止循环 不在继续查找.
- currentValue:数组当前项的值
- index :数组当前项的索引
- arr :数组对象本身

1. filter也是查找满足条件的元素，返回的是一个数组，而且是把所有满足条件的元素返回回来
2. some也是查找满足条件的元素是否存在，返回的是一个布尔值，如果查找到第一 个满足条件的元素就终止循环
   


### 3. filter() 

```javascript
array.filter(function (currentValue, index, arr))
```

- filter()方法创建一个新的数组 ,新数组中的元素是通过检查指定数组中符合条件的所有元素主要用于筛选数组
- **注意它直接返回一个新数组**
- currentValue:数组当前项的值
- index :数组当前项的索引|
- arr :数组对象本身

```javascript
		var arr = [1, 3, 4, 6, 7, 8];
        var arr1 = arr.filter(function (value) {
            return value > 3;
        });
        console.log(arr1);
```

## 案列：查询商品

1. 把数据渲染到页面中 （forEach)
2. 根据价格显示数据 (filter)
3. 根据商品名称显示数据 (some)

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>查询商品</title>
    <style>
        * {
            padding: 0;
            margin: 0;
        }

        .Commodity_inquiry {
            width: 600px;
            margin: 100px auto;
        }

        input {
            outline: none;
        }

        .Commodity_h {
            height: 50px;
            line-height: 50px;
            text-align: center;
        }

        .Commodity_h input {
            width: 46px;
        }

        table {
            width: 420px;
            border-spacing: 0;
            /*把单元格间隙设置为0*/
            border-collapse: collapse;
            /*设置单元格的边框合并为1 */
            margin: 0 auto;
            text-align: center;
        }

        table tr th,
        table tr td {
            border: 1px solid #999
        }
    </style>
</head>

<body>
    <div class="Commodity_inquiry">
        <div class="Commodity_h">
            <label for="price">
                按照价格查询:
                <input type="text" value="" id="price" class="start"> -
                <input type="text" value="" id="" class="end">
                <button class="search-price">搜索</button>
            </label>
            <label for="Tradename">
                按照商品名称查询:
                <input type="text" value="" id="Tradename" class="product">
                <button class="search-pro">查询</button>
            </label>
        </div>
        <table>
            <thead>
                <tr>
                    <th>id</th>
                    <th>产品名称</th>
                    <th>价格</th>
                </tr>
            </thead>
            <tbody>

            </tbody>
        </table>
    </div>
    <script>
        // 利用新增数组吩咐操作数据
        var data = [{
            id: 1,
            pname: '苹果',
            price: 3999
        }, {
            id: 2,
            pname: '小米',
            price: 2999
        }, {
            id: 3,
            pname: 'vivo',
            price: 999
        }, {
            id: 4,
            pname: '华为',
            price: 4999
        }];
        // 1.获取相应的元素
        var tbody = document.querySelector("tbody");
        var start = document.querySelector(".start");
        var end = document.querySelector(".end");
        var search_price = document.querySelector(".search-price");
        var search_pro = document.querySelector(".search-pro");
        var product = document.querySelector(".product");
        // 2.把数据渲染到页面中
        setData(data);
        // 因为会重复渲染 所以把渲染封装程一个函数 用的时候调用
        // 但是每个数组名字不一样 我们要设置形参
        function setData(myData) {
            // 先把tbody里面的数据全部清空 然后再渲染 防止重复
            tbody.innerHTML = '';
            myData.forEach(function (value) {
                var tr = document.createElement("tr");
                tr.innerHTML = '<td>' + value.id + '</td><td>' + value.pname + '</td><td>' + value.price + '</td>';
                tbody.appendChild(tr);
            });
        }
        // 3.当我们点击了按钮，就可以根据我们的商品价格去筛选数组里面的对象
        search_price.addEventListener("click", function () {
            var newData = data.filter(function (value) {
                return value.price >= start.value && value.price <= end.value
            })
            console.log(newData);
            // 把筛选完毕之后的对象渲染到页面中
            setData(newData);
        });

        // 4.根据商品名称查找商品
        // 如果查询数组中唯一的元素，用some方法更合适，因为它找到这个元素，就不再进行循环，效率高。
        search_pro.addEventListener("click", function () {
            // 利用字面量创建个新数组 利于渲染到页面
            var arr = [];
            data.some(function (value) {
                if (value.pname === product.value) {
                    arr.push(value);
                    return true; // 后面必须写true
                }
            });
            setData(arr);
        });
    </script>
</body>

</html>
```

### 4. forEach方法与som方法区别

```javascript
   var arr = ['red', 'pink', 'skyblue', 'yellow'];
        //  1.forEach遍历数组
        // arr.forEach(function (value) {
        //     if (value == 'pink') {
        //         console.log('找到了该元素');
        //         return true; // 在forEach 里面 return 不会终止迭代 但是 当pink找到后 11不会打印 只会终止下面的程序执行 不会终止数组迭代
        //     }
        //     console.log(11);
        // });

        // 如果查询数组中唯一的元素，用some方法更合适，
        arr.some(function (value) {
            if (value == 'pink') {
                console.log('找到了该元素');
                return true; // 在some 里面 return 会终止迭代 下面的11也会被终止
            }
            console.log(11);

        });


        // arr.filter(function (value) {
        //     if (value == 'pink') {
        //         console.log('找到了该元素');
        //         return true; // 在filter 里面 return 不会终止迭代 但是 当pink找到后 11不会打印 只会终止下面的程序执行 不会终止数组迭代
        //     }
        //     // console.log(11);
        // });
```

## 3.3 字符串方法

trim() 方法会从一个字符串的两端删除空白字符。

```javascript
str.trim()
```

trim()方法并不影响原字符串本身,它返回的是一个新的字符串。

```javascript
// trim() 方法去除字符串两端空白
        var str = '   andy    ';
        var str1 = str.trim();
        // console.log(str);
        // console.log(str1);
        // console.log(str1.length);

        var btn = document.querySelector('button');
        var text = document.querySelector("textarea");
        var input = document.querySelector("input");

        btn.onclick = function () {
            var str = input.value.trim();
            if (str == '') {
                alert('请输入内容')
            } else {
                text.value = str;
            }
            console.log(input.value.length);
            console.log(str.length);
            input.value = '';
        }
```

## 3.4 对象方法

### 1.Object.keys() 用于获取对象自身所有的属性

```javascript
object.keys (obj)
```

- 效果类似for..in

- 返回一个由属性名组成的数组.

```javascript
// Object.keys(obj) 用于获取对象自身所有的属性名 
        var obj = {
            id: 1,
            pname: '小米',
            price: 2999
        }
        var arr = Object.keys(obj);
        console.log(arr);
        //   返回的是所有属性名组成的数组  然后再用forEachb遍历数组
        arr.forEach(function (value) {
            console.log(value);
        });
```

### 2.Object.defineProperty() 定义对象中新属性或修改原有的属性。

```javascript
object.defineProperty(obj, prop, descriptor)
```

- obj :必需。目标对象
- prop:必需。需定义或修改的属性的名字
- descriptor :必需。目标属性所拥有的特性

Object.defineProperty(第三个参数descriptor说明: 以对象形式{}书泻

- value: 设置属性的值默认为undefined
- writable:值是否可以重写。 true | false默认为false
- enumerable: 目标属性是否可以被枚举。true |false默认为false
- configurable: 目标属性是否可以被删除或是否可以再次修改特性true | false默认为false

```javascript
var obj = {
            id: 1,
            pname: '小米',
            price: 2999
        };
        // 以前给对象修改或者新增属性的方法
        // obj.price = 3999;
        // obj.num = 1000;
        // console.log(obj);

        // Object.defineProperty() 定义对象中新属性或修改原有的属性。
        Object.defineProperty(obj, 'price', {
            value: 999,
        });

        Object.defineProperty(obj, 'num', {
            value: 900,
            enumerable: true,
        });

        Object.defineProperty(obj, 'id', {
            // 如果值为false 不允许修改这个属性值 默认值是false
            writable: false,

        });
        obj.id = 3;  // 修改不了id的值

        Object.defineProperty(obj, 'address', {
            value: '中国山东蓝翔',
            writable: false,
            // enumerable 如果值为false 则不允许遍历，默认的值是false
            enumerable: true,
            // configurable 如果值为false 则不允许删除这个属性  不允许再修改第三个参数里面的特性 默认为false
            configurable: false
        });

        // Object.defineProperty(obj, 'address', {
        //     value: '中国山东蓝翔',
        //     writable: true,
        //     enumerable: false,
        //     configurable: false
        // });


        console.log(obj);
        console.log(Object.keys(obj));

```

# 1.函数的定义和调用

## 1.1 函数的定义方式

1. 函数声明方式function关键字(命名函数)

2. 函数表达式(匿名函数)

3. new Function(）

   

   ```javascript
   var fn = new Function('参数1', '参数2'..., '函数体')
   ```

- Function 里面参数都必须是字符串格式。
- 第三种方式执行效率低,也不方便书写,因此较少使用
- 所有函数都是Function的实例(对象)
- 函数也属于对象

![image-20220503150921505](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220503150921505.png)

## 1.2 函数的调用方式

1. 普通函数
2. 对象的方法
3. 构造函数
4. 绑定事件函数
5. 定时器函数
6. 立即执行函数

```html
<button>点击事件</button>
    <script>
        // 1. 普通函数
        function fn() {
            console.log('加油哦');
        };
        // fn();
        // fn.call();

        // 2. 对象的方法
        var o = {
            sing: function () {
                console.log('加油哦');

            }
        };
        o.sing();

        // 3. 构造函数
        function Star() {
            this.sing = function () {
                console.log('刘德华会唱歌');
            }
        };
        var ldh = new Star();
        ldh.sing();
        // 4. 绑定事件函数
        var btn = document.querySelector('button'); // 点击了按钮就可以调用这个函数
        btn.onclick = function () {
            clearInterval(timer);
            console.log('周杰伦');
        }
        // 5. 定时器函数
        var str = ' ';
        var timer = setInterval(function () { // 这个函数是定时器自动1秒钟调用一次
            str += '刘师好';
            str.length >= 3 ? str : str + '\n';
            console.log(str);
        }, 1000);

        // 6. 立即执行函数
        // (function () {
        //     console.log(11); // 立即执行函数是自动调用
        // })();
    </script>
```

# 2.this

## 2.1 函数内this的指向

这些this的指向, 是当我们调用函数的时候确定的。调用方式的不同决定了this的指向不同
一般指向我们的调用者.

| 调用方式     | this指向                                  |
| ------------ | ----------------------------------------- |
| 普通函数调用 | window                                    |
| 构造函数调用 | 实例对象 原型对象里面的方法也指向实例对象 |
| 对象方法调用 | 该方法所属对象                            |
| 事件绑定方法 | 绑定事件对象                              |
| 定时器函数   | window                                    |
| 立即执行函数 | window                                    |

```html
<button>点击事件</button>
    <script>
        // 1. 普通函数 (命名函数) this指向的是window
        function fn() {
            console.log('普通函数的this指向' + this);
        };
        window.fn(); // 完整的调用函数方法 但是一般window我们省略不写
        // 2. 对象的方法 (匿名函数) this指向的是对象 o
        var o = {
            sing: function () {
                console.log('对象的方法(匿名函数)' + this);
            }
        };
        o.sing();
        // 3. 构造函数 this 指向 ldh 这个实例对象 原型对象里面的this 指向的也是 ldh这个实例对象
        function Star() {
            console.log('构造函数的this指向' + this);
        };
        var ldh = new Star();
        // 4. 绑定事件函数 指向的是函数的调用者 btn这个按钮对象
        var btn = document.querySelector('button');
        btn.onclick = function () {
            console.log('btn点击事件的this' + this);
        }
        // 5. 定时器函数 this 指向的也是window
        setInterval(function () {
            console.log('定时器函数的this指向' + this);
        }, 1000);
        // 6. 立即执行函数 指向的是window
        (function () {
            console.log('立即执行函数的this指向' + this);
        })();
        </script>
```

## 2.2 改变函数内部 this 指向

JavaScript为我们专门提供了一些函数方法来帮我们更优雅的处理函数内部this的指向问题,常用的有bind()、call()、apply0 三种方法。
### 1.call方法

call()方法调用一个对象。简单理解为调用函数的方式,但是它可以改变函数的this指向。

```javascript
fun.call(thisArg, arg1, arg2, .. .)
```

- thisArg: 当前调用函数this的指向对象
- arg1， arg2: 传递的其他参数

```javascript
 		// 改变函数内this 指向 js提供了三种方法 call() bind() apply()
        // 1.call()
        var o = {
            name: 'andy'
        };

        function fn(a, b) {
            console.log(this);
            console.log(a + b);
        };
        // fn.call();
        fn.call(o, 1, 2);
        // call 第一个可以调用函数 第二个可以改变函数内的this指向 但是不影响传参
        // call 的主要作用可以实现继承 继承父构造函数的属性
        function Father(uname, age, sex) {
            this.uname = uname;
            this.age = age;
            this.sex = sex;
        };
        function Son(uname, age, sex) {
            Father.call(this, uname, age, sex);
        };
        var ldh = new Son('刘德华', 18, '男');
        console.log(ldh);
```

### 2.apply方法

apply()方法**调用**一个函数。简单理解为调用函数的方式,但是它可以改变函数的this指向。

```javascript
fun.apply(thisArg, [argsArray])
```

- thisArg :在fun函数运行时指定的this值
- argsArray :传递的值,必须包含在**数组**里面 (伪数组)
- 返回值就是函数的返回值,因为它就是调用函数

```javascript
		// 2.apply() 应用2 运用的意思
        var o = {
            name: 'andy'
        }

        function fn(arr) {
            console.log(this);
            console.log(arr); // 打印出来的是字符串形式
        }
        fn.apply(o, ['pink red hotpink']); // 数组的形式传递参数
        // 1.就是调用函数 第二个可以改变函数内部的this指向
        // 2.但是他的参数必须是数组(伪数组)
        // 3.apply 的主要应用 比如说我们可以利用 apply 借助于数学内置对象求最大值
        Math.max();
        var arr = [1, 5, 67, 34, 99];
        var max = Math.max.apply(Math, arr); // 调用数学内置对象 因为是Math调用了max 改为Math
        console.log(max);
        var min = Math.min.apply(Math, arr)
        console.log(min);
```

### 3.bind方法

bind()方法不会调用函数，但是能改变函数内部this指向

```javascript
fun.bind(thisArg, arg1, arg2, ...)
```

- thisArg : 在fun函数运行时指定的this值
- arg1 , arg2 :传递的其他参数
- 返回由指定的this值和初始化参数改造的**原函数拷贝**

```html
	<button>点击</button>
    <script>
        // // 3.bind() 绑定 捆绑的意思
        var o = {
            name: 'andy'
        };

        function fn(a, b) {
            console.log(this);
            console.log(a + b);
        };

        var f = fn.bind(o, 1, 2);
        f();
        // 1.不会调用原来的函数 可以改变原来函数内部的this 指向
        // 2.返回的是原函数改变this之后产生的新函数
        // 3.如果有的函数我们不需要立即调用，但是又想改变这个函数内部的this执行 此时用bind
        // 4.我们有一个按钮，当我们点击之后，就禁用这个按钮，3秒钟之后开启这个按钮
        var btn = document.querySelector("button");
        btn.onclick = function () {
            this.disabled = true; // 这个this 指向的是 brn 这个按钮
            // var that = this;  // 可以把这里的this 也就是btn绑定的点击事件 btn
            setInterval(function () {
                // this.disabled = false; // 定时器里面的this 指向的是window 所以不能直接用this 需要给定时器的回调函数加上bind() 这里最好写this 因为当有多个点击事件按钮的时候 不知道你点击的是哪一个
                this.disabled = false;
            }.bind(this), 3000); // 因为在btn绑定的点击事件里面 这里的this 指向的是btn 这个对象 （因为用定时器调用 所以这里用bind 不会立即调用）   

        };

    </script>
```

## 2.3 call apply bind 总结

**相同点：**

都可以改变函数内部的this指向

**区别点：**

1. call和apply会调用函数，并且改变函数内部this指向.
2. call 和apply传递的参数不一样, call传递参数aru1, aru2..形式，apply 必须数组形式(伪数组)[arg]
3. bind 不会调用函数，可以改变函数内部this指向.

**主要应用场景:**

1. call 经常做继承.
2. apply 经常跟数组有关系.比如借助于数学对象实现数组最大值最小值
3. bind 不调用函数但是还想改变this指向.比如改变定时器内部的this指向.

# 3.严格模式

## 3.1 严格模式的含义

JavaScript除了提供正常模式，,还提供了**严格模式( strict mode )**。ES5 的严格模式是采用具有限制性。JavaScript变体的一-种方式，即在严格的条件下运行JS代码。

严格模式在IE10以上版本的浏览器中才会被支持，旧版本浏览器中会被忽略。

严格模式对正常的JavaScript语义做了一些更改 :

1. 消除了Javascript语法的一些不合理、不严谨之处，减少了一些怪异行为。
2. 消除代码运行的一些不安全之处，保证代码运行的安全。
3. 提高编译器效率，增加运行速度。
4. 禁用了在ECMAScript的未来版本中可能会定义的一-些语法,为未来新版本的Javascript做好铺垫。比如一-些保留字如: class, enum, export, extends, import, super不能做变量名

## 3.2 开启严格模式

严格模式可以应用到**整个脚本**或**个别函数**中。因此在使用时,我们可以将严格模式分为为**脚本开启严格模式**和**为函数开启严格模式**两种情况。

### 1.为脚本开启严格模式

为整个脚本文件开启严格模式，需要在所有语句之前放一个特定语句"use strict" ;( 或'use strict' ;) 。

```javascript
"use strict";
// 下面的js 代码就会按照严格模式执行代码
console.log ("这是严格模式。");
```

因为"use strict"加了引号,所以老版本的浏览器会把它当作一行普通字符串而忽略。

有的script 基本是严格模式，有的script脚本是正常模式，这样不利于文件合并,所以可以将整个脚本文件放在一个立即执行的匿名函数之中。这样独立创建一个作用域而不影响其他 script脚本文件。

```javascript
// 立即执行函数的作用 为了变量污染或为整个脚本开启独立的作用域空间
(function () {
	"use strict";
	var num = 10;
	function fn() {}
})();
```

### 2.为函数开启严格模式

要给某个函数开启严格模式，需要把"use strict" ; (或'use strict';)声明放在函数体所有语句之前。

```javascript
function fn() {
    'use strict';
    // 下面的js 代码就会按照严格模式执行代码
    consloe.log('严格模式');
};

function f() {
    consloe.log('普通模式');
    // 下面的js 代码就会按照普通模式执行代码
}
```

## 3.3 严格模式中的变化

严格模式对Javascript的语法和行为，都做了一些改变。

### 1.变量规定

1. 在正常模式中,如果一个变量没有声明就赋值,默认是全局变量。严格模式禁止这种用法,变量都必须先用var命令声明，然后再使用。
2. 严禁删除已经声明变量，例如, delete x;语法是错误的。

```javascript
'use strict';
        // 1.我们的变量名必须先声明再使用
        // num = 10;
        // console.log(num);
        var num = 10;
        console.log(num);
        // 2.我们不能随意删除已经声明好的变量
        // delete num;
```

### 2.严格模式下this指向问题

1. 以前在全局作用域函数中的this指向window对象。
2. **严格模式下全局作用域中函数中的this是undefined.**
3. 以前构造函数时不加new也可以调用，当普通函数, this指向全局对象
4. 严格模式下，如果构造函数不加new调用, this会报错.
5. new实例化的构造函数指向创建的对象实例。
6. 定时器this还是指向window。
7. 事件、对象还是指向调用者。

```javascript
		'use strict';
        // 1.我们的变量名必须先声明再使用
        // num = 10;
        // console.log(num);
        var num = 10;
        console.log(num);

        // 2.我们不能随意删除已经声明好的变量
        // delete num;

        // 3.严格模式下全局作用域中函数中的 this 是undefined
        function fn() {
            console.log(this); // undefined
        };
        fn();

		// 普通模式下，构造函数可以当做普通函数使用 直接用window全局对象调用
 		// 4.严格模式下，如果 构造函数不加new调用， this 会报错
        function Star() {
            this.sex = '男';
            // console.log(this);
        };
        // Star();
        // console.log(window.sex);
        var ldh = new Star();
        console.log(ldh.sex);

        // 5. 定时器 this 还是指向 window
        setTimeout(function () {
            console.log(this);
        }, 2000)
```

### 3.函数变化

1. 函数不能有重名的**参数。**
2. 函数必须声明在顶层新版本的JavaScript会引入"块级作用域”( ES6 中已引入)。为了与新版本接轨，不允许在非函数的代码块内声明函数。

```javascript
		// 6.严格模式下函数里面的参数不允许有重名
         // a = 1;
        // a = 2; // 变量的层叠性 所以传的值实际是2 所以正常模式下 输出的是 4
        // function fun(a, a) {
        //     console.log(a + a);
        // };
        // fun(1, 2);
```

更多严格模式要求参考: https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Strict_mode

# 4.高阶函数

高阶函数是对其他函数进行操作的函数,它**接收函数作为参数**或**将函数作为返回值输出**。
```javascript
function fn(callback()) {
	callback && callback();
}
fn(function() { alert('hi')})
```

```javascript
// 闭包里面经常这样使用
// 闭包就是典型的高阶函数
function fn() {
	return function() {}
};
 fn();
```

此时fn就是一个高阶函数
函数也是一种数据类型,同样可以作为参数,传递给另外一个参数使用。最典型的就是作为回调函数。

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="./js/jQuery.min.js"></script>
    <title>Document</title>
    <style>
        div {
            position: relative;
            width: 200px;
            height: 200px;
            background-color: pink;
        }
    </style>
</head>

<body>
    <div></div>
    <script>
        // 高阶函数 函数可以作为参数传递
        function fn(a, b, callback) {
            console.log(a + b);
            callback && callback();
        }
        fn(1, 2, function () {
            console.log(11);
        });
        $("div").animate({
            left: 500
        }, function () {
            $("div").css("backgroundColor", "purple");
        });
    </script>
</body>

</html>
```

# 5.闭包

## 5.1 变量作用域


变量根据作用域的不同分为两种: 全局变量和局部变量。

1. 函数内部可以使用全局变量。
2. 函数外部不可以使用局部变量。
3. 当函数执行完毕,本作用域内的局部变量会销毁。

## 5.2 闭包的含义

**闭包( closure )**指有权**访问**另一个函数作用域中**变量**的**函数**。---- JavaScript高级程序设计

简单理解就是,一个作用域可以访问另外一个函数内部的局部变量。

```javascript
// 闭包 (closure) 指有权访问另一个函数作用域中变量的函数
        // 一个作用域可以访问另外一个函数的局部变量
        // 我们fn 外面的作用域也可以访问fn 内部的局部变量 fn函数就是闭包
        // 闭包的主要作用： 延伸了变量的作用范围

        // function fn() {
        //     var num = 10;
        //     function fun() {
        //         console.log(num);
        //     };
        //     return fun;
        // }
        // var f = fn();
        // f();
        // 类似于
        // var f = function fun() {
        //     console.log(num);
        // }

        // 上面这样写 太复杂了 直接返回函数 如下
        function fn() {
            var num = 10;
            return function () {
                console.log(num);
            }; // 这就是典型的高阶函数
        };
        var f = fn();
        f(); // num 这个变量不会直接fn() 调用后就销毁 因为f() 还等着调用 等全部调用完毕 num才会销毁 所以这就是闭包的作用 延伸了变量的作用范围
        // 类似于
        // var f = function () {
        //     console.log(num);
        // }
```

## 5.3 闭包案列

1. 循环注册点击事件。
2. 循环中的setTimeout()
3. 计算打车价格

### 1.闭包应用-点击小li输出索引号

```html
<ul class="nav">
        <li>刘德华</li>
        <li>张学友</li>
        <li>周杰伦</li>
        <li>黎明</li>
    </ul>
    <script>
        // 闭包的应用 点击li输出当前li的索引号
        // 1.我们可以利用动态添加属性的方式
         var lis = document.querySelector(".nav").querySelectorAll("li");
        // for (var i = 0; i < lis.length; i++) {
        //     lis[i].index = i;
        //     lis[i].onclick = function () {
        //         // console.log(i); // 这个函数是异步的 for循环是同步的 点击哪一个li都是4
        //         console.log(this.index);
        //     }
        // };

        // 2.利用闭包的方式得到当前li 的索引号
        for (var i = 0; i < lis.length; i++) {
            // 利用for循环创建了四个立即执行函数
            // 立即执行函数也称为小闭包 因为立即执行函数里面的任何一个函数都可以使用它的i这变量
            (function (i) {
                // console.log(i); // 输出 0 1 2 3
                lis[i].onclick = function () {
                    // 当我们点击了过后 才会销毁i这个变量 相当的占内存 称为内存泄漏
                    console.log(i); // 这个i使用了立即执行函数的i 
                }
            })(i); // 这个小括号算是调用这个立即执行函数 也可以接收参数 然后传递给函数
        };
  </script>
```

![image-20220505144908213](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220505144908213.png)

立即执行函数是没有名字的 所以closure没有显示闭包的名字。

### 2.闭包应用-3秒钟之后，打印所有li元素的内容

```html
// 立即执行函数里面的任何一个函数都可以使用它的i这变量
<ul class="nav">
        <li>刘德华</li>
        <li>张学友</li>
        <li>周杰伦</li>
        <li>黎明</li>
    </ul>
    <script>
        // 闭包应用-3秒钟之后，打印所有li元素的内容
        var lis = document.querySelector(".nav").querySelectorAll("li");
        for (var i = 0; i < lis.length; i++) {
            (function (i) {
                setTimeout(function () {
                    console.log(lis[i].innerHTML);
                }, 3000)
            })(i)
        }
    </script>
```

### 3.闭包应用-打车价格

```javascript
// 闭包应用-计算打车价格
        // 打车起步价13 (3公里内)， 之后每多一公里增加5元，用户输入公里数就可以计算打车价格
        // 如果有拥堵情况，总价格多收取10元拥堵费
        var car = (function () {
            var start = 13; // 起步价 局部变量
            var total = 0; // 总结 局部变量
            return {
                // 正常的总价
                price: function (n) {
                    if (n <= 3) {
                        total = start;
                    } else {
                        total = (n - 3) * 5 + start;
                    }
                    return total;
                },
                // 拥堵的费用
                yd: function (flag) {
                    return flag ? total + 10 : total;
                }
            }
        })();
        console.log(car.price(5));
        console.log(car.yd(true));

        console.log(car.price(1));
        console.log(car.yd(false));
```

## 5.4 闭包总结

### 1.闭包是什么

闭包是一个函数(一个作用域可以访问另外一个函数的局部变量)

### 2.闭包的作用

延伸变量的作用范围

# 6.递归

## 6.1 递归的含义

1. 如果一个函数在内部可以调用其本身,那么这个函数就是递归函数。

2. 简单理解:函数内部自己调用自己，这个函数就是递归函数

3. 递归函数的作用和循环效果一样

4. 由于递归很容易发生“栈溢出” 错误( stack overflow ) , 所以**必须要加退出条件return**。

5. 递归的分类，递归分为两种，直接递归和间接递归。直接递归就是自己调用自己。而间接递归可以理解为是A调用了B，而B又调用了A。

6. 一般地，递归是由递归边界和递归体两部分组成。递归边界确定递归到何时结束,递归体确定递归求解时的递推关系。

7. 递归的求解的过程均有这样的特征：

   先将整个问题划分为若干个子问题,通过分别求解子问题,最后获得整个问题的解。而这些子问题具有与原问题相同的求解方法,于是可以再将它们划分成若干个子问题,分别求解,如此反复进行,直到不能再划分成子问题,或已经可以求解为止。

```javascript
// 递归函数： 函数内部自己调用自己，这个函数就是递归函数
        var num = 1;
        function fn() {
            console.log('你好啊');
            if (num == 6) {
                return;  // 递归里面必须加退出条件 不然会一直开辟作用域 一直创建内存 造成栈溢出
            };
            num++;
            fn();
        };
        fn();
```

## 6.2 利用递归求数学题

### 1.求 1 * 2 * 3 ... *n 阶乘

```javascript
 // 利用递归函数求1~n的阶乘 1 * 2 * 3 * 4 * ...n
        function fn(n) {
            if (n == 1) {
                return 1; // 当n等于1时 fn(1)返回的值要为1
            }
            return n * fn(n - 1);
        };
        console.log(fn(3));

        // 详细过程
        // 3 * fn(3 -1)
        // 3 * fn(2)
        // 3 * (2 * fn(2 -1))
        // 3 * (2 * fn(1))
        // 3 * (2 * 1)
        // return 3 * 2 *1
```

### 2.求斐波那契数列

```javascript
 // 利用递归函数求斐波那契数列(兔子数列) 1, 1, 2, 3, 5, 8, 13, 21...
        // 用户输入一个数字n 就可以求出 这个数字对应的兔子序列值
        // 我们只需要知道用户输入的 n 的前面两项 (n - 1 n -2)就可以计算出n 对应的序列值
        function fb(n) {
            if (n === 1 || n === 2) { 
                return 1;
            };
            return fb(n - 1) + fb(n - 2);
        }
        console.log(fb(5));
```

![img](https://img-blog.csdnimg.cn/20200301184115754.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQzNDk3NjUw,size_16,color_FFFFFF,t_70)

## 6.3.利用递归遍历数据

### 根据id返回对应的数据对象

```javascript
var data = [{
            id: 1,
            name: '家电',
            goods: [{
                id: 11,
                gname: '冰箱'
            }, {
                id: 12,
                gname: '洗衣机'
            }]
        }, {
            id: 2,
            name: '服饰'
        }];
        // 我们想要做输入id号，就可以返回的数据对象
        // 1.利用 forEach 去遍历里面的每一个对象
        function getId(json, id) {
            var o = {}; // 专门存储我们筛选后的值
            json.forEach(function (value) { // 遍历的是外层的 ’id为1 为2’的两个元素
                // 递归在forEach 里面 递归判断条件就是 forEach遍历完数组完就结束
                // console.log(value);
                if (value.id == id) {
                    // console.log(value); // 不能直接打印 要有返回值
                    o = value; // 这是储存的外层两个元素的值
                    return value;
                    // 2.得到里层的数据 11 12 可以利用递归函数
                    // 里面应该有goods这个数组 并且属猪的长度不为0
                } else if (value.goods && value.goods.length > 0) {
                    o = getId(value.goods, id); // 直接再次调用这个函数 
                    // return value返回给了getId()  getId(value.goods, id) 里层的数据赋值给了 o 最后又返回回去了          
                };
            });
            return o;

        };
        console.log(getId(data, 1));
        console.log(getId(data, 2));
        console.log(getId(data, 11));
        console.log(getId(data, 12));
```

## 6.4 浅拷贝和深拷贝

1. 浅拷贝只是拷贝一层，更深层次对象级别的只拷贝引用.（拷贝的是地址)
2. 深拷贝拷贝多层，每一级别的数据都会拷贝.
3. Object.assign(target , .. sources) es6 新增方法可以浅拷贝

```javascript
// 浅拷贝
var obj = {
            id: 1,
            name: 'andy',
            msg: {
                age: 18
            }
        };

        var o = {};
        // for (var k in obj) {
        //     //  k 是属性名 obj[k] 是属性值
        //     o[k] = obj[k]; // 键值对
        // };
        // o.msg.age = 20;
        // console.log(o);
        // console.log(obj);

        // Object.assign(target, source); ES6新增的浅拷贝方法
        Object.assign(o, obj);
        o.msg.age = 20;
        console.log(o);
        // console.log(obj);
```

![image-20220506154247021](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220506154247021.png)





```javascript
// 深拷贝
// 深拷贝 拷贝多层， 每一级别的数据都会拷贝
        var obj = {
            id: 1,
            name: 'andy',
            msg: {
                age: 18
            },
            color: ['pink', 'red']
        };
        var o = {};
        // 封装函数 需要使用递归函数
        function deepCopy(newobj, oldobj) {
            for (var k in oldobj) {
                // 判断数据类型 如果是简单数据类型就直接拷贝 如果是复杂数据类型例如对象 数组再进入拷贝
                // 1.获取属性值
                var item = oldobj[k];
                // 2.判断这个属性值是否为数组
                if (item instanceof Array) { // 要先把数组筛选出来 因为数组也属于对象 如果先写对象 会把数组也当对象来解析
                    newobj[k] = [];
                    deepCopy(newobj[k], item);
                    // 3.判断这个属性值是否为对象
                } else if (item instanceof Object) {
                    newobj[k] = {};
                    deepCopy(newobj[k], item);
                    // 4.属于简单数据类型
                } else {
                    newobj[k] = item;
                }
            }
        }
        deepCopy(o, obj);
        console.log(o);
        o.msg.age = 20;
        console.log(obj);
  
```

![image-20220506154304745](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220506154304745.png)

# 1.正则表达式概述

## 1.1 正则表达式的含义

**正则表达式( Regular Expression )**是用于匹配字符串中字符组合的模式。在JavaScript中,正则表达式也是对象。
正则表通常被用来检索、替换那些符合某个模式(规则)的文本,例如验证表单:用户名表单只能输入英文字母、数字或者下划线,昵称输入框中可以输入中文(**匹配**)。此外,正则表达式还常用于过滤掉页面内容中的一些敏感词(**替换**) ,或从字符串中获取我们想要的特定部分(**提取**)等。

其他语言也会使用正则表达式,本阶段我们主要是利用JavaScript正则表达式完成表单验证。

## 1.2 正则表达式的特点

1. 灵活性、逻辑性和功能性非常的强。

2. 可以迅速地用极简单的方式达到字符串的复杂控制。

3. 对于刚接触的人来说,比较晦涩难懂。比如: 

   ```javascript
   ^\w+([-+.]\w+)*@\W+ (-.]\W+ )*.\w+([- .]\w+)*$
   ```

4. 实际开发,一般都是直接复制写好的正则表达式.但是要求会使用正则表达式并且根据实际情况修改正则表达式比如用户名: 

   ```javascript
   /^[a-z0-9_ -]{3,16}$/
   ```

# 2.正则表达式在JavaScript中的使用

## 2.1 创建正则表达式

格式不能留空格

在JavaScript中,可以通过两种方式创建一个正则表达式。

1. 通过调用RegExp对象的构造函数创建

   ```javascript
   var 变量名 = new RegExp (/表达式/ );
   ```

2. 通过字面量创建

   ```javascript
   var 变鼂名= /表达式/ ;
   ```

//注释中间放表达式就是正则字面量

## 2.2 测试正则表达式 test

test()正则对象方法，用于检测字符串是否符合该规则，该对象会返回true或false ，其参数是测试字符串。

```javascript
regexObj.test(str)
```

1. regexobj 是写的正则表达式
2. str我们要测试的文本
3. 就是检测str文本是否符合我们写的正则表达式规范.

```javascript
 // 在JavaScript中, 可以通过两种方式创建一个正则表达式。
        // 1.通过调用RegExp对象的构造函数创建
        var regexp = new RegExp(/123/);
        console.log(regexp);

        // 2.通过字面量创建
        var re = /123/; // 正则表达式里面不需要加引号，不管是数字型还是字符串型
        console.log(re);

        // 3.test()正则对象方法，用于检测字符串是否符合该规则
        console.log(re.test('abc')); // false  这里的就要加引号
        console.log(re.test(123)); // truw
```

# 3.正则表达式中的特殊字符

## 3.1 正则表达式的组成

一个正则表达式可以**由简单的字符构成**,比如/abc/ ,**也可以是简单和特殊字符的组合**,比如/ab*c/。其中
特殊字符也被称为**元字符**,在正则表达式中是具有**特殊**意义的专用符号，如^、$、+等。

特殊字符非常多，可以参考:

- MDN : https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Regular_Expressions
- jQuery手册:正则表达式部分
- 正则测试工具: http://tool.oschina.net/regex

这里我们把元字符划分为几类学习

## 3.2 边界符

正则表达式中的边界符(位置符)用来**提示字符所处的位置**,主要有两个字符。

| 边界符 | 说明                         |
| ------ | ---------------------------- |
| ^      | 表示匹配行首的文本(以谁开始) |
| $      | 表示匹配行尾的文本(以谁结束) |

如果^和$在一起，表示必须是精确匹配。

```javascript
 // 边界符 ^ $
        var re = /abc/; // 正则表达式里面不需要添加引号 不管是数字型还是字符串型
        // /abc/ 只要包含有 abc 这个字符串返回的都是 true
        console.log(re.test('abc')); // true
        console.log(re.test('abcd')); // true
        console.log(re.test('aabc')); // true
        console.log('-------------------');

        // /^abc/ 只要是adc 这个开头的都是 true
        var reg = /^abc/;
        console.log(reg.test('abc')); // true
        console.log(reg.test('abcd')); // true
        console.log(reg.test('aabc')); // false
        console.log('-------------------');

        var rege = /^abc$/; // 精确匹配 要求必须是 abc字符串才符合规范
        console.log(rege.test('abc'));
        console.log(rege.test('abcd'));
        console.log(rege.test('aabc'));
```

## 3.3 字符类

字符类表示有一系列字符可供选择 ,只要匹配其中一个就可以了。所有可供选择的字符都放在方括号内。

1.[] 表示有一系列字符可供选择，只要匹配其中一个就可以了

2.[-]方括号内部范围符-

```javascript
 // var rg = /abc/; 只要包含abc就可以
        // 字符类：[] 表示有一系列字符可供选择， 只要匹配其中一个就可以了
        var rg = /[abc]/; // 只要包含有a 或者 包含有b 或者 包含有c 都返回为true
        console.log(rg.test('andy'));
        console.log(rg.test('baby'));
        console.log(rg.test('color'));
        console.log(rg.test('red'));
        console.log('-------------------');

        var reg = /^[abc]$/; // 三选一 只有是a 或者 是b 或者 是c 这三个字母才返回 true
        console.log(reg.test('aa'));
        console.log(reg.test('a'));
        console.log(reg.test('b'));
        console.log(reg.test('c'));
        console.log(reg.test('abc'));
        console.log('-------------------');

        var rege = /^[a-z]$/; // 26个英文字母任何一个字符返回 true
        console.log(rege.test('a'));
        console.log(rege.test('ab')); // false
		console.log(rege.test('A')); // false

```

3.字符组合

```javascript
// 字符组合 
        var rege1 = /^[a-zA-Z0-9_-]$/; // 26哥英文字母(大写和小写都可以)任何一个字母返回 true
        // - 表示的是 a 到 z的范围
        console.log(rege1.test('a'));
        console.log(rege1.test('A'));
        console.log(rege1.test('9'));
        console.log(rege1.test('-'));
        console.log(rege1.test('_'));
        console.log(rege1.test('!'));
```

方括号内部可以使用字符组合，这里表示含a到z的26个英文字母和0到9的数字都可以。

4.[^]中括号内部 取反符^

```javascript
 // 如果中括号里面有 ^ 表示取反的意思 千万和 我们边界符 ^ 相区别
        var rege2 = /^[^a-zA-Z0-9_-]$/; // 就是不包含这些的意思
        console.log(rege2.test('a'));
        console.log(rege2.test('A'));
        console.log(rege2.test('9'));
        console.log(rege2.test('-'));
        console.log(rege2.test('_'));
        console.log(rege2.test('!'));
```

## 3.4 量词符

量词符用来**设定某个模式出现的次数**。

| 量词  | 说明             |
| ----- | ---------------- |
| *     | 重复零次或更多次 |
| +     | 重复一次或更多次 |
| ?     | 重复零次或一-次  |
| {n}   | 重复n次          |
| {n,}  | 重复n次或更多次  |
| {n,m} | 重复n到m次       |

```javascript
 // 量词符：用来设定某个模式出现的次数
        // 简单理解：就是让下面的a这个字符重复多少次
        // var reg = /^a$/;

        // * 重复零次或更多次 相当于>= 0
        // var reg = /^a*$/;
        // console.log(reg.test('')); // true
        // console.log(reg.test('a')); // true
        // console.log(reg.test('aaa')); // true

        // + 重复一次或更多次 相当于 >= 1
        // var reg = /^a+$/;
        // console.log(reg.test('')); // false
        // console.log(reg.test('a')); // true
        // console.log(reg.test('aaa')); // true

        // ? 重复零次或一次 相当于 0 || 1
        // var reg = /^a?$/;
        // console.log(reg.test('')); // true
        // console.log(reg.test('a')); // true
        // console.log(reg.test('aaa')); // false

        // {n} 重复n次  就是重复n次
        // var reg = /^a{3}$/;
        // console.log(reg.test('')); // false
        // console.log(reg.test('a')); // false
        // console.log(reg.test('aaa')); // true

        // { n,} 重复n次或更多次  相当于 >= 3
        // var reg = /^a{3,}$/;
        // console.log(reg.test('')); // false
        // console.log(reg.test('a')); // false
        // console.log(reg.test('aaa')); // true
        // console.log(reg.test('aaaaaaaaaa')); // true

        // { n, m } 重复n到m次 相当于 >= n 并且 <= m
        var reg = /^a{3,16}$/;
        console.log(reg.test('')); // false
        console.log(reg.test('a')); // false
        console.log(reg.test('aaa')); // true
        console.log(reg.test('aaaaaaaaaa')); // true
```

## 3.5 边界符 字符类 量词符号一起使用

```javascript
 // 量词是设定某个模式出现的次数
        var reg = /^[a-z0-9A-Z_-]{3,16}$/; // 这个模式用户只能输入英文字母 数字 下划线 短横线但是有边界符和[] 这就限定了只能多选1 但是后面加了量词符
        // {0,16} 这样书写是正确的 中间不能空格
        console.log(reg.test(''));
        console.log(reg.test('aaa'));
        console.log(reg.test('abc20118av5l0gst'));
```

## 案例：用户名验证

功能需求:
1. 如果用户名输入合法,则后面提示信息为:用户名合法,并且颜色为绿色

2. 如果用户名输入不合法，则后面提示信息为:用户名不符合规范并且颜色为绿色

案例分析：

1. 用户名只能为英文字母，数字，下划线或者短横线组成，并且用户名长度为6~ 16位.
2. 首先准备好这种正则表达式模式/$[a-zA-Z0-9- ]{6,16}^/
3. 当表单失去焦点就开始验证.
4. 如果符合正则规范则让后面的span标签添加right类.
5. 如果不符合正则规范,则让后面的span标签添加wrong类

```html
 <head>
	<style>
        .uname {
            outline: none;
        }

        .correct {
            color: rgb(8, 126, 8);
        }

        .wrong {
            color: red;
        }
    </style>
</head>

<body>
    <input type="text" value="" class="uname"> <span>请输入用户名</span>
    <script>
        var reg = /^[a-z0-9A-Z_-]{6,16}$/;
        var uname = document.querySelector('.uname');
        var span = document.querySelector('span');
        uname.onblur = function () {
            if (reg.test(this.value)) {
                // console.log('正确的');
                span.className = 'correct';
                span.innerHTML = '用户名格式输入正确';
            } else {
                // console.log('错误的');
                span.className = 'wrong';
                span.innerHTML = '用户名格式输入不正确';
            }
        }
    </script>
</body>
```

## 3.6 括号总结

1. 大括号 量词符，里面表示重复次数
2. 中括号字符集合。匹配方括号中的任意字符. （多选一)
3. 小括号表示优先级

可以在线测试: https://c.runoob.com/

```javascript
 var reg = /^abc{3}$/; // 只有abccc才是 true 这样式的就中括号前面那个重复n次
        console.log(reg.test('abccc'));

        var rege = /^(abc){3}$/; // 只有abcabcabc 才是true 小括号具有优先级
        console.log(rege.test('abcabcabc'));
```

## 3.7 预定义类

预定义类指的是**某些常见模式的简写模式**。

| 预定类 | 说明                                                        |
| ------ | ----------------------------------------------------------- |
| \d     | 匹配0-9之间的任一数字,相当于[0-9]                           |
| \D     | 匹配所有0-9以外的字符，相当于[^0-9】                        |
| \w     | 匹配任意的字母、数字和下划线，相当于[A-Za-z0-9_ ]           |
| \W     | 除所有字母、数字和下划线以外的字符，相当于[^A-Za-z0-9_ 】   |
| \s     | 匹配空格(包括换行符、制表符、空格符等)，相等于[ \t\r\n\v\f] |
| \S     | 匹配非空格的字符，相当于[^ \t\r\n\v\f】                     |

```javascript
// 座机号码验证：全国座机号码 两种格式： 010-12345678 或 0530-1234567
        // 正则里面的或者 符号 |
        var reg = /^\d{3}-\d{7}|\d{4}-\d{7}$/;
```

## 案列：表单验证

分析：

1. 手机号：/^1[3|4|5|7|8][0-9]{9}$/
2. QQ: /^[1-9】\d$]{4,}$] (腾讯QQ号从10000开始)
3. 昵称是中文: /^[\u4e00-\u9fa5]{2,8}$/] (中文的Unicode编码表 第一个到最后一个汉字)

**html部分**

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="./css/iconfont.css">
    <link rel="stylesheet" href="./css/index.css">

<body>
    <!-- 头部大logo部分 -->
    <header class="header w">
        <div class="header_img">
            <img src="./images/banner.jpg" alt="">
        </div>
    </header>
    <!-- 注册部分 -->
    <div class="main w">
        <div class="main_h">
            <div class="account_number">注册新用户</div>
            <div class="sign_in">我有账号, 去<a href="javascript:;">登录</a></div>
        </div>
        <div class="main_b">
            <ul class="personal_registration">
                <li class="personal_item1">
                    <label for="phonenumber">手机号: </label>
                    <input type="number" value="" id="phonenumber">
                    <span class="item"></span>
                </li>
                <li class="personal_item1">
                    <label for="qqnumber">QQ: </label>
                    <input type="number" value="" id="qqnumber">
                    <span class="item"></span>
                </li>
                <li class="personal_item1">
                    <label for="nickname">昵称: </label>
                    <input type="text" value="" id="nickname">
                    <span class="item"></span>
                </li>
                <li class="personal_item1">
                    <label for="verification_code">短信验证码: </label>
                    <input type="number" value="" id="verification_code">
                    <span class="item"></span>
                </li>
                <li class="personal_item1">
                    <label for="phonenumber">登录密码: </label>
                    <input type="password" value="" id="login_password">
                    <span class="item"></span>
                </li>
                <li class="strength">
                    <span>密码强度</span>
                    <div class="strength_q">
                        <span class="strength1">弱</span><span class="strength2">中</span><span class="strength3">强</span>
                    </div>
                </li>
                <li class="personal_item1">
                    <label for="phonenumber">确认密码: </label>
                    <input type="password" value="" id="again_pwd">
                    <span class="item"></span>
                </li>
                <li class="consent_agreement">
                    <input type="checkbox" name="" id="agree_ipt"><label for="">同意协议并注册 <a
                            href="javascript:;">《知果果用户协议》</a></label>
                </li>
                <li class="complete_registration">
                    <button type="button">完成注册</button>
                </li>
            </ul>
        </div>
    </div>
    <script src="./js/index.js"></script>
</body>

</html>
```

**CSS部分**

```css
* {
    padding: 0;
    margin: 0;
}

a {
    text-decoration: none;
}

ul li {
    list-style: none;

}

input::-webkit-outer-spin-button,

input::-webkit-inner-spin-button {

    -webkit-appearance: none;

}

input {
    outline: none;

}

.w {
    width: 1200px;
    margin: 0 auto;
}

.header {
    height: 150px;
}

.header_img {
    border-bottom: 2px solid #D51501;
}

.main {
    border: 1px solid #999;
}

.main_h {
    height: 40px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: #E9ECE9;
    border-bottom: 1px solid #999;
}

.account_number {
    color: #55545C;

}

.sign_in a {
    color: #D51501;
}

.personal_item1 {
    width: 800px;
    height: 40px;
    line-height: 40px;
    margin: 10px auto;
}

.personal_item1 label {
    display: inline-block;
    width: 200px;
    text-align: end;
    padding-right: 10px;
}

.personal_item1 input {
    width: 220px;
    height: 30px;
    border: 2px solid #999;
}

.correct {
    color: #3BA73C;
}

.wrong {
    color: #D51501;
}


.strength {
    display: flex;
    width: 639px;
    justify-content: end;
}

.strength_q {
    width: 130px;
    display: flex;
    justify-content: space-between;
    margin-left: 5px;
}

.strength_q span {
    width: 40px;
    height: 20px;
    text-align: center;
}

.strength1 {
    background-color: #D51501;
}

.strength2 {
    background-color: #3BA73C;
}

.strength3 {
    background-color: #FF9300;
}

.consent_agreement {
    width: 410px;
    margin: 40px auto;
}

.complete_registration {
    width: 300px;
    margin: 40px auto;
}

.complete_registration button {
    width: 160px;
    height: 40px;
    background-color: #D6271F;
    outline: none;
    color: #fff;
}
```

**JS部分**

```javascript
window.onload = function () {
    var regtel = /^1[3|4|5|7|8|9]\d{9}$/;
    var regqq = /^[1-9]\d{4,}$/;
    var regnc = /^[\u4e00-\u9fa5]{2,8}$/;
    var regmsg = /^\d{6}$/;
    var regpwd = /^[a-zA-Z\d_-]{6,16}$/;
    var phonenumber = document.querySelector("#phonenumber");
    var qqnumber = document.querySelector("#qqnumber");
    var nickname = document.querySelector("#nickname");
    var verification_code = document.querySelector("#verification_code");
    var login_password = document.querySelector("#login_password");
    var again_pwd = document.querySelector("#again_pwd");
    var agree_ipt = document.querySelector("#agree_ipt");

    var item1 = document.querySelectorAll(".item");
    getBgc(phonenumber);
    regexp(phonenumber, regtel, '手机号码');
    getBgc(qqnumber);
    regexp(qqnumber, regqq, 'QQ号码');
    getBgc(nickname);
    regexp(nickname, regnc, '昵称');
    getBgc(verification_code);
    regexp(verification_code, regmsg, '短信验证码');
    getBgc(login_password);
    regexp(login_password, regpwd, '密码');
    getBgc(again_pwd);
    function regexp(ele, reg, format) {
        ele.onblur = function () {
            if (reg.test(this.value)) {
                this.nextElementSibling.className = 'correct';
                this.nextElementSibling.innerHTML = '<i class="iconfont">&#xe61e;</i> 恭喜输入正确';
            } else {
                this.nextElementSibling.className = 'wrong';
                this.nextElementSibling.innerHTML = '<i class="iconfont">&#xe613;</i> ' + format + '格式输入错误, 请重新输入';
            }
        }
    };

    again_pwd.onblur = function () {
        if (this.value == login_password.value && this.value != '') {
            this.nextElementSibling.className = 'correct';
            this.nextElementSibling.innerHTML = '<i class="iconfont">&#xe61e;</i> 恭喜输入正确';
        } else {
            this.nextElementSibling.className = 'wrong';
            this.nextElementSibling.innerHTML = '<i class="iconfont">&#xe613;</i> 两次密码不一致, 请重新输入';
        }
    };

    function getBgc(Ele) {
        Ele.onfocus = function () {
            this.style.borderColor = 'hotpink';
        };
    };


};
```

# 4.正则表达式中的替换

## 4.1 replace()

replace()方法可以实现替换字符串操作,用来替换的参数可以是一个字符串或是一 个正则表达式。

```javascript
stringObject.replace(regexp/substr,replacement)
```

1. 第一个参数: 被替换的字符串 或者 正则表达式
2. 第二个参数: 替换为的字符串
3. 返回值是一个替换完毕的新字符串
4. 只能替换第一个

```javascript
 // 替换
        var str = 'andy和red';
        // var newStr = str.replace('andy', 'baby');
        var newStr = str.replace(/andy/, 'bady');
        console.log(newStr);
```

## 4.2 正则表达式参数

```javascript
/表达式/[switch]
```

switch(也称为修饰符)按照什么样的模式来匹配.有三种值:

- g:全局匹配
- i:忽略大小写
- gi:全局匹配+忽略大小写

```html
 <textarea name="" id="" cols="30" rows="10"></textarea> <button type="button">提交</button>
    <div></div>
    <script>
        var text = document.querySelector("textarea");
        var btn = document.querySelector("button");
        var div = document.querySelector("div");
        btn.onclick = function () {
            // div.innerHTML = text.value.replace(/激情|gay/, '**'); // 只会替换第一个被检查的值
            div.innerHTML = text.value.replace(/激情|gay/g, '**');
        }
    </script>
```

