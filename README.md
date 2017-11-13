# 概述
app-router.js是构建SPA（单页面应用程序）的重要js框架，它主要负责单页面应用程序的页面加载和页面路由功能。app-router把各个页面区分开单独开发，类似Android原生应用的开发方式，提高了界面的开发效率。

# 适用场景
开发H5实现的移动端APP，和普通的APP几乎拥有相同的体验。

# 引入
只需要引入以下文件

```
<script type="text/javascript" src="lib/app-router.min.js"></script>
```
就可以使用app-router的所有功能了

# 特性 
### 独立的页面
 每个页面都由一个js文件，一个html文件，一个css文件组成，在组建用户页面时，只需要关注当前页面的代码。你可以看到类似下面这样的目录结构
- home
  - page-home.html
  - page-home.js
  - page-home.css
 
注：移动端通过rem适配会多一个page-home.scss文件，具体参照wiki文档
### 简洁的代码

只需要调用startPage函数，并传入页面的名称，就能看到打开的页面了。
```
router.startPage("home");
```

### 页面加载方式
单页面应用有个显著特点，那就是只有一个主html文件，app-router通过ajax的方式加载其他页面，添加到当前页面的Body中，新加入的页面都是处于隐藏状态，需要用户主动触发显示。

app-router提供两种页面加载的方式
1. **预加载**：所有页面在app打开之前一次性加载完成，这种加载方式需要在进入app之前多花费一定时间。
2. **懒加载**：只当用户需要打开页面时才加载。这种加载方式app刚启动时无需等待，但是在每个页面第一次打开时，需要耗费一定的时间去加载页面。


用户可以根据自己的需求选择合适的加载方式。
# 路由功能
app-router自动记录用户打开页面顺序，可通过以下方式
```
router.back();
```
返回上一个页面。

也可以通过添加router-to属性跳转页面，router-back属性返回上一个页面，类似于下面的代码


```
<header class="bar bar-nav">
	<a router-back>返回</a>
	<h1 class="title">个人信息</h1>
	<a router-to="setting">设置</a>
</header>
```
