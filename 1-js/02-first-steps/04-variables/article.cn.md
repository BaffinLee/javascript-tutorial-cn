# 变量

大多数时候，JavaScript 程序需要加工数据。比如：

1. 网上商城 -- 数据可能包括售卖的商品以及购物车。
2. 聊天程序 -- 数据可能包括用户、聊天信息等。

变量就是用来存储数据的。

## 变量

一个 [变量](https://en.wikipedia.org/wiki/Variable_(computer_science)) 代表存储数据的 “具名仓库”。我们可以用变量来存储商品、访问者以及其它数据。

在 JavaScript 中，使用 `let` 关键字申明变量。

下面的语句会创建（或者叫 *申明* 、 *定义*）一个叫做 “message” 的变量。

```js
let message;
```

现在我们可以用赋值运算符 `=` 往变量里存放数据。

```js
let message;

*!*
message = 'Hello'; // 存储这个字符串
*/!*
```

这个字符串现在已经载入内存中，并且与这个变量关联起来。我们可以用这个变量名去访问它：

```js run
let message;
message = 'Hello!';

*!*
alert(message); // 弹出变量的值
*/!*
```

为了简洁，我们可以让变量的申明与赋值在同一行完成：

```js run
let message = 'Hello!'; // 申明变量并赋值

alert(message); // Hello!
```

我们也可以在同一行申明多个变量：

```js no-beautify
let user = 'John', age = 25, message = 'Hello';
```

这样或许会简洁一点，但是并不推荐这样做。为了可读性，请让每个变量申明占用一行。

多行的变量申明确实会长一点，但是可读性更高：

```js
let user = 'John';
let age = 25;
let message = 'Hello';
```

有些人可能会这样什么多个变量：

```js no-beautify
let user = 'John',
  age = 25,
  message = 'Hello';
```

...或者是 “逗号前置” 的风格：

```js no-beautify
let user = 'John'
  , age = 25
  , message = 'Hello';
```

从技术上来说，这些写法所达到的效果都是一样的。所以，还是看个人的偏好与审美。

````smart header="`var` 还是 `let` ？"
在旧一点的代码里，你可能会看到另一个关键字：`var`，而不是 `let`：

```js
*!*var*/!* message = 'Hello';
```

`var` 关键字 *基本上* 和 `let` 是一样的。它也是用来申明变量的，但是有轻微的不同，比较 “old school”。

`let` 与 `var` 之间有轻微的不同，但是目前并不会影响到我们。我们会在后面的 <info:var> 章节中详细讲解。
````

## 现实写照

如果把 “变量” 想象成一个贴着唯一名称贴纸的装载数据的 “盒子”，我们可很容易理解它的意义。

比如，`message` 变量就可以想象成贴着 `"message"` 标签的、存储值为 `"Hello!"` 的盒子。

![](variable.png)

我们可以把任何值放入盒子中。

当然我们也可以改变盒子里的值，随便改多少次：

```js run
let message;

message = 'Hello!';

message = 'World!'; // 值被改变

alert(message);
```

当变量值改变时，旧的数据被移除：

![](variable-change.png)

我们也可以申明两个变量，然后复制其中一个的值给另一个。

```js run
let hello = 'Hello world!';

let message;

*!*
// 从 hello 复制 'Hello world' 数据 到 message
message = hello;
*/!*

// 现在两个变量的值相同
alert(hello); // Hello world!
alert(message); // Hello world!
```

```smart header="函数式语言"
有趣的是，有一些
It may be interesting to know that there also exist [函数式](https://en.wikipedia.org/wiki/Functional_programming) 编程语言不允许改变变量的值。比如：[Scala](http://www.scala-lang.org/) 和 [Erlang](http://www.erlang.org/)。

在这些语言里，变量一旦赋值就不能再改变。如果我们要存储别的数据，语言会强制我们创建一个新的盒子（申明一个新变量），而不能复用旧的。

第一眼看起来会很奇怪，但是这些语言很适合严谨编程。而且，在某些方面，比如并行计算，这种 “缺点” 会带来特定的优势。推荐大家去学习一下函数式语言（即使你不打算用它），宽阔视野。
```

## 变量命名 [#variable-naming]

There are two limitations for a variable name in JavaScript:

1. The name must contain only letters, digits, symbols `$` and `_`.
2. The first character must not be a digit.

Valid names, for instance:

```js
let userName;
let test123;
```

When the name contains multiple words, [camelCase](https://en.wikipedia.org/wiki/CamelCase) is commonly used. That is: words go one after another, each word starts with a capital letter: `myVeryLongName`.

What's interesting -- the dollar sign `'$'` and the underscore `'_'` can also be used in names. They are regular symbols, just like letters, without any special meaning.

These names are valid:

```js run untrusted
let $ = 1; // declared a variable with the name "$"
let _ = 2; // and now a variable with the name "_"

alert($ + _); // 3
```

Examples of incorrect variable names:

```js no-beautify
let 1a; // cannot start with a digit

let my-name; // a hyphen '-' is not allowed in the name
```

```smart header="Case matters"
Variables named `apple` and `AppLE` -- are two different variables.
```

````smart header="Non-english letters are allowed, but not recommended"
It is possible to use any language, including cyrillic letters or even hieroglyphs, like this:

```js
let имя = '...';
let 我 = '...';
```

Technically, there is no error here, such names are allowed, but there is an international tradition to use English in variable names. Even if we're writing a small script, it may have a long life ahead. People from other countries may need to read it some time.
````

````warn header="Reserved names"
There is a list of reserved words, which cannot be used as variable names, because they are used by the language itself.

For example, words `let`, `class`, `return`, `function` are reserved.

The code below gives a syntax error:

```js run no-beautify
let let = 5; // can't name a variable "let", error!
let return = 5; // also can't name it "return", error!
```
````

````warn header="An assignment without `use strict`"

Normally, we need to define a variable before using it. But in the old times, it was technically possible to create a variable by a mere assignment of the value, without `let`. This still works now if we don't put `use strict`. The behavior is kept for compatibility with old scripts.

```js run no-strict
// note: no "use strict" in this example

num = 5; // the variable "num" is created if didn't exist

alert(num); // 5
```

That's a bad practice, it gives an error in the strict mode:

```js run untrusted
"use strict";

*!*
num = 5; // error: num is not defined
*/!*
```

````

## Constants

To declare a constant (unchanging) variable, one can use `const` instead of `let`:

```js
const myBirthday = '18.04.1982';
```

Variables declared using `const` are called "constants". They cannot be changed. An attempt to do it would cause an error:

```js run
const myBirthday = '18.04.1982';

myBirthday = '01.01.2001'; // error, can't reassign the constant!
```

When a programmer is sure that the variable should never change, he can use `const` to guarantee it, and also to clearly show that fact to everyone.


### Uppercase constants

There is a widespread practice to use constants as aliases for difficult-to-remember values that are known prior to execution.

Such constants are named using capital letters and underscores.

Like this:

```js run
const COLOR_RED = "#F00";
const COLOR_GREEN = "#0F0";
const COLOR_BLUE = "#00F";
const COLOR_ORANGE = "#FF7F00";

// ...when we need to pick a color
let color = COLOR_ORANGE;
alert(color); // #FF7F00
```

Benefits:

- `COLOR_ORANGE` is much easier to remember than `"#FF7F00"`.
- It is much easier to mistype in `"#FF7F00"` than in `COLOR_ORANGE`.
- When reading the code, `COLOR_ORANGE` is much more meaningful than `#FF7F00`.

When should we use capitals for a constant, and when should we name them normally? Let's make that clear.

Being a "constant" just means that the value never changes. But there are constants that are known prior to execution (like a hexadecimal value for red), and there are those that are *calculated* in run-time, during the execution, but do not change after the assignment.

For instance:
```js
const pageLoadTime = /* time taken by a webpage to load */;
```

The value of `pageLoadTime` is not known prior to the page load, so it's named normally. But it's still a constant, because it doesn't change after assignment.

In other words, capital-named constants are only used as aliases for "hard-coded" values.  

## Name things right

Talking about variables, there's one more extremely important thing.

Please name the variables sensibly. Take time to think if needed.

Variable naming is one of the most important and complex skills in programming. A quick glance at variable names can reveal which code is written by a beginner and which by an experienced developer.

In a real project, most of the time is spent on modifying and extending the existing code base, rather than writing something completely separate from scratch. And when we return to the code after some time of doing something else, it's much easier to find information that is well-labeled. Or, in other words, when the variables have good names.

Please spend some time thinking about the right name for a variable before declaring it. This will repay you a lot.

Some good-to-follow rules are:

- Use human-readable names like `userName` or `shoppingCart`.
- Stay away from abbreviations or short names like `a`, `b`, `c`, unless you really know what you're doing.
- Make the name maximally descriptive and concise. Examples of bad names are `data` and `value`. Such a name says nothing. It is only ok to use them if it's exceptionally obvious from the context which data or value is meant.
- Agree on terms within your team and in your own mind. If a site visitor is called a "user" then we should name related variables like `currentUser` or `newUser`, but not `currentVisitor` or a `newManInTown`.

Sounds simple? Indeed it is, but creating good descriptive-and-concise names in practice is not. Go for it.

```smart header="Reuse or create?"
And the last note. There are some lazy programmers who, instead of declaring a new variable, tend to reuse the existing ones.

As a result, the variable is like a box where people throw different things without changing the sticker. What is inside it now? Who knows... We need to come closer and check.

Such a programmer saves a little bit on variable declaration, but loses ten times more on debugging the code.

An extra variable is good, not evil.

Modern JavaScript minifiers and browsers optimize code well enough, so it won't create performance issues. Using different variables for different values can even help the engine to optimize.
```

## Summary

We can declare variables to store data. That can be done using `var` or `let` or `const`.

- `let` -- is a modern variable declaration. The code must be in strict mode to use `let` in Chrome (V8).
- `var` -- is an old-school variable declaration. Normally we don't use it at all, but we'll cover subtle differences from `let` in the chapter <info:var>, just in case you need them.
- `const` -- is like `let`, but the value of the variable can't be changed.

Variables should be named in a way that allows us to easily understand what's inside.
