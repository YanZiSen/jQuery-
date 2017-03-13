
### 回调对象2880 fire方法的实现原理 观察者模式
  * **堆栈**
  <pre>
  加一个开关
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
### 延迟对象的作用
   * 初始化触发 以后不触发
   * 初始化不触发 以后每次经历一个事件后进行触发

    function a(){}
    function b(){}
    setTimeout(function(){$.defer.resolved()},1000)
    $.defer.done(a);
    btn.onclick=function(){$.defer.done(b)}//立即触发
    1^0=1 1^1=1

   根据大多数人的人生经验，我发现“我很迷茫”的真实意思往往是：又不想好好努力，又想继续混吃混喝，可眼看着就要撑不下去了，我该怎么办呐……

   * 函数return对象一定要注意 (地址的问题)
   * promise不传参数则不能修改状态 因为没有修改修改状态的方法
   * .when加长版延迟对象
   * .fail .done链式调用只是作为add添加了而已 以后看状态不同进行调用
版本检测（css3,html5）和性能检测 .support .modernriz
  onfocus不支持冒泡   IE下onfocusin支持
  框架下没有body
  offsetWidth zoom放大倍数
  top百分比值转换为像素
  检测方式 创建元素 元素设置属性 append元素 元素属性是否符合 移除元素

### data数据缓存 ＤＯＭ与对象之间互相引用就会产生内存泄露
  根据不同的参数进行不同的功能调用
  key进行元素的属性与外部对象的映射(设置对应关系后用key值返回)  get set查找对应关系都是用的key
  设置是循环设置 获取则是获取第一个

### 队列 存的都是函数
### 属性操作
    prop与attr的区别  prop使用点方式HTMLDOM设置的 attr则是DOM设置的 href的区别//prop找到所有的地址 attr是绝对地址
    attr删不掉
    document和window对象无法使用getattribute  而打点可以
#### 属性兼容写法
  * 将有问题属性放在数组中 然后将修正后的值与之对应关联 利用或操作符进行兼容性操作
   **空格转布尔为真 &&的优先级要高于||的**
  * option与select的type的兼容处理


### 事件操作
  * on one只绑定一次在on中的处理
     * on,one,off等实例方法调用add/remove add里加上数据缓存是为了使用trigger触发时方便找到fn remove里去掉数据缓存
  * $().trigger 触发 主要用于自定义事件 跟函数有区别
  * trigger建立映射关系的方法;   //不要设置dataset是自动转为字符串
  * 事件的命名空间
  * 事件缓存中的 needContect针对的伪类事件 origitype和type的区别 一个是原始的 一个是处理兼容后的
  * return false既阻止了冒泡 也阻止了默认行为(jquery中)
#### 事件兼容
  * pageY和clientY的差距 pageY是到页面的距离 clientY是到可是区的距离
  * event.which 获得鼠标或者键盘的键值 IE 8不支持 （用keyCode来做兼容）jquery一步步降级进行兼容性的处理 witch charCode keyCode
  * 用onmousedown/onmouseup来代替鼠标左中右键的不同值 另一方面也阻止了默认行为 36.html //mousedown要比click先触发
  * jquery中的event是指的自身修改的
  * special对focus,blur进行的处理
  * 给父元素绑定onmouseout和onmousemove的问题 进入子元素是触发两次  enter与leave解决 41.html special钩子的运用
    * mouseenter与mouseleave用mouseout和mouseleave解决的方法 **event.relateTarget与target的比较，再合适的情况下调用fn**
  * onbeforeunload事件 提示
  * trigger模拟冒泡操作的方法

DOM操作 *5129-6057* *42.html*
  * [^:#\.\[]除了: # . [
  ### 筛选类  参数(str/fn/s) 都调用了winnow
  * filter() not()在自身当中进行筛选 has()在子项中进行筛选
      * 调用的工具方法$.filter 分支的作用简单的加:not伪类进行控制开关 都结合运用了jquery.find进行元素查找 及sizzle;最后复杂的调用是复杂用grep进行过滤
  * index()查找元素在指定集合中的位置 $('#div1').index() $('span').index($('#span1')) $('#span').index('span')
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
  * .closest()查找满足条件的最近的祖先节点(包括自己) rneedsContext？？
  ### 遍历节点类
  parent() parents() parentsUntil();
  next() prev() nextAll() prevAll() nextUntil() prevUntil() **原生中的children只能查找一层**
  siblings();contents()查找各种类型的子节点或者跨iframe操作
   * 实现原理
      * 单独的方法在工具方法内 公共的过滤
      * 通过each对外实现接口
      * 先调用map执行各自的函数方法得到初步符合的数组
      * 如果有过滤条件的话调用filter进一步对其进行过滤
      * 对于特殊的进行去重处理 反转
  ### DOM操作
  detach,remove,empty,text,html(innerHTML不会解析script,link,style*运用的append进行的兼容*),clone(checkbox和radio复制节点时不会复制状态)
   * 阻止与恢复script的执行方法是修改type值
   * append与appendTo的区别 *针对的是后续的操作*

 ### 样式操作  **50.html** **6058-**
  * **style属性只能获取行间样式 getComputedStyle获得计算后的样式(只能获取)**
  * **style可以获得复合样式,getComputedStyle不可以**
  * class=>className float=>cssFloat
  * 返回normal的属性 font-weight(400)/letterspacing(0)
  * css的width等尺寸返回的是数值
  * IE9-不支持opacity 而getComputedStyle无法获取filter getComputedStyle.getPropertyValue('filter')获得;
  * 动态添加的元素为append前的ownerDocument不存在 getComputedStyle也将失效
  * 百分比的转换兼容 保存width width设为该值 获取该值 设置会原来的值
    <pre>
      针对$(elem).css('width',"+=100");
      var reg=/[+-]=(\d+)/;
      var ret=reg.exec(value)
      name=(ret[1] + 1)*ret[2]+parseFloat(jQuery.css(elem,name));
    </pre>
  * jquery中实现智能设置display的方法 getComputedStyle+数据缓存
      * 如果一开始是隐藏的,解决方法是动态创建在删除 body有默认值
      * iframe下的修正
  * 尺寸相关 width() innerWidth()width+padding; outerWidth()width+padding+border/width+padding+border+margin(参数为true时)*8753 94.mp4*
      * 区别width还是height的计算方式
      <pre>
       var i=name==='width'?0:1,
            gather=[left,top,right,bottom];
           for(;i<4;i+=2){
              'padding'+gather[i]
           }
      </pre>

  ### ajax操作
   * 将20%转化为+的原因 后台接收+作为空格
   * 只有表单具有elements的属性
   * #### $().load(url,\[data,fn]) $.get(url,data,fn,dataType) $.post(url,data,fn,dataType) $.ajax() $.getScript(url,data,fn,dataType)按需加载js