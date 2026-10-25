---
title: Firefly博客添加评论功能
published: 2026-08-07
tags: [Markdown, 博客, 评论区]
category: 评论区
draft: false
---

除了友链之外，再加个评论的功能，那就可以收到大伙的评论了！

我选择使用`giscus`来实现评论功能。主要是它不需要依赖于数据库，而且配置也比较简单，最主要的是依赖于`Github`并且纯免费！！！

### 配置giscus[#](#配置giscus)

*   首先，你需要创建一个新的GitHub库用来保存博客的那些评论，你需要确保该仓库是公开的,否则访客将无法查看 `Discussion`。
*   然后，你需要给你的这个仓库repo安装[giscus app](https://github.com/apps/giscus),否则访客将无法评论和回应。
*   最后，你需要确保 `Discussions` 功能已在你的仓库中启用。

打开giscus官方网站 `https://giscus.app/`，进行配置：

*   语言：选择你目前正在使用的语言
*   仓库：填写你刚刚创建的仓库(格式为你的用户名/仓库名)
*   页面 ↔️ discussion 映射关系(默认即可)
*   Discussion 分类（默认即可）
*   特性（默认即可）
*   主题（默认即可）

按照顺序配置好之后，下方会自动生成

```


`<script src="https://giscus.app/client.js"
 data-repo="[在此输入仓库]"
 data-repo-id="[在此输入仓库 ID]"
 data-category="[在此输入分类名]"
 data-category-id="[在此输入分类 ID]"
 data-mapping="pathname"
 data-strict="0"
 data-reactions-enabled="1"
 data-emit-metadata="0"
 data-input-position="bottom"
 data-theme="preferred_color_scheme"
 data-lang="zh-CN"
 crossorigin="anonymous"
 async>
</script>` 


```

### 添加评论到指定页面[#](#添加评论到指定页面)

只需要在每个页面对应的`.astro`文件中的`</MainGridLayout>`前面添加上方生成的代码即可。

比如我要在文章页面添加评论，找到`src\pages\posts\[...slug].astro`文件，在文件中找到`</MainGridLayout>`标签，在其前面添加上方生成的代码即可。

```


 `<Icon name="material-symbols:chevron-right-rounded" class="text-[2rem] text-[var(--primary)]" />
 </div>}
 </a>
 </div>
<!-- giscus评论 -->
+ <script src="https://giscus.app/client.js"
+    data-repo="AULyPc/aulypc.github.io"
+    data-repo-id="xxxxxxxxxxx"
+    data-category="Announcements"
+    data-category-id="xxxxxxxxxxxxx"
+    data-mapping="pathname"
+    data-strict="0"
+    data-reactions-enabled="1"
+    data-emit-metadata="0"
+    data-input-position="top"
+    data-theme="preferred_color_scheme"
+    data-lang="zh-CN"
+    crossorigin="anonymous"
+    async>
+</script>
</MainGridLayout>
<style is:global>
#post-container :nth-child(1) { animation-delay: calc(var(--content-delay) + 0ms) }
#post-container :nth-child(2) { animation-delay: calc(var(--content-delay) + 50ms) }
#post-container :nth-child(3) { animation-delay: calc(var(--content-delay) + 100ms) }
#post-container :nth-child(4) { animation-delay: calc(var(--content-delay) + 175ms) }
#post-container :nth-child(5) { animation-delay: calc(var(--content-delay) + 250ms) }
#post-container :nth-child(6) { animation-delay: calc(var(--content-delay) + 325ms) }
</style>` 


```

最后效果如图 ![](https://blog.kimbleex.top/_astro/comment.BnHt7-YC_20ScJO.webp)