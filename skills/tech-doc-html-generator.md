# Tech Doc HTML Generator Skill

## 描述

这是一个用于生成技术文档类 HTML 页面的 AI 技能。基于《技术文档 HTML 页面设计规范》，能够自动生成符合规范的、美观的技术文档页面。

---

## 技能元数据

```yaml
name: tech-doc-html-generator
version: 1.0.0
description: 生成符合规范的技术文档 HTML 页面
author: CMP Team
tags:
  - html
  - documentation
  - frontend
  - technical-writing
```

---

## 触发条件

当用户请求以下内容时，应该使用此技能：

1. "生成技术文档页面"
2. "创建开发指南 HTML"
3. "制作 API 文档页面"
4. "构建技术手册网页"
5. 提到 "tech-doc" 或 "文档页面" 相关需求

---

## 核心能力

### 1. 页面结构生成

能够生成符合三栏式布局的完整 HTML 结构：

- Header（Logo + 导航 + 搜索）
- Sidebar（可折叠导航目录）
- Main Content（文档主体）

### 2. 组件生成

| 组件 | 用途 |
|------|------|
| `.section-header` | 章节标题 |
| `.subsection-title` | 重要子标题 |
| `.subsection-subtitle` | 次级子标题 |
| `.code-section` | 代码块 |
| `.info-box` | 信息提示框 |
| `.warning-box` | 警告提示框 |
| `.data-table` | 数据表格 |
| `.quick-card` | 快速入口卡片 |
| `.steps` | 步骤说明 |

### 3. 交互功能

- 搜索功能（支持 `⌘K` 快捷键）
- 导航高亮（滚动自动高亮）
- 平滑滚动
- 导航折叠/展开

---

## 使用指南

### 输入要求

用户提供以下信息：

1. **文档标题**：页面主标题
2. **文档内容**：章节结构和内容
3. **导航结构**：侧边栏导航层级
4. **搜索数据**：可搜索的条目列表（可选）

### 输出格式

完整的 HTML 文件，包含：

- 内联 CSS 样式（基于规范）
- 内联 JavaScript（交互功能）
- 响应式设计支持

---

## 生成模板

