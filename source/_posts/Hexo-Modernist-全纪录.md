---
title: Hexo Modernist 配置记录
mathjax: false
categories:
  - Tech
tags:
  - Hexo
  - Modernist
abbrlink: a4a6adfd
comments: true
date: 2020-10-31 22:51:58
---

此篇 post 记录一个小白定制化 Hexo Modernist 主题的相关问题。

<!--more-->
###  添加上下篇导航 
10/31/2020 更新。以下设置参考于 [mGoAlltWay](https://mm.hanbobo.net/2015/03/19/My-Hexo-Modernist-Theme/).
- 在 themes/modernist/layout/_partial/post/ 文件夹中新建 navi.ejs 文件, 添加以下代码：

```javascript
<% if (page.prev || page.next){ %>
<div class="navi clearfix">
  <% if (page.prev){ %>
    <a href="<%- config.root %><%- page.prev.path %>" class="alignleft prev" title="<%= page.prev.title %>"><%= page.prev.title %></a>
  <% } %>
  <% if (page.next){ %>
    <a href="<%- config.root %><%- page.next.path %>" class="alignright next" title="<%= page.next.title %>"><%= page.next.title %></a>
  <% } %>
</div>
<% } %>
```

- 在 themes/modernist/layout/_partial/article.ejs 中找到以下代码片段并加入刚创建的 navi

```javascript
<% } else { %>
      <%- partial('post/category') %>
      <%- partial('post/tag') %>
      <%# '此处是注释，加入navi 如下'%>
	  <%- partial('post/navi') %>
	  <%- partial('post/share') %>
	<% } %>
    <div class="clearfix"></div>
  </footer>
```
- 在 themes/modernist/source/css/_partial/article.styl 中添加以下 CSS代码

```javascript
/* navi */
  .navi
      margin 1em 0
      clear both
      overflow hidden
      a
        display block
        float left
        width 50%
        background #DEDEDE
        text-align center
        padding 0.4em 0
        color #595959
        transition background .45s color .45s
        &:hover
          color #fafafa
          background #717171
        &.prev::before
          content "上一篇："
          padding-right 0.5em
        &.next::before
          content "下一篇："
          padding-right 0.5em
    /*--end navi---*/
```
重新部署即可生成所需效果。

### 添加评论系统-- Disqus
11/1/2020 更新
1. [Disqus](https://disqus.com/)官网注册账号，登录后点击 GET STARTED 按钮，然后选择 I want to install Disqus on my site
2. 创建新的站点，在 Website Name 处 填写自己 shortname, Category 种类可选 Tech
3. 跳过 select plan, 直接在左侧选择 Install Disqus, 然后滑到最后，选择 I don't see my platform listed, install manually with Universal Code.
4. 复制第一段 JS 代码

- 在 themes/modernist/layout/_partial/post/ 文件中新建 comment.ejs 文件，添加刚才复制的JS 代码。

```javascript
<div id="disqus_thread"></div>
<script>

/**
*  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
*  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables*/
/*
var disqus_config = function () {
this.page.url = PAGE_URL;  // Replace PAGE_URL with your page's canonical URL variable
this.page.identifier = PAGE_IDENTIFIER; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
};
*/
(function() { // DON'T EDIT BELOW THIS LINE
var d = document, s = d.createElement('script');
s.src = 'https://hjqian96-1.disqus.com/embed.js';
s.setAttribute('data-timestamp', +new Date());
(d.head || d.body).appendChild(s);
})();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>                       
```
- 在 themes/modernist/layout/_partial/article.ejs  中找到以下代码片段并加入 comment

```javascript
<% } else { %>
      <%- partial('post/category') %>
      <%- partial('post/tag') %>
      <%# '添加 navi'%>
      <%- partial('post/navi') %>
      <%- partial('post/share') %>

      <%# '添加 comment'%>
      <% if (post.layout != ‘page’) { %>
      <%- partial(‘comment’) %>
      <% } %>
    <% } %>
```

[^1]: a footnote demonstration.