# 项目结构

``` bash
.
├── build/                      # webpack 配置文件
│   └── ...
├── config/
│   ├── index.js                # 主要的项目配置
│   └── ...
├── src/
│   ├── main.js                 # app 入口文件
│   ├── App.vue                 # main app 组件
│   ├── components/             # ui组件
│   │   └── ...
│   └── assets/                 # 模块资源（由webpack进行处理）
│       └── ...
├── static/                     # 纯静态资源 (直接拷贝)
├── test/
│   └── unit/                   # 单元测试
│   │   ├── specs/              # 测试规格文件
│   │   ├── index.js            # 测试构建入口文件
│   │   └── karma.conf.js       # 测试运行器配置文件
│   └── e2e/                    # e2e测试
│   │   ├── specs/              # 测试规格文件
│   │   ├── custom-assertions/  # e2e测试的自定义断言
│   │   ├── runner.js           # 测试运行器脚本
│   │   └── nightwatch.conf.js  # 测试运行器配置文件
├── .babelrc                    # babel配置
├── .postcssrc.js               # postcss 配置
├── .eslintrc.js                # eslint 配置
├── .editorconfig               # editor 配置
├── index.html                  # index.html 模板
└── package.json                # 构建脚本和依赖
```

### `build/`

该目录包含了开发环境和生产环境的webpack构建配置。通常你不需要改动这些文件，如果想要自定义Webpack loaders，可以查看`build/webpack.base.conf.js`这个文件。

### `config/index.js`

该文件暴露出了一些最通用的构建安装配置选项，是主要配置文件。更多细节请查看[开发环境API Proxying](proxy.md)和[后端框架集成](backend.md)。

### `src/`

你的应用的大多数代码都应该放在这里。至于里面的文件结构是什么样的，还需要你自己好好策划一下。如果你正在使用Vuex，可以参考vuex示例项目里的结构[Vuex应用推荐](http://vuex.vuejs.org/en/structure.html)。

### `static/`

这里放的是那些你不想让Webpack接管的文件。它们会被直接拷贝到webpack构建assets所生成的路径下面。

查看 [处理静态资源](static.md)获取更多细节。

### `test/unit`

包含单元测试相关的文件。查看 [单元测试](unit.md) 获取更多细节。

### `test/e2e`

 包含e2e测试相关的文件。查看 [e2e测试](e2e.md) 获取更多细节。

### `index.html`

这就是我们单页面应用的**模板** `index.html`文件。在开发和构建过程中，Webpack会生成静态资源，并且引用这些静态资源的URL会被自动地添加到这个模板里，渲染出最终的HTML。

### `package.json`

NPM打包元文件，包含所有的构建依赖和[构建指令](commands.md).
