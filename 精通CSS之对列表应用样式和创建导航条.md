**��ͨCSS֮���б�Ӧ����ʽ�ʹ���������**
----
��������ͨCSS���ĵ������Ƕ��б�Ӧ����ʽ�ʹ������������Դ����б��Լ���ֱ�������Լ�ˮƽ���������Լ���CSS�����˵���ͼ��ӳ����漰�б���ʽ��
֪ʶ��
###�����Ĵ�ֱ������  
���������Ĵ�ֱ�������Ĵ������£�  
```
��������ul{
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
        	��<li><a class="selected" href="home.htm">Home</a> </li>
        	��<li><a href="about.htm">About</a> </li>
        	��<li><a href="services.htm">Our</a> </li>
        	��<li><a href="work.htm">Our Work</a> </li>
        	��<li><a href="news.htm">News</a> </li>
        	��<li><a class="last" href="contact.htm">Contact</a> </li>
        </ul>
		
```
����������Ĵ����У������б���Ӧ����ʽ�����Ƕ����а�����ê����Ӧ����ʽ���ɴ��ṩ���õ�����������ԡ����⣬������������£����Եõ��������ͼ��ʾ��  
![��ֱ����](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/%E5%9E%82%E7%9B%B4%E5%AF%BC%E8%88%AA.png)  
����������IE 6��ȴ�õ����µ�Ч��ͼ:  
![IE 6��Ч��ͼ](https://github.com/luolala/Winter-vacation-study/blob/master/imges/IE6%20%E4%B8%8B%E5%9E%82%E7%9B%B4%E5%AF%BC%E8%88%AA.png)  
����Ϊ���޸����bug,���Խ��б����display�޸ģ���
```css
.nav li{
			display: inline;
		}
```
��������ҳ����Ƕ�뵼����Сվ�㣬ֻ�����ҳ����������ࡣ���ڴ���վ�㣬�����ܿ����Ƕ�̬�����ģ�����������¿����ں��
����ࡣ���ǣ��������������ı���еȹ�ģ��վ�㣬����ͨ���ⲿ�ļ�����������������ÿ��ҳ�������Ԫ�������һ��ID���������Ӷ�ָ��
�û���ǰ���ĸ�ҳ��򲿷��С�Ȼ���ڵ����б��е�ÿ���������һ����Ӧ��ID������������ʹ�������ID���б�ID/���Ψһ
�����վ�㵼����ͻ����ʾ��ǰ���ֻ�ҳ�档����
```<body id="home">
```  
###ˮƽ������
�����������������б���ʵ��ˮƽ������������
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
�������Եõ����µ�Ч����  
![ˮƽ����](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/%E6%B0%B4%E5%B9%B3%E5%AF%BC%E8%88%AA.png)  
���������Ҫ�õ�ͼ�θ��ӷḻ�ĵ��������򻹿���  
```
 ������.nav{
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
```����
�������Եõ���ͼ
![ˮƽ����2](https://raw.githubusercontent.com/luolala/Winter-vacation-study/master/imges/%E6%B0%B4%E5%B9%B3%E5%AF%BC%E8%88%AA2.png)
###�����˵�  
�����������ö༶�б��Լ�css����������˵�
```css
������ul{
   			margin: 0;
   			padding: 0;
   			list-style-type: none;
   			float: left;/*�պϸ���*/
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
   			left: -999em;/*���ص���Ļ��� */
   		}
   		.nav li:hover ul{
   			left: auto;/*��ʾ�����˵�*/
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
�����ּ��������ڴ�����ִ��������������IE���ϰ汾����Ч����Ϊ���ǲ�֧���ڷ�êԪ����ʹ�ã�hoverα�ࡣΪ�˽��������⣬����ʹ�ü���
JavaScript��.htc��Ϊ�ļ�����������ܡ�
###ͼ��ӳ�䡡��
���������ᵽ��ӳ�䷽���ǽ���ê���ӽ��о��Զ�λ����λ����Ӧ��ͼƬ�ϣ��γ��ȵ㡣�����ı�ʹ��һ����ĸ�����Ϊ�ı���������Ȼ�������Ǵ���Ļ����ʧ�����ְ취�о��е�̫�鷳�ˡ�����
֮ǰ��[W3shool](http://www.w3school.com.cn/tiy/t.asp?f=html_areamap)�Ͽ����ķ���������[http://www.w3school.com.cn/tags/tag_area.asp](http://www.w3school.com.cn/tags/tag_area.asp)ʵ�ֵġ��о����ַ�������
һЩ��

������


