# 本地存储
- *** 如果要存储对象类型的数据，那么浏览器默认会调用toSting
        [object Object];
- 所以要把对象转成字符串：
            JSON.stringify();

***

**注意：**    
    对象 + 字符串 会调用toSting:
```
var o = {"name":"mazhi"}
o + ''
"[object Object]"

```

***



## localStorage
- 前端技术
- 作用：本地存储
- 据说每个域名有5M
- 生命周期：    
        只要不清，永远在。
- 设置、获取、移除和清空
    - localStorage.setItem();
    - localStorage.getItem();
    - localStorage.removeItem();
    - localStorage.clear(); //清空



## 本地存储事件
- onstorage 
    - 本域名、本浏览器，当兄弟页面操作了本地数据的时候触发。