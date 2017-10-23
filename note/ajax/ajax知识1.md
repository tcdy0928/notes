# AJAX
### AJAX的全名：
Asynchronous JavaScript and XML（异步JavaScript和XML)

-  当下的数据格式不再只有XML了，还有JSON
-  后端吐的所有的数据都是字符串。
-  功能：前后端的数据交互的
-  优点：    
    可以提高系统性能，优化用户界面，基本不跳转
- 安装集成环境:    
    后端的文件必须运行在服务器上，***文件夹必须不能是中文，尽量文件名也英文。


***
### ajax谨记三点
- url是什么？
- 要给后端传什么？
- 成功了以后数据长什么样子？

***
###  ajax的交互模型（原理）
- 创建一个ajax对象
```
var ajax = new XMLHttpRequest;
```
- 填写地址
```
ajax.open('get','php/get.php?user='+userId.value,true);
```
- 发送给服务器
```
ajax.send();
```
- 等待
```
ajax.onload
```
- 通话
```
ajax.responseText
```

***

### ajax_post
```
var ajax = new XMLHttpRequest;
```
- 填写地址
```
ajax.open('get','php/get.php',true);
```
-  在send前加请求头
```
ajax.setRequestHeader('Content-Type','application/x-www-form-urlencoded');
```
- 发送给服务器
```
ajax.send('user='+userId.value);
```
- 等待
```
ajax.onload
```
- 通话
```
ajax.responseText
```

***

### ajax_get和post的区别
- get方式（安全性不是太高的，体积较小的）
    -  通过地址栏进行数据的传输
    -  相对不安全
    -  体积较小，具体能传输多少，跟浏览器限制有关系
    -  在写中文的时候，IE下会把中文转成URI编码，会引起报错。
    -  通过encodeURI(转一下);
- post方式（跟用户信息相关的、较大体积的）
    - 服务器进行传输(拼接的字段要在send中)
    - 理论上来说是没有大小限制的（后端会做限制）
    - 相对就安全一些
    - 在send前加请求头


***

### URI码
- 码转中文    
   decodeURI()
- 把中文转成URI码     
    encodeURI()      
比如：
```
 let str = '%E4%B8%8E';

console.log(decodeURI(str));  //码转中文

console.log(encodeURI('与'))//把中文转成URI码
```


***
### JSON的转换方法
- parse     
    JSON.parse(jsonString) 把字符串的json转成可以操作的js对象
- stringify     
    JSON.stringify(jsonObject) 把字符串的json对象转成可以发送的js字符串