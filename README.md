### camille Hugo blog 组成部分

1. hugo-theme-keep-forblog, keep theme,修改过后的主题。
2. hexo-blog-sourcecode，现在这个所有的源码，每次添加文件在这里加。
3. camillechang.github.io，用来 host 我的静态网站

# hexo-blog-sourcecode

- 当前的目录内设置了- GitHub Actions，具体见.github/workflows/hexo-deploy.yml
- GitHub Actions 当私有仓库的 hexo-blog-sourcecode master 有内容 push 进来时（例如：主题文件，文章 md 文件、图片等），
  会触发 GitHub Actions 自动编译并部署到公共仓库 camillechang.github.io 的 master 分支。
- 最后需要手动在 Custom domain，添加一下 domain name,过一会就能用了。暂时还没有想到其他解决办法。

# Note:

最后需要手动在 Custom domain，添加一下 domain name,过一会就能用了。暂时还没有想到其他解决办法。
