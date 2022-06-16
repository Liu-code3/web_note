# 一、jQuery概述

## 1.jQuery概述

### 1.1 JavaScript库

仓库：可以把很多东西放到这个仓库里面，找东西只需要到仓库里面查找到就可以了。

**JavaScript库：**即library，是一个**封装**好的特定**的集合**(方法和函数)，从封装一大堆函数的角度理解库，就是在这个库中，封装了很多预先定义好的函数在里面，比如动画animate、hide、show，比如获取元素等。

简单理解: 就是一个JS 文件,里面对我们原生js代码进行了封装,存放到里面。这样我们可以快速高效的使用这些封装好的功能了。

比如jQuery ,就是为了快速方便的操作DOM ,里面基本都是函数(方法)。

**常见的JavaScript库**

- jQuery
- Prototype
- YUI
- Dojo
- Ext JS
- 移动端的zepto

这些库都是对原生JavaScript的封装，内部都是用JavaScript实现的，我们主要学习的是jQuery

### 1.2 JQuery的概念

jQuery是一个快速、简洁的JavaScript库,其设计的宗旨是"write Less , Do More”, 即倡导写更少的代码,做更多的事情。

j就是JavaScript; Query 查询;意思就是查询jis ,把js中的DOM操作做了封装,我们可以快速的查询使用里面的功能。

jQuery封装了JavaScript常用的功能代码,优化了DOM操作、事件处理、动画设计和Ajax交互。

学习jQuery本质:就是学习调用这些函数(方法)。

jQuery出现的目的是加快前端人员的开发速度,我们可以非常方便的调用和使用它,从而提高开发效率。

![image-20220410222038186](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220410222038186.png)

### 1.3 jQuery的优点

- 轻量级。核心文件才几十kb ,不会影响页面加载速度
- 跨浏览器兼容。基本兼容了现在主流的浏览器
- 链式编程、隐式迭代
- 对事件、样式、动画支持,大大简化了DOM操作
- 支持插件扩展开发。有着丰富的第三方的插件,例如: 树形菜单、日期控件、轮播图等
- 免费、开源

## 2.Jquery的基本使用

### 2.1 jQuery的下载

官网地址：https://jquery.com/

版本:

- 1x :兼容IE 678等低版本浏览器，官网不再更新
- 2x:不兼容IE 678等低版本浏览器，官网不再更新
- 3x :不兼容IE 678等低版本浏览器，是官方主要更新维护的版本

各个版本的下载: https://code.jquery.com/

### 2.2 jQuery的使用步骤

1. 引入jQuery文件
2. 使用即可

### 2.3 jQuery的入口函数

```javascript
$(function() {
	...   // 此处是页面DOM加载完成的入口
});
```

```javascript
$(document).ready(function() {
	... // 此处是页面DOM加载完成的入口
});
```

1. 等着DOM结构渲染完毕即可执行内部代码,不必等到所有外部资源加载完成, jQuery帮我们完成了封装。
2. 相当于原生js中的DOMContentLoaded
3. 不同于原生js中的load事件是等页面文档、外部的js文件、css文件、 图片加载完毕才执行内部代码。
4. 更推荐使用第一种方式。

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
            width: 400px;
            height: 200px;
            background-color: pink;
            margin: 100px auto;
        }
    </style>
</head>

<body>
    <script>
        // 1.等着页面DOM元素加载完毕 再去执行js   等同于原生js的load
        // $(document).ready(function () {
        //     $('div').hide();
        // });

        // 2.等着页面DOM元素加载完毕 再去执行js 等同于原生js的DOMContentLoaded 推荐使用这一种 
        $(function () {
            $('div').hide();
        });
    </script>
    <div></div>

</body>

</html>
```

### 2.4 jQuery的顶级对象 $

1. $是jQuery的别称,在代码中可以使用jQuery代替$ ,但一般为了方便,通常都直接使用$。
2. $是jQuery的顶级对象,相当于原生JavaScript中的window。把元素利用$包装成jQuery对象,就可以调用jQuery的方法。

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
            width: 400px;
            height: 200px;
            background-color: hotpink;
        }
    </style>
</head>

<body>
    <script>
        // 1.$ 也是jQuery的别称 (另外的名字)
        $(function () {
            $('div').hide();
        });

        // jQuery(function () {
        //     jQuery('div').hide();
        // });
        // 2. $ 也是jquery的顶级对象
    </script>
    <div></div>
</body>

</html>
```

### 2.5 jQuery对象和DOM对象

1. 用原生JS获取来的对象就是DOM对象
2. jQuery方法获取的元素就是jQuery对象。
3. jQuery对象本质是: 利用$对DOM对象包装后产生的对象(伪数组形式存储)。

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
     <!-- 记得引入jQuery库 -->
    <script src="./js/jQuery.min.js"></script>
    <title>Document</title>
    <style>
        div {
            width: 400px;
            height: 200px;
            background-color: skyblue;
        }
    </style>
</head>

<body>
    <div></div>
    <span>你好</span>
    <script>
        // 1.DOM对象 用原生js获取过来的对象就是DOM对象
        var MyDiv = document.querySelector('div');  // MyDiv 是DOM对象
        var MySpan = document.querySelector('span');  // MySpan 是DOM对象
        console.dir(MyDiv);

        // 2.jQuery对象： 用jQuery方式获取过来的对象是jQuery对象 本质： 通过$把2DOM元素进行了包装
        $('div'); // $('div') 是一个jQuery 对象
        $('span'); // $('span') 是一个jQuery 对象
        console.log($('div'));
        // 3.jQuery对象只能使用 jQuery方法， DOM对象则使用原生的javaScript 属性和方法
        MyDiv.style.display = 'none';  // MyDiv 是DOM对象 所以只能用原生js 的属性和方法
        $('div').hide();
    </script>
</body>

</html>
```

### 2.6 jQuery对象和DOM对象互相转换

DOM对象与jQuery对象之间是可以相互转换的。

因为原生js比jQuery更大,原生的一-些属性和方法jQuery没有给我们封装.要想使用这些属性和方法需要把jQuery对象转换为DOM对象才能使用。

1. DOM对象转换为jQuery对象: $(DOM对象)

   ```javascript
   (1) 直接获取就是 jQuery对象
   $('div');
   (2) 已经使用了原生js 获取过来的DOM对象 $(DOM对象)
   var div = document.querySelector('div');
   $(div); // 直接用$()包装DOM对象 就转换为jQuery对象
   ```

2. jQuery对象转换为DOM对象(两种方式)

   ```javascript
   $('div')[index]   // index是索引号 因为jQuery对象是伪数组形式存储的
   ```

   ```javascript
   $('div').get[index]  //index是索引号
   ```

**例**

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="./js/jQuery.min.js"></script>
    <title>Document</title>
</head>

<body>
    <video src="./video/xuanchuanpian.mp4" muted></video>
    <script>
        // 1.DOM对象转换为 jQuery对象
        // (1) 我们直接获取视频，得到的就是jQuery对象
        // $('video');

        // (2) 我们已经使用原生js 获取过来的 DOM对象
        var myVideo = document.querySelector('video');
        // $(myVideo);
        // $(myVideo).play();  jQuery里面没有play 这个方法 就使用不了

        // 2.jQuery 对象转换DOM对象
        // myVideo.play(); // 原生js的视频play()方法
        // (1)
        $('video')[0].play();
        // (2)
        $('video').get[0].play();
    </script>
    <div></div>

</body>

</html>
```

# 二、jQuery常用API

## 1. jQuery选择器

### 1.1 jQuery选择器

原生JS获取元素方式很多，很杂，而且兼容性情况不一致，因此jQuery给我们做了封装。使获取元素统一标准。

```javascript
$('选择器')  // 里面选择器直接写CSS选择器即可，但是要加引号
```

| 名称               | 用法            | 描述                                                         |
| ------------------ | --------------- | ------------------------------------------------------------ |
| ID选择器           | $('#id')        | 获取指定ID的元素                                             |
| 全选选择器(通配符) | $('*')          | 匹配所有元素                                                 |
| 类选择器           | $('.class')     | 获取同一类class的元素                                        |
| 标签选择器         | $('div')        | 获取同一类标签的所有元素                                     |
| 并集选择器         | $('div, p, li') | 选取多个元素                                                 |
| 交集选择器         | $('li.current') | 交集元素                                                     |
| 子代选择器         | $('ul > li')    | 使用>号，获取亲儿子层级的元素：注意，并不会获取孙子层级的元素 |
| 后代选择器         | $('ul li')      | 使用空格，代表后代选择器，获取ul下的所有li元素，包括孙子等   |

### 1.2 隐式迭代(重要)

jQuery隐式迭代是对同一类元素做了同样的操作。

遍历内部DOM元愫(伪数组形式存储)的过程就叫做**隐式迭代**。

简单理解:给匹配到的所有元愫进行循环遍历,执行相应的方法,而不用我们再进行循环,简化我们的操作,方便我们调用。

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <!-- 不要忘记引入jQuery -->
    <script src="./js/jQuery.min.js"></script>
    <title>Document</title>
</head>

<body>
    <div>意外不，惊喜不</div>
    <div>意外不，惊喜不</div>
    <div>意外不，惊喜不</div>
    <div>意外不，惊喜不</div>
    <ol>
        <li>1</li>
        <li>2</li>
        <li>3</li>
        <li>4</li>
    </ol>
    <ul>
        <li>a</li>
        <li>b</li>
        <li>c</li>
        <li>d</li>
    </ul>
    <script>
        // 1.获取四个div元素
        console.log('div');

        // 2.给四个div设置背景颜色为粉色 jQuery对象不能使用 style
        $('div').css('background', 'pink');

        // 3.隐式迭代就是把匹配的所有元素内部进行遍历循环，给每一个元素添加css这个方法
        $('ul li').css('color', 'red');
    </script>
</body>

