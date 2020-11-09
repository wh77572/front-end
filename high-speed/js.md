js

1.说说你对闭包的理解
>说闭包之前,就要先说全局作用域和函数作用域

>利用函数作用域来保护私有变量，并且返回了对被保护变量的引用，这样的行为就是闭包。

2.浏览器渲染机制

浏览器渲染页面的过程

从耗时的角度，浏览器请求、加载、渲染一个页面，时间花在下面五件事情上：
>DNS 查询

>TCP 连接

>HTTP 请求即响应

>服务器响应

>客户端渲染

下面讨论第五个部分，即浏览器对内容的渲染，这一部分（渲染树构建、布局及绘制），又可以分为下面五个步骤：

>处理 HTML 标记并构建 DOM 树。

>处理 CSS 标记并构建 CSSOM 树。

>将 DOM 与 CSSOM 合并成一个渲染树。

>根据渲染树来布局，以计算每个节点的几何信息。

>将各个节点绘制到屏幕上。

总结：
在了解浏览器渲染过程之前，先来了解一下页面的加载流程。有助于更好理解后续渲染过程。从浏览器地址中从输入url地址到渲染出一个页面，会经过以下过程。
>浏览器输入的url地址经过DNS解析获得对应的IP
>
>向服务器发起TCP的3次握手
>
>建立连接后，浏览器向该IP地址发送http请求
>
>服务器接收到请求，返回一堆 HMTL 格式的字符串代码
>
>浏览器获得html代码，解析成DOM树
>
>获取CSS并构建CSSOM
>
>将DOM与CSSOM结合，创建渲染树
>
>找到所有内容都处于网页的哪个位置，布局渲染树
>
>最终绘制出页面
>
>
回流(reflow)与重绘(repaint)

>当元素的样式发生变化时，浏览器需要触发更新，重新绘制元素。这个过程中，有两种类型的操作，即重绘与回流。
>
>重绘(repaint): 当元素样式的改变不影响布局时，浏览器将使用重绘对元素进行更新，此时由于只需要UI层面的重新像素绘制，因此损耗较少
>回流(reflow): 当元素的尺寸、结构或触发某些属性时，浏览器会重新渲染页面，称为回流。此时，浏览器需要重新经过计算，计算后还需要重新页面布局，因此是较重的操作。会触发回流的操作:
>
>添加或删除可见的DOM元素
>
>元素的位置发生变化
>
>元素的尺寸发生变化（包括外边距、内边框、边框大小、高度和宽度等）
>
>内容发生变化，比如文本变化或图片被另一个不同尺寸的图片所替代。
>
>页面一开始渲染的时候（这肯定避免不了）
>
>浏览器的窗口尺寸变化（因为回流是根据视口的大小来计算元素的位置和大小的
 
 
 注意：回流一定会触发重绘，而重绘不一定会回流,重绘的开销较小，回流的代价较高
 
 因此为了减少性能优化，我们可以尽量避免回流或者重绘操作
 css
 
 避免使用table布局
 将动画效果应用到position属性为absolute或fixed的元素上
 


>https://juejin.im/entry/6844903503609987080
>https://juejin.im/post/6844903846834094094
>https://github.com/ljianshu/Blog/issues/51  详细

3.call，bind，apply的使用与区别
>如果call方法没有参数，或者参数为null或undefined，则等同于指向全局对象

>call跟apply用法类似，唯一不同的就是call是参数列表，apply是一个参数数组

>bind是创建一个新的函数，不会立即执行，call跟apply会立即执行

4.事件捕获与冒泡的区别
>在冒泡与捕获同时存在时,会先执行从外到内的捕获,然后再执行从内到外的冒泡

>按照W3C的标准，先发生捕获事件，后发生冒泡事件。

>所有事件的顺序是：其他元素捕获阶段事件 -> 本元素代码顺序事件 -> 其他元素冒泡阶段事件 。

>addEventListener的第三个参数，true 为捕获，false 为冒泡，默认为冒泡。

