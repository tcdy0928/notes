## sizzle
 sizzle是选择器，JQ中集成了它


## 无new化操作
 因为打算在使用jQuery的时候不在外面new，我们使用了在jQuery函数内部new，但是出现了一个问题，递归！
 
 
 ***
 
- 问题：
    - 如何才能做到既能够在内部new，又不递归？
    - 如何才能做到在内部new还能使用jQuery实例化对象的方法？
- 回答：
    - 只要不new jQuery本身就不会递归,那么找一个炮灰来new,只要让炮灰拥有jQuery的 属性或者方法，是不是new 炮灰就等同于newjQuery
 
 
 ***



***

在低版本浏览器中undefined是可以为变量的
如果需要使用到undefined，并且undefined之前已经被赋值了
那么undefined无效。


***

## jQ的宽高
- width()
- height()
- innerWidth/innerHeight  (包含padding,不包含border)
- outerWidth/outerHeight(包含padding,包含border)
- outerWidth可以支持margin 在第二个参数上加true


## jQ的距离
- offset().left / top  : 绝对位置
- position().left / top : 相对于定位父级的距离
- scrollTop/scrollLeft 滚动的距离


## 事件
- jQ中的事件都是事件绑定，所有的事件都是基于on()
- off() 解除绑定,在哪个元素上解除就在那个元素后添加。
- jQ中的ev是二次封装的
- 要想获取真实的ev。ev.originalEvent 可以获取到原生的事件对象
- 阻止冒泡：ev.stopPropagation();
- 阻止默认行为：ev.preventDefault();
- return false;  (即可以阻止冒泡又可以阻止默认行为)




## animate()
- jQ中的运动都基于 animate()
- delay() 延迟
- 小技巧：
    如果会多次触发运动，那么在运动前加 stop(true,true) 
2个true的时候，立即完成上次一次任务，然后开始本次任务



***

jQ里如果要清除用css()加上的样式，可以使用$('#ele').attr('style','');

***