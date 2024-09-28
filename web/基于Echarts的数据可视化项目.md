# 数据可视化

## 概念

目的：借助图形化的手段，清晰有效的表达和沟通信息

通常用于数据报表、移动端图表、大屏可视化、图编辑等

常见的数据可视化库：

- `D3.js` web端评价最高的JavaScript可视化工具库（入手难）
- `Echarts.js` 百度出品的JavaScript可视化库
- `Highcharts.js` 国外数据可视化库，非商用免费
- `AntV` 蚂蚁金服可视化方案

# Echarts基本使用

1. 下载并引入 `Echarts.js` 文件

```js
<script src="./js/echarts.mini.js"></script>
```

2. 准备一个具备大小的DOM容器

```html
<style>
    .ech {
        width: 500px;
        height: 400px;
        background-color: #eee;
    }
</style>
<body>
    <div class="ech"></div>
</body>
```

3. 初始化`echarts`实例对象

```js
// 基于准备好的dom，初始化echarts实例
var myChart = echarts.init(document.querySelector('.ech'));
```

4. 指定配置项和数据

```js
// 指定图表的配置项和数据
var option = {
    title: {
        text: 'ECharts 入门示例'
    },
    tooltip: {},
    legend: {
        data: ['销量']
    },
    xAxis: {
        data: ['衬衫', '羊毛衫', '雪纺衫', '裤子', '高跟鞋', '袜子']
    },
    yAxis: {},
    series: [
        {
            name: '销量',
            type: 'bar',
            data: [5, 20, 36, 10, 10, 20]
        }
    ]
};

```

5. 把配置项设置给`echarts`实例对象

```js	
// 使用刚指定的配置项和数据显示图表。
myChart.setOption(option);
```

<img src="E:\Picture\下载.png" alt="下载" style="zoom:80%;" />







## 边框图片

使用场景：

盒子的大小不一样，但是使用的边框一样，或者盒子的边框样式无法通过`css`样式生成，此时就需要使用图片边框来完成

border-image：该属性允许用户指定一张图片作为元素的边框

边框图片切图原理：

把四个角切出去（九宫格），中间的部分可以铺排、拉伸或环绕

边框图片语法：

```css
/*边框图片的路径*/
border-image-source

/*图片边框向内偏移*/
/*裁剪尺寸 <不需要单位，上右下左>*/
border-image-slice

/*图片边框的宽度，需要单位*/
/*默认是边框的宽度，改变不会挤压内容*/
border-image-width

/*图片边框是否平铺（repeat）、铺满（round）、拉伸（stretch）[默认]*/
border-image-repeat
```



## 立即执行函数的用法

JavaScript文件中，会用到大量的变量名，为了防止变量名冲突（变量污染），可以采用立即执行函数的策略





## Echatrs适应浏览器缩放

```js
window.addEventListener('resize', function() {
    // 让图标调用resize方法
    myCharts.resize();
})
```





tab栏切换效果：

- 准备后台返回的真实数据



## ES6模板字符

```js
`${表达式}`
// 模板字符采用反钩号``允许自由换行
```

