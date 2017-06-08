# Prerendering for SEO


如果布到生产环境后预渲染路由不会明显的变化，就使用这个经过测试的适用于Vue的插件：[prerender-spa-plugin](https://www.npmjs.com/package/prerender-spa-plugin)。对于那些确实频繁变化的页面，[Prerender.io](https://prerender.io/) 和 [Netlify](https://www.netlify.com/pricing) 都提供了常规的对于搜索引擎预渲染的方案。

## Using `prerender-spa-plugin`

1. Install it as a dev dependency:

```bash
npm install --save-dev prerender-spa-plugin
```

2. Require it in **build/webpack.prod.conf.js**:

```js
// This line should go at the top of the file where other 'imports' live in
var PrerenderSpaPlugin = require('prerender-spa-plugin')
```

3. Configure it in the `plugins` array (also in **build/webpack.prod.conf.js**):

```js
new PrerenderSpaPlugin(
  // Path to compiled app
  path.join(__dirname, '../dist'),
  // List of endpoints you wish to prerender
  [ '/' ]
)
```

If you also wanted to prerender `/about` and `/contact`, then that array would be `[ '/', '/about', '/contact' ]`.

4. Enable history mode for `vue-router`:
```js
const router = new VueRouter({
  mode: 'history',
  routes: [...]
})
```
