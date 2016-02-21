**ѧϰ������JavaScript��ԭ������**
---
����������w3cplus�Ͽ�����һƪ���ģ�����"ѧϰ������JavaScript",������[Learning JavaScript Native Functions and How to Use Them](https://scotch.io/tutorials/learning-javascript-native-functions-and-how-to-use-them),������Ҫ������
`Call/Apply`��`Bind`��`Map`��`filter`�ȼ�����Ϊ��
####this��arguments����
��������ִ�е������������Ǳ�����������������ִ�е�������`this`�������õ�ǰ�����������Ĳ��ҿ����Զ��ַ�ʽ�����á�
�ϸ�ģʽ�£��������δ����ͻ��׳��쳣����������
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

��һ�����������������������滻/����ԭ�ȵĲ���������
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
����`arguments`��α���飬��˲���ֱ���������鷽��������ת��Ϊ���������飬������������ķ���
```javascript
var args = Array.prototype.slice.call(arguments);
```
###Call/Apply
���������ַ������÷����ƣ�ͨ�����ݲ����������õĺ������Է��ʻ��޸Ķ�����
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
����`call`��`apply`��Ҫ�������������ǵ�������ʽ��ͬ��`call`��Ҫ�����ֿ����ݣ���`apply`��Ҫ�����ɲ�����ɵ����顣
###Bind
����`bind`������IE 8�������²�֧�֣�����EcmaScript����չ�ģ�����Ըı������ĵ�`this`,��`call`���÷����ƣ��ɽ��ܵĲ�������Ϊ�����֣��ҵ�һ������������Ϊִ��ʱ�����������е�`this`
���󡣲�ͬ���ǣ�(1)bind �ķ���ֵ�Ǻ���
```javascript
function func(name,id) {
    console.log(name,id,this);
}
var obj = "Look here";
//ʲôҲ����
func("    ","-->");
//ʹ��bind�� ���ظı�������this��ĺ���
var a = func.bind(obj, "bind", "-->");
a();
//ʹ��call�� �ı�������this��ִ�к���
var b = func.call(obj, "call", "-->");
```
���Ϊ��
```javascript
--> Window
bind --> String 
call --> String 
```
��һ�����ڲ�����ʹ����Ҳ������,������������У�
```javascript
function f(a,b,c){
    console.log(a,b,c);
}
var f_Extend = f.bind(null,"extend_A");
f("A","B","C")  //��������--> A B C

f_Extend("A","B","C")  //��������--> extend_A A B

f_Extend("B","C")  //��������--> extend_A B C

f.call(null,"extend_A") //��������--> extend_A undefined undefined
```
�������Ϊ��
```javascript
A B C
52 extend_A A B
52 extend_A B C
52 extend_A undefined undefined
```
������������������ǿ��Կ�����`call`�ǰѵڶ������Ժ�Ĳ�����Ϊf������ʵ�δ���ȥ����`bind`��˵Ҳ�ǻ�ȡ�ڶ������Ժ�Ĳ�������֮�󷽷���ִ�У�����
`f_Extend`�д����ʵ��������bind�д�������Ļ����������ŵġ�
��������`bind`�ļ��ݴ�������ǣ�
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
����`map`�����������е�ÿһ�����и�������������ÿ�κ������ý����ɵ����顣������һ���򵥵����ӡ�
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
��ʵ�ַ����ǣ�
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
����������Ĵ����У�'forEach'Ҳ����ECMAScript5�ж���ķ�������������ÿһ�����и����������������û�з���ֵ��
###Filter
����`filter`�������е�ÿһ�����и������������ظú����᷵��'true'������ɵ����顣����һ�����������ǣ�
```javascript
arr.filter(callback[, thisArg])
```
����`thisArg`�ǿ�ѡ�Ĳ������ص�������������������`currentValue`,`index`,`array`,��Ӧ�����磺
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
�������ַ�����ʵ�ַ����ǣ�
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
����������JavaScript�еļ���ԭ���������ڲ�����IE 8�����µ������ʱ����֪`map``filter`���Լ��ٴ����������⴫ͳ��ѭ����ʽ��

����`call``apply`�Լ�`bind`��Ҫ�����⣬�������÷���