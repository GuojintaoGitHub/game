# 用 GitHub Pages 发布俄罗斯方块 - 详细步骤

按下面顺序做即可，完成后会得到一个类似 `https://你的用户名.github.io/tetris/` 的链接，发给别人就能玩。

---

## 第一步：注册 / 登录 GitHub

1. 打开 [https://github.com](https://github.com)
2. 没有账号就点 **Sign up** 注册，有账号就 **Sign in** 登录

---

## 第二步：新建仓库（Repository）

1. 登录后，点击右上角 **+** → **New repository**
2. 填写：
   - **Repository name**：例如填 `tetris` 或 `tetris-game`（只能英文、数字、短横线）
   - **Description**：可选，例如「俄罗斯方块小游戏」
   - **Public** 选中
   - **不要**勾选 "Add a README file"
3. 点击 **Create repository**

---

## 第三步：把游戏文件上传到仓库

有两种方式，任选其一。

### 方式 A：在网页上直接上传（推荐，不用装 Git）

1. 进入你刚建好的仓库页面（空仓库会提示 "uploading an existing file"）
2. 点击 **uploading an existing file**（或 **Add file** → **Upload files**）
3. 把本地的 **`tetris.html`** 拖进浏览器窗口  
   - 若希望链接是 `https://用户名.github.io/仓库名/` 直接打开游戏，可先把 `tetris.html` 改名为 **`index.html`** 再上传
4. 在页面底部 **Commit changes** 里可以不改，直接点 **Commit changes**

### 方式 B：用命令行（已安装 Git 时可用）

在终端里进入项目文件夹，执行（把 `你的用户名` 和 `tetris` 换成你的 GitHub 用户名和仓库名）：

```bash
cd "/Users/jintao.guo/Cursor Demo 2026.3.2"
git init
git add tetris.html
git commit -m "Add tetris game"
git branch -M main
git remote add origin https://github.com/你的用户名/tetris.git
git push -u origin main
```

若仓库里希望首页就是游戏，可以先把 `tetris.html` 复制为 `index.html` 再 `git add index.html` 并提交。

---

## 第四步：开启 GitHub Pages

1. 在仓库页面点击上方 **Settings**（设置）
2. 左侧菜单最下方找到 **Pages**
3. 在 **Build and deployment** 里：
   - **Source** 选 **Deploy from a branch**
   - **Branch** 选 **main**，右边文件夹选 **/ (root)**
4. 点 **Save** 保存

---

## 第五步：拿到访问链接

1. 保存后刷新页面，顶部会出现绿色提示：**Your site is live at https://你的用户名.github.io/仓库名/**
2. 若你上传的是 **`index.html`**，访问  
   `https://你的用户名.github.io/仓库名/`  
   就会直接打开游戏。
3. 若你上传的是 **`tetris.html`**，则访问  
   `https://你的用户名.github.io/仓库名/tetris.html`  
   才能打开游戏。

把对应链接发给别人即可，无需登录就能玩。

---

## 常见问题

**Q：上传后要等多久才能访问？**  
A：通常 1～2 分钟。若打不开，等 5 分钟再试或检查仓库名、用户名是否正确。

**Q：想换链接里的仓库名怎么办？**  
A：在仓库 **Settings** → **General** 最下方可改仓库名，改完后链接会变成 `https://用户名.github.io/新仓库名/`。

**Q：以后想更新游戏怎么办？**  
A：在仓库里点击 `tetris.html` 或 `index.html` → 点击铅笔图标编辑，改完后 **Commit changes**；或重新上传覆盖原文件。更新后几分钟内新内容会生效。

---

## 小结

| 步骤 | 做什么 |
|------|--------|
| 1 | 注册/登录 GitHub |
| 2 | 新建一个 Public 仓库（如 `tetris`） |
| 3 | 上传 `tetris.html`（可选改名为 `index.html`） |
| 4 | Settings → Pages → 选 main 分支、/ (root) → Save |
| 5 | 用提示的链接访问并分享给他人 |

完成以上步骤后，你的俄罗斯方块就可以通过链接给任何人使用了。
