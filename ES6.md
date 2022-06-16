# 第1章，ECMASript 相关介绍

## 1.1 什么是ECMASript

ES全称EcmaScript，是脚本语言的规范，而平时经常编写的JavaScript，是EcmaScript的一种实现，所以ES新特性其实指的就是JavaScript的新特性

ECMA (European Computer Manufacturers Association)中文名称为欧洲计算机制造商协会，这个组织的目标是评估、开发和认可电信和计算机标准。1994年后该组织改名为Ecma国际。

## 1.2 什么是ECMAScript

ECMAScript是由Ecma国际通过ECMA 262标准化的脚本程序设计语言。

## 1.3 什么是ECMA-262

Ecma国际制定了许多标准，而ECMA-262只是其中的一个，所有标准列表查看

http://www.ecma-international.org/publications/standards/Standard.htm

## 1.4. ECMA-262历史

ECMA-262 (ECMAScript) 历史版本查看网址

http://www.ecma-international.org/publications/standards/Ecma-262-arch.htm

| 第1版   | 1997年             | 制定了语言的基本语法                                         |
| ------- | ------------------ | ------------------------------------------------------------ |
| 第2版   | 1998年             | 较小改动                                                     |
| 第3版   | 1999年             | 引入正则、异常处理、格式化输出等。IE开始支持                 |
| 第4版   | 2007年             | 过于激进，未发布                                             |
| 第5版   | 2009年             | 引入严格模式、JSON,扩展对象、数组、原型、字符串、日期方法    |
| 第6版   | 2015年             | 模块化、面向对象语法、Promise、箭头函数、let.const.数组解构赋值等等 |
| 第7版   | 2016年             | 幂运算符、数组扩展、Async/await关键字                        |
| 第8版   | 2017年             | Async/await、字符串扩展                                      |
| 第9版   | 2018年             | 对象解构赋值、正则扩展                                       |
| 第10版  | 2019年             | 扩展对象、数组方法                                           |
| ES.next | 动态指向下一个版本 |                                                              |

**注:从ES6开始，每年发布一-个版本，版本号比年份最后一位大1**

## 1.5.谁在维护ECMA-262

TC39 (Technical Committee 39)是推进ECMAScript 发展的委员会。其会员都是公司(其中主要是浏览器厂商，有苹果、谷歌、微软、因特尔等)。TC39定期召开会议，会议由会员公司的代表与特邀专家出席

## 1.6.为什么要学习ES6

- ES6 的版本变动内容最多，具有里程碑意义
- ES6加入许多新的语法特性，编程实现更简单、高效
- ES6是前端发展趋势，就业必备技能

## 1.7 ES6兼容性

http://kangax.github.io/compat-table/es6/ 可查看兼容性

# 第二章.ES6新语法

## 2.1 let和const命令

### 1.**let声明变量的规则**

> 特性

- 变量不能重复使用

  ```javascript
  let star = '罗志祥';
  let star = '小猪'; // 报错error 用var不会报错
  ```

  let声明的变量不能重复声明   但是var就没有这个问题

