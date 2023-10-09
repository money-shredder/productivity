## Git 学习教程

以下内容由ChatGPT生成（prompt: 写一个简短的git学习教程）。

### 1. Git 是什么？

Git 是一个版本控制系统，它可以帮助你追踪和管理项目的变化。它允许多人协作开发，也可以在不同的计算机上同步工作。

### 2. 安装 Git

首先，你需要安装 Git。你可以从 [Git 官网](https://git-scm.com/downloads) 下载适合你操作系统的版本。

### 3. 创建一个新的仓库

在你的项目目录中，打开终端或命令提示符，然后运行以下命令：

```bash
git init
```

这会在当前目录下创建一个新的 Git 仓库。

### 4. 添加文件到暂存区

将你的文件添加到 Git 仓库前，你需要先把它们添加到暂存区。运行以下命令：

```bash
git add 文件名
```

如果你想添加所有文件，可以运行：

```bash
git add .
```

### 5. 提交变更

一旦你的文件在暂存区中，你可以通过运行以下命令来将它们提交到仓库：

```bash
git commit -m "提交说明"
```

### 6. 查看状态

你可以随时查看项目的状态，以了解哪些文件被修改，哪些文件已经添加到暂存区，哪些文件已经提交到仓库中：

```bash
git status
```

### 7. 查看提交历史

你可以使用以下命令查看提交历史：

```bash
git log
```

### 8. 创建分支

分支是用来在项目中独立开发某个功能或修复 bug 的。你可以使用以下命令创建一个新分支：

```bash
git branch 分支名
```

### 9. 切换分支

要切换到另一个分支，你可以运行：

```bash
git checkout 分支名
```

### 10. 合并分支

一旦你的工作在一个分支中完成，你可以将其合并到主分支中：

```bash
git merge 分支名
```

### 11. 拉取和推送远程仓库

你可以使用 Git 与远程仓库交互，比如 GitHub 或 GitLab。要从远程仓库拉取最新的代码，可以运行：

```bash
git pull 远程仓库地址
```

要将本地代码推送到远程仓库，可以运行：

```bash
git push 远程仓库地址 分支名
```

### 12. 其他常用操作

- `git diff`: 显示文件的变化
- `git reset`: 撤销暂存的文件
- `git rm`: 删除文件并将更改提交到仓库

### 结束语

这是一个简短的 Git 学习教程，可以让你开始使用 Git 进行基本的版本控制。如果你想深入了解 Git，建议查阅更详细的教程和资源。祝你学习愉快！

## 建议配置

在用户目录下编写如下`.gitconfig`文件：
```ini
[user]
    name = ...
    email = ...
[alias]  # 常用的缩写，可以用如 git br 替代 git branch
    br = branch
    cm = commit
    co = checkout
    d = diff
    ds = diff --staged
    rb = rebase
    rs = restore
    mg = merge
    s = status --short --branch --column
    sm = submodule
    sw = swich
    st = stash
    un = reset
    lg = log --graph --date-order --abbrev-commit --date=relative
    unstage = reset
    unstage-all = reset --soft HEAD^
[core]
    autocrlf = input
[push]
    default = matching
[url "https://github.com/"]
    insteadOf = git://github.com/
    insteadOf = git@github.com:
    insteadOf = gh:
    insteadOf = github:
[init]
    defaultBranch = main
```
