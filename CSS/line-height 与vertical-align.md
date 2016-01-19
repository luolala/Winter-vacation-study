**line-height与vertical-align**
-----
　　近日在写程序的时候发现对于行内元素及其一些特性理解的还很少，找了些资料来读发现其中的知识点还是蛮多的，平常可能有些用过也只是知其然而
不知其所以然，这几天打算好好看一下这方面的内容。  
　　对于line-height，在[W3Shool](http://www.w3school.com.cn/cssref/pr_dim_line-height.asp)上对于其解释是：line-height属性设置行间的距离(行高)，那么行高到底是怎样计算呢？
行高是指文本行基线间的垂直距离。(下面的这张图是引自[CSS行高——line-height](http://www.cnblogs.com/dolphinX/p/3236686.html)的)
![Alt text](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/%E8%A1%8C%E9%AB%98.png)  
　　
　　这里的基线是上下两条红色的线，因此行高为1、2、3、4区域的高度之和。图中从上到下四条线分别是顶线、中线、基线和底线，而`vertical-align`属性中有top、middle、baseline，即与这四条线有关。
在`vertical-align`中，其默认的对齐方式是baseline，也就是基线对齐。来试一个例子：
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
            <img src="静谧.jpg" alt="星空"/>
        </div>
```
　　可以得到

![Alt text](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/%E5%AF%B9%E9%BD%901.png)  

　　上面的图中可以看到“Some Text”的基线与图片的底部对齐，因此下边沿还有一小段空隙。如果想要去掉这段空隙，可以有多种方法，比如设置vertical-align为其他值；  
　　`vertical-aligen:bottom`效果如下图

![Alt text](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/vertical-align-bottom.png)

　`vertical-aligen:middle`效果如下图

![Alt text](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/vertical-align-middle.png)

　　将`.div1`的`line-height`设置为一个比较小的值，因为下面的空隙实际是文字基线与边框底部的距离，将行高值设为比较小的值，则实际文字占据的高度的就会在在文字基线的上面，则图片会与容器底部边缘重合。  
　　`line-height:5px`效果如下图

　![Alt text](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/line-height-5px.png)  

　　另由于`font-size`与`line-height`有关，则将设置`.div1{font-size:0}`也能达到同样的效果。另外对于`display:block`的元素，vertica1-align将失去作用，因此也可将图像进行此设置，不过此时图片会另起一行显示。  
　　在[CSS深入理解vertical-align和line-height的基友关系](http://www.zhangxinxu.com/wordpress/2015/08/css-deep-understand-vertical-align-and-line-height/)中又提到：一个inline-block元素，如果里面没有inline内联元素，
或者overflow不是visible，则该元素的基线就是其margin底边缘，否则，其基线就是元素里面最后一行内联元素的基线。以文章中的例子再检验一下
```css
  .dib-baseline {
              display: inline-block; width: 150px; height: 150px;
              border: 1px solid #cad5eb; background-color: #f0f3f9;
              }
		     
    <span class="dib-baseline"></span>
    <span class="dib-baseline">x-baseline</span>
```
　　可以得到图

![Alt text](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/x-baseline%201.png)  

　　这个例子也印证了上述说法，在第一个方框中没有内联元素，因此其基线是容器的margin底边缘，而在第二个方框中，其基线为其最后
一行内联元素的基线，也就是x字母的下边缘。将边框2的行高设置为`line-height:0`，可以得到　　

![Alt text](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/line-height0-chrome.png)　　

![Alt text](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/line-height0-ff.png)  

　　上面分别是在chrome与Firefox浏览器下得到的结果，可以看到在两张图中，文字的位置略有不同，关于这种不同的原因还须进一步思考。  
　　通过今天的学习，我感觉到对很多看似很简单的知识，其中可能牵扯很多知识，要搞清其原理不是一件容易的事，同时要对很多知识有深刻的理解，
仅从上面提到的一些知识来说，还有很多其他方面需要去研究，CSS的看似简单，实则有很多奥妙在其中，或许这也是它的魅力所在吧，路漫漫其修远兮。。。