- let有块级[作用域](https://so.csdn.net/so/search?q=作用域&spm=1001.2101.3001.7020)

  ```javascript
  {
      //if for else while
      let girl='周扬青'
  }
  console.log(girl) // 报错error 因为拿不到
  ```

  在代码块内有效，出代码块无效，不仅仅针对花括号，例如对象的{}不属于块级作用域，像for(){},if(){},else{}，try{},cath(){}等等的花括号才是块级作用域

  let 是块级作用域  全局 函数 eval  但是var则是全局变量

  这里的块级作用域是指 if else while for 等{}中的作用域

- 不存在变量提前

  ```javascript
  console.log(song);  // 报错error 报错error
  let song='恋爱达人';
  ```

  let 定义的变量,不存在变量提升  但是var可以，如果是var定义的话则会显示undefined

- 不影响作用域链

  ```javascript
  {
     	let school='abc'; // 虽然是块级作用域，但是不能使用school这个变量
  	function fn(){
      console.log(school); //abc 他会向上一级的作用域里找school
  };
  fn(); // 可以拿到
  }
  ```

- 声明的变量具有暂时性死区

  ```javascript
    var num = 10;
          if (true) {
              console.log(num); // 这里的num与var 声明的num没有关系
              let num = 20;
          }
  ```

> 案列：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <div>
        <div class="item" style="width: 50px;height: 50px;background-color: red"></div>
        <div class="item" style="width: 50px;height: 50px;background-color: red"></div>
        <div class="item" style="width: 50px;height: 50px;background-color: red"></div>
    </div>
    <script>
        let items=document.getElementsByClassName("item");
        for (var i=0;i<items.length;i++){
            items[i].onclick=function (){
                items[i].style.backgroundColor='pink';
            }
        }
        console.log(window.i)  //3 
        // 当var=3的时候，点击事件开始向外层作用域找，找不到，就是window.i，此时是3，如果是let i，具有块级作用域，所以每一次触碰事件的i都是不同的。
    </script>
</body>
</html>
```

**经典面试题** var声明的变量

```javascript
 // var arr = [];
		// 此时的var声明的变量i属于函数作用域，声明又不在函数里，所以i属于全局变量
        // for (var i = 0; i < 2; i++) {
        //     arr[i] = function () {
        //         console.log(i); // 此时的函数属于异步函数，for循环已经循环结束，全局变量i已经为2
        //     }
        // };

        // arr[0]();
        // arr[1]();


        var arr = [];
        for (var i = 0; i < 2; i++) {
            arr[i] = (function () {
                console.log(i); // 立即执行函数 是同步操作
            })()
        };
```

![image-20220508141501097](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220508141501097.png)

经典面试题图解:此题的关键点在于变量i是全局的，函数执行时输出的都是全局作用域下的值。

let 声明的变量

```javascript
 let arr = [];
        for (let i = 0; i < 2; i++) {
            arr[i] = function () {
                console.log(i);
            }
        };
        arr[0]();
        arr[1]();
```

![image-20220508145732759](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220508145732759.png)

经典面试题图解:此题的关键点在于每次循环都会产生一个块级作用域， 每个块级作用域中的变量都是不同的,
函数执行时输出的是自己上一级(循环产生的块级作用域)作用域下的值.

### 2.const

一般在定义数组 或是 对象时都定义为const形式，防止误改、数据污染

> 特性

- 声明常量

  ```javascript
  const A = 'abc';
  ```

  1. const 是声明和定义常量的，一定要赋初始值

  2. 一般常量使用大写（潜规则）

  3. 常量的值(内存地址)不能修改

     ```javascript
     if (true) {
                 const a = 3.14;
                 // a = 3.15158;
                 // 普通数据是直接不能修改的 
                 // console.log(a); // 报错 常来的值(内存地址)不能修改
             }
             // console.log(a); // 报错 const关键字也有块级作用域
   
             const arr = [100, 200];
           arr[0] = 123;
             console.log(arr); // 对于复杂数据类型 里面的值可以被修改 因为这样没有修改常量地址
             // arr = [1, 2]; 重新赋值是不行的  更改了常量值对应的地址 这个操作不被允许的
             const o = {
                 name: 'andy',
                 age: 18
     
             };
             o.name = '刘师';
             console.log(o); // 对于复杂数据类型 里面的值可以被修改
     
     ```
  
  4. 也具有块级作用域
  
     ```javascript
     {
         const pyaler = 'uzi'
     }
     console.log(player) // error 拿不到
     ```
  
  5. 对于数组和对象的元素修改，不算作对常量的修改。
  
     简单数据类型，const声明的变量保存的值就是变量的值，是不可以修改，但如果是复杂数据类型(对象，数组等）const只是保存的是复杂数据类型的地址，只是确保地址不可变，但地址指向的内容是可以变的
  
     ```javascript
     const team = ['uzi','MXLG','Ming','Letme'];
     team.push('Meiko'); //不报错，常量地址没有发生变化
     ```

## 2.2 let、const、var的区别

1. 使用var声明的变量，其作用域为该语句所在的函数内，且存在变量提升现象。
2. 使用let声明的变量，其作用域为该语句所在的代码块内，不存在变量提升。
3. 使用const声明的是常量，在后面出现的代码中不能再修改该常量的值。

| var          | let            | const          |
| ------------ | -------------- | -------------- |
| 函数级作用域 | 块级作用域     | 块级作用域     |
| 变量提升     | 不存在变量提升 | 不存在变量提升 |
| 值可更改     | 值可更改       | 值不可更改     |

## 2.3 变量的解构赋值

ES6 允许按照一定模式从数组和对象中提取值，按照对应位置，对变量进行赋值。这被称为解构赋值。

### 1.数组的解构

```javascript
// 数组解构允许我们按照yiyi对应的关系从数组中提取值，然后将值赋值给变量
const F4 = ['小沈阳', '赵四', '刘能','宋小宝'];
// let [];数组的解构 从数组里面提取值
let [xiao, zhao, liu, song, a, b] = F4;
console.log(xiao); 
console.log(zhao);
console.log(liu);
console.log(song); // 值是一一对应的
console.log(a); // undefined 没有对应的值 就为undefined
console.log(b); // undefined 没有对应的值 就为undefined
```

### 2. 对象的解构

```javascript
// 1.对象解构允许我们使用变量的名字匹配对象的属性，匹配成功将对象属性的值赋值给变量		
		const zhao = {
            name: "赵本山",
            age: "18",
            xiaopin: function () {
                console.log("我会演小品");
            }
        }
        // console.log(zhao.age); 以前这样调用的

        let { name, age, xiaopin } = zhao;
        console.log(name);
        console.log(age);
        console.log(xiaopin);
        xiaopin();

		// 2.name: 匹配zhao里面的name属性 匹配完成后 ’赵本山’赋值给myName
		 let { name: myName, age: myAge, xiaopin: myXiaopin } = zhao; 
        console.log(myName);
        console.log(myAge);
        console.log(myXiaopin);
        myXiaopin();
```

## 2.4 String的扩展方法

### 模板字符串

> 特性

1. 声明变量为字符串类型 ''  ""  ``

   ```javascript
   let str = `我也是一个字符串哦!`;
   console.log(str, typeof str);
   ```

2. 内容中可以直接出现换行符

   ```javascript
    		// let str = '<ul>'
           //     + '<li>沈腾</li>'
           //     + '<li>玛丽</li>'
           //     + '<li>魏翔</li>'
           //     + '<li>艾文</li>'
           //     + '</ul>';  // 用'' 和 "" 声明字符串方法 内容中不能直接换行， 必须采取字符串拼接
   
            let str = `<ul>
                <li>沈腾</li>
                <li>玛丽</li>
                <li>魏翔</li>
                <li>艾文</li>
                </ul>`;  // 这是在内容里面直接换行 不会报错
   ```

3. 变量拼接

   ```javascript
   // let str = '罗志祥';
           // let out = str + '是可耻的!';
           // console.log(out); // 以前的字符串拼接
   		
   		// 解析变量
           let str = `罗志祥`;
           let out = `${str}是可耻的!`;
           console.log(out);
   ```
   
4. 调用函数

   ```javascript
    let fn = () => {
               return '我是fn函数';
           };
           let gerrt = `刘师你好! ${fn()}`;
           console.log(gerrt);
   ```

### 实例方法：startsWith() 和 endsWith()

- startsWith(): 表示参数字符串是否在原字符串的头部，返回布尔值
- endsWith():  表示参数字符串是否在原字符串的尾部，返回布尔值

```javascript
		let str = 'Hello ECMAScript 2015';
        let s1 = str.startsWith('Hello');
        console.log(s1);
        let s2 = str.endsWith('2015');
        console.log(s2);
```

### 实例方法：repeat()

repeat方法表示将原字符串重复n次，返回个新字符串。

```javascript
  	let str = 'hello';
    let str1 = str.repeat(5);
    console.log(str1);
```

## 2.5 对象的简化写法

> 介绍

ES6允许在大括号里面，直接写入变量和函数，作为对象的属性和方法,这样的书写更加简洁

> 特性

```javascript
let name = '特战荣耀';
        let Watch = function () {
            console.log('每晚记得去看!');
        };
		
        const tv = {
            name,
            Watch, //可以直接写变量名，不用再写值了
            // 等同于 name: name, Watch: Watch
            inprove() {
                console.log('太精彩了');
            }
            // 旧的方法定义
            // inprove: function() {
            // 		console.log('太精彩了');
            // }
        }
```

## 2.6 箭头函数

> 介绍

ES6允许使用箭头（=>）定义函数

```javascript
// 声明一个函数
let fn = function() {
    
}
// 箭头函数声明一个函数
let fn = (a, b) => {
    return a + b;
};
// 调用函数
 let result = fn(1,2);
 consloe.log(result);
```

> 特性

1. 箭头函数的this是静态的，this始终指向函数声明时所在作用域下的this的值。箭头函数不绑定this关键字，箭头函数中的this，指向的是函数定义位置的上下文this。

   ```javascript
    function getName() {
               // name是window对象的name，直接调用的话 this值指向window
               console.log(this.name);
           };
   
           let getName2 = () => {
               // 这个箭头函数是在全局作用域下声明的，所以this也是指向window
               console.log(this.name);
           }
           // 设置 window 对象的 name属性
           window.name = "中华田园犬";
           const quality = {
               name: "smallDog"
           }
           // 直接调用
           getName(); // name是 中华田园犬，直接调用的话 this指向window
           getName2(); // 而箭头函数是在全局作用域下声明的，所以this也是指向window
   
           // call方法调用
           getName.call(quality); // 此时普通函数this的值已经变为quality
           getName2.call(quality); // 输出 中华田园犬，因为它的this依然指向函数getname2声明时所在作用域下的this的值 window.name = '中华田园犬'
   
   ```

   ```javascript
   // const obj = { name: 'andy' };
           // function fn() {
           //     console.log(this); 
           //     return () => {
           //         console.log(this); // 箭头函数不绑定this，箭头函数没有自己的this 如果在箭头函数中使用this this关键字将指向箭头函数定义位置的this
           //     }
           // };
           // var resfn = fn.call(obj);
           // resfn();
   
           var age = 100;
           var obj = { // 对象不能产生作用域
               age: 20,
               say: () => { // say方法是被定义在全局作用域下 箭头函数的this就是指向的window
                   alert(this.age); // 100
               }
           };
           obj.say();
   ```

2. 箭头函数不能作为构造实例化对象

   ```javascript
   let Person = (name, age) => {
       this.name = name,
           this.age = age
   }
   
   let me = new Person("xiao", 18);
   console.log(me);
   ```

3. 不能使用arguments变量

   ```javascript
   // argumennts: 用来保存实参的
   let fn = () => {
   	console.log(arguments);
   }
   fn(1,2,3); // 会报错， 不用 用来保存实参
   ```

4. 箭头函数的缩写

   1）省略小括号， 当形参有且只有一个的时候

   ```javascript
   let add = (n) => {
   	return n + n;
   }
   console.log(add(3));
   ```

   2) 省略花括号，当代码体只有一条语句的时候，此时return 必须省略

   而且预计的执行结果就是函数的返回值

   ```javascript
   let pwd = (n) => n * n;
   console.log(pwd(3));
   ```

### 案列1：点击div, 让div在2秒之后变成天蓝色。

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        #ad {
            width: 200px;
            height: 200px;
            background-color: pink;
        }
    </style>
</head>

<body>
    <div id="ad"></div>
    <script>
        let ad = document.getElementById("ad");
        // 之前是这样使用的
        // ad.addEventListener("click", function () {
        //     let _this = this; // 声明一个变量把this的值保存起来
        //     setTimeout(function () {
        //         // console.log(_this);
        //         _this.style.backgroundColor = 'skyblue'; // 向外层作用域找_this      作用域链
        //     }, 2000)
        // });

        ad.addEventListener("click", function () {
            setTimeout(() => {
                // this指向的是 点击事件的值 点击事件的事件源是 #id
                this.style.backgroundColor = "skyblue";
            }, 2000);
        });

    </script>
</body>

</html>
```

### 案列2：从数组中返回偶数的元素

```javascript
const arr = [1, 45, 1388, 36, 1024];
        // const result = arr.filter(function (item) {
        //     if (item % 2 === 0) {
        //         return true;
        //     } else {
        //         return false;
        //     }
        // });

        const result = arr.filter(item => item % 2 === 0);

        console.log(result);
```

## 2.7 箭头函数注意事项

1. 箭头函数适合与this无关的回调，比如定时器，数组的方法回调。
2. 箭头函数适合与this无关的回调，比如定时器，数组的方法回调。

```javascript
btn.addEventListener("click", function(){
    //此时普通函数的this指向事件源
    //如果使用箭头函数，事件源将变成外部作用域的this值，即这个函数所在的作用域
})
```

## 2.8 函数参数默认值

> 介绍

ES6允许给函数参数赋值初始值

> 特性

1. 可以给形参赋初始值，一般位置要靠后（潜规则）

   ```javascript
   		// ES6 允许给函数参数赋初始值
           // 1.形参初始值 具有默认值的参数， 一般位置要靠后(潜规则)
           
           function add(a, b, c = 10) {
               return a + b + c;
           };
           // 形参有3个，当实参只有两个值的时候，就可以使用形参的初始值
           // 形参有3个，当实参有三个值的时候，就使用实参里面的值
   		// 传了实参的值就用实参的值， 如果没有传递实参的值，就默认使用函数参数的初始值
           let result = add(1, 2); 
           console.log(result);
   ```

2. 与解构赋值结合

   ```javascript
           // function connect(options) {
           //     let host = options.host;
           //     let username = options.username;
           // };
   		// 解构赋值，不用考虑顺序的，只要传的属性同名就可以
           function connect({ host= ’127.0.0.1’, username, password, port }) {
               console.log(host);
               console.log(username);
               console.log(password);
               console.log(port);
           }
           connect({
               // host: 'localhost',
               username: 'root',
               password: 'root',
               port: 3306
           });
   ```

## 2.9 rest参数(剩余参数)

> 介绍

ES6引入rest参数，用于获取函数的实参，用来代替arguments，语法允许我们将一个不定数量2的参数表示为一个数组。

> 特性

```javascript
         // ES5 获取实参的方式
         function data() {
             console.log(arguments); // 输出的是一个对象
         }
         data('周杰伦', '侯佩岑', '蔡依林', '昆凌'); 
```

```javascript
// rest 参数
        function data(...args) {
            console.log(args); // 输出的是一个数组，可以使用filter some every map等方法
        }
        data('周杰伦', '侯佩岑', '蔡依林', '昆凌'); // 数组

```

```javascript
// rest参数 必须要放到参数最后
        function fn(a, b, ...args) {
            console.log(a);
            console.log(b);
            console.log(args);
        }
        fn(1, 2, 3, 4, 5, 6);
```

```javascript
// 剩余参数和解构配合使用
 let stars = ['周杰伦', '侯佩岑', '蔡依林', '昆凌'];
        let [s1, ...s2] = stars; // ...s2 接收剩余的参数 结果为数组
        console.log(s1);
        console.log(s2);
```

```javascript
const obj1={
    q:'zzl'
}
const obj2={
    s:'wxl'
}
const data={...obj1, ...obj2}; //相当于合并了两个对象
console.log(data);//{q:'zzl',s:'wxl'}
```

## 2.10 扩展运算符(展开语法)

> 介绍

扩展运算符是能将数组转换为逗号分隔的参数序列，(扩展运算符和rest参数很像，但是rest的<...>是在函数的<形参>中，扩展运算符是在调用函数的<实参>里)

> 特性

```javascript
// [...] 扩展运算符能将 【数组】转换为逗号分隔的 【参数序列】
        // 声明一个数组 ... 
        const TfBoys = ['易烊千玺', '王源', '王俊凯'];
        // => '易烊千玺', '王源', '王俊凯'

        // 声明一个函数
        function chuanwan() {
            console.log(arguments);
        }

        // chunwan(TfBoys); // 不用扩展运算符  只输出一个结果，是一个数组
         chuanwan(...TfBoys); // 用扩展运算符 输出3个结果，相当于chunwan('易烊千玺', '王源', '王俊凯')即参数序列
```

> 应用

1. 数组的合并

   ```javascript
   // 方法一
   		 const kuaizi = ['王太利', '肖央'];
            const fenghuang = ['增益', '零花'];
            const zuixuanxiaopingguo = [...fenghuang, ...kuaizi]; // 相当于 let zuixuanxiaopingguo = ['增益', '零花', '王太利', '肖央'];
           // console.log(arr3);
            console.log(zuixuanxiaopingguo);
   // 方法二 
   		const kuaizis = ['王太利', '肖央'];
           const fenghuangs = ['增益', '零花'];
   		kuaizi.push(...fenghuang);
   		console.log(kuaizi);
   ```

2. 数组的克隆

   如果数组里面有引用类型的话，扩展呢运算符也只是浅拷贝。

   ```javascript
    		 const sanzhihua = ['B', 'G', 'M'];
            const sanyecao = [...sanzhihua];
            console.log(sanyecao);
   ```

3. 将伪数组转为真正的数组

   ```javascript
    		 const divs = document.querySelectorAll('div');
            const divdata = [...divs];
            console.log(divdata);
   ```

## 2.11 Array的扩展方法

### **1.构造函数方法：Array.from()**

将类数组或可遍历对象转换为真正的数组

```javascript
const ArrayLike = {
     "0": 1,
     "1": 2,
     "length": 2
   };

   let arr2 = Array.from(ArrayLike);

   console.log(arr2); 
```

方法还可以接受第二个参数，作用类似于数组的map方法，用来对每个元素进行处理，将处理后的值放入返回的数组。

```javascript
 const ArrayLike = {
            "0": 1,
            "1": 2,
            "length": 2
        };

        // let arr2 = Array.from(ArrayLike, (item) => {
        //     return item * 2;
        // });
        // 函数简写 因为只有一个参数 可以去掉小括号 而且返回的值也是函数本身的值 所以去掉大括号
        let arr2 = Array.from(ArrayLike, item => item * 2); // 对数组中的元素加工处理 数组中有多少元素 函数就调用几次
        console.log(arr2);
```

### 2.实例方法：find()

用于找出第一个符合条件的数组成员, 如果没有找到返回undefined

```javascript
 const ary = [{
            id: '1',
            name: '张三'
        }, {
            id: '2',
            name: '李四'
        }, {
            id: '3',
            name: '王麻子'
        }];

        // item 是数组循环到当前的值 index是循环当前的索引号
        // ary.find((item, index) => {
        //     console.log(item);
        //     console.log(index);
        // });

        let arr2 = ary.find(item => item.id == 2);

        console.log(arr2);
```

### 3.实例方法：findIndex()

用于找出第一个符合条件的数组成员的位置，如果没有找到返回-1

```javascript
 const arr1 = ['10', '20', '30'];
        let arr2 = arr1.findIndex(value => value > 31);
        console.log(arr2);
```

### 4.实例方法：includes()

表示某个数组是否包含给定的值，返回布尔值。

```javascript
		const arr = ['a', 'b', 'c'];
        let arr2 = arr.includes('a');
        console.log(arr2); // true
```

## 2.12 Symbol基本使用

**javaScript的七种数据类型记忆口诀：**

```
USONB     you are so niubility
U: undefined
S: Symbol String
O: Object
N: null number
B: boolean
```

### 1.Symbol基本使用

> 介绍

ES6 引入了一种新的原始数据类型Symbol， 表示独-一无二的值。它是JavaScript语言的第七种数据类型，是一种类似于字符串的数据类型。

**Symbol特点**

1. Symbol的值是唯一的，用来解决命名冲突的问题
2. Symbol 值不能与其他数据进行运算
3. Symbol 定义的对象属性不能使用for..in 循环遍历，但是可以使用Reflect.ownKeys来获取对象的所有键名

> 特性

1. 创建

   ```javascript
   // let s = Symbol();
           // console.log(s, typeof Symbol()); // Symbol() 'symbol'
           
   // 1.Symbol的两种创建方式
           let s1 = Symbol("1");
           let s2 = Symbol("1");
           console.log(s1 === s2);  // false
   
           let s3 = Symbol.for("11");
           let s4 = Symbol.for("11");
           console.log(s3 === s4); // true
   ```

2. 不能与其他数据进行运算

   ```javascript
   // let result = s + 100; 报错
           // let result = s * 3; 报错
           // let result = s + '1000'; 报错
           // let result = s + s; 报错
   ```

3. Sybmol内置值

   ```javascript
   class Person {
       static [Symbol.hasInstance](param){
           console.log(param);
           console.log("我被用来检测了")；
           return false;
       }
   }
   let o = {};
   console.log(o instanceof Person); //我被用来检测了，false
   ```

   

> 应用

Symbol的作用：表示独一无二的值，给对象添加属性和方法

```javascript
// 向对象中添加方法 up down
        let game = {
            // 假如有很多代码很多变量名
            name: '俄罗斯方块'
        }

        // 声明一个对象
        let methods = {
            // Symbol保证了up和down的属性名是独一无二的，
            // 所以添加进去也不怕有属性名冲突
            up: Symbol(),
            down: Symbol()
        };

		// 第一种添加方式
		// 把这个Symbol添加到game方法中
        game[methods.up] = function () {
            // 安全的向这个对象中添加了两个方法
            console.log("我可以改变形状");
        };

        game[methods.down] = function () {
            console.log("我可以下降");
        };

        console.log(game);

		// 第二种添加方式
		let youxi = {
            name: "狼人杀",
            [Symbol("say")]: function () {
                console.log("我会发言");
            },
            [Symbol("zibao")]: function () {
                console.log("我会自爆");
            }

        }
        console.log(youxi);
```

### 2.Symbol 内置值

除了定义自己使用的Symbol 值以外，ES6 还提供了11 个内置的Symbol值，指向语言内部使用的方法。

| Symbol.hasInstance        | 当其他对象使用instanceof 运算符，判断是否为该对象的实例时，会调用这个方法 |
| ------------------------- | ------------------------------------------------------------ |
| Symbol.isConcatSpreadable | 对象的SymbolisConcatSpreadable属性等于的是一个布尔值，表示该对象用于Array.prototype.concat()时，是否可以展开。 |
| Symbol.unscopables        | 该对象指定了使用with关键字时，哪些属性会被with环境排除。     |
| Symbol.match              | 当执行st.math(myObject)时，如果该属性存在，会调用它，返回该方法的返回值。 |
| Symbol.replace            | 当该对象被str.replace(myObject)方法调用时，会返回该方法的返回值。 |
| Symbol.search             | 当该对象被str. search (myObjec)方法调用时，会返回该          |
| Symbol.split              | 当该对象被str. split (myObject)方法调用时，会返回该方法的返回值。 |
| Symbol.iterator           | 对象进行for..of循环时，会调用Symbol.iterator 方法,返回该对象的默认遍历器 |
| Symbol.toPrimitive        | 该对象被转为原始类型的值时，会调用这个方法，返回该对象对应的原始类型值。 |
| Symbol. toStringTag       | 在该对象止面调用toString 方法时，返回该方法的返回值          |
| Symbol.species            | 创建衍生对象时，会使用该属性                                 |

```javascript
// 跟构造函数一样的效果 来实例化对象的
        // class Person {
        //     static [Symbol.hasInstance](param) {
        //         console.log('我被用来检测类型了');
        //         return false;
        //     }
        // }

        // let o = {};
        // instanceof 前面的值传递给param这个方法 由param这个方法确定返回的值
        // console.log(o instanceof Person)  ;

        const arr = [1, 2, 3];
        const arr1 = [4, 5, 6];
        arr1[Symbol.isConcatSpreadable] = false; // 控制数组可以展开否
        console.log(arr.concat(arr1)); // concat方法做数组合并的
```

```javascript
		const title1 = Symbol("title");
        const title2 = Symbol("title");
        const info = {
            [title1]: 'zzl',
            [title2]: 'wxl'
        }
        console.log(info);
```

Symbol有很多内置方法

## 2.13 迭代器

迭代器(Iterator)是一种接口,为各种不同的数据结构提供统一的访问机制。任何数据结构只要部署**Iterator 接口**(在js里面这个接口就是对象里面的一个属性，属性的名字叫Symbol.iterator，也可以自己对结构进行布置iterator接口。)，就可以完成遍历操作。

1) ES6 创造了一种新的遍历命令f.r..of循环，Iterator接口主要供fr...of消费

