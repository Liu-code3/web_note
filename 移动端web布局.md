# 1.移动端基础

## 1.1 浏览器现状

![image-20220317112014945](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220317112014945.png)

**总结：兼容移动端主流浏览器，处理Webkit内核浏览器即可。**

## 1.2 手机屏幕现状

![image-20220317112148622](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220317112148622.png)

## 1.3 常见移动端屏幕尺寸

| 设备                  | 尺寸(英寸) | 开发尺寸(px) | 物理像素(dpr) |
| --------------------- | ---------- | ------------ | ------------- |
| iphone3G              | 3.5        | 320*480      | 1.0           |
| iphone4/4S            | 3.5        | 320*480      | 2.0           |
| iphone5/5S/5c         | 4.0        | 320*568      | 2.0           |
| HTC One M8            | 4.5        | 360*640      | 3.0           |
| iphone6               | 4.7        | 375*667      | 2.0           |
| Nexus 4               | 4.7        | 384*640      | 2.0           |
| Nexus 5x              | 5.2        | 411*731      | 2.6           |
| iphone6 Plus          | 5.5        | 414*736      | 3.0           |
| Samsung Galaxy Note 4 | 5.7        | 480*853      | 3.0           |
| Sony Xperia Z Ultra   | 6.4        | 540*960      | 2.0           |
| Nexus 7（12)          | 7.0        | 600*960      | 1.3           |
| iPad Mini             | 7.9        | 768*1024     | 1.0           |

注意：以上数据均参考自 https://material.io/devices/

注意：作为前端开发，不建议大家去纠结dp、dpi、pt、ppi等单位

## 1.4 移动端调试方法

- Chrome DevTools(谷歌浏览器)的模拟手机调试
- 搭建本地web服务器，手机和服务器一个局域网内，通过手机访问服务器
- 使用外网服务器，直接IP或域名访问

## 1.5 总结

- 移动端浏览器我们主要对webkit内核进行兼容
- 我们现在开发的移动端主要针对手机端开发
- 现在移动端碎片化比较严重，分辨率和屏幕尺寸大小不一
- 学会用谷歌浏览器模拟手机界面以及调试

# 2.视口

详情可参考：https://juejin.cn/post/7046169975706353701

**视口(viewport)**就是浏览器显示页面内容的屏幕区域，视口可以分为布局视口、视觉视口和理想视口。

## 2.1 布局视口 layout viewport

- 一般移动设备的浏览器都默认设置了一个布局视口，用于解决早期的PC端页面在手机上显示的问题
- iOS，Android基本都将这个视口分辨率设置为980px，所以PC上的网页大多都能在手机上呈现，只不过元素看上去很小，一般默认可以通过手动缩放网页。

![image-20220317115324823](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220317115324823.png)

## 2.2 视觉视口 visual viewport

- 字面意思，它是用户正在看到的网站的区域。**注意：是网站的区域。**
- 我们可以通过缩放去操作视觉视口，但不会影响布局视口，布局视口仍保持原来的宽度。

![image-20220317115608737](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220317115608737.png)

## 2.3 理想视口 ideal viewport

- 为了使网站在移动端有最理想的浏览和阅读宽度而设定
- 理想视口，对设备来讲，是做理想的视口尺寸
- 需要手动添写meta视口标签通知浏览器操作
- meta视口标签的主要目的：布局视口的宽度应该与理想视口的宽度一致，简单理解就是设备有多宽末我们布局的视口就多宽。

## 2.4 总结

- 视口就是浏览器显示页面内容的屏幕区域
- 视口分为布局视口、视觉视口和理想视口
- 我们移动端布局想要的是理想视口就是手机屏幕有多宽，我们的布局视口就有多宽
- 想要理想视口，我们需要给我们的移动端页面添加meta视口标签

## 2.5 meta视口标签

```html
<meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0,maximum-scale=1.0,minimum-scale=1.0">
```

| 属性          | 解释说明                                             |
| ------------- | ---------------------------------------------------- |
| width         | 宽度设置的是viewport宽度，可以设置device-width特殊值 |
| device-width  | 设备宽度                                             |
| initial-scale | 初始缩放比，大于0的数字                              |
| maximum-scale | 最大缩放比，大于0的数字                              |
| minimum-scale | 最小缩放比，大于0的数字                              |
| user-scalable | 用户是否可以缩放，yes或no(1或0)                      |

## 2.6 标准的viewport设置

- 视口宽度和设备保持一致
- 视口的默认缩放比列1.0
- 不允许用户自行缩放
- 最大允许的缩放比列1.0
- 最小允许的缩放比列1.0

# 3.二倍图

## 3.1 物理像素&物理像素比

- 物理像素点指的是屏幕显示的最小颗粒，是物理真实存在的。这是厂商在出厂时就设置好了，比如苹果6/7/8是 750*1334
- 我们开发时候的1px不是一定等于1个物理像素的。 比如 苹果6/7/8 1px = 2个物理像素
- PC端页面，1px等于1个物理像素的，但是移动端就不尽相同
- 一个px的能显示的物理像素点的个数，称为物理像素比或屏幕像素比。
- PC端和早期的手机屏幕/普通手机屏幕：1CSS像素 = 1 物理像素的
- Retina(视网膜屏幕)是一种显示技术，可以把更多的物理像素点压缩至一块屏幕里，从而达到更高的分辨率，并提高屏幕显示的细腻程度。

![image-20220317153034366](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220317153034366.png)

## 3.2 多倍图

- 对于一张50px*50px的图片在手机Retina屏中打开，按照刚才的物理像素比会放大倍数。
- 在标准的viewport设置中，使用倍图来提高图片质量，解决在高清设备中的模糊问题
- 通常使用二倍图，因为iPhone6\7\8的影响，但是现在还存在3倍图4倍图的情况，这个看实际开发公司需求。
- 背景图片注意缩放问题

```html
/* 我们需要一个50*50像素(css像素)的图片 直接放到我们的iPhone8 里面会放大2倍 100*100 就会模糊 */
/* 我们采取的是 放一个 100*100图片 然后手动的把这个图片 缩小为50*50 (css像素) */
/* 我们准备的图片 比我们实际需要的大小 大2倍，这就方式就是2倍图 */
    img {
        /* 原始图片100*100px */
        width: 50px;
        height: 50px;
    }

    .box {
        /* 原始图片100*100px */
        background-size: 50px 50px;
    }
```

## 3.3 背景缩放 background-size

background-size属性规定背景图像的尺寸

```html
background-size: 背景图片宽度 背景图片高度;
```

- 单位：长度 | 百分比 | cover | contain
- cover把背景图片扩展至足够大，以使背景图像完全覆盖背景区域。
- contain把图像扩展至最大尺寸，以使其宽度和高度完全适应内容区域

```html
 div {
            width: 500px;
            height: 500px;
            border: 1px solid pink;
            background: url(images/demo.jpg) no-repeat;
            /* background-size: 图片的宽度 图片的高度; */
            /* background-size: 500px 200px; */
            /* 1.只写一个参数 肯定是宽度 高度省略了 会等比例缩放 */
            /* background-size: 500px; */
            /* 2.里面的单位可以跟%(百分比) 相对于父盒子而言 */
            /* background-size: 50%; */
            /* 3.cover 要完全覆盖div盒子 可能有部分背景图片显示不全 */
            /* background-size: cover; */
            /* 4.contain 高度和宽度等比例拉伸 当宽度 或者高度 铺满div盒子就不再进行拉伸了 */
            background-size: contain;
        }
```

## 3.4 多倍图切图 cutterman

<img src="C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220317191350724.png" alt="image-20220317191350724" style="zoom:50%;" />

- @3x 3倍图
- @2x 2倍图
- @1x 1倍图 原图

# 4.移动端开发选择

## 4.1 移动端主流方案

### 1.单独制作移动端页面(主流)

- 京东商城手机版
- 淘宝触屏版
- 苏宁易购手机版
- ...

### 2.响应式页面兼容移动端(其次)

- 三星手机官网
- ...

## 4.2 单独移动端页面(主流)

通常情况下，网址域名前面加**m(mobile)**可以打开移动端，通过判断设备，如果是移动端、设备打开，则跳到**移动端页面**。

![image-20220317192803579](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220317192803579.png)

## 4.3 响应式兼容PC移动端

三星电子官网：www.samsung.com/cn , 通过判断屏幕宽度来改变样式，以适应不同终端。

**缺点**：**制作麻烦**，需要花很大精力调**兼容性**问题

![image-20220317193122297](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220317193122297.png)

## 4.4 总结

现在市场常见的移动端开发有单独制作移动端页面 和 响应式页面 两种方案

现在市场主流的选择还是单独制作移动端页面

# 5.移动端技术解决方案

## 5.1 移动端浏览器

移动端浏览器基本以webkit内核为主，因此我们就考虑webkit兼容性问题。

我们可以放心使用H5标签和CSS标签。

同时我们浏览器的私有前缀我们只需要考虑添加webkit即可。

![image-20220317193642834](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220317193642834.png)

## 5.2 CSS初始化 **normalize.css**

移动端CSS初始化推荐使用normalize.css/

