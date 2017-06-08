# 构建命令

所有的构建命令都是通过 [NPM Scripts](https://docs.npmjs.com/misc/scripts)执行的。

### `npm run dev`

> 开启了一个Node.js本地开发服务。 查看 [API Proxying During Development](proxy.md) 获取更多细节。

- 单文件Vue组件使用Webpack + `vue-loader`。
- State preserving hot-reload
- State preserving compilation error overlay
- Lint-on-save with ESLint
- Source maps

### `npm run build`

> 为生产构建资源. 查看 [Integrating with Backend Framework](backend.md) 获取更多细节。

- 使用[UglifyJS](https://github.com/mishoo/UglifyJS2)压缩Javascript.
- 使用[html-minifier](https://github.com/kangax/html-minifier)压缩HTML.
- 所有组件里的css都会被抽成一个单独的文件，然后使用[cssnano](https://github.com/ben-eb/cssnano)压缩.
- 为了更有效的长期缓存，所有的静态资源都被编译成版本哈希，并且产出的`index.html`里会自动生成这些静态资源URL的引入。

### `npm run unit`

> 运行单元测试，使用[Karma](https://karma-runner.github.io/)，基于PhantomJS。查看 [单元测试](unit.md) 获取更多信息

- Supports ES2015+ in test files.
- Supports all webpack loaders.
- Easy [mock injection](http://vuejs.github.io/vue-loader/en/workflow/testing-with-mocks.html).

### `npm run e2e`

> 运行端到端测试，使用 [Nightwatch](http://nightwatchjs.org/). 查看 [端到端测试](e2e.md) 获取更多细节


- Run tests in multiple browsers in parallel.
- Works with one command out of the box:
  - Selenium and chromedriver dependencies automatically handled.
  - Automatically spawns the Selenium server.