2)原生 具备iterator接口的数据(可用for of遍历)

​	a) Array

​	b) Arguments

​	c) Set

​	d) Map

​	e)String

​	f) TypedArray

​	g) NodeList

3)工作原理

​	a) 创建一个指针对象，指向当前数据结构的起始位置

​	b)第一次调用对象的next方法，指针自动指向数据结构的第--一个成员

​	c) 接下来不断调用netx方法，指针一直往后移动，直到指向最后-一个成员

​	d)每调用next方法返回一个包含value和done属性的对象

**注: 需要自定义遍历数据的时候，要想到迭代器。**

```javascript
 const xiyou = ['唐僧', '孙悟空', '猪八戒', '沙僧'];
        // console.log(xiyou); // xiyou里面有Symbol.iterator这个属性
        // 使用 for...of 遍历数组 (v存储的是键值)
        // for (let v of xiyou) {
        //     console.log(v);
        // };

        // 使用 for...in 遍历数组 (v存储的是键值)
        // for (let v in xiyou) {
        //     console.log(v);
        // };

        let iterator = xiyou[Symbol.iterator]();

        // 调用对象的next方法
        console.log(iterator.next());
        console.log(iterator.next());
        console.log(iterator.next());
        console.log(iterator.next());
        console.log(iterator.next());
```

