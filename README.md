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

5. <label>标签的用法

> label标签主要是方便鼠标点击使用，扩大可点击的范围，增强用户操作体验

> label标签用来定义表单控件间的关系,当用户选择该标签时，浏览器会自动将焦点转到和标签相关的表单控件上。label 中有两个属性是非常有用的, FOR和ACCESSKEY。 

> FOR属性功能：表示label标签要绑定的HTML元素，你点击这个标签的时候，所绑定的元素将获取焦点。例如，

>`<label for="labelKey">label</label>  <input id="labelKey" />`

> ACCESSKEY属性功能：表示访问label标签所绑定的元素的热键，当您按下热键，所绑定的元素将获取焦点。例如，

>`<label for="labelKey" accesskey="c">label</label>  <input id="labelKey" />`

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

8. src和href的区别, 以及页面导入样式时，使用link和@import的区别

src和href：
> src是指向外部资源的位置，指向的内容会嵌入到文档中当前标签所在的位置，在请求src资源时会将其指向的资源下载并应用到文档内，如js脚本，img图片和frame等元素。当浏览器解析到该元素时，会暂停其他资
> 源的下载和处理，知道将该资源加载、编译、执行完毕，所以一般js脚本会放在底部而不是头部。


> href是指网络资源所在位置，建立和当前元素（锚点）或当前文档（链接）之间的链接，用于超链接。

link和@import：
> 相同的地方，都是外部引用CSS方式，区别：

> link是xhtml标签，除了加载css外，还可以定义RSS等其他事务；@import属于CSS范畴，只能加载CSS

> link引用CSS时候，页面载入时同时加载；`@import`需要在页面完全加载以后加载，而且`@import`被引用的CSS会等到引用它的CSS文件被加载完才加载

> link是xhtml标签，无兼容问题；@import是在css2.1提出来的，低版本的浏览器不支持

> link支持使用javascript控制去改变样式，而`@import`不支持

> link方式的样式的权重高于@import的权重

> import在html使用时候需要 `<style type="text/css">` 标签

无样式内容闪烁（FOUC）Flash of Unstyle Content

> `@import`导入CSS文件会等到文档加载完后再加载CSS样式表。因此，在页面DOM加载完成到CSS导入完成之间会有一段时间页面上的内容是没有样式的。

> 解决方法：使用link标签加载CSS样式文件。因为link是顺序加载的，这样页面会等到CSS下载完之后再下载HTML文件，这样先布局好，就不会出现FOUC问题。

9. 渐进增强和优雅降级

> 渐进增强：针对低版本浏览器进行构建页面，保证最基本的功能，然后再针对高级浏览器进行效果、交互等改进和追加功能，达到更好的用户体验。

> 优雅降级：一开始就构建完整的功能，然后再针对低版本的浏览器进行兼容。

10. defer和async的区别

> defer要等到整个页面在内存中正常渲染结束（DOM结构完全生成，以及其他脚本执行完成），才会执行。多个defer脚本会按照它们在页面出现的顺序加载。==“渲染完再执行”==

> async一旦下载完，渲染引擎就会中断渲染，执行这个脚本以后，再继续渲染。多个async脚本是不能保证加载顺序的。==“下载完就执行”==

11. 盒模型

> 盒模型的组成，由里向外content,padding,border,margin.

>在IE盒子模型中，width表示content+padding+border这三个部分的宽度

>在标准的盒子模型中，width指content部分的宽度

>box-sizing的使用

>>box-sizing: content-box 是W3C盒子模型

>>box-sizing: border-box 是IE盒子模型

>>box-sizing的默认属性是content-box

12. 简单介绍对浏览器内核的理解

> 主要分成两部分：渲染引擎和JS引擎。

> 渲染引擎：将代码转换成页面。负责取得网页的内容（HTML、XML、图像等等）、整理讯息（例如加入CSS等）、以及计算网页的显示方式，然后会输出至显示器或打印机。浏览器的内核的不同对于网页的语法解释会有
> 不同，所以渲染的效果也不相同。所有网页浏览器、电子邮件客户端以及其他需要编辑、显示网络内容的应用程序都需要内核。
> JS引擎：解析和执行javascript来实现网页的动态效果。

> 最开始渲染引擎和JS引擎并没有区分得很明确，后来JS引擎越来越独立，内核就倾向于只指渲染引擎。

