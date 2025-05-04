# 💻 VSCode Git 集成使用指南

Visual Studio Code (VSCode) 内置了强大的 Git 支持，使得版本控制操作更加直观和便捷。

**(待补充)**

## 核心功能区

VSCode 的 Git 功能主要集中在 **源代码管理 (Source Control)** 面板，通常位于左侧活动栏（一个类似分支的图标）。

*   **更改 (Changes):** 显示所有已修改但未暂存的文件。
    *   点击文件可以查看 **差异 (Diff)**。
    *   鼠标悬停在文件上，会出现：
        *   `+` (Stage Changes): 将此文件的更改添加到暂存区 (`git add`)。
        *   `⤺` (Discard Changes): 撤销对此文件的修改 (`git checkout -- <file>`)。
*   **暂存的更改 (Staged Changes):** 显示已添加到暂存区的文件。
    *   鼠标悬停在文件上，会出现：
        *   `-` (Unstage Changes): 将此文件移出暂存区 (`git reset HEAD <file>`)。
*   **提交 (Commit):**
    *   在顶部的输入框中输入 **提交信息 (Commit Message)**。
    *   点击 **对勾 ✔️ (Commit)** 按钮执行 `git commit`。
    *   Commit 按钮旁边的下拉菜单提供更多选项，如 `Commit & Push`, `Commit & Sync`。
*   **分支 (Branches):**
    *   状态栏左下角显示当前所在分支。点击可以切换分支、创建新分支。
    *   源代码管理面板的 `...` 菜单中也有分支相关的操作（创建、删除、合并等）。
*   **远程 (Remotes):**
    *   `...` 菜单 -> "Pull, Push" 子菜单提供 `Pull`, `Push`, `Sync` (先 Pull 再 Push), `Fetch` 等操作。
    *   状态栏右下角的同步按钮 (🔄) 通常执行 `Sync` 操作。

## 常用操作示例

*   **查看状态:** 打开源代码管理面板即可看到 `Changes` 和 `Staged Changes`。
*   **添加文件:** 在 `Changes` 区域点击文件旁的 `+` 号。点击区域标题旁的 `+` 号可以暂存所有更改。
*   **提交:** 在输入框填写信息，点击 ✔️。
*   **推送:** 点击 `...` -> Pull, Push -> Push，或使用状态栏同步按钮。
*   **拉取:** 点击 `...` -> Pull, Push -> Pull，或使用状态栏同步按钮。
*   **切换分支:** 点击状态栏左下角的分支名，选择要切换的分支。
*   **创建分支:** 点击状态栏左下角的分支名，选择 `+ Create new branch...`。
*   **合并分支:**
    1.  切换到目标分支 (e.g., `main`)。
    2.  点击 `...` -> Branch -> Merge Branch...
    3.  选择要合并进来的源分支 (e.g., `feature`)。
*   **解决冲突:** 当 `Pull` 或 `Merge` 发生冲突时，冲突文件会显示在 `Merge Changes` 区域。
    *   点击冲突文件，VSCode 会提供可视化界面。
    *   你可以选择 "Accept Current Change" (保留你的修改), "Accept Incoming Change" (接受远程或合并分支的修改), "Accept Both Changes" (保留两者)，或者手动编辑代码块。
    *   解决完所有冲突后，保存文件，然后在 `Merge Changes` 区域点击该文件旁的 `+` 号将其暂存。
    *   最后，像正常提交一样，在顶部输入框输入合并提交信息（通常 VSCode 会自动生成一个），点击 ✔️ 完成合并提交。

## 推荐扩展

*   **GitLens:** 极大地增强了 VSCode 的 Git 功能，可以查看代码作者、文件历史、提交详情、分支比较等。
*   **GitHub Pull Requests and Issues:** 直接在 VSCode 中管理 GitHub PR 和 Issue。

**(详细图文教程和更多高级用法待补充)**