> 手写迭代器

```javascript
 const data = {
            name: 'zzl',
            lis: [
                'wxl',
                'll',
                'hll'
            ],
            //自己给某些结构加上iterator接口
            [Symbol.iterator]() {
                //索引变量
                let index = 0;
                let _this = this;
                return {//返回一个指针对象，即创建一个指针对象
                    next: function () { //创建对象的next方法
                        // 返回一个包含value和done属性（是否完成）的对象
                        if (index < _this.lis.length) {   // (这里也可以使用箭头函数 就不需要接this过来)
                            const result = { value: _this.lis[index], done: false };
                            index++;
                            return result;
                        } else {
                            return { value: undefined, done: true };
                        }
                    }
                };
            }
        }
        //自定义遍历这个对象
        for (let v of data) {
            console.log(v);
        }
        console.log('--------------------')
        console.log(data);

```

### 数组的常用方法

#### 1.forEach

 缺点：找到目标还会继续循环，并且不受return和break的影响。

```javascript
 const arr = ['pink', 'red', 'skyblue', 'hotpink'];
        arr.forEach((value) => {
            if (value == 'skyblue') {
                console.log('找到该元素');
                return true;
            }
            console.log('11');
        })  
```

#### 2.some

找到目标后，可以通过return结束循环。

```javascript
const arr = ['pink', 'red', 'skyblue', 'hotpink'];
        arr.some((value) => {
            if (value == 'skyblue') {
                console.log(value);
                return true;
            }
            console.log('11');
        })
```

