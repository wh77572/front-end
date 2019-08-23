# front-end
整理的一些前端资料 . 

#### html:
 > html5的新特性 . 
 
 > 行内元素，块级元素等等 . 
 
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
