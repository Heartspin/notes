# 概述

`Vue`：渐进式JavaScript框架

渐进式：声明式渲染 -> 组件系统 -> 客户端路由 -> 集中式状态管理 -> 项目构建

官网：`[Vue.js - 渐进式 JavaScript 框架 | Vue.js (vuejs.org)](https://cn.vuejs.org/)`

通过 `CDN` 使用 `Vue`

```html
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
```

- 易用：熟悉`HTML` `JavaScript` `CSS` 后，可快速上手`Vue`
- 灵活：在一个库和一套完整的框架之间自由的伸缩
- 高效：超快的虚拟`DOM`

# 基本使用

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <!-- 1.引入外部库文件 -->
    <script src="vue.js"></script>
</head>

<body>
    <!-- 2.提供标签容器 -->
    <div id="con">
        <!-- 将数据引入到标签内使用 {{}} 符号，{{}}称为插值表达式 -->
        {{ msg }}
    </div>
</body>
<!-- 3.书写js代码 -->
<script>
    // 4.创建 Vue 实例对象
    // 5.提供一个对象参数
    var vm = new Vue({
        // el 属性：用于指定当前 Vue 实例为哪个容器服务，值通常为该容器的 id
        el: '#con',
        // data 属性：用于存储数据，数据供 el 所指定的容器去使用，值通常为一个对象
        data: {
            msg: 'Hello Vue!'
        }
    });
</script>

</html>
```

- el: 元素的挂载位置（值可以是CSS选择器或DOM元素）
- data：模型数据（值为一个对象）
- {{}}：插值表达式
  - 将数据填充到HTML标签中
  - 支持基本的计算操作

## Vue模板语法

**原生JS：**

采用拼接字符串的形式，将内容渲染到页面上

缺点：不同的开发人员代码风格差异较大，随着业务的复杂度提高，后期的维护变得逐渐困难。

**模板引擎：**

优点：都遵循同样的规范书写代码，代码的可读性明显提高，方便后期的维护。

缺点：没有专门提供事件机制

**模板语法：**

- 插值表达式
- 指令
- 事件绑定
- 属性绑定
- 样式绑定
- 分支循环结构

### 指令

指令的本质就是自定义属性

格式：以`v-`开头

#### v-ckoak指令

插值表达式的“闪动”问题：

插值表达式在将数据放入标签的时候，会先将产值表达式渲染上去，然后快速的替换为插值表达式的内容。如果快速的刷新页面，可能会将原本的插值表达式显示出来，这便是"闪动"

当使用直接在 DOM 中书写的模板时，可能会出现一种叫做“未编译模板闪现”的情况：用户可能先看到的是还没编译完成的双大括号标签，直到挂载的组件将它们替换为实际渲染的内容。

`v-cloak` 会保留在所绑定的元素上，直到相关组件实例被挂载后才移除。配合像 `[v-cloak] { display: none }` 这样的 `CSS` 规则，它可以在组件编译完毕前隐藏原始模板。

```css
[v-cloak] {
  display: none;
}
```

```html
<div v-cloak>
  {{ message }}
</div>
```

直到编译完成前，`<div>` 将不可见。

#### 数据绑定指令

`v-text`

```html
<!-- 纯文本填充 -->
<span v-text="msg"></span>
<!-- 等价于 -->
<span>{{ msg }}</span>
```

`v-html`

能够将HTML标签直接插入到页面上

```html
<span id="com" v-html="msg"></span>

<script>
	var vm = new Vue({
		el: '#com',
		data: {
			msg: '<h1>HTML</h1>'
		}
	});
</script>
```

> [!CAUTION]
>
> 该指令存在安全性问题，本网站内部的数据可以使用，来自第三方的数据不可以使用

`v-pre`

填充原始信息，跳过编译过程

```html
<span v-pre>{{msg}}</span>
```

正常情况下，{{msg}}会被编译显示绑定的数据内容，`v-pre`可以跳过编译，直接显示成`{{msg}}`

#### 数据响应式

数据的变化直接影响到页面上内容的变化，页面上的内容随数据的改变而变化

数据绑定：将数据填充到标签中。通过插值表达式的形式进行的数据绑定，默认的是响应式的。

`v-once` 只编译一次

显示内容之后，不再具有响应式的功能

```html
<span v-once>{{ msg }}</span>
```

应用场景：如果显示的信息后续不需要进行修改，可以使用`v-once`，这样可以提高性能。

#### 双向数据绑定

输入域中数据的变化，会直接改变页面上的内容

`v-model`

```html
<span>{{ msg }}</span>

