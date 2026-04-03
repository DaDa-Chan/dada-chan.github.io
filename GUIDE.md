# 个人主页使用与定制指南

本文档详细说明如何修改和定制你的个人网站。网站基于 Jekyll 构建，托管在 GitHub Pages 上。

---

## 目录

- [1. 项目结构概览](#1-项目结构概览)
- [2. 基本信息配置](#2-基本信息配置)
- [3. 各板块内容管理](#3-各板块内容管理)
  - [3.1 主页（Home）](#31-主页home)
  - [3.2 Blog](#32-blog)
  - [3.3 Plog（照片日志）](#33-plog照片日志)
  - [3.4 Course（课程笔记）](#34-course课程笔记)
  - [3.5 Publications（出版物）](#35-publications出版物)
  - [3.6 Projects（项目）](#36-projects项目)
  - [3.7 CV（简历）](#37-cv简历)
- [4. 添加新的章节](#4-添加新的章节)
- [5. 外观定制](#5-外观定制)
  - [5.1 切换主题配色](#51-切换主题配色)
  - [5.2 自定义颜色](#52-自定义颜色)
  - [5.3 修改字体](#53-修改字体)
  - [5.4 修改字号](#54-修改字号)
  - [5.5 自定义侧边栏](#55-自定义侧边栏)
  - [5.6 自定义页头和页脚](#56-自定义页头和页脚)
  - [5.7 添加自定义 CSS](#57-添加自定义-css)
  - [5.8 修改网站图标（Favicon）](#58-修改网站图标favicon)
- [6. Markdown 写作参考](#6-markdown-写作参考)
- [7. 本地预览](#7-本地预览)
- [8. 发布](#8-发布)

---

## 1. 项目结构概览

```
.
├── _config.yml              # 全站配置（最重要的文件）
├── _data/
│   └── navigation.yml       # 导航栏菜单配置
├── _pages/                  # 各板块的页面文件
│   ├── about.md             # 主页
│   ├── blog.html            # Blog 列表页
│   ├── plog.html            # Plog 列表页
│   ├── courses.html         # Course 列表页
│   ├── publications.html    # Publications 列表页
│   ├── projects.html        # Projects 列表页
│   ├── cv.md                # CV 页面
│   ├── category-archive.html# Blog 分类归档页
│   └── tag-archive.html     # Blog 标签归档页
├── _posts/                  # Blog 文章
├── _plog/                   # Plog 照片日志
├── _courses/                # Course 笔记
├── _publications/           # 出版物/论文
├── _projects/               # 项目
├── _layouts/                # 页面布局模板
├── _includes/               # 可复用 HTML 组件
├── _sass/                   # 样式文件（SCSS）
├── assets/                  # 静态资源（CSS/JS/字体）
├── images/                  # 图片（头像、文章配图等）
└── files/                   # 可下载文件（PDF 等）
```

---

## 2. 基本信息配置

编辑 `_config.yml`，修改以下部分：

### 站点信息

```yaml
title                    : "Hanzheng's Homepage"   # 网站标题，显示在浏览器标签和页头
name                     : &name "Hanzheng"        # 你的名字
description              : &description "Hanzheng's personal website"  # 网站描述（SEO 用）
url                      : https://DaDa-Chan.github.io  # 你的网站地址
repository               : "DaDa-Chan/dada-chan.github.io"  # GitHub 仓库名
```

### 个人信息（侧边栏）

```yaml
author:
  avatar           : "profile.png"          # 头像文件名，放在 /images/ 目录下
  name             : "Hanzheng"             # 侧边栏显示的名字
  bio              : "A short bio about me" # 一句话简介
  location         : "Beijing, China"       # 所在地
  employer         : "Your University"      # 所在单位
  email            : "your@email.com"       # 邮箱

  # 学术链接（不需要的留空即可）
  googlescholar    : "https://scholar.google.com/citations?user=XXXXX"
  orcid            : "https://orcid.org/0000-0000-0000-0000"

  # 社交链接（不需要的留空即可）
  github           : "your-github-username"
  linkedin         : "your-linkedin-username"
  twitter          : "your-twitter-handle"
```

**头像设置**：将你的头像图片命名为 `profile.png`（或其他名字，对应修改 `avatar` 字段），放到 `/images/` 目录下。

> **注意**：修改 `_config.yml` 后，如果你在本地预览，需要重启 Jekyll 服务才能生效。

---

## 3. 各板块内容管理

### 3.1 主页（Home）

**文件**：`_pages/about.md`

直接编辑这个文件的 Markdown 内容即可。front matter（文件开头 `---` 之间的部分）保持不变：

```yaml
---
permalink: /
title: "Welcome"
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

在这里写你的主页内容...
```

---

### 3.2 Blog

**目录**：`_posts/`

#### 添加新文章

在 `_posts/` 目录下创建一个新的 `.md` 文件。

**文件名格式**（必须严格遵守）：

```
YYYY-MM-DD-文章标题.md
```

例如：`2024-06-15-my-first-post.md`

**文件内容模板**：

```yaml
---
title: '文章标题'
date: 2024-06-15
permalink: /posts/2024/06/my-first-post/
categories:
  - Tutorial        # 分类（可多个）
tags:
  - Python           # 标签（可多个）
  - Machine Learning
excerpt: '文章摘要，会显示在列表页'
---

正文内容写在这里，使用 Markdown 格式...
```

#### Front matter 字段说明

| 字段 | 必填 | 说明 |
|------|------|------|
| `title` | 是 | 文章标题 |
| `date` | 是 | 发布日期，格式 `YYYY-MM-DD` |
| `permalink` | 否 | 自定义 URL 路径 |
| `categories` | 否 | 分类，列表格式，可写多个 |
| `tags` | 否 | 标签，列表格式，可写多个 |
| `excerpt` | 否 | 文章摘要，列表页显示。不写则自动截取正文开头 |
| `header.teaser` | 否 | 缩略图文件名（放在 `/images/` 下） |

#### 分类浏览

Blog 列表页顶部有 "Browse by category" 和 "Browse by tag" 链接，分别对应 `/categories/` 和 `/tags/` 页面。只要你在文章中写了 `categories` 或 `tags`，它们就会自动出现在归档页中。

---

### 3.3 Plog（照片日志）

**目录**：`_plog/`

#### 添加新照片日志

在 `_plog/` 目录下创建一个新的 `.md` 文件。

**文件名格式**：

```
YYYY-MM-DD-标题.md
```

例如：`2024-05-01-tokyo-trip.md`

**文件内容模板**：

```yaml
---
title: "东京之旅"
date: 2024-05-01
excerpt: "2024 年春天的东京之行"
header:
  teaser: "tokyo-cover.jpg"    # 可选，缩略图
---

## Day 1 - 浅草寺

简短的文字描述...

![浅草寺](/images/plog/tokyo-asakusa.jpg)

## Day 2 - 秋叶原

更多照片和文字...

![秋叶原](/images/plog/tokyo-akihabara.jpg)
![东京塔](/images/plog/tokyo-tower.jpg)
```

#### 图片管理建议

- 在 `/images/` 下创建子目录来组织图片，例如 `/images/plog/`
- 图片在 Markdown 中的引用语法：`![描述文字](/images/plog/文件名.jpg)`
- 建议压缩图片（宽度 1200px 以内），避免页面加载过慢
- 如果想并排显示多张图片，可以使用 HTML：

```html
<div style="display: flex; gap: 10px; flex-wrap: wrap;">
  <img src="/images/plog/photo1.jpg" style="width: 48%;" alt="照片1">
  <img src="/images/plog/photo2.jpg" style="width: 48%;" alt="照片2">
</div>
```

---

### 3.4 Course（课程笔记）

**目录**：`_courses/`

Course 页面会**按 `category` 字段自动分类显示**。

#### 添加新笔记

在 `_courses/` 目录下创建 `.md` 文件。

**文件名格式**：

```
YYYY-MM-DD-标题.md
```

例如：`2024-03-01-linear-algebra-ch1.md`

**文件内容模板**：

```yaml
---
title: "线性代数 - 第一章 向量空间"
date: 2024-03-01
category: "Mathematics"        # 分类名，同类笔记会归在一起
excerpt: "向量空间的基本概念和性质"
---

## 1.1 向量空间的定义

正文内容...

## 1.2 子空间

更多内容...
```

#### 分类规则

- `category` 字段值相同的笔记会归为一组
- 分类名区分大小写，确保同类笔记使用一致的名称
- 示例分类：`Mathematics`、`Programming`、`Machine Learning`、`Physics`

#### 支持数学公式

本站支持 MathJax，可以在笔记中使用 LaTeX 数学公式：

```markdown
行内公式：$E = mc^2$

独立公式：
$$
\int_{-\infty}^{\infty} e^{-x^2} dx = \sqrt{\pi}
$$
```

---

### 3.5 Publications（出版物）

**目录**：`_publications/`

#### 添加新论文

在 `_publications/` 目录下创建 `.md` 文件。

**文件名格式**：

```
YYYY-MM-DD-简短标题.md
```

例如：`2024-06-01-graph-neural-network.md`

**文件内容模板**：

```yaml
---
title: "Your Paper Title"
collection: publications
category: manuscripts         # 可选：manuscripts（期刊）、conferences（会议）、books（书籍）
permalink: /publication/2024-graph-neural-network
excerpt: 'A brief description of the paper.'
date: 2024-06-01
venue: 'Nature Machine Intelligence'
paperurl: 'https://link-to-paper.pdf'
slidesurl: 'https://link-to-slides.pdf'   # 可选
bibtexurl: 'https://link-to-bibtex.bib'   # 可选
citation: 'Author1, Author2. (2024). &quot;Paper Title.&quot; <i>Journal Name</i>.'
---

论文的详细描述或补充说明...
```

#### 分类设置

论文分类由 `_config.yml` 中的 `publication_category` 控制：

```yaml
publication_category:
  books:
    title: 'Books'
  manuscripts:
    title: 'Journal Articles'
  conferences:
    title: 'Conference Papers'
```

你可以按需增删分类。

---

### 3.6 Projects（项目）

**目录**：`_projects/`

#### 添加新项目

在 `_projects/` 目录下创建 `.md` 文件。

**文件名不要求日期前缀**，但建议有一定命名规范，例如：`project-name.md`

**文件内容模板**：

```yaml
---
title: "项目名称"
excerpt: "项目简介<br/><img src='/images/project-screenshot.png'>"
collection: projects
date: 2024-01-01
---

## 概述

项目的详细介绍...

## 技术栈

- Python
- PyTorch
- ...

## 链接

- [GitHub](https://github.com/your-repo)
- [在线演示](https://demo-url)
```

`excerpt` 中可以嵌入 HTML（如图片），这段内容会显示在项目列表页。

---

### 3.7 CV（简历）

**文件**：`_pages/cv.md`

CV 页面直接用 Markdown 编写，你可以自由组织内容结构。示例：

```markdown
Education
======
* Ph.D in Computer Science, XX University, 2025 (expected)
* B.S. in Mathematics, XX University, 2020

Skills
======
* Programming: Python, C++, JavaScript
* Frameworks: PyTorch, TensorFlow
* Languages: Chinese (native), English (fluent)
```

如果你有 PDF 版本的简历，可以放到 `/files/` 目录下，然后在 CV 页面添加下载链接：

```markdown
[Download my CV (PDF)](/files/cv.pdf)
```

---

## 4. 添加新的章节

如果你想添加一个全新的板块（比如 "Reading"），需要三步：

### 第一步：在 `_config.yml` 中注册 collection

在 `collections:` 下添加：

```yaml
collections:
  # ... 已有的 collections ...
  reading:
    output: true
    permalink: /:collection/:path/
```

在 `defaults:` 下添加默认配置：

```yaml
defaults:
  # ... 已有的 defaults ...
  # _reading
  - scope:
      path: ""
      type: reading
    values:
      layout: single
      author_profile: true
      share: true
```

### 第二步：创建目录和列表页

1. 在项目根目录创建 `_reading/` 文件夹

2. 在 `_pages/` 下创建列表页 `reading.html`：

```html
---
layout: archive
permalink: /reading/
title: "Reading"
author_profile: true
---

{% include base_path %}

{% for post in site.reading reversed %}
  {% include archive-single.html %}
{% endfor %}
```

如果需要**按分类显示**，参考 `courses.html` 的写法：

```html
{% include group-by-array collection=site.reading field="category" %}

{% for category in group_names %}
  {% assign posts = group_items[forloop.index0] %}
  <h2 id="{{ category | slugify }}" class="archive__subtitle">{{ category }}</h2>
  {% for post in posts %}
    {% include archive-single.html %}
  {% endfor %}
{% endfor %}
```

### 第三步：添加导航入口

编辑 `_data/navigation.yml`，在你希望的位置添加：

```yaml
main:
  # ... 已有的菜单项 ...
  - title: "Reading"
    url: /reading/
```

### 第四步：添加内容

在 `_reading/` 目录下按正常格式添加 `.md` 文件即可。

---

## 5. 外观定制

### 5.1 切换主题配色

编辑 `_config.yml`，修改 `site_theme` 字段：

```yaml
site_theme : "default"   # 可选值：default, air, sunrise, mint, dirt, contrast
```

各主题的风格：

| 主题 | 风格 | 主色调 |
|------|------|--------|
| `default` | 简洁专业 | 青蓝色 #2f7f93 |
| `air` | 清新明亮 | 天蓝色 #0092ca |
| `mint` | 清爽自然 | 薄荷绿 #11999e |
| `sunrise` | 温暖活力 | 珊瑚红 #fc3a52 |
| `dirt` | 沉稳大气 | 大地棕色 |
| `contrast` | 高对比度 | 红蓝双色（适合无障碍访问） |

每个主题都自带**亮色/暗色模式**，用户可以通过页头的太阳图标切换。

### 5.2 自定义颜色

如果预设主题都不满意，你可以自定义颜色。

**方法一：修改主题文件**

编辑 `_sass/theme/_default_light.scss`（以 default 主题为例）：

```scss
/* 修改主色调 */
$primary-color              : #2f7f93;    // 改成你想要的颜色

:root {
    --global-base-color                 : #{$primary-color};     // 主色调（按钮、强调色）
    --global-bg-color                   : #fff;                  // 背景色
    --global-text-color                 : #{$dark-gray};         // 正文文字颜色
    --global-link-color                 : #52adc8;               // 链接颜色
    --global-link-color-hover           : mix(#000, #2f7f93, 25%);  // 链接悬停颜色
    --global-masthead-link-color        : #{$dark-gray};         // 导航栏文字颜色
    --global-footer-bg-color            : #f2f3f3;               // 页脚背景色
    --global-code-background-color      : #fafafa;               // 代码块背景色
    --global-code-text-color            : #{$darker-gray};       // 代码文字颜色
}
```

暗色模式对应文件：`_sass/theme/_default_dark.scss`

**方法二：通过自定义 CSS 覆盖（推荐新手使用）**

在 `_includes/head/custom.html` 中添加 `<style>` 标签：

```html
<style>
  :root {
    --global-base-color: #e74c3c;        /* 主色调改为红色 */
    --global-link-color: #e74c3c;        /* 链接颜色 */
  }
</style>
```

#### 所有可用的颜色变量

| 变量名 | 作用 |
|--------|------|
| `--global-base-color` | 主色调（按钮、强调元素） |
| `--global-bg-color` | 页面背景色 |
| `--global-text-color` | 正文文字颜色 |
| `--global-text-color-light` | 次要文字颜色（较浅） |
| `--global-link-color` | 链接颜色 |
| `--global-link-color-hover` | 链接悬停颜色 |
| `--global-link-color-visited` | 已访问链接颜色 |
| `--global-masthead-link-color` | 导航栏链接颜色 |
| `--global-masthead-link-color-hover` | 导航栏链接悬停颜色 |
| `--global-border-color` | 边框颜色 |
| `--global-footer-bg-color` | 页脚背景色 |
| `--global-code-background-color` | 代码块背景色 |
| `--global-code-text-color` | 代码文字颜色 |
| `--global-thead-color` | 表头背景色 |

### 5.3 修改字体

编辑 `_sass/_themes.scss`：

```scss
/* 正文字体 */
$sans-serif : -apple-system, "Helvetica Neue", Arial, sans-serif;

/* 全局字体设置 */
$global-font-family  : $sans-serif;   // 正文字体
$header-font-family  : $sans-serif;   // 标题字体
$caption-font-family : $serif;        // 图注字体
```

如果想用 Google Fonts（如 Noto Sans SC），在 `_includes/head/custom.html` 中添加：

```html
<link href="https://fonts.googleapis.com/css2?family=Noto+Sans+SC:wght@400;700&display=swap" rel="stylesheet">
<style>
  body {
    font-family: 'Noto Sans SC', -apple-system, sans-serif;
  }
</style>
```

### 5.4 修改字号

编辑 `_sass/_themes.scss`：

```scss
$doc-font-size : 16;      // 基础字号（像素值，不带 px）

/* 各级标题的相对大小 */
$type-size-1   : 2.441em;  // h1 ~39px
$type-size-2   : 1.953em;  // h2 ~31px
$type-size-3   : 1.563em;  // h3 ~25px
$type-size-4   : 1.25em;   // h4 ~20px
$type-size-5   : 1em;      // 正文 ~16px
$type-size-6   : 0.75em;   // 小字 ~12px
```

### 5.5 自定义侧边栏

侧边栏模板位于 `_includes/author-profile.html`，它会根据 `_config.yml` 中 `author:` 的配置自动显示内容。

- **隐藏侧边栏**：在任何页面的 front matter 中设置 `author_profile: false`
- **添加新的社交链接**：编辑 `_includes/author-profile.html`，参考已有链接的格式添加

### 5.6 自定义页头和页脚

- **页头导航**：通过 `_data/navigation.yml` 控制菜单项
- **页脚内容**：编辑 `_includes/footer.html`
- **页头额外内容**：编辑 `_includes/head/custom.html`（添加自定义 CSS、JS、meta 标签等）

### 5.7 添加自定义 CSS

推荐在 `_includes/head/custom.html` 文件末尾（`<!-- end custom head snippets -->` 之前）添加 `<style>` 标签：

```html
<style>
  /* 你的自定义样式 */
  .page__content {
    font-size: 1.05em;   /* 正文稍大一点 */
    line-height: 1.8;    /* 增加行高 */
  }

  .archive__item-title {
    font-size: 1.1em;    /* 列表标题大小 */
  }
</style>
```

### 5.8 修改网站图标（Favicon）

将你的图标文件放到 `/images/` 目录下，替换以下文件：

- `favicon.ico` — 标准图标
- `favicon.svg` — SVG 图标
- `favicon-32x32.png` — 32x32 PNG
- `favicon-192x192.png` — 192x192 PNG（Android）
- `apple-touch-icon-180x180.png` — 180x180 PNG（iOS）

推荐使用 [realfavicongenerator.net](https://realfavicongenerator.net) 一键生成所有尺寸。

---

## 6. Markdown 写作参考

所有内容文件都使用 Markdown 格式，以下是常用语法：

### 基本格式

```markdown
**粗体** *斜体* ~~删除线~~

- 无序列表项 1
- 无序列表项 2

1. 有序列表项 1
2. 有序列表项 2

[链接文字](https://example.com)

> 引用文字
```

### 图片

```markdown
![图片描述](/images/your-image.jpg)
```

### 代码

````markdown
行内代码：`print("hello")`

代码块：
```python
def hello():
    print("Hello, World!")
```
````

### 标题层级

```markdown
# 一级标题（一般不在正文中使用，页面标题已经是 h1）
## 二级标题
### 三级标题
#### 四级标题
```

### 表格

```markdown
| 列1 | 列2 | 列3 |
|-----|-----|-----|
| 内容 | 内容 | 内容 |
```

### 数学公式（MathJax）

```markdown
行内公式：$E = mc^2$

独立公式：
$$\sum_{i=1}^{n} x_i = x_1 + x_2 + \cdots + x_n$$
```

### 嵌入 HTML

Markdown 文件中可以直接写 HTML：

```html
<div style="text-align: center;">
  <img src="/images/photo.jpg" style="width: 60%;" alt="居中图片">
  <p><em>图片说明</em></p>
</div>
```

---

## 7. 本地预览

### 方式一：Docker（推荐）

```bash
docker-compose up
```

然后访问 `http://localhost:4000`。

### 方式二：本地安装 Jekyll

```bash
# 安装依赖（需要先安装 Ruby）
bundle install

# 启动本地服务
bundle exec jekyll serve -l -H localhost
```

然后访问 `http://localhost:4000`。

> 修改 `_config.yml` 后需要重启服务。修改其他文件会自动刷新。

---

## 8. 发布

将改动推送到 GitHub 即可自动部署：

```bash
git add .
git commit -m "Update site content"
git push origin master
```

GitHub Actions 会自动构建并发布到 `https://DaDa-Chan.github.io`。

部署通常在 1-2 分钟内完成，可以在仓库的 Actions 页面查看构建状态。
