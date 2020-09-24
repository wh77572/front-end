#### css:
1. 盒子模型

> 盒模型分为两类: IE盒模型和标准盒模型。 两者的区别在于:

> IE盒模型的width/height = content + border + padding

> 标准盒模型的width/height = content

> https://www.cnblogs.com/chengzp/p/cssbox.html

2. flex原理  

> Flexible Box 模型，通常被称为 flexbox，是一种一维的布局模型。

> 我们说 flexbox 是一种一维的布局，是因为一个 flexbox 一次只能处理一个维度上的元素布局，一行或者一列。作为对比的是另外一个二维布局 CSS Grid Layout，可以同时处理行和列上的布局。

> https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox

3. 垂直居中居中方式

> 区分行内元素以及块级元素

> http://www.cnblogs.com/hutuzhu/p/4450850.html 

4. CSS优先级算法如何计算？

> 优先级就近原则，同权重情况下样式定义最近者为准

> 载入样式以最后载入的定位为准

> 优先级为: !important > id > class > tag; !important比 内联优先级高

5. CSS3有哪些新特性

> 新增各种css选择器

> 圆角 border-radius

> 多列布局

> 阴影和反射

> 文字特效text-shadow

> 线性渐变

> 旋转transform

CSS3新增伪类有那些？

> :after在元素之前添加内容,也可以用来做清除浮动。

> :before在元素之后添加内容。

> :enabled已启用的表单元素。

> :disabled已禁用的表单元素。

> :checked单选框或复选框被选中。

6. CSS常用选择器, 哪些属性可以继承？

CSS选择符：