### 基础结构模板

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{DOCUMENT_TITLE}}</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+SC:wght@400;500;600;700&family=Noto+Serif+SC:wght@600;700&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
    <style>
        /* CSS 变量 */
        :root {
            --accent-coral: #E07A5F;
            --accent-warm: #D4A574;
            --bg-primary: #FAF9F7;
            --bg-secondary: #F5F3F0;
            --bg-card: #FFFFFF;
            --text-primary: #1A1A2E;
            --text-secondary: #4A4A5A;
            --text-muted: #8A8A9A;
            --border-light: #E8E6E3;
            --border-medium: #D1CFCC;
            --gradient-warm: linear-gradient(135deg, #E07A5F 0%, #D4A574 100%);
        }
        
        /* 基础样式 */
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { font-family: -apple-system, 'Noto Sans SC', sans-serif; background: var(--bg-primary); color: var(--text-primary); }
        
        /* ... 更多样式 ... */
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="header-content">
            <div class="logo">
                <div class="logo-icon">{{LOGO_ICON}}</div>
                <div class="logo-text">{{LOGO_TEXT}}</div>
            </div>
            <nav>{{NAV_LINKS}}</nav>
            <div class="header-search">
                <span class="search-icon">🔍</span>
                <input type="text" id="searchInput" placeholder="搜索文档...">
                <span class="search-shortcut">⌘K</span>
                <div class="search-results" id="searchResults"></div>
            </div>
        </div>
    </header>
    
    <!-- Sidebar -->
    <aside class="sidebar">
        <nav class="sidebar-nav">
            {{SIDEBAR_NAV}}
        </nav>
    </aside>
    
    <!-- Main Content -->
    <main>
        {{MAIN_CONTENT}}
    </main>
    
    <!-- JavaScript -->
    <script>
        {{JAVASCRIPT_CODE}}
    </script>
</body>
</html>
```

### 章节内容模板

```html
<section id="{{SECTION_ID}}">
    <div class="section-header">
        <div class="section-number">{{SECTION_NUMBER}}</div>
        <h2 class="section-title">{{SECTION_TITLE}}</h2>
        <p class="section-desc">{{SECTION_DESC}}</p>
    </div>
    
    {{SECTION_CONTENT}}
</section>
```

### 代码块模板

```html
<div class="code-section">
    <div class="code-header">
        <span class="code-title">{{CODE_TITLE}}</span>
        <span class="code-lang">{{CODE_LANG}}</span>
    </div>
    <div class="code-content">
<pre><span class="comment">// {{COMMENT}}</span>
{{CODE_CONTENT}}</pre>
    </div>
</div>
```

### 信息框模板

```html
<div class="info-box">
    <div class="info-box-icon">{{ICON}}</div>
    <div class="info-box-content">
        <div class="info-box-title">{{TITLE}}</div>
        <p>{{CONTENT}}</p>
    </div>
</div>
```

---

## 代码生成规则

### CSS 变量使用

始终使用 CSS 变量而非硬编码颜色：

```css
/* 正确 */
color: var(--accent-coral);
background: var(--bg-secondary);

/* 错误 */
color: #E07A5F;
background: #F5F3F0;
```

### 语义化标签

```html
<!-- 正确 -->
<section id="architecture">
    <h2 class="section-title">技术架构</h2>
    <p class="section-desc">系统架构说明</p>
</section>

<!-- 错误 -->
<div id="architecture">
    <div class="title">技术架构</div>
    <div class="desc">系统架构说明</div>
</div>
```

### 响应式设计

始终包含响应式媒体查询：

```css
@media (max-width: 1200px) {
    .sidebar { display: none; }
    main { margin-left: 0; }
}

@media (max-width: 768px) {
    header nav { display: none; }
}
```

---

## 示例对话

### 用户输入

```
请生成一个 API 文档页面，包含以下内容：
1. 快速入门
2. 认证方式
3. API 列表
4. 错误码
5. 最佳实践
```

### 技能响应

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <!-- 生成的完整 HTML -->
</head>
<body>
    <header>
        <!-- Logo: API -->
        <!-- 导航: 快速入门 | 认证 | API | 错误码 | 最佳实践 -->
        <!-- 搜索框 -->
    </header>
    
    <aside class="sidebar">
        <!-- 可折叠导航 -->
    </aside>
    
    <main>
        <section id="quickstart">
            <!-- 快速入门内容 -->
        </section>
        <!-- 更多章节 -->
    </main>
</body>
</html>
```

---

## 质量检查清单

生成页面后，确保满足以下条件：

- [ ] 使用了所有定义的 CSS 变量
- [ ] Header 高度为 56px
- [ ] Sidebar 宽度为 260px
- [ ] 搜索功能支持 ⌘K 快捷键
- [ ] 导航支持滚动高亮
- [ ] 所有代码块使用 `.code-section`
- [ ] 信息/警告使用 `.info-box` / `.warning-box`
- [ ] 表格使用 `.data-table`
- [ ] 包含响应式媒体查询
- [ ] 使用语义化 HTML 标签

---

## 扩展能力

### 自定义主题

可以通过修改 CSS 变量实现主题切换：

```css
/* 深色主题 */
:root.dark {
    --bg-primary: #1A1A2E;
    --bg-secondary: #252540;
    --bg-card: #2D2D4A;
    --text-primary: #FFFFFF;
    --text-secondary: #B0B0C0;
    --text-muted: #808090;
}
```

### 多语言支持

```html
<html lang="zh-CN">
<!-- 或 -->
<html lang="en-US">
```

### 打印样式

```css
@media print {
    .sidebar, header, .header-search {
        display: none;
    }
    main {
        margin-left: 0;
    }
}
```

---

## 依赖

- Google Fonts（可选）
    - Noto Sans SC
    - Noto Serif SC
    - JetBrains Mono

无其他外部依赖，纯 HTML/CSS/JS 实现。

---

## 版本历史

| 版本 | 日期 | 变更 |
|------|------|------|
| 1.0.0 | 2026-03-03 | 初始版本 |
