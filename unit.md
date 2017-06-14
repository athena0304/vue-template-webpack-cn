# 单元测试

该模板使用的单元测试总览：

- [Karma](https://karma-runner.github.io/): 测试运行器，启动浏览器运行测试然后向我们报告结果。
- [karma-webpack](https://github.com/webpack/karma-webpack): Karma的插件，使用Webpack将我们的测试进行打包
- [Mocha](https://mochajs.org/): 用来写测试规格的测试框架。
- [Chai](http://chaijs.com/): 提供更好的断言语法的断言库。
- [Sinon](http://sinonjs.org/): 测试工具库，提供spies, stubs 和 mocks。

Chai and Sinon整合在了[karma-sinon-chai](https://github.com/kmees/karma-sinon-chai)，所以所有的Chai界面（`should`, `expect`, `assert`）和`sinon`在测试文件中都是全局可用的。

关于文件:

- `index.js`


  使用了`karma-webpack`打包所有的测试代码和源码（为了覆盖）的入口文件。在大多数情况都可以忽略它。

- `specs/`

  这里就是你实际写测试的地方。你可以完全使用ES2015+和所有支持的Webpack loaders。

- `karma.conf.js`

  这是Karma配置文件。查看[Karma docs](https://karma-runner.github.io/) 获取更多细节。

## 在更多的浏览器里运行测试

你可以通过安装更多的[karma launchers](https://karma-runner.github.io/1.0/config/browsers.html)在多个真实的浏览器里运行测试，并且可以在`test/unit/karma.conf.js`调整 `browsers`部分


## Mocking Dependencies

This boilerplate comes with [inject-loader](https://github.com/plasticine/inject-loader) installed by default. For usage with `*.vue` components, see [vue-loader docs on testing with mocks](http://vue-loader.vuejs.org/en/workflow/testing-with-mocks.html).
