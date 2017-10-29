# ajax函数的封装
```

function ajax(json){
	
	let settings = {
		url:'',
		method:'get',
		data:{},
		dataType:'string',
		success:function(){},
		error:function(){}
	}
	
	Object.assign(settings,json);

	var ajax = new XMLHttpRequest;
	
	var arr = [];
	for(var attr in settings.data){
		arr.push(attr + '=' + settings.data[attr]);
	}
	
	settings.data = arr.join('&');
	
//	console.log(settings.data)
	
	if(settings.method.toLowerCase() == 'get'){
		ajax.open('get',settings.url+'?'+settings.data);
		ajax.send();
	}else if(settings.method.toLowerCase() == 'post'){
		ajax.open('post',settings.url);
		ajax.setRequestHeader('Content-Type','application/x-www-form-urlencoded');
		ajax.send(settings.data);
	}else{
		alert('88');
	}
	
	ajax.onreadystatechange = function(){
		if(ajax.readyState == 4){
			
			if(ajax.status >= 200 && ajax.status <= 207 || ajax.status == 304){
				//成功
				
				if(settings.dataType == 'string'){
					settings.success(ajax.responseText);
				} else if(settings.dataType == 'xml'){
					settings.success(ajax.responseXML);
				} else if(settings.dataType == 'json'){
					settings.success(JSON.parse(ajax.responseText));
				}else{
					settings.success('请核对参数');
				}
				
			}else{
				//失败
				
				settings.success({state:ajax.readyState,status:ajax.status});
				//alert(ajax.status)
			}
		}
	}

	
}


```


# ajax函数的封装
```

function jsonp(obj){
				
	//初始化默认项
	var opt = {
		//接口
		url:'',
		//接口里面需要传入的数据
		data:{},
		//修改函数名字的接口的设定
		callback:'callback',
		//设定函数名	处理多次调用的问题，
		fnName:('jquery'+new Date().getTime()+Math.random()).replace('.',''),
		//数据获取成功之后做什么
		success:function(){},
		//数据获取失败之后做什么
		fail:function(){}
	}
	
	//有配置走配置，没配置走默认
	for(var attr in obj){
		opt[attr] = obj[attr];
	}
	//把修改函数名的接口设定传到data里一起循环处理到接口里
	opt.data[opt.callback] = opt.fnName;
	
	//将接口需要的数据拼接到接口里
	var arr = [];
	for(var attr in opt.data){
		arr.push(attr + '=' + opt.data[attr]);
	}
	var queryString = arr.join('&');
	
	var timer = null;
	timer = setTimeout(function(){
		fail();
	},5000)
	
	window[opt.fnName] = function(obj){
		clearTimeout(timer);
		success(obj);
	}
	
	//jsonp数据的处理
	var os = document.createElement('script');
	os.src = opt.url + '?' + queryString;
	document.getElementsByName('head')[0].appendChild(os);
	os.remove();
}


```