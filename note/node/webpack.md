# initial-webpack-learning-notes
初始webpack 学习笔记


## 关于 `.babelrc` 这个配置文件
 1.   干什么的？ 预设和配置的方法？
 
 	> 存放针对本项目，而使用的babel中插件及预设所存放的内容，文件内容用：`{}`进行包含，内容为json格式，
 	所以内容需要`""`;

	> 如图：

	>     {
  	>      "presets": [],//存放安装的预设 如：react env等
  	>      "plugins": []//存放安装的插件 如：单一插件 plugin-transform-object-rest-spread
  	>      }
  	>      //如何区分：预设 或者插件
  	>      //安装的时候，如果是babel-preset开头进行安装的那么就是预设，如果是babel-plugin安装的就是插件

2.  什么时候会被使用？
	> 当`package.json`文件中模块里面写入了
	> 
	>       module:{
	>       rules:[{
	>       //识别模块引入的时候以js结尾的文件
	>       test:/\.js$/,
	>       //使用 babel-loder=>会直接去找babelrc的文件
	>       use:['babel-loader']
	>       }]
	       
##  关于 `babel`
1.  干什么的？
	> 将javascript模块化的时候，因为浏览器只能识别EC5的代码，用babel进行转化。
	
2.  如何在 `cli` 使用？
	> Babel提供babel-cli工具，用于命令行转码。
	> 
	> 它的安装命令如下:
	> 
	>     $ npm install --global babel-cli
	> 基本用法如下:
	> 
	>     # 转码结果输出到标准输出
	>     $ babel example.js
	>     
	>     # 转码结果写入一个文件
	>     # --out-file 或 -o 参数指定输出文件
	>     $ babel example.js --out-file compiled.js
	>     # 或者
	>     $ babel example.js -o compiled.js
	>     
	>     # 整个目录转码      （操作成功）
	>     # --out-dir 或 -d 参数指定输出目录
	>     $ babel src --out-dir lib
	>     # 或者
	>     $ babel src -d lib
	>     
	>     # -s 参数生成source map文件
	>     $ babel src -d lib -s
	> 上面代码是在全局环境下，进行Babel转码。这意味着，如果项目要运行，全局环境必须有Babel，也就是说项目产生了对环境的依赖。另一方面，这样做也无法支持不同项目使用不同版本的Babel。
	> 
	> 一个解决办法是将babel-cli安装在项目之中。
	> 
	>     # 安装
	>     $ npm install --save-dev babel-cli
	>     然后，改写package.json。
	>     {
	>       // ...
	>       "devDependencies": {
	>       "babel-cli": "^6.0.0"
 	>      },
	>       "scripts": {
	>         "build": "babel src -d lib"
	>      },
	>     }
	  
3.  如何在 webpack 使用？
    >     use:['babel-loader']
         
4.  基于什么运行的?
	> 基于插件运行
	 
5.  预设是什么？
	> 可理解为某种特定插件的集合，如Es6有很多语法，如果将每个语法单独拿出来安装叫做插件，如果将Es6、Es7等整合到一起做一个大的插件进行安装叫做预设。
	
## 关于 `webpack`
1.  干什么的?
	>  是javascript应用程序的模块打包器，它会递归构造出一个依赖关系图，其中包含引用程序需要的每个模块，然后将这些程序打包成少量的捆，通常之后一个，由浏览器进行加载。
	
2.  入口是什么意思, 如何配置？
	> 入口：是告知webpack从哪里还是入手去构造出依赖关系图（一般指总的app.js）根据上下文或者app的总文件
	> 配置：
	> 
	>     module.exports ={
	>       entry:'./src/app.js'
	>     }
	   
3.  输出是什么意思, 如何配置(文件名, 输出路径)
	> 输出：让webpack进行打包捆绑之后输出到某个位置，以及文件名称？
	> 
	>     const path=require('path');
	> 
	>     module.exports={
	>       entry:'./src.app.js',
	>       output:{
	>         filename:'bundel.js',
	>         path:path.resolve(__dirname,'dist')
	>       }
	>     };
	     
4.  什么是 loader？
	> loader 是对于模块的源代码进行转换。loader可以在文件 `import` 或“加载”的时候进行预处理文件，loader可以将不同的语言转化为javascript；loader 甚至允许你直接在javascript模块中 `import` CSS文件。
	
5.  如何在 webpack 使用 babel-loader?
	>  > 例如：
	>  
	>  > 可以让webpack加载css文件，或者让TypeScript转化为javascript。所以先安装相应的loader
	>  
	>   >     npm install --save-dev css-loader
	>   >     npm install --save-dev ts-loader
	>   > 然后 webpack 将每个 `.css` 加载为css文件；将每个 `.ts` 加载为javascript文件。
	>   
	>   >  webpack.json 
	>   
	>   >     module.exports={
	>   >      module:{
	>   >       rules:[
	>   >        {test:/\.css$/,use:'css-loader'},
	>   >        {test:/\.ts$/,user:'ts-loader'}
	>   >       ]
	>   >      }
	>   >     }
	  
6.  在什么情况下会让 loader 起作用?
    > 当文件需要预处理的时候。

##关于 npm 的
1. 干什么用的
   > npm 是开源库生态系统,可以再npm官网找到服务器端使用的模块；轻松管理不同版本的代码
   
## 关于package.json的文件
1. 如何生成
   > npm init
   
2. 什么情况下会被使用
   > 安装生产或开发依赖的时候，以及声明命令
   
3. 如何在里面声明命令
   >     scripts：{
   >       "dev"："webpack"
   >     }
   > 好处是方面管理
   
4. 如何安装依赖 (声明为生产还是开发)
   > npm i -S react-dom  //生产依赖 -S
   > 
   > npm i -D babel-cli //开发依赖 -D
   
## 关于模块化语法

### Es6
1. 引入文件方式
>       //引入当前目录下名称为f .js 结尾的文件
>       import 'f.js'
>       //引入当前目录下 名称为ds .js结尾的文件，引入名称为a
>       import a from './ds.js'
>       // 引入当前目录下 名称为ds .js结尾的文件，引入 一个a 一个对象{a,b}
>       import a,{b,c} from './ds.js'
>       //引入当前目录下 名称为ds .js结尾的文件，引入 一个a 在引入一个对象，其中b命名为ccd、c 直接引入
>       import a,{b as ccd,c} from './ds.js'

2. 导出文件方式
>       export
>       export default

###commonJS   //node 引入模块的方法
1. 引入文件方式
>       require('./a.js')

2. 导出文件方式
>       module.exports
>       exports



	