13. 简单介绍对浏览器内核的理解

> 主要分成两部分：渲染引擎和JS引擎。

> 渲染引擎：将代码转换成页面。负责取得网页的内容（HTML、XML、图像等等）、整理讯息（例如加入CSS等）、以及计算网页的显示方式，然后会输出至显示器或打印机。浏览器的内核的不同对于网页的语法解释会有
> 不同，所以渲染的效果也不相同。所有网页浏览器、电子邮件客户端以及其他需要编辑、显示网络内容的应用程序都需要内核。 JS引擎：解析和执行javascript来实现网页的动态效果。

> 最开始渲染引擎和JS引擎并没有区分得很明确，后来JS引擎越来越独立，内核就倾向于只指渲染引擎。

14. 页面渲染html的过程？
> 不需要死记硬背，理解整个过程即可
> 浏览器渲染页面的一般过程：

> 1.浏览器解析html源码，然后创建一个 DOM树。并行请求 css/image/js在DOM树中，每一个HTML标签都有一个对应的节点，并且每一个文本也都会有一个对应的文本节点。DOM树的根节点就是documentElement，
> 对应的是html标签。

> 2.浏览器解析CSS代码，计算出最终的样式数据。构建CSSOM树。对CSS代码中非法的语法它会直接忽略掉。解析CSS的时候会按照如下顺序来定义优先级：浏览器默认设置 < 用户设置 < 外链样式 < 内联样式 < html
> 中的style。

> 3.DOM Tree + CSSOM --> 渲染树（rendering tree）。渲染树和DOM树有点像，但是是有区别的。

> DOM树完全和html标签一一对应，但是渲染树会忽略掉不需要渲染的元素，比如head、display:none的元素等。而且一大段文本中的每一个行在渲染树中都是独立的一个节点。渲染树中的每一个节点都存储有对应的> > css属性。

> 4.一旦渲染树创建好了，浏览器就可以根据渲染树直接把页面绘制到屏幕上。

> 以上四个步骤并不是一次性顺序完成的。如果DOM或者CSSOM被修改，以上过程会被重复执行。实际上，CSS和JavaScript往往会多次修改DOM或者CSSOM。

15. 说一下CORS？

> CORS是一种新标准，支持同源通信，也支持跨域通信。fetch是实现CORS通信的

16. HTML5的form如何关闭自动完成功能？

> HTML的输入框可以拥有自动完成的功能，当你往输入框输入内容的时候，浏览器会从你以前的同名输入框的历史记录中查找出类似的内容并列在输入框下面，这样就不用全部输入进去了，直接选择列表中的项目就可以
> 了。但有时候我们希望关闭输入框的自动完成功能，例如当用户输入内容的时候，我们希望使用AJAX技术从数据库搜索并列举而不是在用户的历史记录中搜索。

方式：
> 在IE的internet选项菜单中里的自动完成里面设置

> 设置form输入框的autocomplete为on或者off来来开启输入框的自动完成功能

17. iframe框架有那些优缺点？

优点：
> iframe能够原封不动的把嵌入的网页展现出来。

> 如果有多个网页引用iframe，那么你只需要修改iframe的内容，就可以实现调用的每一个页面内容的更改，方便快捷。

> 网页如果为了统一风格，头部和版本都是一样的，就可以写成一个页面，用iframe来嵌套，可以增加代码的可重用。

> 如果遇到加载缓慢的第三方内容如图标和广告，这些问题可以由iframe来解决。

缺点：
> 搜索引擎的爬虫程序无法解读这种页面, 不利于seo

> 框架结构中出现各种滚动条

> iframe页面会增加服务器的http请求

> iframe 会阻塞页面的onload事件

> iframe 和主页面共享连接池，浏览器对相同域的链接有限制，影响页面的并行加载

改进：
> 为了避免以上的问题出现可以使用JavaScript 给iframe  添加src 属性值

18. HTML5的文件离线储存怎么使用，工作原理是什么？

> 在线情况下，浏览器发现HTML头部有manifest属性，它会请求manifest文件，如果是第一次访问，那么浏览器就会根据manifest文件的内容下载相应的资源，并进行离线存储。如果已经访问过并且资源已经离线存储> 了，那么浏览器就会使用离线的资源加载页面。然后浏览器会对比新的manifest文件与旧的manifest文件，如果文件没有发生改变，就不会做任何操作，如果文件改变了，那么就会重新下载文件中的资源，并且进行离> > 线存储。例如，

