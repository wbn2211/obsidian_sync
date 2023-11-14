# git commit 规范

---
tag:
#学习 #编程 #git_commit 

---
学习目标：

1. 规范代码提交
2. 总结并清晰表达自己的提交

---

## 1.1 commit message格式

```text
<type>(<scope>): <subject>
```

## 1.2 type(必须)

用于说明 git commit 的类别，只允许使用下面的标识。

`feat` ：新功能（ feature ）。

`fix/to` ：修复bug，可以是 Q/A 发现的BUG，也可以是研发自己发现的 BUG 。

-   `fix` ：产生diff并自动修复此问题。适合于一次提交直接修复问题
-   `to` ：只产生diff不自动修复此问题。适合于多次提交。最终修复问题提交时使用 `fix`

`docs` ：文档（ documentation ）。

`style` ：格式（不影响代码运行的变动）。

`refactor` ：重构（即不是新增功能，也不是修改 bug 的代码变动）。

`perf` ：优化相关，比如提升性能、体验。

`test` ：增加测试。

`chore` ：构建过程或辅助工具的变动。

`revert` ：回滚到上一个版本。

`merge` ：代码合并。

`sync` ：同步主线或分支的 bug 。

## scope(可选)

`scope` 用于说明 commit 影响的范围，比如数据层、控制层、视图层等等，视项目不同而不同。

例如在 Angular，可以是 location ， browser ， compile ， compile ， rootScope ，  ngHref ， ngClick ， ngView 等。如果你的修改影响了不止一个 scope ，你可以使用*代替。

## subject(必须)

`subject` 是 commit 目的的简短描述，不超过50个字符。

建议使用中文（感觉中国人用中文描述问题能更清楚一些）。

-   结尾不加句号或其他标点符号。
-   根据以上规范 git commit message 将是如下的格式：

```text
fix(DAO) :用户查询缺少 username 属性 
feat(Controller) :用户查询接口开发
```

## 好处

-   便于程序员对提交历史进行追溯，了解发生了什么情况。
-   一旦约束了commit message ，意味着我们将慎重的进行每一次提交，不能再一股脑的把各种各样的改动都放在一个 git commit 里面，这样一来整个代码改动的历史也将更加清晰。
-   格式化的 commit message 才可以用于自动化输出 Change log 。
