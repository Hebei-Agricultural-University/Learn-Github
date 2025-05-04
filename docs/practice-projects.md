# 🚀 实战小项目

通过实际操作来巩固 Git 和 GitHub 技能是最好的学习方式。

**(待设计和补充)**

## 项目一：个人简历页面

**目标:** 使用 HTML 和 CSS 创建一个简单的个人简历网页，并通过 GitHub Pages 发布。

**涉及技能:**
*   `git clone`, `add`, `commit`, `push`
*   创建仓库
*   GitHub Pages 部署 (从 `main` 分支)
*   (可选) 分支管理：创建一个 `dev` 分支进行开发，完成后合并回 `main`。

**步骤:**
1.  在 GitHub 上创建一个新的仓库，例如 `my-resume`。
2.  将仓库 `clone` 到本地。
3.  在本地创建 `index.html` 和 `style.css` 文件。
4.  编写简历内容和样式。
5.  使用 `git add .` 和 `git commit -m "Initial commit"` 提交你的代码。
6.  使用 `git push origin main` 推送到 GitHub。
7.  在仓库的 Settings -> Pages 中，配置从 `main` 分支的 `/root` 部署。
8.  等待部署完成，访问你的简历页面 `https://<username>.github.io/my-resume`。
9.  (可选) 创建 `dev` 分支 (`git checkout -b dev`)，在 `dev` 分支上修改简历内容或样式，提交并推送 `dev` 分支 (`git push origin dev`)。然后切换回 `main` 分支 (`git checkout main`)，合并 `dev` 分支 (`git merge dev`)，最后推送 `main` 分支 (`git push origin main`)。观察 GitHub Pages 自动更新。

## 项目二：协作编辑文档

**目标:** 模拟团队协作，使用 Fork 和 Pull Request 流程共同编辑一个 Markdown 文档。

**涉及技能:**
*   Fork 仓库
*   `clone`, `add`, `commit`, `push`
*   创建分支 (`checkout -b`)
*   创建 Pull Request
*   (可选) 处理合并冲突
*   (可选) Code Review (在 PR 页面评论)

**步骤:**
1.  **项目负责人:** 创建一个包含简单 Markdown 文件（例如 `project-plan.md`）的仓库。
2.  **贡献者:**
    *   Fork 负责人的仓库到自己的账号下。
    *   `clone` 你自己 Fork 的仓库到本地。
    *   (推荐) 添加上游仓库 `git remote add upstream <负责人仓库地址>`。
    *   创建新的特性分支，例如 `feature/add-section-one`。
    *   在 `project-plan.md` 中添加或修改内容。
    *   `add`, `commit`, `push` 你的特性分支到你的 Fork 仓库 (`origin`)。
    *   在 GitHub 上，从你的 Fork 向负责人的原始仓库发起 Pull Request。
3.  **项目负责人:**
    *   查看收到的 Pull Request。
    *   (可选) 进行 Code Review，提出评论或修改建议。
    *   如果满意，点击 "Merge pull request" 将贡献者的更改合并到主分支。
4.  **(可选) 制造冲突:** 两个贡献者修改同一行，第二个 PR 会产生冲突，需要负责人或贡献者解决冲突后再合并。

**(更多项目想法待添加...)**
