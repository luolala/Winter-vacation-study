**精通CSS之可视化模型**
------
　　《精通CSS》的第三章主要介绍的是三个在CSS中最重要的概念：浮动、定位和盒模型，这几个概念控制在页面上安排和显示元素的方式，形成CSS的基本布局。  
####盒模型  
　　页面上的每个元素被看做一个矩形框，这个框由元素的内容、内边距、边框和外边距组成。其模型如下图所示：  
![盒模型](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/CSS%E7%9B%92%E6%A8%A1%E5%9E%8B.png)  
　　如果在元素上添加背景，那么背景会应用于由内容和内边距组成的区域。CSS2.1还包含outline属性。与border属性不同，轮廓绘制在元素框上，所以它们不影响元素的大小和
定位。因此，轮廓有助于修复bug,因为它们不影响页面的布局。大多数现代浏览器(包括IE 8)支持轮廓，但是IE 7和更低版本不支持轮廓。同样我们知道，在IE的
早期版本中，包括IE 6，在混杂模式中使用自己的非标准盒模型，这些浏览器的width属性不是内容的宽度，而是内容、内边距和边框的宽度总和。我们可以利用CSS3的[box-sizing](http://www.w3school.com.cn/cssref/pr_box-sizing.asp)
来定义使用哪种盒模型，但是除了一些非常特殊的场合之外很少需要使用这个属性。不要给元素添加具有指定宽度的内边距，而是尝试将内边距或外边距添加到元素的父元素或子元素是回避这个问题的一个解决方案。
####外边距叠加  
　　当两个或更多垂直边距相遇时，它们将形成一个外边距。这个外边距的高度等于两个发生叠加的外边距的高度中的较大者。  
![外边距叠加](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/%E5%A4%96%E8%BE%B9%E8%B7%9D%E5%8F%A0%E5%8A%A0.png)  
　　外边距甚至可以与本身发生叠加,下面外边距发生叠加的不同的情况。  
　　元素的外边距与父元素的外边距发生叠加。   
![外边距叠加](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/%E5%A4%96%E8%BE%B9%E8%B7%9D%E5%8F%A0%E5%8A%A02.png)  
　　元素的顶边距与底边距发生叠加。  
![外边距叠加](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/%E5%A4%96%E8%BE%B9%E8%B7%9D%E5%8F%A0%E5%8A%A03.png)  
　　　空元素已经叠加的外边距与另一个空元素的外边距发生叠加。  
![外边距叠加](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/%E5%A4%96%E8%BE%B9%E8%B7%9D%E5%8F%A0%E5%8A%A04.png)  
　　如果想要避免外边距的叠加，我们知道利用BFC可以达到这一目的。如
```css
.div1{
　　　width: 100px;
　　　height: 100px;
　　　background: #ff3714;
　　　margin: 20px;
　　}
.div2{
    　width: 100px;
    　height: 100px;
    　background: #192492;
    　margin: 20px;
	}
<body>
	<div class="div1"></div>
	<div class="div2"></div>
	
</body>
```  
　　上面的代码我们可以得到下面的结果，发生了margin叠加。  
  ![没有生成BFC](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/%E6%B2%A1%E6%9C%89%E7%94%A8BFC.png)  
  　　当生成BFC时，则
```
.wrap{
	　overflow: hidden;
	}
.div1{
	　width: 100px;
	　height: 100px;
	　background: #ff3714;
	　margin: 20px;
	}
.div2{
	　width: 100px;
	　height: 100px;
	　background: #192492;
	　margin: 20px;
	}

<body>
	<div class="div1"></div>
	<div class="wrap">
	　　　<div class="div2"></div>
	</div>
</body>
```
则得到的结果如下图所示:  
![生成BFC](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/%E7%94%9F%E6%88%90BFC.png)  
　　可以看到上下两个框的距离明显大于上一个图。没有发生margin重叠。另外在普通文档流中块框的垂直外边距才会发生外边距叠加，行内框、浮动框或绝对定位框之间的外边距不会叠加。  
####定位概述
　　`p`、`h1`、`div`等元素常常称为块级元素，这意味着这些元素显示为一块内容，即“块框”。`span`、`strong`等元素称为行内元素，因为它们的内容显示在行中，即
“行内框”。行内框在一行中水平排列。可以使用水平边距、边框和外边距调整它们之间的水平间距，但是，垂直内边距、边框和外边距不影响行内框的高度。在行内框上设置显示的高度或
宽度也没有影响。由一行形成的水平框称为行框，行框的高度总是足以容纳它包含的所有行内框，设置行高可以增加这个框的高度。因此，修改行内框尺寸的唯一方法是修改行高或者水平
边框、内边距或外边距。  
　　CSS中有三种基本的定位机制：普通流、浮动和绝对定位。除非专门制定，否则所有框都在普通流中定位。  
　　框可以按照HTML元素的嵌套方式包含其他框。在一种情况下，即使没有进行显示定义，也会创建块级元素。这种情况发生在将一些文本添加到一个块级元素的开头时，即使没有把这些文本定义为块级元素，它
也会被当成块级元素对待，如
```html
<div>
　　　some text
　　　<p>some more text</p>
</div>
```  
　　得到结果如下图所示：  
![匿名块框](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/%E5%8C%BF%E5%90%8D%E5%9D%97%E6%A1%86.png)  
　　在这种情况下，这个框称为匿名块框，因为它不与专门定义的元素相关联。  
#####相对定位、绝对定位与固定定位  
　　在使用相对定位时，无论是否移动，元素仍然占据原来的空间。因此，移动元素会导致它覆盖其他框。  
　　绝对定位的框与文档流无关，所以它们可以覆盖页面上的其他元素。可以通过设置`z-index`属性来控制这些框的叠放次序。
`z-index`值越高，框在栈中的位置就越高。相对于已经相对定位的祖先元素对框进行绝对定位，在Windows上的IE 5.5和IE 6中有一个bug,如果
要相对于相对定位的框的右边或底部设置绝对定位的框的位置，那么需要确保相对定位的框已经设置了尺寸。如果没有，那么IE会错误地相对于画布定位这个框。  
　　固定定位是绝对定位的一种，差异在于固定元素的包含块是视口(viewport).这使我们能够创建总是出现在窗口中相对位置的浮动元素。不过，在IE 6和更低版本
不支持固定定位。IE 7部分支持这个属性，但是实现中有许多bug.可以利用JavaScript在IE 中重现这个效果。  
######浮动  
　　浮动的框可以左右移动，直到它的外边缘碰到包含框或另一个浮动框的边缘。因为浮动框不在文档流的普通流中，所以文档的普通流中的
块框表现得就像浮动框不存在一样。  
　　浮动会让元素脱离文档流，不再影响不浮动的元素。实际上，并不完全如此，如果浮动元素的后面有一个文档流中的元素，那么这个元素的框会表现得像浮动根本不存在一样。但是，框的文本会受到浮动元素的影响，会移动以留出空间。即，
浮动元素旁边的行框被缩短，从而给浮动元素流出空间，因此行框围绕浮动框。创建浮动框可以围绕图像。
　　清楚浮动可以有多种方式，包括添加一个空元素并应用`clear`,利用BFC，还有一种是
```
.clear:after{
  content:".";
  height:0;
  visibility:hidden;
  display:block;
  clear:both;
}
```  
　　然而这种方式在IE 6中也不起作用，书中提到了最常用的解决方案是用到 Holly hack。
```
.clear{
 display:inline-block;
}
/*Holly Hack Targets IE Win only*/
*html .clear{height:1%;}
.clear {display:block;}
/*End Holly Hack*/
```  
　　关于清除浮动，[那些年我们一起清除的浮动](http://www.iyunlu.com/view/css-xhtml/55.html)这篇文章讲得很全面。这里暂且先不展开写。  
　　这本书的这一章介绍了需要用到的一些基本知识，有了这些，就可以进行基本的布局了，通过这一章的学习把一些概念又再次复习巩固了一遍并加强了理解。
感觉收获还是蛮大的，这本书还要好好读下去。