#### 3.every

只要每一项都满足every里面的判断条件，则最终返回true。

```javascript
const arr = [{
            id: 1,
            state: true
        }, {
            id: 2,
            state: true
        }];
		// 判断数组中的所有state是否都为true
        const A = arr.every(item => item.state);
        console.log(A);
```

#### 4.filter

filter会把满足条件的数据重新过滤到的新数组中。

```javascript
 const arr = ['pink', 'red', 'skyblue', 'hotpink'];
        const a = arr.filter((value) => {
            if (value == 'skyblue') {
                console.log('找到该元素');
                return true;
            }
            console.log('11');
        });
        console.log(a); // ['skyblue']
```

#### 5.reduce

```javascript
arr.filter(item=>item.state).reduce(累加的结果，当前循环项)=>{ },初始值)
```

第一次循环累加的结果默认等于初始值，以后循环累加的结果等于上一次累加的结果加上循环项里的数据。

```javascript
const arr = [{ id: 1, state: true, price: 10 }]
        let sum = 0;
        arr.filter(item => item.state).reduce((sum, item) => {
            return sum += item.price
            //return给下一次累加使用
        }, 0)
        console.log(sum);
```



### Set 数据结构

ES6提供了新的数据结构Set。它类似于数组,但是成员的值都是唯一的, 没有重复的值。
Set本身是一个构造函数，用来生成Set数据结构。

