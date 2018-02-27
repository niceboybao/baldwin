# Webpack

## Learn more here

[掘金-webpack经典入门](https://juejin.im/post/59f93357f265da43305dc90a)

[webpack官网](https://webpack.js.org/concepts/)

[webpack官网(中文)](https://doc.webpack-china.org/concepts/loaders/#-loader)

## Some useful points

### --save-dev 与--save的区别

**--save-dev :** 项目开发过程中需要依赖的包，发布之后无需依赖的包，例如我们的babel，开发过程需要babel为我们把书写的es6转为es5，发布之后由于我们所有书写的es6代码都被转为es5，因此无需继续依赖；

**--save :** 项目发布后依然需要依赖的包，例如我们jquery；
