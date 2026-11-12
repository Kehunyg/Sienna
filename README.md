# 向泫朦 · 个人作品集

静态站点，单页 HTML + 一个本地视频。没有任何构建步骤，克隆下来用浏览器打开 `index.html` 就能看。

域名：`xuanmeng.xyz`（托管在 Cloudflare Pages）

---

## 目录

```
index.html            整个作品集（CSS/JS/图片全部内联，约 0.85 MB）
field-stories.mp4     结尾的英语短视频（约 17 MB，懒加载，与 index.html 同目录）
README.md
```

## 在 Cloudflare Pages 上部署

1. 把这个仓库 push 到 GitHub（网页上传也可以，两个文件都不用命令行）
2. 登录 Cloudflare → **Workers & Pages** → **Create** → **Pages** → **Connect to Git**
3. 选中本仓库，构建配置按下面填（**不要**让它自动猜）：
   - Framework preset：`None`
   - Build command：**留空**
   - Build output directory：`/`
4. 点 Save and Deploy，一两分钟出结果，先拿到一个 `xxx.pages.dev` 的临时地址
5. 进项目 → **Custom domains** → 添加 `xuanmeng.xyz` 和 `www.xuanmeng.xyz`
6. 域名要能绑上，前提是 `xuanmeng.xyz` 已经添加到同一个 Cloudflare 账号（Add a site），并且 NS 已从阿里云改成 Cloudflare 给的那两个

## 更新作品集内容

`index.html` 是从本地 Next.js 项目导出的完整快照，不是手改的文件。更新流程：

1. 本地重新导出新的 HTML 快照（覆盖旧的）
2. 用新文件替换仓库里的 `index.html`
3. 提交，Cloudflare Pages 会自动重新部署

不要直接在这个 HTML 里改文案——下次导出会被覆盖。

## 备用站点（保留，不要关）

WorkBuddy 上还有一份在线原站，作为备份长期保留：

```
https://xiang-portfolio.app.workbuddy.host/?sharecode=ZHZCNVVBHT
```

- 新站（Cloudflare Pages）出任何问题，这个地址随时能顶上
- 简历上可以两个都写：主推 `xuanmeng.xyz`，括号里备注原链接
- 原站里的视频，本仓库已复制一份（`video/field-stories.mp4`），两边互不依赖

## 几个注意

- **视频与 index.html 同目录**：文件名 `field-stories.mp4`，网页里用相对路径引用。改视频文件名要同步改 HTML 里的 `data-src`。
- **字体走 Google Fonts CDN**：国内网络可能加载失败，会自动回退到系统衬线体，布局不会错乱。想要稳定的字体，可以把 woff2 下载下来内联。
- **国内访问**：Cloudflare 免费节点，速度一般，偶尔需要刷新一次。这是不备案的代价，换来的是免审核、HTTPS 自动签发。
- 备案（ICP）对 Cloudflare Pages 没有意义——备案只针对中国大陆境内的服务器。