- Normalize.css：保护了有价值的默认值
- Normalize.css：修复了浏览器的bug
- Normalize.css：是模块化的
- Normalize.css：拥有详细的文档

官网地址：https://necolas.github.io/normalize.css/

## 5.3 CSS3盒子模型 box-sizing

- 传统模式宽度计算：盒子的宽度 = CSS中设置的width+border+padding
- CSS3盒子模型：盒子的宽度=CSS中设置的宽度width里面包含了border和padding，也就是说，我们的CSS3中的盒子模型，padding和border不会撑大盒子

```html
/* CSS3盒子模型 */
box-sizing: border-box;
 /* 传统盒子模型 */
box-sizing: content-box;
```

**如何选择盒子模型**

- 移动端可以全部CSS3盒子模型
- PC端如果完全需要兼容，我们就用传统模式，如果不考虑兼容性，我们就选择CSS3盒子模型

## 5.4 特殊样式

```html
		/* css3盒子模型 */
        box-sizing: border-box;

		/* 全局用css3盒子模型 */
        -webkit-box-sizing: border-box;

        /* 点击高亮我们需要清除 设置为transparent 完成透明 */
        -webkit-tap-highlight-color: transparent;

        /* 在移动端浏览器默认的外观在ios上加上这个属性才能给按钮和输入框自定义样式 */
        -webkit-appearance: none;
		 /* 禁用长按页面时的弹出菜单 */
		/* 清除IE10及以上版本input的叉叉（X）和密码输入框的眼睛图标 */
		input::-ms-clear {
		display: none;
		}
		input::-ms-reveal {
		display: none;
		}
		/*清除谷歌浏览器下的 search 叉号 */
		input[type=search]::-webkit-search-cancel-button {
		-webkit-appearance: none;
		}
		/*清除IE下的 search 叉号 */
		input[type=search]::-ms-clear {
		display: none;
		}
        img,
        a {
            -webkit-touch-callout: none;
        }
```

# 6.移动端常见布局

移动端布局和以前我们学习的PC端有所区别：

**1.单独制作移动端页面(主流)**

- 流失布局(百分比布局)
- flex弹性布局(强烈推荐)
- less+rem+媒体查询布局
- 混合布局

**2.响应式页面兼容移动端(其次)**

- 媒体查询
- bootstrap

## 6.1 流失布局(百分比布局)

- 流失布局，就是百分比布局，也称非固定像素布局。
- 通过盒子的宽度设置成百分比来根据屏幕的宽度来进行伸缩，不受固定像素的限制，内容向两侧填充。
- 流失布局方式是移动web开发使用的比较常见的布局方式。![image-20220317210602253](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220317210602253.png)

- max-width 最大宽度(max-width 最大高度)
- min-width 最小宽度 (min-width 最小高度)

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
            margin: 0;
            padding: 0;
        }

        section {
            width: 100%;
            max-width: 980px;
            min-width: 390px;
            display: flex;
            margin: 0 auto;
        }

        section div {
            width: 50%;
            height: 600px;
        }

        section div:nth-child(1) {
            background-color: pink;
        }

        section div:nth-child(2) {
            background-color: hotpink;
        }
    </style>
</head>

<body>
    <section>
        <div></div>
        <div></div>
    </section>
</body>

</html>
```

### 案列：京东移动端首页

**访问地址：m.jd.com**

#### 1.技术选型

方案：我们采取单独制作移动页面方案

技术：布局采取流失布局

#### 2.搭建相关文件夹结构

![image-20220317222000416](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220317222000416.png)

#### 3.设置视口标签以及引入初始化样式

```html
<meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
/* 引入初始化样式 */
<link rel="stylesheet" href="css/normalize.css">
/* 引入自己写的样式 */
<link rel="stylesheet" href="css/index.css">
```

#### 4.常用初始化样式

```
body {
	margin: 0 auto;
	min-width: 320px;
	max-width: 640px;
	background: #fff;
	font-size: 14px;
	font-family: -apple-system, Helvetica, sans-serif;
	line-height: 1.5;
	color: #666;
}
```

**三栏布局 ：中间自适应 两边定位**

#### 5.二倍精灵图做法

- 在firework里面把精灵图等比例缩放为原来的一半
- 之后根据大小 测量坐标
- 注意代码里面background-size也要写：精灵图原来宽度的一半

#### 6.图片格式

##### dpg图片压缩技术

京东自主研发推出dpg图片压缩技术，经测试该技术，可直接节省用户近50%的浏览流量，极大的提升了用户的网页打开速度。能够兼容jpeg，实现全平台、全部浏览器的兼容支持，经过内部和外部上万张图片的人眼浏览测试后发现，压缩后的图片和webp的清晰度对比没有差距。

##### webp图片格式

谷歌开发的一种旨在加快图片加载速度的图片格式，图片压缩体积大大约只有jpeg的2/3，并能节省大量的服务器宽度资源和数据空间。

## 6.2 flex布局

### 1.传统布局与flex布局

#### 传统布局

- 兼容性差
- 布局繁琐
- 局限性，不能在移动端很好的布局

#### flex弹性布局

- 操作方便，布局极为简单，移动端应用很广泛
- PC端浏览器支持情况较差
- IE 11或更低版本，不支持或仅部分支持

> 建议：
>
> 1. 如果是PC端页面布局，我们还是传统布局
> 2. 如果是移动端或者不考虑兼容性问题的PC端页面布局，我们还是使用flex弹性布局

### 2.flex布局原理

#### 2.1 布局原理

flex是flexible Box的缩写，意为“弹性布局”，用来为盒状模型提供最大的灵活性，任何一个容器都可以指定为flex布局。

- 当我们为父盒子设为flex布局以后，子元素的float、clear和vertical-align属性将失效
- 伸缩布局=弹性布局=伸缩盒布局=弹性盒布局=flex布局

采用flex布局的元素，称为Flex容器(flex container)，简称“容器”，它的所有子元素自动称为容器成员，称为Flex项目(flex item)，简称"项目“。

- 父元素就是flex的容器
- 子元素就是子容器flex项目
- 子容器可以横向排列也可以纵向排列

**总结flex布局原理：就是通过给父盒子添加flex属性，来控制盒子的**位置和排列方式。

![image-20220319201819239](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220319201819239.png)

### 3.flex布局父项常见属性

#### 3.1 常见父项属性

以下由6个属性是对于父元素设置的

- flex-direction: 设置主轴的方向
- justify-content: 设置主轴上的子元素排列方式
- flex-wrap: 设置子元素是否换行
- align-content: 设置侧轴上的子元素的排列方式(多行)
- align-items: 设置侧轴上的子元素排列方式(单行)
- flex-flow: 整合属性，相当于同时设置了flex-direction和flex-wrap

#### 3.2 flex-direction设置主轴的方向

##### 1.主轴和侧轴

在flex布局中，是分为主轴和侧轴两个方向，同样的叫法有：行和列，x轴和y轴

- 默认主轴方向就是x轴方向，水平向右
- 默认侧轴方向就是y轴方向，水平向下

![image-20220319202904157](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220319202904157.png)

##### 2.属性值

flex-direction属性决定主轴的方向(即项目的排列方向)

注意：主轴和侧轴是会变化的，就看flex-direction设置谁为主轴，剩下的就是侧轴，而我们的子元素就是跟着主轴来排列的

| 属性值         | 说明           |
| -------------- | -------------- |
| row            | 默认值从左到右 |
| row-reverse    | 从右到左       |
| column         | 从上到下       |
| column-reverse | 从下到上       |

```html
 <style>
        div {
            /* 给父级添加flex属性 */
            display: flex;
            flex-direction: row-reverse;
            /* width: 900px; */
            height: 300px;
            background-color: hotpink;
            /* 默认的主轴是x轴 行 row 那么y轴就是 侧轴 */
            /* 我们的元素是跟着主轴的方向排列 */
            /* flex-direction: row; */
            /* 简单了解 翻转  从右到左*/
            /* flex-direction: row-reverse; */
            /* 我们可以把我们的主轴设置为y轴 那么x轴 就成了侧轴 */
            flex-direction: column;
        }

        div span {
            width: 150px;
            height: 100px;
            background-color: skyblue;
            margin-right: 2px;
        }
    </style>
</head>

<body>
    <div>
        <span>1</span>
        <span>2</span>
        <span>3</span>
    </div>
</body>

</html>
```

#### 3.3 justify-content设置主轴上的子元素排列方式

justify-content属性定义了项目在主轴上的对齐方式

**注意：使用这个属性之前一定要确定好主轴是哪个**

| 属性值        | 说明                                        |
| ------------- | ------------------------------------------- |
| flex-start    | 默认值 从头部开始 如果主轴是x轴，则从左到右 |
| flex-end      | 从尾部开始排列                              |
| center        | 在主轴居中对齐(如果主轴是x轴则水平居中)     |
| space-around  | 平分剩余空间                                |
| space-between | 先两边贴边 再平分剩余空间(重要)             |
| space-evenly  | 项目与项目之间以及项目与边框之间的距离相等  |

```html
<style>
        div {
            display: flex;
            /* 决定y轴为主轴 */
            flex-direction: column;
            /* 决定x轴为主轴 */
            /* flex-direction: row; */
            /* 项目按照主轴的方向排列 */
            justify-content: space-between;
            width: 800px;
            height: 350px;
            background-color: pink;
        }

        div span {
            width: 150px;
            height: 100px;
            background-color: skyblue;
        }
    </style>
