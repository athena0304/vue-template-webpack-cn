# 环境变量


有时候需要根据应用运行的环境配置不同的东西。

例如:

```js
// config/prod.env.js
module.exports = {
  NODE_ENV: '"production"',
  DEBUG_MODE: false,
  API_KEY: '"..."' // 这个是所有环境共享的
}

// config/dev.env.js
module.exports = merge(prodEnv, {
  NODE_ENV: '"development"',
  DEBUG_MODE: true // 覆盖了prod.env的DEBUG_MODE的值
})

// config/test.env.js
module.exports = merge(devEnv, {
  NODE_ENV: '"testing"'
})
```

> **Note:** 字符串变量需要由单引号和双引号`'"..."'`包裹起来

所以，环境变量是：
- Production
    - NODE_ENV   = 'production',
    - DEBUG_MODE = false,
    - API_KEY    = '...'
- Development
    - NODE_ENV   = 'development',
    - DEBUG_MODE = true,
    - API_KEY    = '...'
- Testing
    - NODE_ENV   = 'testing',
    - DEBUG_MODE = true,
    - API_KEY    = '...'

可以看出来，`test.env`继承自`dev.env`， 而`dev.env`继承自`prod.env`

### 使用

在你的代码中使用环境变量很简单，例如：

```js
Vue.config.debug = process.env.DEBUG_MODE
```
