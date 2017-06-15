# 简介
【译者按】本文是根据[vuejs-templates-webpack官方文档](http://vuejs-templates.github.io/webpack/)原创翻译而来，有些语句或者一些专有名词如果翻译的不到位，欢迎大家提出来我好进行改正；还有一些关于测试的部分，由于个人在实际项目中还没用到，有些术语不太了解，有的就没有翻译，后期如果接触了了解了，再补齐吧；还有一些不知道怎么翻译的地方，我就换成了原文。

该模板是针对大型的严格的工程，并且要求你或多或少对webpack和`vue-loader`有一定的了解。一定也要也看一下[`vue-loader`的文档](http://vuejs.github.io/vue-loader/index.html) 来了解一下常规工作流方法。

如果你只想尝试一下`vue-loader`或者快速开始一个原型，那么用[webpack-simple](https://github.com/vuejs-templates/webpack-simple)就好。


## 快速开始

该模板是基于[vue-cli](https://github.com/vuejs/vue-cli)这个脚手架搭建的。**为了确保使用更有效的依赖树，强烈建议使用npm 3以上的版本。**

``` bash
$ npm install -g vue-cli
$ vue init webpack my-project
$ cd my-project
$ npm install
$ npm run dev
```
