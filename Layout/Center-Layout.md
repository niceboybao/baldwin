# 水平垂直居中

## Learn more here

[掘金-CSS的垂直居中和水平居中总结](https://juejin.im/post/582c04032f301e00594327d4)

[16种方法实现水平居中垂直居中](https://juejin.im/post/58f818bbb123db006233ab2a)

## 水平居中

### 1.行内元素（inline element）, 给其父元素设置 text-align:center （适用行内元素）

[什么是行内元素，块级元素](https://www.cnblogs.com/greenal/archive/2013/01/05/2845513.html)

```html
inline element
也叫内联元素、内嵌元素等；行内元素一般都是基于语义级(semantic)的基本元素，只能容纳文本或其他内联元素，常见内联元素 “a”。比如 SPAN 元素，IFRAME元素和元素样式的display : inline的都是行内元素。
```

### 2.块级元素（block element ）, 该元素设置 margin:0 auto即可.（只有块级元素才生效）

[margin 0 auto与text-align:center的区别](http://www.studyofnet.com/news/41.html)

```html
text-align:center设置为文本或img标签等一些内联对象（或与之类似的元素）的居中。margin:0 auto是设置块元素（或与之类似的元素）的居中。
```

#### 图片的水平居中

我们设置图片标签img {margin:0 auto;} ，我们就犯了一个小错误，img类于内联对象，不可以设置图片img标签的margin属性，如果你一定想要设置，那么首先要将它的属性转变为块元素，如下面的代码：

```css
img {
    display:block;
    margin:0 auto;
}
```

### 3.在一个盒子里面，让一个有固定宽高的盒子实现水平居中：

```css
display: block;  /* 转化成为块级元素 */
magin: auto;
```

### 4.绝对定位元素的居中实现

```css
.element {
    width: 600px; height: 400px;
    position: absolute; left: 50%; top: 50%;
    margin-top: -200px;    /* 高度的一半 */
    margin-left: -300px;    /* 宽度的一半 */
}
```

上面的写法需要严格知道盒子的宽高(局限性)，所以有了下面的写法(手机web开发可忽略,E10+以及其他现代浏览器才支持)

```css
.element {
    width: 600px; height: 400px;
    position: absolute; left: 50%; top: 50%;
    transform: translate(-50%, -50%);    /* 50%为自身尺寸的一半 */
}
```

总结下 ，margin:auto实现绝对定位元素的居中（水平垂直居中）

```css
.element {
    width: 600px; height: 400px;
    position: absolute;
    left: 0; top: 0; right: 0; bottom: 0;
    margin: auto;    /* 有了这个就自动居中了 */
}
```

## 垂直居中

### 1.若元素是单行文本, 则可设置 line-height 等于父元素高度

```css
.element {
    line-height: 10px;
    height:10px;
}
```

### 2.若元素是`行内块级`元素（行内元素的一种）

```css
.element {
    height:10px;
    line-height:10px;
    display: inline-block;
    vertical-align: middle;
}
```

### 3.块级元素（元素高度固定）

```css
.element {
    width: 600px; height: 400px;
    position: absolute;
    left: 0; top: 0; right: 0; bottom: 0;
    margin: auto;    /* 有了这个就自动居中了 */
}
```

### 4.很普通的一种垂直居中

```css
.parent::after, .son{
    display:inline-block;
    vertical-align:middle;
   }
   .parent::after{
    content:'';
    height:100%;
   }
```

## flex弹性布局实现水平垂直居中

用flex布局的水平垂直居中特别方便

[Flex 布局教程：语法篇](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)

```css
.element {
  .display: flex;
  align-items：center;   /* 垂直方向上的对齐方式； */
  justify-content：center;  /* 水平方向上的对齐方式 */
}
```

但是用了flex布局后 有一些css属性会失效？
