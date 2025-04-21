# git-practice

# Git 操作面经练习仓库

本仓库旨在帮助你熟悉 Git 操作，并为 Git 面试做准备。以下是创建和操作 Git 仓库，以及面试中可能考到的 Git 知识点。

### 1. 创建 GitHub 仓库

首先，你需要在 GitHub 上创建一个新的仓库。

1.  **登录 GitHub:** 访问 [https://github.com/](https://github.com/) 并登录你的账号。
2.  **创建新仓库:**
    * 点击页面右上角的 "+" 号，然后选择 "New repository"。
    * 在 "Repository name" 字段中输入你想要的仓库名称，例如 `git-practice`.
    * 你可以选择 "Public" 或 "Private" 仓库。对于练习来说，"Public" 即可。
    * (可选) 你可以添加一个 "Description" 来描述你的仓库。
    * 勾选 "Add a README file"。这是一个好习惯，可以帮助其他人了解你的项目。
    * 点击 "Create repository"。

现在你已经有了一个远程 GitHub 仓库，接下来我们将学习如何在本地操作 Git 并与这个远程仓库进行交互。

### 2. 本地 Git 初始化和基本操作

1.  **克隆远程仓库到本地:**
    * 打开你的终端（Terminal on macOS/Linux, Command Prompt or PowerShell on Windows）。
    * 导航到你想要存放本地仓库的目录，例如 `~/Projects/`.
    * 使用 `git clone` 命令克隆你刚创建的远程仓库。在你的 GitHub 仓库页面，点击 "Code" 按钮，复制 HTTPS 或 SSH 链接。假设是 HTTPS 链接：
        ```bash
        git clone [https://github.com/你的用户名/git-practice.git](https://github.com/你的用户名/git-practice.git)
        cd git-practice
        ```

2.  **查看 Git 状态:**
    * 在你的本地仓库目录中，运行 `git status` 命令。这个命令会显示当前工作区的状态，告诉你哪些文件被修改了，哪些文件在暂存区，以及当前所在的分支。

3.  **添加文件到暂存区:**
    * 创建一个新的文件，例如 `hello.txt`，并在其中添加一些内容。
    * 使用 `git add` 命令将文件添加到暂存区。
        ```bash
        echo "Hello, Git!" > hello.txt
        git add hello.txt
        ```
    * 你也可以使用 `git add .` 添加所有未暂存的修改。

4.  **提交更改:**
    * 使用 `git commit` 命令提交暂存区的更改到本地仓库。每次提交都需要一个有意义的提交信息。
        ```bash
        git commit -m "Add hello.txt file"
        ```

5.  **查看提交历史:**
    * 使用 `git log` 命令查看提交历史。它会显示所有的提交记录，包括提交的作者、日期、时间和提交信息。
    * 可以使用 `git log --oneline` 简化输出，只显示提交哈希和提交信息的第一行。
    * 其他常用的选项包括 `git log --graph --decorate --oneline`，它可以以图形化的方式显示分支和标签。

### 3. 分支管理

分支是 Git 中非常重要的概念，面试中也经常被问到。

1.  **查看分支:**
    * 使用 `git branch` 命令查看本地分支。当前所在的分支会用 `*` 标记。
    * 使用 `git branch -r` 查看远程分支。
    * 使用 `git branch -a` 查看所有分支（本地和远程）。

2.  **创建分支:**
    * 使用 `git branch <branch_name>` 创建一个新的本地分支。例如，创建一个名为 `feature-branch` 的分支：
        ```bash
        git branch feature-branch
        ```

3.  **切换分支:**
    * 使用 `git checkout <branch_name>` 切换到指定的分支。
        ```bash
        git checkout feature-branch
        ```
    * 你也可以使用 `git checkout -b <branch_name>` 命令来创建并立即切换到新的分支。
        ```bash
        git checkout -b another-feature
        ```

4.  **合并分支:**
    * 首先，切换回你想要合并到的目标分支（通常是 `main` 或 `master`）。
        ```bash
        git checkout main
        ```
    * 然后，使用 `git merge <branch_name>` 命令将指定的分支合并到当前分支。
        ```bash
        git merge feature-branch
        ```
    * 在合并过程中可能会出现冲突，你需要手动解决冲突，然后再次 `git add` 和 `git commit`。

5.  **删除分支:**
    * 删除本地分支：使用 `git branch -d <branch_name>` (如果分支已合并) 或 `git branch -D <branch_name>` (强制删除，即使未合并)。
        ```bash
        git branch -d feature-branch
        ```
    * 删除远程分支：使用 `git push origin --delete <branch_name>`.
        ```bash
        git push origin --delete another-feature
        ```

### 4. 远程仓库操作

1.  **推送本地更改到远程仓库:**
    * 使用 `git push <remote_name> <branch_name>` 命令将本地分支的提交推送到远程仓库。通常远程仓库的名字是 `origin`，主分支的名字可能是 `main` 或 `master`。
        ```bash
        git push origin main
        ```
    * 如果你是第一次推送新的本地分支到远程仓库，可能需要使用 `-u` 或 `--set-upstream` 选项来建立本地分支与远程分支的关联。
        ```bash
        git push -u origin feature-branch
        ```

2.  **拉取远程仓库的更改到本地:**
    * 使用 `git pull <remote_name> <branch_name>` 命令拉取远程分支的最新更改并合并到当前本地分支。
        ```bash
        git pull origin main
        ```

3.  **查看远程仓库信息:**
    * 使用 `git remote -v` 命令查看配置的远程仓库的详细信息，包括它们的名称和 URL。

### 5. 标签 (Tags)

标签用于标记仓库中的特定提交点，通常用于发布版本。

1.  **创建标签:**
    * 创建一个轻量级标签（lightweight tag），它只是一个指向特定提交的引用：
        ```bash
        git tag v1.0
        ```
    * 创建一个附注标签（annotated tag），它包含标签创建者的名字、邮箱、日期、以及一个标签消息：
        ```bash
        git tag -a v1.0 -m "Release version 1.0"
        ```

2.  **查看标签:**
    * 使用 `git tag` 命令列出所有标签。
    * 使用 `git show <tag_name>` 查看特定标签的详细信息。

3.  **推送标签到远程仓库:**
    * 默认情况下，`git push` 不会推送标签。你需要显式地推送标签：
        * 推送所有标签：`git push origin --tags`
        * 推送特定标签：`git push origin v1.0`

4.  **检出标签:**
    * 你可以像检出提交一样检出标签，这将使你的仓库处于该标签所指向的提交状态。
        ```bash
        git checkout v1.0
        ```
    * 注意，检出标签会使你处于“分离 HEAD”状态。如果你想在这个状态下进行更改，最好创建一个新的分支。

### 6. 忽略文件 (.gitignore)

`.gitignore` 文件用于指定 Git 应该忽略哪些文件和目录，不将它们纳入版本控制。

1.  **创建 .gitignore 文件:**
    * 在你的本地仓库的根目录下创建一个名为 `.gitignore` 的文件。

2.  **编辑 .gitignore 文件:**
    * 在文件中列出你想要忽略的文件和目录的模式。例如：
        ```
        *.log       # 忽略所有 .log 文件
        temp/       # 忽略名为 temp 的目录及其内容
        build/
        !important.log # 不忽略 important.log 文件，即使它符合之前的 *.log 规则
        ```

3.  **注意:** 已经添加到版本控制的文件，即使后来添加到 `.gitignore` 中，也不会被忽略。你需要先将它们从 Git 的跟踪中移除 (`git rm --cached <file>`)。

### 7. 撤销更改

1.  **撤销工作区的更改:**
    * 如果你的文件在工作区被修改了但还没有添加到暂存区，可以使用 `git restore <file>` 撤销更改。
        ```bash
        git restore hello.txt
        ```

2.  **撤销暂存区的更改:**
    * 如果你的文件已经添加到暂存区但还没有提交，可以使用 `git restore --staged <file>` 将文件移出暂存区。
        ```bash
        git restore --staged hello.txt
        ```

3.  **撤销最近一次提交:**
    * 使用 `git reset --soft HEAD^` 撤销最近一次提交，但保留更改在暂存区。
    * 使用 `git reset --mixed HEAD^` (默认) 撤销最近一次提交，并取消暂存更改，但保留工作区的更改。
    * 使用 `git reset --hard HEAD^` 撤销最近一次提交，并丢弃工作区的所有更改（谨慎使用！）。
    * `HEAD^` 指的是上一次提交，`HEAD^^` 指的是上上次提交，以此类推。你也可以使用提交的哈希值来指定要回退到的提交。

4.  **修改最近一次提交信息:**
    * 如果只是想修改最近一次提交的提交信息，可以使用 `git commit --amend`。

### 8. 解决冲突 (Merge Conflicts)

当合并分支时，如果 Git 无法自动判断如何合并相同的代码行，就会发生冲突。

1.  **识别冲突:**
    * 在 `git merge` 或 `git pull` 之后，Git 会告诉你哪些文件存在冲突。这些文件中会包含特殊的标记 (`<<<<<<<`, `=======`, `>>>>>>>`) 来指示冲突的部分。

2.  **解决冲突:**
    * 打开包含冲突的文件，手动编辑这些部分，选择你想要保留的更改，并删除冲突标记。

3.  **标记为已解决:**
    * 在解决完所有冲突后，使用 `git add <resolved_file>` 将修改后的文件添加到暂存区。

4.  **完成合并:**
    * 使用 `git commit` 命令提交合并结果。Git 会自动生成一个提交信息，你可以修改它。

### 9. Rebase

`git rebase` 是另一种合并分支的方法，它将当前分支的提交移动到目标分支的末尾，创建一个更线性的提交历史。

1.  **基本 Rebase:**
    * 切换到你的特性分支，然后执行 `git rebase <base_branch>`。例如：
        ```bash
        git checkout feature-branch
        git rebase main
        ```
    * 如果发生冲突，你需要像解决合并冲突一样解决它们，然后使用 `git add <resolved_file>` 和 `git rebase --continue`。如果想放弃 Rebase，可以使用 `git rebase --abort`。

2.  **交互式 Rebase:**
    * 使用 `git rebase -i <base_branch>` 可以进行交互式的 Rebase，允许你编辑、合并、删除提交等。
        ```bash
        git rebase -i main
        ```
    * 这将打开一个编辑器，你可以修改提交旁边的命令（例如，将 `pick` 改为 `squash` 来合并提交）。

**面试中可能被问到的 Git 知识点总结：**

* Git 的基本概念（工作区、暂存区、本地仓库、远程仓库）。
* 常用的 Git 命令及其作用（`clone`, `add`, `commit`, `push`, `pull`, `status`, `log`, `branch`, `checkout`, `merge`, `tag`, `remote`, `reset`, `rebase`）。
* 分支管理策略（创建、切换、合并、删除分支）。
* 解决合并冲突的流程。
* `git reset` 的不同模式 (`--soft`, `--mixed`, `--hard`) 及其区别。
* `git rebase` 和 `git merge` 的区别以及各自的使用场景。
* `.gitignore` 文件的作用和配置。
* 标签的使用场景和操作。
* 如何撤销更改。
* Git 的工作流程。

**练习建议：**

* 创建一个或多个本地分支，进行一些修改和提交。
* 尝试合并这些分支，人为制造一些冲突并解决它们。
* 使用 `git log` 查看提交历史，尝试使用不同的选项。
* 创建和推送标签。
* 修改 `.gitignore` 文件，观察 Git 如何忽略文件。
* 尝试使用 `git reset` 和 `git rebase` 来修改提交历史（在非重要分支上进行，避免影响主分支）。
* 与朋友或自己创建另一个 GitHub 账号，模拟多人协作的场景，练习 `push` 和 `pull` 操作。

通过不断地实践这些操作，你将能够更好地理解 Git 的工作原理，并为 Git 面试做好充分的准备。祝你学习顺利！
