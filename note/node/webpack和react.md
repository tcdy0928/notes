## webpack 打包 css文件
-  把css打包到js文件里面，一般是在开发阶段 css 的打包方式
    - 把 css 打包到js  是把css在js中变成一个字符串，然后在head创建一个style 把这个字符串丢进去就可以了
-  把 css 打包成一个单独的 css 文件，通过link引入（自动创建）生产阶段





## 2. 声明 react 的组件
继承了 React.Component 的类就是一个组件
至少有一个 render 方法
    这个方法应该 return 一份 jsx 的对象,
    这就是这个组件的样子


## 3. jsx 语法
-  相邻的jsx元素必须包含在一个闭合的标签里面
- 自己声明的组件要大写开头,内置组件小写开头
- jsx 本身可以是一个表达式
- 在 jsx 里面使用 {} 表示表达式
- 标签之间的内容就叫 children, 如果是类的组件的标签, 它的 children 通过实例(this)的 props.children 拿到
- 关键词要转成另外一种形式 : class->className for->htmlFor, 应该是驼峰式的


## webpack 打包 css 文件
- 把 css 打包到 js 文件里面 , 一般是在开发阶段 css 的打包方式
- 把 css 打包成一个单独的 css 文件, 通过 link 引入(自动创建) 生产阶段

## 关于 css-loader
引入 css 文件的使用这个 loader 处理它
遇到 url 或 @import 帮你去引入里面的资源, 引入资源的过程中, 更根据资源的类型再使用相应的 loader 去处理

## 关于 file-loader
处理资源(字体, 图片, 视频)
转换出一个路径, 把资源搬到输出目录

***
##  props: react的属性
    传递属性: <Content a="8"></Content>
    拿到: this.props
***
***
## state
组件有内部状态: this.state = {}
通过 this.setState() 来改变组件的内部状态, 这个时候页面会更新, 因为组件的 render 执行了, 得到了一份新的 jsx 的结构
父组件的 render 执行了, 子组件的 render 也会执行
改变页面状态, 应该通过 setState 更新
***


### 关于 webpack
    html-webpack-plugin 自动创建 html 文件
    clean-webpack-plugin 清理某一个文件夹在打包之前