5.const，let，var区别
>let 的用法类似于 var，但是 let 只在所在的代码块内有效，所以我们一般使用 let 替代 var。而 const 用来声明常量。

6.箭头函数的作用域，this的指向问题，=>  衍生：作用域
>箭头函数体内的this对象，就是定义该函数时所在的作用域指向的对象，而不是使用时所在的作用域指向的对象。

7.js同步异步的区别
>同步就是所有的任务都处在同一队列中，不可以插队，一个任务执行完接着开始执行下一个，相对于浏览器而言，同步的效率过低，一些耗费时间比较长的任务应该用异步来执行。

>异步就是将一个任务放入到异步队列中，当这个任务执行完成之后，再从异步队列中提取出来，插队到同步队列中，拿到异步任务的结果，可以提升代码执行的效率，不需要因为一个耗费时长的代码而一直等待。

8.算法
排序：
除了我们常用的sort()方法，其实还有其他很多方法可以实现排序：

冒泡排序
```
function bubbleSort(arr){
    for(var i = 0; i < arr.length; i++){
        for(var j = 0; j < arr.length; j++){
            if(arr[i]< arr[j]){
                var temp = arr[j];
    
                arr[j] = arr[i];
    
                arr[i] = temp;
              }
           }
        }
        return arr;
    }

var arr =[524, 684, 5, 69, 15];

bubbleSort(arr);//结果为[5, 15, 69, 524, 684]
```

快速排序
```
function quickSort(arr){
    if(arr.length <= 1){
        return arr;
    }

    var pivotIndex = Math.floor(arr.length / 2);
    var pivot = arr.splice(pivotIndex, 1)[0];
    
    // splice()返回的是被删除元素组成的数组
    var lef =[];
    var rig =[];
    
    for(var i = 0; i < arr.length; i++){
        if(arr[i]< pivot){   
            lef.push(arr[i]);
        } else {
            rig.push(arr[i]);   
        }
    }
    
    return quickSort(lef).concat(pivot, quickSort(rig));//递归
}

var arr =[524, 684, 5, 69, 15];

quickSort(arr);//结果为[5, 15, 69, 524, 684]
```

插入排序

希尔排序

选择排序（坑未填）

归并排序（坑未填）

堆排序（坑未填）

>https://juejin.im/post/6844903569091461133#heading-0
>https://www.cnblogs.com/djw12333/p/11647413.html

9.promise内部实现方法
>https://mengera88.github.io/2017/05/18/Promise%E5%8E%9F%E7%90%86%E8%A7%A3%E6%9E%90/

10.new  set（）方法的使用
>Set和Map主要的应用场景在于数组去重和数据存储
set
>Set实例的属性和方法
 
Set的属性：
>集合是由一组无序且唯一(即不能重复)的项组成的，可以想象成集合是一个既没有重复元素，也没有顺序概念的数组

size：返回集合所包含元素的数量

Set的方法：

操作方法
>add(value)：向集合添加一个新的项

>delete(value)：从集合中移除一个值

>has(value)：如果值在集合中存在，返回true,否则false

>clear(): 移除集合里所有的项
 
遍历方法
>keys()：返回一个包含集合中所有键的数组

>values()：返回一个包含集合中所有值的数组

>entries：返回一个包含集合中所有键值对的数组(感觉没什么用就不实现了)

>forEach()：用于对集合成员执行某种操作，没有返回值

Map:

集合又和字典有什么区别呢：

>共同点：集合、字典可以存储不重复的值

>不同点：集合是以[值，值]的形式存储元素，字典是以[键，值]的形式存储

Map的属性和方法

属性：

size：返回字典所包含的元素个数

操作方法：

>set(key, val): 向字典中添加新元素

>get(key):通过键值查找特定的数值并返回

>has(key):如果键存在字典中返回true,否则false

>delete(key): 通过键值从字典中移除对应的数据

>clear():将这个字典中的所有元素删除

遍历方法：

>keys():将字典中包含的所有键名以数组形式返回

