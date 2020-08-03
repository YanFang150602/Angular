

# Angular开始

## 安装Angular脚手架

```shell
npm install -g @angular/cli
```

## 新建Angular项目

```shell
# --skip-install跳过安装package.json里依赖的包
ng new AngularDemo --skip-install
# 进入项目
cd AngularDemo
# 安装package.json里依赖的包
npm install
```

## 新建组件component

```shell
# 在src/app目录下新增components目录
ng generate component components/header
# 命令执行后，显示：
# CREATE src/app/components/header/header.component.html (21 bytes)
# CREATE src/app/components/header/header.component.spec.ts (628 bytes)
# CREATE src/app/components/header/header.component.ts (276 bytes)
# CREATE src/app/components/header/header.component.scss (0 bytes)
# UPDATE src/app/app.module.ts (572 bytes)
```

## 启动项目

```shell
ng serve --open
# http://localhost:4200/
```

# Angular API

## @Input

### @Input描述

一个装饰器，用来把某个类字段标记为输入属性，并提供配置元数据。 该输入属性会绑定到模板中的某个 DOM 属性。当变更检测时，Angular 会自动使用这个 DOM 属性的值来更新此数据属性。（父组件可以传递数据给子组件，包括将父组件对象也可以传递给子组件）。
### @Input使用
1、子组件里使用
```typescript
// 子组件.ts
// 引用Input
import { Input } from '@angular/cli';

// 在子组件class里使用Input
// x是自定义属性名，用在父组件调用子组件时，子组件的属性<child-selector [x]="父组件里的属性"></child-selector>
// y是直接用在子组件里的属性
@Input('x') y: any;
```
```html
<!-- 子组件模板 -->
<p>{{y}}</p>
```
2、父组件里使用
```html
<!-- 父组件模板 -->
<child-selector [x]="parentMsg"></child-selector>
```
```typescript
// 父组件.ts
// 父组件class里定义parentMsg属性
parentMsg: string = '我来自Parent Component的！';
```

## @ViewChild

## @Output

## 新建服务service

```shell
ng generate service services/common
# 命令执行后，显示：
# CREATE src/app/services/common.service.spec.ts (357 bytes)
# CREATE src/app/services/common.service.ts (135 bytes)
```

# 内部指令

## *ngFor

