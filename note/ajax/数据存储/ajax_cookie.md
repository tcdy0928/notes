# ajax_cookie
-  其实是后端的技术，用来记录匹配后端的sessionID的，从而保证用户只要在当前浏览器访问页面，登录信息不会被丢失。
- cookie是在服务器下运行的。
- 前端使用一般用来数据存储（配合后端进行一些用户优化）
## 设置cookie
- **每个域名**下一般就多少条（多少个、多少k）
```
document.cookie = 'key=value';
```
-  生命周期:
    - 默认的生命周期就是当前的浏览器彻底关闭，生命结束
- 设置生命周期:
    - expires


## 设置cookie的函数封装
```

function setCookie(key,val,time){
    if( time ){
        var d = new Date();
        d.setDate(d.getDate()+time);
        document.cookie = key+'='+val+';expires='+d;
    }else{
        document.cookie = key+'='+val;
    }
}

```
## 获取cookie的函数封装
```
function getCookie(key){
    let cookieArr = document.cookie.split('; ');
    let  temp = '';
    cookieArr.forEach((e)=>{
        let arr = e.split('='); 
        if(arr[0] === key){
            temp = arr[1];
        }
    });
    return temp?temp:null;
}

```