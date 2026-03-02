# 本地代码与 GitHub 同步指南

改完本地文件后，用 Git 把更改推送到 GitHub，网页上的游戏就会更新。按下面做一次「首次设置」，之后每次改完代码只需执行 3 条命令即可同步。

---

## 一、首次设置（只需做一次）

在终端里执行（把 `你的用户名` 和 `tetris` 换成你的 GitHub 用户名和仓库名）。**每条命令的含义**如下：

```bash
cd "/Users/jintao.guo/Cursor Demo 2026.3.2"
```
| 命令 | 含义 |
|------|------|
| `cd "路径"` | **切换当前目录**到指定路径，这里进入你的项目文件夹，后面的 Git 命令都会在这个文件夹里生效。 |

```bash
git init
```
| 命令 | 含义 |
|------|------|
| `git init` | **初始化 Git 仓库**。在当前文件夹里创建一个隐藏的 `.git` 目录，用来记录版本历史，这样 Git 才能管理这个项目。 |

```bash
git add .
```
| 命令 | 含义 |
|------|------|
| `git add .` | **把当前目录下所有修改过的、未跟踪的文件加入“暂存区”**。点号 `.` 表示“当前目录及子目录”，暂存区是提交前的准备区，只有被 add 过的内容才会被下一次 commit 提交。 |

```bash
git commit -m "同步本地游戏"
```
| 命令 | 含义 |
|------|------|
| `git commit -m "说明"` | **把暂存区里的内容正式保存为一次“提交”**，并写一句说明（`-m` 后面用引号包起来）。每次 commit 会生成一个版本快照，方便以后查看或回退。 |

```bash
git branch -M main
```
| 命令 | 含义 |
|------|------|
| `git branch -M main` | **把当前分支改名为 main**（`-M` 表示强制重命名）。GitHub 默认主分支叫 `main`，这样本地和远程分支名一致，后面 push 时不会搞错。 |

```bash
git remote add origin https://github.com/你的用户名/tetris.git
```
| 命令 | 含义 |
|------|------|
| `git remote add origin 地址` | **添加一个名为 origin 的“远程仓库”地址**。origin 是习惯用法，表示你在 GitHub 上的那个仓库；之后 `git push`、`git pull` 都会用这个地址。 |

```bash
git pull origin main --allow-unrelated-histories
```
| 命令 | 含义 |
|------|------|
| `git pull origin main` | **从远程仓库的 main 分支拉取最新内容，并合并到当前分支**。pull = fetch（拉取） + merge（合并）。 |
| `--allow-unrelated-histories` | **允许合并不相关历史**。你本地是新建的仓库，GitHub 上是网页上传的，两边没有共同祖先，加这个参数才能合并，否则 Git 会拒绝。 |

若提示有冲突（conflict），保留本地版本即可：

```bash
git checkout --ours tetris.html
```
| 命令 | 含义 |
|------|------|
| `git checkout --ours 文件名` | **在合并冲突时，指定该文件采用“我们当前分支”的版本**（即你本地的版本），用来解决冲突。 |

```bash
git add tetris.html
git commit -m "合并并保留本地版本"
```
| 命令 | 含义 |
|------|------|
| `git add tetris.html` | **把解决冲突后的 tetris.html 加入暂存区**，表示冲突已处理完。 |
| `git commit -m "..."` | **提交这次合并**，并写上说明。 |

```bash
git push -u origin main
```
| 命令 | 含义 |
|------|------|
| `git push -u origin main` | **把当前分支的提交推送到远程仓库 origin 的 main 分支**。`-u` 表示“设置上游分支”，以后在这个分支上直接打 `git push` 就会默认推到 origin/main，不用再写后面一截。 |

**说明**：若 GitHub 上仓库是空的或你还没建仓库，可省略 `git pull` 那行，直接执行 `git push -u origin main`（需要先在 GitHub 上新建一个空仓库）。

---

## 二、以后每次改完代码怎么同步

在项目文件夹里打开终端，执行下面 3 条。**每条命令的含义**如下：

```bash
cd "/Users/jintao.guo/Cursor Demo 2026.3.2"
```
| 命令 | 含义 |
|------|------|
| `cd "路径"` | **进入你的项目目录**，确保在正确的文件夹里执行后面的 Git 命令。 |

```bash
git add .
```
| 命令 | 含义 |
|------|------|
| `git add .` | **把所有修改过的文件加入暂存区**，准备参与下一次提交。 |

```bash
git commit -m "这里写一句更新说明，比如：修复分数、更新界面"
```
| 命令 | 含义 |
|------|------|
| `git commit -m "说明"` | **把暂存区的内容提交为一个新版本**，`-m` 后面的文字会出现在 GitHub 的提交历史里，方便以后知道这次改了啥。 |

```bash
git push
```
| 命令 | 含义 |
|------|------|
| `git push` | **把本地刚提交的内容推送到 GitHub**。因为首次设置时用过 `git push -u origin main`，这里不用再写分支名，Git 会自动推到 origin 的 main 分支。 |

执行完后，GitHub 上的文件和你的 GitHub Pages 链接里的内容会在 1～2 分钟内更新。

---

## 三、没有安装 Git 时

1. **下载**：打开 [https://git-scm.com/downloads](https://git-scm.com/downloads)，选 macOS 安装包并安装。
2. **验证**：安装后打开终端，输入 `git --version`，能看到版本号即表示安装成功。
3. **首次使用**：在终端里设置用户名和邮箱（与 GitHub 一致更好）：

   ```bash
   git config --global user.name "你的GitHub用户名"
   git config --global user.email "你的GitHub邮箱"
   ```

   | 命令 | 含义 |
   |------|------|
   | `git config --global user.name "..."` | **设置全局用户名**，以后每次 commit 都会记录这个名字，在 GitHub 上会显示是谁提交的。 |
   | `git config --global user.email "..."` | **设置全局邮箱**，一般填你登录 GitHub 的邮箱，便于在 GitHub 上关联你的账号。 |
   | `--global` | 表示对你这台电脑上所有 Git 仓库生效，不用每个项目单独设一次。 |

4. 然后按上面「首次设置」和「以后每次改完代码」的步骤操作即可。

---

## 四、常用命令速查（含含义）

| 命令 | 含义 |
|------|------|
| `cd "路径"` | 进入指定文件夹。 |
| `git init` | 把当前文件夹变成 Git 仓库（只做一次）。 |
| `git add .` | 把所有修改加入暂存区，准备提交。 |
| `git add 文件名` | 只把指定文件加入暂存区。 |
| `git commit -m "说明"` | 把暂存区的内容保存为一次提交，并写一句说明。 |
| `git push` | 把本地提交推送到 GitHub（需先设好 remote 和上游分支）。 |
| `git pull` | 从 GitHub 拉取最新内容并合并到本地。 |
| `git status` | 查看当前有哪些文件被修改、是否已加入暂存区、是否有未提交的提交。 |

---

## 五、小结

- **首次**：在项目文件夹里执行「一、首次设置」里的命令，把本地和 GitHub 连起来并推一次。
- **之后**：改完代码 → `git add .` → `git commit -m "说明"` → `git push`，即可同步，链接会一直有效并显示最新版本。