```javascript
const S = new Set() ;
```

Set函数可以接受一个数组作为参数, 用来初始化。

```javascript
const set = new Set([1, 2，3，4，4]);
```

利用Set数据结构数组去重

```javascript
 const s = new Set();
        console.log(s.size); //  实例对象下面有个size属性 size属性代表在当前数据结构当中存放了多少值

        const s1 = new Set(['a', 'b']);
        console.log(s1.size); // 2

        const s2 = new Set(['a', 'a', 'b', 'b']);
        console.log(s2.size); // 2 在我们向Set数据结构中 传递初始值的时候 会把重复的值过滤掉

        const arr = [...s2];
        console.log(arr); // 利用展开运算符将 将set数据结构转换 一个以逗号隔开的零散量
```

#### 实例方法

- add(value): 添加某个值,返回Set结构本身
- delete(value): 删除某个值,返回一个布尔值,表示删除是否成功
- has(value): 返回一个布尔值，表示该值是否为Set的成员
- clear(): 清除所有成员，没有返回值

```javascript
const S = new Set();
s.add(1).add(2).add(3); //向set结构中添加值
s.delete (2) // 删除set结构中的2值
s.has (1) //表示set结构中是否有1这个值 返回布尔值
s.clear() //清除set结构中的所有值
```

