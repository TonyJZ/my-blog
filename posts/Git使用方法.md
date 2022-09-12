# Git使用方法

## 不同分支之间的feature合并

### 应用场景

某个项目可能有多个不同的迭代分支，且各分支上的功能需求也不同。有时候需要将一个分支上的某个功能合并到另一个分支，但又不能完全合并两个分支。

这时候可以采用以下方法来实现。

#### 比较两个分支上某些文件差异

* 方法1

> Git diff branch1 branch2 --stat          //显示出所有有差异的文件列表
>
> Git diff branch1 branch2 文件名(带路径)   //显示指定文件的详细差异
>
> Git diff branch1 branch2                 //显示出所有有差异的文件的详细差异


* 方法2

在Bitbucket网站上选择指定文件，打开Diff下拉菜单，并选择参与比较的commit ID。

![](../images/Git/bitbucket-diff.jpg)


#### 合并不同分支的部分文件

假设A分支为当前工作分支，B分支有部分功能需要合并到A分支

> $ git branch
>  * A
>    B

首先切换到A分支

> $ git checkout A

**由于git里面的merge是全merge ，没有单个文件merge。要实现一个文件的merge ，需要使用git checkout。**

>  $ git checkout xxxx（分支名）  xxxx（文件名）

这个命令是覆盖的意思，是把另一个分支的文件覆盖到当前的分支上，为了避免破坏当前分支，需要先建立一个临时分支。



 1. 使用git checkout 将根据A分支创建一个A_temp分支，避免影响A分支

> $ git checkout -b A_temp   // Switched to a new branch 'A_temp'

 2. 将B分支部分功能合并到A_temp分支
> $ git checkout B a.js b.js
> $ git commit -m "..."

 3. 将A_temp合并到A分支
> $ git checkout A
> $ git merge B