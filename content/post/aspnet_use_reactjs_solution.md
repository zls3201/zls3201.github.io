+++
title= "AspNet MVC使用Reactjs的解决方案"
date= 2016-09-12T15:42:11+08:00
draft= true
categories = ["dev"]
tags = ["asp.net","reactjs","js"]
toc = true
author = "zls3201"
author_homepage =  "http://www.zls3201.com/"
+++


最新尝试了下使用ReactJs做开发，之前在项目中同时使用过vuejs 和 avalonjs，vue很好使，但IE最低版本只兼容到9，avalon兼容性很好，但相对api定义有些怪异（我之前做的一个功能要求双层for嵌套，结果绑定变量有闭包要求。。。。），后面看了下ReactJs的0.14版本可兼容到IE8，另外ractive.js也可兼容到IE8，但ReactJs新引入了JSX文件语法，vs2015可识别jsx语法，但IE8客户端处理jsx文件有些问题，查询资料发现都是在服务器端将jsx文件编译为js文件，现经实践有两种方案，如下

1.使用reactjs.net
参考地址 https://reactjs.net/

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/es5-shim/4.5.9/es5-shim.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/es5-shim/4.5.9/es5-sham.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/react/0.14.7/react.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/react/0.14.7/react-dom.js"></script>
```

Install-Package React.Web.Mvc4 -Version 1.4.0
代码
```html
@{
    ViewBag.Title = "Index";
    Layout = null;
}
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>@ViewBag.Title - My ASP.NET Application</title>
    <script src="~/Scripts/modernizr-2.6.2.js"></script>

    <script src="~/Scripts/jquery-1.10.2.min.js"></script>
    <script src="~/Scripts/bootstrap.min.js"></script>
</head>
<body>
    <div id="content"></div>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/es5-shim/4.5.9/es5-shim.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/es5-shim/4.5.9/es5-sham.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/react/0.14.7/react.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/react/0.14.7/react-dom.js"></script>
    @*<script src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/6.0.20/browser.js"></script>*@

    <script src="@Url.Content("~/Scripts/HelloWorld.jsx")"></script>
</body>
</html>
```

2.使用vs插件编译时将jsx转换为js文件
webpack类工具使用配置有些繁复
经查询发现 Web Compiler 使用较方便，
参考 https://visualstudiogallery.msdn.microsoft.com/3b329021-cd7a-4a01-86fc-714c2d05bb6c

```html
@{
    ViewBag.Title = "Index";
    Layout = null;
}
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>@ViewBag.Title - My ASP.NET Application</title>
    <script src="~/Scripts/modernizr-2.6.2.js"></script>

    <script src="~/Scripts/jquery-1.10.2.min.js"></script>
    <script src="~/Scripts/bootstrap.min.js"></script>
</head>
<body>
    <div id="content"></div>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/es5-shim/4.5.9/es5-shim.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/es5-shim/4.5.9/es5-sham.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/react/0.14.7/react.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/react/0.14.7/react-dom.js"></script>
    @*<script src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/6.0.20/browser.js"></script>*@

    <script src="@Url.Content("~/Scripts/HelloWorld.js")"></script>
</body>
</html>
```