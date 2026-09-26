# Haokun Ren 学术主页

使用 Jekyll 构建、通过 GitHub Pages 发布的中英双语学术主页。

| 语言 | 路径 |
| --- | --- |
| 中文 | `/` |
| English | `/en/` |

## 内容维护

- 在 `_pages/about.md` 和 `_pages/en.md` 编辑中英文研究介绍。
- 在 `_data/navigation.yml` 维护双语导航标签。
- 在 `_data/publications.yml` 维护论文标题、作者顺序、双语摘要以及 arXiv/PDF 链接。
- 在 `_config.yml` 的 `author` 下维护姓名和双语研究简介。

## 本地开发

```bash
bundle install
bash run_server.sh
bundle exec jekyll build
```

项目没有自动化测试套件。修改后请构建站点，并检查 `_site/index.html` 和 `_site/en/index.html`。

## 部署与 Scholar 工具

推送到 `master` 会触发现有 GitHub Pages 部署。`google_scholar_crawler/` 是独立工具；主页不加载引用数，仓库也没有配置自动更新引用数的 workflow。
