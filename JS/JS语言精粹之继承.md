**JS���Ծ���֮�̳�**
------
������JavaScript���Ծ��⡷�������ǽ��̳еģ��ڵ�һ�ں͵������ᵽ��α���ԭ��,α��ʵ�ּ̳еķ�ʽΪ  
```
var Mammal=function(name){
 this.name=name;
};

Mammal.prototype.get_name=function(){
  return this.name;
};
Mammal.prototype.says=function(){
return this.saying||'';
};
var Cat=function(name){
 this.name=name;
 this.saying='meow';
};
Cat.prototype=new Mammal();
```
�����������ơ��ࡱ�Ĺ�����������û��˽�л��������е����Զ��ǹ����ģ����޷�����super(����)�����⣬ʹ�ù�����������
��һ������Σ���ǣ�����ڵ��ù���������ʱ��������ǰ�����newǰ׺����ôthis�����ᱻ�󶨵�һ���¶����ϣ����ǻᱻ�󶨵�ȫ�ֶ����ϣ�
���Բ���û�������¶��󣬷������ƻ�ȫ�ֱ�����  
�����ڵ������ᵽ��ԭ�ͼ̳У�����Ҫ����һ���ɶ���Ϊ������һ���¶���̳�һ���ɶ�������ԡ������ڵ����������Object.beget()��������������ʵ����  
```
  if(typeof Object.beget!=='function'){
      Object.beget=function(o){
      var F=function(){};
      F.prototype=o;
      return new F();
  }
  }
```
�������beget��������һ��ʹ��ԭ������Ϊ��ԭ�͵��¶�����ECMAScript5�е�Object.create()Ӧ�����������������ͬ���ڸ̵߳������У�ԭ�ͼ̳�ֱ���õ���Object.create();
```
var myMamml={
name:'Herb the Mammal',
get_name:function(){
 return this.name;
},
says:function(){
return this.saying||'';
 }
};
var myCat=Object.beget(myMammal);
```
�����������ϼ̳з�ʽû�а취������˽������ڵ��Ľ�����ģ��ģʽ��������һ�ּ̳з�ʽ��  
������������������α����ģ��
```
var constructor=function(spec,my){
    var that,������˽��ʵ��������
    my=my||{};
    
    �ѹ���ı����ͺ�����ӵ�my��
    
    that=һ���¶���
    
    ��Ӹ�that����Ȩ����
    
    return that��
}
```
������spec ���������������Ҫ����һ����������������Ϣ�������ݿ��ܻᱻ���Ƶ�˽�б����У�
���߱����������ı䡣���߷�����������Ҫ��ʱ�����spec����Ϣ������һ���¶��󲢸�ֵ��that,�кܶ෽ʽ���Թ���һ���¶���
����ʹ�ö���������������ʹ��new ���������һ��α�๹���������԰�ԭ�Ͷ�����ʹ��Object.beget����������
���Ե�����һ���������Ĺ�������������һ��spec�����my����my�������������Ĺ���������ŵ�my�е����ϡ��������������ܻ�
���Լ��Ŀɷ���ĳ�Ա�Ž�my�����У��Ա㹹����������������  
����������������that,������ɸö���ӿڵ���Ȩ���������Է���һ���º�����Ϊthat�ĳ�Ա�������߸��Ӱ�ȫ�ؽ���������Ϊ˽�з�����
Ȼ���ٽ����Ƿ����that��
```
var methodical=function(){
...
};
that.methodical=methodical;
```
��������������methodical�ĺô��ǣ��������������Ҫ����methodical�����ǿ���ֱ�ӵ���methodical����������that��methodical()�������ʵ�����ƻ���
�۸ģ�����that��methodical���滻���ˣ�����methodical�ķ�����ͬ��������������������˽�е�methodical���ܸ�ʵ���޸ĵ�Ӱ�졣������ģʽ�кܴ������ԣ��䲻������α��ģʽ������Ҫ�ܶ�
�������ܹ��õ����õķ�װ����Ϣ���أ��Լ����ʸ��෽����������
����