>values():将字典中包含的所有数值以数组形式返回

>forEach()：遍历字典的所有成员

11.hybrid怎么跟APP通信
Hybrid App（混合模式移动应用）是指介于web-app、native-app这两者之间的app，兼具" Native App良好用户交互体验的优势 "和" Web App跨平台开发的优势 "。

>H5 + JSBridge，通过JSBridge完成H5和Native的通信，赋予H5一定的端能力。是一种基于WebView UI的解决方案。

>React-Native，进一步通过JSbridge将js解析为虚拟DOM传递到Native，并使用原生进行渲染。

>小程序解决方案，采用双线程的渲染机制，将渲染层WebView和逻辑层JavaScriptCore形成独立的模块，通过Native进行通信（setData），逻辑层的网络请求也会由Native进行转发。在UI方面，采用的是WebView和原生相结合的方式。

12.跨域请求拦截
>解决跨域的解决办法有多种，比如jsonp，或者apache 或者nigix里面配置，或者后端的php或者java中配置 cross orgion。

有三个标签本身就是允许跨域加载资源的

```
    <img src=XXX>
    <link href=XXX>
    <script src=XXX>
```

> https://my.oschina.net/u/3216837/blog/3196454

13.图片懒加载

懒加载防止布局抖动
>Placeholder图片

>滚动加载

总结
>懒加载用户当前视窗中的图片可以提升页面的加载性能。

>懒加载的思路是在html解析时先加载一个placeholder图片，最后再用js选择性的加载真实图片。

>如果需要滚动加载可以使用 Intersection Observer 。

>对于固定尺寸和不定尺寸的图片，我们可以选择不同的服务去或者placeholder图片。

>对于图片尺寸不确定引起的布局抖动问题我们可以使用 aspect ratio box 来解决。

14.dns解析的过程
>DNS，就是Domain Name System的缩写，翻译过来就是域名系统，是互联网上作为域名和IP地址相互映射的一个分布式数据库。DNS能够使用户更方便的访问互联网，而不用去记住能够被机器直接读取的IP数串。通过域名，最终得到该域名对应的IP地址的过程叫做域名解析（或主机名解析）。

为什么需要DNS解析域名为IP地址？ 
>网络通讯大部分是基于TCP/IP的，而TCP/IP是基于IP地址的，所以计算机在网络上进行通讯时只能识别如“202.96.134.133”之类的IP地址，而不能认识域名。我们无法记住10个以上IP地址的网站，所以我们访问网站时，更多的是在浏览器地址栏中输入域名，就能看到所需要的页面，这是因为有一个叫“DNS服务器”的计算机自动把我们的域名“翻译”成了相应的IP地址，然后调出IP地址所对应的网页。

>https://www.zhihu.com/question/23042131

15.前端安全性
####XSS
>DOM型xss

>反射型xss

>存储型xss

解决方案
>过滤。

>编码

>httpOnly, 在cookie中设置HttpOnly属性，使js脚本无法读取到cookie信息。

####CSRF
>CSRF全称(Cross-Site Request Forgeries)跨站请求伪造。指攻击者冒充用户发起请求（在用户不知情的情况下），完成一些违背用户意愿的事情

解决方案
>使用token

>Referer 验证

>使用验证码

####点击劫持
>点击劫持就是将一个危险网站设置透明，然后在其上方设置一个按钮，当你点击这个按钮的时候，就会触发底部恶意网站的某些事件。

解决方案
>设置http响应头 X-Frame-Options

>使用CSP(Content Security Policy)内容安全策略

####不安全的第三方依赖
>现如今进行应用开发，无论是后端服务器应用还是前端应用开发，绝大多数时候我们都是在借助开发框架和各种类库进行快速开发。然而，一些第三方的依赖或者插件存在很多安全性问题，也会存在这样那样的漏洞，所以使用起来得谨慎。

解决方案
>尽量减少第三方依赖，选用相对成熟的依赖包。

>使用自动化工具检查这些第三方代码有没有安全问题，比如NSP(Node Security Platform)，Snyk等等。

