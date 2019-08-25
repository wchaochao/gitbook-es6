# 概述

标签（空格分隔）： ES6

---

JavaScript5.1版本后的下一代标准，包括ES2015、ES2016...

## 历史

* 1996：开始ECMAScript标准
* 1997：ECMAScript1.0发布
* 1998：ECMAScript2.0发布
* 1999：ECMAScript3.0发布
* 2000：ECMAScript4.0开始制定，一直未通过
* 2008：中止ECMAScript4.0开发
* 2009：ECMAScript4.0不激进的部分作为ECMAScript5.0发布
* 2011：ECMAScript5.1发布
* 2015：ECMASCript6发布，以后每年发布一个版本，为ES2015、ES2016...

## 支持度

### 浏览器

* 查看 http://kangax.github.io/compat-table/es6/
* 访问 http://ruanyf.github.io/es-checker/

### Node

```bash
// Linux & Mac
$ node --v8-options | grep harmony

// Windows
$ node --v8-options | findstr harmony
```

使用es-checker

```bash
$ npm install -g es-checker
$ es-checker

=========================================
Passes 24 feature Detections
Your runtime supports 57% of ECMAScript 6
=========================================
```
