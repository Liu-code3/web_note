# 1 Vue 介绍

- lVue.js（读音 /vjuː/, 类似于 view） 是一套构建用户界面的渐进式(**你可以在原有大系统的上面，把一两个组件改用它实现。不会过多的去做职责外的事情**)框架。
- Vue 只关注视图层， 采用自底向上增量开发的设计。
- Vue()是一个构造函数，用new Vue(构造参数)得到的就是一个实例对象，Vue实例对象是Vue.js中最基本的单元。构造参数是一个对象，构造参数的属性即为参数选项，常见的参数选项有el、data、template、components等。
   在项目中， 在main.js中通过创建最外层(边界)的Vue实例对象来实现根结点、根组件的功能。
- Vue 的目标是通过尽可能简单的 API 实现响应的数据绑定和组合的视图组件(数据双向绑定)。

 

**入门案例**

```html
<div id="app">

  <p>{{ message }}</p>

</div>

 

<script>

new Vue({

 el: '#app',

 data: {

  message: 'Hello world!'

 }

})

</script>
```



## 1.1环境准备

1 我们可以在 Vue.js 的官网上直接下载 vue.min.js 并用 <script> 标签引入。

下载地址：[https://vue.js.org/js/vue.min.js](https://vuejs.org/js/vue.min.js)

 

2、使用 CDN 方法

以下推荐国外比较稳定的两个 CDN，国内还没发现哪一家比较好，目前还是建议下载到本地。

 

Staticfile CDN（国内） : https://cdn.staticfile.org/vue/2.2.2/vue.min.js

 

unpkg：https://unpkg.com/vue/dist/vue.js, 会保持和 npm 发布的最新的版本一致。

 

cdnjs : https://cdnjs.cloudflare.com/ajax/libs/vue/2.1.8/vue.min.js

 

3、NPM 安装，一般用于前后端分离开发模式

# 2 Vue 模板语法

Vue.js 使用了基于 HTML 的模板语法，允许开发者声明式地将 DOM 绑定至底层 Vue 实例的数据。

## 2.1绑定文本

数据绑定最常见的形式就是使用 {{...}}（双大括号）的文本插值：

```html
<div id="app">

  <p>{{ message }}</p>

</div>

 

<script>

new Vue({

 el: '#app',

 data: {

  message: 'Hello world!'

 }

})

</script>

 
```



## 2.2绑定HTML

使用 v-html 指令用于输出 html 代码：

```html


<div id="app">

    <div v-html="message"></div>

</div> 

<script>

new Vue({

 el: '#app',

 data: {

  message: '<h1>Hello world</h1>'

 }

})

</script>
```



## 2.3绑定HTML属性

参数在指令后以冒号指明。例如， v-bind 指令被用来响应地更新 HTML 属性

```html
<div id="app">
    <pre><a v-bind:href="url">百度</a></pre>
</div>
	
<script>
new Vue({
  el: '#app',
  data: {
    url: 'http://www.baidu.com'
  }
})
</script>

```



## 2.4绑定表单元素

v-model 指令用来在 input、select、textarea、checkbox、radio 等表单控件元素上创建双向数据绑定，根据表单上的值，自动更新绑定的元素的值

 

```html
<div id="app">
    <p>{{ message }}</p>
    <input v-model="message">
</div>
    
<script>
new Vue({
  el: '#app',
  data: {
    message: hello!'
  }
})
</script>


```



## 2.5缩写

**1 v-bind** **缩写**

Vue.js 为两个最为常用的指令提供了特别的缩写：

 

```html
<!-- 完整语法 -->

<a v-bind:href="url"></a>

<!-- 缩写 -->

<a :href="url"></a>
```

**2  v-on** **缩写**

 

```html
<!-- 完整语法 -->

<a v-on:click="doSomething"></a>

<!-- 缩写 -->

<a @click="doSomething"></a>
```



## 2.6 v-show指令

v-show指令用来控制html元素是否显示

 

```html
<div id="app">

  <h1 v-show="ok">Hello!</h1>

  

  <button @click="ss">控制HTML元素显示</button>

</div>

  

<script>

new Vue({

 el: '#app',

 data: {

  ok: true

 },

 methods:{

  ss:function(){

​    this.ok =!this.ok

  }

 }

})

</script> 
```



# 3 Vue条件语句

```html
<div id="app">
    <div v-if="type == 'A'">
      A
	</div>
	<div v-else-if="type == 'B'">
	  B
	</div>
	<div v-else-if="type == 'C'">
	  C
	</div>
	<div v-else>
	  Not A/B/C
	</div>
</div>
	
<script>
new Vue({
  el: '#app',
  data: {
    type: 'A'
  }
})
</script>

```



# 4 Vue循环语句

循环使用 v-for 指令。

 

v-for 指令需要以 x in sites 形式的特殊语法， sites 是源数据数组并且 x 是数组元素迭代的别名。

 

v-for 可以绑定数据到数组来渲染一个列表：

```html
<div id="app">
	<table>
		<thead>
				<th>id</th>
				<th>name</th>
		</thead>
		<tbody>
			  <tr v-for="x in sites">
			  	<td>  {{ x.id }}</td>
			  	<td>  {{ x.name }}</td>
			  </tr>
		</tbody>
	</table>
</div> 
<script>
new Vue({
  el: '#app',
  data: {
    sites: [
      { id:1,name: 'cat' },
      { id:2, name: 'pig' },
      { id:3, name: 'dog' }
    ]
  }
})
</script>

```

 

注意：如果要获取数据索引值，v-for可以这样写：v-for="(x,index) in sites"

Index就是数据索引值(0开头)

# 5 Vue事件处理

## 5.1 v-on 用法

v-on或者缩写@ 可以接收一个定义的方法来调用。



```html
 <div id="app">
	<button @click="login">登录</button>

</div>

 

<script>

new Vue({

 el: '#app',

 methods: {

   login:function(){

	    alert("登录")

   }

   

 }

})

</script>
```

 

## 5.2 方法传参

2 方法参数传递，和javascript一样可以直接传参

```html
<div id="app">

  <button @click="login(1)">登录</button>

</div>

<script>

new Vue({

 el: '#app',

 methods: {

   login:function(data){

​     alert("登录"+data)

   }

   

 }

})

</script>
```

 

 

## 5.3 文档事件

3 如果要函数需要在文档加载完后执行，需要定义mouted属性 代码如下：

```html
<script>

new Vue({

 el: '#app',

 methods: {

   login:function(data){

	    alert("登录"+data)

   }

 },

 mounted:function(){

  this.login(1)

 }

})

</script>
```



## 5.4 键盘事件

如果我们要用回车实现登录，Vue 允许为 v-on 在监听键盘事件时添加按键修饰符：

```html


<div id="app">

<button @keyup.13="login" >登录</button>

</div>

<script>

new Vue({

 el: '#app',

 methods: {

   login:function(){

     alert("登录")

   }

   

 }

})

</script>
```

Keyup是键盘事件 ，13 是键码值

注意：次案例演示回车登录，需要用tab键把光标切换到按钮上，再按回车

 

 

**Keycode**对照表如下：

![https://img-blog.csdnimg.cn/20190121145008991.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3lvdXJuZXZlcm1vcmU=,size_16,color_FFFFFF,t_70](file:///C:/Users/刘星敏/AppData/Local/Temp/msohtmlclip1/01/clip_image002.gif)

# 6 Vue表单处理

## 6.1输入框

input 和 textarea 元素中使用 v-model 实现双向数据绑定，前面绑定表单元素已经有案例，

这里就不贴案例了

 

## 6.2复选框

复选框也是使用 v-model 实现双向数据绑定，需要注意的是定义的值是一个js数组,

代码如下：

```html
  <p>多个复选框：</p>

 <input type="checkbox" value="电影" v-model="checkedNames">

 <label>电影</label>

 <input type="checkbox" value="游戏" v-model="checkedNames">

 <label>游戏</label>

 <input type="checkbox" value="看书" v-model="checkedNames">

 <label>看书</label>

 <br>

 <span>选择的值为: {{ checkedNames }}</span>

</div>

 

<script>

new Vue({

 el: '#app',

 data: {

  checkedNames: []//定义一个数组

 }

})
```

 

## 6.3单选框

 

```html


<div id="app">

 <input type="radio" value="男" v-model="sex">

 <label >男</label>

 <br>

 <input type="radio" value="女" v-model="sex">

 <label >女</label>

 <br>

 <span>选中值为: {{ sex }}</span>

</div>

 

<script>

new Vue({

 	el: '#app',

 	data: {

  		sex : '男'

 }

})

</script>

</body>
```

 

## 6.4下拉框

以下实例中演示了下拉列表的双向数据绑定：

 

```html


<div id="app">

 <select v-model="selected" >

  <option value="">选择一个网站</option>

  <option value="www.baidu.com">百度</option>

  <option value="www.google.com">谷歌</option>

 </select>

 

  <div id="output">

   选择的网站是: {{selected}}

 </div>

</div>

 

<script>

new Vue({

 el: '#app',

 data: {

  selected: '' 

 }

})

</script>
```