####本地存储数据泄露
很多开发者为了方便，把一些个人信息不经加密直接存到本地或者cookie，这样是非常不安全的，黑客们可以很容易就拿到用户的信息。
解决方案
>不在本地存储重要数据,敏感、机密信息不要存储在本地。

>加密,所有在放到cookie中的信息或者localStorage里的信息要进行加密，加密可以自己定义一些加密方法或者网上寻找一些加密的插件，或者用base64进行多次加密然后再多次解码。

>https://juejin.im/post/6844903942036389895

16.对象的深拷贝浅拷贝 

JS的数据类型可以分为两种：基本数据类型和引用数据类型。
 
>Object.assgin({},target) => 这种方式第一层是深拷贝,第二层是浅拷贝

>我们在对数据进行复制的时候，如果这个数据是基本的数据类型，那么很好办，直接赋值就好，如果在使用JavaScript对数组或对象进行操作的时候，我们经常需要将数组或对象进行备份，事实证明如果只是简单的将它赋予其他变量，那么我们只要更改其中的任何一个，然后其他的也会跟着改变，这就导致了问题的发生。为了避免不必要问题的发生，我们需要明白，在对不同类型的数据进行复制的时候，发生了什么？

对象的浅拷贝：
>浅拷贝是对象共用一个内存地址，对象的变化相互影响。比如常见的赋值引用就是浅拷贝:

对象的深拷贝:
>简单理解深拷贝是将对象放到一个新的内存中，两个对象的改变不会相互影响。

17.HTTP使用TCP三次握手过程
>https://hit-alibaba.github.io/interview/basic/network/TCP.html

18.js继承

原型链：
>每个实例对象（ object ）都有一个私有属性（称之为 __proto__ ）指向它的构造函数的原型对象（prototype ）。该原型对象也有一个自己的原型对象( __proto__ ) ，层层向上直到一个对象的原型对象为 null。根据定义，null 没有原型，并作为这个原型链中的最后一个环节。

原型链继承
```
核心： 将父类的实例作为子类的原型

function Cat(){ 
}
Cat.prototype = new Animal();
Cat.prototype.name = 'cat';

//　Test Code
var cat = new Cat();
console.log(cat.name);
console.log(cat.eat('fish'));
console.log(cat.sleep());
console.log(cat instanceof Animal); //true 
console.log(cat instanceof Cat); //true
```

构造继承
```
核心：使用父类的构造函数来增强子类实例，等于是复制父类的实例属性给子类（没用到原型）

function Cat(name){
  Animal.call(this);
  this.name = name || 'Tom';
}

// Test Code
var cat = new Cat();
console.log(cat.name);
console.log(cat.sleep());
console.log(cat instanceof Animal); // false
console.log(cat instanceof Cat); // true
```

实例继承
```
核心：为父类实例添加新特性，作为子类实例返回

function Cat(name){
  var instance = new Animal();
  instance.name = name || 'Tom';
  return instance;
}

// Test Code
var cat = new Cat();
console.log(cat.name);
console.log(cat.sleep());
console.log(cat instanceof Animal); // true
console.log(cat instanceof Cat); // false
```

组合继承
```
核心：通过调用父类构造，继承父类的属性并保留传参的优点，然后通过将父类实例作为子类原型，实现函数复用

function Cat(name){
  Animal.call(this);
  this.name = name || 'Tom';
}
Cat.prototype = new Animal();

// 感谢 @学无止境c 的提醒，组合继承也是需要修复构造函数指向的。

Cat.prototype.constructor = Cat;

// Test Code
var cat = new Cat();
console.log(cat.name);
console.log(cat.sleep());
console.log(cat instanceof Animal); // true
console.log(cat instanceof Cat); // true
```

