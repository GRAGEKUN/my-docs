# 关于本项目

## 项目目标

实现从 Markdown 文档到公开网站的自动化发布：作者只维护 `docs/` 里的文本，剩下的构建与发布交给流水线。

## 技术组成

| 工具 | 作用 | 在本次实践中的位置 |
| --- | --- | --- |
| Markdown | 编写文档内容 | `docs/*.md` |
| MkDocs Material | 将文档构建成静态网站 | `mkdocs.yml` + `requirements.txt` |
| GitHub Actions | 自动执行安装、构建和部署 | `.github/workflows/deploy.yml` |
| GitHub Pages | 托管并提供网站访问地址 | 仓库 Settings → Pages |

## 目录职责

```text
my-docs/
├── docs/                 # 源码：页面内容
├── mkdocs.yml            # 源码：站点配置与导航
├── requirements.txt      # 源码：依赖版本范围
├── .github/workflows/    # 源码：部署流水线定义
├── site/                 # 构建产物：自动生成，已忽略
└── report/               # 作业报告与截图
```

- `docs/`：四页 Markdown，是网站内容的唯一来源。
- `nav`：`mkdocs.yml` 中的导航声明，路径相对 `docs/`，写 `index.md` 而不是 `docs/index.md`。
- `site/`：`mkdocs build` 的输出目录，由 Actions 打包成 artifact 后交给 Pages。

## 一次发布发生了什么

1. 我把 `docs/` 的修改推到 `main`。
2. 工作流匹配到 `paths` 规则，启动 `build` 任务：检出源码 → 配置 Python 3.12 → 安装依赖 → `mkdocs build --strict` → 上传 `site/`。
3. `build` 成功后 `deploy` 任务开始，用 `actions/deploy-pages` 把 artifact 发布到 `github-pages` 环境。
4. 网站地址刷新后即为新内容。

因为页面是纯静态 HTML/CSS/JS，没有数据库和服务端进程，所以托管成本为零，也不需要 `gh-pages` 分支：产物直接通过 Pages 的 artifact 通道发布。

返回 [首页](index.md)，或继续阅读 [使用指南](guide.md)。