[`*ngFor`](https://angular.cn/guide/template-syntax#ngFor) 是一个 Angular 的复写器（repeater）指令。 它会为列表中的每项数据复写它的宿主元素。 

不要忘了 `ngFor` 前面的星号（`*`），它是该语法中的关键部分。 


# 注意

## npm install时失败

执行npm install后，失败

```shell
$ npm install
npm WARN registry Using stale data from https://registry.npm.taobao.org/ because the host is inaccessible -- are you offline?
npm WARN registry Using stale data from https://registry.npm.taobao.org/ due to a request error during revalidation.
npm ERR! code ENOTFOUND
npm ERR! errno ENOTFOUND
npm ERR! network request to https://registry.npm.taobao.org/@angular%2fanimations failed, reason: getaddrinfo ENOTFOUND registry.npm.taobao.org
npm ERR! network This is a problem related to network connectivity.
npm ERR! network In most cases you are behind a proxy or have bad network settings.
npm ERR! network
npm ERR! network If you are behind a proxy, please make sure that the
npm ERR! network 'proxy' config is set properly.  See: 'npm help config'

npm ERR! A complete log of this run can be found in:
npm ERR!     C:\Users\彦博\AppData\Roaming\npm-cache\_logs\2020-08-02T01_11_54_679Z-debug.log

# 再次执行npm install，还是失败：
$ npm install
npm WARN deprecated request@2.88.2: request has been deprecated, see https://github.com/request/request/issues/3142
npm WARN deprecated chokidar@2.1.8: Chokidar 2 will break on node v14+. Upgrade to chokidar 3 with 15x less dependencies.
npm WARN deprecated har-validator@5.1.5: this library is no longer supported
npm ERR! Unexpected end of JSON input while parsing near '...de","version":"4.2.6"'

npm ERR! A complete log of this run can be found in:
npm ERR!     C:\Users\彦博\AppData\Roaming\npm-cache\_logs\2020-08-02T01_13_05_409Z-debug.log
```

解决

```shell
$ npm cache clean --force
# 这回 npm install成功
$ npm install
npm WARN deprecated chokidar@2.1.8: Chokidar 2 will break on node v14+. Upgrade to chokidar 3 with 15x less dependencies.
npm WARN deprecated request@2.88.2: request has been deprecated, see https://github.com/request/request/issues/3142
npm WARN deprecated fsevents@1.2.13: fsevents 1 will break on node v14+ and could be using insecure binaries. Upgrade to fsevents 2.
npm WARN deprecated har-validator@5.1.5: this library is no longer supported
npm WARN deprecated urix@0.1.0: Please see https://github.com/lydell/urix#deprecated
npm WARN deprecated resolve-url@0.2.1: https://github.com/lydell/resolve-url#deprecated

> core-js@3.6.4 postinstall c:\development\VSCodeWorkspace\AngularDemo\node_modules\core-js
> node -e "try{require('./postinstall')}catch(e){}"

Thank you for using core-js ( https://github.com/zloirock/core-js ) for polyfilling JavaScript standard library!

The project needs your help! Please consider supporting of core-js on Open Collective or Patreon:
> https://opencollective.com/core-js
> https://www.patreon.com/zloirock

Also, the author of core-js ( https://github.com/zloirock ) is looking for a good job -)


> @angular/cli@10.0.5 postinstall c:\development\VSCodeWorkspace\AngularDemo\node_modules\@angular\cli
> node ./bin/postinstall/script.js

npm notice created a lockfile as package-lock.json. You should commit this file.
npm WARN notsup Unsupported engine for watchpack-chokidar2@2.0.0: wanted: {"node":"<8.10.0"} (current: {"node":"12.16.3","npm":"6.14.4"})
npm WARN notsup Not compatible with your version of node/npm: watchpack-chokidar2@2.0.0
npm WARN sass-loader@8.0.2 requires a peer of node-sass@^4.0.0 but none is installed. You must install peer dependencies yourself.
npm WARN sass-loader@8.0.2 requires a peer of fibers@>= 3.1.0 but none is installed. You must install peer dependencies yourself.
npm WARN webpack-subresource-integrity@1.4.1 requires a peer of html-webpack-plugin@^2.21.0 || ~3 || >=4.0.0-alpha.2 <5 but none is installed. You must install peer dependencies yourself.
npm WARN ws@7.3.1 requires a peer of bufferutil@^4.0.1 but none is installed. You must install peer dependencies yourself.
npm WARN ws@7.3.1 requires a peer of utf-8-validate@^5.0.2 but none is installed. You must install peer dependencies yourself.
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.13 (node_modules\webpack-dev-server\node_modules\fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.13: wanted {"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"x64"})
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.13 (node_modules\watchpack-chokidar2\node_modules\fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.13: wanted {"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"x64"})
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@2.1.3 (node_modules\fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@2.1.3: wanted {"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"x64"})

added 1458 packages from 1215 contributors in 120.549s

59 packages are looking for funding
  run `npm fund` for details

```

## 双向绑定

**[(ngModel)]** 是 Angular 的双向数据绑定语法。 

ngModel属于一个可选模块 `FormsModule`，必须自行添加此模块才能使用该指令 ：

1、打开`AppModule` (`app.module.ts`) 从 `@angular/forms` 库中导入 `FormsModule` 符号 ；

2、把 `FormsModule` 添加到 `@NgModule` 元数据的 `imports` 数组中，`imports` 是该应用所需外部模块的列表 。

## 每个组件都必须声明在（且只能声明在）一个 [NgModule](https://angular.cn/guide/ngmodules) 中 

Angular CLI 在生成 组件的时候就自动把它加到了 `AppModule` 中 ；

`AppModule` 声明了应用中的所有组件 。
