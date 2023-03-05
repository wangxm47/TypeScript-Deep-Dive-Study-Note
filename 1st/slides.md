---
theme: seriph
background: https://source.unsplash.com/collection/94734566/1920x1080
class: text-center
highlighter: shiki
lineNumbers: false
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
drawings:
  persist: false
transition: slide-left
css: unocss
monaco: true
title: 2023学习班第一期
---

# 2023学习班第一期

2023.03.02 王显淼

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    欢乐时光就要开始啦！ <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="abs-br m-6 flex gap-2">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon:edit />
  </button>
  <a href="https://github.com/slidevjs/slidev" target="_blank" alt="GitHub"
    class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
transition: fade-out
---

# 什么是 TypeScript ?

TypeScript 是一种基于 JavaScript 构建的强类型编程语言，可为您提供任何规模的更好工具。TypeScript 是 JavaScript 的类型化超集

- <cib-javascript class="mr-1 text-[#3178c6]"/> **JavaScript and More** - TypeScript 提供了 JavaScript 的所有功能，并在这些功能之上添加了一层：TypeScript 的类型系统。
- <carbon-result class="mr-1 text-[#3178c6]"/> **A Result You Can Trust** - 原则上，TypeScript 绝不改变 JavaScript 代码的运行时行为。这意味着，如果将代码从 JavaScript 迁移到 TypeScript ，即使 TypeScript 认为代码有类型错误，也可以保证以相同的方式运行。通过 TypeScript 编译器（tsc），TypeScript 代码可以被编译成纯净、简洁的 JavaScript 代码。
- <codicon-workspace-trusted class="mr-1 text-[#3178c6]"/> **Safety at Scale** - TypeScript 能够理解 JavaScript ，并且通过类型推断结合编辑器提供更好的编程环境而无需额外的代码。TypeScript可以让开发者在编辑器中更早的捕获错误。


---
transition: slide-down
---

# why TypeScript?
TypeScript有两个主要目标：

- 为JavaScript提供一个类型系统

- 提供最新和不断发展的 JavaScript 特性

<img src="/img/typescript-npm.png" class="h-260px object-center" />

<p class="absolute bottom-10" v-click>Read more about <a href="https://basarat.gitbook.io/typescript/getting-started/why-typescript" target="_blank">Why TypeScript?</a></p>

<!-- 为什么选择 TypeScript? https://rexdainiel.gitbooks.io/typescript/content/docs/why-typescript.html -->

---
transition: slide-up
---

# why TypeScript? - TypeScript的类型系统
为什么要向JavaScript添加类型呢？类型能够提高代码的质量以及可阅读性。这一结论已经被各大公司及团队认证。

- 在重构时，类型增加了效率及敏捷性。 让编译器捕获错误比在运行时崩溃更好。

- 类型是能拥有的最好的文档形式之一。 函数签名是定理，而函数体则是证明过程。

<br>
然而类型有着不必要的过分严谨。因此 TypeScript 讲究让门槛尽可能地低。接下来将介绍这样说的原因。



---

# 你的 JavaScript 就是 TypeScript
Your JavaScript is TypeScript。原则上，TypeScript 绝不改变 JavaScript 代码的运行时行为。

<p>TypeScript 为你的 JavaScript 代码提供了编译时的类型安全。这也难怪它有着这样的名字。厉害之处在于类型是完全可选的。</p>
<p>你的 JavaScript 代码的 <code>.js</code> 文件能够被重命名为 <code>.ts</code> 文件，而 TypeScript 仍会给你有效的 <code>.js</code> 文件，这个文件跟你的原来的 JavaScript 文件一模一样。</p>
<p>TypeScript 有意而且严格地成为了有着可选类型检查的 JavaScript 的超集。</p>


---

# 类型可以是隐含的
TypeScript 可以识别 JavaScript 语言，在许多情况下可以推断类型。

TypeScript 会尝试去推断尽可能多的类型信息，因此它可以在代码开发时通过最小的生产力开销给予你类型安全。例如，在下面的例子中 TypeScript 会知道 foo 是 number 类型并且在第二行报错：

```ts {monaco}
var foo = 123;
foo = '456';
```

这种类型推断是动机良好的。如果在JavaScript中你做了类似于例子展示的事情，那么在你剩余的代码中，你就不能确定 foo 是 number 还是 string。这种问题常常出现在大型的多文件代码仓库中。我们之后会对类型推断规则进行深入挖掘。

<style>
  iframe {
    min-height: 130px
  }
</style>

---

