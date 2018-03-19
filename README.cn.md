
# 现代 JavaScript 教程

此仓库为现代 javascript 教程中文翻译，fork 自[英文版仓库 https://github.com/iliakan/javascript-tutorial-en](https://github.com/iliakan/javascript-tutorial-en)，英文版发布于 [https://javascript.info](https://javascript.info).

## 翻译

已发布:
- 俄语: [https://github.com/iliakan/javascript-tutorial-ru](https://github.com/iliakan/javascript-tutorial-ru).
- 英语：[https://github.com/iliakan/javascript-tutorial-en](https://github.com/iliakan/javascript-tutorial-en).

完善中:
- 中文: [https://github.com/BaffinLee/javascript-tutorial-cn](https://github.com/BaffinLee/javascript-tutorial-cn), 有意翻译请提交PR（译者附：原作者自己有个中文版的仓库，但是基本没有维护，而且翻译方式是覆盖式的，不利于拉取上游的更新，所以我自己建了一个）.
- 西班牙语: [https://github.com/lmauromb/javascript-tutorial-es](https://github.com/lmauromb/javascript-tutorial-es).

如果你想要翻译此项目为你熟悉的语言的话，直接 fork 英文版仓库进行翻译。我（原作者）可以帮你附上你的信息发布在类似 fr.javascript.info 的域名上，当然你也可以发布在自己域名上。

你也可以给此文件提交PR，以此表示你的翻译版本正在进行中。

提示：你可以在本地运行此项目，参见 <https://github.com/iliakan/javascript-tutorial-server/>.

## 项目结构

每一个章节、文章或者习题都有自己的文件夹。

文件夹的命名方式类似于 `N-url` , `N` 是一个数字，代表顺序； `url` 代表章节、文章的 URL。

文件结构如下:

  - `index.md` 代表一个章节
  - `article.md` 代表一篇文章
  - `task.md` 代表习题 （习题答案在 `solution.md` 文件中）

每个文件均以 `# Main header` 开头。

所需的附件应该放在同一个文件夹中。
