# ES6

## 参考文档

[深入理解ES6](https://github.com/hyy1115/ES6-learning)

[ECMAScript 6 入门](http://es6.ruanyifeng.com/)

[技术胖带你玩转ES6](http://jspang.com/2017/06/03/es6/)

## ES6的开发环境搭建

### 初始化项目

```
npm init -y (-y代表全部默认同意)
```

```
{
  "name": "es6",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```

### 安装环境依赖

```
npm install -g babel-cli  //全局安装Babel-cli
npm install babel-cli --save-dev
npm install babel-preset-es2015 --save-dev
```

### 新建.babelrc

```
{
    "presets":[
        "es2015"
    ],
    "plugins":[]
}
```

### 简化转化命令

修改成如下代码 使用 `npm run build` 就可以将es6转化成es5

```
{
  "name": "es6",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "build": "babel src/index.js -o dist/index.js"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "babel-cli": "^6.24.1",
    "babel-preset-es2015": "^6.24.1"
  }
}
```

## 变量声明

var let const

## 解构赋值

### 对象的解构赋值

```
let obj = {
    a: 1,
    b: [1, 2]
}
// 对象解构
const {
    a
} = obj
console.log(a) //1
```

## 扩展运算符 rest运算符
