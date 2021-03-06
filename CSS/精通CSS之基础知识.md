**精通CSS之基础知识**
----
　　上一周本来是想读《CSS禅意花园》的，因为在CSS书籍中这本书的推荐率也挺高的，但是不知道为什么我不怎么喜欢看这本书，可能是因为这本书对于网页的设计
思想阐述了很多，而我目前还是只想对于CSS的一些知识进行深入学习。于是我又找来了《精通CSS：高级Web标准解决方案》(第二版)，之前看过一点第一版的内容，但是比较少，但是感觉内容还是不错的，
这次决定再好好看看这本书。  
　　这本书的第一章主要讲了关于CSS的基础知识，再读一遍发现以前忽略了很多，这次再总结一下，又有了一些新收获。

　　1、语义化
　　在本章介绍标签简史之后，就介绍了关于语义化的重要性（书中的标题翻译成了意义的重要性）。这个问题在前端面试题中也是经常提到的问题。
书中对于予语义化的意义总结为三点：首先，与表现性的页面相比，语义化的页面更容易处理。从书中给出的例子来说，假设需要修改页面中的一个引用，
如果这个引用加上了正确的标记，那么很容易搜索代码，找到第一个块引用元素。但是，如果这个引用只是一个段落元素标签，就很难寻找了；其次，程序和其他设备也可以理解
有意义的标记。搜索引擎可以识别出标题并予以重视。屏幕阅读器的用户可以依靠标题进行页面导航；更重要的是，有意义的标记可以简便地将元素调整为你所需的样式。它在文档中添加结构并且创建
一个底层框架。可以直接设置元素的样式，而不需要添加其他标识符，因此避免了不必要的代码膨胀。  
　　书中列举了一些具有丰富的有意义的元素  

* h1、h2等；
* ul、ol和dl;
* strong和em;
* blackquote和cite;
* abbr、acronym和code；
* fieldset、legend和label;
* caption、thead和tbody和tfoot。  
　　当然，HTML5在语义化方面又进行了进一步加强，上面的只是一小部分。查了一下[W3C](https://www.w3.org/html/wg/drafts/html/master/obsolete.html#non-conforming-features),`acronym`这个标签已经被弃用了。另外搜索的过程中，
又看到了一个比较有意思的网站[HTML5元素](http://demo.yanue.net/HTML5element/)，也一并记录下来。

　　2、ID用于标识页面上的特定元素(如站点导航)，而且必须是唯一的。ID也可以用来标识持久的结构性元素，如主导航区或内容区域。ID还可以
用来标识一次性元素，例如某个链接或表单元素。一个ID名只能应用于页面上的一个元素，而同一个雷鸣可以应用于页面上任意多个元素，因此类的功能强大得多。类非常适合标识内容的类型或其他相似的条目。
因此，在对ID和类的选择时，对于ID一定要慎重，由于其权重较高，所以在页面书写时应尽可能利用类名。

　　3、在分配ID和类名时，一定要尽可能保持名称与表现形式无关。这个错误我是犯过的。。。之前好多地方不知道应该怎么给类命名，实在起不出名来，就用了
与表现形式有关的。书中也指出了这是一种很不好的代码风格。应该根据“它们是什么”来为元素命名，而不应该根据“它们的外观如何”来命名。这种方式会让代码更有意义，并且避免
代码与设计不同步。例如不要根据字体颜色比如‘red’来命名，而应该根据其意义来命名，书中也给出了一个对比：  
　　差的名称：red、leftColumn、topNav、firstPara  
　　好的名称：error、secondaryContent、mainNav、intro  
　　不得不说，上面提到的差的名称，我现在写程序的时候还是会冒出来，比如`leftColumn`之类的，所以以后这个方面还是要注意。

　　4、一般原则上，类应该应用于概念相似的元素，这些元素可以出现在同一页面上的多个位置，而ID应该应用于不同的唯一的元素。如果使用大量ID，很快就会难以找到唯一的
名称，最终不得不创建非常长、非常复杂的命名约定。只有在目标元素非常独特，绝不会对网站上其他地方别的东西使用这个名称时，才会使用ID。换句话说，只有在绝对确定这个元素只会出现一次的情况下，才应该
使用ID。保持命名约定通用，并且使用类，就不会出现一长串ID选择器都与非常相似的样式相关联的现象。  
　　书中提到：只要你发现类名中出现了重复的单词，比如news-head和news-link或者section-head和section-foot，就应该考虑是否可以
把这些元素分解成它们的组成部分。这会让代码更“组件化”，会大大提高灵活性。以这种方式删除不必要的类有助于简化代码，使页面更简洁。作者提的这种现象我也有啊。。。
到现在作者提到的好几种不提倡的我都出现过，这一方面现在还没有完全改掉，经常会命名类似这种news-head之类的命名，之后在这方面要更注意，看是否能简化代码。

　　5、"有助于在文档中添加结构的一个元素是div元素。许多人误以为div元素没有语义。但是，div实际上代表部分，它可以将文档分割成几个有意义的区域“
我认为现在这句话是不准确的，因为在HTML5中新加入了[section](http://www.w3school.com.cn/html5/html5_section.asp)标签，用它来定义文档中的节、
区段。`div`可以用来对块级元素进行分组，而`span`可以用来对行内元素进行分组或标识。

　　6、命名约定基于vCard和iCalendar等现有的数据格式，是开发人员开发的一套表示人、地点或日期等类型信息的标准的命名约定和标记模式。被称为微格式。
```
<div class="vcard">
  <p><a class="url fn" href="http://andybudd.com/">Andy Budd</a>
    <span class="org">Clearleft Ltd</span>
    <a class="email" href="mailto:info@andybudd.com">info@andybudd.com</a>
  </p>
  <p class="adr">
      <span class="locality">Brighton</span>
      <span class="country-name">England</span>
   </p>
 </div>
```
　　微格式可以以一种特定的方式标记数据，让其他程序和服务可以访问它。这种形式我是第一次看到，在表示日期时，在HTML5中加入了`time`,应该可以
代替这种微格式。

　　7、浏览器通过分析页面的DOCTYPE声明来了解要使用哪个DTD，由此知道要使用HTML哪个版本。浏览器模式有：标准模式与混杂模式，另外Mozilla和Safari还有第三种模式：几乎标准的模式。在标准模式中，浏览器根据规范呈现页面；在
混杂模式中，页面以一种比较宽松的向后兼容的方式显示。混杂模式通常模拟老式浏览器的行为以防止老站点无法工作。浏览器根据DOCTYPE是否存在以及
使用的是哪种DTD来选择要使用的呈现方式。包含过渡DTD和URL的DOCTYPE也导致页面以标准模式呈现，但是又过渡DTD而没有URL会导致页面以混杂模式呈现。另外，如果
DOCTYPE声明不是页面上的第一个元素，那么IE6会自动切换到混杂模式。
  
　　第一章看起来不复杂，但是也确实介绍了一些基本的知识点，有些是经常见到的，有些却还需要再注意，对于书中提到的一些问题，还需要在写程序的过程中不断
改进。
　　
　　
　　