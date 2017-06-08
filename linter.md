# Linter 配置

This boilerplate uses [ESLint](http://eslint.org/) as the linter, and uses the [Standard](https://github.com/feross/standard/blob/master/RULES.md) preset with some small customizations.

该模板使用[ESLint](http://eslint.org/)作为提示检查器，并且使用[标准的](https://github.com/feross/standard/blob/master/RULES.md) 预设和一些小的定制。



如果你不满意默认的检验规则，有下面几个选择：

1. 重写`.eslintrc.js`里的自定义规则。例如，你可以添加下列规则来强制使用分号，而不是忽略分号。

  ``` js
  // .eslintrc.js
  "semi": [2, "always"]
  ```

2. 在生成项目的时候选择一个不同的ESLint预设，例如[eslint-config-airbnb](https://github.com/airbnb/javascript/tree/master/packages/eslint-config-airbnb).

3. 生成项目的时候不做ESLint预设，然后再顶你你自己的规则。查看 [ESLint 文档](http://eslint.org/docs/rules/) 获取更多细节。
