# javascript深入理解其执行环境和作用域链
###### 作者：guangwei.bao

## 执行环境

* 执行环境 *（Execution context，EC）或执行上下文，是JS中一个极为重要的概念

### EC的组成

当JavaScript代码执行的时候，会进入不同的执行上下文，这些执行上下文会构成了一个执行上下文栈（Execution context stack，ECS）。

![](http://upload-images.jianshu.io/upload_images/1846966-9ded98302b647e3d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 变量对象（Variable object，VO）: 变量对象即包含变量的对象，除了我们无法访问它外，和普通对象没什么区别。

* [[Scope]]属性:作用域即变量对象，作用域链是一个由变量对象组成的带头结点的单向链表，其主要作用就是用来进行变量查找。而[[Scope]]属性是一个指向这个链表头节点的指针。

* this: 指向一个环境对象，注意是一个对象，而且是一个普通对象，而不是一个执行环境。

### 产生EC的两个阶段

当一段JS代码执行的时候，JS解释器会通过两个阶段去产生一个EC

1.创建阶段（当函数被调用，但是开始执行函数内部代码之前）

	1.创建变量对象VO

	2.设置[[Scope]]属性的值
	
	3.设置this的值
	
2.激活/代码执行阶段

	初始化变量对象，即设置变量的值、函数的引用，然后解释/执行代码。

函数的每次调用都有与之紧密相关的作用域和执行环境。从根本上来说，作用域是基于函数的，而执行环境是基于对象的(例如：全局执行环境即window对象)。 

换句话说，作用域涉及到所被调用函数中的变量访问，并且不同的调用场景是不一样的。**执行环境始终是this关键字的值**，它是拥有当前所执行代码的对象的引用。**每个执行环境都有一个与之关联的变量对象，环境中定义的所有变量和函数都保存在这个对象中**。虽然我们编写的代码无法访问这个对象，但解析器在处理数据时会在后台使用它。

### 执行环境（也称执行上下文–execution context）

当**JavaScript**解释器初始化执行代码时，它首先默认进入全局执行环境，从此刻开始，**函数的每次调用都会创建一个新的执行环境**。 

每个函数都有自己的执行环境。当执行流进入一个函数时，函数的环境就会被推入一个环境栈中（execution stack）。在函数执行完后，栈将其环境弹出，把控制权返回给之前的执行环境。ECMAScript程序中的执行流正是由这个便利的机制控制着。 

执行环境可以分为**创建**和**执行**两个阶段。在创建阶段，解析器首先会创建一个变量对象（variable object，也称为活动对象 activation object），它由定义在执行环境中的变量、函数声明、和参数组成。在这个阶段，作用域链会被初始化，this的值也会被最终确定。在执行阶段，代码被解释执行。 

demo：

```
function a() { 
 var i = 0; 
 function b() { alert(++i); } 
 return b;
}
var c = a();
c();
```

![](http://img.blog.csdn.net/20160818165204236)

### 小结

当javascript代码被浏览器载入后，默认最先进入的是一个全局执行环境。当在全局执行环境中调用执行一个函数时，程序流就进入该被调用函数内，此时JS引擎就会为该函数创建一个新的执行环境，并且将其压入到执行环境堆栈的顶部。浏览器总是执行当前在堆栈顶部的执行环境，一旦执行完毕，该执行环境就会从堆栈顶部被弹出，然后，进入其下的执行环境执行代码。这样，堆栈中的执行环境就会被依次执行并且弹出堆栈，直到回到全局执行环境。 

此外还要注意一下几点：

* 单线程

* 同步执行

* 唯一的全局执行环境

* 局部执行环境的个数没有限制

* 每次某个函数被调用，就会有个新的局部执行环境为其创建，即使是多次

* 调用的自身函数(即一个函数被调用多次，也会创建多个不同的局部执行环境)。


### 在javascript中，可执行的JavaScript代码分三种类型： 

1. Global Code，即全局的、不在任何函数里面的代码，例如：一个js文件、嵌入在HTML页面中的js代码等。
 
2. Eval Code，即使用eval()函数动态执行的JS代码。 

3. Function Code，即用户自定义函数中的函数体JS代码。 

不同类型的JavaScript代码具有不同的执行环境，这里我们不考虑evel code，对应于global code和function code存在2种执行环境：全局执行环境和函数执行环境。

### 全局执行环境

在一个页面中，第一次载入JS代码时创建一个全局执行环境，全局执行环境是最外围的执行环境，在Web浏览器中，全局执行环境被认为是window对象。因此，所有的全局变量和函数都是作为window对象的属性和方法创建的。

某个执行环境中的所有代码执行完毕后，该环境被销毁，保存在其中的所有变量和函数定义也随之销毁，全局执行环境直到应用程序退出后---例如关闭浏览器和网页---时才被销毁。

### 函数执行环境

每个函数都有自己的执行环境，当执行进入一个函数时，函数的执行环境就会被推入一个执行环境栈的顶部并获取执行权。当这个函数执行完毕，它的执行环境又从这个栈的顶部被删除，并把执行权并还给之前执行环境。这就是ECMAScript程序中的执行流。

![](http://pic002.cnblogs.com/images/2012/327530/2012063015553443.jpg)

### 【定义期】

函数定义的时候，都会创建一个** scope **属性，这个对象对应的是一个对象的列表，列表中的对象仅能javascript内部访问，没法通过语法访问。

我们定义一全局函数A，那么A函数就创建了一个A的[[scope]]属性。此时，[[scope]]里面只包含了全局对象【Global Object】。而如果， 我们在A的内部定义一个B函数，那B函数同样会创建一个[[scope]]属性，B的[[scope]]属性包含了两个对象，一个是A的活动对象【Activation Object】【对于函数来说】一个是全局对象，A的活动对象上面，全局对象在下面。以此类摧，每个函数的都在定义的时候创建自己的[[scope]]，里面保存着一个类似于栈的格式的数据。

下面是示例代码：

```
// 外部函数
function A(){
     var somevar;
        
     // 内部函数
    function B(){
         var somevar;
     }
}
```

看下示意图：
![](http://pic002.cnblogs.com/images/2012/327530/2012063017020623.jpg)

### 【执行期】

当函数被执行的时候，就是进入这个函数的执行环境，首先会创一个它自己的活动对象【Activation Object】（这个对象中包含了this、参数(arguments)、局部变量(包括命名的参数)的定义，当然全局对象是没有arguments的）和一个变量对象的作用域链[[scope chain]]，然后，把这个执行环境的[scope]按顺序复制到[[scope chain]]里，最后把这个活动对象推入到[[scope chain]]的顶部。这样[[scope chain]]就是一个有序的栈，这样保了对执行环境有权访问的所有变量和对象的有序访问。

```
// 第一步页面载入创全局执行环境global executing context和全局活动象
// 定义全局[[scope]],只含有Window对象
// 扫描全局的定义变量及函数对象:color【undefined】、changecolor【FD创建changecolor的[[scope]]，此时里面只含有全局活动对象】,加入到window中，所以全局变量和全局函数对象都是做为window的属性定义的。
// FD已经定义好所以在此执行环境内任何位置都可以执行changecolor(),color也已经被定义，但是它的值是undefined

// 第二步color赋值"blue"
var color = "blue";

// 它是不需要赋值的，它就是引用本身
function changecolor() {
    // 第四步进入changecolor的执行环境
    // 复制changecolor的[[scope]]到scope chain
    // 创建活动对象，扫描定义变量和定义函数，anothercolor【undefined】和swapcolors【FD创建swapcolors的[[scope]]加入changecolor的活动对象和全局活动对象】加入到活动对象,活动对象中同时还要加入arguments和this
    // 活动对象推入scope chain 顶端
    // FD已经定义好所以在此执行环境内任何位置都可以执行swapcolors(),anothercolor也已经被定义好，但它的值是undefined
    
    // 第五anothercolor赋值"red"
    var anothercolor = "red";
    
    // 它是不需要赋值的，它就是引用本身
    function swapcolors() {
        // 第七步进入swapcolors的执行环境，创建它的活动对象
        // 复制swapcolors的[[scope]]到scope chain
        // 扫描定义变量和定义函数对象，活动对象中加入变量tempcolor【undefined】以及arguments和this
        // 活动对象推入scope chain 顶端
        
        // 第八步tempcolor赋值anothercolor,anothercolor和color会沿着scope chain被查到，并继续往下执行
        var tempcolor = anothercolor;
            anothercolor = color;
            color = tempcolor;    
    }

    // 第六步执行swapcolors,进入其执行环境
    swapcolors();
}

// 第三步执行changecolor,进入其执行环境
changecolor();

```

**访问标识符**：当执行js代码的过程中，遇到一个标识符，就会根据标识符的名称，在执行上下文(Execution Context)的作用域链中进行搜索。从作用域链的第一个对象（该函数的Activation Object对象）开始，如果没有找到，就搜索作用域链中的下一个对象，如此往复，直到找到了标识符的定义。如果在搜索完作用域中的最后一个对象，也就是全局对象(Global Object)以后也没有找到，则会抛出一个错误，提示undefined。 

既然讲到执行期，顺便讲一下javascript的**【声明提升机制Hoisting】**

先看下面代码：

```
var myvar = 'my value';  
alert(myvar); // my value  
```

当然会弹出my value

再看下面这样

```
var myvar = 'my value';  
(function(){
    alert(myvar); // undefined
    var myvar = 'you value';  
})()
```

结果却是undefined

这是因为，javascript解析器，进入一个函数执行环境，先对var 和 function进行扫描。相当于会把var或者function【函数声明】声明提升到执行环境顶部。

上面的代码会被解析成下面这样：

```
var myvar = 'my value';  
(function(){
    var myvar;
    alert(myvar); // undefined
    myvar = 'you value';  
})()
```

根据，标识符找查机制当执行到alert的时候，查找myvar是局部变量的myvar，此时myvar并没有被赋值。所以结果是undefined。

再看看下面的例子：

```
count(1,2); // 3
function count(a,b)
{
    alert(a+b);    
}
```

```
count(1,2); // 会报错误count is not a function
var count = function (a,b)
{
    alert(a+b);    
}
```

我们知道，根据声明提升机制，var和function都会被提升到执行环境的顶部，已经扫描完毕。所以，上面那种写法，会把function声明提到执行环境顶部，所以即使调用在声明的前面依然能够执行。

而下面这种写法会被解析成这样：

```
var count;
count(1,2); // 会报错误count is not a function
count = function (a,b)
{
    alert(a+b);    
}
```

因为此时count只是被扫描，但还末被引用到函数对象，所以此时，它不是一个function，所以把它当函数来执行会报错。

另外一个需要提一下的是，函数的声明是优先于变量的声明的。


## 作用域

当代码在一个环境中执行时，**会创建变量对象的一个作用域链**（scope chain）。作用域链的用途是**保证对执行环境有权访问的所有变量和函数的有序访问**。

**作用域链包含了执行环境栈中的每个执行环境对应的变量对象**。通过作用域链，可以决定变量的访问和标识符的解析。 

注意：全局执行环境的变量对象始终都是作用域链的最后一个对象。

在访问变量时，就必须存在一个可见性的问题(**内层环境可以访问外层中的变量和函数，而外层环境不能访问内层的变量和函数**)。更深入的说，当访问一个变量或调用一个函数时，JavaScript引擎将不同执行环境中的变量对象按照规则**构建一个链表**，在访问一个变量时，先在链表的第一个变量对象上查找，如果没有找到则继续在第二个变量对象上查找，直到搜索到全局执行环境的变量对象即**window对象**。这也就形成了Scope Chain的概念。 

![](http://img.blog.csdn.net/20160818165843993)

作用域链图，清楚的表达了执行环境与作用域的关系(一一对应的关系)，作用域与作用域之间的关系(链表结构，由上至下的关系)。

demo:

```
var color = "blue";
function changeColor(){
  var anotherColor = "red";
  function swapColors(){
    var tempColor = anotherColor;
    anotherColor = color;
    color = tempColor;
    // 这里可以访问color, anotherColor, 和 tempColor
  }
  // 这里可以访问color 和 anotherColor，但是不能访问 tempColor
  swapColors();
}
changeColor();
// 这里只能访问color
console.log("Color is now " + color);
```

上述代码一共包括三个执行环境：全局执行环境、changeColor()的局部执行环境、swapColors()的局部执行环境。

* 全局环境有一个变量color和一个函数changecolor();

* changecolor()函数的局部环境中具有一个anothercolor属性和一个swapcolors函数，当然，changecolor函数中可以访问自身以及它外围（即全局环境）中的变量;

* swapcolor()函数的局部环境中具有一个变量tempcolor。在该函数内部可以访问上面的两个环境（changecolor和window）中的所有变量，因为那两个环境都是它的父执行环境。 

上述代码的作用域链如下图所示： 

![](http://img.blog.csdn.net/20160818183034965)

从上图发现。内部环境可以通过作用域链访问所有的外部环境，但是外部环境不能访问内部环境中的任何变量和函数。 

**标识符解析**（变量名或函数名搜索）是沿着作用域链一级一级地搜索标识符的过程。搜索过程始终从作用域链的前端开始，然后逐级地向后（全局执行环境）回溯，直到找到标识符为止。

### 执行环境与作用域的区别与联系

执行环境为全局执行环境和局部执行环境，局部执行环境是函数执行过程中创建的。 

**作用域链是基于执行环境的变量对象的**，由所有执行环境的变量对象(对于函数而言是活动对象，因为在函数执行环境中，变量对象是不能直接访问的，此时由活动对象(activation object,缩写为AO)扮演VO(变量对象)的角色。)共同组成。 

当代码在一个环境中执行时，会创建变量对象的一个作用域链。作用域链的用途：是保证对执行环境有权访问的所有变量和函数的有序访问。作用域链的前端，始终都是当前执行的代码所在环境的变量对象。

### 小练习

```
<script type="text/javascript">
(function(){
    a= 5;
    console.log(window.a);//undefined
    var a = 1;//这里会发生变量声明提升
    console.log(a);//1
})();
</script>
```

window.a之所以是undefined，是因为var a = 1;发生了变量声明提升。相当于如下代码：
```
<script type="text/javascript">
(function(){
    var a;//a是局部变量
    a = 5;//这里局部环境中有a，就不会找全局中的
    console.log(window.a);//undefined
    a = 1;//这里会发生变量声明提升
    console.log(a);//1
})();
</script>
```

###### 1.如果你对javascript作用域链还不是很理解，那么请看原文出处：(原文:http://www.cnblogs.com/wilber2013/p/4909459.html)
###### 2.如果你对javascript执行环境还不是很理解，那么请看原文出处：(原文:http://www.cnblogs.com/pigtail/archive/2012/07/19/2570988.html)
 
