**JavaScript ���Ծ���֮����**
------
������JavaScript���Ծ��⡷�ĵ����½�����JavaScript�е����飬JavaScript���ṩ����һ��ӵ��һЩ��������
���ԵĶ��������ݽṹ�У�������һ�����Է�����ڴ棬��ͨ������ȥ����ƫ�Ʋ��������е�Ԫ�أ���һ�ֺܿ��
�ʵ����ݽṹ��������JavaScrit�е����鲢����������һ�����ݽṹ�������ڵ��������ᵽ�ģ���JavaScript�У�
һ�нԶ����������Ҳ�Ƕ�������������±�ת����ַ�����������Ϊ���ԣ�������һ��������������Ϊ������
�������⣬�����Եļ����͸��µķ�ʽ�����һģһ����    
��������һ���У������������һЩ����֪ʶ�������ж�����ķ�ʽ�����и���һ�αȽϳ��Ĵ��룬֮ǰȷʵû��ע������ַ�ʽ

```
var is_array=function(value){
    return value&&
    typeof value==='object'&&
    typeof value.length==='number'&&
    typeof value.slice==='function'&&
    !(value.propertyIsEnumerable('length'))
}
```
���������жϵ������ֵ�Ƿ�Ϊ�棬��null������Ϊ�ٵ�ֵ������֪������JavaScript�й�������ֵ�г���Ϊ�٣��ֱ�Ϊ
false��null��undefined�����ַ���'',����0������NaN������ж��Ƿ�Ϊ������������Ҳ���������ͣ���˶��������null
�����õ�true���ٴΣ��жϴ�value�Ƿ����length���ԣ���Ȼ���󲻾��ж�������С����ģ��ж����ֵ�Ƿ����splice����������ж�length�����Ƿ���
��ö�١���δ����Ƕ������һ�κܿɿ��Ĳ��ԡ����Ǹо���Щ����ѽ����
```
������  console.log(is_array([1,2,3,4,5]));//true
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
�����ع������ж��Ƿ�Ϊ����ķ���������instnceof�����������ٶ�ֻ��һ��ȫ��ִ�л����������ҳ�а��������ܣ���ʵ���Ͼʹ����������ϲ�ͬ��
ȫ�ֻ������Ӷ������������ϲ�ͬ�汾��Array���캯���������һ���������һ����ܴ������飬��ô�����������ڶ��������ԭ������������ֱ���и��Բ�ͬ�Ĺ��캯���������һ�������ᳫ��    
��������ECMAScript5�е�`isArray()`����IE9���ϵİ汾���ã�����ڼ����Է��治�Ǻܺá�Ŀǰ�õıȽ϶�ķ�����
```
var isArray = function(obj) { 
return Object.prototype.toString.call(obj) === '[object Array]'; 
}
```
�����������arguments�����������Ԫ�أ���������'Array.prototype.slice.call(arguments)'����ת����֮������������鷽��������в�����