</html>
```

### 1.3 jQuery筛选选择器

| 语法       | 用法          | 描述                                                      |
| ---------- | ------------- | --------------------------------------------------------- |
| :first     | $('li:first') | 获取第一个li元素                                          |
| :last      | $('li:last')  | 获取最后一个元素                                          |
| :eq(index) | $('li:eq(2)') | 获取到的li元素中，选择索引号为2的元素，索引号index从0开始 |
| :odd       | $('li:odd')   | 获取到的元素中，选择索引号为奇数的元素                    |
| :even      | $('li:even')  | 获取到的元素中，选择索引号为偶数的元素                    |

### 1.4 jQuery筛选方法(重点)

| 语法               | 用法                             | 说明                                                   |
| ------------------ | -------------------------------- | ------------------------------------------------------ |
| parent()           | $("li"). parent();               | 查找父级                                               |
| children(selector) | $("ul"). children("li");         | 相当于$("ul>li")，最近一级(亲儿子)                     |
| find(selector)     | $("ul"). find("li");             | 相当于$("ul li")，后代选择器                           |
| siblings(selector) | $(" . first").siblings("li");    | 查找兄弟节点，不包括自己本身                           |
| nextAll([expr])    | $(". first"). nextAll()          | 查找当前元素之后所有的同辈元素                         |
| prevtAll([expr])   | $(" .last"). prevAll()           | 查找当前元素之前所有的同辈元素                         |
| hasClass(class)    | $(' div').hasClass(" protected") | 检查当前的元素是否含有某个特定的类，如果有，则返回true |
| eq( index)         | $("li").eq(2);                   | 相当于$("1i:eq(2)"), index从0开始                      |
| parents("选择器")  | $("li").parents("ul")            | 查找当前子元素的所有父元素                             |
| :checked           | $("input:checked")               | 被选择的复选框                                         |

重点记住：parent() children() find() siblings() eq()

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="./js/jQuery.min.js"></script>
    <title>Document</title>
    <!-- <style>
        div {
            color: yellow;
        }
    </style> -->
</head>

<body>
    <ul>
        <li>春眠不觉晓，</li>
        <li>处处闻啼鸟。</li>
        <li class="item">夜来风雨声,</li>
        <li>花落知多少。</li>
    </ul>
    <ol>
        <li>鹅鹅鹅，</li>
        <li>曲项向天歌。</li>
        <li>白毛浮绿水，</li>
        <li>红掌拨清波。</li>
    </ol>
    <div class="current">春晓</div>
    <div>咏鹅</div>
    <script>
        // 注意 这都是方法  带括号
        $(function () {
            // 1.兄弟元素 siblings 除了自身元素之外的所有亲兄弟
            $('ul .item').siblings('li').css('color', 'red');

            // 2.第n个元素
            var index = 2;
            // (1) 利用选择器的方式选择
            // $('ol li:eq(2)').css('color', 'yellow');
            $('ol li:eq(' + index + ')').css('color', 'yellow');

            // (2) 利用选择方法的方式选择  更推荐这种写法
            // $('ul li').eq(2).css('color', 'hotpink');
            $('ul li').eq(index).css('color', 'hotpink');
            // 两种方法都是等价的 但是第二种更推荐 例 当索引号为变量的时候
        });
         // 3.判断是否有某个类名
        console.log($('div:first').hasClass('current'));  // true
        console.log($('div:last').hasClass('current'));  // false
    </script>
</body>

</html>
```



#### 案列：新浪下拉菜单

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!-- 不要忘记引入jQuery -->
    <script src="./js/jQuery.min.js"></script>
    <title>Document</title>
    <style>
        ul {
            list-style: none;
            padding-left: 0;
        }

        a {
            text-decoration: none;
        }

        .row {
            display: flex;
        }

        .row>li {
            margin: 0 20px;
        }

        .row>li>a {
            display: block;
            width: 100px;
            height: 40px;
            line-height: 40px;
            color: #000;
            text-align: center;
        }

        .clu {
            display: none;

        }

        .clu li {
            height: 40px;
            border: 1px solid #FF8200;
            border-top: none;
            text-align: center;
            line-height: 40px;
        }

        .clu li a {
            color: #000;
        }

        .clu li:hover {
            background-color: rgba(254, 197, 46, .2);
        }
    </style>
</head>

<body>
    <ul class="row">
        <li>
            <a href="#">微博</a>
            <ul class="clu">
                <li>
                    <a href="#">主页</a>
                </li>
                <li>
                    <a href="#">评论</a>
                </li>
                <li>
                    <a href="#">@我</a>
                </li>
                <li>
                    <a href="#">联系</a>
                </li>
            </ul>
        </li>
        <li>
            <a href="#">微博</a>
            <ul class="clu">
                <li>
                    <a href="#">主页</a>
                </li>
                <li>
                    <a href="#">评论</a>
                </li>
                <li>
                    <a href="#">@我</a>
                </li>
                <li>
                    <a href="#">联系</a>
                </li>
            </ul>
        </li>
        <li>
            <a href="#">微博</a>
            <ul class="clu">
                <li>
                    <a href="#">主页</a>
                </li>
                <li>
                    <a href="#">评论</a>
                </li>
                <li>
                    <a href="#">@我</a>
                </li>
                <li>
                    <a href="#">联系</a>
                </li>
            </ul>
        </li>
        <li>
            <a href="#">微博</a>
            <ul class="clu">
                <li>
                    <a href="#">主页</a>
                </li>
                <li>
                    <a href="#">评论</a>
                </li>
                <li>
                    <a href="#">@我</a>
                </li>
                <li>
                    <a href="#">联系</a>
                </li>
            </ul>
        </li>
    </ul>
    <script>
        $(function () {
            // 鼠标经过
            //  $('.row>li')  jQuery隐式迭代 .row>li 里面每个小li都绑定了 mouseover事件 (.row>li 这样是隐式迭代row里面的亲儿子 也就是就近一级子级元素)    相当于原生js循环绑定了li
            $('.row>li').mousemove(function () {
                // $(this) jQuery 当前元素  this不要加引号
                // show() 显示元素 hide()  隐藏元素
                $(this).children('a').css('backgroundColor', '#999');
                $(this).find('.clu').show();

            });
            // 鼠标离开
            $('.row>li').mouseout(function () {
                $(this).children('a').css('backgroundColor', '');
                $(this).find('.clu').hide();
            });
        })

    </script>
</body>

</html>
```

### 1.5 jQuery的排他思想

想要多选一的效果， 排他思想：当前元素设置样式，其余的兄弟清除样式

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!-- jQuery记得引入 -->
    <script src="./js/jQuery.min.js"></script>
    <title>Document</title>
</head>

<body>
    <button>点击变色</button>
    <button>点击变色</button>
    <button>点击变色</button>
    <button>点击变色</button>
    <button>点击变色</button>
    <button>点击变色</button>
    <button>点击变色</button>
    <script>
        // 这是原生js的排他思想
        // var btns = document.querySelectorAll('button');
        // console.log(btns);
        // for (var i = 0; i < btns.length; i++) {
        //     btns[i].addEventListener('click', function () {
        //         // 先清除所有的button的背景颜色
        //         for (var i = 0; i < btns.length; i++) {
        //             btns[i].style.backgroundColor = '';
        //         }
        //         // 然后留下当前点击的button按钮的背景颜色
        //         this.style.backgroundColor = 'pink';
        //     })
        // };

        // jQuery的排他思想
        // 第一个隐式迭代 给所有的button按钮都绑定了点击事件
        $('button').click(function () {
            // 当前点击的元素变化背景颜色
            $(this).css('backgroundColor', 'hotpink');
            // 第二个隐式迭代， 其余的兄弟去掉背景颜色 留下当前点击的元素为pink色
            $(this).siblings('button').css('background', '');
        });
    </script>
</body>

</html>
```

#### 案列：淘宝服饰精品案列

**淘宝服饰精品案列分析**

1. 核心原理:鼠标经过左侧盒子某个小li ,就让内容区盒子相对应图片显示,其余的图片隐藏。
2. 需要得到当前小li的索引号,就可以显示对应索引号的图片
3. **jQuery得到当前元素索引号$(this).index()**
4. 中间对应的图片,可以通过eq(index)方法去选择
5. 显示元素show0      隐藏元素hide0

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!-- jQuery记得引入 -->
    <script src="./js/jQuery.min.js"></script>
    <title>Document</title>
    <style>
        ul {
            list-style: none;
            margin: 0;
            padding: 0;
        }

        a {
            text-decoration: none;
        }

        .con {
            display: flex;
            width: 800px;
            height: 420px;
            margin: 100px auto;
        }

        .right {
            display: flex;
            flex-direction: column;
        }

        .right li {
            flex: 1;
            line-height: 57px;
            border: 1px solid skyblue;
        }

        .main {
            position: relative;
        }

        .main div a {
            display: block;
            width: 600px;
            height: 420px;
        }

        .main div a img {
            position: absolute;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;

        }
    </style>
</head>

<body>
    <div class="con">
        <ul class="right">
            <li>
                <a href="#">家电</a>
            </li>
            <li>
                <a href="#">零食</a>
            </li>
            <li>
                <a href="#">男装</a>
            </li>
            <li>
                <a href="#">女鞋</a>
            </li>
            <li>
                <a href="#">女装</a>
            </li>
            <li>
                <a href="#">手机</a>
            </li>
            <li>
                <a href="#">童装</a>
            </li>
        </ul>
        <div class="main">
            <div>
                <a href="#"><img src="./images/jiadian.webp" alt=""></a>
            </div>
            <div>
                <a href="#"><img src="./images/linshi.webp" alt=""></a>
            </div>
            <div>
                <a href="#"><img src="./images/nanzhuang.webp" alt=""></a>
            </div>
            <div>
                <a href="#"><img src="./images/nvxie.jpg" alt=""></a>
            </div>
            <div>
                <a href="#"><img src="./images/nvzhuang.jpg" alt=""></a>
            </div>
            <div>
                <a href="#"><img src="./images/shouji.webp" alt=""></a>
            </div>
            <div>
                <a href="#"><img src="./images/tongzhuang.jpg" alt=""></a>
            </div>
        </div>
    </div>
    <script>
        $(function () {
            // 1.鼠标经过左侧的小li
            $('.right li').mouseover(function () {
                $(this).siblings('li').css('backgroundColor', '');
                $(this).css('backgroundColor', 'pink');
                // $(this).index() 得到当前小li的索引号
                $('.main div').eq($(this).index()).siblings().hide();
                $('.main div').eq($(this).index()).show();

            });
            $('.right li').mouseout(function () {
                $(this).css('backgroundColor', '');

            });

        })

    </script>
