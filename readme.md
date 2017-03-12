* jquery 构造器中传入window对象的原因 不用退回顶级作用域 更快访问window对象 代码压缩；
* 自执行函数防止全局污染 不与其他库冲突；
* 传入undefined是为了防止undefined被改变，外界修改undefined的值；
* 不要省略自执行函数在开头与结尾的分号；防止前面或者后面的未知作为函数调用而报错;
* jquery后面构造函数中的new 为了不让jQuery前面有new并且还要有继承 所以return后面加了new 函数的执行结果是一个对象,侧面曲折实现链式调用；
* jQuery.fn就是jQuery.prototype 为了省略字符；
<pre>
  function JQuery(){
    return new Jquery.prototype.init();
  }
  Jquery.prototype.init=function(){};
  jQuery.prototype.css=functioin(){};
  Jquery.prototype.init.prototype=jquery.prototype;//省略new的方式
  对象字面量的方式重写原型后如果需要用到constauctor需要手动修复constructor,否则为Object;
</pre>
* XSS攻击??；
* rootjQuery = jQuery(document);为了更好进行压缩；
* var a=a+10//不好维护 var speed=10；a+speed;
* 老版本的IE判断undefined用typeof obj.attr=='undefined';
* _jquery和_s是实现防止冲突的作用 定义在开头 不冲突是undefined等于做了标记；
* class2type 类型判断；
<pre>
    Object.prototype.tostring.call() [object A*]比较靠谱 class2type属性挂载
    type:function(obj){
      if(obj==null){
        return  String(obj);
      }
      return (typeof obj=='function'||typeof obj=='object')?
              class2type[{}.tostring.call(obj)]||'object':
                  typeof obj;
    }
</pre>
* 伪数组jquery实现循环的方式；
    **加上了length**

+ $().css();实例方法；
  $.trim();工具方法；
  * jquery工具方法 $.merge();合并数组 类数组；
  * jquery.makeArray();//两餐与一餐 第二个参数有length转为对象 没有转为数组；
  * jqeury实例方法；
    * .pushStack(elem) .end() 将elem用merge变为jQuery对象 然后用preJQuery指向this end指回栈底下的元素
      .first() .last() .eq() 前两个调用的第三个方法 第三个调用了pushStack方法
      .map .each
* **jquery中使用的是拷贝继承 其他还有类式继承（new+Function） 原型继承；**
* jquery继承方法 （方法写在函数后面则指的是函数的静态方法）；*285~347*
    * $.extend() 的三种用法 $.extend({}) $.fn.extend({})
    * $.extend({},{},{},{}) 将后面的对象合并到前一个上
    * $.extend(true,{},{}) 深考备
    * 如果length=i 那么扩展到原型上 为原型实时拷贝复制；

* $.globleEval()将变量转为全局的
* window.eval与eval的区别 能否转为全局变量；

* push可以压入数组但是并不会将数组打散  应用apply可以；
**!!两个为的是将undefined转为FALSE；**
* **.grep()过滤反转设计的巧妙；**
* .swap()怎样获得display为none的元素的宽度(在none时无法获得,但是不是时可以,转成不是时又要不影响页面元素,所以position+visible)；
* .proxy()的绑定参数传入合并真的秒啊；

* ready()的实现
* **window.onload是要等所有的元素都加载完 而document.DOMcontentloaded是不包含图片flash的 较早触发；**
<pre>
if(document.readyState==='complete'){
  setTimeout(fn);//IE hack写法 IE在没加载完时就会触发
}
</pre>
  document.addEventListener()
  window.addEventListener()  哪一个快哪一个加载 为的是有的浏览器有缓存

*   undefined和null没有对应的包装对象；使用!!的意义

* 由于for in会遍历整个原型链 所以继承层次太深的话会影响性能；

* .noop空函数的作用；

*  $('<li></li>',{html:,attr:,}) 在this做for in循环如果有此方法 则调用；
*  ownerDocument表示当前DOM对象所在的文档对象
<pre>
    循环数组
    for（var i=0;i<arr.length;i++）{
      var elem=arr[i];
      if(elem!=null)
    }
    for (var i=0,elem;elem=arr[i],elem!=null;i++){
    }
</pre>
* 兼容
  * ms 前缀要改为Ms css属性；
  * 利用 || 修正函数的参数的问题；
  * 转小写的作用 不同浏览器下nodeName有时是小写 有时是大写；
  * **\w中指的是数字字母和下划线 不包括其他符号 （？！）反前向声明,不包含在分组中**；
  * IE9以下的浏览器中不能序列化标签link script 及用innerHTML不能转化　解决方式是包一层div　p51页
                使用document.createElement()教会浏览器正确的使用HTML5标签
                document.createDocumentFragment()在文档中存在,并且没有挂载在DOM树上
  * json.parse IE8以下不兼容；
     ActiveXObbject IE兼容；
  * support功能检测比版本检测要好 版本检测版本更新迭代较快