</head>

<body>
    <div>
        <span>1</span>
        <span>2</span>
        <span>3</span>
    </div>
</body>

</html>
```

#### 3.4 flex-wrap设置子元素是否换行

默认情况下，项目都排在一条线(又称“轴线”)上，flex-wrap属性定义，flex布局中默认是不换行的。

flex布局中，默认的子元素是不换行的，如果装不下，会缩小子元素的宽度(子元素在设置宽度的情况下也会缩小)，放到父元素里面。

| 属性值 | 说明           |
| ------ | -------------- |
| nowrap | 默认值，不换行 |
| wrap   | 换行           |

```html
<style>
        div {
            display: flex;
            /* justify-content: space-between; */
            /* flex布局中，默认的子元素是不换行的，如果装不下，会缩小子元素的宽度(子元素在设置宽度的情况下也会缩小)，放到父元素里面。 */
            flex-wrap: wrap;
            width: 800px;
            height: 300px;
            background-color: pink;
        }

        div span {
            width: 150px;
            height: 100px;
            background-color: skyblue;
        }
    </style>
</head>

<body>
    <div>
        <span>1</span>
        <span>2</span>
        <span>3</span>
        <span>4</span>
        <span>5</span>
        <span>6</span>
        <span>7</span>
        <span>8</span>
        <span>9</span>
    </div>
</body>

</html>
```

#### 3.5 align-items设置侧轴上的子元素排列方式(单行)

该属性是控制子项在侧轴(默认是y轴)上的排列方式，在子项为单项的时候使用。

stretch 子元素不能设置高度

| 属性值     | 说明                   |
| ---------- | ---------------------- |
| flex-start | 从上到下               |
| flex-end   | 从下到上               |
| center     | 挤在一起居中(垂直居中) |
| stretch    | 拉伸(默认值)           |

```html
<style>
        div {
            display: flex;
            /* 默认的主轴是x轴  在x轴上水平居中 */
            /* justify-content: center; */
            /* y轴就是侧轴 在y轴上垂直居中 */
            /* align-items: center; */

            /* 主轴是y轴 在y轴上垂直居中 */
            flex-direction: column;
            justify-content: center;
            /* x轴就是侧轴 在x轴上水平居中*/
            align-items: center;
            width: 800px;
            height: 400px;
            background-color: pink;
        }

        div span {
            width: 150px;
            height: 100px;
            background-color: skyblue;
        }
    </style>
</head>

<body>
    <div>
        <span>1</span>
        <span>2</span>
        <span>3</span>
    </div>
</body>

</html>
```

#### 3.6 align-content设置侧轴上的子元素的排列方式(多行)

设置子项在侧轴上的排列方式，并且只能用于子项出现**换行**的情况(多行)，在单项下是没有效果的。

| 属性值        | 说明                                       |
| ------------- | ------------------------------------------ |
| flex-start    | 默认值在侧轴的头部开始排列                 |
| flex-end      | 在侧轴的尾部开始排列                       |
| center        | 在侧轴中间显示                             |
| space-around  | 子项在侧轴平分剩余空间                     |
| space-between | 子项在侧轴先分布在两头，再平分剩余空间     |
| space-evenly  | 项目与项目之间以及项目与边框之间的距离相等 |
| stretch       | 设置子项元素高度平分父元素高度             |

##### align-content和align-items区别

- align-items适用于单行情况下，只有上对齐、下对齐、居中和拉伸。
- align-content适用于换行(多行)的情况下(单行情况下无效)，可以设置上对齐、下对齐、居中、拉伸以及平均分配空间等属性值
- 总结就是单行找align-items，多行找align-content

![image-20220319233831285](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220319233831285.png)

```html
<style>
	div {
            display: flex;
            /* 在换行情况下 才用align-content */
            flex-wrap: wrap;
            /* align-content: start; */
            align-content: space-evenly;
            width: 800px;
            height: 400px;
            background-color: pink;
        }

        div span {
            width: 150px;
            height: 100px;
            background-color: skyblue;
        }
    </style>
</head>

<body>
    <div>
        <span>1</span>
        <span>2</span>
        <span>3</span>
        <span>4</span>
        <span>5</span>
        <span>6</span>
        <span>7</span>
        <span>8</span>
    </div>
</body>

</html>
```

#### 3.7 flex-flow

flex-flow属性是flex-direction和flex-wrap属性的复合属性

```html
flex-wrap: row wrap;
```

- flex-direction: 设置主轴的方向
- justify-content: 设置主轴上的子元素排列方式
- felx-wrap: 设置子元素是否换行
- align-items: 设置侧轴上的子元素排列方式(单行)
- align-content: 设置侧轴上的子元素排列方式(多行)
- flex-flow: 复合属性，相当于同时设置了flex-direction和flex-wrap

### 4.flex布局子项常见属性

- flex子项目占的份数
- align-self控制子项目自己在侧轴的排列方式
- order属性定义子项目的排列顺序(前后顺序)

#### 4.1 flex属性

flex属性定义子项目分配剩余空间，用flex来表示占多少**份数**。

里面的子盒子可以写 % ，相对于父级来说的。例：flex：20%；

```html
.item {
	flex: <number>; /* default 0 */
}
```

```html
<style>
        * {
            padding: 0;
            margin: 0;
        }

        section {
            /* 父元素采取flex布局的情况下 */
            /* 默认的主轴是x轴 */
            display: flex;
            width: 60%;
            height: 100px;
            margin: 0 auto;
        }

        section div:nth-child(1) {
            width: 10%;
            /* height: 100px; */
            background-color: skyblue;
        }

        section div:nth-child(2) {
            /* 其他盒子宽高设置上，其余的就是剩余空间 */
            flex: 1;
            background-color: hotpink;
        }

        section div:nth-child(3) {
            width: 10%;
            /* height: 100px; */
            background-color: green;
        }

        p {
            /* 父元素采取flex布局的情况下 */
            /* 默认的主轴是x轴 */
            display: flex;
            width: 60%;
            height: 100px;
            margin: 100px auto;
            background-color: skyblue;
        }

        p span {
            /* 三个span直接平分p的宽度 */
            flex: 1;
        }
    </style>
</head>

<body>
    <section>
        <div></div>
        <div></div>
        <div></div>
    </section>

    <p>
        <span>1</span>
        <span>2</span>
        <span>3</span>
    </p>
</body>

</html>
```

#### 4.2 align-self控制子项自己在侧轴上的排列方式

align-self属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。

默认值为auto，表示继承父元素的algin-items属性，如果没有父元素，则等同于stretch。

```html
span:nth-child(2) {
	/* 设置自己在侧轴上的排列方式 */
	align-self: flex-end;
}
```

#### 4.3 order属性定义项目的排列顺序

数值越小，排列越靠前，默认为0.

注意：和z-index不一样，z-index是z轴前后顺序(叠罗汉)。

```html
<style>
        * {
            padding: 0;
            margin: 0;
        }

        div {
            display: flex;
            width: 60%;
            height: 100px;
            background-color: pink;
            margin: 0 auto;
        }

        div span {
            width: 100px;
            height: 50px;
            background-color: skyblue;

        }

        div span:nth-child(3) {
            /* 子项目自己的排列反向 */
            align-self: center;
        }

        div span:nth-child(2) {
            /* 默认的是order为0 1比0大 所在span2在span1前面 */
            order: 1;
        }
    </style>
</head>

<body>
    <div>
        <span>1</span>
        <span>2</span>
        <span>3</span>
    </div>
</body>

