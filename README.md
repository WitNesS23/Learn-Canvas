# 学习Canvas之路

####导语：
在写自己的[前端第一个项目](http://www.witness23.info/)的时候，想在第二个页面里面加入类似戳气球，然后内容自由落体的一个特效。在网上查询资料之后，发现需要用到HTML5中新增加的Canvas标签，所以在这记录下这段时间从零学习这个标签的各种基础使用到效果实现的过程。

## 一、 认识Canvas
> Canvas 对象表示一个 HTML 画布元素 - <canvas>。它没有自己的行为，但是定义了一个 API 支持脚本化客户端绘图操作。简单来说，这个 HTML 元素是为了客户端矢量图形而设计的。它自己没有行为，但却把一个绘图 API 展现给客户端 JavaScript 以使脚本能够把想绘制的东西都绘制到一块画布上。

- [W3C对 HTML DOM Canvas 对象的官方解释](http://www.w3school.com.cn/jsref/dom_obj_canvas.asp)
- [W3C对 HTML5 <canvas> 标签的官方解释](http://www.w3school.com.cn/html5/html5_canvas.asp)

定义总是生涩难懂的，下面开始从简单项目着手介绍各个特性。

### 1. 标签与特性

`<canvas id="canvas" width="1000" height="500"></canvas>`