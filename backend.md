# 后端框架集成

如果你做的是一个纯静态应用（和后端API分离部署），那么你甚至可能都不用编辑`config/index.js`。
然而，如果你想将这个模板迁移到一个已经存在的后端框架里，例如Rails/Django/Laravel，他们都有自己的项目结构，那么你可以编辑`config/index.js`，将生成前端的资源直接放进你后端的项目里。

让我们看一下默认的`config/index.js`:

``` js
// config/index.js
var path = require('path')

module.exports = {
  build: {
    index: path.resolve(__dirname, 'dist/index.html'),
    assetsRoot: path.resolve(__dirname, 'dist'),
    assetsSubDirectory: 'static',
    assetsPublicPath: '/',
    productionSourceMap: true
  },
  dev: {
    port: 8080,
    proxyTable: {}
  }
}
```

在`build`部分，我们有下面的选项：

### `build.index`

> 必须是你本地文件系统的绝对路径

这里就是`index.html`（有插入的资源URL）生成的地方.

如果你正在和一个后端框架一起使用这个模板，你可以相应地编辑`index.html`，然后将路径指到后端app渲染的view文件那里。例如`app/views/layouts/application.html.erb`是一个Rails app，或者`resources/views/index.blade.php`是一个Laravel app

### `build.assetsRoot`

> 必须是你本地系统里的绝对路径

这里应该指向的是整个项目下包含所有静态文件的根目录。例如Rails/Laravel的都是 `public/`

### `build.assetsSubDirectory`

(Nest webpack-generated assets under this directory in build.assetsRoot, so that they are not mixed with other files you may have in build.assetsRoot.)举个例子，如果你的 `build.assetsRoot`是`/path/to/dist`，然后`build.assetsSubDirectory`是`static`，那么所有的Webpack资源都会生成在`path/to/dist/static`。

每次构建的时候，这个目录都会被清空，所以它只应该包含由构建产生的资源文件。

在`static/`文件夹下面的文件在构建的时候也会被拷贝到这个目录下。也就是说如果你改了这个前缀，那么你所有的`static/`下面绝对路径引的URL也需要跟着一起改。查看[处理静态资源](static.md) 获取更多信息.

### `build.assetsPublicPath`

这里应该是你的`build.assetsRoot`将要通过HTTP服务的URL路径。在大多数情况，都应该会是根目录（`/`）。只有在你的后端框架服务静态资源时候有路径前缀的时候才需要修改。在内部，它会通过Webpack变成`output.publicPath`。

### `build.productionSourceMap`

生产环境构建是否生成source maps

### `dev.port`

指定dev服务所监听的端口。

### `dev.proxyTable`

定义dev服务的代理规则。查看[API Proxying During Development](proxy.md)获取更多细节。
