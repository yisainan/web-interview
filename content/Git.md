# [返回主页](https://github.com/yisainan/web-interview/blob/master/README.md)

<b><details><summary>1. 简单对比 git pull 和 git pull --rebase 的使用</summary></b>

参考答案：

git pull = git fetch + git merge
git pull --rebase = git fetch + git rebase

解析：现在来看看[git merge 和 git rebase 的区别](https://www.cnblogs.com/kevingrace/p/5896706.html)

[参与互动](https://github.com/yisainan/web-interview/issues/997)

</details>

<b><details><summary>2. 什么时候使用“git rebase”代替“git merge”？</summary></b>

参考答案：你自己开发分支一直在做，然后你想把主线的修改合到你的分支上，做一次集成，这种情况就用rebase比较好，把你的提交都放在主线修改的头上

1. rebase会把你当前分支的commit放到公共分支的最后，所以叫做变基。就如同你从公共分支又重新拉出来这个分支一样。
2. merge会把公共分支和你当前的commit合并在一起，形成一个新的commit提交。

[参与互动](https://github.com/yisainan/web-interview/issues/998)

</details>

<b><details><summary>3. “拉取请求（pull request）”和“分支（branch）”之间有什么区别？</summary></b>

参考答案：

* 分支（branch） 是代码的一个独立版本。

* 拉取请求（pull request） 是当有人用仓库，建立了自己的分支，做了些修改并合并到该分支（把自己修改应用到别人的代码仓库）。

[参与互动](https://github.com/yisainan/web-interview/issues/999)

</details>

<b><details><summary>4. 什么是 Git 复刻（fork）？复刻（fork）、分支（branch）和克隆（clone）之间有什么区别？</summary></b>

参考答案：

* 复刻（fork） 是对存储仓库（repository）进行的远程的、服务器端的拷贝，从源头上就有所区别。复刻实际上不是 Git 的范畴。它更像是个政治/社会概念。

* 克隆（clone） 不是复刻，克隆是个对某个远程仓库的本地拷贝。克隆时，实际上是拷贝整个源存储仓库，包括所有历史记录和分支。

* 分支（branch） 是一种机制，用于处理单一存储仓库中的变更，并最终目的是用于与其他部分代码合并。

[参与互动](https://github.com/yisainan/web-interview/issues/1000)

</details>

<b><details><summary>5. 使用过 git cherry-pick，有什么作用？</summary></b>

参考答案：

命令 git cherry-pick 通常用于把特定提交从存储仓库的一个分支引入到其他分支中。常见的用途是从维护的分支到开发分支进行向前或回滚提交。
这与其他操作（例如：合并（merge）、变基（rebase））形成鲜明对比，后者通常是把许多提交应用到其他分支中。

```
git cherry-pick <commit-hash>
```

步骤：

1.先使用 git log 命令（或 git reflog ）获取提交的记录，然后找到我们对应想要的那个 commit 的 SHA 。
2.再使用 git checkout 命令切换到我们需要提交这个 commit 的新分支。
3.最后再使用 git cherry-pick xxxxxxxxx 将你想要的那个 commit 的内容合并到新分支即可
————————————————
版权声明：本文为CSDN博主「码飞_CC」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/cc18868876837/article/details/108402798

[参与互动](https://github.com/yisainan/web-interview/issues/1001)

</details>

<b><details><summary>6. git 跟其他版本控制器有啥区别？</summary></b>

参考答案：

Git比svn快，而且更加的流畅。

Git在本地就可以使用，可以随便保存各种历史记录，不用担心污染服务器。

Git在branch和branch之间切换非常简单。

Git没有被lock不能commit 的情况。

[参与互动](https://github.com/yisainan/web-interview/issues/1002)

</details>

<b><details><summary>7. 我们在本地工程常会修改一些配置文件，这些文件不需要被提交，而我们又不想每次执行 git status 时都让这些文件显示出来，我们该如何操作？</summary></b>

参考答案：在 Git 工作区的跟目录下创建一个特殊的. gitignore 文件，然后把忽略的文件名编辑进去，Git 就会自动忽略这些文件。

[参与互动](https://github.com/yisainan/web-interview/issues/1003)

</details>

<b><details><summary>8. 如何把本地仓库的内容推向一个空的远程仓库？</summary></b>

参考答案：

git init //生成. git 文件
git remote add origin 远程仓库地址 // 将本地和远程厂库关联起来
git add . 
git commit -m '提交信息'
git push origin master // 将本地代码推送到库上

[参与互动](https://github.com/yisainan/web-interview/issues/1004)

</details>

<b><details><summary>9. 提交时发生冲突，你能解释冲突是如何产生的吗？你是如何解决的？</summary></b>

参考答案：

#### 1. 冲突是如何产生的

我们都知道，Git 的实现途径是 1 棵树。比如有一个节点树(point1), 

* 我们基于 point1 进行开发，开发出了结点 point2；
* 我们基于 point1 进行开发，开发出了结点 point3；

  如果我们在 point2 和 point3 内操作了同一类元素，那么势必会导致冲突的存在。
  主要的思想如下图 1 所示:

point1. js

```js
function test() {
    console.log(a);
    var a = 1;
}
```

人物甲 更新了版本 2
代码: poin2. js

```js
function test() {
    console.log(a);
    var a = 2;
}
```

人物乙 更新了版本 3
代码: poin3. js

```js
function test() {
    console.log(a);
    var a = 3;
}
```

场景如下，甲乙都是根据 point. js 文件进行了开发。甲开发出了版本 2，并且提交了代码；乙开发出了版本 3，也需要提交了代码，此时将会报错存在冲突。

为什么呢？因为甲开发完了版本，提交了版本之后，此时远端的代码已经是版本 2 点代码了，而乙是基于版本 1 进行的开发出了版本 3。所以，乙想要提交代码，势必要将自己的代码更新为版本 2 的代码，然后再进行提交，如果存在冲突则解决冲突后提交

#### 2. 冲突是如何解决的

上面已经详细的说明了冲突时如何产生的，那么又该如何解决冲突呢?

解决冲突通常使用如下的步骤即可:

* 情况 1 无冲突

先拉取远端的代码，更新本地代码。然后提交自己的更新代码即可。

* 情况 2 有冲突

拉取远端代码。存在冲突，会报错。
此时我们需要将本地代码暂存起来 stash；
更新本地代码，将本地代码版本更新和远端的代码一致即可；
将暂存的代码合并到更新后的代码后，有冲突解决冲突(需要手动进行解决冲突)；
提交解决冲突后的代码。

[参与互动](https://github.com/yisainan/web-interview/issues/1005)

</details>

<b><details><summary>10. 列举工作中常用的几个 git 命令？</summary></b>

参考答案：

```
git init                     // 新建 git 代码库
git add                      // 添加指定文件到暂存区
git rm                       // 删除工作区文件，并且将这次删除放入暂存区
git commit -m [message]      // 提交暂存区到仓库区
git branch                   // 列出所有分支
git checkout -b [branch]     // 新建一个分支，并切换到该分支
git status                   // 显示有变更的文件
```
详细资料可以参考：
[《常用 Git 命令清单》](http://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html)

[参与互动](https://github.com/yisainan/web-interview/issues/1006)

</details>

<b><details><summary>11. git提交代码时候写错commit信息后，如何重新设置commit信息？</summary></b>

参考答案：可以通过git commit --amend 来对本次commit进行修改。

[参与互动](https://github.com/yisainan/web-interview/issues/1007)

</details>

<b><details><summary>12. 说明新建一个GIT功能分支的步骤，提供每个步骤的指令，并对指令进行说明</summary></b>

参考答案：

git branch name     创建名字为name的branch

git checkout xxx_dev    切换到名字为xxx_dev的分支

git pull    从远程分支拉取代码到本地分支

git checkout -b main_furture_xxx    创建并切换到main_furture_xxx

git push origin main_furture_xxx    执行推送的操作，完成本地分支向远程分支的同步

[参与互动](https://github.com/yisainan/web-interview/issues/1008)

</details>

<b><details><summary>13. 说明git合并的两种方法以及区别</summary></b>

参考答案：

git代码合并有两种：git Merge 和 git ReBase

Git Merge：这种合并方式是将两个分支的历史合并到一起，现在的分支不会被更改，它会比对双方不同的文件缓存下来，生成一个commit，去push。

Git ReBase：这种合并方法通常被称为“衍合”。他是提交修改历史，比对双方的commit，然后找出不同的去缓存，然后去push，修改commit历史。

[参与互动](https://github.com/yisainan/web-interview/issues/1009)

</details>

<b><details><summary>14. 如何查看文件的提交历史和分支的提交历史</summary></b>

参考答案：

使用git log查看文件提交历史

git log filename

使用git log查看分支提交历史

git log branch file

[参与互动](https://github.com/yisainan/web-interview/issues/1010)

</details>

<b><details><summary>15. 当GIT出现如下情况时，该如何处理？</summary></b>

## your-branch-is-ahead-of-origin-master-by-3-commits

参考答案：

Git commit

Git pull

Git push

[参与互动](https://github.com/yisainan/web-interview/issues/1011)

</details>

<b><details><summary>16. 如何从 git 中删除文件，而不将其从文件系统中删除？</summary></b>

参考答案：

如果你在 git add 过程中误操作，你最终会添加不想提交的文件。但是，git rm 则会把你的文件从你暂存区（索引）和文件系统（工作树）中删除，这可能不是你想要的。

换成 git reset 操作：

```

git reset filename          # or
echo filename >> .gitingore # add it to .gitignore to avoid re-adding it
```

上面意思是， `git reset <paths>` 是 `git add <paths>` 的逆操作

[参与互动](https://github.com/yisainan/web-interview/issues/1011)

</details>

<b><details><summary>17. 什么时候应使用 “git stash”？</summary></b>

参考答案：

git stash 命令把你未提交的修改（已暂存（staged）和未暂存的（unstaged））保存以供后续使用，以后就可以从工作副本中进行还原。

[参与互动](https://github.com/yisainan/web-interview/issues/1011)

</details>

<b><details><summary>18. 你能解释下 Gitflow 工作流程吗？</summary></b>

参考答案：

Gitflow 工作流程使用两个并行的、长期运行的分支来记录项目的历史记录，分别是 master 和 develop 分支。

* Master，随时准备发布线上版本的分支，其所有内容都是经过全面测试和核准的（生产就绪）。

Hotfix，维护（maintenance）或修复（hotfix）分支是用于给快速给生产版本修复打补丁的。修复（hotfix）分支很像发布（release）分支和功能（feature）分支，除非它们是基于 master 而不是 develop 分支。

* Develop，是合并所有功能（feature）分支，并执行所有测试的分支。只有当所有内容都经过彻底检查和修复后，才能合并到 master 分支。

Feature，每个功能都应留在自己的分支中开发，可以推送到 develop 分支作为功能（feature）分支的父分支。

[参与互动](https://github.com/yisainan/web-interview/issues/1011)

</details>

<b><details><summary>19. Git 中 HEAD、工作树和索引之间的区别？</summary></b>

参考答案：

* 该工作树/工作目录/工作空间是你看到和编辑的（源）文件的目录树。
* 该索引/中转区（staging area）是个在 /. git/index，单一的、庞大的二进制文件，该文件列出了当前分支中所有文件的 SHA1 检验和、时间戳和文件名，它不是个带有文件副本的目录。
* HEAD是当前检出分支的最后一次提交的引用/指针。

[参与互动](https://github.com/yisainan/web-interview/issues/1011)

</details>

<b><details><summary>20. 解释 Forking 工作流程的优点？</summary></b>

参考答案：

* Forking 工作流程 与其他流行的 Git 工作流程有着根本的区别。它不是用单个服务端仓库充当“中央”代码库，而是为每个开发者提供自己的服务端仓库。Forking 工作流程最常用于公共开源项目中。

* Forking 工作流程的主要优点是可以汇集提交贡献，又无需每个开发者提交到一个中央仓库中，从而实现干净的项目历史记录。开发者可以推送（push）代码到自己的服务端仓库，而只有项目维护人员才能直接推送（push）代码到官方仓库中。

* 当开发者准备发布本地提交时，他们的提交会推送到自己的公共仓库中，而不是官方仓库。然后他们向主仓库提交请求拉取（pull request），这会告知项目维护人员有可以集成的更新。

[参与互动](https://github.com/yisainan/web-interview/issues/1011)

</details>

<b><details><summary>21. 我想丢弃本地未提交的变化(uncommitted changes)</summary></b>

参考答案：

> git reset --hard HEAD^

</details>

<b><details><summary>22. 我意外的做了一次硬重置(hard reset)，我想找回我的内容</summary></b>

参考答案：

如果你意外的做了 git reset --hard, 你通常能找回你的提交(commit), 因为Git对每件事都会有日志，且都会保存几天。

> (main)$ git reflog

你将会看到一个你过去提交(commit)的列表, 和一个重置的提交。 选择你想要回到的提交(commit)的SHA，再重置一次:

> (main)$ git reset --hard SHA1234

这样就完成了。

</details>

<b><details><summary>23. 我的提交信息(commit message)写错了</summary></b>

参考答案：如果你的提交信息(commit message)写错了且这次提交(commit)还没有推(push), 你可以通过下面的方法来修改提交信息(commit message):

> git commit --amend --only -m 'fix: 新的提交信息'

</details>

<b><details><summary>24.git 与 svn 的区别在哪里？</summary></b>

参考答案：

| Git | SVN | 
| --- | --- |
| 1. Git是一个分布式的版本控制工具 | 	1. SVN 是集中版本控制工具 | 
| 2.它属于第3代版本控制工具 | 	2.它属于第2代版本控制工具 | 
| 3.客户端可以在其本地系统上克隆整个存储库 | 	3.版本历史记录存储在服务器端存储库中 | 
| 4.即使离线也可以提交 | 	4.只允许在线提交 | 
| 5.Push/pull 操作更快 | 	5.Push/pull 操作较慢 | 
| 6.工程可以用 commit 自动共享 | 	6.没有任何东西自动共享 | 

</details>

<b><details><summary>25.git pull 和 git fetch 的区别 </summary></b>

参考答案：

   ```
   git fetch 只是将远程仓库的变化下载下来，并没有和本地分支合并。

   git pull 会将远程仓库的变化下载下来，并和当前分支合并。
   ```
   [《详解 git pull 和 git fetch 的区别》](https://blog.csdn.net/weixin_41975655/article/details/82887273)

</details>

<b><details><summary>26.git rebase 和 git merge 的区别</summary></b>

参考答案：

   ```
   git merge 和 git rebase 都是用于分支合并，关键在 commit 记录的处理上不同。

   git merge 会新建一个新的 commit 对象，然后两个分支以前的 commit 记录都指向这个新 commit 记录。这种方法会
   保留之前每个分支的 commit 历史。

   git rebase 会先找到两个分支的第一个共同的 commit 祖先记录，然后将提取当前分支这之后的所有 commit 记录，然后
   将这个 commit 记录添加到目标分支的最新提交后面。经过这个合并后，两个分支合并后的 commit 记录就变为了线性的记
   录了。
   ```
   [《git rebase 和 git merge 的区别》](https://www.jianshu.com/p/f23f72251abc)
   [《git merge 与 git rebase 的区别》](https://blog.csdn.net/liuxiaoheng1992/article/details/79108233)

</details>

<b><details><summary>27. 删除/添加远程地址</summary></b>

参考答案：

```
删除远程地址
git remote rm origin

添加远程地址
git remote add origin git@github.com:qiilee/vue3.git
```

</details>

<b><details><summary>28. 只是提交信息里有一个单词写错了，可以使用以下命令进行修补</summary></b>

git commit --amend -m “xxx”

</details>

<b><details><summary>29. 撤销提交历史中的某一次指定的提交</summary></b>

git revert 711bb0b

</details>

<b><details><summary>30. 合并出现冲突时，撤销合并操作</summary></b>

git merge --abort

</details>

<b><details><summary>31. 暂存区的文件加多了，想移除，又不想删掉本地的文件</summary></b>

git rm --cached src/test.md

</details>

<b><details><summary>32. 分支重命名</summary></b>

git br -m [old_br] [new_br]

</details>

<b><details><summary>33. git提交规范</summary></b>

```
1、提交前缀规范（区分类别）

(1) feat：新增功能或页面；
(2) delete：删除功能或文件；
(3) fix：修复bug、解决冲突（尽量避免）；
(4) modify：修改功能；
(5) docs：修改文档；
(6) refactor：代码重构，未新增任何功能和修复任何bug；
(7) build：改变构建流程，新增依赖库、工具等（例如webpack修改）；
(8) style：仅仅修改了空格、缩进、注释等，不改变代码逻辑的变动；
(9) perf：改善性能和体现的修改；
(10) chore：非src和test的修改；
(11) test：测试用例的新增、修改；
(12) ci：自动化流程配置修改；
(13) revert：回滚到上一个版本；
(14) scope：【可选】用于说明commit的影响范围
(15) subject：commit的简要说明，尽量简短

2、提交文字规范

格式：提交前缀：动作行为+问题内容
示例：
（1）feat：新增xx页面
（2）feat：新增xx页面xx功能
（3）fix：修复xx页面xx bug
（4）modify：修改xx页面xx功能
（5）delete：删除xx页面
（6）refactor：重构xx页面xx功能
（7）style：删除多余注释代码/控制台打印代码
（8）refactor：迁移xx文件到xx目录

3、单次提交注意事项

1、提交问题必须为同一类别；
2、提交问题不能超过3个；
3、提交的commit发现不符合规范，git commit --amend -m "新的提交信息"或 git reset --hard HEAD^ 重新提交一次

```


```
feat 增加新功能
fix 修复问题/BUG
style 代码风格相关无影响运行结果的
perf 优化/性能提升
refactor 重构
revert 撤销修改
test 测试相关
docs 文档/注释
chore 依赖更新/脚手架配置修改等
workflow 工作流改进
ci 持续集成
types 类型定义文件更改
wip 开发中

参考：https://github.com/buqiyuan/vue3-antd-admin
```

</details>

<b><details><summary>34. npm和pnpm有什么区别</summary></b>

```
npm和pnpm都是JavaScript的包管理工具，用于自动化安装、配置、更新和卸载npm包依赖。然而，它们在设计和功能上有一些关键的区别：

    存储方式:
        npm为每个项目安装独立的包版本，即使多个项目使用相同的包版本，也会在每个项目的node_modules目录下存储一个副本。
        pnpm使用一个内容寻址的文件存储方式，如果多个项目使用相同的包版本，pnpm会存储单个副本，并在每个项目中创建硬链接。这节省了大量的磁盘空间并提高了安装速度。

    性能:
        pnpm在性能方面通常优于npm，因为它使用硬链接和符号链接来避免重复包的冗余副本，从而加快了安装速度。

    安全性:
        pnpm在安装包时采用了严格的依赖解析策略。默认情况下，它不会扁平化依赖，这意味着子依赖不会被提升到项目的顶层node_modules目录，这减少了意外覆盖依赖的风险。

    依赖关系:
        npm的依赖扁平化可以导致许多顶层node_modules目录中的包，这在一些情况下可能会导致版本冲突或意外的行为。
        pnpm通过创建非扁平化的node_modules结构，避免了由于包之间的版本冲突所导致的问题。

    命令行界面:
        npm和pnpm的命令行界面（CLI）非常相似，大多数命令都是一致的，如install, run, test等，但可能在某些高级功能和命令上有所不同。

    兼容性:
        npm作为最早和最广泛使用的包管理器，几乎被所有的Node.js项目支持。
        pnpm虽然在许多项目中能够无缝工作，但在某些依赖于特定node_modules结构的工具或项目中可能会遇到兼容性问题。

总体来说，pnpm在空间和性能方面提供了显著的优势，但在某些项目中可能需要额外的配置来保证与传统npm相同的行为。选择哪一个主要取决于个人或团队的需求和项目的特定要求。
```

</details>

<b><details><summary>35. </summary></b>

</details>