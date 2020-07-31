

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

# 注意

## 双向绑定

**[(ngModel)]** 是 Angular 的双向数据绑定语法。 

ngModel属于一个可选模块 `FormsModule`，必须自行添加此模块才能使用该指令 ：

1、打开`AppModule` (`app.module.ts`) 从 `@angular/forms` 库中导入 `FormsModule` 符号 ；

2、把 `FormsModule` 添加到 `@NgModule` 元数据的 `imports` 数组中，`imports` 是该应用所需外部模块的列表 。

## 每个组件都必须声明在（且只能声明在）一个 [NgModule](https://angular.cn/guide/ngmodules) 中 

Angular CLI 在生成 组件的时候就自动把它加到了 `AppModule` 中 ；

`AppModule` 声明了应用中的所有组件 。
