**精通CSS之对列表应用样式和创建导航条**
----
　　《精通CSS》的第六章是对列表应用样式和创建导航条，对创建列表以及垂直导航栏以及水平导航栏、以及纯CSS下拉菜单和图像映射等涉及列表样式的
知识。
###基本的垂直导航条  
　　基本的垂直导航条的代码如下：  
```
　　　　ul{
	        padding: 0;
			margin: 0;
			list-style-type: none;
		}
		.nav{
			width: 8em;
			background-color: #8BD400;
			border: 1px solid #486B02;
		}
		.nav a{
			display: block;
			color: #2B3B00;
			text-decoration: none;
			border-top: 1px solid #E4FFD3;
			border-bottom: 1px solid #486B02;
			padding: 0.3em 1em;
		}
		.nav .last{
			border-bottom: 0;
		}
		.nav a:hover,.nav a:focus,.nav .selected{
			color: #E4FFD3;
			background-color: #6DA203;
		}
		
		<ul class="nav">
        	　<li><a class="selected" href="home.htm">Home</a> </li>
        	　<li><a href="about.htm">About</a> </li>
        	　<li><a href="services.htm">Our</a> </li>
        	　<li><a href="work.htm">Our Work</a> </li>
        	　<li><a href="news.htm">News</a> </li>
        	　<li><a class="last" href="contact.htm">Contact</a> </li>
        </ul>
		
```
　　在上面的代码中，不对列表项应用样式，而是对其中包含的锚链接应用样式，由此提供更好的浏览器兼容性。另外，在其他浏览器下，可以得到结果如下图所示：  
![垂直导航](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/%E5%9E%82%E7%9B%B4%E5%AF%BC%E8%88%AA.png)  
　　但是在IE 6下却得到如下的效果图:  
![IE 6下效果图](https://github.com/luolala/Winter-vacation-study/blob/master/imges/IE6%20%E4%B8%8B%E5%9E%82%E7%9B%B4%E5%AF%BC%E8%88%AA.png)  
　　为了修复这个bug,可以将列表项的display修改，即
```css
.nav li{
			display: inline;
		}
```
　　对于页面中嵌入导航的小站点，只需逐个页面地添加这个类。对于大型站点，导航很可能是动态建立的，在这种情况下可以在后端
添加类。但是，对于主导航不改变的中等规模的站点，往往通过外部文件包含导航。即：在每个页面的主体元素中添加一个ID或类名，从而指出
用户当前在哪个页面或部分中。然后，在导航列表中的每个项中添加一个对应的ID或类名。可以使用主体的ID和列表ID/类的唯一
组合在站点导航中突出显示当前部分或页面。例如
```<body id="home">
```  
###水平导航栏
　　可以利用有序列表来实现水平导航栏，例如
```
	     ol{
    			margin: 0;
    			padding: 0;
    			list-style-type: none;
    		}
    		.pagination li{
    			float: left;
    			margin-right: 0.6em;
    		}
    		.pagination a,.pagination .selected{
    			display: block;
    			padding: 0.2em 0.5em;
    			border: 1px solid #ccc;
    			text-decoration: none;
    		}
    		.pagination a:hover,.pagination a:focus,.pagination .selected{
    			background-color: #09C;
    			color: #fff;
    		}
    		.pagination a[rel="prev"]:before{
    			content: "\00AB";
    			padding-right: 0.5em;
    		}
    		.pagination a[rel="next"]:after{
    			content: "\00BB";
    			padding-left: 0.5em;
    		}
    		
    		<ol class="pagination">
            		<li><a href="search.htm?page=1" rel="prev">Prev</a></li>
            		<li><a href="search.htm?page=1">1</a></li>
            		<li><a class="selected">2</a></li>
            		<li><a href="search.htm?page=3">3</a></li>
            		<li><a href="search.htm?page=4">4</a></li>
            		<li><a href="search.htm?page=5">5</a></li>
            		<li><a href="search.htm?page=6" rel="next">next</a></li>
           </ol>
	
```
　　可以得到如下的效果：  
![水平导航](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/%E6%B0%B4%E5%B9%B3%E5%AF%BC%E8%88%AA.png)  
　　如果想要得到图形更加丰富的导航栏，则还可以  
```
 　　　.nav{
			padding: 0;
			margin: 0;
			list-style: none;
			width: 52em;
			overflow: hidden;
			background: #FAA819;
		}
		.nav li{
			float: left;
		}
		.nav a{
			display: block;
			padding: 0 3em;
			line-height: 2.1em;
			text-decoration: none;
			color: #fff;
			border:  solid #FF6600;
			border-width: 1px 1px 1px 0;
		}
		.nav .first{
			border: 1px solid #FF6600;
		}
        .nav a:hover,.nav a:focus{
			color: #333;
		}
		<ul class="nav">
        		<li><a class="first" href="home.htm">Home</a> </li>
        		<li><a href="about.htm">About</a> </li>
        		<li><a href="services.htm">Our</a> </li>
        		<li><a href="work.htm">Our Work</a> </li>
        		<li><a href="news.htm">News</a> </li>
        		<li><a class="last" href="contact.htm">Contact</a> </li>
        </ul>
```　　
　　可以得到下图
![水平导航2](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/%E6%B0%B4%E5%B9%B3%E5%AF%BC%E8%88%AA2.png)
###下拉菜单  
　　可以利用多级列表以及css来设计下拉菜单
```css
　　　ul{
   			margin: 0;
   			padding: 0;
   			list-style-type: none;
   			float: left;/*闭合浮动*/
   			border: 1px solid #486B02;
   			background-color: #8BD400;
   		}
   		.nav li{
   			float: left;
   			width: 8em;
   			background-color: #8BD400;
   		}
   		.nav li ul{
   			width: 8em;
   			position: absolute;
   			left: -999em;/*隐藏到屏幕左边 */
   		}
   		.nav li:hover ul{
   			left: auto;/*显示下拉菜单*/
   		}
   		.nav a{
   			display: block;
   			color: #2B3F00;
   			text-decoration: none;
   			padding: 0.3em 1em;
   			border-right: 1px solid #486B02;
   			border-left: 1px solid #E4FFD3;
   		}
   		.nav li li a{
   			border-top: 1px solid #E4FFD3;
   			border-bottom: 1px solid #486B02;
   			border-left: 0;
   			border-right: 0;
   		}
   		.nav li:last-child a{
   			border-right:0;
   			border-bottom: 0;
   		}
   		ul a:hover,ul a:focus{
   			color: #E4FFD3;
   			background-color: #6DA203;
   		}
<ul class="nav">
	<li ><a href="/home">Home</a></li>
	<li ><a href="/products">Products</a>
	    <ul>
			<li><a href="/products/silverback/">Silverback</a></li>
			<li><a href="/products/fontdeck/">Font Deck</a></li>
		</ul>
	</li>
	<li ><a href="/services/">Services</a>
	    <ul>
			<li><a href="/services/design/">Design</a></li>
			<li><a href="/services/development/">Design</a></li>
			<li><a href="/services/consultancy/">Consultancy</a></li>
		</ul>
       </li>
	<li ><a href="/contact">Contact Us</a> </li>
</ul>
```
　这种技术适用于大多数现代浏览器，但是在IE的老版本中无效，因为它们不支持在非锚元素上使用：hover伪类。为了解决这个问题，可以使用几行
JavaScript或.htc行为文件启用这个功能。
###图像映射　　
　　书中提到的映射方法是将对锚链接进行绝对定位，定位到相应的图片上，形成热点。链接文本使用一个大的负数作为文本缩进量，然后让它们从屏幕上消失。这种办法感觉有点太麻烦了。。。
之前在[W3shool](http://www.w3school.com.cn/tiy/t.asp?f=html_areamap)上看到的方法是利用[http://www.w3school.com.cn/tags/tag_area.asp](http://www.w3school.com.cn/tags/tag_area.asp)实现的。感觉这种方法更简单
一些。

　　　


