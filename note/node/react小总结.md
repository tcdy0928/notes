# React
## React是什么
用于构建用户界面的JavaScript库

## 如何使用React
- 下载静态页面
- 通过工具


## React的特点
- 虚拟 DOM
    - 通过DOM diff算法，只会更新有差异的部分，不用渲染整个页面，从而提高效率
- 组件化      
    - 把页面分成若干个组件，组件中包含逻辑结构和样式
    - 组件只包含自身逻辑，跟新组件的时候可以预测，利于维护
    - 页面拆分成多个组件，可以做到重用
- 单向数据流
    - 数据是从顶层组件传递到子组件中
    - 数据可控


## JSX是什么
-  它是JavaScript XML     
-  JSX 是 React 编写组件的一中语法规范，它支持将Html和JS混写在一起，最后编译为常规的JavaScript， 便于浏览器解析   
-   JSX 的基本语法规则：遇到 HTML 标签（以 < 开头），就用 HTML 规则解析；遇到代码块（以 { 开头），就用 JavaScript 规则解析。
-   JSX 允许直接在模板插入 JavaScript 变量。如果这个变量是一个数组，则会展开这个数组的所有成员
```
    比如:
    var arr = [
      <h1>Hello world!</h1>,
      <h2>React is awesome</h2>,
    ];
    ReactDOM.render(
      <div>{arr}</div>,
      document.getElementById('example')
    );
    
    输出：
        Hello world!
        React is awesome
```


## 组件     
React 允许将代码封装成组件（component），然后像插入普通 HTML 标签一样，在网页中插入这个组件。
-  所有组件类都必须有自己的 render 方法，用于输出组件。
-  组件类的第一个字母必须大写，否则会报错。
-  组件类只能包含一个顶层标签，否则也会报错。
-  组件的用法与原生的 HTML 标签完全一致，可以任意加入属性。
-  组件的属性可以在组件类的 this.props 对象上获取
-  添加组件属性，有一个地方需要注意，不能使用关键字。所以 class 属性需要写成 className ，for 属性需要写成 htmlFor 


## this.props.children
this.props 对象的属性与组件的属性一一对应，但是有一个例外，就是 this.props.children 属性。它表示组件的所有子节点
-  this.props.children 的值有三种可能：
    - 如果当前组件没有子节点，它就是 undefined
    - 如果有一个子节点，数据类型是 object
    - 如果有多个子节点，数据类型就是 array   
**React 提供一个工具方法 React.Children 来处理 this.props.children 。我们可以用 React.Children.map 来遍历子节点，而不用担心 this.props.children 的数据类型是 undefined 还是 object**


## 获取真实的DOM节点
组件并不是真实的 DOM 节点，而是存在于内存之中的一种数据结构，叫做虚拟 DOM （virtual DOM）。只有当它插入文档以后，才会变成真实的 DOM 。根据 React 的设计，所有的 DOM 变动，都先在虚拟 DOM 上发生，然后再将实际发生变动的部分，反映在真实 DOM上，这种算法叫做 DOM diff ，它可以极大提高网页的性能表现。      
但是，有时需要从组件获取真实 DOM 的节点，这时就要用到 ref 属性
-  需要注意的是，由于 this.refs.[refName] 属性获取的是真实 DOM ，所以必须等到虚拟 DOM 插入文档以后，才能使用这个属性，否则会报错。
