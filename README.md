### camille Hugo blog 组成部分

1. hugo-theme-keep-forblog, keep theme,修改过后的主题。
2. hexo-blog-sourcecode，现在这个所有的源码，每次添加文件在这里加。
3. camillechang.github.io，用来 host 我的静态网站

# hexo-blog-sourcecode

- 当前的目录内设置了- GitHub Actions，具体见.github/workflows/hexo-deploy.yml
- GitHub Actions 当私有仓库的 hexo-blog-sourcecode master 有内容 push 进来时（例如：主题文件，文章 md 文件、图片等），
  会触发 GitHub Actions 自动编译并部署到公共仓库 camillechang.github.io 的 master 分支。
- 如果想修改主题的话，直接修改根目录下的\_config.keep.yml 就行，因为部署的时候，会替换原来的主题配置文件。
- 最后需要手动在 Custom domain，添加一下 domain name,过一会就能用了。暂时还没有想到其他解决办法。

## camillechang.github.io：Pages 报错 `No such file or directory ... /docs`

这条错误来自 **`camillechang.github.io` 仓库**里的 GitHub Pages 配置（Jekyll 在找不存在的 `docs` 目录），**改 hexo-blog-sourcecode 无法消除**，必须在**公开站仓库**里改。

1. 打开 **https://github.com/camillechang/camillechang.github.io** → **Settings** → **Pages**。
2. **Build and deployment** → **Source**：
   - 选 **Deploy from a branch**（从分支发布）。
   - **Branch**：`master`，**Folder**：**`/ (root)`**，**不要**选 **`/docs`**。
3. 若当前 Source 是 **GitHub Actions**：到同一仓库 **Actions** 或代码里的 **`.github/workflows/`**，删掉或停用会跑 **Jekyll**、且工作目录是 **`docs`** 的 workflow（日志里出现 `Source: .../docs` 就是它在跑）。改完后再把 Pages 的 Source 改成上面第 2 步的「从分支 + 根目录」，与 Hexo `hexo deploy` 推到 `master` 根目录的方式一致。
4. 站点根目录应有 **`CNAME`**（若用自定义域名）和 **`.nojekyll`**（由本仓库构建写入，避免 GitHub 再跑 Jekyll 处理静态文件）。

# Note:

最后需要手动在 Custom domain，添加一下 domain name,过一会就能用了。暂时还没有想到其他解决办法。

# 主要命令为

hexo new hello （这里的 article 写上你的文章的名称）
你的 source/\_posts 下就会生成一个 hello.md 文件，在这个文件下就可以写上你的博客内容了。用 Markdown 的语法去写。
打开标签功能：

![add tag](pictures/1.png)
![add catogory](pictures/2.png)

# 参考文章

https://sanonz.github.io/2020/deploy-a-hexo-blog-from-github-actions/
https://juejin.cn/post/6954942216808693773
