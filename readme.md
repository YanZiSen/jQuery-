* jquery �������д���window�����ԭ�� �����˻ض��������� �������window���� ����ѹ����
* ��ִ�к�����ֹȫ����Ⱦ �����������ͻ��
* ����undefined��Ϊ�˷�ֹundefined���ı䣬����޸�undefined��ֵ��
* ��Ҫʡ����ִ�к����ڿ�ͷ���β�ķֺţ���ֹǰ����ߺ����δ֪��Ϊ�������ö�����;
* jquery���湹�캯���е�new Ϊ�˲���jQueryǰ����new���һ�Ҫ�м̳� ����return�������new ������ִ�н����һ������,��������ʵ����ʽ���ã�
* jQuery.fn����jQuery.prototype Ϊ��ʡ���ַ���
<pre>
  function JQuery(){
    return new Jquery.prototype.init();
  }
  Jquery.prototype.init=function(){};
  jQuery.prototype.css=functioin(){};
  Jquery.prototype.init.prototype=jquery.prototype;//ʡ��new�ķ�ʽ
  �����������ķ�ʽ��дԭ�ͺ������Ҫ�õ�constauctor��Ҫ�ֶ��޸�constructor,����ΪObject;
</pre>
* XSS����??��
* rootjQuery = jQuery(document);Ϊ�˸��ý���ѹ����
* var a=a+10//����ά�� var speed=10��a+speed;
* �ϰ汾��IE�ж�undefined��typeof obj.attr=='undefined';
* _jquery��_s��ʵ�ַ�ֹ��ͻ������ �����ڿ�ͷ ����ͻ��undefined�������˱�ǣ�
* class2type �����жϣ�
<pre>
    Object.prototype.tostring.call() [object A*]�ȽϿ��� class2type���Թ���
    type:function(obj){
      if(obj==null){
        return  String(obj);
      }
      return (typeof obj=='function'||typeof obj=='object')?
              class2type[{}.tostring.call(obj)]||'object':
                  typeof obj;
    }
</pre>
* α����jqueryʵ��ѭ���ķ�ʽ��
    **������length**

+ $().css();ʵ��������
  $.trim();���߷�����
  * jquery���߷��� $.merge();�ϲ����� �����飻
  * jquery.makeArray();//������һ�� �ڶ���������lengthתΪ���� û��תΪ���飻
  * jqeuryʵ��������
    * .pushStack(elem) .end() ��elem��merge��ΪjQuery���� Ȼ����preJQueryָ��this endָ��ջ���µ�Ԫ��
      .first() .last() .eq() ǰ�������õĵ��������� ������������pushStack����
      .map .each
* **jquery��ʹ�õ��ǿ����̳� ����������ʽ�̳У�new+Function�� ԭ�ͼ̳У�**
* jquery�̳з��� ������д�ں���������ָ���Ǻ����ľ�̬��������*285~347*
    * $.extend() �������÷� $.extend({}) $.fn.extend({})
    * $.extend({},{},{},{}) ������Ķ���ϲ���ǰһ����
    * $.extend(true,{},{}) ���
    * ���length=i ��ô��չ��ԭ���� Ϊԭ��ʵʱ�������ƣ�

* $.globleEval()������תΪȫ�ֵ�
* window.eval��eval������ �ܷ�תΪȫ�ֱ�����

* push����ѹ�����鵫�ǲ����Ὣ�����ɢ  Ӧ��apply���ԣ�
**!!����Ϊ���ǽ�undefinedתΪFALSE��**
* **.grep()���˷�ת��Ƶ����**
* .swap()�������displayΪnone��Ԫ�صĿ��(��noneʱ�޷����,���ǲ���ʱ����,ת�ɲ���ʱ��Ҫ��Ӱ��ҳ��Ԫ��,����position+visible)��
* .proxy()�İ󶨲�������ϲ�����밡��

* ready()��ʵ��
* **window.onload��Ҫ�����е�Ԫ�ض������� ��document.DOMcontentloaded�ǲ�����ͼƬflash�� ���紥����**
<pre>
if(document.readyState==='complete'){
  setTimeout(fn);//IE hackд�� IE��û������ʱ�ͻᴥ��
}
</pre>
  document.addEventListener()
  window.addEventListener()  ��һ������һ������ Ϊ�����е�������л���

*   undefined��nullû�ж�Ӧ�İ�װ����ʹ��!!������

* ����for in���������ԭ���� ���Լ̳в��̫��Ļ���Ӱ�����ܣ�

* .noop�պ��������ã�

*  $('<li></li>',{html:,attr:,}) ��this��for inѭ������д˷��� ����ã�
*  ownerDocument��ʾ��ǰDOM�������ڵ��ĵ�����
<pre>
    ѭ������
    for��var i=0;i<arr.length;i++��{
      var elem=arr[i];
      if(elem!=null)
    }
    for (var i=0,elem;elem=arr[i],elem!=null;i++){
    }
</pre>
* ����
  * ms ǰ׺Ҫ��ΪMs css���ԣ�
  * ���� || ���������Ĳ��������⣻
  * תСд������ ��ͬ�������nodeName��ʱ��Сд ��ʱ�Ǵ�д��
  * **\w��ָ����������ĸ���»��� �������������� ����������ǰ������,�������ڷ�����**��
  * IE9���µ�������в������л���ǩlink script ����innerHTML����ת���������ʽ�ǰ�һ��div��p51ҳ
                ʹ��document.createElement()�̻��������ȷ��ʹ��HTML5��ǩ
                document.createDocumentFragment()���ĵ��д���,����û�й�����DOM����
  * json.parse IE8���²����ݣ�
     ActiveXObbject IE���ݣ�
  * support���ܼ��Ȱ汾���Ҫ�� �汾���汾���µ����Ͽ