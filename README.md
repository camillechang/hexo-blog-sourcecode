### camille Hugo blog 组成部分

1. keep theme,修改过后的，保存在 repo hugo-theme-keep-forblog
2. 现在这个所有的源码，每次添加文件在这里加。
3. 编译后，hexo d,部署到 camillechang.github.io 里面。

# hexo-blog-sourcecode

- This is the sourcecode website for blog.
- GitHub Actions 当私有仓库的 hexo-blog-sourcecode master 有内容 push 进来时（例如：主题文件，文章 md 文件、图片等），
  会触发 GitHub Actions 自动编译并部署到公共仓库 camillechang.github.io 的 master 分支。

# Note:

# Preventing CNAME file being removed by Github Actions

https://blog.mattdaines.me/p/adding-a-custom-domain-to-your-hugo-site-on-github-pages/
In your site root, create a directory named static

Create a file named CNAME - make sure there’s no file extension

Add your custom domain name to this file. For my site that would mean a file containing blog.mattdaines.me.
