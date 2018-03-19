# JavaScript 介绍

是什么让 JavaScript 如此特别？我们能用它来干什么？让我们开始探索吧！

## 什么是 JavaScript？

*JavaScript* 初衷是 *"让网页富有活力"*。

用 JavaScript 编写的程序叫做 *scripts（脚本）* ，可以直接写在 HTML 中，在网页加载时自动运行。

脚本以纯本文的形式编写与运行，不需要特别的前置处理或编译。

从名称上看，需要特别说明的是，JavaScript 与另一门叫 [Java](http://en.wikipedia.org/wiki/Java) 的语言并无太大的关系。

```smart header="为什么是 <u>Java</u>Script?"
JavaScript 在创建时，其实叫另一个名字：“LiveScript”。但是当时 Java 语言非常流行，为了沾一下 Java 的光，便有了 JavaScript 这个名字。

但是 JavaScript 在多年的发展中，已经成为一门完全独立的语言，也有了官方规范 [ECMAScript](http://en.wikipedia.org/wiki/ECMAScript) ，所以现在和 Java 并无关系。
```

目前，JavaScript 不仅能在 web 浏览器中运行，也能在服务器运行。实际上，任何带有一个叫 [JavaScript 引擎](https://en.wikipedia.org/wiki/JavaScript_engine) 的程序的设备，均可运行 JavaScript。

Web 浏览器有一个内置的 JavaScript 引擎，有时候也被称为 “JavaScript 虚拟机”。

不同的引擎具有不同的 “代号”，例如：

- [V8](https://en.wikipedia.org/wiki/V8_(JavaScript_engine)) -- 运行于谷歌 Chrome 浏览器和 Opera 浏览器中。
- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) -- 运行于火狐 （Firefox）浏览器中。
- ...还有运行于不同版本的 IE 浏览器中的 "Trident" 和 "Chakra" 引擎；运行于微软 Edge 浏览器中的 "ChakraCore" 引擎，运行于 Safari 浏览器中的 "Nitro" 和 "SquirrelFish" 引擎等。

以上列举的都是大众熟知的 JavaScript 引擎，因为它们经常出现在开发者的技术文章中。我们也将会使用它们，举个例子：如果你看到 “某特性被 V8 支持”，通常意味着这个特性可以在谷歌 Chrome 浏览器和 Opera 浏览器很好地工作。

```smart header="引擎是怎样工作的？"

引擎总体上是很复杂的，但是基础理论很简单。

1. 引擎（在浏览器中是内置的）解析（parses）脚本文件。
2. 然后编译（compile）脚本为机器码。
3. 最后运行机器码，性能极高。

引擎在各个环节都会做性能优化。甚至，引擎会在代码运行的时候，观察分析其中的数据，然后为机器码做优化。所以，脚本的最终运行是很快的。
```

## 浏览器中的 JavaScript 能做什么？

现代的 JavaScript 是一门 “安全” 的编程语言，没有提供低级的访问内存或者 CPU 的 api，毕竟，最开始为 web 浏览器而创建的语言并不需要这些。

JavaScript 的能力很大程度上取决于运行环境。比如，[Node.JS](https://wikipedia.org/wiki/Node.js) 就提供了丰富的函数库，让 JavaScript 拥有读写任意文件、管理网络请求等能力。

Web 浏览器中的 JavaScript 能做任何跟网页操作、与用户交互和与服务器交互相关的事情。

比如，web 浏览器中的 JavaScript 能做：

- 添加新的 HTML 代码到页面上、改变已有的内容与样式。
- 响应用户的操作，在鼠标点击、触控板移动和键盘按下时给用户反馈。
- 利用互联网向远程服务器发出请求，下载或上传文件（也就是所谓的 [AJAX](https://en.wikipedia.org/wiki/Ajax_(programming)) 和 [COMET](https://en.wikipedia.org/wiki/Comet_(programming)) 技术）
- 获取与设置 cookies、向网页访问者询问信息、展示信息。
- 在客户端 （浏览器）存储数据（"local storage"）。

## 浏览器中的 JavaScript 不能做什么?

为了用户的安全，JavaScript 的能力被浏览器限制。这些限制的目的是防止恶意的网页获取用户的私密信息或者损害用户的数据。

以下是这些限制的例子：

- 网页上的 JavaScript 不能读写、复制或执行硬盘上任意的文件；不能直接访问操作系统函数。

    现代的浏览器允许 JavaScript 代码操作文件，但只能做受限的操作，而且仅仅发生在用户做出特定的操作后，比如拖放一个文件到浏览器窗口或在 `<input>` 标签中选择一个文件。

    即使有很多方式去操作相机、话筒等设备，但是都需要用户的许可。所以一个使用了 JavaScript 的网页是无法偷偷地打开摄像头，监听并发送数据给 [NSA](https://en.wikipedia.org/wiki/National_Security_Agency) 的。

- 不同的标签（tabs）/ 窗口通常是无法感知彼此的存在的。虽然有时候确实可以，比如某个窗口用 JavaScript 去打开一个新窗口时，但是即使在这种情况下，只要网页属于不同的网站（网址、端口或协议不同），JavaScript 就不能访问另一个窗口。

    这个特性被称为 “同源策略”。利用此特性时，*两个网页* 都必须包含特定的 JavaScript 代码去处理数据交换。

    这个特性也是为了用户的安全。一个用户打开的来自 `http://anysite.com` 的网页，不能访问并盗取另一个浏览器标签（tab）里来自 URL `http://gmail.com` 的网页的信息。
    
- JavaScript 可以很容易地与当前网页相同来源的服务器通信，但是和其它网站/网址收发数据的能力则是受限的。虽然可以实现，但是需要远程服务器很明确的许可（通过 HTTP 头信息（headers）传达）。当然，这也是一种安全限制。

![](limitations.png)

当 JavaScript 运行于浏览器之外时，这些限制可能并不存在，比如在服务器上运行的 JavaScript 就没有这些限制。现代的浏览器均支持安装插件，可能会给插件额外的能力许可。

## 为什么 JavaScript 独一无二?

关于 JavaScript ，至少有三个伟大的特性：

```compare
+ 可与 HTML、CSS 完美组合
+ 简洁优雅
+ 被主流浏览器支持并且默认打开
```

而且，这三个特性仅存于 JavaScript ，没有其它浏览器技术可以匹敌。

正是这些原因成就了 JavaScript 的独一无二，使其成为构建浏览器交互的传播最广的工具。

在计划学习一门新的技术的时候，从宏观的角度了解一遍是非常有好处的。接下来让我们看看新语言和浏览器能力的现代化趋势吧。

## 构建于 JavaScript “之上” 的语言

JavaScript 的语法并不能满足每一个人的需求，不同的人想要不同的特性。

这是预料之中的，毕竟项目与需求对每个人来说都是不同的。

所以近期出现了许多新的语言，它们会先 *转换* (transpiled) 为 JavaScript 以便能在浏览器运行。

现代的工具能够快速并且透明地完成这些转换，也就是说，可以让开发者以另一种语言编写代码而且 “背地里” 自动完成转换。

以下是这样的语言的例子:

- [CoffeeScript](http://coffeescript.org/) 是 JavaScript 的语法糖, 引入了简洁的语法，让开发者得以编写简练的代码。通常 Ruby 开发者会喜欢此语言.
- [TypeScript](http://www.typescriptlang.org/) 致力于给 JavaScript 增加 “强类型” 的特性，以简化开发工作并且让程序更可靠地运行于复杂的系统中。这是微软公司主导开发的。
- [Dart](https://www.dartlang.org/) 是一个独立的语言，它有自己的运行于非浏览器环境（比如手机app）的引擎。它最开始是由谷歌提供的一个 JavaScript 替代品，但到目前为止，它仍需要转换为 JavaScript 才能在浏览器上运行，就跟以上语言一样。

这样的语言其实还有很多。当然，就算我们使用这些语言的其中一个，我们也要了解 JavaScript ，这样才能真正理解我们在做什么。

## 总结

- JavaScript 最初创建时只能在浏览器上运行，但是现在已经可以运行在很多其它环境了。
- 就目前来看，JavaScript 与 HTML/CSS 完美结合的能力，使其成为最广为认可的浏览器语言，演绎着独一无二的角色。
- 现在有许多语言可以 “转换” （transpiled）为 JavaScript，推荐大家在掌握 JavaScript 之后去了解一下。