寄生组合继承
```
核心：通过寄生方式，砍掉父类的实例属性，这样，在调用两次父类的构造的时候，就不会初始化两次实例方法/属性，避免的组合继承的缺点

function Cat(name){
  Animal.call(this);
  this.name = name || 'Tom';
}
(function(){
  // 创建一个没有实例方法的类
  var Super = function(){};
  Super.prototype = Animal.prototype;
  //将实例作为子类的原型
  Cat.prototype = new Super();
})();

// Test Code
var cat = new Cat();
console.log(cat.name);
console.log(cat.sleep());
console.log(cat instanceof Animal); // true
console.log(cat instanceof Cat); //true

```


19.js的设计模式

设计模式目的
>设计模式是为了更好的代码重用性，可读性，可靠性，可维护性。

设计六大原则
>单一职责原则

>里氏替换原则

>依赖倒转原则

>接口隔离原则

>最少知识原则(迪米特法则)

>开放封闭原则

设计模式分类

总体来说设计模式分为三大类：
>创建型模式，共五种：工厂方法模式、抽象工厂模式、单例模式、建造者模式、原型模式。

>结构型模式，共七种：适配器模式、装饰器模式、代理模式、外观模式、桥接模式、组合模式、享元模式。

>行为型模式，共十一种：策略模式、模板方法模式、观察者模式、迭代子模式、责任链模式、命令模式、备忘录模式、状态模式、访问者模式、中介者模式、解释器模式。
 
>https://juejin.im/entry/6844903469397049352

20.es6 get，set的使用
>get和set我个人理解本身只是一个语法糖，它定义的属性相当于“存储器属性”,为内部属性提供了一个方便习惯的读/写方式

迭代器（Iterator）与生成器（Generator）
>https://segmentfault.com/a/1190000010747122

21.prototype与__proto__的区别
>每个实例对象（ object ）都有一个私有属性（称之为 __proto__ ）指向它的构造函数的原型对象（prototype ）

>对象有属性__proto__,指向该对象的构造函数的原型对象。

>方法除了有属性__proto__,还有属性prototype，prototype指向该方法的原型对象。

总结：
>所有对象都有__proto__属性。

>只有函数对象才有prototype属性。

>protoype对象默认有两个属性：constructor 和 proto。

>实例对象的__proto__指向的是函数的protoype

>函数对象的prototype属性是外部共享的，而__proto__是隐式的。

>函数和Object的__proto__的顶端是null

22.http的属性以及https的区别 
>https协议需要到ca申请证书，一般免费证书较少，因而需要一定费用。

>http是超文本传输协议，信息是明文传输，https则是具有安全性的ssl加密传输协议。

>http和https使用的是完全不同的连接方式，用的端口也不一样，前者是80，后者是443。

>http的连接很简单，是无状态的；HTTPS协议是由SSL+HTTP协议构建的可进行加密传输、身份认证的网络协议，比http协议安全。

https的优缺点：
>SEO方面，有利有弊，好处是搜索靠前，缺点是加载时长比较长

安全性,比http更加安全
>使用HTTPS协议可认证用户和服务器，确保数据发送到正确的客户机和服务器；

>HTTPS协议是由SSL+HTTP协议构建的可进行加密传输、身份认证的网络协议，要比http协议安全，可防止数据在传输过程中不被窃取、改变，确保数据的完整性。

>HTTPS是现行架构下最安全的解决方案，虽然不是绝对安全，但它大幅增加了中间人攻击的成本。

SSL的作用
>认证用户和服务器，确保数据发送到正确的客户机和服务器；
 
>加密数据以防止数据中途被窃取；
 
>维护数据的完整性，确保数据在传输过程中不被改变。

22.仓库的概念与使用
>仓库（repository）:文件存储的实际位置。分为本地和远程。通常理解为本地仓库为各个开发人员的本地文件位置。远程仓库是存储所有人工作的地方。

23.CSR 和 SSR 的区别

服务端渲染(SSR)和客户端(CSR)
>CSR：Client side render

>SSR：Server side render