遍历
Set结构的实例与数组-样,也拥有forEach方法，用于对每个成员执行某种操作，没有返回值。

```javascript
s.forEach(value => console.1og(value))
```

## 2.14 生成器

生成器函数是ES6提供的一种异步编程解决方案，语法行为与传统函数完全不同，是一种特殊的函数

```javascript
 // 生成器就是一个特殊的函数 进行异步编程 以前我们用的纯回调函数
function* fun() {
            console.log('你好');
        };
        let a = fun();
        // console.log(a); // 输出一个迭代器对象(有next方法)
        a.next(); // 输出 '你好'
```

```java
function* fun() {
            console.log('你好');
            console.log('晚上好');
        };
        let a = fun();
        // console.log(a); // 输出一个迭代器对象(有next方法)
        a.next(); // 输出 '你好' '晚上好' 即全部输出
```

![image-20220511184347666](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220511184347666.png)

```javascript
function * fun() {
            console.log('你好');
            yield '我要暂停'
            console.log('晚上好');
        }
        let a = fun();
        // console.log(a);
        a.next(); // '你好'
```

```javascript
function * fun(){
     console.log('你好');
    yield '我要暂停'
    console.log('晚上好');
}
let a=fun();
// console.log(a);//输出一个迭代器对象（有next方法）
a.next();//输出 '你好'
a.next();//输出 ’晚上好’
```