# 类型可以是清晰的
某些情况下类型难以自动推断，为了使类型推断涵盖这些情况，TypeScript 支持显式地类型定义

就像我们之前提到过的一样，TypeScript 会尽可能安全地去推断，然而你也可以使用标注来：

  1. 帮助编译器，以及更重要地，为下一个不得不阅读你的代码的开发者（有可能就是未来的你）添加文档。
  2. 强制让编译器看到的就是你认为它应该看到的。这就让你对于代码的理解能跟（编译器做的）代码的算法分析匹配。

TypeScript 使用了在其他可选标注语言（例如 ActionScript 和 F#）中很流行的后缀类型标注。
```ts
var foo: number = 123;
```

因此如果你做了错误的事，编译器会报错，例如：
```ts {monaco}

var foo: number = '123'; // Error: cannot assign a `string` to a `number`
```
<style>
  iframe {
    min-height: 130px
  }
</style>

---

# 类型是结构化的
TypeScript 的一个核心原则是类型检查基于对象的属性和行为。这有时被叫做“鸭子类型”或“结构类型”（structural typing）。

在结构化的类型系统当中，如果两个对象具有相同的结构，则认为它们是相同类型的。

<div v-click-hide>
```ts
interface Point {
  x: number;
  y: number;
}

function logPoint(p: Point) {
  console.log(`${p.x}, ${p.y}`);
}

// 打印 "12, 26"
const point = { x: 12, y: 26 };
logPoint(point);
```

point 变量从未声明为 Point 类型。 但是，在类型检查中，TypeScript 将 point 的结构与 Point的结构进行比较。它们的结构相同，所以代码通过了。
</div>

<div v-after>
结构匹配只需要匹配对象字段的子集。

```ts {monaco}
interface Point {
  x: number;
  y: number;
}

function logPoint(p: Point) {
  console.log(`${p.x}, ${p.y}`);
}

const point3 = { x: 12, y: 26, z: 89 };
logPoint(point3); // 打印 "12, 26"

const rect = { x: 33, y: 3, width: 30, height: 80 };
logPoint(rect); // 打印 "33, 3"

const color = { hex: "#187ABF" };
logPoint(color);
```
</div>

<style>
  .slidev-vclick-target {
    transition: all 500ms ease;
  }
  .slidev-vclick-hidden {
    opacity: 0;
    pointer-events: none;
    height: 0;
  }
</style>

---

类和对象确定结构的方式没有区别：

```ts
interface Point {
  x: number;
  y: number;
}

function logPoint(p: Point) {
  console.log(`${p.x}, ${p.y}`);
}
// ---分割线---
class VirtualPoint {
  x: number;
  y: number;

  constructor(x: number, y: number) {
    this.x = x;
    this.y = y;
  }
}

const newVPoint = new VirtualPoint(13, 56);
logPoint(newVPoint); // 打印 "13, 56"
```

---

# 类型错误不会阻止 JavaScript 生成
为了让你更容易地把 JavaScript 代码迁移到 TypeScript 上，尽管会有编译错误，默认情况下 TypeScript 会尽可能地**生成有效的 JavaScript**。

例子：
```ts
var foo = 123;
foo = '456'; // Error: cannot assign a `string` to a `number`
```

会生成这样的 js：
```ts
var foo = 123;
foo = '456';
```

因此可以逐步将 JavaScript 代码升级到 TypeScript。这跟其他语言编译器的工作机制有很大区别，也是另外一个使用 TypeScript 的原因。

---

# why TypeScript? - Future JavaScript => Now
TypeScript 为现在的 JavaScript 引擎（只支持 ES5 等等）提供了一系列在 ES6 中出现的特性。

TypeScript 团队正积极地添加这些特性，这个列表只会随着时间的推移越来越大，而我们会在之后的章节讨论它。仅仅作为一个样品，这里是一个 class 的例子：
```ts
class Point {
    constructor(public x: number, public y: number) {
    }
    add(point: Point) {
        return new Point(this.x + point.x, this.y + point.y);
    }
}

var p1 = new Point(0, 10);
var p2 = new Point(10, 20);
var p3 = p1.add(p2); // {x:10,y:30}
```

以及我们可爱的箭头函数：
```ts
var inc = (x) => x + 1;
```

---

# TypeScript基础
JavaScript 中的每个值会随着我们执行不同的操作表现出一系列的行为。这听起来很抽象，看下面的例子，考虑一下针对变量 message 可能执行的操作。

```ts
// 访问 message 的 toLowerCase 方法并调用它
message.toLowerCase();
// 调用 message 函数
message();
```

