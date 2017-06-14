# SEO预渲染


如果布到生产环境后预渲染路由不会明显的变化，就使用这个经过测试的适用于Vue的插件：[prerender-spa-plugin](https://www.npmjs.com/package/prerender-spa-plugin)。对于那些确实频繁变化的页面，[Prerender.io](https://prerender.io/) 和 [Netlify](https://www.netlify.com/pricing) 都提供了常规的对于搜索引擎预渲染的方案。

## 使用 `prerender-spa-plugin`

1. 作为一个dev依赖进行安装:

```bash
npm install --save-dev prerender-spa-plugin
```

2. 在**build/webpack.prod.conf.js**引用进来:

```js
// This line should go at the top of the file where other 'imports' live in
var PrerenderSpaPlugin = require('prerender-spa-plugin')
```

3. 在`plugins` 数组进行配置 (也在 **build/webpack.prod.conf.js** 里):

```js
new PrerenderSpaPlugin(
  // Path to compiled app
  path.join(__dirname, '../dist'),
  // List of endpoints you wish to prerender
  [ '/' ]
)
```

如果你也想预渲染 `/about` and `/contact`, 那么数组是 `[ '/', '/about', '/contact' ]`.

4. 为`vue-router`开启history mode:

```js
const router = new VueRouter({
  mode: 'history',
  routes: [...]
})
```