```javascript
function * fun(){
    // console.log('你好');
    yield '我要暂停'
    // console.log('晚上好');
    yield '我要暂停一下'
}
let a=fun();
// console.log(a);//输出一个迭代器对象（有next方法）

// 遍历
for(let k of fun()){
    console.log(k);//我要暂停 我要暂停一下
}
```

```javascript
function * fun(){
   // console.log('你好');
    yield '我要暂停'
    // console.log('晚上好');
    yield '我要暂停一下'
}
let a=fun();
console.log(a.next()); //输出 {value: '我要暂停', done: false}
console.log(a.next()); //输出 {value: '我要暂停一下', done: false}
console.log(a.next()); //输出 {value: undefined, done: true}
```

### 生成器函数的参数传递

```javascript
function * fun(arg){
    console.log(arg);//输出aaa
    let one=yield 111;
    console.log(one);//输出bbb
    let two=yield 222;
    console.log(two);//输出ccc
    let three=yield 333;
    console.log(three);//输出ddd
};
  // 执行获取迭代器对象
let a=fun('aaa');
console.log(a.next());//第一次调用next
//next方法可以传入实参
//第二次调用next的实参将作为第一个yield的整体返回结果
console.log(a.next('bbb'))//输出{value: 222, done: false}
console.log(a.next('ccc'))//输出{value: 333, done: false}
console.log(a.next('ddd'))//输出{value:  undefined, done: false}
```

### 实例1：解决回调地狱问题

用生成器函数的方式解决回调地狱问题

```javascript
// setTimeout(() => {
//     console.log(111);
//     setTimeout(() => {
//         console.log(222);
//         setTimeout(() => {
//             console.log(333);
//         }, 3000);
//     }, 2000);
// }, 1000);

function one(){
    setTimeout(()=>{
        console.log(111);
        a.next();//定时器运行完调用下一个，实现了异步编程
    },1000)
}
function two(){
    setTimeout(()=>{
        console.log(222);
        a.next();
    },2000)
}
function three(){
    setTimeout(()=>{
        console.log(333);
        a.next();
    },3000)
}
function *fun(){
    yield one();
    yield two();
    yield three();
}
//调用生成器函数
let a=fun();
a.next();
```

### 实例2：模拟异步获取数据

```javascript
// 模拟获取 用户数据 订单数据 商品数据
        function getUsers() {
            setTimeout(() => {
                let data = '用户数据';
                // 调用next 方法，并将数据传入
                iterator.next(data);
            }, 1000);
        };

        function gerOrders() {
            setTimeout(() => {
                let data = '订单数据';
                iterator.next(data);
            }, 1000);
        };

        function getGoods() {
            setTimeout(() => {
                let data = '商品数据';
                iterator.next(data);
            }, 1000);
        };

        // 不能直接调用 不符合实际的场景  他们之间是有关联度的 现有用户 才能看到用户的订单信息 有了订单信息才能看商品信息 
        // 所以要按着先后顺序去走
        // getUsers();
        // gerOrders();
        // getUsers();

        function* gen() {
            let user = yield getUsers(); //用户数据 作为第一个yield的整体返回结果
            console.log(user);
            let order = yield gerOrders();
            console.log(order);
            let good = yield getGoods();
            console.log(good);
        };

        // 调用生成器函数
        let iterator = gen();
        iterator.next();
```

## 2.15 Promise

Promise是ES6引入的异步编程的新解决方案。语法上Promise是-一个构造函

数,用来封装异步操作并可以获取其成功或失败的结果。

1. Promise 构造函数: Promise (excutor) {}|
2. Promise.prototype.then 方法
3. Promise.prototype.catch 方法

```javascript
 // 在实例化里 接收一个参数 是一个函数类型的值  函数里面有两个形参 reslove reject
        const p = new Promise(function (reslove, reject) {
            setTimeout(function () {
                // let data = '数据库数据';
                // reslove(data); // 调用了reslove Promise对象的状态就会变成成功

                let data = '数据读取失败';
                reject(data); // 调用了reason Promise对象的状态就会变成失败
            }, 1000)
        });
        // Promise对象 有三个状态 1.初始化 2成功 3失败
        // 调用 reslove 和 reject 来改变 Promise对象的状态

        // 调用Promise 对象的 then方法
        // then方法接收两个参数 都是函数类型的值 每个函数都有一个形参 成功状态的形参 value 失败状态的形参 为reason
        p.then(function (value) {
            console.log(value); // 当我们的Promise对象的状态为成功 也就是异步任务里面调用了reslove then方法就会执行他第一个回调函数里面的代码
        }, function (reason) {
            console.error(reason); // 当我们的Promise对象的状态为失败 也就是异步任务里面调用了reason then方法就会执行他第二个回调函数里面的代码
        });

        // 总结： 我们把异步任务封装在Promise对象里面 利用reslove 和 reject 来改变 Promise对象的状态 改变状态后 利用then方法里面的回调 (当我们的Promise对象的状态为成功 也就是异步任务里面调用了reslove then方法就会执行他第一个回调函数里面的代码, 当我们的Promise对象的状态为失败 也就是异步任务里面调用了reason then方法就会执行他第二个回调函数里面的代码)
```

