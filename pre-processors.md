# 预处理器

该模板已经预先配置好了最流行的几个css预处理器，包括LESS, SASS, Stylus, 和 PostCSS。使用时只需要安装相应的webpack loader就可以了。例如，如果使用SASS的话：

``` bash
npm install sass-loader node-sass --save-dev
```

注意你还需要安装`node-sass`，因为`sass-loader`是依赖于它的。

### 在组件中使用预处理器

安装了之后，你就可以在`*.vue`的组件中使用预处理器了，在`<style>` 标签上添加`lang`属性：

``` html
<style lang="scss">
/* write SASS! */
</style>
```

###  SASS 语法提示

- `lang="scss"` 对应的是CSS-超集语法（带有花括号和分号）
- `lang="sass"` 对应的是基于缩进的语法.

### PostCSS

`*.vue`文件中的样式默认都是经过PostCSS处理的，所以你不需要再用专门的loader了。直接在`build/webpack.base.conf.js`文件的`vue`块下面添加PostCSS插件就可以了：

``` js
// build/webpack.base.conf.js
module.exports = {
  // ...
  vue: {
    postcss: [/* your plugins */]
  }
}
```

查看 [vue-loader的相关文档](http://vuejs.github.io/vue-loader/en/features/postcss.html) 获取更多细节。

### 单独的 CSS 文件


为了确保一致的抽取和处理，强烈建议在根组件`App.vue`里引用全局的单独的样式文件。例如：

``` html
<!-- App.vue -->
<style src="./styles/global.less" lang="less"></style>
```

注意这种引用方法应该只适用于那些你自己写的样式文件。对于已经存在的库文件，例如Bootstrap或者Semantic UI这种，你可以放在 `/static`文件夹下，然后直接在`index.html`里引用它们。这样避免额外的构建时间，并且对于浏览器缓存来说会更好一些。(查看 [静态资源处理](static.md))
