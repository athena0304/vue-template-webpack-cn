# 静态资源处理

你可能已经注意到，在我们的项目结构里，有两个静态文件的路径，分别是：`src/assets` 和 `static/`。那这两个到底有什么区别呢？

### Webpacked 资源

为了回答这个问题，我们首先需要理解webpack是怎样处理静态资源的。在`*.vue`组件中，所有的templates和css都会被`vue-html-loader` 和 `css-loader`解析，寻找资源的URL。举个例子，在`<img src="./logo.png">` 和 `background: url(./logo.png)`, `"./logo.png"`中，都是相对资源路径，都会被**Webpack解析成模块依赖** 。

由于`logo.png`不是JavaScript，当被看成一个模块依赖的时候，我们需要使用`url-loader` 和 `file-loader`进行处理。
该模板已经配置好了这些loaders，所以你能够使用相对/模块路径时不需要担心部署的问题。
（This boilerplate has already configured these loaders for you, so you basically get features such as filename fingerprinting and conditional base64 inlining for free, while being able to use relative/module paths without worrying about deployment.）

由于这些资源可能在构建的时候被内联/复制/重命名， 所以它们从本质上来说是你源码的一部分。这就是为什么我们建议将交由webpack处理的静态资源和其它源文件一样放在`/src`路径下面。实际上，你甚至不需要把它们全都放在`/src/assets`路径下：你可以基于模块/组件的使用来组织文件结构。例如，你可以把每个组件和属于它的静态资源放在它自己的目录下。


### 资源处理规则

- **相对URL**, e.g. `./assets/logo.png` 将会被解释成一个模块依赖。它们会被一个基于你的Webpack输出配置自动生成的URL替代。

- **没有前缀的URL**, e.g. `assets/logo.png` 将会被看成相对URLs，并且转换`./assets/logo.png`

- **前缀带`~`的URL** 会被当成模块请求, 类似于`require('some-module/image.png')`. 如果你想要利用Webpack的模块处理配置，就可以使用这个前缀。例如，如果你有一个对于`assets`的路径解析，你需要使用`<img src="~assets/logo.png">`来确保解析是对应上的。

- **相对根目录的URL**, e.g. `/assets/logo.png` 是不会被处理的.

### 在JavaScript里获取资源路径

为了能让Webpack返回正确的资源路径，你需要使用`require('./relative/path/to/file.jpg')`，将会被`file-loader`处理，然后返回处理过的URL。例如：

``` js
computed: {
  background () {
    return require('./bgs/' + this.id + '.jpg')
  }
}
```

**注意上面的例子，在最终的构建时将会包含`./bgs/`路径下的所有图片** 这是因为Webpack不能猜出来在运行时它们当中的那个会被用到，所以会包含所有的。

### "真实的" 静态资源


作为对比，在`static/`下的文件都不会被Webpack处理：它们使用相同的文件名，直接拷贝到最终的路径。你必须使用绝对路径引用这些文件，取决于在`config.js`里面假如的`build.assetsPublicPath` and `build.assetsSubDirectory`

举个例子，下面的默认值是：

``` js
// config/index.js
module.exports = {
  // ...
  build: {
    assetsPublicPath: '/',
    assetsSubDirectory: 'static'
  }
}
```

所有放在 `static/`目录下的文件都应该是使用绝对URL`/static/[filename]`引用的。如果你将`assetSubDirectory`的值改成`assets`， 那么这些URL就会被变成 `/assets/[filename]`

在[backend integration](backend.md)章节我们会了解更多关于这个配置文件的内容。
