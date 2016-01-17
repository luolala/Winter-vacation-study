**JavaScript 语言精粹之数组**
------
　　《JavaScript语言精粹》的第六章介绍了JavaScript中的数组，JavaScript中提供的是一种拥有一些类似数组
特性的对象。在数据结构中，数组是一段线性分配的内存，它通过整数去计算偏移并访问其中的元素，是一种很快访
问的数据结构。但是在JavaScrit中的数组并不是这样的一种数据结构，正如在第三章所提到的，在JavaScript中，
一切皆对象，因此数组也是对象，它把数组的下标转变成字符串，用其作为属性，除了有一个可以用整数作为属性名
的特性外，其属性的检索和更新的方式与对象一模一样。    
　　在这一章中，介绍了数组的一些基本知识，对于判断数组的方式，其中给了一段比较长的代码，之前确实没有注意过这种方式

```
var is_array=function(value){
    return value&&
    typeof value==='object'&&
    typeof value.length==='number'&&
    typeof value.slice==='function'&&
    !(value.propertyIsEnumerable('length'))
}
```
　　首先判断的是这个值是否为真，即null和其他为假的值，我们知道，在JavaScript中共有六种值列出后为假，分别为
false，null，undefined，空字符串'',数字0和数字NaN。其次判断是否为对象，由于数组也是引用类型，因此对象、数组和null
都将得到true。再次，判断此value是否具有length属性，显然对象不具有而数组具有。第四，判断这个值是否包含splice方法。最后，判断length属性是否是
可枚举。这段代码是对数组的一段很可靠的测试。但是感觉有些复杂呀。。
```
　　　  console.log(is_array([1,2,3,4,5]));//true
	console.log(is_array({}));//false
	console.log(is_array(undefined));//undefined
	console.log(is_array(NaN));//NaN
	console.log(is_array(0));//0
	console.log(is_array(false));//false
	console.log(is_array(''));//
	console.log(is_array(null));//null
	console.log(is_array('abc'));//false
	console.log(is_array(true));//false
```
　　回顾其他判断是否为数组的方法，对于instnceof操作符，它假定只有一个全局执行环境，如果网页中包含多个框架，则实际上就存在两个以上不同的
全局环境，从而存在两个以上不同版本的Array构造函数。如果从一个框架向另一个框架传入数组，那么传入的数组与第二个框架中原生创建的数组分别具有各自不同的构造函数。因此这一方法不提倡。    
　　对于ECMAScript5中的`isArray()`，在IE9以上的版本适用，因此在兼容性方面不是很好。目前用的比较多的方法是
```
var isArray = function(obj) { 
return Object.prototype.toString.call(obj) === '[object Array]'; 
}
```
　　另外对于arguments这类的类数组元素，可以利用'Array.prototype.slice.call(arguments)'进行转换。之后可以利用数组方法对其进行操作。