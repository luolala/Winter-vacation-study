**精通CSS之对链接应用样式**
----
　　《精通CSS》的第五章是对链接应用样式，其中提到了几种在应用链接时要注意的增强用户体验的方面，同时也给出了解决方案。  
###简单链接样式  
　　对链接应用样式最容易的方式是使用锚类型选择器。例如
```css
a{color:red};
```
　　但是，有时会出现下面的情况，锚可以作为内部引用，也可以作为外部链接，即<a>既可以作为超链接也可以作为片段标识符例如：
```html
<p><a href="#mainContent">Skip to main content</a></p>
....
<h1><a name="mainContent">Welconme</a></h1>
```
　　上面的代码产生的效果会是：在用户单击第一个锚时，页面将跳转到第二个锚的位置。虽然只想让真正的链接变成红色，但是标题的内容也变成了红色。可以利用伪类选择器来避免这个问题。
在锚类型的伪类选择器中，其选择器的次序非常重要。分别为

* a:link,   寻找没有被访问过的链接；
* a:visited,寻找被访问过的链接；
* a:hover,   寻找鼠标悬停处的元素；
* a:focus,   寻找获得焦点的元素；
* a:active  寻找被激活的元素；  

　　书中给出了一个比较好记的方法：Lord Vader Hates Furry Animals。另外需要注意的是在上面的代码行中的方式在HTML 5中是不支持的，可以在
W3School中关于[a标签](http://www.w3school.com.cn/tags/tag_a.asp)的解释中看到，则还有一种写法是
```
<p><a href="#mainContent">Skip to main content</a></p>
....
<h1 id="mainContent">Welconme</h1>
```
　　关于这两种写法，在W3school上同样有一段讨论，[使用 name 属性还是 id 属性](http://www.w3school.com.cn/tags/att_a_name.asp),在[StackOverflow](http://stackoverflow.com/questions/484719/html-anchors-with-name-or-id)上也看到了一个相关问题，一起贴上来
###应用链接增强用户体验的一些技巧
　　1、从易用性和可访问性的角度来说，通过颜色之外的某些方式让链接区别于其他内容是很重要的。这是因为许多有视觉障碍的人很难区分
对比不强烈的颜色，尤其是在文本比较小的情况下。因此，默认情况下，链接时有下划线的。但是由于下划线会使页面看上去比较乱，所以可以去掉下划线，当鼠标悬停在链接上或激活链接时，可以重新应用下划线，从而增强其
交互状态。也可以使用边框创建不太影响美观的下划线。  
　　2、不同的已访问链接样式可以帮助用户，让他们知道哪些页面或站点他们已经访问过了，避免不必要的“回溯”操作。通过在每个已访问链接的旁边添加一个复选框，就可以创建一种非常简单的已访问链接的样式。  
　　3、除了链接到指定的文档外，还可以使用包含片段标识符的链接链接到页面的特定部分。但是，如果页面内容非常多，常常很难看出链接把你转到了
哪个元素，CSS 3允许使用`:target`伪类为目标元素设置样式。还可以为目标元素设置动画背景图像。  
　　4、在很多站点上，很难看出链接是指向本站点的另一个页面，还是指向另一个站点。书中提到了这样一个经历：单击一个链接，期望浏览器转到当前站点上的
另一个页面，却被带到了别处。为了解决这个问题，许多站点在新窗口中打开外部链接。但是，这也不是一个好办法，因为它使用户失去了控制能力，而且这些多余的窗口可能会弄乱用户的桌面。如果没有通知用户出现了新窗口，这还会给屏幕阅读器用户造成问题。另外，新窗口实际上无法使用后退按钮，因为不可能返回
到前一个屏幕。一个比较好的解决方案是让外部链接看起来不一样，让用户自己选择时离开当前站点，还是在新窗口或新的标签页中打开这个链接。因此，可以在外部链接旁加一个小图标。  
　　5、锚是行内元素，这意味着只有在单击链接的内容时它们才会激活。但是，有时候希望实现更像按钮的效果，有更大的可单击区域。因此，可将锚的`display`属性设置为`block`。另外，选择这种技术，须确保元素是真正的链接，而不是更新服务器，绝不要使用链接更新服务器。或者说，链接应该只用于GET
请求，绝不要用于POST请求。  
　　这一章主要对链接应用样式进行了介绍，在一些增强用户体验方面，我认为要视网站的用途等情况而定，比如对于第四点，在外部链接增加小图标，如果一个网页应用了较多的外部链接，那么这种方式反而会使页面看起来比较乱。
总之，在用户体验方面，要视具体情况应用不同的设计以及处理方式。

　　

