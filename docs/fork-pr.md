# 🤝 Fork 与 Pull Request (协作流程)

Fork 和 Pull Request (PR) 是 GitHub 上进行开源贡献和团队协作的核心机制。它允许你在不直接修改原始项目的情况下提出更改建议。

## 流程概览

1.  **Fork (分叉):** 将别人的仓库复制一份到你自己的 GitHub 账号下。这个副本完全属于你，你可以自由修改。
2.  **Clone (克隆):** 将你 Fork 后的仓库克隆到本地电脑。
3.  **Create Branch (创建分支):** 在本地仓库创建一个新的分支来开发新功能或修复 Bug。
4.  **Make Changes (修改代码):** 在新分支上进行代码修改、添加文件等。
5.  **Commit & Push (提交与推送):** 将本地的修改提交，并将新分支推送到你 GitHub 上的 Fork 仓库。
6.  **Create Pull Request (创建 PR):** 在 GitHub 上，从你的 Fork 仓库向原始仓库发起一个 Pull Request，请求他们合并你的更改。
7.  **Code Review (代码审查):** 原始仓库的维护者会审查你的代码，可能会提出修改意见。
8.  **Merge (合并):** 如果代码没有问题，维护者会将你的 Pull Request 合并到原始仓库中。

## 详细步骤

### 1. Fork 仓库
在你想贡献的 GitHub 仓库页面，点击右上角的 "Fork" 按钮。选择你自己的账号作为目标。

### 2. Clone 你的 Fork
```bash
# 替换 <你的用户名> 和 <仓库名>
git clone https://github.com/<你的用户名>/<仓库名>.git
cd <仓库名>
```

### 3. (可选但推荐) 配置上游仓库 (Upstream)
为了方便同步原始仓库的更新，添加一个指向上游（原始）仓库的远程连接。
```bash
# 替换 <原始仓库作者名> 和 <仓库名>
git remote add upstream https://github.com/<原始仓库作者名>/<仓库名>.git

# 验证是否添加成功
git remote -v
# origin  https://github.com/<你的用户名>/<仓库名>.git (fetch)
# origin  https://github.com/<你的用户名>/<仓库名>.git (push)
# upstream https://github.com/<原始仓库作者名>/<仓库名>.git (fetch)
# upstream https://github.com/<原始仓库作者名>/<仓库名>.git (push)
```

### 4. 创建并切换到新分支
```bash
git checkout -b <你的新分支名> # 例如: feature/add-login 或 fix/typo-readme
```

### 5. 进行修改、提交和推送
```bash
# ... 进行代码修改 ...
git add .
git commit -m "添加登录功能" # 清晰的提交信息
git push origin <你的新分支名>
```

### 6. 创建 Pull Request
-   回到你 GitHub 上的 Fork 仓库页面。
-   GitHub 通常会自动检测到你推送了新分支，并显示一个 "Compare & pull request" 按钮，点击它。
-   如果没看到按钮，切换到你的新分支，点击 "Contribute" -> "Open pull request"。
-   **重要:** 确认 `base repository` 是原始仓库，`base` 分支通常是 `main` 或 `master`；`head repository` 是你的 Fork 仓库，`compare` 分支是你刚刚推送的新分支。
-   填写清晰的标题和描述，说明你做了什么更改以及为什么。
-   点击 "Create pull request"。

### 7. 同步原始仓库的更新 (保持 Fork 更新)
在进行新的修改前，或 PR 等待合并期间，最好保持你的 `main` 分支与上游仓库同步。
```bash
# 切换到 main 分支
git checkout main

# 从上游拉取最新代码
git pull upstream main

# (可选) 更新你 GitHub 上的 Fork 的 main 分支
git push origin main
```
如果需要将上游的更新合并到你的特性分支，可以切换到特性分支后执行 `git merge main` 或 `git rebase main` (参考 Rebase vs Merge)。

---

这个流程确保了原始仓库的整洁，所有更改都经过审查后才会被合并。
