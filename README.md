# 📘 零基础 GitHub 教程 | Learn GitHub for Students

这是为河北农业大学的同学们准备的 Git/GitHub 入门教程。**无需基础、一步步教你从零开始掌握版本控制和协作流程！**

---

## 🎯 为什么要学这个？
- 上传代码，管理项目
- 多人协作、写作业、做毕设都好用
- 展示自己的作品，建立简历亮点！

---

## 🛠️ 环境准备
1. 注册 GitHub 账号：https://github.com
2. 下载 Git：https://git-scm.com/downloads
3. 安装 VSCode（推荐）：https://code.visualstudio.com

---

## 🚀 入门命令

### 1. 克隆一个项目 (Clone a Repository)
把远程仓库复制到本地。
```bash
git clone <仓库链接>
```
进入项目目录：
```bash
cd <项目名称>
```

### 2. 查看状态 (Check Status)
查看当前仓库文件的状态（哪些文件被修改了，哪些文件已暂存等）。
```bash
git status
```

### 3. 添加文件到暂存区 (Stage Changes)
告诉 Git 你想要在下次提交中包含哪些文件的更改。
```bash
# 添加指定文件
git add <文件名>

# 添加所有更改的文件
git add .
```

### 4. 提交更改 (Commit Changes)
将暂存区的文件更改保存到本地仓库历史记录中。
```bash
git commit -m "你的提交信息，说明你做了什么更改"
```

### 5. 推送到远程仓库 (Push Changes)
将本地的提交上传到 GitHub 远程仓库。
```bash
git push origin <分支名> # 通常是 main 或 master
```

### 6. 拉取远程仓库的更新 (Pull Changes)
从远程仓库获取最新的更改并合并到你的本地分支。
```bash
git pull origin <分支名> # 通常是 main 或 master
```

### 7. 分支管理 (Branching)
分支允许你独立开发新功能或修复问题，而不影响主代码。

```bash
# 查看所有本地分支
git branch

# 创建一个新分支
git branch <新分支名>

# 切换到指定分支
git checkout <分支名>

# 创建并切换到新分支 (常用)
git checkout -b <新分支名>

# 删除一个本地分支 (确保已合并或不再需要)
git branch -d <分支名>
```

### 8. 合并分支 (Merging)
将一个分支的更改合并到当前所在的分支。

```bash
# 1. 首先切换到你想要合并入的目标分支 (例如 main)
git checkout main

# 2. 拉取最新代码确保目标分支是更新的
git pull origin main

# 3. 执行合并，将 <特性分支名> 的代码合并到当前分支 (main)
git merge <特性分支名>

# 4. 推送合并后的目标分支
git push origin main
```

### 9. 查看提交历史 (View History)
查看项目的提交记录。
```bash
# 查看详细历史
git log

# 查看简洁历史
git log --oneline
```

---

## ✨ 进阶技巧

-   [处理合并冲突 (Handling Merge Conflicts)](./docs/merge-conflicts.md)
-   [Fork 与 Pull Request (协作流程)](./docs/fork-pr.md)
-   [.gitignore 文件详解](./docs/gitignore.md)
-   [Rebase vs Merge](./docs/rebase-vs-merge.md)
-   [GitHub Pages 部署静态网站](./docs/github-pages.md)

---

## 🎯 后续计划 (TODO)

**基础部分:**
-   [x] **核心命令介绍:** 已包含 Clone, Status, Add, Commit, Push, Pull, Branch, Merge, Log 等基础命令。
-   [ ] **图文/视频补充:** 为每个命令或概念添加更直观的图示或推荐视频教程链接。
-   [ ] **环境准备细化:** 提供更详细的 Git 安装和配置步骤（如 SSH Key 配置）。

**进阶部分:**
-   [x] **合并冲突解决:** [查看文档](./docs/merge-conflicts.md)
-   [x] **协作流程 (Fork & PR):** [查看文档](./docs/fork-pr.md)
-   [x] **.gitignore 详解:** [查看文档](./docs/gitignore.md)
-   [x] **Rebase vs Merge:** [查看文档](./docs/rebase-vs-merge.md)
-   [x] **GitHub Pages 部署:** [查看文档](./docs/github-pages.md)

**实践与答疑:**
-   [x] **常见问题解答 (FAQ):** [查看文档](./docs/faq.md) (初步)
-   [x] **实战小项目:** [查看文档](./docs/practice-projects.md) (初步)
-   [x] **VSCode Git 集成:** [查看文档](./docs/vscode-git.md) (初步)

---

**继续学习，不断实践！**