</body>

</html>
```

### 1.6 链式编程

链式编程是为了节省代码量，看起来更优雅。、

```javascript
$(this).css('color', 'red').sibling().css('color','');
```

使用链式编程一定注意是哪个对象执行样式。先顺着一层一层往下找，一定要注意是哪个对象执行样式。

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="./js/jQuery.min.js"></script>
    <title>Document</title>
</head>

<body>
    woshi body font
    <button>按钮</button>
    <button>按钮</button>
    <button>按钮</button>
    <button>按钮</button>
    <button>按钮</button>
    <button>按钮</button>
    <button>按钮</button>
    <button>按钮</button>
    <button>按钮</button>
    <button>按钮</button>
    <script>
        $(function () {
            // 1.隐式迭代 给所有的按钮都绑定了点击事件
            $('button').click(function () {
                // 2.让当前元素的颜色变为红色
                // $(this).css('color', 'red');
                // 3.让其余的兄弟元素 不变色
                // $(this).siblings('button').css('color', '');
                // 链式编程
                $(this).css('color', 'red').siblings('button').css('color', '');
                // 当前元素的颜色变为红色 我的兄弟不变色
                $(this).siblings('button').parent().css('color', 'pink');
                // 给我的兄弟元素的父元素 body 变化颜色
                // 一层一层的顺着往下找 注意是哪个元素执行样式
            })
        })

    </script>
</body>

</html>
```

## 2.jQuery样式操作

### 2.1 操作css方法

jQuery可以使用css方法来修改简单元素样式；也可以操作类，修改多个样式。

1. 参数只写属性名,则是返回属性值 (如果属性不加引号 则返回属性值)

   ```javascript
   $(this),css("color");
   ```

2. 参数是 **属性名,属性值** 逗号分隔,是设置一组样式,属性必须加引号,值如果是数字可以不用跟单位和引号

   ```javascript
   $(this),css("color", "red");
   ```

3. 参数可以是对象形式，方便设置多组样式。属性名和属性值用冒号隔开，属性可以不用加引号，如果属性是复合属性(backgroundColor) 必须采用驼峰命名法就可以不加引号，复合属性可以加引号("font-size") ，属性值是数字可以不用加引号，不是数字必须加引号

   ```javascript
   $(this).css({ "color":"white"," font-size":" 20px"});
   
   $(this).css({
       color: "red",
       fontSize: 20
   })
   ```

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
            width: 200px;
            height: 200px;
            background-color: pink;
        }
    </style>
</head>

<body>
    <div></div>
    <script>
        // 1.返回的是值 为200px 属性名要加引号
        // console.log($('div').css('width')); 

        // 2.属性名要加引号 属性值是数字可以不加引号 也可以不加单位 这是设置一组样式
        // $('div').css('width', 300); 
        // $('div').css('width', '600px');

        // 3.对象形式 设置多组方式 属性名可以不加引号 属性值是数字可以不加引号 如果是复合属性 1.可以用驼峰命名就不用加引号 2.直接加引号使用复合属性
        $('div').css({
            height: 400,
            width: 500,
            'background-color': 'red'
            // backgroundColor: 'red'
        })
    </script>
</body>

