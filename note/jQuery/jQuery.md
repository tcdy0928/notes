# jQuery
jQuery是一个快速，小巧，功能丰富的JavaScript库。它使诸如HTML文档遍历和操纵，事件处理，动画和Ajax等事情变得简单得多，而且易于使用的API可以在多种浏览器中使用。结合多功能性和可扩展性，jQuery改变了数百万人写JavaScript的方式。     
**1.72兼容所有浏览器的**
**http://www.jquery123.com/**
## 注意事项
- 如果你要使用jq的方法，那么必须保证，前面那个对象是JQ对象
-  JQ对象转原生对象使用下标即可        
原生对象转JQ对象用$()包一下即可


## css():
- 一个参数
    - (1)字符串是获取
    - (2)对象（批量设置）

- 两个参数是设置


## prop():
- prop:专门用来操作表单元素属性的（比如:checked）

```
$('input[type="checkbox"]').prop('checked',false)

```


## JQ.each():
- JQ的循环,里面有个回调函数
- function (i,e){}  ,i->index  e->element


## DOM
- 第一个元素  first()
- 最后一个元素  last()
- 兄弟元素 
    - next
    - prev
    - siblings  


## JQ.index()
- 添加class
    - addClass()
- 删除class
    - removeClass()
- JQ.index(可以选填范围)
    - 找到当前元素所在的位置（在父级同级兄弟元素中的位置）




## closest():
closest会首先检查当前元素是否匹配，如果匹配则直接返回元素本身如果不匹配则向上查找父元素，一层一层往上，直到找到匹配选择器的元素。如果什么都没找到则返回一个空的jQuery对象。


## find()
获取元素的方式，会先找li再去找#ul2，那么性能会差很多
代码缓存：
  先使用find把大模块缓存起来，然后从这个代码块下去获取，节省性能
  
  
## append()
最后添加

## insertBefore()
插入什么东西.insertBefore.要插入到哪个前面

## prepend()
父级.prepend(插入的元素) -> 结果添加到第一个上

## remove()
 $(xx).remove();
 


## Object.assign()
从右往左赋值,浅拷贝

## symbol(唯一)
一个新的数据类型


## Set():
里面的内容不能有重复的
- 去重
```
let arr = ['1',2,2,3,3,4,54,32,2,3,4,6,2,1,2,1];
console.log([... new Set(arr)]);

```