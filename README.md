# 学习Canvas之路

####导语：
在写自己的[前端第一个项目](http://www.witness23.info/)的时候，想在第二个页面里面加入类似戳气球，然后内容自由落体的一个特效。在网上查询资料之后，发现需要用到HTML5中新增加的Canvas标签，所以在这记录下这段时间从零学习这个标签的各种基础使用到效果实现的过程。

## 一、 认识Canvas
> Canvas 对象表示一个 HTML 画布元素 - <canvas>。它没有自己的行为，但是定义了一个 API 支持脚本化客户端绘图操作。简单来说，这个 HTML 元素是为了客户端矢量图形而设计的。它自己没有行为，但却把一个绘图 API 展现给客户端 JavaScript 以使脚本能够把想绘制的东西都绘制到一块画布上。

- [W3C对 HTML DOM Canvas 对象的官方解释](http://www.w3school.com.cn/jsref/dom_obj_canvas.asp)
- [W3C对 HTML5 <canvas> 标签的官方解释](http://www.w3school.com.cn/html5/html5_canvas.asp)

定义总是生涩难懂的，下面开始从简单项目着手介绍各个特性。

### 1. 标签与特性

```html
<canvas id="canvas" width="1000" height="500">
	当前浏览器不支持Canvas（优雅降级）
</canvas>
```

这样就是很常见的使用canvas标签的例子，其中比较重要的知识点如下:

1. 在不指定宽和高的情况下，canvas元素标签的默认大小是 300px * 150px；
2. id 属性是总是需要指定的，因为主要对canvas进行操作的是JavaScript；
3. **官方推荐，指定canvas标签大小使用上面代码中的直接指定属性的方式，而不是使用CSS样式来指定**，同样指定的值不需要加单位。原理上简单解释下就是因为，通过指定属性值的方式不仅指定了canvas画布的大小，同样指定了内里图画分辨率的大小，有助于内里画面显示的精度；

### 2. 交给JavaScript

前面导语就有提到，其实真正呈现页面、带来惊艳效果的背后功臣是JavaScript。下面简单说说使用JavaScript初始化绘制对象的操作。

```javascript
var canvas = document.getElementById('canvas');
var context = canvas.getContext('2d');

canvas.width = 1024;
canvas.height = 768;
```

1. 第一行代码很简单，就是取得canvas的DOM对象；
2. 第二行代码，官方术语的解释就是 **得到绘图的上下文环境**，这是真实的绘制所需要的接口，有了这个对象，就可以进行真实的绘制；
3. 后面的代码可以动态设置canvas的大小精度；

#### A. 直线、多边形和七巧板

重要的概念说在前面，**canvas中的绘图是一种基于状态的绘图**，先简单解释下，整个绘制过程是，先设置绘图的状态，之后再调用绘图的函数来做一个具体的绘制。
现在说起来，这个概念解释的很无趣，同学们有个印象就行，下面会不断强化理解这个概念。

```javascript
context.moveTo(100, 100);
context.lineTo(600, 600);

// 上面两行就是状态的设置
// 下面一行才是具体的绘制

context.stroke();
```

这段代码的执行过程很简单：

1. .moveTo() 设置直线起始位置，.lineTo() 设置直线终止位置（绘制的意图，并没有真正的绘制）；
2. .stroke() 具体的绘制；
3. 总结来说，就是先设置绘图的状态，在调用函数来绘制图形；