**JS语言精粹之函数**
----------------
　　今天主要看的是《JavaScript语言精粹》的第四章：函数。这一章相对来说是这本书中内容比较多的一章。对于一些知识点再次进行了回顾并有一些细节需要注意。  
　　1、在JavaScript中函数就是对象。对象字面量产生的对象连接到Object.prototype.函数对象连接到Function.prototype(该原型对象本身连接到Object.prototype,之前看过的博客文章[深入理解javascript原型和闭包（4）——隐式原型](http://www.cnblogs.com/wangfupeng1988/p/3979290.html)可以看的更明白些).每个函数在创建时富有两个附加的隐藏属性：函数的上下文和实现函数行为代码。([深入理解javascript原型和闭包（8）——简述【执行上下文】上](http://www.cnblogs.com/wangfupeng1988/p/3986420.html)）  
　　2、在4.9节中提到，JavaScript是有函数作用域的。那意味着定义在函数中的参数和变量在函数外部是不可见的，而且在一个函数中的任何位置定义的任何地方都可见。很多现代语言都推荐尽可能迟地声明变量。而用在JavaScript上的话却是糟糕的建议，因为它缺少块级作用域。所以，最好的做法是在函数体的顶部声明函数中可能用到的所有变量。虽然之前也是这么做的，但是以后还是要注意一下。  
　　3、4.11节关于回调，函数可以让不连续事件的处理变得更容易。书中的例子我觉得很具有典型性，也一并记录下来：假定有一个序列，由用户交互开始，向服务器发送请求，最终显示服务器的响应。若写成
```
request=prepare_the_request();
response=send_request_synchronously(request);
display(response);
```
　利用这种方式的问题在于网络上的同步请求将会导致客户端进入假死状态。如果网络传输或者服务器很慢，响应性的降低将是不可接受的。因此更好的方式是发起异步的请求，提供一个当服务器的响应到达时将被调用的回调函数。异步的函数立即返回，这样客户端不会被阻塞。
```
request=prepare_the_request();
send_request_asynchronously(request,function(response){
display(response);
});
```
　　将一个函数作为参数给send_request_asynchronously函数，它将在接收到响应时被调用。
　　4、4.12节模块部分，书中写到模块模式利用了函数作用域和必报来创建绑定对象与私有成员的关联。模块模式的一般形式是：一个定义了私有变量和函数的函数；利用闭包创建可以访问私有变量和函数的特权函数；最后返回这个特权函数，或者把它们保存到一个可访问到的地方。利用模块模式可以摒弃全局变量的使用。

```
var serial_maker=function(){
		var prefix='';
		var seq=0;
		return{
			set_prefix:function(p){
				prefix=String(p);
			},
			set_seq:function(s){
				seq=s;
			},
			gensym:function(){
				var result=prefix+seq;
				seq+=1;
				return result;
			}
		};
	};
	var seqer=serial_maker();
	seqer.set_prefix('Q');
	seqer.set_seq(1000);
	var unique=seqer.gensym();
	console.log(unique);//Q1000
	var nu=seqer.gensym();
	console.log(nu);//Q1001;
```
　　上面这段代码很好地印证了上面的说法，除非调用对应的方法，否则无法改变prefix或seq的值。seqer利用闭包可以访问这些值，且拥有使用或修改私有状态的能力。之前阅读了很多闭包的文章，在练习中也遇到过这种模块模式编一段小程序，但是这种思想的运用还不是很灵活，因此应该多注意，在产生接口并隐藏状态与实现的时候利用函数和闭包来构造模块。  
　　这本书确实写出了JavaScript精华的部分，这一章内容也很多，很可能有理解不到位的地方，回头还应在使用的过程中再理解消化并回过头来反复阅读。