优化首屏加载，减少白屏时间，提升加载性能：
>加速或减少HTTP请求损耗：使用CDN加载公用库，
>
>使用强缓存和协商缓存，使用域名收敛，
>
>小图片使用Base64代替，
>
>使用Get请求代替Post请求，
>
>设置 Access-Control-Max-Age 减少预检请求，
>
>页面内跳转其他域名或请求其他域名的资源时使用浏览器prefetch预解析等；

>延迟加载：非重要的库、非首屏图片延迟加载，SPA的组件懒加载等；

>减少请求内容的体积：开启服务器Gzip压缩，JS、CSS文件压缩合并，减少cookies大小，SSR直接输出渲染后的HTML等；

>浏览器渲染原理：优化关键渲染路径，尽可能减少阻塞渲染的JS、CSS；

>优化用户等待体验：白屏使用加载进度条、loading图、骨架屏代替等；
 
强缓存和协商缓存
>强缓存是利用http头中的Expires和Cache-Control两个字段来控制的，用来表示资源的缓存时间
>协商缓存：浏览器第一次请求一个资源的时候，服务器返回的header中会加上Last-Modify，Last-modify是一个时间标识该资源的最后修改时间；当浏览器再次请求该资源时，request的请求头中会包含If-Modify-Since，该值为缓存之前返回的Last-Modify。服务器收到If-Modify-Since后，根据资源的最后修改时间判断是否命中缓存；其中Etag：web服务器响应请求时，告诉浏览器当前资源在服务器的唯一标识
>Access-Control-Max-Age：缓存可以被缓存的时间

DNS 预解析：浏览器会在加载网页时对网页中的域名进行解析缓存，这样在你单击当前网页中的连接时就无需进行DNS的解析，减少用户等待时间，提高用户体验。

```
<link rel="dns-prefetch" href="www.ytuwlg.iteye.com" />

Gzip页面压缩，像服务器发送压缩文件，同时服务器需要设置解析
```

>https://www.jianshu.com/p/55a445193118
>https://juejin.im/post/6844904052589854728

24.构造函数

构造函数的三大特点：
>构造函数的函数名的第一个字母通常大写。

>函数体内使用this关键字，代表所要生成的对象实例。

>生成对象的时候，必须使用new命令来调用构造函数。

>https://juejin.im/entry/6844903456478593031

25.this指向问题
>this永远指向一个对象；

>this的指向完全取决于函数调用的位置；

26.基于防抖和节流的性能优化

防抖
>防抖就是指触发事件后在 n 秒内函数只能执行一次，如果在 n 秒内又触发了事件，则会重新计算函数执行时间。

```
var box = document.getElementById('box');
box.onmousemove = debounce(mouseMove, 1000);

function mouseMove(event) {
    console.log(event.clientX)
}

function debounce(fn, wait) {
    let timer = null;
    return function () {
        var args = arguments;
        timer && clearTimeout(timer);
        timer = setTimeout(() => {
            fn.apply(this, args);
        }, wait)
    }
}
```

节流
>节流就是指连续触发事件，但是在一段时间中只执行一次函数。
```
var box = document.getElementById('box');
box.onmousemove = throttle(mouseMove, 1000);

function mouseMove(event) {
    console.log(event.clientX)
}

function throttle(fn, wait) {
    var last = 0;
    return function () {
        var args = arguments;
        var now = Date.now();
        if (now - last > wait) {
            fn.apply(this, args);
            last = now;
        }
    }
}
```

27.数据响应式原理剖析

>https://juejin.im/post/6884490483624574990

28.基于Web Component的组件化开发
>https://juejin.im/post/6844904197654052877
>https://jishuin.proginn.com/p/763bfbd30446

29.柯里化
>把接受多个参数的函数变换成接受一个单一参数（最初函数的第一个参数）的函数，并且返回接受余下的参数而且返回结果的新函数，在某些编程语言中（如 Haskell），是通过 Currying 技术支持多参函数这一语言特性的。
>所以 Currying 原本是一门编译原理层面的技术，用途是实现多参函数。

>https://zh.javascript.info/currying-partials

30.正则
/[1-9][0-9]*/
