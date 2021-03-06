**JS语言精粹之鸡肋篇**
---
　　在《JS语言精粹》的附录B中，总结了JavaScript这个语言的的一些有问题的特性，在利用这门语言进行编程的过程中，应该尽量避免。

 ==
　　应始终使用`===`和`!==`.这是因为这两个运算符在两个运算数类型一致且拥有相同的值时，`===`将会返回true，
`!==`会返回false。而`==`与`!=`只有在两个运算数类型一致时才会做出正确的判断，但是如果两个运算数是不同的类型时，它们试图去强制转换其值得类型，转换的规则比较复杂且难以记忆。例如
```
''=='0'          //false
0==''            //true
0=='0'           //true

false=='false'   //false
false=='0'       //true

false==undefined //false
false==null      //false
null==undefined  //true

'\t\r\n'==0     //true
```
　　而上面的这些例子如果把`==`都换成`===`则都会返回`false`;则可以看出利用`==`进行判断会变得复杂，因此应使用`===`与`!==`进行判断。

* with语句　　
　　在利用with语句快捷访问对象的属性时，它的结果可能有时是不可预料的，所以应该避免使用它，且在with语句在该门语言中存在，本身就严重影响了JavaScript
处理器的速度，因为它阻止了变量名的此法作用域绑定。

* eval　　
　　使用eval形式的代码会更加难以阅读。这种形式须进行运行编译器，而有时也许只是为了执行一个微不足道的赋值语句，因此会使得性能显著降低。另eval函数还会减弱应用的安全性，
因为它给被求值的文本赋予了太多的权力，且与with语句执行的方式一样，会降低语言性能。  
　　Function构造器是eval的另一种形式，所以也应避免使用。对于setTimeout与setInterval函数，当它们在接受字符串参数时，setTimeout和
setInterval会像eval那样去处理。字符串参数也应该避免。

* continue语句　
　　continue语句跳到循环的顶部，作者证实在移除continue语句后，性能会得到改善。

* switch贯穿
　　应尽量避免switch贯穿，凡是有case的地方，一律加上break。这样可以防止在贯穿出错时难以找到错误。

* 缺少块的语句  
　　if、while、do或for语句可以接受一个括在花括号中的代码块，也可以接受单行语句。应避免使用单行语句，这样会模糊程序结构，且不利于阅读。

* ++ --  
　　递增和递减虽然可以使代码看起来更简洁，但是这是一种不谨慎的编程风格，大多数的缓冲区溢出错误所造成的安全漏洞，都是由于像这样的编码而导致的。

* 位运算符  
　　JavaScript与Java具有形同的一套位运算符。但是在Java里，位运算符处理的是整数，而JavaScript中没有整数类型，它只是双精度的浮点数，因此位操作符将它们的数字数字运算数
先转换成整数，接着执行运算，然后再转换回去。在大多数语言中，这些位运算符接近于硬件处理而非常快。但是在JavaScript中，它们非但不是硬件处理，而且非常慢。另外按位与运算符"&"同逻辑与运算符"&&"很容易混淆，因此JavaScript很少执行位操作。

* function 语句对比函数表达式  
　　在JavaScript中既有function语句，同时也有函数表达式，而作者提倡的形式是
```
var foo=function (){};
```
　　上面的形式能明确表示foo是一个包含一个函数值的变量。function语句在解析时会发被提升的情况，虽然这种形式放宽了函数先声明后使用的要求，但是会导致混乱，另外要避免在if
语句中使用function语句，因为大多数浏览器虽然允许if语句中使用function语句，但是在解析时的处理不同，会造成可移植性的问题。
　　一个语句不能以一个函数的表达式开头，因为官方的语法假定以单词function开头的语句是一个function语句。解决方法就是把函数表达式括在一个圆括号中。如
```
(function(){
   var hidden_variable;
})();
```
* 类型的包装对象
　　不要使用new Boolean、new Number或new String,也要避免使用`new Object`和`new Array`。可使用`{}`和`[]`来代替。

* new
　　在JavaScript中，利用new运算符创建一个继承于其运算数的原型的新对象，然后调用该运算数，把新创建的对象绑定给this。如果忘记使用new运算符，
则得到是一个普通的函数调用，并且this被绑定到全局对象，这样会污染全局变量且没有编译警告和运行时警告。
　　因此在与new结合的函数命名时应该首字母大写，而一个更好的策略是不去使用new这个运算符。

* void
　　我们知道在很多语言，类似c语言中，void是一种类型，表示没有值，而在JavaScript中，void表示一个运算符，它接受一个运算符并返回undefined。则这个运算符用处不大，所以应该避免使用它。
　　