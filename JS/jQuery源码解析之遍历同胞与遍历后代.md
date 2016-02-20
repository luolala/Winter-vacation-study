**jQueryԴ�����֮����ͬ����������**
----
������ѧϰ���������֮�󣬿γ��ֽ����Ž����˶�ͬ���Լ�����ı�����ͬ������ӵ����ͬ�ĸ�Ԫ�ص�Ԫ�أ�����`nextAll`,`prevAll`,
`nextUntil`,`prevUntil`��������ȵĲ��Ҵ���ǳ����ơ�  
����`.nextAll()`���ƥ��Ԫ�ؼ�����ÿ��Ԫ��֮�����е�ͬ��Ԫ�أ���ѡ��������ɸѡ(��ѡ)��`.nextUntil()`���ÿ��Ԫ��֮������
��ͬ��Ԫ�أ�ֱ������ƥ��ѡ������Ԫ��Ϊֹ��`.prevAll()`���ƥ��Ԫ�ؼ�����ÿ��Ԫ��֮ǰ������ͬ��Ԫ�أ���ѡ��������ɸѡ(��ѡ)��`prevUntil()`
���ÿ��Ԫ��֮ǰ���е�ͬ��Ԫ�أ�ֱ������ƥ��ѡ������Ԫ��Ϊֹ����˿��Գ����һ������������������������Ĵ���������£�

```javascript
function dir(elem, dir, until) {
  var matched = [],
  //�ж��Ƿ������Ҫƥ���Ԫ��
    truncate = until !== undefined;
    //Ԫ�ز���Document
  while ((elem = elem[dir]) && elem.nodeType !== 9) {
    if (elem.nodeType === 1) {
    //���������Ҫƥ���Ԫ��������ٴ��жϣ�����ֱ�ӽ�����������Ԫ�ؼ�������
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
������ˣ�����ļ�����������������`dir()`ʵ�֡�
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
����������Ա���ͬ���ķ�������`next`,`prev`,`siblings()`.`.next()`���ƥ��Ԫ�ؼ�����ÿ��Ԫ�ؽ��ڵ�ͬ��Ԫ�ء�`.prev()`���ƥ��Ԫ�ؼ�����ÿ��Ԫ�ؽ��ڵ�
ǰһ��ͬ��Ԫ�ء�`siblings()`���ƥ��Ԫ�ؼ���������Ԫ�ص�ͬ��Ԫ�أ���ѡ����ɸѡ(��ѡ)��
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
�� ���ڱ������������������`children`��`find`,�����ַ����������������Ԫ�ص���Ԫ�أ����߶����᷵��text node���䲻ͬ�ĵط�����`children`����������Ԫ�ص���һ������Ԫ�أ���`find()`�������Ի�������¼�Ԫ�ء