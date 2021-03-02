react：

1.mvc  mvp  mvvm区别

>View传送指令到Controller。

>Controller完成业务逻辑后改变Model状态。

>Model将新的数据发送至View,用户得到反馈。

>MVVM将“数据模型数据双向绑定”的思想作为核心，因此在View和Model之间没有联系，通过ViewModel进行交互，而且Model和ViewModel之间的交互是双向的，因此视图的数据的变化会同时修改数据源，而数据源数据的变化也会立即反应到View上。即，ViewModel 是一个 View 信息的存储结构，ViewModel 和 View 上的信息是一一映射关系。

2.hooks的使用

React 是主流的前端框架，v16.8 版本引入了全新的 API，叫做 React Hooks，颠覆了以前的用法。

>https://www.ruanyifeng.com/blog/2019/09/react-hooks.html 阮一峰

3.虚拟dom概念
>document.createElemen()

4.新的生命周期有哪些改变
>React 从 v16.3 开始，对生命周期进行了渐进式的调整。废弃了一些生命周期方法和添加了一些新的生命周期方法。

>https://juejin.im/post/6844904005152276487

5.跟vue，angular跟新机制的区别

6.react父子组件的生命周期
>当父组建 render 时遇到子组件，然后进入子组件的生命周期，当执行完子组件生命周期中的componentDidMount 时会回到父组建继续执行父组建未完成的生命周期。

>https://www.jianshu.com/p/26c6242f6746

7.react render做了什么事情

>https://zhuanlan.zhihu.com/p/45091185

8.redux原理 

Redux应用的三大原则

单一数据源
>我们可以把Redux的状态管理理解成一个全局对象，那么这个全局对象是唯一的，所有的状态都在全局对象store下进行统一”配置”，这样做也是为了做统一管理，便于调试与维护。

State是只读的
>与React的setState相似，直接改变组件的state是不会触发render进行渲染组件的。同样，在Redux中唯一改变state的方法就是触发action，action是一个用于描述发生了什么的“关键词”，而具体使action在state上更新生效的是reducer，用来描述事件发生的详细过程，reducer充当了发起一个action连接到state的桥梁。这样做的好处是当开发者试图去修改状态时，Redux会记录这个动作是什么类型的、具体完成了什么功能等（更新、传播过程），在调试阶段可以为开发者提供完整的数据流路径。

Reducer必须是一个纯函数
>Reducer用来描述action如何改变state，接收旧的state和action，返回新的state。Reducer内部的执行操作必须是无副作用的，不能对state进行直接修改，当状态发生变化时，需要返回一个全新的对象代表新的state。这样做的好处是，状态的更新是可预测的，另外，这与Redux的比较分发机制相关，阅读Redux判断状态更新的源码部分(combineReducers)，发现Redux是对新旧state直接用==来进行比较，也就是浅比较，如果我们直接在state对象上进行修改，那么state所分配的内存地址其实是没有变化的，“==”是比较对象间的内存地址，因此Redux将不会响应我们的更新。之所以这样处理是避免对象深层次比较所带来的性能损耗（需要递归遍历比较）。 

>https://zhuanlan.zhihu.com/p/50247513

9.中间键 middlewares 
>Redux 的中间件提供的是位于 action 被发起之后，到达 reducer 之前的扩展点，换而言之，原本 view -> action -> reducer -> store 的数据流加上中间件后变成了 view -> action -> middleware -> reducer -> store ，在这一环节我们可以做一些 “副作用” 的操作，如 异步请求、打印日志等。


10. 高阶组件  HOC
>高阶组件（HOC）是 React 中用于复用组件逻辑的一种高级技巧。HOC 自身不是 React API 的一部分，它是一种基于 React 的组合特性而形成的设计模式。

>具体而言，高阶组件是参数为组件，返回值为新组件的函数。

>https://zh-hans.reactjs.org/docs/higher-order-components.html

11.setState原理
>要知道setState本质是通过一个队列机制实现state更新的。 执行setState时，会将需要更新的state合并后放入状态队列，而不会立刻更新state，队列机制可以批量更新state。
>如果不通过setState而直接修改this.state，那么这个state不会放入状态队列中，下次调用setState时对状态队列进行合并时，会忽略之前直接被修改的state，这样我们就无法合并了，而且实际也没有把你想要的state更新上去
 

setState函数的第二个参数允许传入回调函数，在状态更新完毕后进行调用，譬如：
```
this.setState({
      load: !this.state.load,
      count: this.state.count + 1
    }, () => {
      console.log(this.state.count);
      console.log('加载完成')
    });
```
   
12.数据管理工具Flux、Redux、Vuex的区别
>https://cloud.tencent.com/developer/article/1454710
>https://zhuanlan.zhihu.com/p/75696114

13.react router原理

14.jsx，虚拟dom怎么渲染，什么时候渲染出来

15.setstate  内部实现方式

16.由浅入深快速掌握React Fiber
> https://www.jianshu.com/p/37d7de212df1
