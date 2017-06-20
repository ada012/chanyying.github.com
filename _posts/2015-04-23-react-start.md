---
layout: post
title: ReactJS入门知识
description: ""
date: 2015-04-23
tags: [React]
comments: true
share: true
---

### 首先需要先引入两个文件
{% highlight html %}
<script src="react.js"></script>
<script src="JSXTransformer.js"></script>
<div id="example"></div>
{% endhighlight %}

{% highlight js %}
<script type="text/jsx">
    React.render(
    <h1>Hello,world!</h1>,
    document.getElementById('example'));
</script>
{% endhighlight %}

> 上边的JSXTransformer.js文件之所以引入，是为了转换type="text/jsx"文件为javascript代码的。
如果你已经jsx了上边所需要的功能代码，就可以不引入JSXTransformer.js文件。

### <script type="text/jsx">写到另外的js文件中并jsx --watch之后，引入的时候不能这样引入：

{% highlight js %}

  <script type="text/jsx" src="*.js"></script>

{% endhighlight %}

因为此js文件已经是javascript代码了，就不需要type="text/jsx"语句去格式化了。

### 也并不能 类似的用法：

{% highlight js %}
<script src="build/JSXTransformer.js"></script>
<script type="text/jsx" src="src/helloworld.js"></script>
{% endhighlight %}

JSXTransformer.js解析的必须是页面内的 type="text/jsx"代码

### 组件传递：

{% highlight js %}
var Box=React.createClass({
    render:function(){
      return (
         <div className="Box">
         <h1>评论：</h1>
            <BoxList />
         </div>
      );
    }
});

var BoxList=React.createClass({
    render:function(){
      return (
        <div className="BoxList">
          <Comment author="Pete Hunt">This is one comment</Comment>
          <Comment author="Jordan Walke">This is *another* comment</Comment>
        </div>
      );
    }
});

var Comment=React.createClass({
    render:function(){
      return(
        <div className="comment">
          <h2 className="commentAuthor">
            {this.props.author}
          </h2>
          {this.props.children}
        </div>
      )
    }
})
{% endhighlight %}

### 名词解释：
* 访问组件的属性：
        * this.props//是自下而上的，由里到外的
* 以上边的例子：
        * {this.props.author}
* 将在本层显示出上一层的author属性
* 任何内嵌的元素作为
        * this.props.children

### 注意：

> var定义的组件名称首字母，必须大写，例如：Box
除了要渲染为DOM的var变量用</>之外，输出内容用{}
var 定义变量必须在作用域以内

{% highlight js %}

render:function(){
    var a=...
}

{% endhighlight %}

