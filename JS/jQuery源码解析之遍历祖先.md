**jQueryԴ�����֮��������**
----
����һ�ܴ���ѧϰһ��jQueryԴ�룬��Ľ��������һ����ص����ֽ̳̣��о����������㰴����̳���ѧϰ�����쿴����һ�㣬��Ҫ������
DOM���ֱ������ȵ�ʵ�֡�
```javascript
function parent(elem) {
   var parent = elem.parentNode;
   return parent && parent.nodeType !== 11 ? parent : null;
 }
```
����parent()�������������ܹ���DOM������������ЩԪ�صĸ���Ԫ�أ����������ƥ��Ԫ�أ�������ƥ���Ԫ�ش���һ���µ�jQuery������
����ķ�������Ҫע����ǣ��ڷ��ص�ʱ����Ҫ�ж�`parent.nodeType`�Ƿ���'DocumentFragment',�ڡ�javaScript���Ծ��⡷�еĵ�385ҳ����
����DocumentFragment��һ�������Node������Ϊ�����ڵ��һ����ʱ�������䴴����ʽΪ��

```javascript
var frag=document.createDocumentFragment();
```
��������`parentNode`����Ϊ`null`,������Element,���������������ӽڵ㣬������appendChild()��insertBefore()�ȷ�����
�������ǡ�  
����DocumentFragment������֮��������ʹ��һ��ڵ㱻����һ���ڵ㿴���������`appendChild()`��`insertBefore()`��`replaceChild()`
����һ��`DocumentFragment`,��ʵ�ǽ����ĵ�Ƭ�ε������ӽڵ���뵽�ĵ��У�����Ƭ�α���(�ĵ�Ƭ�ε��ӽڵ��Ƭ���ƶ����ĵ��У��ĵ�Ƭ������Ա����ã������絹������
һ���ڵ���ӽڵ㡣

```javascript
//�������нڵ�n���ӽڵ�
function reverse(n){
 var f=document.createDocumentFragment();
 while(n.lastChild) f.appendChild(n.lastChild);
 n.appendChild(f);
}
```
```javascript
function parents(elem){
  var matched = [];
   //��Ԫ�صĸ��ڵ㸳ֵ����ǰ�Ľڵ㣬��������ִ����Ԫ�ز���`Document`�ڵ�
  while ( (elem = elem['parentNode']) && elem.nodeType !== 9 ) {
   //�ж�Ԫ���Ƿ���Element�ڵ�
    if ( elem.nodeType === 1 ) {
      matched.push( elem );//�������Ҫ��������������С�
    }
  }
  return matched;
}
```
����`parents()`������`parent()`������ͬ�ĵط��ǻ�õ�ǰƥ��Ԫ�ؼ�����ÿ��Ԫ�ص�����Ԫ�ء���һ����صķ�����`parentUntil()`
```javascript
function parentsUntil(elem, filter) {
  var matched = [],
    until,
    truncate = filter !== undefined;//�ж�filter�Ƿ����
  while ((elem = elem['parentNode']) && elem.nodeType !== 9) {
    if (elem.nodeType === 1) {
      if (truncate) {
        if(elem.nodeName.toLowerCase() ==filter){//�ж�Ԫ���Ƿ���filterһ�£���������ѭ��������ѭ��������
          break;
        }
      }
      matched.push(elem);
    }
  }
  return matched;
}
```
����`parentsUtil()`�������ұ�������ЩԪ�ص�ǰ��Ԫ�أ�ֱ�������˸�Ԫ�ز���ƥ���Ԫ�زŻ�ֹͣ�����ص�jQuery�����а����������ҵ���ǰ��Ԫ�أ�������`.parentUtil()`ѡ����ƥ����Ǹ�Ԫ�ء�
����ֵ��ע����ǣ���jQuery�ж��⼸�ַ�����ʵ�ֵ�д�������������ģ�����ȡ����Щ�������������ƵĲ��֣�Ȼ���װ��һ��������
��ѧϰ�����������������ٶԽ��н��ܡ�����ʱ����ȣ�ֻ����һС���֣�����Ҫ��ʼ�������~