如果我们拆分这个过程，那么第一行代码就是访问了 message 的 toLowerCase 方法并调用它；第二行代码则尝试直接调用 message 函数。
不过让我们假设一下，我们并不知道 message 的值 —— 这是很常见的一种情况，仅从上面的代码中我们无法确切得知最终的结果。 每个操作的结果完全取决于 message 的初始值。

* message 是否可以调用？
* 它有 toLowerCase 属性吗？
* 如果有这个属性，那么 toLowerCase 可以调用吗？
* 如果 message 以及它的属性都是可以调用的，那么分别返回什么？

在编写 JavaScript 代码的时候，这些问题的答案经常需要我们自己记在脑子里，而且我们必须得祈祷自己处理好了所有细节。

<style>
  .slidev-layout h1 + p {
    opacity: 1;
  }
</style>

---

假设 message 是这样定义的：
```ts
const message = "Hello World!";
```
你可能很容易猜到，如果执行 message.toLowerCase()，我们将会得到一个所有字母都是小写的字符串。

如果执行第二行代码呢？

熟悉 JavaScript 的你肯定猜到了，这会抛出一个异常：**TypeError: message is not a function**

如果可以避免这样的错误就好了。

对于诸如 string 或者 number 这样的原始类型，我们可以通过 typeof 操作符在运行时计算出它们的类型。

但对于像函数这样的类型，并没有对应的运行时机制去计算类型。唯一的方法就是实际调用 函数。

JavaScript 只提供了动态类型 —— 执行代码，然后才能知道会发生什么事。

那么不妨采用一种替代方案，使用一个静态的类型系统，在代码实际执行前预测代码的行为。

---

# TypeScript 基础 - 静态类型检查
**静态类型系统**描述了程序运行时值的结构和行为。

在之前的例子中我们将字符串作为函数调用时，抛出了 TypeError 错误。但是很多人不希望在执行代码时看到任何错误 —— 毕竟这些都是 bug！

当我们编写新代码的时候，我们也会尽量避免引入新的 bug。

如果我们只是添加了一点代码，保存文件，重新运行代码，然后马上看到报错，那么我们或许可以快速定位到问题 —— 但这种情况毕竟只是少数。

我们可能没有全面、彻底地进行测试，以至于没有发现一些潜在错误！

像 TypeScript 这样的静态类型检查器会利用类型系统提供的信息，并在事态发展不对劲的时候告知我们。

```ts {monaco}
const message = "hello!";

message();
```

---

# TypeScript 基础 - 非异常失败
目前为止，我们讨论的都是运行时错误 —— JavaScript 运行时告诉我们，它觉得某个地方有异常。

这些异常之所以能够抛出，是因为 ECMAScript 规范 明确规定了针对异常应该表现的行为。

举个例子，规范指出，试图调用无法调用的东西应该抛出一个错误。但恰恰相反，JavaScript 的表现和我们的预想不同，它返回的是值 `undefined`。

```js
const user = {
    name: 'Daniel',
    age: 26,
};
user.location;       // 返回 undefined
```

最终，我们需要一个静态类型系统来告诉我们，哪些代码在这个系统中被标记为错误的代码 —— 即使它是不会马上引起错误的“有效” JavaScript 代码。

---

在 TypeScript 中，下面的代码会抛出一个错误，指出 location 没有定义：
```ts {monaco}
const user = {
  name: "Daniel",
  age: 26,
};

user.location;
```

虽然有时候这意味着你需要在表达的内容上进行权衡，但我们的目的是为了找到程序中更多合法的 bug。

举个例子，基本的逻辑错误：

```ts {monaco}
const value = Math.random() < 0.5 ? "a" : "b";
if (value !== "a") {
  // ...
} else if (value === "b") {
  // 永远无法到达这个分支
}
```

---

# TypeScript 基础 - TypeScript 编译器
TypeScript 编译器 —— tsc

首先，通过 npm 进行安装。
```bash
npm install -g typescript
```
<br>

> 这将全局安装 TypeScript 的编译器 tsc。如果你更倾向于安装在本地的 node_modules 文件夹中，那你可能需要借助 npx 或者类似的工具才能便捷地运行 tsc 指令。

新建一个空文件夹，尝试编写第一个 TypeScript 程序：hello.ts ：
```ts
// 和世界打个招呼
console.log('Hello world!');
```
注意这行代码没有任何多余的修饰，它看起来就和使用 JavaScript 编写的 “hello world” 程序一模一样。

