**��ͨCSS֮����ͼ��**
-----
��������ͨCSS���ĵ����½����˱���ͼ���Ч����������Բ�ǿ�ͶӰ�Լ���͸���ȵȼ���������������CSS3ʵ���Լ�������һЩ������  
###����ͼ�����  
������ָ��ͼ���λ��ʱ�����ʹ���������ñ���λ�ã���ôͼ�����Ͻǵ�Ԫ�����Ͻǵľ���Ϊָ���������������ǣ�ʹ�ðٷ������б�����λ�Ĺ�����ʽ��̫һ�����ٷ�����λ�����Ա���ͼ���
���Ͻǽ��ж�λ������ʹ��ͼ���ϵ�һ����Ӧ�㡣���ԣ����ָ����ֱ��ˮƽλ�ö���20%����ôʵ�������ڽ�ͼ���Ͼ������Ͻ�20%�ĵ㶨λ����Ԫ���Ͼ������Ͻ�20%��λ�á���ˣ����ϣ��ʹ�ðٷ��������ǹؼ���ʵ��ͼ��ֱ���У�����ֱλ������Ϊ50%���ɡ�  
![�������غͰٷ�����λ����ͼ��](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/%E5%88%A9%E7%94%A8%E5%83%8F%E7%B4%A0%E5%92%8C%E7%99%BE%E5%88%86%E6%95%B0%E8%BF%9B%E8%A1%8C%E8%83%8C%E6%99%AF%E5%9B%BE%E5%83%8F%E5%AE%9A%E4%BD%8D.png)  
�������⣬�淶ָ������Ҫ�����ػ�ٷ����ȵ�λ��ؼ��ֻ��ʹ�á���Ȼ����ִ���������������������򣬵��ǣ����ʹ�õ�λ�͹ؼ�����ĳЩ������ϻᵼ�´��󣬶��Һܿ���ʹCSSʧЧ����ˣ���ò�Ҫ���ʹ�õ�λ�͹ؼ��֡�
###Բ�ǿ�  
��������֪������CSS3�У�����border-radius[CSS3��Բ��Border-radius](http://www.w3cplus.com/css3/border-radius)���ԣ�ֻ�����ñ߿�ǵİ뾶�����������ʵ��Բ�ǿ����磺  
```html
<div style="width: 100px;height: 100px;border:2px solid #FF6600;border-radius: 10px;"></div>
<div style="width: 100px;height: 100px;border:2px solid #ff3170;border-radius: 30px;margin-top: 10px;"></div>
```
�������Եõ�����ͼ��  
![Բ�ǿ�](https://github.com/luolala/Winter-vacation-study/raw/master/imges/%E5%9C%86%E8%A7%92%E6%A1%86.png)  
��������IE������µļ��������IE 9+���ڽϵͰ汾��������£�����Ҳ�ᵽ��һЩ�����ķ��������ڴ����̶���ȵ�Բ�ǿ�ֻ��Ҫ����ͼ��һ��ͼ�����ڿ�Ķ�������һ�����ڵײ����������Ҫ�������Ŀ���ô����Ӧ�������໥�ص���ͼ�񣬶�������һ��ͼ����ɶ����͵ײ������ߡ����������ʱ�򱻳�Ϊ�����ż�������Ϊһ��ͼ������һ��ͼ���ϻ�����������һ�������������������������Ҫ�����ͼ�����Ա����ڱ����������������������Ԫ�ء�
```html
<div class="box">
����<div class="box-outer">
   <div class="box-innner">
       <h2>Headliner</h2>
        <p>Content</p>
    </div>
    </div>
</div>��
```
  ���������Ҫ4��ͼ����������ͼ����ɶ������ߣ������ײ�ͼ����ɵײ����ߺͿ�����塣��ˣ��ײ�ͼ��ĸ߶ȱ����������߶���ͬ��
����
###ͶӰ  
������CSS3�У�ͬ���п�������ͶӰ�����ԣ���[border-shadow](http://www.w3school.com.cn/cssref/pr_box-shadow.asp)���ԣ����������Ҫ4��ֵ����ֱ��ˮƽƫ�ơ�ͶӰ�Ŀ��(Ҳ����ģ���̶�)����ɫ��
``` css
div {
������width: 200px;
������height: 200px;
������background-color: #1a7292;
������-moz-box-shadow: 10px 10px 5px #888; /* �ϵ� Firefox */
������box-shadow: 10px 10px #888;
	}

<body>
	<div></div>
</body>
```
�������Եõ�����Ľ����  
![��Ӱ](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/%E9%98%B4%E5%BD%B1%E6%95%88%E6%9E%9C.png)  
�����Ҿ�����ӰЧ����һ�ֱȽ�Ư����Ч����Ȼ����Ȼ��IE���������������Ȼ���á����ڲ�֧��CSS3���Ե����������������Dunstan Orchard�����һ�ּ򵥵�ͶӰ������������һ�����ͶӰͼ��Ӧ��������div�ı�����
Ȼ��ʹ�ø�����߾�ƫ��ͼ�񣬴Ӷ���ʾ��ͶӰ��
����������һ�������ƵĴ���ͶӰ�ķ�������ʹ�ø�����߾࣬����ʹ����Զ�λ��ƫ��ͼ��  
###��͸����  
����������CSSʵ�ֲ�͸�����У���һ�ַ����ǣ�
``` css
.no-transparent{
����������������width: 100px;
����������������height: 100px;
����������������background: #ff3170;
		}
.transparent_class {
����������������width: 100px;
����������������height: 100px;
����������������background: #ff3170;
����������������margin-top: 10px;
����������������filter:alpha(opacity=50);
����������������-moz-opacity:0.5;
����������������-khtml-opacity: 0.5;
����������������opacity: 0.5;
		}
		
<div class="no-transparent">FOR TEST</div>
<div class="transparent_class">FOR TEST</div>
```
�������Եõ�����Ľ������
![͸��]()  
����������ͼ���Կ����������ַ����ܹ�ʵ�ֲ�͸���ȣ�������һ�������ǣ������Ԫ��Ӧ�������͸����֮������Ԫ��Ҳ��̳������������ֻ��ӵ����͸��Ч���ı�����������������ֵȲ��߱����Ч������ô��������rgba()��ʵ�֡�  
```css
.no-transparent{
������������width: 100px;
������������height: 100px;
������������background: #ff3170;
		}
.transparent_class {
������������width: 100px;
������������height: 100px;
������������background: rgb(255,49,112); /*The Fallback color*/
������������background:rgba(255,49,112,0.5);
������������-ms-filter: "progid:DXImageTransform.Microsoft.gradient(GradientType=1,startColorstr=#80FF3170,endColorstr=#80FF3170)"; /*Filter for IE8 */
������������filter: progid:DXImageTransform.Microsoft.gradient(GradientType=1,startColorstr=#80FF3170, endColorstr=#80FF3170); /*Filter for older IEs */
������������margin-top: 10px;
		}

<div class="no-transparent">FOR TEST</div>
<div class="transparent_class">FOR TEST</div>
```
![͸����](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/%E9%80%8F%E6%98%8E%E5%BA%A62.png)
���������õ���һ�ַ�����[CSS3 RGBA](http://www.w3cplus.com/content/css3-rgba)�еķ�����fallback color��,�ڲ�֧��rgba()��������и���һ����ɫ�������Ļ���IE 8�µ���û��͸����Ч���ģ������Ҫ�����е�������дﵽͬ����Ч����������������`div`��ʵ�֡�
####PNG͸����  
����PNG�ļ���ʽ�����ŵ�֮һ����֧��alpha͸���ȣ�����IE 6��ֱ��֧��PNG͸���ȣ���IE 7 ��IE 8֧�֡�����IE���ϰ汾�������ֽ��������  
������IE 6��֧��PNG͸���ȵķ�����ʹ��ר�е�ALphaImageLoader��������Ϊ�ˣ���Ҫ��CSS�а������´����С�
```css
filter:progid:DXImageTransform.Microsoft.AlphaImageLoader(src='',sizingMethod='crop');
```
�������ǣ�ʹ�����д���ᵼ��CSS��Ч��������ð�������IE 6ר�õ���ʽ���С�  
```css
.img-wrapper div{
 filter:progid:DXImageTransform.Microsoft.AlphaImageLoader(src='',sizingMethod='crop');
 background:none;
}
```
������һ������ʹ��ר�еĹ���������PNG��Ӧ��alpha͸���ȡ�ԭ���ı���ͼ����Ȼ����ʾ�����Եڶ�����������ԭ���ı���ͼ��IE ������һ�ֳ�Ϊ��������ע�͡���ר�д��룬�������ǿ�����IE���ض��汾�ṩ�ض�����ʽ������ϣ��ֻ��IE 6��������µ���ʽ�����Կ�����ҳ�涥�����һ�´��롣
```
<!--[if ie 6]>
<link rel="stylesheet" type="text/css" href="ie6.css">
<![endif]-->
```
�����������ּ����������ǣ�����Ҫʹ�õ�ÿ��͸��PNG��������������д��룬����������͸��PNGֻ����������������£����͸��PNG�Ƚ϶࣬����ʹ�õ���
IE PNG fix��������Ҫʹ��һ�ֲ�̫Ϊ����֪��Microsoftר��CSS��չ-��Ϊ(behavior).���غ��ʵ�.htc�ļ�����IE 6ר�õ���ʽ�������������Ϳ������κ�Ԫ��������PNG͸���ȡ�
```css
div{
behavior:url(iepngfix.htc)
}

```  
�������ñ���ͼ���Ч��������ʹҳ��������ۣ����������С����Ҫ������ͼ�������ҳ����ȻCSS3 ʵ���˺ܶ�ܺÿ���Ч����Ȼ�������Ҫ����
һЩ�Ƚ���ʽ��������Ļ�������Ҫע������������⡣
����
����