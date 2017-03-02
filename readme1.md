观察者模式  回调对象2880 fire方法的实现原理
  堆就是队列 
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
延迟对象的作用
  初始化出发 以后不触发
    初始化不触发 以后每次经历一个事件后进行触发
    function a(){}
    function b(){}
    setTimeout(function(){$.defer.resolved()},1000)
    $.defer.done(a);
    btn.onclick=function(){$.defer.done(b)}//立即触发
    1^0=1 1^1=1

    根据大多数人的人生经验，我发现“我很迷茫”的真实意思往往是：又不想好好努力，又想继续混吃混喝，可眼看着就要撑不下去了，我该怎么办呐……

    函数return对象一定要注意
    promise不传参数则不能修改状态 因为没有修改修改状态的方法
    .when加长版延迟对象
    .fail .done链式调用只是作为add添加了而已 以后看状态不同进行调用
版本检测（css3,html5）和性能检测 .support .modernriz
  onfocus不支持冒泡   IE下onfocusin支持
  框架下没有body
  offsetWidth zoom放大倍数
  top百分比值转换为像素
  检测方式 创建元素 元素设置属性 append元素 元素属性是否符合 移除元素

data数据缓存 ＤＯＭ与对象之间互相引用就会产生内存泄露
  根据不同的参数进行不同的功能调用
  key进行元素的属性与外部对象的映射(设置对应关系后用key值返回)  get set查找对应关系都是用的key
  设置是循环设置 获取则是获取第一个

队列 存的都是函数

prop与attr的区别  prop使用点方式HTMLDOM设置的 attr则是DOM设置的 href的区别//prop找到所有的地址 attr是绝对地址
attr删不掉
  document和window对象无法使用getattribute  而打点可以
属性兼容写法
  将有问题属性放在数组中 然后将修正后的值与之对应关联 利用或操作符进行兼容性操作
  空格转布尔为真
  &&的优先级要高于或的  option与select的type的兼容处理