<input type='text' v-model="msg" />
```

数据的变化影响页面内容的变化。同时，页面内容的变化直接作用在数据上，影响数据的变化

**MVVM设计思想：**

- M（model）
- V（view）
- VM（view-model）

视图（view）同通过事件监听传递给数据，数据（model）通过数据绑定将结果返回到视图。`VM`是二者联系的桥梁

#### 事件绑定

`v-on:事件名`

```html
<span v-on:click=''></span>
```

简写形式，使用`@`取代`v-on:`

```html
<span @click=''></span>
```

随着业务量的变大，直接在标签里书写处理函数是不明智的，Vue提供了一个`methods`属性，该属性的值为一个对象，内部可以定义多种方法

```js
var vm = new Vue({
    el: '',
    data: {},
    methods: {
        add: function() {
            // 这里的 this 指的是 Vue 的实例对象
        	this.num++;
        }
    }
})
```

**调用方式**

```html
<!-- 直接绑定函数名 -->
<span @click='add'></span>

<!-- 调用函数 -->
<span @click='add()'></span>
```

#### 事件函数参数传递

- 普通参数和事件对象

```html
<button @click: 'say('hi'，$event)'></button>
```

> [!CAUTION]
>
> $event 表示事件对象，为固定写法，不是用户自定义。最后一个参数表示事件对象
>
> 对于直接绑定函数名的传参，默认携带事件函数对象为函数的第一个参数

```html
<body>
    <div id="app">
        <div id="num" v-cloak>{{num}}</div>
        <button id="btn" @click='add(1, $event)'>点击1</button>
        <button id="btn1" @click='say'>点击2</button>
    </div>
</body>

<script>
    // 通过事件委托触发事件
    var vm = new Vue({
        el: '#app',
        data: {
            num: 0
        },
        methods: {
            say: function (event) {
                alert('hello');
                console.log(event.target);
            },
            add: function (p1, event) {
                this.num++;
                console.log(p1)
                console.log(event.target);
            }
        }
    })
</script>
```

#### 事件修饰符

- `.stop`阻止冒泡

```html
<a v-on:click.stop="handle">跳转</a>
```

- `.prevent`阻止默认行为

```html
<a v-on:click.prevent="handle">跳转</a>
```

#### 按键修饰符

`.enter`回车键

```html
<input v-on:keyup.enter="submit" />
```

- `.delete`删除键

```html
<input v-on:keydown.delete="handle" />
```

**自定义按键修饰符：**

全局 `config.keyCodes` 对象

```js
Vue.config.keyCodes = number
```

```html
<a v-on:click.f1>删除</a>

<script>
    // 自定义功能键
    Vue.config.keyCodes.f1 = 112
	var vm = new Vue({
        el: '',
        data: {},
        methods: {
            handle: function(event) {
                console.log(event.keyCode)
            }
        }
    })
</script>
```

规则：自定义按键修饰符的名字是自定义的，但是对应的值必须是对应按键的ASCII码值

#### 属性绑定

- `v-bind`

```html
<a v-bind:href="url"></a>
```

- 缩写形式

```html
<a :href="url"></a>
```

#### 样式绑定

- 对象语法

```html
<style>
    .active {}
</style>

<!-- 键值对形式表示 -->
<div v-bind:class="{ active: isActive}">
    
</div>

<!-- isActive 表示标志位，true或false -->
<!-- active 表示类名 -->
<script>
	var vm = new Vue({
        el: '',
        data: {
            isActive: true
        },
        methods: {},
    })
</script>
```

- 数组语法

```html
<style>
    .active {}
    .error {}
</style>

<!-- activeClass 表示占位符 -->
<div v-bind:class="[activeClass, errorClass]"></div>

<script>
    var vm = new Vue({
        el: '',
        data: {
            // 占位符: '类名'，通过该种方式，在数组形势下关联类名
            activeClass: 'active',
            errorClass: 'error'
        },
        methods: {}
    })
</script>
```

**有关样式绑定的几个问题：**

1. 对象绑定和数组绑定可以结合使用

```html
<!-- 数组结合对象添加类 -->
<div :class='[activeClass, errorClass, {active:isActive}]'>
</div>

<script>
	var vm = new Vue({
        el: '',
        data: {
            activeClass: 'active',
            errorClass: 'error',
            isActive: true
        }
    })
</script>
```

2. class绑定的值可以简化操作

```html
<!-- 通过数组的形式添加类 -->
<div :class='arrClasses'>
    
</div>

<script>
	var vm = new Vue({
        el: '',
        data: {
            // 数组
            arrClasses: ['active', 'error'],
            // 对象
            objClasses: {
                active: true,
                error: true
            }
        }
    })
</script>
<!-- 如果想对类进行操作，需要对数组进行操作 -->
```

3. 如果标签原来有 class 在绑定类时的处理
   1. 如果标签本来就有 class 再绑定的 class 不会覆盖原来的 class

#### 样式绑定之style绑定用法

