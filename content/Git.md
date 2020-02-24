# [返回主页](https://github.com/yisainan/web-interview/blob/master/README.md)

<b><details><summary>1.简单对比 git pull 和 git pull --rebase 的使用</summary></b>

答案：

git pull = git fetch + git merge
git pull --rebase = git fetch + git rebase

解析：现在来看看[git merge 和 git rebase 的区别](https://www.cnblogs.com/kevingrace/p/5896706.html)

[参与互动](https://github.com/yisainan/web-interview/issues/997)

</details>

<b><details><summary>2.什么时候使用“git rebase”代替“git merge”？</summary></b>

答案：

[参与互动](https://github.com/yisainan/web-interview/issues/998)

</details>

<b><details><summary>3.“拉取请求（pull request）”和“分支（branch）”之间有什么区别？</summary></b>

答案：

[参与互动](https://github.com/yisainan/web-interview/issues/999)

</details>

<b><details><summary>4.什么是 Git 复刻（fork）？复刻（fork）、分支（branch）和克隆（clone）之间有什么区别？</summary></b>

答案：

[参与互动](https://github.com/yisainan/web-interview/issues/1000)

</details>

<b><details><summary>5.使用过 git cherry-pick，有什么作用？</summary></b>

答案：

[参与互动](https://github.com/yisainan/web-interview/issues/1001)

</details>

<b><details><summary>6.git 跟其他版本控制器有啥区别？</summary></b>

答案：

Git比svn快，而且更加的流畅。

Git在本地就可以使用，可以随便保存各种历史记录，不用担心污染服务器。

Git在branch和branch之间切换非常简单。

Git没有被lock不能commit 的情况。

[参与互动](https://github.com/yisainan/web-interview/issues/1002)

</details>

<b><details><summary>7.我们在本地工程常会修改一些配置文件，这些文件不需要被提交，而我们又不想每次执行 git status 时都让这些文件显示出来，我们该如何操作？</summary></b>

答案：在 Git 工作区的跟目录下创建一个特殊的.gitignore 文件，然后把忽略的文件名编辑进去，Git 就会自动忽略这些文件。

[参与互动](https://github.com/yisainan/web-interview/issues/1003)

</details>

<b><details><summary>8.如何把本地仓库的内容推向一个空的远程仓库？</summary></b>

答案：

git init //生成.git 文件
git remote add origin 远程仓库地址 // 将本地和远程厂库关联起来
git add .
git commit -m '提交信息'
git push origin master // 将本地代码推送到库上

[参与互动](https://github.com/yisainan/web-interview/issues/1004)

</details>

<b><details><summary>9.提交时发生冲突，你能解释冲突是如何产生的吗？你是如何解决的？</summary></b>

答案：

#### 1. 冲突是如何产生的

我们都知道，Git 的实现途径是 1 棵树。比如有一个节点树(point1),

- 我们基于 point1 进行开发，开发出了结点 point2；
- 我们基于 point1 进行开发，开发出了结点 point3；
  如果我们在 point2 和 point3 内操作了同一类元素，那么势必会导致冲突的存在。
  主要的思想如下图 1 所示:

point1.js

```js
function test() {
  console.log(a);
  var a = 1;
}
```

人物甲 更新了版本 2
代码: poin2.js

```js
function test() {
  console.log(a);
  var a = 2;
}
```

人物乙 更新了版本 3
代码: poin3.js

```js
function test() {
  console.log(a);
  var a = 3;
}
```

场景如下，甲乙都是根据 point.js 文件进行了开发。甲开发出了版本 2，并且提交了代码；乙开发出了版本 3，也需要提交了代码，此时将会报错存在冲突。

为什么呢？因为甲开发完了版本，提交了版本之后，此时远端的代码已经是版本 2 点代码了，而乙是基于版本 1 进行的开发出了版本 3。所以，乙想要提交代码，势必要将自己的代码更新为版本 2 的代码，然后再进行提交，如果存在冲突则解决冲突后提交

#### 2. 冲突是如何解决的

上面已经详细的说明了冲突时如何产生的，那么又该如何解决冲突呢?

解决冲突通常使用如下的步骤即可:

- 情况 1 无冲突

先拉取远端的代码，更新本地代码。然后提交自己的更新代码即可。

- 情况 2 有冲突

拉取远端代码。存在冲突，会报错。
此时我们需要将本地代码暂存起来 stash；
更新本地代码，将本地代码版本更新和远端的代码一致即可；
将暂存的代码合并到更新后的代码后，有冲突解决冲突(需要手动进行解决冲突)；
提交解决冲突后的代码。

[参与互动](https://github.com/yisainan/web-interview/issues/1005)

</details>

<b><details><summary>10.列举工作中常用的几个 git 命令？</summary></b>

答案：

git add
git status
git commit -m
git pull
git push

[参与互动](https://github.com/yisainan/web-interview/issues/1006)

</details>

<b><details><summary>11.git提交代码时候写错commit信息后，如何重新设置commit信息？</summary></b>

答案：可以通过git commit --amend 来对本次commit进行修改。

[参与互动](https://github.com/yisainan/web-interview/issues/1007)

</details>

<b><details><summary>12.说明新建一个GIT功能分支的步骤，提供每个步骤的指令，并对指令进行说明</summary></b>

答案：

git branch name     创建名字为name的branch

git checkout xxx_dev    切换到名字为xxx_dev的分支

git pull    从远程分支拉取代码到本地分支

git checkout -b main_furture_xxx    创建并切换到main_furture_xxx

git push origin main_furture_xxx    执行推送的操作，完成本地分支向远程分支的同步

[参与互动](https://github.com/yisainan/web-interview/issues/1008)

</details>

<b><details><summary>13.说明git合并的两种方法以及区别</summary></b>

答案：

git代码合并有两种：git Merge 和 git ReBase

Git Merge：这种合并方式是将两个分支的历史合并到一起，现在的分支不会被更改，它会比对双方不同的文件缓存下来，生成一个commit，去push。

Git ReBase：这种合并方法通常被称为“衍合”。他是提交修改历史，比对双方的commit，然后找出不同的去缓存，然后去push，修改commit历史。

[参与互动](https://github.com/yisainan/web-interview/issues/1009)

</details>

<b><details><summary>14.如何查看文件的提交历史和分支的提交历史</summary></b>

答案：

使用git log查看文件提交历史

git log filename

使用git log查看分支提交历史

git log branch file

[参与互动](https://github.com/yisainan/web-interview/issues/1010)

</details>

<b><details><summary>15.当GIT出现如下情况时，该如何处理？</summary></b>

## your-branch-is-ahead-of-origin-master-by-3-commits

答案：

Git commit

Git pull

Git push

[参与互动](https://github.com/yisainan/web-interview/issues/1011)

</details>
