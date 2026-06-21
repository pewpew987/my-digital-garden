# Obsidian + GitHub 知识库与博客构建指南
ps:这是第二次v4版本

本指南将带你完成从本地写作到云端托管的完整闭环。请严格按照顺序执行。

## 第一阶段：建立云端与本地的连接（基础练习）

_(此阶段用于理解原理，你已完成)_

1. 在 GitHub 创建云端仓库。
    
2. 用 GitHub Desktop 将仓库克隆 (Clone) 到本地。
    
3. 将 Obsidian 接入该本地文件夹。
    

## 第二阶段：日常工作流 (The Daily Loop)

_(此阶段为你以后的核心操作，你已掌握)_

1. **创作**：在 Obsidian 中写 Markdown 文件。
    
2. **确认与打包**：在 GitHub Desktop 中写 Summary，点击 Commit。
    
3. **推送上云**：点击 Push origin 同步到 GitHub。
    

## 第三阶段：部署 Quartz 静态博客（正式建站）

纯文本（Markdown）需要一个“翻译器”才能变成网页。目前 Obsidian 生态中最优秀且支持双向链接的框架是 **Quartz 4**。

为了避免在你的电脑上安装复杂的本地代码环境，我们将利用 GitHub 的云端服务器（GitHub Actions）来自动为你“翻译”并生成网页。

### 1. 复制 (Fork) 官方博客模板到你的账号

你需要把开发者的开源模板，合规地“复制”一份成为你自己的初始网站。**这一步极易选错版本，请务必仔细操作。**

1. 登录你的 GitHub，在浏览器中打开 Quartz 的开源仓库主页：[https://github.com/jackyzha0/quartz](https://github.com/jackyzha0/quartz "null")
    
2. 点击页面右上角的 **Fork** 按钮。
    
3. 在弹出的页面中：
    
    - **Repository name**: 给你的博客起个正式的名字（建议全小写英文或拼音，不要有空格，如 `my-digital-garden`）。
        
    - **【高危注意】**：由于开发者正在开发 v5 版本，默认复制的可能是 v5。请**务必**取消勾选 "Copy the default branch only"（只复制默认分支），以确保你可以获取到稳定的 **`v4`** 分支。
        
4. 点击绿色的 **Create fork**。 _(现在，你的账号下就有了一个带有完整网页渲染代码的新仓库了。)_
    
5. **【关键：切换默认分支】** 进入你刚创建的仓库，点击 **Settings** -> 左侧边栏点击 **Default branch**（默认分支） -> 将它从 `v5` 或 `main` 切换为 **`v4`**，点击 Update 更新。
    

### 2. 授权 GitHub 云端服务器自动构建网页

你需要告诉 GitHub：“以后我只要传了新的 Markdown 笔记上来，你就自动帮我生成网页。”

1. 留在你的新仓库页面。
    
2. 点击仓库主页顶部的 **Settings** 选项卡（⚙️图标）。
    
3. 在左侧边栏向下滚动，找到并点击 **Pages**。
    
4. 在右侧的核心设置区，找到 **Build and deployment** 下方的 **Source**。
    
5. 将 Source 的下拉菜单从 "Deploy from a branch" 更改为 **GitHub Actions**。 _(这一步极其关键，它激活了 Quartz 自带的云端自动化工作流。)_
    

### 3. 用 GitHub Desktop 克隆你的新博客

1. 打开 GitHub Desktop。
    
2. 点击左上角 `File` -> `Clone repository...`。
    
3. 在列表里找到你刚才 Fork 的新仓库（如 `my-digital-garden`）。
    
4. 选择一个新的 `Local Path`（例如 `D:\my-digital-garden`），点击 **Clone**。
    

### 4. 将 Obsidian 接入博客的 `content` 文件夹

Quartz 框架有严格的目录结构，只有放在特定文件夹里的笔记才会被变成网页。

1. 打开 Obsidian，点击左下角的 **打开其他仓库 (Open another vault)**。
    
2. 选择 **"打开文件夹作为仓库"**。
    
3. 浏览你刚刚克隆的新文件夹（`D:\my-digital-garden`），**请双击进入这个文件夹，然后选中它里面的 `content` 子文件夹**。
    
4. 点击“选择文件夹”打开。 _(逻辑：Quartz 会把 `content` 文件夹里的所有东西渲染成网页。所以你以后只在这个 `content` 文件夹里写东西即可。)_
    

### 5. 撰写、推送与见证奇迹

1. 在 Obsidian（目前指向 `content` 文件夹）中，你会看到一个自带的 `index.md`，这是你网站的首页。你可以修改它，或者新建一篇标题为 `index` 的 `.md` 笔记。
    
2. 随意写一句话（例如：“强制唤醒测试 123”），保存后打开 GitHub Desktop。
    
3. 和第二阶段一样：填写 Summary -> 点击 **Commit to v4** -> 点击 **Push origin**。
    

### 6. 查看你的专属网站

1. 回到浏览器，打开你在 GitHub 上的仓库主页。
    
2. 点击顶部栏的 **Actions** 选项卡。此时你应该能看到一个名为 **`Deploy Quartz site`** 的任务，带有黄色动画圆圈正在运行。
    
3. 喝口水等待约 1-2 分钟。当圆圈变成**绿色的对勾 (✅)**，说明网站构建完成。
    
4. 回到仓库的 **Settings** -> **Pages** 页面。
    
5. 页面顶部会显示一行字：**"Your site is live at https://你的用户名.github.io/my-digital-garden"**。
    
6. 点击那个网址，你的博客就正式上线了。