
-------

title: react 
category: React

-------

#### es6

#### react

?一句话概括解决了什么问题
?渲染流程
?知识组块->功能->实现

- jsx 
 	- 表达式
 	- 自定义属性：字符串指定属性、js表达式嵌入到属性
 	- 可包含元素
 	- 防止xss攻击
 		- 转义在JSX中嵌入的任何值	
 	
	React.createElement()	
 	
- react-dom 
	- render: (React Element -> DOM node) ReactDOM.render()
	- * diff 
 
- react components
	- es6 class (class Welcome extends React.Component{} )
	- function Welcome(){} 
	- React.createClass() （貌似已经取消了这个方法) （引入'create-react-class')

- 数据处理 props state context 自顶向下，单项数据流
	- Lifecycle hooks
	- state
		- 不能直接修改state
		- state更新是异步的
			- this.setState()
			- this.setState((prevState,props)=>({}))

- 事件处理 Event
	- 为什么需要 bind(this) ？	

- 条件渲染 Conditional Rendering 
	- if else 
	- && 
	- ? : 
	
- Lists and Keys 渲染列表
	- 为什么键是必要的?
	- 索引用于键会引发什么问题？

- Forms 
	- 受控组件 （example input组件本身有自己的状态,现在react接管它的状态）
	- 不受控组件

- Lifting State Up 提升状态
	
- composition vs inheritance



Q&A
context 上下文
Fragments 片段
Portals
Higher-Order Components 

Test utilities 单测


#### react-router 

控制路径与UI渲染同步

Link 更新url    （证明 源码）
Route 渲染UI

react-router 
react-router-dom (升级库，比react-router多link,browserRouter)
	- router 保持与location同步
	- route location 匹配到 path 时，渲染某些UI
react-router-native
react-router-redux 
react-router-config


?路由拆分 按需加载
?静态路由和动态路由的区别
?知识组块

#### flux

?解决了什么问题

#### redux

redux

react-redux

redux-saga

#### mobx


#### webpack 




webpack hmr 热更新

webpack-dev-server

mock


css modules 原理
js modules 原理


## 同构 SSR


