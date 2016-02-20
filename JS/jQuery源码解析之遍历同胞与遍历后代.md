**jQuery源码解析之遍历同胞与遍历后代**
----
　　在学习完遍历祖先之后，课程又紧接着介绍了对同胞以及后代的遍历。同胞就是拥有相同的父元素的元素，其中`nextAll`,`prevAll`,
`nextUntil`,`prevUntil`与遍历祖先的查找处理非常类似。  
　　`.nextAll()`获得匹配元素集合中每个元素之后所有的同辈元素，由选择器进行筛选(可选)。`.nextUntil()`获得每个元素之后所有
的同辈元素，直到遇到匹配选择器的元素为止。`.prevAll()`获得匹配元素集合中每个元素之前的所有同辈元素，由选择器进行筛选(可选)。`prevUntil()`
获得每个元素之前所有的同辈元素，直到遇到匹配选择器的元素为止。因此可以抽象出一个公共函数。这个公共函数的代码可以如下：

```javascript
function dir(elem, dir, until) {
  var matched = [],
  //判断是否存在需要匹配的元素
    truncate = until !== undefined;
    //元素不是Document
  while ((elem = elem[dir]) && elem.nodeType !== 9) {
    if (elem.nodeType === 1) {
    //如果存在需要匹配的元素则进行再次判断；否则直接将符合条件的元素加入数组
      if (truncate) {
        if (elem.nodeName.toLowerCase() == until || elem.className == until) {
          break;
        }
      }
      matched.push(elem);
    }
  }
  return matched;
}
```
　　因此，上面的几个方法都可以利用`dir()`实现。
```
function nextAll(elem) {
  return dir(elem, "nextSibling");
}

function prevAll(elem) {
  return dir(elem, "previousSibling");
}

function nextUntil(elem, until) {
  return dir(elem, "nextSibling", until);
}

function prevUntil(elem, until) {
  return dir(elem, "previousSibling", until);
}
```
　　另外可以遍历同胞的方法还有`next`,`prev`,`siblings()`.`.next()`获得匹配元素集合中每个元素紧邻的同辈元素。`.prev()`获得匹配元素集合中每个元素紧邻的
前一个同辈元素。`siblings()`获得匹配元素集合中所有元素的同辈元素，由选择器筛选(可选)。
```javascript
function sibling(cur, dir) {
  while ((cur = cur[dir]) && cur.nodeType !== 1) {}
  return cur;
}

function next(elem) {
  return sibling(elem, "nextSibling");
}

function prev(elem) {
  return sibling(elem, "previousSibling");
}
```
　 对于遍历后代，有两个方法`children`和`find`,这两种方法都可以用来获得元素的子元素，两者都不会返回text node。其不同的地方在于`children`方法仅仅是元素的下一级的子元素，而`find()`方法可以获得所有下级元素。