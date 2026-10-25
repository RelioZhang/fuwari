# 自定义改动清单

同步上游（saicaca/fuwari）之前先读这里。以下是相对原仓库的改动，merge 时重点看这几处。

## 一、改过的上游文件（merge 可能冲突）

| 文件 | 改动内容 | 冲突风险 | 处理原则 |
|---|---|---|---|
| `src/config.ts` | 站名、副标题、语言、主题色、头像、签名、导航、社交链接 | **中**（上游常改这个文件） | 保留本地的值，接受上游新增的字段 |
| `src/pages/posts/[...slug].astro` | License 之后插入 `<GiscusComments />` 及对应 import | 低（各一行） | 保留插入，其余接受上游 |
| `src/content/spec/about.md` | 换成了自己的中文介绍 | 无（内容文件） | 上游不会覆盖 |
| `src/assets/images/avatar.png` | 自己的头像（并删了 demo-avatar.png） | 无 | — |

## 二、新增文件（merge 永不冲突）

| 文件 | 用途 |
|---|---|
| `src/components/misc/GiscusComments.astro` | giscus 评论组件 |
| `src/content/posts/*.md` | 18 篇文章 |

## 三、同步上游

```bash
git remote add upstream https://github.com/saicaca/fuwari.git   # 只需一次
git fetch upstream
git merge upstream/main
```

冲突集中在 `src/config.ts` 时：**保留本地的站点信息**，接受上游新增的配置项。
不要用 `git rebase` 除非你能把冲突逐个解完——merge 更容易回退。

## 四、绝对不要做的事

- `git reset --hard upstream/main` —— 会丢掉全部自定义和文章
- `git checkout upstream/main -- .` —— 同上
- 删除 `src/content/posts` 或 `src/content/spec`
- 把 `src/config.ts` 直接替换成上游版本

## 五、加新功能时的原则

1. **优先新增文件，不改上游文件**：新页面放 `src/pages/`，新组件放 `src/components/`，上游永远不会碰这些路径。
2. **只改配置的「值」，不改配置的「结构」**：在 `config.ts` 里改字符串和数字是安全的，改对象结构会提高冲突概率。
3. **第三方服务用 `<script is:inline>` 注入**，不要引新的 npm 依赖；依赖越多，`package.json` 的冲突越难解。
4. **每次改动记到这张表里**，否则半年后 merge 冲突时不知道怎么取舍。

## 六、已知问题（待处理）

- `astro.config.mjs` 的 `site` 仍是 `https://fuwari.vercel.app/`，会导致 sitemap、RSS、OG 里的绝对链接错误，需要改成实际域名。
- giscus 与 swup 的兼容：swup 切换页面时会替换 `main` 容器，评论 iframe 不会自动重新初始化，需要在 `page:load` 事件里重新注入。