</html>
```

### 5.携程网首页案列制作

**访问地址：m.ctrip.com**

#### 5.1.技术选型

方案：我们采取单独制作移动页面方案

技术：布局采取flex布局

#### 5.2.搭建相关文件夹结构

![image-20220320152658875](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220320152658875.png)

#### 5.3.设置视口标签以及引入初始化样式

```html
<meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
/* 引入初始化样式 */
<link rel="stylesheet" href="css/normalize.css">
/* 引入自己写的样式 */
<link rel="stylesheet" href="css/index.css">
```

#### 5.4.常用初始化样式

```html
body {
	max-width: 540px;
	min-width: 320px;
	margin: 0 auto;
	font: normal 16px/1.5 PingFangSC-regular,Tahoma,Lucida Grande,Verdana,Microsoft Yahei,STXihei,hei;
	color: #000;
	background: #f2f2f2;
	overflow-x: hidden;
	-webkit-tap-highlight-color:transparent;
}
```

#### 5.5.常见模块命名

![image-20220320204215360](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220320204215360.png)

#### 5.6.常见flex布局思路

![image-20220320204307329](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220320204307329.png)

## 6.3 less+rem+媒体查询布局

### 1.rem基础

rem (root em)是一个相对单位，类似于em，em是父元素字体大小。

不同的是rem的基准是相对于html元素的字体大小。

比如，根元素(html)设置 font-size = 12px; 非根元素设置width: 2rem；则换成px表示就是12px；

1. em相对于父元素 的字体大小来说的 不会因为html根元素的字体大小而改变
2. rem 相对于 html元素 字体大小来说的 不会因为父元素的字体大小而改变
3. rem的优点就是可以通过修改html里面的文字大小来改变页面中元素的大小可以整体控制

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        /* body {
            max-width: 540px;
            min-width: 320px;
            margin: 0 auto;
            font: normal 16px/1.5 PingFangSC-regular, Tahoma, Lucida Grande, Verdana, Microsoft Yahei, STXihei, hei;
            color: #000;
            background: #f2f2f2;
            overflow-x: hidden;
            -webkit-tap-highlight-color: transparent;

        } */
        html {
            font-size: 10px;
        }

        div {
            font-size: 10px;
        }

        span {
            display: inline-block;
            /* 1.em相对于父元素 的字体大小来说的 不会因为html根元素的字体大小而改变*/
            width: 4em;
            height: 4em;
            background-color: pink;
        }

        p {
            /*2. rem 相对于 html元素 字体大小来说的 */
            width: 10rem;
            height: 10rem;
            background-color: skyblue;
        }

        /* 3.rem的优点就是可以通过修改html里面的文字大小来改变页面中元素的大小可以整体控制 */
    </style>
</head>

<body>
    <div>
        <span></span>
        <p></p>
    </div>
</body>

</html>
```

### 2.媒体查询

#### 2.1 什么是媒体查询

媒体查询(Media Query)是CSS3新语法。

- 使用@media查询，可以针对不同的媒体类型定义不同的样式
- @media可以针对不同的屏幕尺寸设置不同的样式
- 当你重置浏览器大小的过程中，页面也会根据浏览器的宽度和高度重新渲染页面
- 目前针对很多苹果手机，Android手机、平板等设备都用得到多媒体查询

#### 2.2 语法规范

```html
@media mediatype and|not|only (media feature) {
	CSS-Code;
}
```

- 用@media开头 注意@符号
- mediatype媒体查询
- 关键字 and |not| only
- media feature 媒体特性 必须有小括号包含

##### 1.mediatype查询类型

将不同的终端设备划分成不同的类型，称为媒体查询

| 值    | 解释说明                           |
| ----- | ---------------------------------- |
| all   | 用于所有设备                       |
| print | 用于打印机和打印预览               |
| scree | 用于电脑屏幕、平板电脑、智能手机等 |

##### 2.关键字

关键字将媒体类型或多个媒体特性连接到一起做为媒体查询的条件。

- and：可以将多个媒体特性连接到一起，相当于“且”的意思。
- not：排除某个媒体类型，相当于“非”的意思，可以省略。
- only：指定某个特定的媒体类型，可以省略。

##### 3.媒体特性

每种媒体类型都具有各自不同的特性，根本不同媒体类型的媒体特性设置不同的展示风格。我们暂且了解三个。

注意：1.他们要加小括号包含。2.max-width和min-width都是包含等于的

| 值        | 解释说明                           |
| --------- | ---------------------------------- |
| width     | 定义输出设备中页面可见区域的宽度   |
| min-width | 定义输出设备中页面最小可见区域宽度 |
| max-width | 定义输出设备中页面最大可见区域宽度 |

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        /* 这句话的意思就是：在我们屏幕上 并且最大的宽度是 800像素 设置我们想要的样式 */
        /* max-width: 800px; 小于等于800px  也就是小于等于800px 才显示我们设置的样式 */
        /* 媒体查询可以根据不同的屏幕尺寸在改变不同的样式 */
        @media screen and (max-width: 800px) {
            body {
                background-color: hotpink;
            }
        }

        @media screen and (max-width: 500px) {
            body {
                background-color: purple;
            }
        }
    </style>
</head>

<body>

</body>

</html>
```

#### 案列：根据页面宽度改变背景颜色

实现思路：

1. 按照从大到小的或者从小到大的思路。
2. 注意我们有最大值max-width和最小值min-width都是包含等于的
3. 当屏幕小于540像素，背景颜色变为蓝色(x<539)
4. 当屏幕大于等于540像素并且小于等于969像素的时候背景颜色为绿色( 540 =< x <=969)
5. 当屏幕大于等于970像素的时候，背景颜色为红色(x >= 970)

注意：为了防止混乱，媒体查询我们要按照从小到大或者从大到小的顺序来写，但是**我们最喜欢的还是从小到大来写，这样代码更简洁，利用了CSS层叠性.**

![image-20220323112920114](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220323112920114.png)

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        /* 1. 按照从大到小的或者从小到大的思路。
        2. 注意我们有最大值max-width和最小值min-width都是包含等于的 */
        /* 3. 当屏幕小于540像素，背景颜色变为蓝色(x<539) */
        @media screen and (max-width: 539px) {
            body {
                background-color: pink;
            }
        }

        /* 4. 当屏幕大于等于540像素并且小于等于969像素的时候背景颜色为绿色( 540 =< x <=969) */
        /* @media screen and (min-width: 540px) and (max-width: 969px) {
            body {
                background-color: hotpink;
            }
        } */
        @media screen and (min-width: 540px) {
            body {
                background-color: hotpink;
            }
        }



        /* 5. 当屏幕大于等于970像素的时候，背景颜色为红色(x >=970) */
        @media screen and (min-width: 970px) {
            body {
                background-color: yellow;
            }
        }
    </style>
</head>

<body>

</body>

</html>
```

#### 2.3 媒体查询+rem实现元素动态大小变化

rem单位是跟着html来走的，有了rem页面元素可以设置不同大小尺寸

媒体查询可以根据不同设备宽度来修改样式

媒体查询+rem 就可以实现不同设备宽度，实现页面元素大小的动态变化。

#### 案列：媒体查询+rem实现元素变化

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

        @media screen and (min-width: 320px) {
            html {
                font-size: 20px;
            }


        }

        @media screen and (min-width: 600px) {
            html {
                font-size: 40px;
            }


        }

        div {
            height: 1rem;
            font-size: .5rem;
            text-align: center;
            line-height: 1rem;
            background-color: hotpink;
        }
    </style>
</head>

<body>
    <div>购物车</div>
</body>

</html>
```

#### 2.4 引入资源(理解)

当样式比较繁多的时候，我们可以针对不同的媒体使用不同shtylesheets(样式表)，原理，就是直接在link中判断设备的尺寸，然后引用不同的css文件。

语法：

```html
<link rel="stylesheet" href="mystylesheet1.css" media="mediatype and | not| only (media feature)"
```

例：

```html
<link rel="stylesheet" href="./css/style640.css" media="screen and (min-width: 640px)">
```

### 3.Less基础

#### 3.1 维护css的弊端

css是一门非程序式语言，没有变量、函数、SCOPE(作用域)等概念。

- CSS需要书写大量看似没有逻辑的代码，CSS冗余度是比较高的。
- 不方便维护及扩展，不利用复用。
- CSS没有很好的计算能力
- 非前端开发工程师来讲，往往会因为缺少CSS编写经验而很难写出组织良好且易于维护的CSS代码项目。

#### 3.2 Less介绍

Less(Leaner Style Sheets 的缩写) 是一门CSS扩展语言，也成为CSS预处理器。做为CSS的一种形式的扩展，它并没有减少CSS的功能，而是在现有的CSS语法上，为CSS加入程序式语言的特性。

它在CSS的语法基础之上，引入了变量，Mixin(混入)，运算以及函数等功能，大大简化了CSS的编写，并且降低了CSS的维护成本，就像它的名称所说的那样，Less可以让我们用更少的代码做更多的事情。

Less中文网址：http://lesscss.cn/

可以参考网址：https://juejin.cn/post/7035590363418984455

常见的CSS预处理器：Sass、Less、Stylus

一句话：**Less是一门CSS预处理器，它扩展了CSS的动态特性**

#### 3.3 Less使用

我们首先新建一个后缀名为less的文件，在这个less文件里面书写less语句。

- less变量
- less编译
- less嵌套
- less运算

##### 1. Less变量

变量是指没有固定的值，可以改变的。因为我们CSS中的一些颜色和数值等经常使用。

语法：@变量名：值；

(1).变量命名规范

- 必须有@为前缀
- 不能包含特殊字符
- 不能以数字开头
- 大小写敏感

```less
@color: pink;
// 变量名区分大小写， @color 与 @Color 是不同的变量
// 定义了一个字体为14的变量
@font14: 14px;
body {
    background-color: @color;
}

div {
    background-color: @color;
}

a {
    font-size: @font14;
    color: @color;
}
```

##### 2.less编译

本质上，Less包含一套自定义的语法及一个解析器，用户根据这些语法定义自己的样式规则，这些规则最终会通过解析器，编译生成对应的CSS文件。

所以，我们需要把我们的less文件，编译生成为CSS文件，这样我们的html页面才能使用。

Easy LESS 插件用来把less文件编译为css文件。安装完毕插件，重新加载下vs code，只要保存一下Less文件，会自动生成CSS文件。

##### 3.Less嵌套

我们经常用到选择器的嵌套

```css
#header .logo {
	width: 100px;
}
```

Less嵌套写法

```less
#header {
    // less嵌套 子元素的样式直接写到父元素里面就好了
	.logo {
		width: 100px;
	}
}
```

如果遇见(交集 | 伪类 | 伪元素选择器)

- 内层选择器的前面没有&符号 ，则它被解析为父选择器的后代。
- 如果有&字符，它就被解析为父元素自身或父元素的伪类。

```css
a:hover {
	color: pink;
}

