jquery �������д���window�����ԭ�� �����˻ض��������� �������window���� ����ѹ��
��ִ�к�����ֹȫ����Ⱦ �����������ͻ
����undefined��Ϊ�˷�ֹundefined���ı䣬����޸�undefined��ֵ
��Ҫʡ���ڿ�ͷ���β�ķֺ�
jquery���湹�캯���е�new Ϊ�˲���jQueryǰ����new���һ�Ҫ�м̳� ����return�������new ������ִ�н����һ������,��������ʵ����ʽ����
jQuery.fn����jQuery.prototype Ϊ��ʡ���ַ�
XSS����
$().css();ʵ������
$.trim();���߷���
rootjQuery = jQuery(document);Ϊ�˷�ֹѹ��
var a=a+10//����ά�� var speed=10��a+speed;
�ϰ汾��IE�ж�undefined��typeof x.m=='undefined';
_jquery��_s�Ƿ�ֹ��ͻ�ķ��� �����ڿ�ͷ ����ͻ��undefined�������˱��
class2type �����ж�
function JQuery(){
  return new Jquery.prototype.init();
}
Jquery.prototype.init=function(){};
jQuery.prototype.css=functioin(){};
Jquery.prototype.init.prototype=jquery.prototype;//ʡ��new�ķ�ʽ
�����������ķ�ʽ��Ҫ�ֶ��޸�constructor;

jqueryʵ��ѭ���ķ�ʽ
    ������length

jquery���߷��� $.merge();�ϲ����� ������
jquery.makeArray();//������һ�� �ڶ���������lengthתΪ���� û��תΪ����
jqeuryʵ������
  .pushStack(elem) .end() ��elem��merge��ΪjQuery���� Ȼ����preJQueryָ��this endָ��ջ���µ�Ԫ��
  .first() .last() .eq() ǰ�������õĵ��������� ������������pushStack����
  .map .each
jquery�̳з��� ������д�ں���������ָ���Ǻ����ľ�̬������
$.extend() �������÷� $.extend({}) $.fn.extend({})
$.extend({},{},{},{}) ������Ķ���ϲ���ǰһ����
$.extend(true,{},{}) ���
$.globleEval()������תΪȫ�ֵ�
window.eval��eval������ �ܷ�תΪȫ�ֱ���
��ͬ�������nodeName��ʱ��Сд ��ʱ�Ǵ�д

push����ѹ�����鵫�ǲ����Ὣ�����ɢ  Ӧ��apply����
!!����Ϊ���ǽ�undefinedתΪFALSE
.grep()���˷�ת��Ƶ�����
.swap()�������displayΪnone��Ԫ�صĿ��(��noneʱ�޷����,���ǲ���ʱ����,ת�ɲ���ʱ��Ҫ��Ӱ��ҳ��Ԫ��,����position+visible)
.proxy()�İ󶨲�������ϲ�����밡

jquery��ʹ�õ��ǿ����̳� ����������ʽ�̳У�new+Function�� ԭ�ͼ̳�
���length=i ��ô��չ��ԭ���� Ϊԭ��ʵʱ��������
window.onload��Ҫ�����е�Ԫ�ض������� ��document.DOMcontentloaded�ǲ�����ͼƬflash�� ���紥��
if(document.readyState==='complete'){
  setTimeout(fn);//IE hackд��
}
  document.addEventListener()
  window.addEventListener()  ��һ������һ������ Ϊ�����е�������л���

undefined��nullû�ж�Ӧ�İ�װ����
  tostring.call() [object A*]�ȽϿ���
  class2type���Թ���
  type:function(obj){
    if(obj==null){
      return  String(obj);
    }
    return (typeof obj=='function'||typeof obj=='object')?
            class2type[tostring.call(obj)]||'object':
                typeof obj;
  }
����for in���������ԭ���� ���Լ̳в��̫��Ļ���Ӱ������
json.parse IE8���²�����
ActiveXObbject IE����
.noop�պ���������

$('<li></li>',{html:,attr:,}) ��this��for inѭ������д˷��� �����
ownerDocument��ʾ��ǰDOM�������ڵ��ĵ�����
  ѭ������
  for��var i=0;i<arr.length;i++��{
    var elem=arr[i];
    if(elem!=null)
  }
  for (var i=0,elem;elem=arr[i],elem!=null;i++){

  }
ms ǰ׺Ms css����
���� || ���������Ĳ���������
\w��ָ����������ĸ���»��� �������������� ����������ǰ������,�������ڷ�����
IE9���µ�������в������л���ǩlink script ���ã�����ȣԣ̲ͣ���ת���������ʽ�ǰ�һ��������У���ҳ
              ʹ��document.createElement()�̻��������ȷ��ʹ��HTML5��ǩ
              document.createDocumentFragment()���ĵ��д���,����û�й�����DOM����
support���ܼ��Ȱ汾���Ҫ�� �汾���汾���µ����Ͽ