</html>
```

### 2.2 设置类样式方法

作用等同于以前的classList，可以操作类样式,注意操作类里面的参数不要加点。

1. 添加类

   ```javascript
   $( "div" ).addClass("current'");
   ```

2. 移除类

   ```javascript
   $( "div" ).removeClass("current');
   ```

3. 切换类

   ```javascript
   $( "div" ).toggleClass("current');// 如果有这个类名 就去除; 如果没有这个类名，就加上
   ```

#### 案列：商品tap栏切换

案列分析：

1. 点击上部的Ii ,当前li添加current类, 其余兄弟移除类。
2. 点击的同时,得到当前i的索引号
3. 让下部里面相应索引|号的item显示,其余的item隐藏

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
        ul {
            list-style: none;
            margin: 0;
            padding: 0;
        }

        a {
            text-decoration: none;
        }

        .tab {
            width: 1200px;
            height: auto;
            margin: 50px auto;
        }

        .tab_list {
            width: 1000px;
            height: 60px;
            display: flex;
            justify-content: space-between;
            align-items: end;
            background-color: #f5f8f564;
            border-bottom: 2px solid #F14A35;
        }

        .tab_item {
            width: 800px;
            height: 100%;
            display: flex;
            justify-content: space-between;
            align-items: flex-end;
        }

        .tab_item li {
            width: 136px;
            height: 30px;
            line-height: 30px;
            text-align: center;
            cursor: pointer;
            /* background-color: pink; */
        }

        .current {
            color: #fff;
            background-color: #F14A35;
        }

        .tab_icon {
            width: 100px;
            height: 30px;
            line-height: 30px;
            text-align: center;
            background-color: #F14A35;
        }

        .tab_icon a {
            display: block;
            color: #fff;
        }

        .tab_cont {
            position: relative;
        }

        .tab_cont_1 {
            display: none;
            position: absolute;
            top: 0;
            left: 0;
        }
    </style>
</head>

<body>
    <div class="tab">
        <div class="tab_list">
            <ul class="tab_item">
                <li class="current">商品介绍</li>
                <li>规格与包装</li>
                <li>售后保障</li>
                <li>商品评价(10000+)</li>
                <li>手机社区</li>
            </ul>
            <div class="tab_icon">
                <a href="#">加入购物车</a>
            </div>
        </div>
        <div class="tab_cont">
            <div class="tab_cont_1" style="display: block;">
                商品介绍内容
            </div>
            <div class="tab_cont_1">
                规格与包装内容
            </div>
            <div class="tab_cont_1">
                售后保障内容
            </div>
            <div class="tab_cont_1">
                商品评价内容
            </div>
            <div class="tab_cont_1">
                手机社区内容
            </div>
        </div>
    </div>
    <script>
        $(function () {
            // 1.点击上部的Ii, 当前li添加current类, 其余兄弟移除类。
            $(".tab_item li").click(function () {
                // 1.点击的同时, 得到当前i的索引号
                $(this).addClass("current").siblings("li").removeClass("current");
                // 3.让下部里面相应索引 | 号的item显示, 其余的item隐藏
                $(".tab_cont .tab_cont_1").eq($(this).index()).show().siblings('.tab_cont_1').hide();
            });

        })
    </script>
</body>

</html>
```

### 2.3 类操作与className区别

原生JS中className会覆盖元素原先里面的类名。

jQuery里面类操作只是对指定类进行操作,不影响原先的类名。

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
        .one {
            width: 200px;
            height: 200px;
            background-color: pink;
        }

        .two {
            width: 100px;
            height: 100px;
            background-color: hotpink;
        }
    </style>
</head>

<body>
    <div class="one"></div>
    <script>
        // 会把原先的类名替换掉
        // var one = document.querySelector('.one');
        // one.className = 'two';
        // 这个addClass 相当于追加类名 不影响原先的类名
        $(".one").addClass('two');
    </script>
</body>

```

## 3.jQuery 效果

jQuery 给我们封装了很多动画效果，最为常见的如下：

**显示隐藏**

- show()
- hide()
- toggle()

**滑动**

- slideDwon()
- slideUp()
- slideToggle()

**淡入淡出**

- fadeln()
- fadeOut()
- fadeToggle()
- fadeTo()

**自定义**

- animate()

### 3.1 显示隐藏效果

#### 1.显示语法规范

```javascript
show([speed, [easing], [fn]] )
```

**一般情况下，我们都不加参数 直接显示隐藏就可以了**

#### 2.显示参数

1. 参数都可以省略，无动画直接显示。
2.  speed:三种预定速度之一 -的字符串( "slow"，"normal" , or  "fast" )或表示动画时长的毫秒数值(如: 1000)。
3. easing : (Optional)用来指定切换效果,默认是"swing” , 可用参数"linear" 。
4. fn:回调函数,在动画完成时执行的函数,每个元素执行一次。

#### 1.隐藏语法规范

```javascript
hide([speed, [easing], [fn]])
```

#### 2.隐藏参数

1. 参数都可以省略,无动画直接显示。
2. speed :三种预定速度之一 的字符串( "slow"，"normal" ,or "fast" )或表示动画时长的毫秒数值(如: 1000)。
3. easing : (Optional)用来指定切换效果,默认是"swing” ,可用参数"linear" 。
4.  fn:回调函数,在动画完成时执行的函数,每个元素执行次。

#### 1.切换语法规范

```javascript
toggle([speed, [easing] , [fn]])
```

#### 2.切换参数

1. 参数都可以省略,无动画直接显示。
2. speed :三种预定速度之一 的字符串( "slow"，"normal" ,or "fast" )或表示动画时长的毫秒数值(如: 1000)。
3. easing : (Optional)用来指定切换效果,默认是"swing” ,可用参数"linear" 。
4.  fn:回调函数,在动画完成时执行的函数,每个元素执行次。

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
            width: 200px;
            height: 400px;
            background-color: pink;
        }
    </style>
</head>

<body>
    <button>显示</button>
    <button>隐藏</button>
    <button>切换</button>
    <div></div>
    <script>
        // 1.隐藏 hide([speed, [easing], [fn]]) 
        $('button').eq(1).click(function () {
            $("div").hide(2000, function () {
                alert('1');
            });
        });
        // 2.显示 show([speed, [easing], [fn]])
        $('button').eq(0).click(function () {
            $("div").show(2000, function () {
                alert('1');
            });
        });
        // 3.切换 toggle([speed, [easing], [fn]])
        $('button').eq(2).click(function () {
            $("div").toggle(2000, function () {
                alert('1');
            });
        });
    </script>
</body>

</html>
```

### 3.2 滑动效果

使用滑动，元素必须先用css隐藏起来

#### 1.下滑效果语法规范

```javascript
slideDown([speed, [easing], [fn]])
```

#### 2.下滑效果参数

1. 参数都可以省略,无动画直接显示。
2. speed :三种预定速度之一 的字符串( "slow"，"normal" ,or "fast" )或表示动画时长的毫秒数值(如: 1000)。
3. easing : (Optional)用来指定切换效果,默认是"swing” ,可用参数"linear" 。
4.  fn:回调函数,在动画完成时执行的函数,每个元素执行次

#### 1.上滑效果语法规范

```javascript
slideUp([speed, [easing], [fn]])
```

#### 2.上滑效果参数

1. 参数都可以省略,无动画直接显示。
2. speed :三种预定速度之一 的字符串( "slow"，"normal" ,or "fast" )或表示动画时长的毫秒数值(如: 1000)。
3. easing : (Optional)用来指定切换效果,默认是"swing” ,可用参数"linear" 。
4.  fn:回调函数,在动画完成时执行的函数,每个元素执行次

#### 1.滑动切换效果语法规范

```javascript
slideToggle([speed], [easing], [fn]])
```

#### 2.滑动切换效果参数

1. 参数都可以省略,无动画直接显示。
2. speed :三种预定速度之一 的字符串( "slow"，"normal" ,or "fast" )或表示动画时长的毫秒数值(如: 1000)。
3. easing : (Optional)用来指定切换效果,默认是"swing” ,可用参数"linear" 。
4.  fn:回调函数,在动画完成时执行的函数,每个元素执行次

### 3.3 事件切换

```javascript
hover{[over,]out}
```

1. over鼠标**移到**元素上要触发的函数(相当于mouseenter)
2. out鼠标**移出**元素上要触发的函数(相当于mouseleave)

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!-- 不要忘记引入jQuery -->
    <script src="./js/jQuery.min.js"></script>
    <title>Document</title>
    <style>
        ul {
            list-style: none;
            padding-left: 0;
        }

        a {
            text-decoration: none;
        }

        .row {
            display: flex;
        }

        .row>li {
            margin: 0 20px;
        }

        .row>li>a {
            display: block;
            width: 100px;
            height: 40px;
            line-height: 40px;
            color: #000;
            text-align: center;
        }

        .clu {
            display: none;

        }

        .clu li {
            height: 40px;
            border: 1px solid #FF8200;
            border-top: none;
            text-align: center;
            line-height: 40px;
        }

        .clu li a {
            color: #000;
        }

        .clu li:hover {
            background-color: rgba(254, 197, 46, .2);
        }
    </style>
</head>

<body>
    <ul class="row">
        <li>
            <a href="#">微博</a>
            <ul class="clu">
                <li>
                    <a href="#">主页</a>
                </li>
                <li>
                    <a href="#">评论</a>
                </li>
                <li>
                    <a href="#">@我</a>
                </li>
                <li>
                    <a href="#">联系</a>
                </li>
            </ul>
        </li>
        <li>
            <a href="#">微博</a>
            <ul class="clu">
                <li>
                    <a href="#">主页</a>
                </li>
                <li>
                    <a href="#">评论</a>
                </li>
                <li>
                    <a href="#">@我</a>
                </li>
                <li>
                    <a href="#">联系</a>
                </li>
            </ul>
        </li>
        <li>
            <a href="#">微博</a>
            <ul class="clu">
                <li>
                    <a href="#">主页</a>
                </li>
                <li>
                    <a href="#">评论</a>
                </li>
                <li>
                    <a href="#">@我</a>
                </li>
                <li>
                    <a href="#">联系</a>
                </li>
            </ul>
        </li>
        <li>
            <a href="#">微博</a>
            <ul class="clu">
                <li>
                    <a href="#">主页</a>
                </li>
                <li>
                    <a href="#">评论</a>
                </li>
                <li>
                    <a href="#">@我</a>
                </li>
                <li>
                    <a href="#">联系</a>
                </li>
            </ul>
        </li>
    </ul>
    <script>
        $(function () {
            // 鼠标经过
            //  $('.row>li')  jQuery隐式迭代 .row>li 里面每个小li都绑定了 mouseover事件 (.row>li 这样是隐式迭代row里面的亲儿子 也就是就近一级子级元素)    相当于原生js循环绑定了li
            //     $('.row>li').mousemove(function () {
            //         // $(this) jQuery 当前元素  this不要加引号
            //         // show() 显示元素 hide()  隐藏元素
            //         $(this).children('a').css('backgroundColor', '#999');
            //         $(this).find('.clu').show();

            //     });
            //     // 鼠标离开
            //     $('.row>li').mouseout(function () {
            //         $(this).children('a').css('backgroundColor', '');
            //         $(this).find('.clu').hide();
            //     });

            // $(".row>li").mousemove(function () {
            //     $(this).children("a").css("background-color", "#999");
            //     $(this).children("ul").slideDown(200);
            // });
            // $(".row>li").mouseleave(function () {
            //     $(this).children("a").css("background-color", "");
            //     $(this).children("ul").slideUp(200);
            // });

            // 1.事件切换 hover 就是鼠标经过和离开的复合写法
            // $(".row>li").hover(function () {
            //     $(this).children("a").css("background-color", "#999");

            //     $(this).children("ul").slideDown(200);
            // }, function () {
            //     $(this).children("a").css("background-color", "");
            //     $(this).children("ul").slideUp(200);
            // });

            // 2.事件切换 hover 如果只写一个函数，那么鼠标经过和鼠标离开都会触发这个函数
            $(".row>li").hover(function () {
                // stop()方法必须写到动画的前面 这样每个动画才能有队列
                $(this).children("ul").stop().slideToggle(200);
            });
        });

    </script>
</body>

</html>
```

### 3.4 动画队列及其停止排队方法

#### 1.动画或效果排列

动画或者效果一旦触发就会执行 ,如果多次触发,就造成多个动画或者效果排队执行。

#### 2.停止排队

```javascript
stop()
```

1. stop()方法用于停止动画或效果。
2. 注意: stop()写到动画或者效果的前面,相当于停止结束上一次的动画。

例：

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!-- 不要忘记引入jQuery -->
    <script src="./js/jQuery.min.js"></script>
    <title>Document</title>
    <style>
        ul {
            list-style: none;
            padding-left: 0;
        }

        a {
            text-decoration: none;
        }

        .row {
            display: flex;
        }

        .row>li {
            margin: 0 20px;
        }

        .row>li>a {
            display: block;
            width: 100px;
            height: 40px;
            line-height: 40px;
            color: #000;
            text-align: center;
        }

        .clu {
            display: none;

        }

        .clu li {
            height: 40px;
            border: 1px solid #FF8200;
            border-top: none;
            text-align: center;
            line-height: 40px;
        }

        .clu li a {
            color: #000;
        }

        .clu li:hover {
            background-color: rgba(254, 197, 46, .2);
        }
    </style>
</head>

<body>
    <ul class="row">
        <li>
            <a href="#">微博</a>
            <ul class="clu">
                <li>
                    <a href="#">主页</a>
                </li>
                <li>
                    <a href="#">评论</a>
                </li>
                <li>
                    <a href="#">@我</a>
                </li>
                <li>
                    <a href="#">联系</a>
                </li>
            </ul>
        </li>
        <li>
            <a href="#">微博</a>
            <ul class="clu">
                <li>
                    <a href="#">主页</a>
                </li>
                <li>
                    <a href="#">评论</a>
                </li>
                <li>
                    <a href="#">@我</a>
                </li>
                <li>
                    <a href="#">联系</a>
                </li>
            </ul>
        </li>
        <li>
            <a href="#">微博</a>
            <ul class="clu">
                <li>
                    <a href="#">主页</a>
                </li>
                <li>
                    <a href="#">评论</a>
                </li>
                <li>
                    <a href="#">@我</a>
                </li>
                <li>
                    <a href="#">联系</a>
                </li>
            </ul>
        </li>
        <li>
            <a href="#">微博</a>
            <ul class="clu">
                <li>
                    <a href="#">主页</a>
                </li>
                <li>
                    <a href="#">评论</a>
                </li>
                <li>
                    <a href="#">@我</a>
                </li>
                <li>
                    <a href="#">联系</a>
                </li>
            </ul>
        </li>
    </ul>
    </body>
    <script>
    	$(function() {
            $(".row>li").hover(function() {
                // stop()方法必须写到动画的前面
               $(this).children("ul").stop().slideToggle(200);
            });
        });
    </script>
</html>
```

### 3.5 淡入淡出效果

#### 1.淡入效果语法规范

```javascript
fadeIn([speed, [easing], [fn]])
```

#### 2.淡入效果参数

1. 参数都可以省略,无动画直接显示。
2. speed :三种预定速度之一 的字符串( "slow"，"normal" ,or "fast" )或表示动画时长的毫秒数值(如: 1000)。
3. easing : (Optional)用来指定切换效果,默认是"swing” ,可用参数"linear" 。
4. fn:回调函数,在动画完成时执行的函数,每个元素执行次

#### 1.淡出效果语法规范

```javascript
fadeOut([speed, [easing], [fn]])
```

#### 2.淡入效果参数

1. 参数都可以省略,无动画直接显示。
2. speed :三种预定速度之一 的字符串( "slow"，"normal" ,or "fast" )或表示动画时长的毫秒数值(如: 1000)。
3. easing : (Optional)用来指定切换效果,默认是"swing” ,可用参数"linear" 。
4. fn:回调函数,在动画完成时执行的函数,每个元素执行次

#### 1.淡入淡出切换效果语法规范

```javascript
fadeToggle([speed, [easing], [fn]])
```

#### 2.淡入效果参数

1. 参数都可以省略,无动画直接显示。
2. speed :三种预定速度之一 的字符串( "slow"，"normal" ,or "fast" )或表示动画时长的毫秒数值(如: 1000)。
3. easing : (Optional)用来指定切换效果,默认是"swing” ,可用参数"linear" 。
4. fn:回调函数,在动画完成时执行的函数,每个元素执行次

#### 1.渐进方式调整到指定的不透明度

```javascript
fadeTo([[speed], opacity,[easing], [fn]])
```

#### 2.效果参数

1. opacity透明度**必须写**,取值0~1之间。
2. speed :三种预定速度之一的字符串( "slow" , "normal”， or "fast" )或表示动画时长的毫秒数值(如: 1000)。**必须写**
3. easing : (Optional)用来指定切换效果,默认是"swing” ,可用参数"linear" 。
4. fn:回调函数,在动画完成时执行的函数,每个元素执行次

### 3.6 自定义动画 animate

#### 1.语法

```javascript
animate(params, [speed], [easing], [fn])
```

#### 2.参数

1. params:想要更改的样式属性,以对象形式传递,必须写。属性名可以不用带引号,如果是复合属性则需要采取驼峰命名法borderLeft。其余参数都可以省略。
2. speed:三种预定速度之一的字符串( "slow" ，"normal" , or "fast" )或表示动画时长的毫秒数值(如: 1000)。
3. easing : (Optional) 用来指定切换效果,默认是"swing" , 可用参数"linear” 。
4. fn:回调函数,在动画完成时执行的函数,每个元素执行一次。

注意：只有元素才能做动画，如果需要文档做动画 要使用body，html

如果是要元素做移动效果，一定要加定位。

#### 案列：王者荣耀手风琴效果

**案例分析**

1. 鼠标经过某个小i有两步操作: 
2. 当前小li宽度变为224px，同时里面的小图片淡出,大图片淡入
3. 其余兄弟小i宽度变为69px,小图片淡入，大图片淡出

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
        ul {
            list-style: none;
            margin: 0;
            padding: 0;
            display: flex;
        }

        .king {
            width: 769px;
            height: 115px;
            margin: 100px auto;
            background: url(./images/king.png) no-repeat;
            padding: 20px;
        }

        img {
            display: block;
        }

        .king ul li {
            position: relative;
            width: 69px;
            height: 69px;
            border-radius: 10px;
            margin-right: 15px;
            overflow: hidden;
        }

        .king ul li.current {
            width: 224px;
        }

        ul li.current .small {
            display: none;
        }

        ul li.current .big {
            display: block;
        }

        .small {
            position: absolute;
            top: 0;
            left: 0;
            width: 69px;
            height: 69px;
        }

        .big {
            width: 224px;
            height: 69px;
            display: none;
        }
    </style>
</head>

<body>
    <div class="king">
        <ul>
            <li class="current">
                <a href="#">
                    <img src="./images/zhaoyun_s.jpg" alt="" class="small">
                    <img src="./images/zhaoyun_b.png" alt="" class="big">
                </a>
            </li>
            <li>
                <a href="#">
                    <img src="./images/damo_s.jpg" alt="" class="small">
                    <img src="./images/damo_b.png" alt="" class="big">
                </a>
            </li>
            <li>
                <a href="#">
                    <img src="./images/diaochan_s.jpg" alt="" class="small">
                    <img src="./images/diaochan_b.png" alt="" class="big">
                </a>
            </li>
            <li>
                <a href="#">
                    <img src="./images/chengyaojin_s.jpg" alt="" class="small">
                    <img src="./images/chengyaojin_b.png" alt="" class="big">
                </a>
            </li>
            <li>
                <a href="#">
                    <img src="./images/jiaoziya_s.jpg" alt="" class="small">
                    <img src="./images/jiangziya_b.png" alt="" class="big">
                </a>
            </li>
            <li>
                <a href="#">
                    <img src="./images/zhangfei_s.jpg" alt="" class="small">
                    <img src="./images/zhangfei_b.png" alt="" class="big">
                </a>
            </li>
            <li>
                <a href="#">
                    <img src="./images/chengjisihan_s.jpg" alt="" class="small">
                    <img src="./images/chengjisihan_b.png" alt="" class="big">
                </a>
            </li>
        </ul>
    </div>
</body>
<script>
    $(function () {
        $(".king li").mouseenter(function () {
            $(this).stop().animate({
                width: 224          }).find(".small").stop().fadeOut().siblings(".big").stop().fadeIn();
            $(this).siblings("li").stop().animate({
                width: 694
            }).find(".big").stop().fadeOut().siblings(".small").stop().fadeIn();
        });
    });
</script>

</html>
```

## 4.jQuery属性操作

### 4.1 设置或获取元素固有属性值prop()

所谓元素固有属性就是元素本身自带的属性,比如<a>元素里面的href , 比如<input>元素里面的type.

#### 1.获取属性语法

```javascript
prop("属性")
```

#### 2.设置属性语法

```javascript
prop("属性"，"属性值")
```

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="./js/jQuery.min.js"></script>
    <title>Document</title>
</head>

<body>
    <a href="https://www.juejin.cn/" title="加油">稀土掘金</a>
    <!-- <input type="text" value="0"> -->
    <input type="checkbox" checked>
    <script>
        // 元素的固有属性
        // (1).Element.prop("属性"); 返回属性值 
        console.log($("a").prop("href"));
        // (2).Element.prop("属性", "属性名"); 改属性值
        // $("a").prop("title", "我们加油");
        // console.log($("input").prop("value"));
        // $("input").prop("value", 1);
        
        // 复选框的change事件
        $("input").change(function () {
            console.log($(this).prop("checked"));
        });
    </script>
    </body>
</html>
```

### 4.2 设置或获取元素自定义属性值 attr()

用户自己给元素添加的属性,我们称为自定义属性。比如给div添加index =“1”.

#### 1.获取属性语法

```javascript
attr("属性")   // 类似原生getAttribute()
```

#### 2.设置属性语法

```javascript
attr("属性", "属性值') // 类似原生setAttribute()
```

改方法也可以获取H5自定义属性

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="./js/jQuery.min.js"></script>
    <title>Document</title>
</head>

<body>
    <a href="https://www.juejin.cn/" title="加油">稀土掘金</a>
    <!-- <input type="text" value="0"> -->
    <input type="checkbox" checked>
    <div index="1">你好</div>
    <script>
        // 元素自定义属性
        console.log($("div").attr("index"));
       $("div").attr("index", 4);
        console.log($("span").attr("data-index")); // 这个是字符串型 要加前缀data-

    </script>
</body>

</html>
```

### 4.3 数据缓存 data()

data(方法可以在指定的元素上存取数据,并钚会修改DOM元素结构。一-旦 页面刷新,之前存放的数据都将被移除。

#### 1.附加数据语法

```javascript
data("name","value") // 向被选元素附加数据
```

#### 2.获取数据语法

```javascript
date("name")  //向被选元素获取数据
```

同时,还可以读取HTML5自定义属性data-index ,得到的是数字型

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="./js/jQuery.min.js"></script>
    <title>Document</title>
</head>

<body>
    <span data-index="3">123</span>
    <script>
        
                // 数据缓存 data() 这个里面的数据是存放在元素的内存里面 页面一刷新 就没有了
        $("span").data("uname", "adny");
        console.log($("span").data("uname"));

               //  这个方法获取 data-index h5自定义属性 第一个不用写  data-  而且返回的是数字型
        console.log($("span").data("index"));
    </script>
</body>

</html>
```

### 案列：购物车全选按钮

案列分析

1. 全选思路:里面3个小的复选框按钮( j-checkbox )选中状态( checked )跟着全选按钮( checkall )走。
2. 因为checked 是复选框的固有属性,此时我们需要利用prop()方法获取和设置该属性。
3. 把全选按钮状态赋值给3个小复选框就可以了。
4. 当我们每次点击小的复选框按钮,就来判断:
5. 如果小复选框被选中的个数等于3就应该把全选按钮选上,否则全选按钮不选。
6. :checked 选择器    :checked查找被选中的表单元素。

## 5.jQuery 内容文本值

主要针对元素的**内容**还有**表单的值**操作。

### 5.1 普通元素内容html()   (相当于原生js中的innerHTML)

```javascript
html()  // 获取元素的内容
```

```javascript
html("内容")  // 设置元素的内容
```

### 5.2 普通元素文本内容text()    (相当于原生js中的innerText)

```javascript
text()  // 获取元素的文本内容
```

```javascript
text("文本内容") // 设置元素的文本内容
```

### 5.3 表单的值 val()  (相当于原生js中的value)

```javascript
val()  // 获取表单的值
```

```javascript
val("内容") // 设置表单的值
```

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="./js/jQuery.min.js"></script>
    <title>Document</title>
</head>

<body>
    <div>
        <span>123</span>
    </div>
    <input type="text" value="请输入内容">

</body>
<script>
    $(function () {
        // html() 获取元素内容  相当于原生js中的innerHTML
        console.log($("div").html());
        // html("内容") 设置元素内容 
        $("div").html("键盘敲烂");

        // text() 获取文本内容 相当于原生js中的innerText 
        console.log($("div").text());
        // text("内容") 设置文本内容
        $("div").text("fuck");

        // val() 获取表单的值 相当于原生js中的 value
        console.log($("input").val());
        // val("内容") 设置表单的值
        $("input").val("123");
    });
</script>

</html>
```

### 案列：购物车增减商品数量

案列分析

1. 核心思路:首先声明一个变量,当我们点击+号( increment) , 就让这个值++ ,然后赋值给文本框。
2. 注意1 :只能增加本商品的数量，就是当前+号的兄弟文本框的值。
3. 修改表单的值是val()方法
4. 注意2 :这个变量初始值应该是这个文本框的值,在这个值的基础上++。要获取表单的值
5. 减号( decrement )思路同理,但是如果文本框的值是1 ,就不能再减了。

### 案列：修改商品小计

案列分析

1. 核心思路:每次点击+号或者号,根据文本框的值乘以当前商品的价格就是商品的小计
2. 注意1 :只能增加本商品的小计,就是当前商品的小计模块( p-sum )
3. 修改普通元素的内容是text()方法
4. 注意2 :当前商品的价格,要把￥符号去掉再相乘截取字符串substr(1)
5. **parents("选择器")** 可以返回指定祖先元素  如果里面不加选择器 返回的是当前元素的所有父元素。
6. 最后计算的结果如果想要保留2位小数通过**toFixed(2)**方法。
7. 用户也可以直接修改表单里面的值, 同样要计算小计。用**表单change事件**
8. 用最新的表单内的值乘以单价即可，但是还是当前商品小计

## 6.jQuery元素操作

主要是**遍历**、创建、添加、删除元素操作。

### 6.1 遍历元素

jQuery隐式迭代是对同一元素做了同样的操作。如果想要给同- 元素做不同操作,就需要用到遍历。

**语法1 :**

```javascript
$("div").each(function (index, domEle) { XXX; } )
```

1. each()方法遍历匹配的每一个元素。主要用于DOM元素处理。each每一 个
2. 里面的回调函数有2个参数: index 是每个元素的索引号,可以自己指定索引号名称; demEle是**DOM元素对象,不是jquery对象**，这个对象也可以自己设置名称。
3. 所以要想使用jquery方法,需要给这个dom元素转换为jquery对象$(domEle)

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="./js/jQuery.min.js"></script>
    <title>Document</title>
</head>

<body>
    <div>1</div>
    <div>2</div>
    <div>3</div>
</body>
<script>
    $(function () {
        // 1.each() 方法遍历元素
        var sum = 0;
        var arr = ["red", "blue", "yellow"];
        $("div").each(function (index, domEle) {
            // 回调函数第一个参数一定是索引号  可以自己指定索引号名称
            // console.log(index);
            // 回调函数第二个参数一定是 dom元素对象
            // console.log(domEle);
            // dom对象没有css方法
            $(domEle).css("color", arr[index]);
            // 先转为数字型的 然后相加
            sum += parseInt($(domEle).text());
        });
        console.log(sum);
    });
</script>

</html>
```

**语法2：**

```javascript
$.each(object, function(index, element) { xxx; } )
```

1. $.each()方法可用于遍历任何对象。主要用于数据处理,比如数组,对象
2. 里面的函数有2个参数: index 是每个元素的索引号; element遍历内容

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="./js/jQuery.min.js"></script>
    <title>Document</title>
</head>

<body>
    <div>1</div>
    <div>2</div>
    <div>3</div>
</body>
<script>
    $(function () {        
        // 2.$.each() 方法遍历对象，数组
        // (1) 也可以遍历DOM元素
        $.each($("div"), function (index, domEle) {
            console.log(index);
            console.log(domEle);
        });
        // (2) 遍历数组
        $.each(arr, function (index, domEle) {
            console.log(index);
            console.log(domEle);
        });
        // (3) 遍历对象
        $.each({ name: "andy", age: 16 }, function (index, domEle) {
            console.log(index);  // 属性名 name age
            console.log(domEle); // 属性值 andy 16
        })

    });
</script>

</html>
```

### 案列：购物车案例模块计算总计和总额

1. 核心思路:把所有文本框里面的值相加就是总计数量。总额同理
2. 文本框里面的值不相同,如果想要相加需要用到each遍历。声明一个变量,相加即可
3. 点击+号-号,会改变总计和总额,如果用户修改了文本框里面的值同样会改变总计和总额
4. 因此可以封装一个函数求总计和总额的 ，以上2个操作调用这个函数即可。
5. 注意1 :总计是文本框里面的值相加用val() 总额是普通元素的内容用text0
6. 要注意普通元素里面的内容要去掉￥并且转换为数字型才能相加

### 6.2 创建元素

主要是遍历、**创建**、添加、删除元素操作。

语法：

```javascript
$("<li></li>")
```

动态创建了一个<li>

### 6.3 添加元素

#### 1.内部添加

```javascript
element.append("内容”);
```

把内容放入匹配元素内部最**后面**,类似于原生appendChild.

```javascript
element.prepend("内容")
```

把内容放入匹配元素内部**前面**

#### 2.外部添加

```javascript
element.after("内容")  //把内容放入目标元素后面
```

```javascript
element.before("内容") // 把内容放入目标元素前面
```

1. 内部添加元素,生成之后,它们是父子关系。
2. 外部添加元素,生成之后,他们是兄弟关系。

### 6.4 删除元素

```javascript
element.remove()  // 删除匹配的元素(本身)
```

```javascript
element.empty() // 删除匹配的元素集合中所有的子节点
```

```javascript
element.html("") // 清空匹配的元素内容
```

### 案列：购物车案列模块-删除商品模块

1. 核心思路:把商品remove()删除元素即可
2. 有三个地方需要删除: 1. 商品后面的删除按钮2.删除选中的商品3.清理购物车
3. 商品后面的删除按钮:一定是删除当前的商品 ,所以从$(this)出发
4. 删除选中的商品:先判断小的复选框按钮是否选中状态,如果是选中,则删除对应的商品

### 案列：购物车案例模块-选中商品添加背景

1. 核心思路:选中的商品添加背景,不选中移除背景即可
2. 全选按钮点击:如果全选是选中的,则所有的商品添加背景,否则移除背景
3. 小的复选框点击:如果是选中状态,则当前商品添加背景,否则移除背景
4. 这个背景，可以通过类名修改,添加类和删除类

## 7.jQuery尺寸、位置操作

### 7.1 jQuery尺寸

| 语法                                 | 用法                                                |
| ------------------------------------ | --------------------------------------------------- |
| width()/ height()                    | 取得匹配元素宽度和高度值只算width 1 height          |
| innerWidth() / innerHieght()         | 取得匹配元素宽度和高度值包含padding                 |
| outerWidth() / outerHeight()         | 取得匹配元素宽度和高度值包含padding、border         |
| outerWidth(true) / outerHeight(true) | 取得匹配元素宽度和高度值包含padding、borde、 margin |

- 以上参数为空，则是获取相应值，返回的是数字型。
- 如果参数为数字,则是修改相应值。
- 参数可以不必写单位。

### 7.2 jQuery 位置

位置主要有三个: **offset0**、 position()、 scrollTop()/scrollLeft()

#### 1.offset()设置或获取元素偏移

1. offset() 方法设置或返回被选元素**相对于文档**的偏移坐标,跟父级没有关系。
2. 该方法有2个属性left、top。offset().top 用于获取距离文档顶部的距离, offset().Ieft 用于获取距离文档左侧的距离。
3. 可以设置元素的偏移: offset({ top: 10, left: 30 });

位置主要有三个: offset()、 **position()**、 scrollTop()/scrollLeft()

#### 2.position() 获取元素偏移

1. position()方法用于返回被选元素相对于带有定位的父级偏移坐标，如果父级都没有定位，则以文档为准。
2. 这个方法只能获取不能设置偏移

位置主要有三个: offset()、 position()、 **scrollTop()/scrollLeft()**

#### 3.scrollTop0/scrollLeft(设置或获取元素被卷去的头部和左侧

1. scrollTop()方法设置或返回被选元素被卷去的头部。

![image-20220421174842212](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220421174842212.png)

### 案列：带有动画的返回顶部

1. 核心原理:使用animate动画返回顶部。
2. animate动画函数里面有个scrolITop属性,可以设置位置
3. 但是是元素做动画,因此$( "body,html" ).animate({scrollTop: 0})

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
        .continer {
            width: 800px;
            height: 800px;
            margin: 400px auto;
            background-color: pink;
        }

        .casr {
            position: fixed;
            right: 30px;
            bottom: 100px;
            width: 100px;
            height: 30px;
            line-height: 30px;
            text-align: center;
            background-color: skyblue;
            cursor: pointer;
            display: none;
        }
    </style>
</head>

<body>
    <div class="continer"></div>
    <div class="casr">返回顶部</div>
    <script>
        $(function () {
            // 被卷去的头部 scrollTop()  /  被卷去的左侧 scrollLeft()
            // 页面滚动事件
            $(window).scroll(function () {
                console.log($(document).scrollTop());  // 文档被卷去的头部
                if ($(document).scrollTop() >= $(".continer").offset().top) {
                    $(".casr").fadeIn(500);
                } else {
                    $(".casr").fadeOut(500);

                }
				// 	返回顶部
                $(".casr").click(function () {
                    // $(document).scrollTop(0); // 这个是直接返回顶部
                    // 因为只有元素才能做动画 所以要用body 和 html
                    $("body,html").animate({
                        scrollTop: 0
                    }, 800)
                });
            });
        });
    </script>
</body>

</html>
```

### 案列：电梯导航

1. 当我们滚动到今日推荐模块,就让电梯导航显示出来
2. 点击电梯导航页面可以滚动到相应内容区域
3. 核心算法:因为电梯导航模块和内容区模块一对应的
4. 当我们点击电梯导航某个小模块,就可以拿到当前小模块的索引号
5. 就可以把animate要移动的距离求出来:当前索引号内容区模块它的offset().top
6. 然后执行动画即可

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
        * {
            padding: 0;
            margin: 0;
        }

        body {
            height: 3000px;
        }

        .w {
            width: 1200px;
            margin: 0 auto;
        }

        .con {
            height: 500px;
            background-color: yellow;

        }

        .yifu {
            height: 300px;
            background-color: pink;
        }

        .jiadian {
            height: 300px;
            background-color: skyblue;
        }

        .dianshi {
            height: 300px;
            background-color: purple;
        }

        .bangong {
            height: 300px;
            background-color: hotpink;
        }

        .cast {
            display: none;
            position: fixed;
            top: 0;
            left: 20px;
            width: 100px;
            border: 1px solid #000;
            text-align: center;
        }

        .item {
            height: 30px;
            line-height: 30px;

        }

        .item:hover {
            background-color: skyblue;
        }
    </style>
</head>

<body>
    <div class="con">

    </div>
    <div class="yifu w">
        <h3>衣服模块</h3>
    </div>
    <div class="jiadian w">
        <h3>家电模块</h3>
    </div>
    <div class="dianshi w">
        <h3>电视模块</h3>
    </div>
    <div class="bangong w">
        <h3>办公模块</h3>
    </div>
    <div class="cast">
        <div class="item">
            衣服部分
        </div>
        <div class="item">
            家电部分
        </div>
        <div class="item">
            电视部分
        </div>
        <div class="item">
            办公部分
        </div>
    </div>
    <script>
        $(function () {
            $(window).scroll(function () {
                if ($("html, body").scrollTop() >= $(".yifu").offset().top) {
                    $(".cast").fadeIn(800);
                } else {
                    $(".cast").fadeOut(800);

                }
                // 2.点击电梯导航页面可以滚动到相应内容区域
                $(".item").click(function () {
                    console.log($(this).index()); // 获取当前点击的item的索引号
                    // 当我们每次点击小li 就需要计算出页面要去往的位置
                    // 选出对应索引号的内容区的盒子  计算它的 offset().top
                    var current = $(".w").eq($(this).index()).offset().top
                    $("html, body").stop().animate({
                        scrollTop: current
                    })
                });
            });
        });
    </script>
</body>

</html>
```

### 案列：电梯导航

1. 当我们点击电梯导航某个小i，当前小i添加current类,兄弟移除类名
2. 当我们页面滚动到内容区域某个模块,左侧电梯导航,相对应的小|i模块,也会添加current类，兄弟移除current类。
3. 触发的事件是页面滚动，因此这个功能要写到页面滚动事件里面。
4. 需要用到each ,遍历内容区域大模块。each里面能拿 到内容区域每一个模块元素和索引号
5. 判断的条件：被卷去的头部大于等于内容区域里面每个模块的offset().top
6. 就利用这个索引号找到相应的电梯导航小Ii添加类。

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
        * {
            padding: 0;
            margin: 0;
        }

        body {
            height: 3000px;
        }

        .w {
            width: 1200px;
            margin: 0 auto;
        }

        .con {
            height: 500px;
            background-color: yellow;

        }

        .yifu {
            height: 300px;
            background-color: pink;
        }

        .jiadian {
            height: 300px;
            background-color: skyblue;
        }

        .dianshi {
            height: 300px;
            background-color: purple;
        }

        .bangong {
            height: 300px;
            background-color: hotpink;
        }

        .cast {
            display: none;
            position: fixed;
            top: 0;
            left: 20px;
            width: 100px;
            border: 1px solid #000;
            text-align: center;
        }

        .item {
            height: 30px;
            line-height: 30px;
            cursor: pointer;
        }

        .current {
            background-color: #FF5A00;
        }
    </style>
</head>

<body>
    <div class="con">

    </div>
    <div class="yifu w">
        <h3>衣服模块</h3>
    </div>
    <div class="jiadian w">
        <h3>家电模块</h3>
    </div>
    <div class="dianshi w">
        <h3>电视模块</h3>
    </div>
    <div class="bangong w">
        <h3>办公模块</h3>
    </div>
    <div class="cast">
        <div class="item">
            衣服部分
        </div>
        <div class="item">
            家电部分
        </div>
        <div class="item">
            电视部分
        </div>
        <div class="item">
            办公部分
        </div>
    </div>
    <script>
        $(function () {
            // 当我们点击了item 此时不需要执行页面滚动里面的代码 页面滚动事件里面的 item 的背景选择 添加 current
            // 节流阀 互斥锁
            var flag = true;
            // 1.显示隐藏电梯导航
            // 页面卷去的头部 = 衣服模块距离顶部的距离
            // 因为放在页面滚动的时候 cast才显示 如果刷新了就不显示了 所以需要函数封装
            toggleTool();
            // 切换侧边导航的状态
            function toggleTool() {
                if ($("html, body").scrollTop() >= $(".yifu").offset().top) {
                    $(".cast").stop().fadeIn(200);
                } else {
                    $(".cast").stop().fadeOut(200);

                }
            };
            // 页面滚动事件 $(window).scroll()
            $(window).scroll(function () {
                // 指定位置显示导航
                toggleTool();
                // 3.页面滑动相对应的内容区域 导航栏选项 item 添加或删除类
                // 通过内容区域索引号 找到导航栏选项的索引
                // 页面滚动到某个内容区域，左侧电梯导航item相应添加和删除current类名
                if (flag) {
                    $(".w").each(function (index, domEle) {
                        if ($(document).scrollTop() >= $(domEle).offset().top) {
                            $(".item").eq(index).addClass("current").siblings(".item").removeClass("current");
                        }
                    });
                }
            });

            // 2.点击电梯导航页面可以滚动到相应内容区域
            $(".item").click(function () {
                // 点击item时 不需要进行类的切换 关闭节流阀
                flag = false;
                // console.log($(this).index());  // 获取当前点击的item的索引号
                // 当我们每次点击小li 就需要计算出页面要去往的位置
                // 选出对应索引号的内容区的盒子  计算它的 offset().top
                var current = $(".w").eq($(this).index()).offset().top
                $("html, body").stop().animate({
                    scrollTop: current
                }, function () {
                    flag = true; // 当页面动画效果完成后打开节流阀;
                    // 点击之后，当前小li的类名加上，当前小li的其他兄弟去除类名
                    // $(this).addClass("current").siblings(".item").removeClass("current");
                })
                // 同时选中的选项添加类
                $(this).addClass("current").siblings(".item").removeClass("current");
            });
        });

        // 此时程序有bug, 当我们点击导航选项item时, 会有闪烁的背景色变化
        // 原因是只要我们点击item,就会给当前item添加背景色的类其余移除类
        // 解决方法就是在点击item是不需要进行背景色类的切换
        // 设置节流阀
    </script>
</body>

</html>
```

# 三、jQuery事件

## 1.jQuery事件注册

**单个事件注册**

语法:

```javascript
element.事件(function() {})
```

```javascript
$("div").click(function() {事件处理程序 })
```

其他事件和原生基本一致。

比如mouseover、mouseout、 blur、 focus、 change、 keydown、 keyup、 resize、 scroll等

## 2.jQuery事件处理

### 2.1事件处理on()绑定事件

on()方法在匹配元素上绑定一个或多 个事件的事件处理函数

**语法：**

```javascript
element.on(events, [selector], fn)
```

1. events:一个或多 个用空格分隔的事件类型,如"click' 或"keydown"。
2. selector:元素的子元素选择器。
3. fn:回调函数即绑定在元素身上的侦听函数。

**on()方法优势1 ：**

可以绑定多个事件,多个处理事件处理程序。

```javascript
$("div").on({
    mouseenter: function() {},
    mouseout: function() {},
    click: function() {}
});
```

如果事件处理程序相同

```javascript
$("div").on("mouseover mouseout", function() {
	$(this).toggleClass("current");
});
```

**on()方法优势2 ：**

可以事件委派操作。事件委派的定义就是,把原来加给子元素身上的事件绑定在父元素身上,就是把事件委派给父元素。

```javascript
// 事件是绑定在ul身上的 所以只有一个ul添加了点击事件 但是触发对象是小li 只有我点击了小li才会触发 点击小li之后有事件冒泡 会冒到父元素ul身上 ul绑定了点击事件 所以就会执行这个程序
$('ul') .on('click', 'li', function() {
	alert("hello world!");
	});
```

在此之前有bind0, live() delegate(等方法来处理事件绑定或者事件委派,最新版本的请用**on**替代他们。

**on()方法优势3 :**

动态创建的元素, click() 没有办法绑定事件, on(可以给动态生成的元素绑定事件

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
            width: 200px;
            height: 200px;
            background: hotpink;
        }

        .current {
            background-color: skyblue;
        }
    </style>
</head>

<body>
    <div></div>
    <ul>
        <li>大家好啊</li>
        <li>大家好啊</li>
        <li>大家好啊</li>
        <li>大家好啊</li>
        <li>大家好啊</li>
        <li>大家好啊</li>
    </ul>

    <ol>

    </ol>
    <script>
        $(function () {
            // 1.单个事件注册
            // $("div").mouseenter(function () {
            //     $(this).css("backgroundColor", "pink");
            // });
            // $("div").click(function () {
            //     $(this).css("backgroundColor", "skyblue");
            // });

            // 可以绑定多个事件, 多个处理事件处理程序。
            // $("div").on({
            //     click: function () {
            //         $(this).css("backgroundColor", "skyblue")
            //     },
            //     mouseenter: function () {
            //         $(this).css("backgroundColor", "pink")

            //     }
            // })
            // 如果事件处理程序相同
            // $("div").on("mouseenter  mouseleave", function () {
            //     $(this).toggleClass("current")
            // });

            // 事件委派
            // $("ul").on("click", "li", function () {
            //     alert(11);
            // })

            // 给新创建的li 绑定点击事件
            // var li = $("<li>后来者</li>")
            // $("ol").append(li);
            // $("ol li").click(function () {
            //     alert(11);
            // })

            // on可以给未来动态创建的元素绑定事件
            $("ol").on("click", "li", function () {
                alert(11);
            })
            $("ol").append("<li>后来者</li>");
        });

    </script>
</body>

</html>
```

### 案列：微博发布案列

1. 点击发布按钮,动态创建一个小i ,放入文本框的内容和删除按钮,并且添加到ul中。
2. 点击的删除按钮,可以删除当前的微博留言。

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
        ul {
            list-style: none;
            padding: 0;
            margin: 0;
        }

        .box {
            position: relative;
            width: 600px;
            height: auto;
            border: 1px solid #000;
            margin: 100px auto;
        }

        .txt {
            resize: none;
            outline: none;
            width: 400px;
            height: 200px;
            margin: 50px 100px;
            /* transform: translate(75%, 50%); */
        }

        span {
            position: absolute;
            left: 32px;
            top: 238px;
        }

        .btn {
            position: absolute;
            right: 32px;
            top: 238px;
        }

        ul {
            height: auto;
            width: 400px;
            position: absolute;
            left: 106px;
            bottom: 22px;

        }

        ul li {
            display: none;
        }

        a {
            align-self: right;
        }
    </style>
</head>

<body>
    <div class="box">
        <textarea name="text" id="" cols="30" rows="10" class="txt">你好</textarea>
        <span>发布微博</span>
        <button class="btn">发布</button>
        <ul>

        </ul>
    </div>
    <script>
        $(function () {


            function addHeight(liHeight) {
                var h = $(".box").height();
                $(".box").height(h + liHeight);
            };

            function removeHeight(liHeight) {
                var h = $(".box").height();
                $(".box").height(h - liHeight);
            };
            // 1.点击发布按钮, 动态创建一个小li，放入文本框的内容和删除按钮， 并且添加到ul中
            $(".btn").on("click", function () {
                var li = $("<li></li>");
                // trim() 删除字符串开始和末尾的空格  如果为空 直接返回提示不能为空
                if ($(".txt").val().trim("") == "") {
                    return alert("内容不能为空! FUCKYOU")
                } else {
                    li.html($(".txt").val() + "<a href='javascript:;'>删除</a>");
                    $("ul").prepend(li)
                    $(li).slideDown();
                    $("li").css({
                        display: "flex",
                        "justify-content": "space-between"
                    });
                    addHeight(20);
                    $(".txt").val("");
                }

                var fileName = $.trim($(".txt").val())
                console.log(fileName);;
            });
            // 2.点击的删除按钮，可以删除当前的微博留言
            $("ul").on("click", "a", function () {
                $(this).parents("li").slideUp(function () {
                    $(this).remove();
                    removeHeight(20);
                })
            });


        });
    </script>
</body>

</html>
```

### 2.2 事件处理 off() 解绑事件

off()方法可以移除通过on()方法添加的事件处理程序。

```javascript
$("p").off() // 解绑p元素所有事件处理程序
$("p").off("click") // 解绑p元素上面的点击事件后面的foo 是侦听函数名
$("ul").off("click", "li"); // 解绑事件委托
```

如果有的事件只想触发一次，可以使用one(来绑定事件。

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
            width: 200px;
            height: 200px;
            background-color: hotpink;
        }
    </style>
</head>

<body>
    <div></div>
    <ul>
        <li>世上无难事</li>
        <li>世上无难事</li>
        <li>世上无难事</li>
        <li>世上无难事</li>
    </ul>
    <script>
        $(function () {
            $("div").on({
                click: function () {
                    console.log("点击了这个盒子");
                },
                mouseenter: function () {
                    console.log("经过了这个盒子");
                }
            });
            // $("div").off(); // 解绑在div身上全部的事件
            // $("div").off("click"); // 解绑在div身上的点击事件

            $("ul").on("click", "li", function () {
                alert(11);
            });

            $("ul").off("click", "li");  // 解绑事件委托
            // 如果用one绑定事件 就只会触发一次
            $("ul li").one("click", function () {
                alert(22);
            })
        });
    </script>
</body>

</html>
```

### 2.3 自动触发事件trigger()

有些事件希望自动触发,比如轮播图自动播放功能跟点击右侧按钮一致。可以利用定时器自动触发右侧按钮点击事件,不必鼠标点击触发。

```javascript
element.click() // 第一种简写形式 会触发元素的默认行为
```

```javascript
element.trigger ("type") //第二种自动触发模式 type事件类型 会触发元素的默认行为
```

```javascript
$("p").on("click", function () {
    alert("hi~"); 
});
$("p").trigger("click"); //此时自动触发点击事件，不需要鼠标点击 
```

```javascript
element.triggerHandler(type) // 第三种自动触发模式 就是不会触发元素的默认行为
```

## 3.jQuery 事件对象

事件被触发,就会有事件对象的产生。

```javascript
element.on(events, [selector] , function (event) { })
```

阻止默认行为: event.preventDefault(）或者return false

阻止冒泡: event.stopPropagation()

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
            width: 200px;
            height: 200px;
            background-color: hotpink;
        }
    </style>
</head>

<body>
    <div></div>
    <script>
        $(function () {
            $(document).on("click", function () {
                console.log("点击了document");
            });

            $("div").on("click", function (event) {
                // console.log(event);
                console.log("点击了div"); // 事件冒泡 点击了div 会冒泡到 document
                // 阻止冒泡
                event.stopPropagation();
            });
        });
    </script>
</body>

</html>
```

### 3.1 jQuery 对象拷贝

如果想要把某个对象拷贝(合并)给另外-一个对象使用,此时可以使用$ . extend ()方法

**语法：**

```javascript
$.extend([deep], target, object1, [objectN] )
```

1. deep：如果设为true为深拷贝，默认为false浅拷贝
2. target:要拷贝的目标对象
3. object1:待拷贝到第一个对象的对象。
4. objectN:待拷贝到第N个对象的对象。
5. 浅拷贝是把被拷贝的对象复杂数据类型中的地址拷贝给目标对象,修改目标对象会影响被拷贝对象。
6. 深拷贝,前面加true，完全克隆(拷贝的对象,而不是地址) ,修改目标对象不会影响被拷贝对象。

![image-20220423152733085](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220423152733085.png)

![image-20220423152140301](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220423152140301.png)

```javascript
$(function () {
            // var targetObj = {
            //     id: 0,
            // };
            // var Obj = {
            //     id: 1,
            //     msg: {
            //         name: "andy"
            //     }
            // };
            // $.extend(targetObj, Obj);
            // console.log(targetObj); // 会覆盖targetObj 里面原来的感觉
            // console.log(Obj);
            // 1.浅拷贝把原来对象里面的复杂数据类型地址拷贝给目标对象
            // targetObj.msg.age = 10;
            // console.log(targetObj);
            // console.log(Obj);

            // 2.深拷贝把里面的数据完全复制一份给目标对象 如果里面有不冲突的属性 会合并到一起
            var targetObj = {
                id: 0,
                msg: {
                    sex: "男"
                }
            }
            var Obj = {
                id: 1,
                msg: {
                    name: "andy"
                }
            }
            $.extend(true, targetObj, Obj);
            // console.log(targetObj); // 会覆盖targetObj 里面原来的数据
            targetObj.msg.age = 20;
            console.log(targetObj); // msg: {sex: "男"， name: "andy"}
            console.log(Obj);
        })
```

### 3.2 jQuery多库共存

**问题概述:**

jQuery使用$作为标示符，随着jQuery的流行，其他js库也会用这$作为标识符,这样一起使用会引起冲突。

**客观需求:**

需要一个解决方案,让jQuery和其他的js库不存在冲突,可以同时存在,这就叫做多库共存。

#### jQuery解决方案:

1. 把里面的$符号统一改为jQuery。比如jQuery(”div")
2. jQuery变量规定新的名称: $.noConflict()     var xx = $.noConflict();

### 3.3 jQuery插件

jQuery功能比较有限,想要更复杂的特效效果,可以借助于jQuery插件完成。

注意:这些插件也是依赖于jQuery来完成的,所以必须要先弓l入jQuery文件,因此也称为jQuery插件。

**jQuery插件常用的网站:**

1. jQuery 插件库http://www.jq22.com/
2. jQuery之家http://www.htmleaf.com/

**jQuery插件使用步骤:**

1. 引入相关文件。( jQuery文件和插件文件)
2. 复制相关html、Css、 js (调用插件)。

**jQuery插件演示:**

1. 瀑布流

2. 图片懒加载(图片使用延迟加载在可提高网页下载速度。它也能帮助减轻服务器负载)

   当我们页面滑动到可视区域,再显示图片。

   我们使用jquery插件库EasyLazyload。 注意,此时的js弓|入文件和js调用必须写到DOM元素(图片)最后面

3. 全屏滚动( fullpage.js )

   gitHub : https://github.com/alvarotrigo/fullPage.js

   中文翻译网站: http://www.dowebok.com/demo/2014/77/

4. bootstrapJS插件:

   bootstrap框架也是依赖于jQuery开发的,因此里面的js插件使用, 也必须引入jQuery文件。

## 综合案列：toDolist

1. 文本框里面输入内容, 按下回车,就可以生成待办事项。
2. 点击待办事项复选框,就可以把当前数据添加到E完成事项里面。
3. 点击已完成事项复选框,就可以把当前数据添加到待办事项里面。
4. **但是本页面内容刷新页面不会丢失。**

**案列分析**

1. 刷新页面不会丢失数据,因此需要用到本地存储localStorage
2. 核心思路:不管按下回车,还是点击复选框,都是把本地存储的数据加载到页面中,这样保证刷新关闭页面不会丢失数据
3. 存储的数据格式: var todolist= [{ title: 'xxx' , done: false}]
4. 注意点1 :本地存储localStorage里面只能存储字符串格式, 因此需要把对象转换为字符串JSON.stringify(data)。
5. 注意点2 :获取本地存储数据,需要把里面的字符串转换为对象格式JSON.parse()我们才能使用里面的数据。

**案列：todoList按下回车把新数据添加到本地存储里面**

1. 切记:页面中的数据,都要从本地存储里面获取,这样刷新页面不会丢失数据,所以先要把数据保存到本地存储里面。
2. 利用事件对象.keyCode判断用户按下回车键( 13)。
3. 声明一个数组,保存数据。
4. 先要读取本地存储原来的数据(声明函数getData()) , 放到这个数组里面。
5. 之后把最新从表单获聪过来的数据,追加到数组里面。
6. 最后把数组存储给本地存储(声明函数savaDate())

**案列：todolist删除操作**

1. 点击里面的a链接,不是删除的Ii ,而是删除本地存储对应的数据。
2. 核心原理:先获取本地存储数据,删除对应的数据,保存给本地存储,重新渲染列表li
3. 我们可以给链接自定义属性记录当前的索引号 (因为a链接与a链接之间的关系不是兄弟关系，$(this).index()方法不能使用)
4. 根据这个索引号删除相关的数据- --数组的splice(i, 1)方法 splice(从哪里开始删，删几个)
5. 存储修改后的数据,然后存储给本地存储
6. 重新渲染加载数据列表
7. 因为a是动态创建的,我们使用on方法绑定事件

**案例: toDoList正在进行和已完成选项操作**

1. 当我们点击了小的复选框,修改本地存储数据,再重新渲染数据列表。
2. 点击之后,获取本地存储数据。
3. 修改对应数据属性done为当前复选框的checked状态。
4. 之后保存数据到本地存储
5. 重新渲染加载数据列表
6. load加载函数里面,新增一个条件, 如果当前数据的done为true就是已经完成的,就把列表渲染加载到ul里面
7. 如果当前数据的done为false，则是待办事项,就把列表渲染加载到ol里面

**案例:  toDoList统计正在进行个数和已经完成个数**

1. 在我们load函数里面操作
2. 声明2个变量: todoCount待办个数doneCount已完成个数
3. 当进行遍历本地存储数据的时候,如果数据done为false，则todoCount+ +,否则doneCount+ +
4. 最后修改相应的元素text()