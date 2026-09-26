# Haokun Ren 学术主页

基于 [AcadHomepage](https://github.com/RayeRen/acad-homepage.github.io) 与 Minimal Mistakes 构建的 Jekyll 中英双语学术主页。

| 语言 | 路径 |
| --- | --- |
| 中文 | `/` |
| English | `/en/` |

## 内容维护

- 在 `_pages/about.md` 和 `_pages/en.md` 编辑中英文研究介绍。
- 在 `_data/navigation.yml` 维护双语 masthead 导航。
- 在 `_data/publications.yml` 维护论文标题、作者顺序、双语摘要以及 arXiv/PDF 链接。
- 在 `_config.yml` 的 `author` 下维护姓名和双语简介。

## 框架

共享布局、顶部导航、作者侧栏、Sass 主题和论文卡片采用 AcadHomepage/Minimal Mistakes 组件结构。上游主题资源基于 AcadHomepage 提交 [`2cc1577`](https://github.com/RayeRen/acad-homepage.github.io/tree/2cc1577eeaf2f74dede6d016a70722dbd409ea2f)。项目保留上游 MIT 许可证及主题依赖的版权声明。

## 本地开发

```bash
bundle install
bash run_server.sh
bundle exec jekyll build
```

项目没有自动化测试套件。修改后请构建站点，并检查 `_site/index.html` 和 `_site/en/index.html`。

## 可选集成与部署

Google Analytics 和 Scholar 引用数展示在配置对应 ID 和数据源前保持关闭。`google_scholar_crawler/` 是独立工具，目前没有连接主页的自动更新 workflow。推送到 `master` 会触发 GitHub Pages 部署。
