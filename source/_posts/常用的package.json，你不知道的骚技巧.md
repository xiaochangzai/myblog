## 常用的package.json，还有这多你不知道的骚技巧

前端小黑 [前端梦想家](javascript:void(0);) *今天*

![img](https://mmbiz.qpic.cn/mmbiz_png/ib46ibiblQLaTHHUa1cpmuicWPBNPJlGhpTccYpB5dY09SLtJcqE4LSiaynFGUCjicoJPdqDFry7Az3krYIjJA4bSk0Q/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

## 前言 🤔 

在每个项目的根目录下面，一般都会有一个 `package.json` 文件，其定义了运行项目所需要的各种依赖和项目的配置信息（如名称、版本、许可证等元数据）。

大多数人对 `package.json` 文件的了解，仅停留在：

- - 项目名称、项目构建版本、许可证的定义；
  - 依赖定义（包括 `dependencies` 字段，`devDependencies` 字段）；
  - 使用`scripts`字段指定运行脚本命令的 `npm` 命令行缩写。

其实，`package.json` 的作用远不止于此，我们可以通过新增配置项实现更强大的功能，下面将带你重新认识  `package.json`。

## 由简入繁，丰富项目的 package.json

### 简单版的 package.json

当我们新建一个名称为 `my-test` 的项目时，使用 `yarn init -y` 或 `npm init -y` 命令后，在项目目录下会新增一个 `package.json`文件，内容如下：

```
{
"name": "my-test", # 项目名称
"version": "1.0.0", # 项目版本（格式：大版本.次要版本.小版本）
"description": "", # 项目描述
"main": "index.js", # 入口文件
"scripts": { # 指定运行脚本命令的 npm 命令行缩写
"test": "echo \"Error: no test specified\" && exit 1"
  },
"keywords": [], # 关键词
"author": "", # 作者
"license": "ISC" # 许可证
}
```

可以看到，`package.json` 文件的内容是一个 `JSON` 对象，对象的每一个成员就是当前项目的一项配置。

### 必备属性（name & version）

- `package.json` 中有非常多的配置项，其中必须填写的两个字段分别是 `name` 字段和 `version` 字段，它们是组成一个 `npm` 模块的唯一标识。

#### name 字段

`name` 字段定义了模块的名称，其命名时需要遵循官方的一些规范和建议：

- - 模块名会成为模块 `url`、命令行中的一个参数或者一个文件夹名称，任何非 `url` 安全的字符在模块名中都不能使用（我们可以使用 `validate-npm-package-name` 包来检测模块名是否合法）；
  - 语义化模块名，可以帮助开发者更快的找到需要的模块，并且避免意外获取错误的模块；
  - 若模块名称中存在一些符号，将符号去除后不得与现有的模块名重复，例如：由于 `react-router-dom` 已经存在，`react.router.dom`、`reactrouterdom` 都不可以再创建。

`name` 字段不能与其他模块名重复，我们可以执行以下命令查看模块名是否已经被使用：

```
npm view <packageName>
```

如果模块存在，可以查看该模块的一些基本信息：

![img](https://mmbiz.qpic.cn/mmbiz_jpg/XP4dRIhZqqUQV8Z3TJGIH6Fas9pDtDhZdz15AQSbOGRhWwiaHPR7erLWVLIkAEhppxON6fQ7s3qJGsl5PCIxdag/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

如果该模块名从未被使用过，则会抛出 404 错误：

![img](https://mmbiz.qpic.cn/mmbiz_jpg/XP4dRIhZqqUQV8Z3TJGIH6Fas9pDtDhZjJM9a9pkaghUlWpzV32cZ0k2uaoHd1lgA7jGWXMhlXWMzov3MMCNOA/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

或者，我们也可以去 `npm` 上输入模块名，如果搜不到，则可以使用该模块名。

#### version 字段

`npm` 包中的模块版本都需要遵循 `SemVer` 规范，该规范的标准版本号采用 `X.Y.Z` 的格式，其中 `X`、`Y` 和 `Z` 均为非负的整数，且禁止在数字前方补零：

- - `X` 是主版本号(major)：修改了不兼容的 API
  - `Y` 是次版本号(minor)：新增了向下兼容的功能
  - `Z` 为修订号(patch)：修正了向下兼容的问题

当某个版本改动比较大、并非稳定而且可能无法满足预期的兼容性需求时，我们可能要先发布一个先行版本。

先行版本号可以加到`主版本号.次版本号.修订号`的后面，通过 `-` 号连接一连串以句点分隔的标识符和版本编译信息：

- - 内部版本(alpha)
  - 公测版本(beta)
  - 正式版本的候选版本rc（即 Release candiate）

我们可以执行以下命令查看模块的版本：

```
npm view <packageName> version # 查看某个模块的最新版本
npm view <packageName> versions # 查看某个模块的所有历史版本
复制代码
```

查看 `antd` 的最新版本：![img](https://mmbiz.qpic.cn/mmbiz_jpg/XP4dRIhZqqUQV8Z3TJGIH6Fas9pDtDhZSTu3002rLOrljRicE48ia9Dv0C2oZDJdNptaJVH84gTiaHzR1Z8IRk4kw/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

查看 `antd` 的所有历史版本：

![img](https://mmbiz.qpic.cn/mmbiz_gif/XP4dRIhZqqUQV8Z3TJGIH6Fas9pDtDhZYIvjp4sgSuUrLRKxKzz6WwgiaMIhOrRmWsqkEA9IEwzTFCXywtOZKhA/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)

可以看到，`antd` 是严格按照 `SemVer` 规范来发版的，版本号是严格按照`主版本号.次版本号.修订号`的格式命名和严格递增的，在发布的版本改动较大时，还会先发布`alpha`、`beta`、`rc`等先行版本。

### 描述信息（description & keywords）

- `description` 字段用于添加模块的描述信息，便于用户了解该模块。
- `keywords` 字段用于给模块添加关键字。
- 当我们使用 `npm` 检索模块时，会对模块中的 `description` 字段和 `keywords` 字段进行匹配，写好 `package.json`中的 `description` 和 `keywords` 将有利于增加我们模块的曝光率。

### 安装项目依赖（dependencies & devDependencies）

`dependencies`字段指定了项目运行所依赖的模块（生产环境使用），如 `antd`、 `react`、 `moment`等插件库：

- - 它们是我们生产环境所需要的依赖项，在把项目作为一个 `npm` 包的时候，用户安装 `npm` 包时只会安装 `dependencies` 里面的依赖。

`devDependencies` 字段指定了项目开发所需要的模块（开发环境使用），如 `webpack`、`typescript`、`babel`等：

- - 在代码打包提交线上时，我们并不需要这些工具，所以我们将它放入 `devDependencies` 中。

如果一个模块不在 `package.json` 文件之中，我们可以单独安装这个模块，并使用相应的参数，将其写入 `dependencies` 字段/ `devDependencies` 字段中：

```
# 使用 npm
npm install <package...> --save # 写入 dependencies 属性
npm install <package...> --save-dev # 写入 devDependencies 属性

# 使用 yarn
yarn add <package...> # 写入 dependencies 属性
yarn add <package...> --dev # 写入 devDependencies 属性
复制代码
```

有了 `package.json` 文件，开发直接使用 `npm install` / `yarn install` 命令，就会在当前目录中自动安装所需要的模块，安装完成项目所需的运行和开发环境就配置好了。

### 简化终端命令（scripts）

`scripts` 字段是 `package.json` 中的一种元数据功能，它接受一个对象，对象的属性为可以通过 `npm run `运行的脚本，值为实际运行的命令（通常是终端命令），如：

```
"scripts": {
"start": "node index.js"
},
```

将终端命令放入 `scripts` 字段，既可以记录它们又可以实现轻松重用。

### 定义项目入口（main）

`main` 字段是 `package.json` 中的另一种元数据功能，它可以用来指定加载的入口文件。假如你的项目是一个 `npm` 包，当用户安装你的包后，`require('my-module')` 返回的是 `main` 字段中所列出文件的 `module.exports` 属性。



当不指定`main` 字段时，默认值是模块根目录下面的`index.js` 文件。

### 发布文件配置（files）

`files` 字段用于描述我们使用 `npm publish` 命令后推送到 `npm` 服务器的文件列表，如果指定文件夹，则文件夹内的所有内容都会包含进来。

我们可以查看下载的 `antd` 的 `package.json` 的`files` 字段，内容如下：

```
"files": [
"dist",
"lib",
"es"
],
```

可以看到下载后的 `antd` 包是下面的目录结构：

![img](https://mmbiz.qpic.cn/mmbiz_jpg/XP4dRIhZqqUQV8Z3TJGIH6Fas9pDtDhZm07FyYHeh30OrsggekZ88BHAe6qpicQD4vDkt1WHWjZBeIhSZuRLYew/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

另外，我们还可以通过配置一个 `.npmignore` 文件来排除一些文件， 防止大量的垃圾文件推送到 `npm` 上。

### 定义私有模块（private）

一般公司的非开源项目，都会设置 `private` 属性的值为 `true`，这是因为 `npm` 拒绝发布私有模块，通过设置该字段可以防止私有模块被无意间发布出去。

### 指定模块适用系统（os）

假如我们开发了一个模块，只能跑在 `darwin` 系统下，我们需要保证 `windows` 用户不会安装到该模块，从而避免发生不必要的错误。

这时候，使用 `os` 属性则可以帮助我们实现以上的需求，该属性可以指定模块适用系统的系统，或者指定不能安装的系统黑名单（当在系统黑名单中的系统中安装模块则会报错）：

```
"os" : [ "darwin", "linux" ] # 适用系统
"os" : [ "!win32" ] # 黑名单
```

> Tips：在 `node` 环境下可以使用 `process.platform` 来判断操作系统。

### 指定模块适用 cpu 架构（cpu）

和上面的 `os` 字段类似，我们可以用 `cpu` 字段更精准的限制用户安装环境：

```
"cpu" : [ "x64", "ia32" ] # 适用 cpu
"cpu" : [ "!arm", "!mips" ] # 黑名单
```

> Tips：在 `node` 环境下可以使用 `process.arch` 来判断 `cpu` 架构。

### 指定项目 node 版本（engines）

有时候，新拉一个项目的时候，由于和其他开发使用的 `node` 版本不同，导致会出现很多奇奇怪怪的问题（如某些依赖安装报错、依赖安装完项目跑不起来等）。

![img](https://mmbiz.qpic.cn/mmbiz_jpg/XP4dRIhZqqUQV8Z3TJGIH6Fas9pDtDhZ3IXOcuKe4lswmxkIpwiaia0qgDYbXAFQVVuLzvwmsFfrTyooqnic7LbgQ/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

为了实现项目开箱即用的伟大理想，这时候可以使用 `package.json` 的 `engines` 字段来指定项目 node 版本：

```
"engines": {
"node": ">= 8.16.0"
},
```

该字段也可以指定适用的 `npm` 版本：

```
"engines": {
"npm": ">= 6.9.0"
 },
```

需要注意的是，engines属性仅起到一个说明的作用，当用户版本不符合指定值时也不影响依赖的安装。

### 自定义命令（bin）

用过 `vue-cli`，`create-react-app`等脚手架的朋友们，不知道你们有没有好奇过，为什么安装这些脚手架后，就可以使用类似 `vue create`/`create-react-app`之类的命令，其实这和 `package.json` 中的 `bin` 字段有关。

`bin` 字段用来指定各个内部命令对应的可执行文件的位置。当`package.json` 提供了 `bin` 字段后，即相当于做了一个命令名和本地文件名的映射。

当用户安装带有 `bin` 字段的包时，

- - 如果是全局安装，`npm` 将会使用符号链接把这些文件链接到`/usr/local/node_modules/.bin/`；
  - 如果是本地安装，会链接到`./node_modules/.bin/`。

举个 🌰，如果要使用 `my-app-cli` 作为命令时，可以配置以下 `bin` 字段：

```
"bin": {
"my-app-cli": "./bin/cli.js"
}
```

上面代码指定，`my-app-cli` 命令对应的可执行文件为 `bin` 子目录下的 `cli.js`，因此在安装了 `my-app-cli` 包的项目中，就可以很方便地利用 `npm`执行脚本：

```
"scripts": {
  start: 'node node_modules/.bin/my-app-cli'
}
```

![img](https://mmbiz.qpic.cn/mmbiz_jpg/XP4dRIhZqqUQV8Z3TJGIH6Fas9pDtDhZEiaqlsl4iaJ6icZYO9HKRC9ibtK5lz0eMWneQIWyncjHEOp00iaxPebeGag/640?wx_fmt=jpeg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

咦，怎么看起来和 `vue create`/`create-react-app`之类的命令不太像？原因：

- - 当需要 `node` 环境时就需要加上 `node` 前缀
  - 如果加上 `node` 前缀，就需要指定 `my-app-cli` 的路径 -> `node_modules/.bin`，否则 `node my-app-cli`会去查找当前路径下的 `my-app-cli.js`，这样肯定是不对。

若要实现像 `vue create`/`create-react-app`之类的命令一样简便的方式，则可以在上文提到的 `bin` 子目录下可执行文件`cli.js` 中的第一行写入以下命令：

```
#!/usr/bin/env node
```

这行命令的作用是告诉系统用 `node` 解析，这样命令就可以简写成 `my-app-cli` 了。

### React 项目相关

#### 设置应用根路径（homepage）

当我们使用 `create-react-app` 脚手架搭建的 `React` 项目，默认是使用内置的 `webpack` 配置，当`package.json` 中不配置 `homepage` 属性时，build 打包之后的文件资源应用路径默认是  `/`，如下图：

![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

一般来说，我们打包的静态资源会部署在 `CDN` 上，为了让我们的应用知道去哪里加载资源，则需要我们设置一个根路径，这时可以通过 `package.json` 中的 `homepage` 字段设置应用的根路径。

当我们设置了 `homepage` 属性后：

```
{
"homepage": "https://xxxx.cdn/my-project",
}
```

打包后的资源路径就会加上 `homepage` 的地址：

![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

#### 开发环境解决跨域问题（proxy）

在做前后端分离的项目的时候，调用接口时则会遇到跨域的问题，当在开发环境中时，可以通过配置 `package.json` 中的 `proxy` 来解决跨域问题，配置如下：

```
{
"proxy": "http://localhost:4000"  // 配置你要请求的服务器地址
}
```

注意，当 `create-react-app` 的版本高于 2.0 版本的时候在 `package.json` 中只能配置 `string` 类型，这意味着如果要使用 `package.json` 来解决跨域问题，则只能代理一个服务器地址。

如果要代理多个服务器地址时，则需要安装 `http-proxy-middleware` ，在 `src` 目录下新建 `setupProxy.js` ：

```
const proxy = require("http-proxy-middleware");

module.exports = function(app) {
  app.use(
    proxy("/base", {
      target: "http://localhost:4000",
      changeOrigin: true
    })
  );
  app.use(
    proxy("/fans", {
      target: "http://localhost:5000",
      changeOrigin: true
    })
  );
};
```

#### 根据开发环境采用不同的全局变量值（自定义字段）

假设有这么一个组件，当组件被点击时，在开发环境时是跳转测试环境的 `sentry` 地址，在正式环境时则跳转正式环境的 `sentry` 地址。

首先，通过配置前面提到的 `scripts` 字段，实现环境变量（NODE_ENV）的设置：

```
"scripts": {
"start": "NODE_ENV=development node scripts/start.js",
"build": "NODE_ENV=production node scripts/build.js",
},
```

项目启动起来后，在代码中我们可以通过 `process.env.NODE_ENV` 访问到 `NODE_ENV` 的值。

##### 方案一

我们可以在组件中写类似以下的判断代码，根据不同环境给 `sentryUrl` 设置不同的值：

```
let sentryUrl;
if (process.env.NODE_ENV === 'development') {
    sentryUrl = 'test-sentry.xxx.com';
} else {
    sentryUrl = 'sentry.xxx.com';
}
```

这么做好像没毛病，但是深入一想，如果有多个组件，要根据不同的环境使用不同的服务（多种服务）地址，如果按照上面的写法，项目中将存在许多重复的判断代码，且当服务地址发生变化时，包含这些服务地址的组件都需要相应的做改动，这样明显是不合理的。

![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

##### 方案二

解决方案：相关服务的地址配置在 `package.json`中，同时修改项目的 `webpack` 配置。

注：修改项目的 `webpack` 配置需要 eject 项目的 `webpack` 配置（更多细节可阅读 👉：react + typescript 项目的定制化过程）。

在项目根目录下使用 `yarn eject` 成功 eject 出配置后，可以发现项目目录的变化如下：

![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

如果需要定制化项目，一般就是在 `config` 目录下对默认的 `webpack` 配置进行修改，在这里我们需要关注 `config/path.js` 和 `config/env.js` 两个文件：

- - `env.js` 的主要目的在于读取 `env` 配置文件并将 `env` 的配置信息给到全局变量 `process.env` ；
  - `path.js` 的主要目的在于为项目提供各种路径，包括构建路径、 `public` 路径等。

由于本文的重点不是学习 `webpack` 配置，这里仅介绍如何实现【根据开发环境采用不同的全局变量值】的功能。

首先，需要在 `package.json` 中配置以下内容：

```
"scripts": {
"start": "NODE_ENV=development node scripts/start.js",
"build": "NODE_ENV=production node scripts/build.js",
},
"sentryPath": {
"dev": "https://test-sentry.xxx.com",
"prod": "https://sentry.xxx.com"
 }
```

然后，修改 `path.js` 文件，内容如下：

```
// 重写 getPublicUrl 方法
const getPublicUrl = (appPackageJson, pathName) => {
let path;
switch (process.env.DEPLOY_ENV) {
case'development':
      path = require(appPackageJson)[pathName].dev;
break;
case'production':
      path = require(appPackageJson)[pathName].prod;
break;
default:
      path = envPublicUrl || require(appPackageJson).homepage;
  }
return path;
}

// 新增 getSentryPath 方法
const getSentryPath = (appPackageJson) => {
return getPublicUrl(appPackageJson, 'sentryPath');
}

// config after eject: we're in ./config/
module.exports = {
  ...,
sentryUrl: getSentryPath(resolveApp('package.json')), // 新增
};
```

最后，修改 `env.js` 文件，内容如下：

```
// 修改 getClientEnvironment 方法
function getClientEnvironment(publicUrl) {
const raw = Object.keys(process.env)
    .filter(key => REACT_APP.test(key))
    .reduce(
(env, key) => {
        ...
      },
      {
NODE_ENV: process.env.NODE_ENV || 'development',
PUBLIC_URL: publicUrl,
SENTRY_URL: paths.sentryUrl // 新增
      }
    );

const stringified = {
    ...
  };
return { raw, stringified };
}
```

通过上面的配置，我们就可以在组件中通过 `process.env.SENTRY_URL` 获取到 `sentry` 服务的地址了，虽然看起来比方案一繁琐，但是这种收益是长期的，如要新增一个  `sonarqube` 服务，同理实现即可，通过使用 `package.json` 也可以清楚的看到当前服务在不同环境下使用的地址。

## 总结 👀

本文介绍了 `package.json` 的多种常见的配置字段及作用，并通过例子加深大家对 `package.json`这些字段的理解。

除了一些常用字段，还介绍了在`React` 项目中 `package.json` 文件能实现的一些功能进行介绍。

> 以上内容如有遗漏错误，欢迎留言 ✍️ 指出，一起进步 💪💪💪

> 如果觉得本文对你有帮助，🏀🏀 留下你宝贵的 👍

## 参考资料 📖

1. Creating a package.json file
2. package.json bin的作用
3. 在开发环境中代理 API 请求
4. react + typescript 项目的定制化过程
5. React学习笔记

![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

❤️ 爱心三连击



1.看到这里了就点个在看支持下吧，你的「在看」是我创作的动力。



2.关注公众号前端梦想家，「一起学前端」！



3.添加微信【qdw1370336125】，拉你进技术交流群一起学习。

![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

在看点这里

![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)





[阅读原文](https://mp.weixin.qq.com/s?__biz=MzUyNDA2NTg5NQ==&mid=2247483774&idx=1&sn=4b08fd64305903332bf91dbce5c8f334&chksm=fa324c76cd45c560498645dc358fe78563c102680141669395e82c4ff7bfc46bc6148add56f6&mpshare=1&scene=1&srcid=&sharer_sharetime=1590968877589&sharer_shareid=77ba8debb81295e7116ea85bee64bb55&key=4f01d58ec7196d07e1a6b63018e94327b4cd830a3ce0919a971a5f7163a9e0896564f9e79d7c1d4b3473c32c982b1a82e5db44b6e4a43753b9e782dc93e2337b98fe4cf8e2c2c740817c4eba5fb189cf&ascene=1&uin=NzQ1NDc4NDEz&devicetype=Windows+10+x64&version=62090070&lang=zh_CN&exportkey=A0InUXE8bcG3xlivD2WokMc%3D&pass_ticket=bypY3bZPAuT2pGmEIdf5siU1%2BBXphIvIdFpgwz46qIgh0JUKPgcVYYVNhoAUpQAl&winzoom=1##)

阅读 93

 在看8