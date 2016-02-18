**jQuery源码解析之遍历祖先**
----
　这一周打算学习一下jQuery源码，在慕课网上有一个相关的文字教程，感觉还不错，打算按这个教程来学习。今天看的少一点，主要看的是
DOM部分遍历祖先的实现。
```javascript
function parent(elem) {
   var parent = elem.parentNode;
   return parent && parent.nodeType !== 11 ? parent : null;
 }
```
　　parent()方法允许我们能够在DOM树中搜索到这些元素的父级元素，有序的向上匹配元素，并根据匹配的元素创建一个新的jQuery对象。在
上面的方法中需要注意的是，在返回的时候需要判断`parent.nodeType`是否是'DocumentFragment',在《javaScript语言精粹》中的第385页介绍
到：DocumentFragment是一种特殊的Node，它作为其他节点的一个临时容器，其创建方式为：

```javascript
var frag=document.createDocumentFragment();
```
　　它的`parentNode`总是为`null`,但类似Element,它可以有任意多的子节点，可以用appendChild()、insertBefore()等方法来
操作它们。  
　　DocumentFragment的特殊之处在于它使得一组节点被当作一个节点看待：如果给`appendChild()`、`insertBefore()`、`replaceChild()`
传递一个`DocumentFragment`,其实是将该文档片段的所有子节点插入到文档中，而非片段本身。(文档片段的子节点从片段移动到文档中，文档片段清空以便重用）。例如倒序排列
一个节点的子节点。

```javascript
//倒序排列节点n的子节点
function reverse(n){
 var f=document.createDocumentFragment();
 while(n.lastChild) f.appendChild(n.lastChild);
 n.appendChild(f);
}
```
```javascript
function parents(elem){
  var matched = [];
   //将元素的父节点赋值给当前的节点，当操作可执行且元素不是`Document`节点
  while ( (elem = elem['parentNode']) && elem.nodeType !== 9 ) {
   //判断元素是否是Element节点
    if ( elem.nodeType === 1 ) {
      matched.push( elem );//如果符合要求则将其加入数组中。
    }
  }
  return matched;
}
```
　　`parents()`方法与`parent()`方法不同的地方是获得当前匹配元素集合中每个元素的祖先元素。另一个相关的方法是`parentUntil()`
```javascript
function parentsUntil(elem, filter) {
  var matched = [],
    until,
    truncate = filter !== undefined;//判断filter是否存在
  while ((elem = elem['parentNode']) && elem.nodeType !== 9) {
    if (elem.nodeType === 1) {
      if (truncate) {
        if(elem.nodeName.toLowerCase() ==filter){//判断元素是否与filter一致，是则跳出循环，否则循环继续。
          break;
        }
      }
      matched.push(elem);
    }
  }
  return matched;
}
```
　　`parentsUtil()`方法会找遍所有这些元素的前辈元素，直到遇到了跟元素参数匹配的元素才会停止。返回的jQuery对象中包含了所有找到的前辈元素，除了与`.parentUtil()`选择器匹配的那个元素。
　　值得注意的是，在jQuery中对这几种方法的实现的写法并不是这样的，其提取了这些方法中内容相似的部分，然后封装了一个函数，
在学习了其他遍历方法后再对进行介绍。今天时间紧迫，只看了一小部分，明天要开始多积累了~