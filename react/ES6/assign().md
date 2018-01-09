# assign()

## 基本用法

Object.assign() 方法用于将所有可枚举属性的值从一个或多个源对象复制到目标对象。它将返回目标对象。

[JavaScript中的可枚举属性与不可枚举属性](https://www.cnblogs.com/kongxy/p/4618173.html)

`语法`Object.assign(target, ...sources)

`实例`

```javascript
var obj = { a: 1 };
var copy = Object.assign({}, obj);
console.log(copy); // { a: 1 }
```

对象尽量静态化，一旦定义，就不得随意添加新的属性。如果添加属性不可避免，要使用`Object.assign`方法。

```javascript
// bad
const a = {};
a.x = 3;

// if reshape unavoidable
const a = {};
Object.assign(a, {x: 3});
```

在拷贝的过程中修改对象的某个属性

```javascript
var burryPoint = {
    "userName": "",
    "fullName": "",
    "school": "",
};
return Object.assign({}, burryPoint, {
    userName: res.username,
    fullName: res.givename,
    school: school.join(",") //将数组转成字符串
});
```

`注意` Object.assign() 克隆时，只会做赋值操作，嵌套对象直接传递引用，不是深拷贝。

## 关联

### 深拷贝

[浅拷贝和深拷贝的区别？](https://www.cnblogs.com/always-chang/p/6107437.html)
