# 前端体系知识梳理

> 前言：暂无

---
## HTML
## CSS
#### CSS模块化
#### 盒模型
#### 选择器

---
## JavaScript
#### 热更新
#### 前端路由
> 前端路由主要有两种实现方式，第一种是通过```history```对象进行控制，与它新增的两个api```history.pushState```和```history.replaceState```有着重要的关联；第二种则是通过hash实现。
>
> * __history__
>
>   这篇文章[history对象--JavaScript标准参考教程](http://javascript.ruanyifeng.com/bom/history.html#)可以使我们很好地再次回顾```history```对象。我们可以通过```history.pushState```与```history.replaceState```去控制标签页的地址改变而不引起页面刷新，再配合```popstate```事件与```event.state```的合理使用，即可实现前端路由
>
>   ```javascript
>   <!DOCTYPE html>
>   <html>
>   <head>
>   	<title>Line Game -5</title>
>   </head>
>   <body>
>   <p>You are at coordinate <span id="coord">5</span>on the line</p>
>   <p>
>   	<a href="?x=6" onclick="go(1); return false;">Advance to 6</a> or 
>   	<a href="?x=4" onclick="go(-1); return false;">retreat to 4</a>?
>   </p>
>   <script type="text/javascript">
>   	var currentPage = 5;
>   	function go(d) {
>   		setupPage(currentPage + d);
>   		history.pushState(currentPage, document.title, '?x=' + currentPage);
>   	}
>   	window.onpopstate = function(event) {
>   		setupPage(event.state);
>   		console.log(event.state);
>   	}
>   	function setupPage(page) {
>   		currentPage = page;
>   		document.title = 'Line Game -' + currentPage;
>   		document.getElementById('coord').textContent = currentPage;
>   		document.links[0].href = '?x=' + (currentPage + 1);
>   		document.links[0].textContent = 'Advance to ' + (currentPage+1);
>   		document.links[1].href = '?x=' + (
>   			currentPage - 1);
>   		document.links[1].textContent = 'retreat to ' + (currentPage-1);
>   	}
>   </script>
>   </body>
>   </html>
>   ```
>
>   ​
>
> * __hash__ 
>
>   当我们通过```window.location```去处理hash的变化时并不会引发页面的重新渲染，而是当作新页面加到历史记录中。每当hash变化时会触发```hashchange```事件，只要我们在```hashchange```事件的回调函数里进行相关处理（如通过ajax请求，改变页面内容），即可实现前端路由控制
>
> 关于更多更详细的细节，可以查看这篇文章——[前端路由的两种实现原理](https://segmentfault.com/a/1190000007238999) 
#### 前端模块化

> 前端模块化，提得最多的莫非CommmonJS，AMD，CMD，UMD这些了，这篇文章对它们做了较为详细的介绍：[AMD, CMD, CommonJS和UMD](https://segmentfault.com/a/1190000004873947)，但个人感觉这篇博文还待完善（如AMD与CMD的区别这部分讲得过于粗略）

---
## 流行框架
#### React
###### 虚拟DOM
#### Vue
###### 虚拟DOM
#### 其他

---
## 浏览器机制
#### 渲染过程
#### 重绘与回流

> 关于重绘与回流，可以查看这篇文章：[页面重绘和回流以及优化](http://www.css88.com/archives/4996)  

---
## 计算机网络
#### 计算机分层
