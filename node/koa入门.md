#Koa入门

##Koa是什么
koa是Express的下一代基于Node.js的web框架.由 Express 幕后的原班人马打造， 致力于成为 web 应用和 API 开发领域中的一个更小、更富有表现力、更健壮的基石。


##Koa优势
Koa 就是一种简单好用的 Web 框架。它的特点是优雅、简洁、表达力强、自由度高。本身代码只有1000多行，所有功能都通过插件实现，很符合 Unix 哲学。

>Express基于ES5的语法，使用传统的回调方式来实现异步代码。如果异步嵌套层次过多，书写便利性和可维性就较低。<br>
Koa目前有1.x和2.0两个版本。koa1基于es6,koa2基于es7。koa 1.0使用generator实现异步，koa2完全使用Promise并配合async来实现异步。（目前koa2仍支持generator的写法，但下一个版本将会去掉）

*(接下来内容中默认版本为Koa2)*

##Hello Word
```
// 导入koa
const Koa = require('koa');

// 创建一个Koa对象表示web app本身
const app = new Koa();

// 对于任何请求，app将调用该异步函数处理请求
app.use(async (ctx, next) => {
    await next();
    ctx.response.type = 'text/html';
    ctx.response.body = '<h1>Hello, Word</h1>';
});

// 在端口3000监听:
app.listen(3000);
console.log('app started at port 3000...');
```

##上下文(Context)
Koa 提供一个 Context 对象，表示一次对话的上下文（包括 HTTP 请求和 HTTP 回复）。通过加工这个对象，就可以控制返回给用户的内容。<br>

在上面的Hello Word示例代码中的ctx，Context.response.body属性就是发送给用户的内容；ctx.response代表 HTTP Response。同样地，ctx.request代表 HTTP Request。<br>
Koa Context 将 node 的 request 和 response 对象封装到单个对象中，为编写 Web 应用程序和 API 提供了许多有用的方法。

>[更多Context API详情](https://koa.bootcss.com/#context)

##路由
###原生路由
可以通过ctx.request.path可以获取用户请求的路径，由此实现简单的路由。示例代码：
```
const Koa = require('koa');
const app = new Koa();

const main = ctx => {
  if (ctx.request.path !== '/') {
    ctx.response.type = 'html';
    ctx.response.body = '<a href="/">Index Page</a>';
  } else {
    ctx.response.body = 'Hello World';
  }
};

app.use(main);
app.listen(3000);
```

###koa-route
原生路由用起来不太方便，可以使用封装好的koa-route模块，让它负责处理URL映射。示例：
```
const Koa = require('koa');
const route = require('koa-route');
const app = new Koa();

const about = ctx => {
  ctx.response.type = 'html';
  ctx.response.body = '<a href="/">Index Page</a>';
};

const main = ctx => {
  ctx.response.body = 'Hello World';
};

app.use(route.get('/', main));
app.use(route.get('/about', about));

app.listen(3000);
```

###重定向
有时我们会用到重定向功能，比如，用户登陆以后，将他重定向到登陆前的页面。
```
const Koa = require('koa');
const route = require('koa-route');
const app = new Koa();

const redirect = ctx => {
  ctx.response.redirect('/');
};

const main = ctx => {
  ctx.response.body = 'Hello World';
};

app.use(route.get('/', main));
app.use(route.get('/redirect', redirect));

app.use(main);
app.listen(3000);
```

##中间件（middleware）
###什么是中间件
示例：日志中间件logger
```
const Koa = require('koa');
const app = new Koa();

const logger = (ctx, next) => {
  console.log(`${Date.now()} ${ctx.request.method} ${ctx.request.url}`);
  next();
}

const main = ctx => {
  ctx.response.body = 'Hello World';
};

app.use(logger);
app.use(main);
app.listen(3000);
```

如上面代码所示，logger函数就叫做"中间件"（middleware），因为它处在 HTTP Request 和 HTTP Response 中间，用来实现某种中间功能。使用app.use()用来加载中间件。<br>

基本上，Koa 所有的功能都是通过中间件实现的，每个中间件默认接受两个参数，第一个参数是 Context 对象，第二个参数是next函数。只要调用next函数，就可以把执行权转交给下一个中间件。

###处理链
如果存在多个中间件，会形成一个栈结构，以"先进后出"的顺序执行。middleware的顺序很重要，也就是调用app.use()的顺序决定了middleware的顺序。

以下用示例展示：
```
const Koa = require('koa');
const app = new Koa();

const one = (ctx, next) => {
  console.log('>> 1');
  next();
  console.log('<< 1');
}

const two = (ctx, next) => {
  console.log('>> 2');
  next();
  console.log('<< 2');
}

const three = (ctx, next) => {
  console.log('>> 3');
  next();
  console.log('<< 3');
}

app.use(one);
app.use(two);
app.use(three);

app.listen(3000);
```
执行之后，输出结果：
```
>> 1
>> 2
>> 3
<< 4
<< 2
<< 1
```
示例代码中，用next()来实现调用下一个middleware。那假如一个middleware没有调用next()，会怎么样？答案是后续的middleware将不再执行了。<br>
>上面示例的middleware是同步的，也可以用async 函数来书写异步middleware

###组合
可以使用koa-compose模块可以将多个中间件组合成一个。
```
const Koa = require('koa');
const compose = require('koa-compose');
const app = new Koa();

const logger = (ctx, next) => {
  console.log(`${Date.now()} ${ctx.request.method} ${ctx.request.url}`);
  next();
}

const main = ctx => {
  ctx.response.body = 'Hello World';
};

const middlewares = compose([logger, main]);

app.use(middlewares);
app.listen(3000);
```

##其它参考
* [koa中文文档](https://github.com/demopark/koa-docs-Zh-CN)
* [Koa Examples](https://github.com/koajs/examples)
