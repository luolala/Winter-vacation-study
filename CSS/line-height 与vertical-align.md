**line-height��vertical-align**
-----
����������д�����ʱ���ֶ�������Ԫ�ؼ���һЩ�������Ļ����٣�����Щ���������������е�֪ʶ�㻹������ģ�ƽ��������Щ�ù�Ҳֻ��֪��Ȼ��
��֪������Ȼ���⼸�����úÿ�һ���ⷽ������ݡ�  
��������line-height����[W3Shool](http://www.w3school.com.cn/cssref/pr_dim_line-height.asp)�϶���������ǣ�line-height���������м�ľ���(�и�)����ô�иߵ��������������أ�
�и���ָ�ı��л��߼�Ĵ�ֱ���롣(���������ͼ������[CSS�иߡ���line-height](http://www.cnblogs.com/dolphinX/p/3236686.html)��)
![Alt text](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/%E8%A1%8C%E9%AB%98.png)  
����
��������Ļ���������������ɫ���ߣ�����и�Ϊ1��2��3��4����ĸ߶�֮�͡�ͼ�д��ϵ��������߷ֱ��Ƕ��ߡ����ߡ����ߺ͵��ߣ���`vertical-align`��������top��middle��baseline���������������йء�
��`vertical-align`�У���Ĭ�ϵĶ��뷽ʽ��baseline��Ҳ���ǻ��߶��롣����һ�����ӣ�
```css
    body {
    	  margin: 0;
          font: 32px/1 'Microsoft YaHei';
    }
    .div1 {
    	   width: 400px;
    	   margin: 30px auto;
    	   background: #008E59;
    	 }
    img {
    	   height: 80px;
    	   margin-top: 10px;
    	}
    	
    	<div class="div1">
            <span>Some Text</span>
            <img src="����.jpg" alt="�ǿ�"/>
        </div>
```
�������Եõ�

![Alt text](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/%E5%AF%B9%E9%BD%901.png)  

���������ͼ�п��Կ�����Some Text���Ļ�����ͼƬ�ĵײ����룬����±��ػ���һС�ο�϶�������Ҫȥ����ο�϶�������ж��ַ�������������vertical-alignΪ����ֵ��  
����`vertical-aligen:bottom`Ч������ͼ

![Alt text](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/vertical-align-bottom.png)

��`vertical-aligen:middle`Ч������ͼ

![Alt text](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/vertical-align-middle.png)

������`.div1`��`line-height`����Ϊһ���Ƚ�С��ֵ����Ϊ����Ŀ�϶ʵ�������ֻ�����߿�ײ��ľ��룬���и�ֵ��Ϊ�Ƚ�С��ֵ����ʵ������ռ�ݵĸ߶ȵľͻ��������ֻ��ߵ����棬��ͼƬ���������ײ���Ե�غϡ�  
����`line-height:5px`Ч������ͼ

��![Alt text](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/line-height-5px.png)  

����������`font-size`��`line-height`�йأ�������`.div1{font-size:0}`Ҳ�ܴﵽͬ����Ч�����������`display:block`��Ԫ�أ�vertica1-align��ʧȥ���ã����Ҳ�ɽ�ͼ����д����ã�������ʱͼƬ������һ����ʾ��  
������[CSS�������vertical-align��line-height�Ļ��ѹ�ϵ](http://www.zhangxinxu.com/wordpress/2015/08/css-deep-understand-vertical-align-and-line-height/)�����ᵽ��һ��inline-blockԪ�أ��������û��inline����Ԫ�أ�
����overflow����visible�����Ԫ�صĻ��߾�����margin�ױ�Ե����������߾���Ԫ���������һ������Ԫ�صĻ��ߡ��������е������ټ���һ��
```css
  .dib-baseline {
              display: inline-block; width: 150px; height: 150px;
              border: 1px solid #cad5eb; background-color: #f0f3f9;
              }
		     
    <span class="dib-baseline"></span>
    <span class="dib-baseline">x-baseline</span>
```
�������Եõ�ͼ

![Alt text](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/x-baseline%201.png)  

�����������Ҳӡ֤������˵�����ڵ�һ��������û������Ԫ�أ�����������������margin�ױ�Ե�����ڵڶ��������У������Ϊ�����
һ������Ԫ�صĻ��ߣ�Ҳ����x��ĸ���±�Ե�����߿�2���и�����Ϊ`line-height:0`�����Եõ�����

![Alt text](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/line-height0-chrome.png)����

![Alt text](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/line-height0-ff.png)  

��������ֱ�����chrome��Firefox������µõ��Ľ�������Կ���������ͼ�У����ֵ�λ�����в�ͬ���������ֲ�ͬ��ԭ�����һ��˼����  
����ͨ�������ѧϰ���Ҹо����Ժܶ࿴�ƺܼ򵥵�֪ʶ�����п���ǣ���ܶ�֪ʶ��Ҫ������ԭ����һ�����׵��£�ͬʱҪ�Ժܶ�֪ʶ����̵���⣬
���������ᵽ��һЩ֪ʶ��˵�����кܶ�����������Ҫȥ�о���CSS�Ŀ��Ƽ򵥣�ʵ���кܶ���������У�������Ҳ�������������ڰɣ�·��������Զ�⡣����
