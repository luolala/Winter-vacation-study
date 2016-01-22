**line-height相关**
----
　　最近一直在看这方面的博客，发现对于行高的知识也是有很多需要注意的地方的。对于单行文字垂直居中，我们经常会用到例如下面的代码
```
<div style="width: 150px;line-height: 100px;border: 1px solid #FF6600 ">
	这是一段测试文字
</div>
```
　　效果如下图所示：  

![Alt text](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/%E5%8D%95%E8%A1%8C%E5%B1%85%E4%B8%AD.png)  


　　另外在上面的情况中去掉`height:100px`也能达到同样的效果。内容区的行高与字体尺寸有关，padding不会对行高造成影响。
```
<div style="width: 200px;border:dashed 1px #ff3170;margin-bottom:30px;">
		<span style="font-size:14px;background-color:#999;">这是一段测试文字</span>
	</div>
	<div style="width: 200px;border:dashed 1px #6f6bee;">
		<span style="font-size:14px;padding:20px;background-color:#999;">这是一段测试文字</span>
	</div>
```
结果如下图  

![Alt text](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/padding%E5%AF%B9%E8%A1%8C%E9%AB%98%E7%9A%84%E5%BD%B1%E5%93%8D.png)  

　　另外，在[W3School](http://www.w3school.com.cn/cssref/pr_dim_line-height.asp)对于`line-height`有这样一段描述
：该属性会影响行框的布局。在应用到一个块级元素时，它定义了该元素中基线之间的最小距离而不是最大距离。`line-height`与`font-size`
计算值之差(在CSS中称为‘行间距’)分为两半，分别加到一个文本内容的顶部和底部。可以包含这些内容的最小框就是行框。其可能的值为
`normal`、`number`、`length`、`%`、`inherit`这几种值，子元素在默认情况下会继承父元素的`line-height`值。对于下面的例子
```
<div style="width: 300px;border:dashed 1px #ff3714;line-height:150%;font-size:10px;">
		<p style="border:dashed 1px #ff3714;font-size:30px;">
			1232<br/>
			123
		</p>
	</div>
```
　　得到的结果如下图：  

![Alt text](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/line-height-150%25.png)  
　
　　在父元素的`line-height`为百分数时，子元素在继承的方法是：将父元素的`line-height`与`font-size`相乘，子元素继承的是
这个相乘后的结果，而在另一种情况下
```
<div style="width: 300px;border:dashed 1px #ff3714;line-height:1.5;font-size:10px;">
		<p style="border:dashed 1px #ff3714;font-size:30px;">
			1232<br/>
			123
		</p>
	</div>
```
　　得到的结果如下图  

![Alt text](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/line-height-1.5.png)  

　　与`line-height:150%`不同的是，在将此属性设置为倍数的形式时，子元素只会继承这个'缩放因子'，也就是说子元素会根据这个因子来计算
自身的行高，在此情况下也就是`30*1.5=45px`,因此与`line-height:150%`时的`10*150%=15px`结果不同。因此在文章或博客时，对于将`line-height`
设成倍数形式时一个比较好的选择。  
 　　对于`line-height`可研究的点还是有很多需要学习的地方的，对于这些方面的学习还应该加强。另外从这方面也可以看出，对于CSS方面的知识点
 还有很多需要注意的地方，有些地方看些细小却可能影响全局。CSS的学习任重道远。。。。
　　
