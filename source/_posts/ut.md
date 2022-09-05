---
title: 如何书写单元测试
tag: unit test
categories: test
top_img: ../img/unit-test.png
cover: ../img/unit-test.png
---

## 概述

在开发大型的项目过程中经常会面临这样的问题，比如添加新的 feature 或者修复 bugs 时，原本没有修改的地方出现了问题，往往需要费时又费力的去找到问题所在。因此为项目添加测试是十分有必要的，它是保证代码质量的重要环节，通常测试分为两种不同类型：单元测试和功能测试。

**单元测试** 有时也称为隔离测试，它是测试独立的小段代码的实践。如果需要测试使用一些外部资源，例如网络或数据库，则它不是单元测试。

**功能测试** 用来测试应用程序的完整功能。在 Web 应用程序的实践中，能测试到应用程序在浏览器中运行时的交互，就像用户在现实生活中与它进行交互一样，例如点击页面，也称为端到端或 E2E 测试。

单元测试虽然不能完全完成功能测试，但是在开发 web 项目时却能保证底层单一模块的工作质量，并且在代码重构的时候保证对外接口不会发生变化。

## 测试框架

目前有许多测试框架，下面介绍一些常见的测试框架及其特点：

### Jasmine

Jasmine 是一个 JavaScript 测试框架，支持称为行为驱动开发（简称 BDD ）的软件开发实践。它是测试驱动开发( TDD )的一种特殊形式 。Jasmine 和一般的 BDD 一样以人类可读的格式描述测试，以便非技术人员能够理解正在测试的内容。

Jasmine 的优点包括：

- 由于几乎为零的外部依赖关系, 从而降低了开销
- 现成的几乎所有必需的工具
- 支持前端和后端测试
- 编码非常类似于用自然语言编写
- 广泛的文档, 可用于多个框架

### Jest

Jest 是 Facebook 团队构建和维护的 JavaScript 测试框架，是基于 Jasmine 的 JavaScript 单元测试框架。它是基于 React 的应用程序的首选框架，但它不限于与React一起使用。

Jest 的一些功能包括：

- 适用于 NodeJS, VueJS, React, Angular 和其他基于 Babel 的项目的单一框架
- 好的文档和编码的标准语法
- 使用实时快照, 可以管理较大对象的测试

### Karma

Karma 是一个高效的测试环境, 其内部支持所有流行的测试描述框架。它为你的应用程序提供了在不同环境中执行测试的支持。它具有对在不同设备和应用程序上执行测试的广泛支持。

## 快速开始

本文主要以 Jasmine 为例来介绍，其他的测试框架都大同小异，主要是语法上的差异。

### 安装

需要安装 node 后，使用 npm 安装

```shell
npm install jasmine --save-dev
```

### 基本语法

*describe(string, function)* 定义一个测试spec，即单个测试规范的集合，例如测试一个函数。

*it(string, function)* 定义了一个单独的测试规范，它包含一个或多个测试期望，例如一个代码块。

*expect(actual)* 表达式是我们所说的 Expectation。它与 Matcher 一起描述了应用程序中的预期行为。

*matcher(expected)* 表达式是我们所说的 Matcher。它与 expected 传入的 actual 值与传递给 expect 函数的值进行布尔比较，如果它们为假，则规范失败。框架提供了许多断言函数：toHaveBeenCalled, toBe, toEqual 等。

```ts
describe('Hello world', () => {
  it('says hello', () => {
    expect(helloWorld()).toEqual('Hello world!');
  });
});
```

在运行测试代码时，会将所有的测试代码全部运行一遍，如果只想运行一个测试套件或者测试用例，只需要在 describe/it 之前加一个 f 即可，也就是 fdescribe/fit。

### setup & teardown

*beforeEach()/afterEach()* 在运行每个测试规范（it函数）之前/后调用此函数。
*beforeAll()/afterAll()* 在运行测试套件（describe函数）中的所有规范之前/后，此函数被调用一次。

```ts
describe('Hello world', () => {
  let expected = "";
  beforeEach(() => {
    expected = "Hello World";
  });
  afterEach(() => {
    expected = "";
  });
  it('says hello', () => {
    expect(helloWorld()).toEqual(expected);
  });
});
```

### Mock & Spy

在测试每个单元时，由于没有真实的数据和输入，因此需要 mock 相应的值，让程序执行特定的逻辑代码块，例如我们在测试一个 function 时，里面存在许多条件分支语句，或者循环语句，就可以 mock 数据让程序进入指定的分支执行对应的代码，从而来测试其中的逻辑是否正确。

Spy 是 Jasmine 的一个函数，类似于一个拦截器，它可以获取现有的 class, function 或 object。使用 SpyOn 可以拦截原本的函数调用，变成 SpyOn 返回的的假的函数或者值，这样能解除各个函数直接的依赖，方便我们进行单元测试。spy 常用的方法如下：

- spyOn: 建立一个假的 method

```ts
spyOn<T>(object: T, method: keyof T): Spy
```

- returnValue: 设置假 spy method 被调用时返回的值

```ts
returnValue(val: any): Spy
```

- callFake: 建立假 spy method 的调用

```ts
callFake(fn: Function): Spy
```

- throwError: 假设抛出异常

```ts
throwError(msg: string): Spy
```

- callTrough: 调用原本的method，但 spy 会对此 method 进行监测，因此可搭配其他 toHaveBeenCalled() 等 matcher 检测 method 是否被调用过。

```ts
callThrough(): Spy
```

下面是一个例子对本节进行一个总结

```ts
import {LoginComponent} from './login.component';
import {AuthService} from "./auth.service";

describe('Component: Login', () => {

  let component: LoginComponent;
  let service: AuthService;
  let spy: any;

  beforeEach(() => {
    service = new AuthService();
    component = new LoginComponent(service);
  });

  afterEach(() => {
    service = null;
    component = null;
  });


  it('needsLogin returns true when the user has not been authenticated', () => {
    spy = spyOn(service, 'isAuthenticated').and.returnValue(false);
    expect(component.needsLogin()).toBeTruthy();
    expect(service.isAuthenticated).toHaveBeenCalled()
    });

  it('needsLogin returns false when the user has been authenticated', () => {
    spy = spyOn(service, 'isAuthenticated').and.returnValue(true);
    expect(component.needsLogin()).toBeFalsy();
    expect(service.isAuthenticated).toHaveBeenCalled();
  });
});
```

使用依赖项的真实实例进行测试会导致我们的测试代码需要依赖其他类的内部函数，从而导致紧密耦合和脆弱的代码。

为了能写出独立的测试代码片段，并且无需了解其依赖项的内部工作原理。我们通过创建 Mocks 来做到这一点；我们可以使用假类、扩展现有类或使用类的真实实例但通过 Spies 控制它们来创建 Mocks。

## Ref

- [11种最佳JavaScript单元测试框架和工具](http://www.srcmini.com/47544.html)
- [Jasmine and Karma](https://codecraft.tv/courses/angular/unit-testing/jasmine-and-karma/)
- [Jasmine Spy](https://medium.com/allen%E7%9A%84%E6%8A%80%E8%A1%93%E7%AD%86%E8%A8%98/jasmine-spy-%E5%AD%B8%E7%BF%92%E7%AD%86%E8%A8%98-8f1ca2ae641c)
