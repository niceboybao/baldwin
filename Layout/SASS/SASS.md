# sass深入理解

## Learn more here

[sass 入门](https://www.w3cplus.com/sassguide/)

[阮一峰 SASS用法指南](http://www.ruanyifeng.com/blog/2012/06/sass.html)

[sass的@规则（进阶篇）](http://blog.csdn.net/macanfa/article/details/51744324)

[sass github](https://github.com/sass/sass)

[sass github 参考文档](https://github.com/sass/sass/blob/stable/doc-src/SASS_REFERENCE.md)

## Some useful points

### 导入

sass的导入( @import)规则和CSS的有所不同，编译时会将 @import的scss文件合并进来只生成一个CSS文件。但是如果你在sass文件中导入css文件如 @import 'reset.css'，那效果跟普通CSS导入样式文件一样，导入的css文件不会合并到编译后的文件中，而是以 @import方式存在。

所有的sass导入文件都可以忽略后缀名 .scss。一般来说基础的文件命名方法以_开头，如 _mixin.scss。这种文件在导入的时候可以不写下划线，可写成 @import "mixin"。

```scss
//a.scss
//-------------------------------
body {
  background: #eee;
}
```

```scss
//b.scss
//-------------------------------
@import "reset.css";
@import "a";//(or @import "a.scss)
p{
  background: #0982c1;
}
```

**编译过后**

```css
@import "reset.css";
body {
  background: #eee;
}
p{
  background: #0982c1;
}
```

**个人理解：**@import的方式导入.scss脚本，当代码很多的情况也容易查看，代码架构一目了然

### 占位选择器 `%`

这种选择器的优势在于：如果不调用则不会有任何多余的css文件，避免了以前在一些基础的文件中预定义了很多基础的样式，然后实际应用中不管是否使用了 @extend去继承相应的样式，都会解析出来所有的样式。占位选择器以 %标识定义，通过 @extend调用。

```scss
//sass style
//-------------------------------
%ir{
  color: transparent;
  text-shadow: none;
  background-color: transparent;
  border: 0;
}
%clearfix{
  @if $lte7 {
    *zoom: 1;
  }
  &:before,
  &:after {
    content: "";
    display: table;
    font: 0/0 a;
  }
  &:after {
    clear: both;
  }
}
#header{
  h1{
    @extend %ir;
    width:300px;
  }
}
.ir{
  @extend %ir;
}

//css style
//-------------------------------
#header h1,
.ir{
  color: transparent;
  text-shadow: none;
  background-color: transparent;
  border: 0;
}
#header h1{
  width:300px;
}
```

其中 %clearfix这个没有调用，所以解析出来的css样式也就没有clearfix部分。占位选择器的出现，使css文件更加简练可控，没有多余。所以可以用其定义一些基础的样式文件，然后根据需要调用产生相应的css。

**PS:** 在 @media中暂时不能 @extend @media外的代码片段（@media隔离作用域的问题？？？）

在 @media 里面定义变量 相当于 在 {} 的作用域里面定义了局部变量 并不会起到重新设置 前面的变量 的效果
