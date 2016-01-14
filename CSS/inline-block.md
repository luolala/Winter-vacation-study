**inline-block**
----------
　　 在之前读过张鑫旭大神的一篇关于利用inline-block进行浮动布局的文章[拜拜了,浮动布局-基于display:inline-block的列表布局](http://www.zhangxinxu.com/wordpress/2010/11/%E6%8B%9C%E6%8B%9C%E4%BA%86%E6%B5%AE%E5%8A%A8%E5%B8%83%E5%B1%80-%E5%9F%BA%E4%BA%8Edisplayinline-block%E7%9A%84%E5%88%97%E8%A1%A8%E5%B8%83%E5%B1%80/)，对于浮动布局每个列表元素必须保持一致以及高度塌陷等缺陷，他提出利用inline-block代替浮动进行布局。对于每一行所有的inline元素和inline-block元素会共同形成一个line boxes ,这个line box 的高度由里面最高的元素决定。所以，即使inline-block属性的列表元素高度异常，撑开的是整个line boxes 的高度，因而不会与下一行的列表元素发生错位。之前确实用到了很多次这个方法，但是忽略了它的兼容性问题。今天在用到的时候发现在这种方式下，IE7下会有不同情况。  
 　　对于原本是块级元素的元素来说，有两种方式可以解决这一问题：
	１、
```
{
 　display: inline-block;
  *display:inline;
  *zoom:1;
 }
```
　
 　　2、
 　　
```
{
 　display:inline-block;
}
{
　　display:inline;
}
```

　在第二种情况中，需注意两段display代码要分开来写。
　而对于原本是行内元素的（如`<span>`和`<a>`等）元素来说，直接写`{display：inline-block}`即可。 在今天所写的布局中，主要是利用无序列表`<li>`进行的列表布局，因此利用上面的第一种情况实现了兼容性。