现在，运行 typescript 安装包自带的 tsc 指令进行类型检查。虽然控制台没有信息输出（毕竟没有类型错误）但是得到了一个输出文件。如果查看当前目录，会发现除了 hello.ts 文件外还有一个 hello.js 文件。

---

如果检查 hello.js 文件的内容，我们可以看到 TypeScript 编译器处理完 .ts 文件后产出的内容：
```js
// 和世界打个招呼
console.log('Hello world!');
```
在这个例子中，TypeScript 几乎没有需要转译的内容，所以转译前后的代码看起来一模一样。编译器总是试图产出清晰可读的代码，这些代码看起来就像正常的开发者编写的一样。

如果我们刻意引入了一个类型检查错误呢？我们重写一下 hello.ts ：
```ts
// This is an industrial-grade general-purpose greeter function:
function greet(person, date) {
  console.log(`Hello ${person}, today is ${date}!`);
}

greet("Brendan");
```

再次执行 tsc hello.ts，那么会注意到命令行抛出了一个错误！TypeScript 告诉我们，我们少传了一个参数给 greet 函数 —— 本来应该是要传入参数的。
```bash
Expected 2 arguments, but got 1.
```

目前为止，我们编写的仍然是标准的 JavaScript 代码，但类型检查依然可以发现我们代码中的问题。

---

# TypeScript 编译器 - 报错时仍产出文件
 TypeScript 的核心原则：大多数时候，你比 TypeScript 更了解代码。

有一件事你可能没有注意到，在上面的例子中，我们的 hello.js 文件再次发生了改动。如果我们打开这个文件，会发现内容和输入的文件内容是一样的。

这可能有点出乎意料，毕竟 tsc 刚才报错了。但这种结果其实和 TypeScript 的核心原则有关：大多数时候，你比 TypeScript 更了解代码。

再次重申，对代码进行类型检查，会限制可以运行的程序的种类，因此类型检查器会进行权衡，以确定哪些代码是可以被接受的。大多数时候，这样没什么问题，但有的时候，这些检查会对我们造成阻碍。

举个例子，想象你现在正把 JavaScript 代码迁移到 TypeScript 代码，并产生了很多类型检查错误。最后，你不得不花费时间解决类型检查器抛出的错误，但问题在于，原始的 JavaScript 代码本身就是可以运行的！为什么把它们转换为 TypeScript 代码之后，反而就不能运行了呢？

所以 TypeScript 并不会对你造成阻碍。

当然，随着时间的推移，你可能希望对错误采取更具防御性的措施，同时也让 TypeScript 采取更加严格的行为。在这种情况下，你可以开启 `noEmitOnError` 编译选项。

---

# TypeScript 编译器 - 擦除类型及降级

如果我们显式地声明了类型，如：
```ts
function greet(person: string, date: Date) {
  console.log(`Hello ${person}, today is ${date.toDateString()}!`);
}

greet("Maddison", new Date());
```

但是经过 tsc 编译之后，类型会被擦除：
```js
"use strict";
function greet(person, date) {
    console.log("Hello " + person + ", today is " + date.toDateString() + "!");
}
greet("Maddison", new Date());
```

毕竟类型注解并不属于 JavaScript（或者专业上所说的 ECMAScript）的内容，所以没有任何浏览器或者运行时能够直接执行不经处理的 TypeScript 代码。
大多数 TypeScript 独有的代码都会被擦除，在这个例子中，可以看到类型注解的代码完全被擦除了。

> **记住：** 类型注解永远不会改变你的程序在运行时的行为

<style>
  .slidev-layout h1 + p {
    opacity: 1;
  }
</style>

---

上面的另一个变化，就是我们的模板字符串从：
```ts
`Hello ${person}, today is ${date.toDateString()}!`;
```
被重写为：
```js
"Hello " + person + ", today is " + date.toDateString() + "!";
```

为什么会这样子呢？

模板字符串是 ECMAScript 2015（或者 ECMAScript6、ES2015、ES6 等）引入的新特性。

TypeScript 可以将高版本 ECMAScript 的代码重写为类似 ECMAScript3 或者 ECMAScript5 （也就是 ES3 或者 ES5）这样较低版本的代码。就是所谓的**降级**。

默认情况下，TypeScript 会转化为 ES3 代码，这是一个非常旧的 ECMAScript 版本。
可以使用 `target` 选项将代码往较新的 ECMAScript 版本转换。例如通过使用 `--target es2015` 参数进行编译，我们可以得到 ECMAScript2015 版本的目标代码