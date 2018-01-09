# 第一天
1. 字符串的trim方法

---

    用来去除字符串两端的空格，不能去掉内容中间的空格

2. 字符串

---

    encodeURI   编码    ==> 将内容编码为assii码
    decodeURI   解码    ==> 将assii码转为原来的字符
    
3. \u4e00 - \u9fs5

---

    汉字所属于的assii码范围
    
4. jQuery的使用方法

---

    1.引包  ==> 引入JQuery文件
    2.入口函数
        //第一种
        $(document).ready(function(){
            $('选择器').事件(function(){
                $('选择器').方法
            })
        })
        //第二种
        $(function(){
            $('选择器').事件(function(){
                $('选择器').方法
            })
        })

5.  常用方法

---

    text('内容')        //添加内容，相当于innerText
    show(1000)          //显示出来，括号内为时间，相当于定时器
    hide()              //隐藏
    css('属性','值')     //用来操作样式
    children()          //获取父元素中的子元素  相当于子代选择器
    find()              //相当于后代选择器
    siblings()          //获取兄弟元素
    index()             //获取索引号
    next()              //获取后面一个兄弟元素
    prev()              //获取前面一个兄弟元素
    parent()            //获取当前元素的父元素

6. DOM对象转化jQuery对象

---

    btn ==> $(btn)

7. jQuery对象转化DOM对象

---

    btn ==> $('btn')[0] / $('btn').get(0)

8. jQuery选择器

---

    -     简单选择器
            id选择器    ==> $('#id')
            类选择器    ==> $('.class')
            标签选择器  ==> $('p')
            并集选择器  ==> $('p , li, a')  //中间的空格可有可无
            交集选择器  ==> $('li.class')   //同时满足两个条件li里面含有class类的标签
            *通配符选择器   ==> &('*')
            
    -     层级选择器
            子代选择器  ==> $('div>span')
            后代选择器  ==> $('div span')
            
    -     过滤选择器
            奇数选择器  ==> :odd    $('li:odd')
            偶数选择器  ==> :even   $('li:even')
            相等选择器  ==> :eq(索引号) $('li:eq(5)')   //把第五个li选择出来
            小于选择器  ==> :lt(索引号) $('li:lt(5)')   //把小于5的li选择
            大于选择器  ==> :gt(索引号) $('li:gt(5)')   //把大于5的li选择


# 第二天

1. css()方法

---

    设置样式
        A. $('div').css('属性名'，值)
        B. $('div').css({json})
    读取样式
        console.log($('div').css('属性名'))
        外链样式也可以获取到
        获取的是字符串类型
    
2. 类操作   ==> 注意类名不用加.

---

    添加类
        $('div').addClass('类名')；
    移除类
        $('div').removeClass('类名')；
    判断有没有类    ==> 返回布尔值
        console.log($('div').hasClass('类名'))；
    切换类
        $('div').toggleClass('类名')

3. 动画

---

    show()  展示动画
        -   不传参数，没有动画效果  //show()
        -   传入数值，数值是毫秒数，表示动画执行的时间长度  //show(5000)
        -   传入字符串，只能是内置的几个 fast/slow/normal
        -   传入时间和回调函数表示该动画执行完成后再立马执行的操作  //show(2000,function)
    hide()  隐藏动画
        -   不传参数，没有动画效果  //hide()
        -   传入数值，数值是毫秒数，表示动画执行的时间长度  //hide(5000)
        -   传入字符串，只能是内置的几个 fast/slow/normal
        -   传入时间和回调函数表示该动画执行完成后再立马执行的操作  //hide(2000,function)
        
    Toggle()    切换
        -   让一组动画函数自动切换
        -   例：
                &('div').showToggle();  //在隐藏和显示之间转换
                
    slideDown() 滑入
        -   操作方式同上
        -   改变的是元素高度
        -   有Toggle模式
    slideUp() 滑入
        -   操作方式同上
        -   改变的是元素高度
        -   所有的动画函数都受定位影响
        
    fadeIn()    淡入
        -   操作方式同上
        -   改变的是元素不透明度
        -   有Toggle模式
    fadeOut()    淡出
        -   操作方式同上
    fadeTo()    改变不透明度到某个值
        -   $('div').fadeTo(3000,0.5)   //第一个参数表示动画执行时长，第二个参数表示不透明度的目标值
        
    animate()   自定义动画
        $('div').animate({json},5000,function) 
        //第一个参数表示要改变的属性
        //第二个参数表示动画执行所需要的总时间
        //第三个参数表示动画执行完成后再执行的动作
        
4.  hover()方法

---

    作用：相当于css中的：hover样式
    内部是通过mouseenter()和mouseleave()方法来实现的
    例:
        $('div').hover(function1,function2) //第一个函数表示鼠标进入，第二个表示鼠标离开

5.  stop()方法  ==> 停止动画

---

    -   使用方式
            先使用stop()方法，再执行动画
            例：
                $('div').stop().slideDown(1000).slideUp(1000);
    -   参数
        stop([cearQueue][,jumpToEnd])
            第一个参数表示是否清空队列
            第二个参数表示是否立即结束，并达到当前动画的目标状态

6.  创建元素

---

    //第一种    $()方法
        $('标签').appendTo('标签')；
        appendTo('标签')方法能接受选择器
        
    //第二种    append()    ==> 将后面的元素添加到前面的标签中来
        不接受选择器，相当于innerText
        可接受jQuery对象
        在最后一个子元素后面追加元素  
        
    //第三种    prepend()   ==> 插入元素
        在第一个子元素前面插入元素
        同样有 prependTo()方法
        
    //第四种    .befor/.after
        在元素的前后添加元素
        
    //第五种  .html()  
        传入了参数，表示设置内容
            设置内容时，只能是文本，不能是标签
        没有参数，表示获取内容
            只能获取第一个匹配的内容
            