> id选择器(#myid)

> 类选择器(.myclassname)

> 标签选择器(div, h1, p)

> 相邻选择器(h1 + p)

> 子选择器（ul > li）

> 后代选择器（li a）

> 通配符选择器（*）

> 属性选择器（`a[rel="external"]`）

> 伪类选择器（`a:hover, li:nth-child`）

> 可继承的属性：font-size, font-family, color

> 不可继承的样式：border, padding, margin, width, height

7. 如何创建块级格式化上下文(block formatting context),BFC有什么用

> 什么是BFC?

> BFC格式化上下文，它是一个独立的渲染区域，让处于 BFC内部的元素和外部的元素相互隔离，使内外元素的定位不会相互影响

> 如何产生BFC?

> display: inline-block

> position: absolute/fixed

> BFC作用

> BFC最大的一个作用就是：在页面上有一个独立隔离容器，容器内的元素和容器外的元素布局不会相互影响

> 解决上外边距重叠;重叠的两个box都开启bfc;

> 解决浮动引起高度塌陷;容器盒子开启bfc

> 解决文字环绕图片;左边图片div,右边文字容器p,将p容器开启bfc


> BFC （块级格式化上下文），是一个独立的渲染区域，让处于 BFC 内部的元素与外部的元素相互隔离，使内外元素的定位不会相互影响。

触发条件:

> 根元素

> position: absolute/fixed

> display: inline-block / table

> float 元素

> ovevflow !== visible

规则:

> 属于同一个 BFC 的两个相邻 Box 垂直排列

> 属于同一个 BFC 的两个相邻 Box 的 margin 会发生重叠

> BFC 的区域不会与 float 的元素区域重叠

> 计算 BFC 的高度时，浮动子元素也参与计算

> 文字层不会被浮动层覆盖，环绕于周围

bfc  

> https://www.cnblogs.com/zczhangcui/p/6081574.html  

> http://chenhaizhou.github.io/2015/01/14/bfc.html

8. 绝对定位和相对定位的区别

position: absolute

> 绝对定位：绝对定位是相对于元素最近的已定位的祖先元素（即是设置了绝对定位或者相对定位的祖先元素）。如果元素没有已定位的祖先元素，那么它的位置则是相对于最初的包含块（body）。

position: relative

> 相对定位：相对定位是相对于元素在文档中的初始位置


9. display:inline-block什么时候不会显示间隙？

> 间隙是由空白符（white space）造成的, 可能使用了空格、换行、tab、换页等

> 移除空格

> 使用margin负值

> 使用font-size:0

> letter-spacing

> word-spacing

> https://github.com/XXHolic/blog/issues/13

10. 清除浮动的几种方式，各自的优缺点

> 父级div定义height

> 结尾处加空div标签clear:both

> 父级div定义伪类:after和zoom

> 父级div定义overflow:hidden

> 父级div也浮动，需要定义宽度

> 结尾处加br标签clear:both

> 比较好的是第3种方式，好多网站都这么用

11. CSS3中translate、transform和translation的区别和联系

translate:移动，是transform的一个方法。

> 通过 translate() 方法，元素从其当前位置移动，根据给定的 left（x 坐标） 和 top（y 坐标） 位置参数：

> `transform: translate(50px, 100px);`

> `-ms-transform: translate(50px,100px);`

> `-webkit-transform: translate(50px,100px);`

> `-o-transform: translate(50px,100px);`

> `-moz-transform: translate(50px,100px);`

transform:变形。改变

> CSS3中主要包括 旋转：rotate() 顺时针旋转给定的角度，允许负值 rotate(30deg)

> 扭曲：skew() 元素翻转给定的角度,根据给定的水平线（X 轴）和垂直线（Y 轴）参数：skew(30deg,20deg)

> 缩放：scale() 放大或缩小，根据给定的宽度（X 轴）和高度（Y 轴）参数： scale(2,4)

> 移动：translate() 平移，传进 x,y值，代表沿x轴和y轴平移的距离

transition: 允许CSS属性值在一定的时间区间内平滑的过渡

> 需要事件的触发，例如单击、获取焦点、失去焦点等.

> 例如：transition:width 2s ease 0s;

> `transition:property duration timing-function delay;`

> property:CSS的属性，例如：width height 为none时停止所有的运动，可以为transform

> duration:持续时间

> timing-function:ease等

> delay:延迟

CSS3动画（简单动画的实现，如旋转等）

> 依靠CSS3中提出的三个属性：transition、transform、animation

> transition：定义了元素在变化过程中是怎么样的，包含transition-property、transition-duration、transition-timing-function、transition-delay。

> transform：定义元素的变化结果，包含rotate、scale、skew、translate。

> animation：动画定义了动作的每一帧（@keyframes）有什么效果，包括animation-name，animation-duration、animation-timing-function、animation-delay、animation-iteration-count、> animation-direction

> https://www.jianshu.com/p/1376b76a3b90

12. 为什么要初始化CSS样式?

> 因为浏览器的兼容问题，不同浏览器对有些标签的默认值是不同的，如果没对CSS初始化往往会出现浏览器之间的页面显示差异。

> 当然，初始化样式会对SEO有一定的影响，但鱼和熊掌不可兼得，但力求影响最小的情况下初始化

13. position有哪些值？有什么作用？

> static。默认值，不脱离文档流，top，right，bottom，left等属性不生效。

> relative。不脱离文档流，依据自身位置进行偏离，当子元素设置absolute，将依据它进行偏离。

> absolute。脱离文档流，依据top，right，bottom，left等属性在正常文档流中偏移位置。

> fixed。通过浏览器窗口进行定位，出现滚动条的时候，不会随之滚动。

13. Flex布局

> display: flex  //设置Flex模式

> flex-direction: column  //决定元素是横排还是竖着排

> flex-wrap: wrap     //决定元素换行格式

> justify-content: space-between  //同一排下对齐方式，空格如何隔开各个元素

> align-items: center     //同一排下元素如何对齐

> align-content: space-between    //多行对齐方式

flex:1;详解:

> https://www.jianshu.com/p/57a94430dcbe

14. CSS优先级算法如何计算？

选择器的优先级

> ID选择器>class选择器>标签选择器

> css权重计算方法(有时套用的选择器过于繁琐，并不知道优先级的高低)

> 内联样式，如: style=””，权值为1000。

> ID选择器，如：#content，权值为100。

> 类，伪类和属性选择器，如.content，权值为10。

> 标签选择器和伪元素选择器，如div p，权值为1。    

复合选择器的权重计算：
 
> 将基本选择器的权重相加之和，就是权重大小，值越大，权重越高

example：

> div  li a ：1+1+1=3 

> .box  li  a : 10+1+1=12 

> #box  li   a : 100+1+1=102

实例：

> #box ul li a.cur  {color:red;}  权重是  100+1+1+1+10 = 113

> #box li .cur {color:green;}  权重是  100+1+10  = 111   

> 那么后面的样式就会被前面的样式层叠掉,那么最终a的颜色是red

15. CSS3新增伪类有那些?

> p:first-of-type 选择属于其父元素的首个元素

> p:last-of-type 选择属于其父元素的最后元素

> p:only-of-type 选择属于其父元素唯一的元素

> p:only-child 选择属于其父元素的唯一子元素

> p:nth-child(2) 选择属于其父元素的第二个子元素

> :enabled :disabled 表单控件的禁用状态。

> :checked 单选框或复选框被选中。

16、常用的 CSS 预处理器是什么？有什么特点？（先谈stylus/sass/less区别）

均具有“变量”、“混合”、“嵌套”、“继承”、“颜色混合”五大基本特性

> Scss和LESS语法较为严谨，LESS要求一定要使用大括号“{}”，Scss和Stylus可以通过缩进表示层次与嵌套关系

> Scss无全局变量的概念，LESS和Stylus有类似于其它语言的作用域概念

> Sass是基于Ruby语言的，而LESS和Stylus可以基于NodeJS NPM下载相应库后进行编译；

17. 知道css有个content属性吗？有什么作用？有什么应用？

> css的content属性专门应用在 before/after伪元素上，用于来插入生成内容。最常见的应用是利用伪类清除浮动。

18. CSS在性能优化方面的实践

>css压缩与合并、Gzip压缩

>css文件放在head里、不要用@import

>尽量用缩写、避免用滤镜、合理使用选择器

19.CSS的解析顺序是什么?浏览器是怎样解析CSS选择器的？

> CSS选择器的解析是从右向左解析的。若从左向右的匹配，发现不符合规则，需要进行回溯，会损失很多性能。若从右向左匹配，先找到所有的最右节点，对于每一个节点，向上寻找其父节点直到找到根元素或满足条件的> 匹配规则，则结束这个分支的遍历。两种匹配规则的性能差别很大，是因为从右向左的匹配在第一步就筛选掉了大量的不符合条件的最右节点（叶子节点），而从左向右的匹配规则的性能都浪费在了失败的查找上面。
> 而在 CSS 解析完毕后，需要将解析的结果与 DOM Tree 的内容一起进行分析建立一棵 Render Tree，最终用来进行绘图。在建立 Render Tree 时（WebKit 中的「Attachment」过程），浏览器就要为每个
> DOM Tree 中的元素根据 CSS 的解析结果（Style Rules）来确定生成怎样的 Render Tree。

20. px，em，rem的区别是什么，应用场景有哪些？

21. 手机端有哪些适配方案？

22. ::before 和 :after中双冒号和单冒号有什么区别？

> 单冒号(:)用于CSS3伪类，双冒号(::)用于CSS3伪元素。

> ::before就是以一个子元素的存在，定义在元素主体内容之前的一个伪元素。并不存在于dom之中，只存在在页面之中。

> :before 和 :after 这两个伪元素，是在CSS2.1里新出现的。起初，伪元素的前缀使用的是单冒号语法，但随着Web的进化，在CSS3的规范里，伪元素的语法被修改成使用双冒号，成为::before ::after



> 验证css传送门  
http://www.w3school.com.cn/tiy/t.asp?f=csse_selector_child
