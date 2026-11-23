# my-docs

个人技术文档站：用 Markdown + MkDocs Material 编写，通过 GitHub Actions 自动构建并部署到 GitHub Pages。

- 网站：<https://GRAGEKUN.github.io/my-docs/>
- 源码：<https://github.com/GRAGEKUN/my-docs>
- 作业报告：[个人实验报告](report/README.md)

## 本地预览

```bash
python -m venv .venv
# Windows PowerShell
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
python -m mkdocs serve        # http://127.0.0.1:8000/
python -m mkdocs build --strict
```

## 目录

| 路径 | 作用 |
| --- | --- |
| `docs/` | 网站内容（四页 Markdown） |
| `mkdocs.yml` | 站点配置与导航 |
| `.github/workflows/deploy.yml` | 自动构建与部署流水线 |
| `report/` | 作业报告与截图 |
| `site/` | 构建产物，自动生成，已忽略 |

推送 `docs/`、`mkdocs.yml`、`requirements.txt` 或工作流本身的改动到 `main`，会自动触发构建与部署。
