
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
     * on,one,off��ʵ����������add/remove add��������ݻ�����Ϊ��ʹ��trigger����ʱ�����ҵ�fn remove��ȥ�����ݻ���
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
  * ����Ԫ�ذ�onmouseout��onmousemove������ ������Ԫ���Ǵ�������  enter��leave��� 41.html special���ӵ�����
    * mouseenter��mouseleave��mouseout��mouseleave����ķ��� **event.relateTarget��target�ıȽϣ��ٺ��ʵ�����µ���fn**
  * onbeforeunload�¼� ��ʾ
  * triggerģ��ð�ݲ����ķ���

DOM���� *5129-6057* *42.html*
  * [^:#\.\[]����: # . [
  ### ɸѡ��  ����(str/fn/s) ��������winnow
  * filter() not()�������н���ɸѡ has()�������н���ɸѡ
      * ���õĹ��߷���$.filter ��֧�����ü򵥵ļ�:notα����п��ƿ��� �����������jquery.find����Ԫ�ز��� ��sizzle;����ӵĵ����Ǹ�����grep���й���
  * index()����Ԫ����ָ�������е�λ�� $('#div1').index() $('span').index($('#span1')) $('#span').index('span')
    &nbsp; <pre>
    index:function (elem){
      if (!elem){
        return (this\[0]\&&this\[0].parentNode)?this.first().prevAll().length:-1;
      }
      if(typeof elem==='string'){
        return [].indexOf.call(jQuery(elem),this\[0]);
      }
      <--return elem.jquery?[].indexOf.call(elem,this\[0]):elem;-->
      return [].indexOf.call(this,elem.jquery?elem\[0]:elem);
    }
    </pre>
  * .closest()����������������������Ƚڵ�(�����Լ�) rneedsContext����
  ### �����ڵ���
  parent() parents() parentsUntil();
  next() prev() nextAll() prevAll() nextUntil() prevUntil() **ԭ���е�childrenֻ�ܲ���һ��**
  siblings();contents()���Ҹ������͵��ӽڵ���߿�iframe����
   * ʵ��ԭ��
      * �����ķ����ڹ��߷����� �����Ĺ���
      * ͨ��each����ʵ�ֽӿ�
      * �ȵ���mapִ�и��Եĺ��������õ��������ϵ�����
      * ����й��������Ļ�����filter��һ��������й���
      * ��������Ľ���ȥ�ش��� ��ת
  ### DOM����
  detach,remove,empty,text,html(innerHTML�������script,link,style*���õ�append���еļ���*),clone(checkbox��radio���ƽڵ�ʱ���Ḵ��״̬)
   * ��ֹ��ָ�script��ִ�з������޸�typeֵ
   * append��appendTo������ *��Ե��Ǻ����Ĳ���*

 ### ��ʽ����  **50.html** **6058-**
  * **style����ֻ�ܻ�ȡ�м���ʽ getComputedStyle��ü�������ʽ(ֻ�ܻ�ȡ)**
  * **style���Ի�ø�����ʽ,getComputedStyle������**
  * class=>className float=>cssFloat
  * ����normal������ font-weight(400)/letterspacing(0)
  * css��width�ȳߴ緵�ص�����ֵ
  * IE9-��֧��opacity ��getComputedStyle�޷���ȡfilter getComputedStyle.getPropertyValue('filter')���;
  * ��̬��ӵ�Ԫ��Ϊappendǰ��ownerDocument������ getComputedStyleҲ��ʧЧ
  * �ٷֱȵ�ת������ ����width width��Ϊ��ֵ ��ȡ��ֵ ���û�ԭ����ֵ
    <pre>
      ���$(elem).css('width',"+=100");
      var reg=/[+-]=(\d+)/;
      var ret=reg.exec(value)
      name=(ret[1] + 1)*ret[2]+parseFloat(jQuery.css(elem,name));
    </pre>
  * jquery��ʵ����������display�ķ��� getComputedStyle+���ݻ���
      * ���һ��ʼ�����ص�,��������Ƕ�̬������ɾ�� body��Ĭ��ֵ
      * iframe�µ�����
  * �ߴ���� width() innerWidth()width+padding; outerWidth()width+padding+border/width+padding+border+margin(����Ϊtrueʱ)*8753 94.mp4*
      * ����width����height�ļ��㷽ʽ
      <pre>
       var i=name==='width'?0:1,
            gather=[left,top,right,bottom];
           for(;i<4;i+=2){
              'padding'+gather[i]
           }
      </pre>

  ### ajax����
   * ��20%ת��Ϊ+��ԭ�� ��̨����+��Ϊ�ո�
   * ֻ�б�����elements������
   * #### $().load(url,\[data,fn]) $.get(url,data,fn,dataType) $.post(url,data,fn,dataType) $.ajax() $.getScript(url,data,fn,dataType)�������js