a::before {
    content: "";
}
```

Less嵌套写法

```less
a {
    // 如果有伪类、交集选择器、伪元素选择器 我们内层选择器的前面需要加&
	&:hover {
		color: pink;
	}
    &::before {
        content: "";
    }
}


```

##### 4.less运算

任何数字、颜色或者变量都可以参与运算。就是Less提供了加(+)、减(-)、乘(*)、除(/)算术运算。

```less
/* Less 里面写 */
@width: 10px + 5;
div {
    border: @width solid red;
}

/* 生成的css */
div {
    border: 15px solid red;
}

```

```less
/* Less 里面写 */
@width: 10px;
width: (@width + 5) * 2;
```

注意：

- 乘号(*)、**除号(/) 要用括号()**起来 的写法
- **运算符中间左右有个空格隔开1px + 5**
- 对于两个不同的单位的值之间的运算，运算结果的值取第一个值的单位。
- 如果两个值之间只有一个值有单位，则运算结果就取该单位。

```less
@width: (100px / 2); // 除号(/) 要用括号()起来
@height: 80px + 6;
@bgColor: pink;

div {
    height: @height;
    width: @width * 3;
    background-color: @bgColor;
}
```

### 4.rem适配方案

1. 让一些不能等比自适应的元素，达到当设备尺寸发生改变的时候，等比例适配当前设备。
2. 使用媒体查询根据不同设备按比例设置html的字体大小，然后页面元素使用rem做尺寸单位，当html字体大小变化，元素尺寸也会发生变化，从而达到等比缩放的适配。

#### 4.1 rem实际开发适配方案

1. 按照设计稿与设备宽度的比列，动态计算并设置html根标签的font-size大小；(媒体查询)
2. CSS中，设计稿元素的宽、高，相对位置等取值，按照同等比例换算为rem为单位的值

#### 4.2 rem适配方案技术使用(市场主流)

##### **技术方案1**

- less
- 媒体查询
- rem

##### **技术方案2(推荐)**

- flexble.js
- rem

总结：

1. 两种方案现在都存在。
2. 方案2更简单，现阶段大家无需了解里面的js代码。

#### 4.3 rem实际开发适配方案1

rem + 媒体查询 + less技术

##### 1.设计稿常见尺寸宽度

| 设备       | 常见宽度                                                     |
| ---------- | ------------------------------------------------------------ |
| iPhone 4,5 | 640px                                                        |
| iPhone 678 | 750px                                                        |
| Android    | 常见320px、360px、384px、400px、414px、500px、720px 大部分4.7 ~ 5寸的安卓设备为720px |

一般情况下，我们以一套或两套效果图适应大部分的屏幕。放弃极端屏或对其优雅降级，牺牲一些效果，现在基本以750为准。

##### 2.动态设置html标签 font-size大小

1. 假设设计稿是750px
2. 假设我们把整个屏幕划分为15等份(划分标准不一，可以是20份也可以是10等份)
3. 每一份作为html字体大小，这里就是50px
4. 那么在320px设备的时候，字体大小为320px/15 就是21.33px
5. 用我们页面元素的大小除以不同的html字体大小会发现他们比例还是相同。

例如：

1. 我们以750为标准设计稿
2. 一个100*100像素的页面元素在750屏幕下，就是100 / 50转换为rem 是2rem * 2rem比例 是1:1
3. 320屏幕下，html字体大小为21.33 则2rem = 46.66px 此时宽和高都是 42.66 但是宽和高的比例还是 1:1
4. 但是已经能实现不同屏幕下  页面元素盒子 等比例缩放的效果

##### 3.元素大小取值方法

1. 最后的公式：页面元素的rem值 = （页面元素(px) / (屏幕宽度 / 划分的份数)）
2. （屏幕宽度 / 划分的份数） 就是 html的font-size的大小
3. 或者：页面元素的rem值 = （页面元素值(px) / html的font-size 字体大小）

##### 4.元素大小取值步骤

1. 首先我们选一套标准尺寸 750为准
2. 我们用屏幕尺寸 除以 我们划分的份数 得到了 html 里面的文字大小 但是我们知道不同屏幕下得到的文字大小是不一样的。
3. 页面元素的rem值 = （页面元素在 750px下 / html 里面的文字大小）

### 5.苏宁网首页案例制作

#### 5.1 rem适配方案1

技术方案1

- less
- 媒体查询
- rem

访问地址：m.suning.com

##### 1.技术选型

方案：我们采取单独制作页面方案

技术：布局采取rem适配布局(less + rem + 媒体查询)

设计图：本设计图采用750px设计尺寸

##### 2.搭建相关文件夹结构

![image-20220325142140981](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220325142140981.png)

##### 3.设置视口标签以及引入初始化样式

```html
<meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
<link rel="stylesheet" href="css/normalize.css">
```

##### 4.设置公共common.less文件

1. 新建common.less 设置好最常见的屏幕尺寸，利用媒体查询设置不同的html字体大小，因为除了首页其他页面也需要。
2. 我们关心的尺寸有320px、360px、375px、384px、400px、414px、424px、480px、540px、720px、750px
3. 划分的份数我们定为15等份
4. 因为我们pc端也可以打开我们苏宁移动端首页，我们默认html字体大小为50px，**注意这句话写到最上面。**

##### 5.新建index.less文件

1. 新建index.less 这里面写首页的样式
2. 将common.less引入到index.less里面 语法如下：

// 在 index.less 中导入 common.less文件

```less
@import “common”; 旧版less引入
@import url(common.less); 新版less引入
```

3.生成index.css引入到index.html里面

##### 6.body样式

```css
body {
	min-width: 320px;
	width: 15rem; // 设计稿为750px 划分为15份
	margin: 0 auto;
	line-height: 1.5; // 字体高度的1.5倍
	font-family: Arial, Helvetica;
	background: #F2F2F2;
}
```

#### 5.2 rem适配方案2

##### 简洁高效的rem适配方案flexible.js

###### 技术方案1

- less
- 媒体查询
- rem

###### 技术方案2

- flexible.js
- rem

手淘宝团队出的简洁高效移动端适配库

我们再也不需要在写不同屏幕的媒体查询，因为里面js做了处理

它的原理是把当前设备划分为10等份，但是不同设备下，比例还是一致的。

我们要做的，就是确定好我们当前设备的html字体大小就可以了

比如当前设计稿是750px，那么我们只需要把html文字大小设置为750px(750px / 10)就可以

里面页面元素rem值：页面元素的px值 / 75

剩余的，让flexible.js去算。

github地址：https://github.com/amfe/lib-flexible

##### 1.技术选型

方案：我们采取单独制作移动页面方案

技术：布局采取rem适配布局2(flexible.js + rem)

设计图：本设计图采用750px设计尺寸

##### 2.搭建相关文件夹结构

![image-20220327112736791](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220327112736791.png)

##### 3.设置视口标签以及引入初始化样式还有js文件

```html
<meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
<link rel="stylesheet" href="./css/normalize.css"> // 引入初始化样式
<link rel="stylesheet" href="./css/index.css"> // 引入自己的样式
```

我们页面需要引入这个js文件

```html
在index.html中引入flexible.js这个文件
<script src="./js/flexible.js"></script>
```

##### 4.body样式

```css
body {
	min-width:320px;
    max-width:750px; // 限制最大宽度和margin值就会有版心居中
    width:10rem; // flexible 给我们划分了 10等份
    margin: 0 auto;
    line-height: 1.5;
    font-family: Arial, Helvetica;
    background: #F2F2F2;
}
```

#### 5.3 VS code  px转换rem 插件 px to rem & rpx (cssrem)

这个插件默认的html文字大小 cssroot 为16px，也就是1rem = 16px

可以设置html字体大小基准值 ，在cssrem这个扩展里面搜索cssroot就直接可以修改

## 黑马面面布局开发

### 一、目的

1.了解移动端页面开发流程

2.掌握移动端常见布局思路

#### 1. 技术方案

1. 弹性盒子+rem+LESS
2. 最小适配设备为iphone5 320px 最大适配设备为iPhone8Plus(iPad能正常查看内容即可)

#### 2.代码规范

1.类名语义化，尽量精短、明确、必须以字母开头命名，且全部字母为小写，单词之间统一使用下划线"_" 连接

2.类名嵌套层次尽量不超过三层

3.尽量避免直接使用元素选择器

4.属性书写顺序

```
布局定位属性: display / position / float / clear /visibility / overflow
尺寸属性: width / height / margin / padding / border / background
文本属性: color / font / text-decoration / text-aligin / vertical-aligin
其他属性(CSS3): content / cursor / border-radius / box-shadow / text-shadow 
```

5.避免使用id选择器

6.避免使用通配符*和!important

#### 3.目录规范

项目文件夹：heimamm

​	样式文件夹：css

​	业务类图片文件夹：images

​	样式类图片文件夹：icons

​	字体类文件夹：fonts

## 二、流程开发

### 2.1 蓝湖/摹客协作平台

- UI设计师 psd效果图完成后，会上传到蓝湖/摹客里面，同时会拉前端工程师进入开发
- 大部分情况下，UI会把图片按照前端设计要求给切好，
- UI设计师 上传到蓝湖或者摹客

```
1.摹客官网地址：https://www.mockplus.cn/
2.ps安装摹客/蓝湖插件
3.打开ps摹客/蓝湖插件
4.上传(需要切图，需要先标注切图)
5.查看项目
6.邀请成员进入(分享按钮，链接地址)
```

- 前端设计师可以直接摹客/蓝湖测量取值

### 2.2 适配方案

- flex布局
- 百分比布局
- rem布局
- vw/vh布局
- 响应式布局
- 本次案列 flex + rem + flexible.js + LESS

### 2.3 初始化文件

- 引入 normalize.css

- less中初始化body样式

- 约束范围

- ```
  @media screen and (min-width: 750px) {
  	html {
  		font-size: 75px!important;
  	}
  }
  ```

### 2.4 布局模块

1. 头部模块  .header    高度为 80px 

2. nav 模块制作  多用 flex

3. 充电学习 阴影

```css
box-shadow: 0 0px 10px rgba(0, 0, 0, 0.1)
```

### 2.5 swiper 插件使用

 官网地址：<https://www.swiper.com.cn/>

- 下载需要的css和js文件  html页面中 引入相关文件
- 官网找到类似案例，复制html结构，css样式  js 语法
- 根据需求定制修改模块

### 2.6 图标字体上传下载

上传步骤：

1. 让UI美工准备好 图标字体（必须是svg格式）

2. 点上传按钮（保留颜色并提交）

   ![59331725820](C:\Users\kandy\AppData\Local\Temp\1593317258207.png)

3. 生成之后加入购物车即可

4. 点击下载 --- 下载代码

小技巧：  如何批量下载全部字体图标呢？

```javascript
var span = document.querySelectorAll('.icon-cover');
for (var i = 0, len = span.length; i < len; i++) {
     console.log(span[i].querySelector('span').click());
}
```

### 2.7  上传码云并发布部署静态网站

准备工作：  需要下载git软件    需要码云注册账号

git 可以把我们的本地网站提交上传到远程仓库（码云 gitee）里面    类似以前的   ftp  

码云  就是远程仓库， 类似服务器 

1. 码云创建新的仓库。   heimamm  
2. 利用git 提交 把本地网站提交到 码云新建的仓库里面
   - 在网站根目录右键-- Git Bash Here

   - 如果是第一次利用git提交，请配置好全局选项

```javascript
git config --global user.name "用户名"
git config --global user.email "你的邮箱地址"
```

- 初始化仓库

  ~~~javascript
  git init
  ~~~

- 把本地文件放到暂存区

  ~~~javascript
  git add .
  ~~~

- 把本地文件放到本地仓库里面

  ~~~javascript
  git commit -m '提交黑马面面网站'
  ~~~

- 链接远程仓库

  ~~~javascript
  git remote add origin 你新建的仓库地址
  ~~~

- 把本地仓库的文件推送到远程仓库 push

  ```javascript
  git remote add origin 你新建的仓库地址
  ```

3.码云部署发布静态网站

- 在当前仓库中，点击  “服务”   菜单 

  ![59333600753](C:\Users\kandy\AppData\Local\Temp\1593336007530.png)

- 选择 Gitee Pages

  ![59333604301](C:\Users\kandy\AppData\Local\Temp\1593336043016.png)

- 选择 “启动” 按钮

  ![59333609181](C:\Users\kandy\AppData\Local\Temp\1593336091814.png)

- 稍等之后，会拿到地址，就可以利用这个地址来预览网页了![59333616429](C:\Users\kandy\AppData\Local\Temp\1593336164295.png)

- 当然你也可以利用  草料二维码 生成二维码    <https://cli.im/>

  ![59333634981](C:\Users\kandy\AppData\Local\Temp\1593336349811.png)

最后： 如果提交网站，你不愿意用git 提交， 可以直接找到仓库，里面有文件，选择上传本地文件即可。

 ![59333642656](C:\Users\kandy\AppData\Local\Temp\1593336426566.png)

![59333645048](C:\Users\kandy\AppData\Local\Temp\1593336450481.png)

但是，1个小时内，只能上传 20个以内的文件， 前端人员，git必备技能

## 6.4 移动端web开发之响应式布局

### 1.响应式开发

#### 1.1 响应式开发原理

就是使用媒体查询针对不同宽度的设备进行布局和样式的设置，从而适配不同设备的目的。

| 设备划分               | 尺寸区别            |
| ---------------------- | ------------------- |
| 超小屏幕(手机)         | < 768px             |
| 小屏设备(平板)         | >= 768px ~ <992px   |
| 中等屏幕(桌面显示器)   | >= 992px ~ < 1200px |
| 宽屏设备(大桌面显示器) | >= 1200px           |

#### 1.2 响应式布局容器

响应式需要一个父级作为布局容器，来配合子级元素来实现变化效果。

原理就是在不同屏幕下，通过媒体查询来改变这个布局容器的大小，再改变里面子元素的排列方式和大小，从而实现不同屏幕下，看到不同的页面布局和样式变化。

**平时我们的响应式尺寸划分**

- 超小屏幕(手机、小于768px)：设置宽度为100%
- 小屏幕(平板、大于等于768px)：设置宽度为750px
- 中等屏幕(桌面显示器，大于等于992px)：设置宽度为970px
- 大屏幕(大桌面显示器，大于等于1200px)：设置宽度为1170px

宽度比屏幕尺寸低的原因就是：版心留个左右的空隙。

但是我们也可以根据实际情况自己定义划分

#### 1.3 响应式导航栏布局案列

需求分析

1. 当我们屏幕大于等于768像素，我们给布局容器container宽度为750px
2. container里面包含9个小li盒子，每个盒子的宽度定为cale(100% / 9),高度为30px，使用flex一行显示
3. 当我们屏幕缩放，宽度小于768像素的时候，container盒子宽度修改为100%宽度
4. 此时里面的9个小li，宽度修改为cale(100% / 3)，这样一行就只能显示3个小li，剩余下行显示。

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>导航栏响应式布局案列</title>
    <style>
        * {
            padding: 0;
            margin: 0;
        }

        ul {
            list-style: none;
        }

        .container {
            width: 750px;
            margin: 0 auto;
        }

        ul {
            display: flex;
            width: 100%;
            height: 100%;
        }

        ul li {
            display: flex;
            justify-content: center;
            align-items: center;
            width: calc(100% / 9);
            height: 30px;
            background-color: pink;
        }

        @media screen and (max-width: 767px) {
            .container {
                width: 100%;
            }

            ul {
                flex-wrap: wrap;
            }

            ul li {
                width: calc(100% / 3);
            }
        }
    </style>
</head>

<body>
    <div class="container">
        <ul>
            <li>导航栏</li>
            <li>导航栏</li>
            <li>导航栏</li>
            <li>导航栏</li>
            <li>导航栏</li>
            <li>导航栏</li>
            <li>导航栏</li>
            <li>导航栏</li>
            <li>导航栏</li>
        </ul>
    </div>
</body>

</html>
```