> 在页面头部加入manifest属性

> `<html manifest="cache.manifest">`

> 在cache.manifest文件中编写离线存储的资源

```
CACHE MANIFEST
#v0.11
CACHE:
js/app.js
...

```

19.描述cookie、session的区别？
> cookie 是网站为了标示用户身份而存储在用户本地的上的数据，不占据服务器资源

> cookie 始终在同源http 中携带，在浏览器和服务端间来回传递

> cookie 只能保存string类型的数据，所以如果要存储复杂对象，需要进行序列化

> cookie 存储在本地，所以安全级别较低，所以一般都要加密，并且不推荐保存敏感数据在本地

> session   存储在服务器的数据，安全级别高，但占用服务器资源

> session   可以存储任意类型的数据

20. 渲染优化

> 禁止使用iframe（阻塞父文档onload事件）;

> 禁止使用gif图片实现loading效果（降低CPU消耗，提升渲染性能）；

> 使用CSS3代码代替JS动画（尽可能避免重绘重排以及回流）；

> 对于一些小图标，可以使用base64位编码，以减少网络请求。但不建议大图使用，比较耗费CPU；

> 页面头部的<style></style> 会阻塞页面；（因为 Renderer进程中 JS线程和渲染线程是互斥的）；

> 页面头部<script</script> 会阻塞页面；（因为 Renderer进程中 JS线程和渲染线程是互斥的）；

> 页面中空的 href 和 src 会阻塞页面其他资源的加载 (阻塞下载进程)；

> 网页Gzip，CDN托管，data缓存 ，图片服务器；

> 前端模板 JS+数据，减少由于HTML标签导致的带宽浪费，前端用变量保存AJAX请求结果，每次操作本地变量，不用请求，减少请求次数

> 用innerHTML代替DOM操作，减少DOM操作次数，优化javascript性能。

> 当需要设置的样式很多时设置className而不是直接操作style。

> 少用全局变量、缓存DOM节点查找的结果。减少IO读取操作。

> 避免使用CSS Expression（css表达式)又称Dynamic properties(动态属性)。

> 图片预加载，将样式表放在顶部，将脚本放在底部  加上时间戳。

> 避免在页面的主体布局中使用table，table要等其中的内容完全下载之后才会显示出来，显示比div+css布局慢。

#### css:
 1. flex原理  
 >> https://www.cnblogs.com/nuannuan7362/p/5823381.html

 2. 垂直居中居中方式
 >> http://www.cnblogs.com/hutuzhu/p/4450850.html 
 

 > 盒模型等等 . 
 >> https://www.cnblogs.com/chengzp/p/cssbox.html

 > transform的几种属性等等 . 
 >> https://www.cnblogs.com/mumu-web/p/5706779.html  

 > css面试题及答案  
 >> https://segmentfault.com/a/1190000013325778  

12. 清除浮动的几种方式，及原理？

> 清除浮动简单，但这题要引出的是BFC，BFC也是必考的基础知识点

>> ::after / <br> / clear: both

>> 创建父级 BFC(overflow:hidden)

>> 父级设置高度

>> BFC （块级格式化上下文），是一个独立的渲染区域，让处于 BFC 内部的元素与外部的元素相互隔离，使内外元素的定位不会相互影响。

> 触发条件:
>> 根元素

>> position: absolute/fixed

>> display: inline-block / table

>> float 元素

>> ovevflow !== visible

规则:
>> 属于同一个 BFC 的两个相邻 Box 垂直排列

>> 属于同一个 BFC 的两个相邻 Box 的 margin 会发生重叠

>> BFC 的区域不会与 float 的元素区域重叠

>> 计算 BFC 的高度时，浮动子元素也参与计算

>> 文字层不会被浮动层覆盖，环绕于周围
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

 24.js的几种常见问题  
 >> https://www.haorooms.com/post/qd_ghfx  
 
 25. 如何中断ajax请求？

 > 一种是设置超时时间让ajax自动断开，另一种是手动停止ajax请求，其核心是调用XML对象的abort方法，ajax.abort()



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
