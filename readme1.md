
### �ص�����2880 fire������ʵ��ԭ�� �۲���ģʽ
  * **��ջ**
  <pre>
  ��һ������
  var status=true;
  var a=function(){
    alert(1);
    if(status){
      fire();
      status=false;
    }
  }
  var b=function(){
    alert(2);
  }
  $.add(a);
  $.add(b);
  $.fire();
  </pre>
### �ӳٶ��������
   * ��ʼ������ �Ժ󲻴���
   * ��ʼ�������� �Ժ�ÿ�ξ���һ���¼�����д���

    function a(){}
    function b(){}
    setTimeout(function(){$.defer.resolved()},1000)
    $.defer.done(a);
    btn.onclick=function(){$.defer.done(b)}//��������
    1^0=1 1^1=1

   ���ݴ�����˵��������飬�ҷ��֡��Һ���ã������ʵ��˼�����ǣ��ֲ���ú�Ŭ�������������Ի�ȣ����ۿ��ž�Ҫ�Ų���ȥ�ˣ��Ҹ���ô���š���

   * ����return����һ��Ҫע�� (��ַ������)
   * promise�������������޸�״̬ ��Ϊû���޸��޸�״̬�ķ���
   * .when�ӳ����ӳٶ���
   * .fail .done��ʽ����ֻ����Ϊadd����˶��� �Ժ�״̬��ͬ���е���
�汾��⣨css3,html5�������ܼ�� .support .modernriz
  onfocus��֧��ð��   IE��onfocusin֧��
  �����û��body
  offsetWidth zoom�Ŵ���
  top�ٷֱ�ֵת��Ϊ����
  ��ⷽʽ ����Ԫ�� Ԫ���������� appendԪ�� Ԫ�������Ƿ���� �Ƴ�Ԫ��

### data���ݻ��� �ģϣ������֮�以�����þͻ�����ڴ�й¶
  ���ݲ�ͬ�Ĳ������в�ͬ�Ĺ��ܵ���
  key����Ԫ�ص��������ⲿ�����ӳ��(���ö�Ӧ��ϵ����keyֵ����)  get set���Ҷ�Ӧ��ϵ�����õ�key
  ������ѭ������ ��ȡ���ǻ�ȡ��һ��

### ���� ��Ķ��Ǻ���
### ���Բ���
    prop��attr������  propʹ�õ㷽ʽHTMLDOM���õ� attr����DOM���õ� href������//prop�ҵ����еĵ�ַ attr�Ǿ��Ե�ַ
    attrɾ����
    document��window�����޷�ʹ��getattribute  ��������
#### ���Լ���д��
  * �����������Է��������� Ȼ���������ֵ��֮��Ӧ���� ���û���������м����Բ���
   **�ո�ת����Ϊ�� &&�����ȼ�Ҫ����||��**
  * option��select��type�ļ��ݴ���


### �¼�����
  * on oneֻ��һ����on�еĴ���
  * $().trigger ���� ��Ҫ�����Զ����¼� ������������
  * trigger����ӳ���ϵ�ķ���;   //��Ҫ����dataset���Զ�תΪ�ַ���
  * �¼��������ռ�
  * �¼������е� needContect��Ե�α���¼� origitype��type������ һ����ԭʼ�� һ���Ǵ�����ݺ��
  * return false����ֹ��ð�� Ҳ��ֹ��Ĭ����Ϊ(jquery��)
#### �¼�����
  * pageY��clientY�Ĳ�� pageY�ǵ�ҳ��ľ��� clientY�ǵ��������ľ���
  * event.which ��������߼��̵ļ�ֵ IE 8��֧�� ����keyCode�������ݣ�jqueryһ�����������м����ԵĴ��� witch charCode keyCode
  * ��onmousedown/onmouseup��������������Ҽ��Ĳ�ֵͬ ��һ����Ҳ��ֹ��Ĭ����Ϊ 36.html //mousedownҪ��click�ȴ���
  * jquery�е�event��ָ�������޸ĵ�
  * special��focus,blur���еĴ���
  * ����Ԫ�ذ�onmouseout��onmousemove������ ������Ԫ���Ǵ�������  enter��leave��� 41.html
  * onbeforeunload�¼� ��ʾ
  * triggerģ��ð�ݲ����ķ���

DOM����
  * [^:#\.\[]����: # . [
  * filter() not()�������н���ɸѡ has()�������н���ɸѡ