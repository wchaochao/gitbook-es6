# Babel

标签（空格分隔）： ES6

---

将ES6转换为ES5的转码器

* 语法转换
* API支持

## @babel/core

babel的核心库，根据配置转换代码

```bash
npm install --save-dev @babel/core
```

### babel API

```javascript
const babel = require('@babel/core')

// 字符串转码
babel.transform('code();', options)
// => { code, map, ast }

// 文件转码（异步）
babel.transformFile('filename.js', options, function(err, result) {
  result // => { code, map, ast }
})

// 文件转码（同步）
babel.transformFileSync('filename.js', options)
// => { code, map, ast }

// Babel AST转码
babel.transformFromAst(ast, code, options)
// => { code, map, ast }
```

示例

```javascript
let es6Code = 'let x = n => n + 1'
let es5Code = require('@babel/core')
  .transform(es6Code, {
    presets: ['@babel/env']
  })
  .code

console.log(es5Code)
// '"use strict";\n\nvar x = function x(n) {\n  return n + 1;\n};'
```

## 配置文件

`.babelrc`，存放在根目录下，用于设置预设和插件，需要安装设置的模块

```json
{
  "presets": [],
  "plugins": []
}
```

* `presets`: 预设，某一类插件的集合
* `plugins`: 插件，进行代码转换

### presets

* 预设名称：预设名称前缀为`babel-preset-`时，可使用短名称
* 预设顺序：倒序执行presets中的预设
* 预设参数：插件名和参数对象组成一个数组

```json
// 预设名称
{
  "presets": [
    "@org/babel-preset-name",
    "@org/name" // equivalent
  ]
}

// 预设参数
{
  "presets": ["presetA", ["pluginA"], ["pluginA", {}]]
}
```

### 官方preset

* `@babel/preset-env`: 处理es6+规范语法的插件集合
* `@babel/preset-stage`：处理尚处在提案语法的插件集合
* `@babel/preset-react`：处理react语法的插件集合
* `@babel/preset-flow`：处理flow语法的插件集合
* `@babel/preset-typescript`：处理typescript语法的插件集合

### plugins

* 插件名称：插件名称前缀为`babel-plugin-`时，可使用短名称
* 插件顺序：顺序执行plugins中的插件，再执行presets
* 插件参数：插件名和参数对象组成一个数组

```json
// 插件名称
{
  "plugins": [
    "@org/babel-plugin-name",
    "@org/name" // 两个插件实际是同一个
  ]
}

// 插件参数
{
  "plugins": ["pluginA", ["pluginA"], ["pluginA", {}]]
}
```

## @babel/cli

babel的命令行工具，用于命令行转码

### 安装

```bash
npm install --save-dev @babel/cli
```

### 用法

```bash
# 转码文件，输出到标准输出
npx babel <source>

# 转码文件，输出到新文件
npx babel <source> -o <compile>

# 转码目录，输出到新目录
npx babel <src> -d <dir>

# 转码目录，输出到新目录并生成source map文件
npx babel <src> -d <dir> -s
```

## @babel/polyfill

新API的垫片

## 安装

```bash
npm install --save @babel/polyfill
```

### 使用

引入

```javascript
import '@babel/polyfill'
```

按需引入

```json
{
  "presets": [
    [
      "env",
      {
        "useBuiltIns": "entry"
      }
    ]
  ]
}
```

## @babel/runtime

使用辅助函数辅助转换

### 安装

```bash
npm install --save-dev @babel/runtime
```

### 按需引入

```bash
npm install --save-dev @babel/plugin-transform-runtime
```

配置

```json
{
  "presets": [
    [
      "env",
      {
        "useBuiltIns": "entry"
      }
    ]
  ],
  "plugins": [
    "@babel/plugin-transform-runtime"
  ]
}
```

## @babel/register

对require加载的文件进行转码

### 安装

```bash
npm install --save-dev @babel/register
```

### 使用

```javascript
// index.js
require('@babel/register');
require('./es6.js');
```

## @babel/node

提供支持 ES6 的 REPL 环境

### 安装

```bash
npm install --save-dev @babel/node
```

### 用法

```bash
# 进入ES6 的 REPL 环境
npx babel-node

# 执行ES6文件
npx babel-node <source>
```

## 浏览器环境

在浏览器环境使用

```html
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
<script type="text/babel">
  // Your ES6 code
</script>
```

## 在线编译器

https://babeljs.io/repl/
