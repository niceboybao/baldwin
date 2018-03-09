# JavaScript

## Learn more here

[JavaScript 对象的属性和方法](http://cache.baiducontent.com/c?m=9f65cb4a8c8507ed4fece763105392230e54f7263d96814f2289cd5f93130a1c1871e3cc767e0d5c92d8242616a83d01baa86123714237b7ec9bc908c9fecf6879877f23716c913061c469afdc3724d650964de8df0e96c9e74396b9d3a3c82457dd25036df1849c2e0103cb1fe76542f4d29f5f635d07cceb27648f4e075a885236a14689f7426b10f180ca2c49d459da&p=9c6dd41b85cc43f108e2977f0d5092&newp=92769a479cdd5fdd03bd9b7d0c168f231610db2151d6d2116b82c825d7331b001c3bbfb423251003d6c37b670ba94356e1f33c7237012ba3dda5c91d9fb4c57479c2392a0247&user=baidu&fm=sc&query=j%CA%B2%C3%B4%CA%C7%B6%D4%CF%F3%CA%F4%D0%D4%BA%CD%B7%BD%B7%A8&qid=87651cb2000133d1&p1=4)

## Some useful points

### 数组去重

```javascript
var arr = [2, 3, 4, 4, 5, 2, 3, 6];
/*
array.filter(function(currentValue,index,arr), thisValue)
currentValue当前元素的值 index当前元素的索引值 arr当前元素属于的数组对象 thisValue可选。对象作为该执行回调时使用，传递给函数，用作 "this" 的值。
如果省略了 thisValue ，"this" 的值为 "undefined"
*/
var arr2 = arr.filter(function(element, index, self) {
    return self.indexOf(element) === index;
});
console.log(arr2);
```

### JavaScript 对象

对象只是带有属性和方法的特殊数据类型。属性是与对象相关的值，方法是能够在对象上执行的动作