7.  :slected 选择方法

---

    用法：
        -   $('#sel > opation:selected')
        -   $('sel').children(:selected)
        

# 第三天

1. p标签里面不能包括块级元素

2. 清空元素

---

    -   empty()     清空内容及子元素
    -   $('div').html('')
    -   remove()    //会移除自己

3. 克隆元素 clone()

---

    作用：复制一个当前jQuery对象
    使用：$('a').clone().html('content').appendTo('div')
    特点：不传参数也可以深度复制，**传入参数会把当前元素的事件也复制进来**

4. val()   用来获取或设置表单元素的值

---

    用法与html()完全相同
    括号内没有参数表示读取，有参数表示设置

5. text()   设置或读取文本内容

---

    与html()方法的区别是只针对文本，不会设置或获取标签，与DOM的innerText相同
    用法与val()和html()相同

6. attr()    属性操作 

---

    -   attr()既能读取也可以设置，用法与css()相同
    -   注意：checked / selected / disabled 这几个属性不能通过attr()来操作
    -   prop()的用法与attr()相同，且可以设置上面几个特殊属性
    -   attr()能获取自定义属性
    -   prop()不能获取自定义属性

7. :checkbox 获取所有的复选框

8. :checked 获取到所有被选中的input标签

9. 其他需要了解的属性

---

    -   width() 返回的是数值，用法同css()   //有参数的时候是设置宽度
    -   height() 返回的是数值，用法同css()  //有参数的时候是设置高度
    -   offset() 获取当前元素相对文档的左侧和上侧的距离，返回值是对象，对象中有两个属性，TOP和LEFT
    -   offsetParent() 返回最近的有定位的祖先元素
    -   position()  获取相对于有定位父元素的偏移，只能读取，不能设置，返回值是对象，对象中有，top和left
    -   scrollLeft() 既能读取卷去的宽度，也能设置
    -   scrollTOP() 既能读取卷去的高度，也能设置

10. bind()  绑定事件    (了解)

---

    $('div').bind('click',function) //绑定单个
    $('div').bind('click mouseenter',function) //绑定多个
    $('div').bind('click.test1',function) //绑定命名空间
    和传统方法一样不支持绑定动态创建的元素的事件绑定

11. unbind() 解绑事件   (了解)

---

    -   普通解绑        $('div').unbind('click')
    -   解绑命名空间    $('div').unbind('.test1')

12. delegate()   绑定事件   (了解)

---

    支持动态创建的元素绑定事件
    $('ul').delegate('li','click',function) ==> 让li元素触发事件
    只有点击li元素才能触发该事件
    里面的元素一定要是外面元素的子元素
    
13. on() 绑定事件   （重点）

---

    jQuery中不管是使用哪种方式绑定事件，内部都是通过on()方法来实现
    兼容zepto
    支持动态创建的元素绑定事件
    on()方法是在jQuery 1.7版本后出现的
    用法：
        -   $('div').on('click',function)   //普通绑定  （常用）
        -   $('div').on('click mouseenter',function)    //绑定多个事件
        -   $('div').on({‘click':function, 'mouseenter':function})    //绑定多个事件,并有多个方式
        -   $('div').on('click','p',function)   //支持动态创建出来的元素的绑定事件（p是动态创建的） （常用）
    
# 第四天

1. 解绑事件（on方式绑定的事件）

---

    例：
        <div><input type="button" value="按钮"></div>
    -   $('input').off('click')   //移除元素的单个事件
    -   $('input').off()  //移除元素所有的事件
    -   $('div').off('click')   //解除代理绑定的事件，通过父元素（同时解除了父元素本身的事件）
    -   $('div').off('click'，'**')     //通过父元素解除代理绑定的事件，且不接触父元素本身的事件

2. 其他解绑事件 

---

    -   通过bind()方式绑定的时间，需要通过unbind()解绑
    -   delegate()方式绑定的事件，需要通过undelegate()解绑
    
3. 触发事件

---

    -   例：
        $('#btn1').on('click',function(){
            console.log('xxx')
        });
        $('#btn2').on('click',function(){
            $('#btn1').trigger('click')              //方式一
            $('#btn1').triggerHandler('click')       //方式二
        });
    -   trigger()   //既能够触发事件调用程序，也能够触发浏览器默认行为
    -   triggerHandler()    //仅仅调用事件处理程序，不会触发浏览器默认行为
    -   浏览器默认行为：例如文本框的获取焦点就是浏览器的默认行为
    
4. 事件对象

---

    -   不存在兼容性问题，所有浏览器的对象属性都是相同的
    -   阻止浏览器默认行为
            e.preventDefault()  //原生JS也支持这个方法，阻止浏览器默认行为
            e.stopPropagation() //阻止冒泡
            return false;       //既阻止了浏览器的默认行为，也阻止事件冒泡
    
5. jQuery的特点

---

    -   链式编程
            只能在设置操作的时候进行，如果进行的是读取操作，则不能用链式编程
    -   隐式迭代
            jQuery内部会自动获取元素并遍历
            
6. end()方法    ==> 链恢复

---

    -   链破坏
            prevAll() / prev() / next() / nextAll() / children() / find() / eq()    都会破化链式编程的链
    -   链恢复
            end() 方法可以恢复到链破坏前的一个状态

7. jQuery 插件

---

    -   使用步骤
            1.引入jQuery文件
            2.引入插件js文件
            3.引入插件的样式文件
            4.调用插件提供的方法
    -   
















