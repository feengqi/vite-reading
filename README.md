# 阅读vite

## npm init vite 执行了什么

> npm init <initializer> 通常被用于创建一个新的或者已经存在的 npm 包。

在官方文档中：

``` shell
npm init [--force|-f|--yes|-y|--scope]
npm init <@scope> (same as `npx <@scope>/create`)
npm init [<@scope>/]<name> (same as `npx [<@scope>/]create-<name>`)
```

可以使用 `npm init <initializer>` 设置新的或现有的npm包。 `initializer`是一个名为 `create-<initializer>` 的 `npm` 包，它将由 `npx` 安装，然后执行 `package.json` 中 `bin` 属性对应的脚本，会创建或更新 package.json 并运行一些与初始化相关的操作。

init命令转换为相应的npx操作，如下所示：

-   `npm init foo` -> `npx create-foo`
-   `npm init @usr/foo` -> `npx @usr/create-foo`
-   `npm init @usr` -> `npx @usr/create`

由此可知
```shell
npm init vite
```
会转换成
```shell
npx create-vite
```
会安装 `create-vite` 包，然后执行 `package.json` 中 `bin` 属性对应的脚本。脚本指向 `src/index.ts` ，执行内部的 `init` 方法。
