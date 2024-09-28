# 2D 转换

转换（transform）：实现元素位移、旋转、缩放等效果

1. 移动 translate

```js
transform: translate(x,y);
transform: translateX(n);
transform: translateY(n);
```

优点：不影响其他盒子的布局

2. 旋转 rotate

```js
transform: rotate(度数)	// 单位deg
```

度数为正，顺时针；度数为负，逆时针。

设置旋转中心点：

````js
transform-origin: x y;
````

> [!CAUTION]
>
> x y 通过空格间隔
>
> 可以使用像素、百分比、方向名词

3. 缩放 scale

```js
transform: scale(x, y)
```

> [!CAUTION]
>
> 如果只写一个参数，则宽高缩放倍数一致

# 动画

动画(animation)：复杂的动画效果实现

1. 定义动画 @keyframes

```css
@keyframes 动画名称 {
    0% {
        ...
    }
    100% {
        ...
    }
}
```

动画序列：0%是动画的开始，100%是动画的结束，这种规则就是动画序列

2. 使用动画 animation-name

```css
选择器 {
    animation-name: 动画名称;
}
```

3. 持续时间 animation-duration

```css
选择器 {
    animation-name: 动画名称;
    animation-duration: 2s;
}
```

## 动画的常见属性

1. 运动曲线 

animation-timing-function

2. 动画开始时间

animation-delay

3. 动画播放次数

animation-iteration-count

4. 逆向播放

animation-diraction (mormal/alternate)

5. 动画结束后的状态

animation-fill-mode  (backwards/forwards)

6. 动画是否运行或停止

aniamtion-play-state  (pause/running)

```css
animation: 动画名称 持续时间 运动曲线 开始时间 播放次数 是否反向;
```

### 运动曲线

1. linear	匀速
2. ease          低速开始，低速结束
3. steps()       步长

# 3D 转换

坐标轴方向分布：

<img src="https://img-blog.csdnimg.cn/20210615132412458.png" alt="CSS 坐标系_css yx方向-CSDN博客" style="zoom:80%;" />

1. 3D移动 translate3d

```css
transform: translateX();
transform: translateY();
transform: translateZ();	// 一般用px做单位
transform: translate3d(x, y, z);
```

2. 透视 perspective

让网页产生3d效果

透视属性需要写在被观察盒子的父盒子上（只能是上一级盒子，越级不起作用）

视距越小成像越大，视距越大成像越小。

3. 3d旋转 rotate3d

```css
transform: rotateX();
transform: rotateY();
transform: rotateZ();
transform: rotate3d(x,y,z,deg);
```

旋转方向的判定，左手准则：

当度数为正时：拇指指向当前坐标轴的正方向，四指弯曲的方向便是旋转方向；度数为负时同理。

4. 3d呈现 transform-style

控制子盒子是否开启3d立体空间，该属性写给父级盒子，影响对象是子盒子。

保持后代3d立体效果的存在。

```css
transform-style: preserve-3d;
```

**示例** 实现盒子的两面翻转

HTML布局

```html
<body>
    <div class="box">
        <div class="back">2222222</div>
        <div class="front">1111111</div>
    </div>
</body>
```

CSS样式

```css
<style>
/*外部的大盒子*/
    .box {
        width: 200px;
        height: 200px;
        position: relative;
        margin: 100px auto;
        transition: all .5s;
        /*子代盒子做了3d效果，为了在操作box时让子代保持3d效果，开启3d呈现*/
        transform-style: preserve-3d;
    }
/*内部的两个小盒子*/
    .front,
    .back {
        width: 100%;
        height: 100%;
        position: absolute;
        top: 0;
        left: 0;
        border-radius: 50%;
        text-align: center;
        line-height: 200px;
        color: #fff;
        font-size: 20px;
    }
    .box:hover {
        transform: rotateY(180deg);
    }
    .front {
        background-color: salmon;
        /*此属性一定要添加，否则看不到背后的盒子*/
        backface-visibility: hidden;
    }
    .back {
        background-color: springgreen;
    	/*先将背面的盒子进行翻转，这样整体翻转以后背面才不会形成镜像*/
        transform: rotateY(180deg);
    }
</style>
```

