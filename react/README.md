#### 库的使用:
react:  

1. redux原理  

2. 中间键  

3. 高阶组件  

4. 生命周期  

关于react引入antd没有样式问题.

> 在modules下面找到babel-loder，然后在options下面加上

`plugins: [
             ['import', { libraryName: 'antd', style: 'css' }],
          ]`