### 2.Bootstrap前端开发框架

#### 2.1 Bootstrap简介

Bootstrap来自Twitter(推特)，是目前最受欢迎的前端框架，Bootstrap是基于HTML、CSS和JavaScript的，它简介灵活，使得web开发更加快捷。

- 中文官网：http://www.bootcss.com/
- 官网：http://getbootstrap.com/
- 推荐使用：http://bootstrap.css88.com/

框架：顾名思义就是一套架构，它有一套比较完整的网页功能解决方案，而且控制权在框架本身，有预制样式、组件和插件，使用者要按照框架所规定的某种规范进行开发。

![image-20220330104437158](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220330104437158.png)

##### 1.优点

- 标准化的html+css编码规范
- 提供了一套简洁、直观、强悍的组件
- 有自己的生态圈。不断的更新迭代
- 让开发更简单，提高了开发的效率

##### 2.版本

- 2.x.x ：停止维护，兼容性好，代码不够简洁，功能不够完善
- 3.x.x ：目前使用最多，但是放弃了ie6-ie7.对ie8 支持但是界面效果不好，偏向于开发响应式布局。移动设备优先的WEB项目
- 4.x.x ：最新的，目前还不是很流行

#### 2.2 Bootstrap 使用

现在使用的是它的样式表。

控制权在框架本身，使用者要按照框架所规定的某种规范进行开发。

Bootstrap使用的四步：

1. 创建文件夹结构
2. 创建html骨架结构
3. 引入相关样式文件
4. 书写内容

##### 1.创建文件夹结构

!![image-20220330121356383](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220330121356383.png)

##### 2.创建html骨架结构

