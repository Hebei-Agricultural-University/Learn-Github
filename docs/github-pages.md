# 🌐 GitHub Pages 部署静态网站

GitHub Pages 是 GitHub 提供的一项免费服务，允许你直接从你的 GitHub 仓库托管静态网站（HTML, CSS, JavaScript 文件）。

## 网站类型

GitHub Pages 可以托管两种类型的网站：

1.  **用户/组织网站 (User/Organization Site):**
    *   每个 GitHub 用户或组织只能拥有一个。
    *   仓库必须命名为 `<username>.github.io` 或 `<orgname>.github.io`。
    *   网站内容必须放在 `main` (或 `master`) 分支的根目录。
    *   网站地址为 `https://<username>.github.io` 或 `https://<orgname>.github.io`。
2.  **项目网站 (Project Site):**
    *   可以为你的任何项目仓库创建。
    *   网站内容可以来自特定分支 (`main`, `gh-pages`) 或该分支下的 `/docs` 目录。
    *   网站地址为 `https://<username>.github.io/<repository-name>` 或 `https://<orgname>.github.io/<repository-name>`。

## 部署步骤 (以项目网站为例)

假设你有一个名为 `my-awesome-project` 的仓库，里面包含 `index.html`, `style.css`, `script.js` 等静态文件。

### 方法一: 从 `main` 分支部署

这是最简单的方法，如果你的仓库根目录就是你的网站文件。

1.  **确保你的网站文件在仓库根目录:**
    ```
    my-awesome-project/
    ├── index.html
    ├── style.css
    └── script.js
    ```
2.  **推送到 GitHub:** 确保你的代码已经推送到 GitHub 仓库。
3.  **启用 GitHub Pages:**
    *   进入你的 GitHub 仓库页面。
    *   点击 "Settings" (设置)。
    *   在左侧导航栏找到 "Pages"。
    *   在 "Build and deployment" 部分：
        *   **Source:** 选择 "Deploy from a branch"。
        *   **Branch:** 选择 `main` 分支，文件夹选择 `/ (root)`。
    *   点击 "Save"。
4.  **等待部署:** GitHub Actions 会开始构建和部署你的网站。这可能需要几分钟时间。部署完成后，页面顶部会显示你的网站地址。
5.  **访问网站:** 打开 `https://<username>.github.io/my-awesome-project` 查看你的网站。

### 方法二: 从 `gh-pages` 分支部署

如果你不想让网站文件污染 `main` 分支的根目录，或者你的构建工具（如 Jekyll, Vite, Create React App 等）会将最终的静态文件输出到特定目录（如 `dist`, `build`），可以使用 `gh-pages` 分支。

1.  **创建 `gh-pages` 分支:**
    *   **手动创建:**
        ```bash
        # 假设你的构建产物在 dist 目录
        # 确保 dist 目录存在且包含网站文件
        git checkout --orphan gh-pages # 创建一个没有历史的新分支
        git add -f dist/ # 强制添加 dist 目录 (如果它在 .gitignore 中)
        git commit -m "Initial gh-pages commit"
        # 将 dist 目录的内容移动到根目录 (如果需要)
        # 例如: git mv dist/* . (需要小心操作，或者使用工具)
        # 或者直接配置 GitHub Pages 从 dist 目录部署 (见下文)

        # 推送 gh-pages 分支
        git push origin gh-pages
        ```
    *   **使用工具:** 很多构建工具或库（如 `gh-pages` npm 包）可以自动完成构建并将结果推送到 `gh-pages` 分支。
        ```bash
        # 示例: 使用 gh-pages npm 包 (需要先 npm install gh-pages --save-dev)
        # 在 package.json 的 scripts 中添加:
        # "deploy": "gh-pages -d dist"
        npm run deploy
        ```
2.  **启用 GitHub Pages:**
    *   进入仓库 "Settings" -> "Pages"。
    *   在 "Build and deployment" 部分：
        *   **Source:** 选择 "Deploy from a branch"。
        *   **Branch:** 选择 `gh-pages` 分支，文件夹选择 `/ (root)`。
    *   点击 "Save"。
3.  **等待部署并访问。**

### 方法三: 从 `main` 分支的 `/docs` 目录部署

如果你的网站文件放在 `main` 分支下的 `docs` 目录中，可以选择此选项。

1.  **将网站文件放入 `docs` 目录:**
    ```
    my-awesome-project/
    ├── docs/
    │   ├── index.html
    │   ├── style.css
    │   └── script.js
    └── ... (其他项目文件)
    ```
2.  **推送到 GitHub。**
3.  **启用 GitHub Pages:**
    *   进入仓库 "Settings" -> "Pages"。
    *   在 "Build and deployment" 部分：
        *   **Source:** 选择 "Deploy from a branch"。
        *   **Branch:** 选择 `main` 分支，文件夹选择 `/docs`。
    *   点击 "Save"。
4.  **等待部署并访问。**

## 自定义域名

你可以在 GitHub Pages 设置中配置使用你自己的域名。

## 注意事项

-   GitHub Pages 只适用于 **静态网站**。不能运行服务器端代码（如 PHP, Python, Node.js 服务端逻辑）。数据库等动态内容需要通过前端 JavaScript 调用外部 API 实现。
-   仓库大小和流量有限制（具体参考 GitHub 文档），但对于个人项目和文档通常足够。
-   私有仓库也可以使用 GitHub Pages，但网站本身仍然是公开的（除非使用 GitHub Enterprise Cloud）。

GitHub Pages 是展示项目、托管文档或建立个人博客的绝佳方式！