> [!IMPORTANT]
>
> [CSS](https://developer.mozilla.org/zh-CN/docs/Web/CSS) 属性 `backface-visibility` 指定当元素背面朝向观察者时是否可见。
>
> 元素的背面是其正面的镜像。虽然在 2D 中不可见，但是当变换导致元素在 3D 空间中旋转时，背面可以变得可见。（此属性对 2D 变换没有影响，它没有透视。）
>
> `backface-visibility` 属性可以指定为下面列出的值:
>
> - [`visible`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/backface-visibility#visible)
>
>   背面朝向用户时可见。
>
> - [`hidden`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/backface-visibility#hidden)
>
>   背面朝向用户时不可见。

# 浏览器私有前缀

- `-moz-`:Firefox
- `-ms-`:ie
- `-webkit-`:safari、chrome
- `-o-`:Opera

# Flex伸缩布局

## 视口

视口：浏览器显示页面的区域。视口分为布局视口、视觉视口、理想是口

### 布局视口 layout viewport

iOS和Android都将视口分辨率设置为了980px，但是元素过小，只能手动缩放。

### 视觉视口 visual viewport

正在查看的网站区域

### meta视口标签

```html
<meta name="viewport" content="width=device-width,max"
```

## 二倍图

- 物理像素，指的是屏幕中的最小显示颗粒，是物理上真实存在的
- 在PC端页面，1px等于1物理像素，但是移动端不尽相同。移动端上，1px能显示的物理像素的个数，成为物理像素比或屏幕像素比

准备的图片比实际需要的图片大两倍，经过手动缩放至所需要的尺寸，经过设备再次放大以后，恢复原来的尺寸，此时，图片不会失真。

#### 背景缩放

```css
background-size: width height;
/*
	宽高可以是数字、百分比
	cover:把图像扩展至足够大，使其能够使其能够完全覆盖背景区域
	contain:把图像扩展至最大尺寸，使其宽度和高度完全适应内容区域
*/
```

#### 二倍精灵图

- 首先将精灵图等比例缩放为原来的一半
- 测量缩放以后的精灵图上的位置
- 在程序里面，精灵图也要缩放为原来的一半

# 移动端开发

## 方案选择

1. 单独制作移动端页面
2. 响应式页面兼容移动端

## 技术解决方案

样式初始化：https://necolas.github.io/normalize.css/latest/normalize.css

### 特殊样式

```css
/*清楚点击高亮*/
-webkit-tap-heighlight-color: transparent;
/*清除按钮自带的默认样式*/
-webkit-appearance: none;
/*禁用长按页面时的弹出菜单*/
img,a {-webkit-touch-callout: none;}
```

## 常见布局

### 技术选型

- 单独制作移动端页面
  1. 流式布局（百分比布局）
  2. flex弹性布局
  3. less + rem + 媒体查布局
  4. 混合布局
- 响应式页面兼容移动端
  1. 媒体查询
  2. bootstrap

### 流式布局

百分比布局、非固定像素布局

通过把盒子的宽度设置成百分比进行伸缩，不受固定像素限制，内容向两侧填充

需要给定最大宽度 `max-width(max-height)` 与最小宽度 `min-width(min-hright)`

### flex布局

原理：

- 当父盒子设置为 flex 布局以后，子元素的 float clear vertical-align属性将会失效
- 伸缩布局=弹性布局=伸缩盒布局=弹性盒布局=flex布局
- 采用 flex 布局的元素称为 flex容器，简称“容器”，他的所有子元素成为容器的成员，称为 flex项目，简称“项目”。

#### 父级属性

- flex-direction

设置主轴方向，row(默认) row-reverse column column-reverse

- justify-content

设置主轴上子元素的排列方式，flex-start flex-end center space-around(平分剩余空间) space-between(先贴两边，再平分剩余空间)

- flex-warp

子元素是否换行，默认不换行 no-wrap wrap

- align-items

设置侧轴上元素的排列方式 flex-start flex-end center stretch(拉伸)

该属性只能设置单行元素，在多行下没有效果

- align-content

设置侧轴上子元素的排列方式，并且只能用于子项换行的情况（多行），在单行下没有效果

flex-start flex-end center space-around space-between stretch(子元素平分父元素高度)

> [!CAUTION]
>
> flex 默认的是不换行的，需要设置 flex=warp

- flex-flow

该属性是 flex-direction flex-warp 的复合属性

#### 子项属性

- flex

定义子项分配剩余空间，用 flex 表示占有多少份，后跟数字，默认为0

- align-self

控制子项在侧轴的排列方式，可以允许某一个项目的对其方式与其他子项不同

- order

定义项目的排列顺序，数值越小，排列越靠前，默认是 0

### rem适配布局

#### rem基础

==rem==是一种==单位==，==em==单位的大小是==相对于父元素文字的大小==来说的，而==rem==是==相对于html元素的字体大小==

flex布局只能是改变盒子的宽度，使其能自适应变化，但是不能改变高度。

rem适配布局，能根据窗口的大小，自动调节页面上文字和盒子的大小

可以通过修改html里的文字大小进行全局控制

#### 媒体查询

媒体查询（Media Query）

可以针对不同的屏幕尺寸设置不同的样式

```css
@media mediatype and|not|only (media feature) {}
```

mediatype: all(所有设备) print(打印机与打印预览) screen(屏幕)

关键字：

- and：将多个媒体特性连接到一起

- not：排除某个媒体类型

- only：指定某个特定的媒体类型，可以省略

媒体特性：

根据不同类型的媒体特性设置不同的展示风格

- width：输出设备中页面的可见宽度
- min-width：输出设备中页面的最小可见宽度
- max-width：输出设备中页面的最大可见宽度

#### 引入资源

当样式比较多的时候，可以针对不同的媒体引用不同的样式表

```html
<link rel="stylesheet" media="mediatype and|not|only (media feature)" href="" >
```

### less基础

维护CSS的弊端：

- 冗余度高
- 不方便维护和扩展，复用性差
- CSS没有很好的计算能力

Less(Leaner Style Sheets)是一门CSS扩展语言，也是CSS预处理器。他在CSS的基础上，引入了变量、Mixin（混入）、运算以及函数等功能

常见的预处理器：Sass、Less、Styles

#### 安装使用

- 安装 node
- node 环境安装 less: npm install -g less
- 版本检测 lessc -v

#### less 变量

```less
@变量名: 值;
```

命名规则：

1. 必须以 `@` 为前缀
2. 不能包含特殊字符
3. 不能以数字开头
4. 大小写敏感

#### less编译

Less包含一套自定义的语法与解析器，编译器会将用户自定义的规则编译成CSS文件。

通过插件形式 easy less

#### less嵌套

允许在HTML结构上嵌套的元素，在less中依然可以进行与HTML结构类似的嵌套方式

如果遇见（交集选择器、伪类、伪元素选择器）

- 如果内层选择器前没有 `&` ，将被视为后代选择器

#### less运算

可以直接对数值进行四则运算

- 运算符的两侧必须有空格
- 当有多个单位出现在计算式中时，以最左侧的为准

### rem适配方案1

less + rem + 媒体查询

动态配置 html 文字大小，将屏幕等分成若干份，在不同的屏幕尺寸上，除以该份数，就可以得到不同的数值，通过媒体查询，动态的将该结果设置为 html 的字体大小，就能实现页面的动态缩放。

### rem适配方案2

flexible.js + rem



### 响应式布局

原理：使用媒体查询，针对不同宽度的设备进行布局和样式设置，从而达到适配不同设备的目的

#### 响应式布局容器

响应式需要一个父级作为布局容器，来配合自己元素来实现变化效果

通过媒体查询来改变布局容器的大小，再改变里面子元素的排列方式和大小，从而实现不同屏幕下，看到不同的页面布局和样式变化。

#### Bootstrap

框架：有这一套比较完整的网页功能解决方案，而且控制权在框架本身，有预置样式库、组件库和插件。使用者按照某种规定的规范进行开发。

- 标准的HTML + CSS代码规范
- 提供了一套简洁、直观、强悍的组件
- 有自己的生态圈，不断地更新迭代

#### bootstrap中的布局容器

Bootstrap需要将页面内容和栅格系统包裹在一个容器里面，Bootstrap预先定义好了这个类，叫 `.container`



#### bootstrap栅格系统

栅格系统（grid system）:它是指将页面布局划分为等宽的列，然后通过列数的定义来模块化页面布局。

bootst提供了一套响应式的、移动设备优先的流式栅格系统，随着屏幕或视口尺寸的增加，系统会自动分裂成最多12列。

bootstrap里的 container的宽度是固定的，但是不通过的屏幕下，container的宽度不同，再将container划分为12等分。

#### bootstrap栅格系统参数

类前缀：

- 超小屏	`.col-xs-`
- 小屏         `.col-sm-`
- 中屏           `.col-md-`
- 大屏         `.col-lg-`

```html
<div class="col-sm-3"
```

#### bootstrap列嵌套

列在嵌套的时候最好加一个行，这样可以去掉父级元素的padding值，高度与父级一样高

 

#### bootstrap列偏移

使用 `.col-md-offset-*` 类可以将列向右偏移。这些类实际是通过使用 `*` 选择器为当前元素增加了左侧的边距（margin）



#### bootstrap列排序

通过使用 `.col-md-push-*` 和 `.col-md-pull-*` 类就可以很容易地改变列的顺序



#### 响应式工具

为了加快对移动设备友好的开发工作，利用媒体查询功能，并使用这些工具类可以方便的针对不同设备展示或隐藏页面内容。

`.hidden-xs` :超小屏隐藏，其余可见

`.hidden-sm` :小屏隐藏，其余可见

`.hidden-md` :中屏隐藏，其余可见

`.hidden-lg` :大屏可见，其余隐藏

`visible-*`
