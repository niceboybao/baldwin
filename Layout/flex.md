# Flexbox

## Learn more here

[How to Build a News Website Layout with Flexbox](https://webdesign.tutsplus.com/tutorials/how-to-build-a-news-website-layout-with-flexbox--cms-26611)

[Flex 布局教程：语法篇-阮一峰](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)

## Some useful points for flex

1.flex布局实现 水平垂直居中

```css
.display: flex;
align-items：center;垂直方向上的对齐方式；
justify-content：center;水平方向上的对齐方式；
```

shortcoming:针对换行文本不支持

2.row col 老是分不清

```html
<ons-row>
  <ons-col>1</ons-col>
  <ons-col>2</ons-col>
  <ons-col>3</ons-col>
</ons-row>
1---2---3
```
