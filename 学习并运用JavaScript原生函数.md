**学习并运用JavaScript的原生函数**
---
　　今天在w3cplus上看到了一篇译文，即是"学习并运用JavaScript",翻译自[Learning JavaScript Native Functions and How to Use Them](https://scotch.io/tutorials/learning-javascript-native-functions-and-how-to-use-them),文章主要介绍了
`Call/Apply`、`Bind`、`Map`、`filter`等几种行为。
####this和arguments对象
　　函数执行的作用域是它们被定义的作用域而不是执行的作用域。`this`对象引用当前函数的上下文并且可以以多种方式被调用。
严格模式下，如果变量未定义就会抛出异常、错误。例如
```javascript
this.globalVar = 'globalVar';

function nonStrictFunctionTest () {
    return function () {
        console.log(this.globalVar); // globalVar
    }
}

function strictFunctionTest () {
    'use strict'; // Strict Mode
    return function () {
        console.log(this.globalVar); // TypeError: Cannot read property 'globalVar' of undefined
    }
}

nonStrictFunctionTest()();
strictFunctionTest()();
```

在一个函数中声明变量参数会替换/覆盖原先的参数对象，如
```javascript
function fn (){
    console.log(typeof arguments); // [object Object]
    console.log(arguments[0]); // DeathStar
    console.log(arguments[1]); // Tatooine
    arguments.push("Naboo"); // TypeError: undefined is not a function
    var arguments = "Star Wars";
    console.log(arguments[5]); // W
}

fn("DeathStar", "Tatooine");
```
　　`arguments`是伪数组，因此不能直接运用数组方法，将其转化为真正的数组，可以利用下面的方法
```javascript
var args = Array.prototype.slice.call(arguments);
```
###Call/Apply
　　这两种方法的用法相似，通过传递参数，被调用的函数可以访问或修改对象。如
```javascript
this.lightSaberColor = 'none';

var darthVader = {
    team: 'Empire',
    lightSaberColor: 'Red'
};

var printLightSaberColor = function(){
    console.log(this.lightSaberColor);

}

printLightSaberColor() // none
printLightSaberColor.call(darthVader); // Red
printLightSaberColor.apply(darthVader); // Red

```
　　`call`和`apply`主要的区别在于他们的声明方式不同，`call`需要参数分开传递，而`apply`需要传入由参数组成的数组。
###Bind
　　`bind`方法在IE 8及其以下不支持，是在EcmaScript中扩展的，其可以改变上下文的`this`,与`call`的用法相似，可接受的参数都分为两部分，且第一个参数都是作为执行时函数上下文中的`this`
对象。不同的是：(1)bind 的返回值是函数
```javascript
function func(name,id) {
    console.log(name,id,this);
}
var obj = "Look here";
//什么也不加
func("    ","-->");
//使用bind是 返回改变上下文this后的函数
var a = func.bind(obj, "bind", "-->");
a();
//使用call是 改变上下文this并执行函数
var b = func.call(obj, "call", "-->");
```
结果为：
```javascript
--> Window
bind --> String 
call --> String 
```
另一方面在参数的使用上也有区别,在下面的例子中：
```javascript
function f(a,b,c){
    console.log(a,b,c);
}
var f_Extend = f.bind(null,"extend_A");
f("A","B","C")  //这里会输出--> A B C

f_Extend("A","B","C")  //这里会输出--> extend_A A B

f_Extend("B","C")  //这里会输出--> extend_A B C

f.call(null,"extend_A") //这里会输出--> extend_A undefined undefined
```
　　结果为：
```javascript
A B C
52 extend_A A B
52 extend_A B C
52 extend_A undefined undefined
```
　　由上面的例子我们可以看出，`call`是把第二个及以后的参数作为f方法的实参传进去。而`bind`虽说也是获取第二个及以后的参数用于之后方法的执行，但是
`f_Extend`中传入的实参则是在bind中传入参数的基础上往后排的。
　　对于`bind`的兼容处理可以是：
```javascript
if (!Function.prototype.bind) {
    Function.prototype.bind = function(obj) {
        var _self = this
            ,args = arguments;
        return function() {
            _self.apply(obj, Array.prototype.slice.call(args, 1));
        }
    }
}
```
###Map
　　`map`函数对数组中的每一项运行给定函数，返回每次函数调用结果组成的数组。下面是一个简单的例子。
```javascript
function Jedi(name) {
    this.name = name;
}

var kit = new Jedi('Kit');
var count = new Jedi('Count');
var mace = new Jedi('Mace');

var jedis = [kit, count, mace];

var lastNames = ['Fisto', 'Dooku', 'Windu'];

var jedisWithFullNames = jedis.map(function(currentValue, index, array) {
    var clonedJedi = (JSON.parse(JSON.stringify(currentValue))) // Clone currentValue
    clonedJedi.name = currentValue.name + " " + lastNames[index];
    return clonedJedi;
});

jedisWithFullNames.map(function(currentValue) {
    console.log(currentValue.name);
});


/**
Output:
Kit Fisto
Count Dooku
Mace Windu
*/
```
其实现方法是：
```javascript
Array.prototype.map=function(fun,thisArg){
   if(typeof fun!==='function'){
       throw new Error("The first argument must be of type function");
   }
   var arr=[];
   thisArg=(thisArg)?thisArg:this;
   thisArg.forEach(function(element)){
     arr[arr.length]=fun.call(thisArg,element);
   });
}
```
　　在上面的代码中，'forEach'也是在ECMAScript5中定义的方法，其对数组的每一项运行给定函数，这个方法没有返回值。
###Filter
　　`filter`对数组中的每一项运行给定函数，返回该函数会返回'true'的项组成的数组。其中一种声明方法是：
```javascript
arr.filter(callback[, thisArg])
```
　　`thisArg`是可选的参数，回调函数接受三个参数，`currentValue`,`index`,`array`,其应用例如：
```javascript
function Person(name, side) {
    this.name = name;
    this.side = side;
}

var hanSolo = new Person('Han Solo','Rebels');
var bobaFett = new Person('Boba Fett','Empire');
var princessLeia = new Person('Princess Leia', 'Rebels');

var people = [hanSolo, bobaFett, princessLeia];

var enemies = people.filter(function (currentValue, index, array) {
    return currentValue.side === 'Empire';
})
.map(function(currentValue) {
    console.log(currentValue.name + " fights for the " + currentValue.side + ".");
});

/**
Output:
Boba Fett fights for the Empire.
*/
```
　　这种方法的实现方法是：
```javascript
Array.prototype.filter=function(fun,thisArg){
  if(typeof fun!==`function`){
    throw new Error("The first argument must be of type function");
  }
   var arr=[];
   thisArg=(thisArg)?thisArg:this;
   
   this.forEach(function(element){
     if(fun.call(thisArg,elment)){
       arr[arr.length]=element;
     }
   });
   return arr;
};
```
　　以上是JavaScript中的几个原生方法，在不兼容IE 8及以下的浏览器时，可知`map``filter`可以减少代码量，避免传统的循环方式。

对于`call``apply`以及`bind`还要多多理解，把握其用法。