**精通CSS之背景图像**
-----
　　《精通CSS》的第四章介绍了背景图像的效果，包括了圆角框、投影以及不透明度等技术，介绍了利用CSS3实现以及其他的一些方法。  
###背景图像基础  
　　在指出图像的位置时，如果使用像素设置背景位置，那么图像左上角到元素左上角的距离为指定的像素数。但是，使用百分数进行背景定位的工作方式不太一样。百分数定位并不对背景图像的
左上角进行定位，而是使用图像上的一个对应点。所以，如果指定垂直和水平位置都是20%，那么实际上是在将图像上距离左上角20%的点定位到父元素上距离左上角20%的位置。因此，如果希望使用百分数而不是关键字实现图像垂直居中，将垂直位置设置为50%即可。  
![利用像素和百分数定位背景图像](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/%E5%88%A9%E7%94%A8%E5%83%8F%E7%B4%A0%E5%92%8C%E7%99%BE%E5%88%86%E6%95%B0%E8%BF%9B%E8%A1%8C%E8%83%8C%E6%99%AF%E5%9B%BE%E5%83%8F%E5%AE%9A%E4%BD%8D.png)  
　　另外，规范指出，不要将像素或百分数等单位与关键字混合使用。虽然许多现代浏览器故意忽略了这个规则，但是，混合使用单位和关键字在某些浏览器上会导致错误，而且很可能使CSS失效，因此，最好不要混合使用单位和关键字。
###圆角框  
　　我们知道，在CSS3中，利用border-radius[CSS3的圆角Border-radius](http://www.w3cplus.com/css3/border-radius)属性，只需设置边框角的半径，浏览器就能实现圆角框。例如：  
```html
<div style="width: 100px;height: 100px;border:2px solid #FF6600;border-radius: 10px;"></div>
<div style="width: 100px;height: 100px;border:2px solid #ff3170;border-radius: 30px;margin-top: 10px;"></div>
```
　　可以得到如下图：  
![圆角框](https://github.com/luolala/Winter-vacation-study/raw/master/imges/%E5%9C%86%E8%A7%92%E6%A1%86.png)  
　　其在IE浏览器下的兼容情况是IE 9+，在较低版本的浏览器下，书中也提到了一些其他的方法。对于创建固定宽度的圆角框，只需要两个图像：一个图像用于框的顶部，另一个用于底部。而如果想要创建灵活的框，那么可以应用两个相互重叠的图像，而不是用一个图像组成顶部和底部的曲线。这个方法有时候被称为滑动门技术，因为一个图像在另一个图像上滑动，将它的一部分隐藏了起来。这个方法需要更多的图像，所以必须在标记中添加两个额外的无语义元素。
```html
<div class="box">
　　<div class="box-outer">
   <div class="box-innner">
       <h2>Headliner</h2>
        <p>Content</p>
    </div>
    </div>
</div>　
```
  这个方法需要4个图像：两个顶部图像组成顶部曲线，两个底部图像组成底部曲线和框的主体。因此，底部图像的高度必须与框的最大高度相同。
　　
###投影  
　　在CSS3中，同样有可以生成投影的属性，即[border-shadow](http://www.w3school.com.cn/cssref/pr_box-shadow.asp)属性，这个属性需要4个值：垂直和水平偏移、投影的宽度(也就是模糊程度)和颜色。
``` css
div {
　　　width: 200px;
　　　height: 200px;
　　　background-color: #1a7292;
　　　-moz-box-shadow: 10px 10px 5px #888; /* 老的 Firefox */
　　　box-shadow: 10px 10px #888;
	}

<body>
	<div></div>
</body>
```
　　可以得到下面的结果：  
![阴影](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/%E9%98%B4%E5%BD%B1%E6%95%88%E6%9E%9C.png)  
　　我觉得阴影效果是一种比较漂亮的效果，然而仍然是IE。。对其兼容性仍然不好。对于不支持CSS3属性的浏览器，可以利用Dunstan Orchard提出的一种简单的投影方法，即：将一个大的投影图像应用于容器div的背景，
然后使用负的外边距偏移图像，从而显示出投影。
　　另外有一个很相似的创建投影的方法：不使用负的外边距，而是使用相对定位来偏移图像。  
###不透明度  
　　在利用CSS实现不透明度中，有一种方法是：
``` css
.no-transparent{
　　　　　　　　width: 100px;
　　　　　　　　height: 100px;
　　　　　　　　background: #ff3170;
		}
.transparent_class {
　　　　　　　　width: 100px;
　　　　　　　　height: 100px;
　　　　　　　　background: #ff3170;
　　　　　　　　margin-top: 10px;
　　　　　　　　filter:alpha(opacity=50);
　　　　　　　　-moz-opacity:0.5;
　　　　　　　　-khtml-opacity: 0.5;
　　　　　　　　opacity: 0.5;
		}
		
<div class="no-transparent">FOR TEST</div>
<div class="transparent_class">FOR TEST</div>
```
　　可以得到下面的结果：　
![透度]()  
　　　由上图可以看出利用这种方法能够实现不透明度，但是有一个问题是：如果父元素应用了这个透明度之后，则子元素也会继承它。如果我们只想拥有有透明效果的背景，而其包含的文字等不具备这个效果，那么可以利用rgba()来实现。  
```css
.no-transparent{
　　　　　　width: 100px;
　　　　　　height: 100px;
　　　　　　background: #ff3170;
		}
.transparent_class {
　　　　　　width: 100px;
　　　　　　height: 100px;
　　　　　　background: rgb(255,49,112); /*The Fallback color*/
　　　　　　background:rgba(255,49,112,0.5);
　　　　　　-ms-filter: "progid:DXImageTransform.Microsoft.gradient(GradientType=1,startColorstr=#80FF3170,endColorstr=#80FF3170)"; /*Filter for IE8 */
　　　　　　filter: progid:DXImageTransform.Microsoft.gradient(GradientType=1,startColorstr=#80FF3170, endColorstr=#80FF3170); /*Filter for older IEs */
　　　　　　margin-top: 10px;
		}

<div class="no-transparent">FOR TEST</div>
<div class="transparent_class">FOR TEST</div>
```
![透明度](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/%E9%80%8F%E6%98%8E%E5%BA%A62.png)
　　上面用到的一种方法是[CSS3 RGBA](http://www.w3cplus.com/content/css3-rgba)中的方法“fallback color”,在不支持rgba()的浏览器中给它一个颜色。这样的话在IE 8下的是没有透明度效果的，如果想要在所有的浏览器中达到同样的效果，可以利用两个`div`来实现。
####PNG透明度  
　　PNG文件格式最大的优点之一是它支持alpha透明度，但是IE 6不直接支持PNG透明度，而IE 7 和IE 8支持。对于IE的老版本，有两种解决方法。  
　　在IE 6中支持PNG透明度的方法是使用专有的ALphaImageLoader过滤器，为此，需要再CSS中包含以下代码行。
```css
filter:progid:DXImageTransform.Microsoft.AlphaImageLoader(src='',sizingMethod='crop');
```
　　但是，使用这行代码会导致CSS无效，所以最好把它放在IE 6专用的样式表中。  
```css
.img-wrapper div{
 filter:progid:DXImageTransform.Microsoft.AlphaImageLoader(src='',sizingMethod='crop');
 background:none;
}
```
　　第一个规则使用专有的过滤器加载PNG并应用alpha透明度。原来的背景图像仍然会显示，所以第二个规则隐藏原来的背景图像。IE 还有另一种称为“有条件注释”的专有代码，折让我们可以向IE的特定版本提供特定的样式表。这里希望只让IE 6看到这个新的样式表，所以可以在页面顶部添加一下代码。
```
<!--[if ie 6]>
<link rel="stylesheet" type="text/css" href="ie6.css">
<![endif]-->
```
　　上面这种技术的问题是，对于要使用的每个透明PNG，都必须包含这行代码，可以适用在透明PNG只有少数几个的情况下，如果透明PNG比较多，可以使用的是
IE PNG fix技术。需要使用一种不太为人所知的Microsoft专有CSS扩展-行为(behavior).下载合适的.htc文件并在IE 6专用的样式表中引用它，就可以在任何元素上启用PNG透明度。
```css
div{
behavior:url(iepngfix.htc)
}

```  
　　利用背景图像等效果，可以使页面更加美观，更具有美感。因此要巧利用图像设计网页，虽然CSS3 实现了很多很好看的效果，然而如果想要适用
一些比较老式的浏览器的话，还是要注意其兼容性问题。
　　
　　