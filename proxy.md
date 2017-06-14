# 开发环境API Proxying

当和一个已经存在的后端进行模板整合的时候，一个常见的需求就是当使用dev server的时候能后获取后端API。为了实现，我们可以并行的（或者远程的）运行dev server和API后端，然后让dev server代理所有的通往真实后端的API请求。

编辑`config/index.js`里面的`dev.proxyTable`来配置代理规则。dev server用的是[http-proxy-middleware](https://github.com/chimurai/http-proxy-middleware)进行的代理，所以你应该去看一下它的文档查看更细节的使用方法。但这里给出了一个简单的例子：

``` js
// config/index.js
module.exports = {
  // ...
  dev: {
    proxyTable: {
      // proxy all requests starting with /api to jsonplaceholder
      '/api': {
        target: 'http://jsonplaceholder.typicode.com',
        changeOrigin: true,
        pathRewrite: {
          '^/api': ''
        }
      }
    }
  }
}
```
上面的例子将会把`/api/posts/1`请求代理到`http://jsonplaceholder.typicode.com/posts/1`

## URL Matching

除了静态url之外你也可以使用glob模式去匹配URL，例如`/api/**`。查看 [Context Matching](https://github.com/chimurai/http-proxy-middleware#context-matching) 获取更多细节。还有，你可以提供一个`filter`选项，成为一个定制的方法，来决定一个请求是否应该被代理。


``` js
proxyTable: {
  '*': {
    target: 'http://jsonplaceholder.typicode.com',
    filter: function (pathname, req) {
      return pathname.match('^/api') && req.method === 'GET'
    }
  }
}
```
