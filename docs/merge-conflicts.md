# 🤯 处理合并冲突 (Handling Merge Conflicts)

当 Git 无法自动合并来自不同分支的更改时，就会发生合并冲突。这通常发生在两个分支修改了同一文件的同一部分。

## 识别冲突

当你尝试合并 (`git merge`) 或拉取 (`git pull`) 并且存在冲突时，Git 会提示你。`git status` 也会显示哪些文件存在冲突。

冲突的文件会包含类似以下的标记：

```diff
<<<<<<< HEAD
// 当前分支 (例如 main) 的代码
代码 A
=======
// 正在合并的分支 (例如 feature-branch) 的代码
代码 B
>>>>>>> feature-branch
```

## 解决冲突步骤

1.  **打开冲突文件:** 使用你的代码编辑器打开标记为冲突的文件。
2.  **编辑文件:**
    *   找到 `<<<<<<<`, `=======`, `>>>>>>>` 标记。
    *   决定保留哪部分代码，或者结合两部分代码。
    *   删除这些标记 (`<<<<<<< HEAD`, `=======`, `>>>>>>> feature-branch`)。
    *   确保最终的代码是你想要的样子。
3.  **暂存已解决的文件:**
    ```bash
    git add <已解决冲突的文件名>
    ```
4.  **完成合并:**
    *   如果是在 `git merge` 过程中：
        ```bash
        git commit -m "解决合并冲突: <简要说明>"
        ```
        (Git 通常会自动生成一个提交信息，你可以直接使用或修改)
    *   如果是在 `git pull` (内部包含 merge) 过程中，通常在 `git add` 后冲突就解决了，后续的 `push` 可以正常进行。如果 `pull` 被中断，可能需要手动 `git commit`。

## 示例

假设 `myfile.txt` 发生冲突：

```
<<<<<<< HEAD
这是 main 分支的内容。
=======
这是 feature 分支的新内容。
>>>>>>> feature-branch
```

**解决方法 1: 保留 feature 分支的内容**

编辑 `myfile.txt` 为：

```
这是 feature 分支的新内容。
```

然后执行 `git add myfile.txt` 和 `git commit`。

**解决方法 2: 结合两者**

编辑 `myfile.txt` 为：

```
这是 main 分支的内容，并且这是 feature 分支的新内容。
```

然后执行 `git add myfile.txt` 和 `git commit`。

**关键:** 理解冲突的原因，并手动编辑文件以达到最终期望的状态。
