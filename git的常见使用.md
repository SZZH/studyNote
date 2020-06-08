## git的常见使用

- 回退版本
  
  - reset
    - --soft，`git reset xxxx --soft`，代码将回退到指定版本，该版本后commit的代码退回到缓存区
    - --hard，`git reset xxxx --hard`，代码将回退到指定版本，并放弃commit过的代码
    - 不写，`git reset xxxx`，代码将回退到指定版本，变动的代码变为追踪状态
  - revert ，用法与reset基本一致，不同点在与，reset 将会退回到某个版本，并删除该commit，revert 是用一次新的 commit 抵消之前的 commit
  
- 合并 [详情]([https://git-scm.com/book/zh/v2/Git-%E5%88%86%E6%94%AF-%E5%8F%98%E5%9F%BA](https://git-scm.com/book/zh/v2/Git-分支-变基))

  - `git cherry-pick 版本号`将某个分支的某次 commit ，并入当前分支

  - merge，找到两个分支最近的共同祖先，并以此进行合并

  - rebase，先找到两个分支最近的组件，对比差异，把目标分支的差异提交到，当前分支的 HEAD 上

    ![截屏2020-05-20 下午11.38.50](/Users/zenghao/Desktop/studyNote/img/截屏2020-05-20 下午11.38.50.png)

- 暂存

  - stash 
    - `git stash` 暂存所有文件
    - `git stash -u `可以选定暂存哪些文件
    - `git stash list` 查看当前暂存列表
    - `git stash save 'xxx' ` 暂存文件并写一串描述
    - `git stash pop` 应用暂存文件，并pop出暂存列表
    - `git stash apply` 应用暂存文件，列表不变
    - `git stash branch [分支名]`
  
- 分支变动

  - 创建分支
    - `git branch [branch name]`
    - 创建并切换到该分支上 `git checkout -b [branch name]`
  
- 删除分支
    - 删除本地分支
      - `branch -d/branch --delete`	
      - `branch -D/branch --delete --force`
    - 删除远程分支
  - 修改分支名称 `git branch -m oldName newName`
  
- 子模块

  - 更新子模块：`git submodule update --init`
  
- 关联远端分支：`git branch --set-upstream-to=orgin/远端分支名`