```html
<!doctype html>
<html lang="zh-CN">
  <head>
    <meta charset="utf-8">
    <!-- 要求当前网页使用IE浏览器最高版本的内核来渲染 -->
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <!-- 视口的设置：视口的宽度和设备一致，默认的缩放比列和PC端一样，用户不能自行缩放 -->
    <meta name="viewport" content="width=device-width, initial-scale=1，user-scalable=0">
    <!-- 上述3个meta标签*必须*放在最前面，任何其他内容都*必须*跟随其后！ -->
    <title>Bootstrap 101 Template</title>

    <!-- Bootstrap -->
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/3.4.1/css/bootstrap.min.css" integrity="sha384-HSMxcRTRxnN+Bdg0JdbxYKrThecOKuH5zCYotlSAcp1+c8xmyTe9GYg1l9a69psu" crossorigin="anonymous">

    <!-- HTML5 shim 和 Respond.js 是为了让 IE8 支持 HTML5 元素和媒体查询（media queries）功能 -->
    <!-- 警告：通过 file:// 协议（就是直接将 html 页面拖拽到浏览器中）访问页面时 Respond.js 不起作用 -->
    <!--低于ie9以下版本的浏览器 > 条件注释标签
    <!-- HTML5 shim 和 Respond.js 是为了让 IE8 支持 HTML5 元素和媒体查询（media queries）功能 -->
    <!-- 警告：通过 file:// 协议（就是直接将 html 页面拖拽到浏览器中）访问页面时 Respond.js 不起作用 -->
    <!--[if lt IE 9]>
      <script src="https://fastly.jsdelivr.net/npm/html5shiv@3.7.3/dist/html5shiv.min.js"></script>
      <script src="https://fastly.jsdelivr.net/npm/respond.js@1.4.2/dest/respond.min.js"></script>
    <![endif]-->
  </head>
  <body>
    <h1>你好，世界！</h1>
  </body>
</html>
```

##### 3.引入相关样式文件

```html
<!-- Bootstrap 核心样式 -->
<link rel="stylesheet" href="bootstrap/css/bootstrap.min.css">
```

##### 4.书写内容

- 直接拿Bootstrap预先定义好的样式来使用
- 修改Bootstrap原来的样式，注意权重问题
- 学好Bootstrap的关键在于知道它定义了哪些样式，以及这些样式能实现什么样的效果

#### 2.3 布局容器

Bootstrap需要为页面内容和栅格系统包裹一个.container容器，Bootstrap预先定义好了这个类，叫.container它提供了两个做此用处的类。

##### 1.container类

- 响应式布局的容器 固定宽度
- 大屏(>= 1200px) 宽度定为1170px
- 中屏(>= 992px) 宽度定为970px
- 小屏(>= 768px) 宽度定为750px
- 最小屏(100%)

##### 2.container-fluid类

- 流失布局容器百分百宽度
- 占据全部视口(viewport)的容器
- 适合于单独做移动端开发

### 3.Bootstrap 栅格系统

#### 3.1 栅格系统简介

栅格系统英文为”grid systems”，也有人翻译为"网格系统"，它是指将页面布局划分为等宽的列，然后通过列数的定义来模块化页面布局。

Bootstrap提供了一套响应式，移动设备优先的流式栅格系统，随着屏幕或视口(viewport)尺寸的增加，系统自动分为最多**12列**。

Bootstrap里面container宽度是固定的，但是不同屏幕下，container的宽度不同，我们再把container划分为12等份

#### 3.2 栅格选项参数

栅格系统用于通过一系列的行(row)与列(column)的组合来创建页面布局，你的内容就可以放入这些创建好的布局中。

|                     | 最小屏幕(手机) < 768px | 小屏设备(平板) >=768px | 中等屏幕(桌面显显示器) >=992px | 宽屏设备(大桌面显示器) >=1200px |
| ------------------- | ---------------------- | ---------------------- | ------------------------------ | :-----------------------------: |
| .container 最大宽度 | 自动(100%)             | 750px                  | 970px                          |             1170px              |
| 类前缀              | .col-xs-               | .col-sm-               | .col-md-                       |            .col-lg-             |
| 列(column)          |                        | 12                     |                                |                                 |

- 行(row)必须放到container布局容器里面
- 我们实现列的平均划分 需要给列添加 类前缀 ，类前缀后面跟列的份数 例：class=”col-lg-2",2就为列的份数
- 按照不同屏幕划分为1~12等份
- 行(row)可以去除父容器左右15px的内边距
- xs-extra-small：超小；sm-small：小；md-medium：中等；lg-large：大；
- 列(column)大于12，多余的”列(column)”所在的元素将被作为一个整体另起一行排列
- 每一列默认有左右15像素的padding
- 可以同时为一列指定多个设备的类名，以便划分不同份数，例如：class=”col-md-4 col-sm-6”

![image-20220330171041506](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220330171041506.png)

这种通栏的盒子 先设置一个盒子宽度为100%，然后里面再包含.container。没必要全局先使用container。

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!--[if lt IE 9]>
        <script src="https://fastly.jsdelivr.net/npm/html5shiv@3.7.3/dist/html5shiv.min.js"></script>
        <script src="https://fastly.jsdelivr.net/npm/respond.js@1.4.2/dest/respond.min.js"></script>
        <![endif]-->
    <link rel="stylesheet" href="./Bootstrap/css/bootstrap.min.css">
    <title>Document</title>
    <style>
        [class^="col"] {
            border: 1px solid #999;
        }

        .container .row:nth-child(1) {
            background-color: pink;
        }
    </style>

<body>
    <!-- 列平均划分行的宽度 -->
    <!-- 可以同时为一列指定多个设备的类名，以便划分不同份数 -->
    <div class="container">
        <div class="row">
            <div class="col-lg-3 col-md-4 col-sm-6 col-xs-12">1</div>
            <div class="col-lg-3 col-md-4 col-sm-6 col-xs-12">2</div>
            <div class="col-lg-3 col-md-4 col-sm-6 col-xs-12">3</div>
            <div class="col-lg-3 col-md-4 col-sm-6 col-xs-12">4</div>
        </div>
        <!-- 如果列的份数相加等于12 那么就会占满整行 也就是container的宽度 -->
        <div class="row">
            <div class="col-lg-6">1</div>
            <div class="col-lg-2">2</div>
            <div class="col-lg-2">3</div>
            <div class="col-lg-2">4</div>
        </div>
        <!-- 如果列的份数相加小于12 那么不会占满整行 会留有空白 -->
        <div class="row">
            <div class="col-lg-6">1</div>
            <div class="col-lg-2">2</div>
            <div class="col-lg-2">3</div>
            <div class="col-lg-1">4</div>
        </div>
        <!-- 如果列的份数相加大于12 那么多余的部分会再另起一行 -->
        <div class="row">
            <div class="col-lg-6">1</div>
            <div class="col-lg-2">2</div>
            <div class="col-lg-2">3</div>
            <div class="col-lg-4">4</div>
        </div>
    </div>
</body>

</html>
```

#### 3.3 列嵌套

栅格系统内置的栅格系统将内容再次嵌套，简单理解就是一个列内再分成若干份小列，我们可以通过添加一个新的  ”.row” 元素和一系列 ".col-sm-"元素到已经存在的 ".col-sm-"元素内。

![image-20220330183612354](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220330183612354.png)

我们列嵌套最好加 行".row",这样可以取消父元素的padding值 而且高度自动和父级一样高。

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!--[if lt IE 9]>
            <script src="https://fastly.jsdelivr.net/npm/html5shiv@3.7.3/dist/html5shiv.min.js"></script>
            <script src="https://fastly.jsdelivr.net/npm/respond.js@1.4.2/dest/respond.min.js"></script>
            <![endif]-->
    <link rel="stylesheet" href="./Bootstrap/css/bootstrap.min.css">
    <title>Document</title>
    <style>
        [class^="col"] {
            height: 30px;
            background-color: pink;
        }
    </style>
</head>

<body>
    <div class="container">
        <div class="row">
            <!-- 列嵌套 -->
            <div class="col-md-4">
                <div class="row">
                    <div class="col-md-6">1</div>
                    <div class="col-md-6">2</div>
                </div>
            </div>
            <div class="col-md-4">2</div>
            <div class="col-md-4">3</div>
        </div>
    </div>
</body>

</html>
```

#### 3.4 列偏移

使用".col-md-offset-"类可以将列向右侧偏移，这些类实际是通过使用*选择器为当前元素增加了左侧的边距(margin)

![image-20220330205643134](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220330205643134.png)

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!--[if lt IE 9]>
    <script src="https://fastly.jsdelivr.net/npm/html5shiv@3.7.3/dist/html5shiv.min.js"></script>
    <script src="https://fastly.jsdelivr.net/npm/respond.js@1.4.2/dest/respond.min.js"></script>
    <![endif]-->
    <link rel="stylesheet" href="./Bootstrap/css/bootstrap.min.css">
    <title>列偏移</title>
    <style>
        .row div {
            height: 30px;
            background-color: pink;
        }
    </style>
</head>

