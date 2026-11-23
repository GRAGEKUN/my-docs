# 我的技术文档

欢迎访问我的个人文档网站。本网站使用 **Markdown + MkDocs Material** 构建，通过 **GitHub Actions** 自动部署到 **GitHub Pages**。

## 站点信息

| 项目 | 内容 |
| --- | --- |
| 作者 | GRAGEKUN |
| 实践主题 | 静态文档自动部署 |
| 构建工具 | MkDocs 1.6 + Material 9.6 |
| 部署方式 | GitHub Actions 官方 Pages 工作流 |
| 源码仓库 | <https://github.com/GRAGEKUN/my-docs> |

## 页面导航

- [关于本项目](about.md) —— 站点目标、技术组成与目录职责
- [使用指南](guide.md) —— 本地预览、构建与日常写作流程
- [API 参考](api.md) —— 文档示例接口的请求与返回格式

## 为什么做这个站点

我平时查资料时经常遇到“文档写在本地、同事看不到”的问题。这次实践想验证一条最小可用的路径：
本地写 Markdown → 推送到 GitHub → 云端自动构建 → 网页立即更新。

整条链路里唯一需要人工做的事就是 `git push`，其余步骤（安装依赖、构建站点、上传产物、发布 Pages）全部由工作流完成。
这也解释了一个常见误解：**`site/` 目录是构建产物，它由 MkDocs 生成，不属于源码**，所以它被写进 `.gitignore`，永远不手工修改。

