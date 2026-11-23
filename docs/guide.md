# 使用指南

## 日常写作流程

1. 修改 `docs` 目录中的 Markdown 文件。
2. 在本地预览并检查页面及链接。
3. 提交修改并推送到 `main` 分支。
4. 在 Actions 页面查看构建与部署状态。
5. 打开网站检查内容是否更新。

## 常用命令

```bash
# 首次准备（在项目根目录）
python -m venv .venv
# Windows PowerShell 激活
.\.venv\Scripts\Activate.ps1

# 安装依赖
python -m pip install -r requirements.txt

# 本地预览，默认 http://127.0.0.1:8000/
python -m mkdocs serve

# 构建并严格检查警告（CI 使用同一条命令）
python -m mkdocs build --strict
```

## 命令对照表

| 命令 | 用途 | 产物 |
| --- | --- | --- |
| `mkdocs serve` | 本地预览，改文件自动刷新 | 内存中的临时站点 |
| `mkdocs build` | 生成本地静态站点 | `site/` |
| `mkdocs build --strict` | 把警告当错误处理 | `site/` 或直接失败 |

`--strict` 是我特意保留的：链接写错、导航指向不存在的文件这类低级错误会在 CI 阶段直接失败，而不是发布一个 404 网站。

## 配置示例

```yaml
site_name: 我的技术文档
site_url: https://GRAGEKUN.github.io/my-docs/
theme:
  name: material
  language: zh
nav:
  - 首页: index.md
  - 关于: about.md
  - 使用指南: guide.md
  - API参考: api.md
```

## 排错清单

- `site_url` 少了仓库路径 → Pages 资源 404。
- `nav` 里写了 `docs/index.md` → 构建报文件不存在。
- YAML 用了 Tab 缩进 → 解析失败。
- 只改了 `report/README.md` → 工作流不触发，这是 `paths` 过滤的预期行为。

回到 [首页](index.md) 或查看 [API 参考](api.md)。