<body>
    <div class="container">
        <div class="row">
            <div class="col-md-4">1</div>
            <!-- 偏移的份数 就是 12 - 两个盒子的份数 = 4 -->
            <div class="col-md-4 col-md-offset-4">2</div>
        </div>
        <div class="row">
            <!-- 如果只有一个盒子 那么就偏移的份数 = (12 - 8) / 2 -->
            <div class="col-md-8 col-md-offset-2">1</div>
        </div>
    </div>
</body>

</html>
```

#### 3.5 列排序

通过使用".col-md-push-"和".col-md-pull-"类就可以很容易的改变列(column)的顺序。

![image-20220330210238758](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220330210238758.png)

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!--[if lt IE 9]>
    <script src="https://fastly.jsdelivr.net/npm/html5shiv@3.7.3/dist/html5shiv.min.js"></script>
    <script src="https://fastly.jsdelivr.net/npm/respond.js@1.4.2/dest/respond.min.js"></script>
    <![endif]-->
    <link rel="stylesheet" href="./Bootstrap/css/bootstrap.min.css">
    <title>Document</title>
    <style>
        .row div {
            height: 30px;
            background-color: pink;
        }
    </style>
</head>

<body>
    <div class="container">
        <div class="row">
            <div class="col-md-4 col-md-push-8">左侧</div>
            <div class="col-md-8 col-md-pull-4">右侧</div>
        </div>
    </div>
</body>

</html>
```

#### 3.6 响应式工具

为了加快对移动设备友好的页面开发工作，利用媒体查询功能，并使用这些工具类可以方便的针对不同设备展示或隐藏页面内容。

| 类名       | 超小屏 | 小屏 | 中屏 | 大屏 |
| ---------- | ------ | ---- | ---- | ---- |
| .hidden-xs | 隐藏   | 可见 | 可见 | 可见 |
| .hidden-sm | 可见   | 隐藏 | 可见 | 可见 |
| .hidden-md | 可见   | 可见 | 隐藏 | 可见 |
| .hidden-lg | 可见   | 可见 | 可见 | 隐藏 |

与之相比，是"visible-"是显示某个页面内容

| 类名        | 超小屏 | 小屏 | 中屏 | 大屏 |
| ----------- | ------ | ---- | ---- | ---- |
| .visible-xs | 可见   | 隐藏 | 隐藏 | 隐藏 |
| .visible-sm | 隐藏   | 可见 | 隐藏 | 隐藏 |
| .visible-md | 隐藏   | 隐藏 | 可见 | 隐藏 |
| .visible-lg | 隐藏   | 隐藏 | 隐藏 | 可见 |

Bootstrap其他(按钮、表单、表格)，请参考Bootstrap文档。

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!--[if lt IE 9]>
    <script src="https://fastly.jsdelivr.net/npm/html5shiv@3.7.3/dist/html5shiv.min.js"></script>
    <script src="https://fastly.jsdelivr.net/npm/respond.js@1.4.2/dest/respond.min.js"></script>
    <![endif]-->
    <link rel="stylesheet" href="./Bootstrap/css/bootstrap.min.css">
    <title>响应式工具</title>
    <style>
        .row div {
            height: 100px;
            background-color: pink;
        }

        .row div:nth-child(1) {
            font-size: 50px;
            color: skyblue;
        }

        .row div:nth-child(3) {
            font-size: 50px;
            color: #fff;
        }
    </style>

</head>

<body>
    <div class="container">
        <div class="row">
            <div class="col-md-4 visible-lg">在大屏下才显示</div>
            <div class="col-md-4">2</div>
            <div class="col-md-4 hidden-xs">在超小屏下消失</div>
        </div>
    </div>
</body>

</html>
```

## 案列：阿里百秀首页案列

**技术选型**

方案：我们采取响应式页面开发方案

技术：bootstrap框架

设计图：本设计图采用1280px设计尺寸

### 需求分析

#### 1.页面布局分析

![image-20220330214334232](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220330214334232.png)

#### 2.屏幕划分分析

1. 屏幕缩放发现 中屏幕 和 大屏幕布局 是一致的。因此我们列 定义为".col-md-"就可以了，md是大于等于970以上的
2. 屏幕缩放发现 小屏幕 布局发生变化，因此我们需要为小屏幕根据需求改变布局
3. 屏幕缩放发现 超小屏幕布局又发生了变化，因此我们需要为超小屏幕根据需求改变布局
4. 策略：我们先布局md以上的pc端布局，最后根据实际需求在修改 小屏幕和超小屏幕的 特殊布局样式

#### 3.页面制作

##### 1.创建文件夹

![image-20220330220333802](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220330220333802.png)

##### 2.container宽度修改

因为本效果图采取1280px，而bootstrap里面 container宽度最大为1170px，因此我们需要手动改下container最大宽度。

# 6.移动端布局总结

## 6.1 移动端主流方案

### 1.单独制作移动端页面(主流)

京东商城手机版

淘宝触屏版

苏宁易购手机版

...

### 2.响应式页面兼容移动端(其次)

三星手机官网

...

## 6.2 移动端技术选型

- 流失布局(百分比布局)
- flex弹性布局(推荐)
- rem适配布局(推荐)
- 响应式布局

建议：我们选取一种主要技术选型，其他技术做为辅助，这种混合技术开发。

# 7.vw和vh

## 7.1 移动端布局

- 移动端布局---flex布局
- 为了实现可以适配移动端，页面元素可以宽度和高度等比例缩放
- 需要移动端适配有如下方案：

![image-20220406170901443](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220406170901443.png)

## 7.2 vw和vh是什么

- vw和vh是一个相对单位(类似于em和rem相对单位)

  vw是：viewport width 视口宽度单位

  vh是：viewport height 视口高度单位

- 相对视口的尺寸计算结果

  1vw = 1/ 100视口宽度

  1vh = 1 / 100视口高度

例如：当前屏幕视口是375像素，则1vw就是3.75像素。如果当前屏幕视口为414像素，则1vw = 4.14像素

**注意：**

和百分比有区别的，百分比是相对于父元素来说的，而vw和vh总是针对于当前视口来说的

## 7.3 vw和vh的使用

### 1.使用

- 超级简单，元素单位直接使用新单位vw和vh即可。
- 因为vw和vh是相对单位，总是相对于视口的，所以不同视口(屏幕)下，宽高一起变化完成适配。

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        div {

            width: 10vw;
            height: 10vh;
            background-color: pink;
        }
    </style>
</head>

<body>
    <div></div>
</body>

</html>
```

### 2.如何还原设计稿

前提：我们设计稿按照iPhone6/7/8来设计，有个盒子是50px*50px的，如何使用vw/vh呢

分析：

1. 设计稿参照iPhone6/7/8，所以视口宽度尺寸是375像素(像素大厨切换到2x模式)

2. 那么1vw是多少像素？

   375px / 100 = 3.75px.即 ：视口宽度 / 100 = 1vw是多少像素

3. 我们元素的目标是多少像素？

   50px * 50px

4. 那么50 * 50是多少个vw？

   50 / 3.75px = 13.3333vw.即：目标元素的宽度 / 1vw是多少像素 = 目标元素宽度的vw了

### 3.vs code px转换vw的插件

![image-20220406195250667](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220406195250667.png)

![image-20220406195258932](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220406195258932.png)

Px2vw 需要改为开发页面视口宽度

## 7.4 小结

1. 开发中使用vw，需要像素大厨有哪些改动？

   把模式改为2x模式

2. 开发中使用vw，如何还原设计稿？

   确定设计稿视口宽度。比如375

   直接使用测量数值 / （视口宽度 / 100）

   比如：50  / （375 / 100)

## 7.5 vw注意事项

- 因为涉及到大量除法，还是适应less搭配更好点。
- 我们本质是根据视口宽度来等比例缩放页面元素高度和宽度的，所以开发中使用vw就基本够用了。vh很少使用。
- 检查兼容性： 网址：https://caniuse.com/

![image-20220406185719482](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220406185719482.png)

# 案列实战-bilibili官网首页

## bilibili官网移动端首页布局

需求：实现在不同宽度设备中等比例缩放的网页效果。

分析：

![image-20220406190708666](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220406190708666.png)

1. 准备好项目目录以及文件

2. 准备好字体文件(下载别人网站字体)

   检查元素--->iconfont样式表--->复制字体URL到浏览器地址栏--->回车

   ![image-20220406193339051](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220406193339051.png)

   ![img](file:///C:\Users\刘星敏\Documents\Tencent Files\1944754630\Image\C2C\58F7FD499EEB202EF8B0A54F5E8D1A08.png)

   ![img](file:///C:\Users\刘星敏\Documents\Tencent Files\1944754630\Image\C2C\58F7FD499EEB202EF8B0A54F5E8D1A08.png)

3. 准备好less文件

   生成的css文件自动放到css文件下面

   ![image-20220406190608793](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220406190608793.png)

4. 准备开始项目内容

4.1.头部模块 suspension-box 悬挂盒子

![image-20220406194603862](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220406194603862.png)

4.2 m-navbar 模块

![image-20220406195429749](C:\Users\刘星敏\AppData\Roaming\Typora\typora-user-images\image-20220406195429749.png)