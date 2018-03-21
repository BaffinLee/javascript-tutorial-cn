# Hello, world!

此教程讲的是与平台无关的 JavaScript 核心知识，将来你可能会学习并使用 Node.JS 与其它平台。

但是，我们需要一个环境去运行我们的代码，加上此教程又是在线的，这时候浏览器就是一个很好的选择。我们会尽可能少地使用依赖于浏览器环境的命令/函数（比如 `alert` ），这样如果你计划在其它平台（比如 Node.JS ）上使用 JavaScript 的话，就不用关心无关的内容。而且，浏览器相关知识会在教程的 [下一章](/ui) 里详细介绍。

在开始前，让我们先学习怎么把脚本附到网页中去吧。对于服务端环境，你可以直接用命令行运行脚本，比如 Node.JS 是 `node my.js` 。

## "script" 标签

在 `<script>` 的帮助下，JavaScript 程序可以放到到 HTML 文档的任何部位。

举个例子：

```html run height=100
<!DOCTYPE HTML>
<html>

<body>

  <p>script 标签前面...</p>

*!*
  <script>
    alert( 'Hello, world!' );
  </script>
*/!*

  <p>...script 标签后面.</p>

</body>

</html>
```

```online
你可以点击代码块右上角的 “运行” 按钮在线运行此示例。
```

`<script>` 标签里包含的 JavaScript 代码会在浏览器遇到此标签时自动执行。

## 现代化

`<script>` 有几个现在已经很少用到的属性，我们可能会在旧代码里看到。

 `type` 属性：<code>&lt;script <u>type</u>=...&gt;</code>

 旧的 HTML4 标准规定 `script` 标签必须申明一个类型（type），通常来说是 `type="text/javascript"`。现代浏览器都默认是此类型，所以不再需要指定。

 `language` 属性： <code>&lt;script <u>language</u>=...&gt;</code>

 这个属性表名脚本的语言，现在语言默认是 JavaScript ，这个属性已经没有意义，也就不需要了。

脚本前后的注释。
在远古时期的教程和书籍里，可能出现会像下面这样的在 `<script>` 里面加上 HTML 注释的代码示例：

 ```html no-beautify
 <script type="text/javascript"><!--
     ...
 //--></script>
 ```

 这个注释是用来在不支持 `<script>` 标签的旧浏览器里隐藏代码。事实证明，在过去 15 年里涌现的浏览器均没有问题。在此顺便说一下，如果你在哪里看到这样的注释，很可能意味着：这是远古时期的代码，不值得一看。

## 外部脚本

如果我们有大量的 JavaScript 代码的话，可以把代码放入一个单独的文件中。

脚本文件依靠 `src` 属性附到 HTML 页面中。

```html
<script src="/path/to/script.js"></script>
```

这里的 `/path/to/script.js` 是一个指向脚本文件的绝对路径（网站根目录）。

当然也可以指定一个相对于当前页面的相对路径。比如：`src="script.js"` 则代表当前文件夹下的 `"script.js"` 文件。

我们也可以指定一个完整的 URL，比如：

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/lodash.js/3.2.0/lodash.js"></script>
```

需要多个脚本的话，加上多个标签即可：

```html
<script src="/js/script1.js"></script>
<script src="/js/script2.js"></script>
…
```

```smart
最佳实践：简单的脚本才直接写在 HTML 里，复杂一点的都应该放在单独的文件中。

好处是单独的文件在被浏览器下载后会存入 [缓存，cache](https://en.wikipedia.org/wiki/Web_cache)。

之后，别的页面需要相同的脚本文件时，浏览器只需要从缓存中加载而不是再下载一次。所以文件其实只会下载一次。

这减少了网络传输，让网页以更快的速度呈现。
```

````warn header="如果设置了 `src` 属性的话, `script` 标签里面的脚本会被忽略。"

这样是不行的:

```html
<script src="file.js">
  alert(1); // 里面的代码会被忽略，因为设置了 src 属性
</script>
```

我们必须在外置脚本 `<script src="…">` 和 `<script>` 内联脚本之间选一个。

下面这个分开的例子是可以的：

```html
<script src="file.js"></script>
<script>
  alert(1);
</script>
```
````

## 总结

- 我们可以使用 `<script>` 标签把 JavaScript 代码附于网页中。
- 不需要设置 `type` 和 `language` 属性。
- 脚本可以放在单独的文件中，通过 `<script src="path/to/script.js"></script>` 引入。

关于浏览器脚本与页面交互有很多东西可以学，但是鉴于本章是 JavaScript 语言的教程，我们就先不分心讲其它的了。我们用浏览器运行 JavaScript 代码是为了方便阅读，你要明白这只是众多方式中的一种。
