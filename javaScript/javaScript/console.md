# console

## Learn more here

[console.log格式输出全解及console的其他方法](http://blog.csdn.net/u010081689/article/details/51025836)

[DISABLE JAVASCRIPT CONSOLE ON PRODUCTION](https://stapp.space/disable-javascript-console-on-production/)

## Some useful points

### disable javascript console on production

`function1`

```javascript
window.console.log = function(){}
console.log =()=>false
```

`function2`

```javascript
window.isDebugger = true; //false为生产模式，true为调试模式
    console.log = (function(oriLogFunc){
        return function(str)
        {
            if (window.isDebugger) {
                debugger;
                oriLogFunc.call(console,str);
            }
        }
    })(console.log);
```
