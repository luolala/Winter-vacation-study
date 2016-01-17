**JS语言精粹之继承**
------
　　《JavaScript语言精粹》第五章是讲继承的，在第一节和第三节提到了伪类和原型,伪类实现继承的方式为  
```
var Mammal=function(name){
 this.name=name;
};

Mammal.prototype.get_name=function(){
  return this.name;
};
Mammal.prototype.says=function(){
return this.saying||'';
};
var Cat=function(name){
 this.name=name;
 this.saying='meow';
};
Cat.prototype=new Mammal();
```
　　利用类似“类”的构造器函数，没有私有环境，所有的属性都是公开的，且无法访问super(父类)。另外，使用构造器函数的
另一个严重危害是，如果在调用构造器函数时忘记了在前面加上new前缀，那么this将不会被绑定到一个新对象上，而是会被绑定到全局对象上，
所以不但没有扩充新对象，反而将破坏全局变量。  
　　在第三节提到了原型继承，其主要是以一个旧对象为基础，一个新对象继承一个旧对象的属性。利用在第三章提出的Object.beget()方法构造出更多的实例来  
```
  if(typeof Object.beget!=='function'){
      Object.beget=function(o){
      var F=function(){};
      F.prototype=o;
      return new F();
  }
  }
```
　　这个beget方法创建一个使用原对象作为其原型的新对象。在ECMAScript5中的Object.create()应该与这个方法作用相同。在高程第六章中，原型继承直接用的是Object.create();
```
var myMamml={
name:'Herb the Mammal',
get_name:function(){
 return this.name;
},
says:function(){
return this.saying||'';
 }
};
var myCat=Object.beget(myMammal);
```
　　对于以上继承方式没有办法保护隐私，因此在第四节利用模块模式给出了另一种继承方式。  
　　函数化构造器的伪代码模板
```
var constructor=function(spec,my){
    var that,其他的私有实例变量；
    my=my||{};
    
    把共享的变量和函数添加到my中
    
    that=一个新对象
    
    添加给that的特权方法
    
    return that；
}
```
　　　spec 对象包含构造器需要构造一个新势力的所有信息，其内容可能会被复制到私有变量中，
或者被其他函数改变。或者方法可以在需要的时候访问spec的信息。构造一个新对象并赋值给that,有很多方式可以构造一个新对象。
可以使用对象字面量，可以使用new 运算符调用一个伪类构造器。可以爱原型对象上使用Object.beget方法，或者
可以调用另一个函数化的构造器，传给其一个spec对象和my对象。my对象允许其他的构造器分享放到my中的资料。其他构造器可能会
将自己的可分享的成员放进my对象中，以便构造器可以利用它。  
　　接下来，扩充that,加入组成该对象接口的特权方法。可以分配一个新函数成为that的成员方法或者更加安全地将函数定义为私有方法。
然后再将它们分配给that。
```
var methodical=function(){
...
};
that.methodical=methodical;
```
　　分两步定义methodical的好处是，如果其他方法想要调用methodical，它们可以直接调用methodical（）而不是that。methodical()。如果该实例被破坏或
篡改，甚至that。methodical被替换掉了，调用methodical的方法将同样会继续工作，因此它们私有的methodical不受该实例修改的影响。函数化模式有很大的灵活性，其不仅不像伪类模式那样需要很多
功夫，且能够得到更好的封装和信息隐藏，以及访问父类方法的能力。
　　