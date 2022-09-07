# 创建react项目的三种方式

## Table of Contents

  * [What is React](###What%20is%20React)
  * [html中直接引用](###html中直接引用)
  * [使用脚手架create-react-app](###使用脚手架create-react-app)
  * [使用webpack创建](###使用webpack创建)

### What is React
[From wikipedia](https://en.wikipedia.org/wiki/React_(JavaScript_library))
React (also known as React.js or ReactJS) is a free and open-source **front-end JavaScript library** for building user interfaces based on UI components. It is maintained by Meta (formerly Facebook) and a community of individual developers and companies.React can be used as <u>a base in the development of **single-page**, **mobile**, or **server-rendered** applications with frameworks like Next.js</u>. However, React is only concerned with **state management** and **rendering** that state to the DOM, so creating React applications usually requires the use of additional libraries for routing, as well as certain client-side functionality.

### html中直接引用

在一个标准html文件中直接应用react核心包。
> \<!-- 引入react -->
\<script src="https://unpkg.com/react@16/umd/react.development.js" crossorigin>\</script>
\<!-- 引入react-dom -->
\<script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js" crossorigin>\</script>

如果想要使用JSX语法，那么必须引入Babel。
> \<!-- 引入Babel,使浏览器可以识别JSX语法，如果不使用JSX语法，可以不引入 -->
\<script src="https://unpkg.com/babel-standalone@6/babel.min.js">\</script>

在body标签中创建Dom结构以及script标签，这里因为引入了babel,所以script标签的type必须是"text/babel"。
然后在scirpt中写React代码
> \<body>
  \<div id="app">\</div>
  \<script type="text/babel">
    // 必须添加type="text/babel",否则不识别JSX语法
    class App extends React.Component {
    render() {
      return(
        \<div>
          \<h1>Hello World\</h1>
        \</div>
      )
    }
  }
  ReactDOM.render(\<App />, document.getElementById('app'))
    \</script>
\</body>

[demo](../examples/create-react-app/html/index.html)

### 使用脚手架create-react-app

create-react-app 是官方提供的一种创建React单页应用的方法。[官方例子](https://www.html.cn/create-react-app/docs/getting-started/)

>npx create-react-app my-app
cd my-app
npm start

在npm 6+ 中可用
> npm init react-app my-app

在yarn 0.25+ 中可用
> yarn create react-app my-app

[demo](../examples/create-react-app/my-app/)

### 使用webpack创建
