# front-end
整理的一些前端资料 . 

前端就是基于浏览器的一门技术，可以通过js来跟浏览器沟通交流，浏览器抛出的api与之通信，前端所用的框架也是基于此，首先先得理解浏览的工作原理，然后看下框架的实现方式，首先要手写一个框架，了解其工作原理，然后再通过一些其他的方式来优化，比如webpack等方式。


#### html:
 1. `<!DOCTYPE>`
 
 > `<!DOCTYPE>` 声明位于文档中的最前面的位置，处于 <html> 标签之前。

 > `<!DOCTYPE>` 声明不是一个 HTML 标签；它是用来告知 Web 浏览器页面使用了哪种 HTML 版本。

 > 在 HTML 4.01 中，`<!DOCTYPE>` 声明需引用 DTD （文档类型声明），因为 HTML 4.01 是基于 SGML （Standard Generalized Markup Language 标准通用标记语言）。DTD 指定了标记语言的规则，
 > 确保了浏览器能够正确的渲染内容。
 > HTML5 不是基于 SGML，因此不要求引用 DTD。
 
 > HTML 4.01 与 HTML5之间的差异
 
 > HTML 4.01 规定了三种不同的 `<!DOCTYPE>` 声明，分别是：Strict、Transitional 和 Frameset。 HTML5 中仅规定了一种：`<!DOCTYPE html>`
 
 2. meta标签
 
 > 提供给页面的一些元信息（名称/值对），有助于SEO。
 
 > 属性值
 >> name：名称/值对中的名称。author、description、keywords、generator、revised、others。 把 content 属性关联到一个名称。
 
 >> http-equiv：没有name时，会采用这个属性的值。content-type、expires、refresh、set-cookie。把content属性关联到http头部
 
 >> content：名称/值对中的值， 可以是任何有效的字符串。 始终要和 name 属性或 http-equiv 属性一起使用
 
 >> scheme： 用于指定要用来翻译属性值的方案
 
 3. HTML语义化
 
 > 用正确的标签做正确的事情。
 
 > html语义化让页面的内容结构化，结构更清晰，便于对浏览器，搜索引擎解析；
 
 > 即使在没有样式CSS情况下也以一种文档格式显示，并且是容易阅读的；
 
 > 搜索引擎的爬虫也依赖于HTML标记确定上下文和各个关键字的权重，利于SEO;
 
 > 使阅读源代码的人对网站更容易将网站分块，便于阅读维护理解。
 
 4. 常见的浏览器内核
 
 > Trident内核：IE,MaxThon,TT,The Word,360,搜狗浏览器等。
 
 > Gecko内核：Netscape6及以上版本，FF,MozillaSuite/SeaMonkey等；
 
 > Presto内核：Opera7及以上。[现为：Blink]
 
 > Webkit内核：Safari,Chrome等。[Chrome的:Blink(Webkit的分支)]
 
 5. 简单介绍对浏览器内核的理解
 
 > 主要分成两部分：渲染引擎和JS引擎。

 > 渲染引擎：将代码转换成页面。负责取得网页的内容（HTML、XML、图像等等）、整理讯息（例如加入CSS等）、以及计算网页的显示方式，然后会输出至显示器或打印机。浏览器的内核的不同对于网页的语法解释会有
 > 不同，所以渲染的效果也不相同。所有网页浏览器、电子邮件客户端以及其他需要编辑、显示网络内容的应用程序都需要内核。
 > JS引擎：解析和执行javascript来实现网页的动态效果。

 > 最开始渲染引擎和JS引擎并没有区分得很明确，后来JS引擎越来越独立，内核就倾向于只指渲染引擎。
 
 6. HTML5有哪些新特性，移除了哪些元素？如何处理HTML5新标签的浏览器兼容问题？
 
 > 新特性：

 >> 用于绘画的canvas元素；
 
 >> 用于媒介回放的video和audio元素；
 
 >> 对本地离线存储有更好的支持，localStorage长期存储数据，浏览器关闭后数据不丢失；sessionStorage的数据在浏览器关闭后自动删除；
 
 >> 语意化更好的内容元素，比如header,nav,section,article,footer；
 
 >> 新的表单控件：calendar,date,time,email,url,search；
 
 >> 新的技术webworker,websockt、Geolocation；

 > 移除元素：

 >> 纯表现的元素：basefont,big,center,font,s,strike,tt,u;
 >> 对可用性产生负面影响的元素：frame,frameset,noframes;

 > 处理兼容性问题：

 >> IE8/IE7/IE6支持document.createElement方法产生的标签，可以利用这一特性让这些浏览器支持HTML5新标签，浏览器支持新标签后，还需要添加标签默认的样式。
 
 7. html5哪些标签可以做SEO优化？
 
 > title、meta、header、footer、nav、article、aside
 
 
 
#### css:
  > style: flex原理  
  >> https://www.cnblogs.com/nuannuan7362/p/5823381.html
  
  > 垂直居中居中方式 . 
  >> http://www.cnblogs.com/hutuzhu/p/4450850.html  
  
  > 盒模型等等 . 
  >> https://www.cnblogs.com/chengzp/p/cssbox.html
  
  > transform的几种属性等等 . 
  >> https://www.cnblogs.com/mumu-web/p/5706779.html  
  
  > css面试题及答案  
  >> https://segmentfault.com/a/1190000013325778  
  
  > bfc  
  https://www.cnblogs.com/zczhangcui/p/6081574.html  
  
  > 验证css传送门  
  http://www.w3school.com.cn/tiy/t.asp?f=csse_selector_child
  
#### js:
  > 1、浏览器输入url之后发生了什么?  
  >> https://www.jianshu.com/p/c1dfc6caa520 . 
  
  > 2、indexDB数据 . 
  
  > 3、resultfulApi . 
  
  > 4、js的设计模式 . 
  >> https://juejin.im/entry/58c280b1da2f600d8725b887
    
  > 5、serviceWorker . 
  
  > 6、svg . 
  
  > 7、js的单元测试 . 
  
  > 8、js的算法： 去重、排序等等 . 
  
  > 9、新版css  
  
  > 10、dart语言 . 
  
  > 11、seo优化 . 
  
  > 12、es6的set、get、迭代器 . 
  
  > 13、http的属性以及https的区别 . 
  
  > 14、js继承的几种方式
  
  > 15、双向数据绑定的原理（es6）
  
  > 16、prototype（原型定义）
  
  > 17、浏览器怎么渲染页面 . 
  
  > 18、ajax。request . 
  
  > 19、hybrid
  
  > 20、递归
  
  > 21、箭头函数原理（this指向问题）  
  
  > 22、事件捕获原理 . 
  
  > 23、对象的深拷贝浅拷贝  
  
  > 24、js的几种常见问题  
  >> https://www.haorooms.com/post/qd_ghfx  
  
#### 库的使用:
  > react:  
  
  >> 1、redux原理  
    
  >> 2、中间键  
  
  >> 3、高阶组件  
  
  > > 4、生命周期  
  
  >vue:  
  
  >> 1、vuex . 
  
  > > 2、广播 . 
  
  > > 3、mixin . 
  
  > > 4、生命周期 . 
  
  >关于react引入antd没有样式问题.
  在modules下面找到babel-loder，然后在options下面加上
  plugins: [
                ['import', { libraryName: 'antd', style: 'css' }],
              ],
