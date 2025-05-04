# ❓ 常见问题解答 (FAQ)

这里收集和解答学习 Git 和 GitHub 过程中可能遇到的常见问题。

**(待补充)**

*   **Q: `git pull` 和 `git fetch` 有什么区别？**
    *   A: `git fetch` 只是将远程仓库的最新元数据和对象下载到本地，但 **不会** 自动合并或修改你当前的工作。你可以先 `fetch` 查看远程有哪些更新，再决定是否 `merge` 或 `rebase`。`git pull` 则相当于 `git fetch` 之后立刻执行 `git merge` (或者 `git rebase`，取决于你的配置)。

*   **Q: 提交错了 Commit Message 怎么办？**
    *   A: 如果是 **最近一次** 提交并且 **还没有 push** 到远程：
        ```bash
        git commit --amend -m "新的提交信息"
        ```
    *   如果已经 push 了，或者想修改更早的提交，情况会更复杂，通常需要 `git rebase -i`，并且如果已经 push，需要强制推送 (`--force-with-lease`)，这会影响协作者，需谨慎操作。

*   **Q: 如何撤销 `git add`？**
    *   A: 将文件从暂存区移回工作区：
        ```bash
        git reset HEAD <文件名> # 撤销指定文件的暂存
        git reset HEAD .       # 撤销所有文件的暂存
        # 或者使用新命令 (Git 2.23+)
        git restore --staged <文件名>
        ```

*   **Q: 如何撤销本地修改 (还未 add)？**
    *   A: 放弃工作区对某个文件的修改，恢复到上次提交时的状态：
        ```bash
        git checkout -- <文件名>
        # 或者使用新命令 (Git 2.23+)
        git restore <文件名>
        ```
        **注意：** 这个操作会 **丢失** 你对该文件的所有未暂存的修改，请谨慎使用！

*   **Q: SSH Key 配置失败怎么办？**
    *   A: 检查步骤：
        1.  确认 `.ssh` 目录 (通常在用户主目录下 `~/.ssh`) 是否存在 `id_rsa` (私钥) 和 `id_rsa.pub` (公钥) 文件。
        2.  确认 `id_rsa.pub` 的内容已完整、正确地添加到 GitHub 账号的 SSH Keys 设置中 (Settings -> SSH and GPG keys -> New SSH key)。不要添加私钥！
        3.  测试连接：`ssh -T git@github.com`。如果看到 "Hi <username>! You've successfully authenticated..." 则表示成功。
        4.  检查 Git 仓库的远程 URL 是 SSH 格式 (`git@github.com:...`) 而不是 HTTPS 格式 (`https://github.com/...`)。使用 `git remote -v` 查看，使用 `git remote set-url origin git@github.com:<username>/<repo>.git` 修改。
        5.  确保 SSH Agent 正在运行并且添加了你的私钥 (特别是设置了密码的私钥)。

*   **Q: 为什么 `git push` 被拒绝 (rejected)？**
    *   A: 最常见的原因是远程仓库包含了你本地没有的提交。你需要先 `git pull` (或 `git fetch` + `git merge`/`rebase`) 将远程更新合并到本地，解决可能出现的冲突，然后再 `git push`。

*   **Q: `master` 和 `main` 分支有什么区别？**
    *   A: 功能上没有区别，都是 Git 仓库的默认主分支名。`main` 是近年来为了替代具有潜在冒犯性含义的 `master` 而推广的新默认名称。GitHub 新建仓库默认使用 `main`。旧项目可能仍然使用 `master`。

*   **Q: 如何删除远程分支？**
    *   A:
        ```bash
        git push origin --delete <远程分支名>
        # 或者使用旧语法
        git push origin :<远程分支名>
        ```

**(更多问题待添加...)**
