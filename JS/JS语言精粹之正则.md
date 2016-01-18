**JS语言精粹之正则**
-------
　　今天读的是《JavaScript 语言精粹》第七章-正则，在第一小节的阅读中，注意到了两个名词：非捕获型分组和捕获型分组。
之前没有注意过，因此查阅资料学习了这两个名词。  
　　分组是将若干单位（可以是字符，正则表达式等等）组织在一起，成为一个独立的单元，该单位可以跟独立的字符一样。
捕获型分组是将分组所匹配的内容存储在某个地方，以便下次使用，以(...)表示，而非捕获型分组不捕获分组所匹配的内容，当然也
得不到匹配的结果，以(?:...)表示。由上面对两种分组不同的解释可以得到，在一些只需要分组匹配但是不需要得到各个分组匹配的结果时，利用非捕获型
分组可以节约资源，提高效率。  
　　从一个成功返回的匹配中捕获组数量总是等于原来正则表达式中捕获组的数量。举个例子来说：对于正则表达式`((cat)|dog)`,存在两组捕获数组，
若输入的是`dog`,则捕获组1是`dog`,捕获组2是空字符串。  
```
    var reg=/((cat)|dog)/;
	var str='dog';
	console.log(reg.test(str));//true;
	console.log(RegExp.$1);//dog
	console.log(RegExp.$2);
```
　　由上面的例子可以看出，利用`$`可以获得捕获组中的内容。同样的，对于文本`cat`,
```
    var reg=/((cat)|dog)/;
	var str='cat';
	console.log(reg.test(str));//true;
	console.log(RegExp.$1);//cat
	console.log(RegExp.$2);//cat
```
　　再试一下非捕获型分组，
```
    var reg=/((?:cat)|dog)/;
	var str='cat';
	console.log(reg.test(str));//true;
	console.log(RegExp.$1);//cat
	console.log(RegExp.$2);
```
　　由上面的例子可以看出，第二个分组是非捕获型分组，因此我们在利用`RegExp.$2`获取第二个分组的内容时得到内容为空。  
　　利用捕获型分组，有时可以利用其内容进行替换操作，比如在[Learn regular expressions in about 55 minutes](http://qntm.org/files/re/re.html)中提到了一个小练习
用ISO 8691格式的日期（YYYY-MM-DD）去替换美式日期（MM/DD/YY），
```
    var reg=/(\d\d)\/(\d\d)\/(\d\d)/;
	var str='03/04/05';//(2005年3月4号)
	console.log(reg.test(str));//true;
	console.log(RegExp.$1);//03
	console.log(RegExp.$2);//04
	console.log(RegExp.$3);//05
    console.log(str.replace(reg,'20$3-$1-$2'));//2005-03-04
```
　　在这篇文章中提到可以通过使用一个反斜杆和一个捕获组号来引用一个捕获组，即替换的表达式`20\3-\1-\2`,然而试了下并不能。。。。  
　　关于捕获型分组与非捕获型分组只是正则表达式中的一个知识点，其他内容也需要认真再研究，对于[Learn regular expressions in about 55 minutes](http://qntm.org/files/re/re.html)可以再阅读下。