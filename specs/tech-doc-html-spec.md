# 技术文档 HTML 页面设计规范

## 概述

本规范定义了技术文档类 HTML 页面的设计标准，参考 Mintlify 风格，适用于开发指南、API 文档、技术手册等场景。

---

## 1. 整体布局

### 1.1 三栏式布局结构

```
┌──────────────────────────────────────────────────────────────────┐
│                        Header (fixed)                             │
│  Logo + 横向导航 + 搜索框                                         │
├──────────────┬───────────────────────────────────────────────────┤
│              │                                                   │
│   Sidebar    │                 Main Content                      │
│   (260px)    │               (margin-left: 260px)                │
│              │                                                   │
│   导航目录    │               文档主体内容                          │
│              │                                                   │
└──────────────┴───────────────────────────────────────────────────┘
```

### 1.2 尺寸规范

| 组件 | 尺寸 | 说明 |
|------|------|------|
| Header 高度 | 56px | 固定高度 |
| Sidebar 宽度 | 260px | 固定宽度 |
| Main padding-top | 4.5rem | 避免被 header 遮挡 |
| 内容最大宽度 | 无限制 | 自适应屏幕 |

---

## 2. 颜色系统

### 2.1 CSS 变量定义

```css
:root {
    /* 主色调 - 温暖橙色系 */
    --accent-coral: #E07A5F;      /* 主强调色 */
    --accent-warm: #D4A574;       /* 次强调色 */
    
    /* 背景色 */
    --bg-primary: #FAF9F7;        /* 页面背景 */
    --bg-secondary: #F5F3F0;      /* 次级背景 */
    --bg-card: #FFFFFF;           /* 卡片背景 */
    
    /* 文字颜色 */
    --text-primary: #1A1A2E;      /* 主文字 */
    --text-secondary: #4A4A5A;    /* 次级文字 */
    --text-muted: #8A8A9A;        /* 弱化文字 */
    
    /* 边框 */
    --border-light: #E8E6E3;      /* 浅边框 */
    --border-medium: #D1CFCC;     /* 中等边框 */
    
    /* 渐变 */
    --gradient-warm: linear-gradient(135deg, #E07A5F 0%, #D4A574 100%);
    --gradient-soft: linear-gradient(135deg, rgba(224, 122, 95, 0.1) 0%, rgba(212, 165, 116, 0.1) 100%);
}
```

### 2.2 颜色使用规则

| 场景 | 颜色 | 用途 |
|------|------|------|
| 主标题 | --text-primary | 章节标题、重要文字 |
| 次标题 | --text-secondary | 子标题、导航文字 |
| 辅助文字 | --text-muted | 说明文字、时间戳 |
| 强调/高亮 | --accent-coral | 当前选中、重要标记 |
| 链接 hover | --accent-warm | 鼠标悬停状态 |

---

## 3. Header 设计

### 3.1 结构

```html
<header>
    <div class="header-content">
        <div class="logo">
            <div class="logo-icon">C</div>
            <div class="logo-text">CMP <span>开发指北</span></div>
        </div>
        <nav>
            <a href="#section1">导航1</a>
            <a href="#section2">导航2</a>
        </nav>
        <div class="header-search">
            <span class="search-icon">🔍</span>
            <input type="text" placeholder="搜索文档...">
            <span class="search-shortcut">⌘K</span>
        </div>
    </div>
</header>
```

### 3.2 样式规范

```css
header {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    height: 56px;
    padding: 0.75rem 1.5rem;
    background: rgba(250, 249, 247, 0.95);
    backdrop-filter: blur(16px);
    border-bottom: 1px solid var(--border-light);
    z-index: 1000;
    display: flex;
    align-items: center;
}

.logo-icon {
    width: 32px;
    height: 32px;
    background: var(--gradient-warm);
    border-radius: 8px;
    font-size: 0.95rem;
    font-weight: 700;
    color: white;
}

header nav a {
    padding: 0.35rem 0.65rem;
    font-size: 0.8rem;
    font-weight: 500;
    border-radius: 4px;
    color: var(--text-secondary);
}

header nav a.active {
    background: rgba(224, 122, 95, 0.1);
    color: var(--accent-coral);
}
```

---

## 4. Sidebar 设计

### 4.1 结构

```html
<aside class="sidebar">
    <nav class="sidebar-nav">
        <div class="nav-section expanded">
            <a href="#section" class="nav-section-title">
                <span class="nav-section-icon">▶</span>
                章节名称
            </a>
            <div class="nav-subsection">
                <a href="#subsection">子章节</a>
            </div>
        </div>
    </nav>
</aside>
```

### 4.2 样式规范

```css
.sidebar {
    position: fixed;
    left: 0;
    top: 56px;
    width: 260px;
    height: calc(100vh - 56px);
    background: var(--bg-card);
    border-right: 1px solid var(--border-light);
    overflow-y: auto;
}

.nav-section-title {
    padding: 0.5rem 1.25rem;
    font-size: 0.82rem;
    font-weight: 500;
    color: var(--text-secondary);
}

.nav-section-title:hover {
    background: rgba(0, 0, 0, 0.03);
    color: var(--text-primary);
}

.nav-section-title.active {
    background: linear-gradient(90deg, rgba(224, 122, 95, 0.08) 0%, transparent 100%);
    color: var(--accent-coral);
}

.nav-subsection a {
    padding: 0.4rem 1.25rem 0.4rem 2rem;
    font-size: 0.78rem;
    color: var(--text-muted);
}

.nav-subsection a::before {
    content: '';
    width: 4px;
    height: 4px;
    background: var(--border-medium);
    border-radius: 50%;
}
```

---

## 5. 搜索功能

### 5.1 搜索框样式

```css
.header-search {
    width: 280px;
    position: relative;
}

.search-input {
    width: 100%;
    padding: 0.5rem 0.75rem 0.5rem 2rem;
    background: var(--bg-secondary);
    border: 1px solid transparent;
    border-radius: 6px;
    font-size: 0.8rem;
}

.search-input:focus {
    border-color: var(--accent-warm);
    background: var(--bg-card);
    box-shadow: 0 0 0 2px rgba(212, 165, 116, 0.1);
}

.search-shortcut {
    position: absolute;
    right: 0.5rem;
    top: 50%;
    transform: translateY(-50%);
    padding: 0.1rem 0.35rem;
    background: var(--bg-card);
    border: 1px solid var(--border-light);
    border-radius: 3px;
    font-size: 0.65rem;
    color: var(--text-muted);
}
```

### 5.2 搜索结果下拉

```css
.search-results {
    position: fixed;
    top: 56px;
    left: 50%;
    transform: translateX(-50%);
    width: 480px;
    max-width: 90vw;
    background: var(--bg-card);
    border: 1px solid var(--border-light);
    border-radius: 8px;
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.15);
    max-height: 400px;
    overflow-y: auto;
}

.search-result-title mark {
    background: rgba(224, 122, 95, 0.25);
    color: var(--accent-coral);
}
```

### 5.3 快捷键

- `⌘K` / `Ctrl+K`: 聚焦搜索框
- `↑` `↓`: 选择搜索结果
- `Enter`: 跳转
- `Esc`: 关闭搜索

---

## 6. 排版规范

### 6.1 字体

```css
body {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Noto Sans SC', sans-serif;
    font-size: 16px;
    line-height: 1.6;
    color: var(--text-primary);
}

/* 代码字体 */
code, pre {
    font-family: 'JetBrains Mono', 'Fira Code', monospace;
}
```

### 6.2 标题层级

| 标题 | 字号 | 字重 | 间距 |
|------|------|------|------|
| H1 (hero) | 3.5rem | 700 | margin-bottom: 1rem |
| H2 (section) | 1.75rem | 600 | margin: 2.5rem 0 1rem |
| H3 (subsection) | 1.1rem | 600 | margin: 2.5rem 0 1rem |
| H4 (sub-subsection) | 1rem | 500 | margin: 1.5rem 0 0.75rem |

### 6.3 子标题样式

```css
/* 重要子标题 */
.subsection-title {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    font-size: 1.1rem;
    font-weight: 600;
    margin: 2.5rem 0 1rem;
    padding: 0.75rem 1rem;
    color: var(--text-primary);
    background: linear-gradient(90deg, rgba(224, 122, 95, 0.08) 0%, rgba(212, 165, 116, 0.04) 50%, transparent 100%);
    border-left: 3px solid var(--accent-coral);
    border-radius: 0 8px 8px 0;
}

/* 次级子标题 */
.subsection-subtitle {
    font-size: 1rem;
    font-weight: 500;
    margin: 1.5rem 0 0.75rem;
    color: var(--text-secondary);
    padding-bottom: 0.5rem;
    border-bottom: 1px dashed var(--border-light);
}
```

---

## 7. 代码块设计

### 7.1 结构

```html
<div class="code-section">
    <div class="code-header">
        <span class="code-title">标题</span>
        <span class="code-lang">Java</span>
    </div>
    <div class="code-content">
        <pre><code>...</code></pre>
    </div>
</div>
```

### 7.2 样式规范

```css
.code-section {
    background: var(--bg-secondary);
    border: 1px solid var(--border-light);
    border-radius: 12px;
    overflow: hidden;
}

.code-header {
    display: flex;
    justify-content: space-between;
    padding: 0.75rem 1rem;
    background: rgba(0, 0, 0, 0.02);
    border-bottom: 1px solid var(--border-light);
}

.code-title {
    font-size: 0.85rem;
    font-weight: 500;
    color: var(--text-primary);
}

.code-lang {
    font-size: 0.75rem;
    color: var(--text-muted);
    text-transform: uppercase;
}

.code-content {
    padding: 1rem;
    overflow-x: auto;
}

.code-content pre {
    font-size: 0.85rem;
    line-height: 1.6;
}
```

---

## 8. 组件样式

### 8.1 信息框

```css
.info-box, .warning-box {
    display: flex;
    gap: 1rem;
    padding: 1rem 1.25rem;
    border-radius: 12px;
    margin: 1.5rem 0;
}

.info-box {
    background: linear-gradient(135deg, rgba(224, 122, 95, 0.05) 0%, rgba(212, 165, 116, 0.05) 100%);
    border: 1px solid rgba(224, 122, 95, 0.15);
}

.warning-box {
    background: rgba(212, 165, 116, 0.08);
    border: 1px solid rgba(212, 165, 116, 0.2);
}

.info-box-icon, .warning-box-icon {
    font-size: 1.25rem;
    flex-shrink: 0;
}

.info-box-title, .warning-box-title {
    font-weight: 600;
    font-size: 0.95rem;
    margin-bottom: 0.25rem;
    color: var(--text-primary);
}
```

### 8.2 数据表格

```css
.data-table {
    width: 100%;
    border-collapse: collapse;
    margin: 1rem 0;
    font-size: 0.9rem;
}

.data-table th {
    background: var(--bg-secondary);
    padding: 0.75rem 1rem;
    text-align: left;
    font-weight: 600;
    font-size: 0.8rem;
    text-transform: uppercase;
    letter-spacing: 0.05em;
    color: var(--text-secondary);
    border-bottom: 2px solid var(--border-light);
}

.data-table td {
    padding: 0.75rem 1rem;
    border-bottom: 1px solid var(--border-light);
    color: var(--text-primary);
}

.data-table tr:hover {
    background: rgba(0, 0, 0, 0.02);
}
```

### 8.3 快速卡片

```css
.quick-card {
    background: var(--bg-card);
    border: 1px solid var(--border-light);
    border-radius: 16px;
    padding: 1.5rem;
    cursor: pointer;
    transition: all 0.3s ease;
}

.quick-card:hover {
    transform: translateY(-3px);
    border-color: var(--accent-warm);
    box-shadow: 0 12px 32px rgba(212, 165, 116, 0.12);
}

.quick-card-icon {
    width: 44px;
    height: 44px;
    background: var(--gradient-soft);
    border-radius: 12px;
    font-size: 1.4rem;
    margin-bottom: 1rem;
}
```

---

## 9. 动效规范

### 9.1 过渡动画

```css
/* 通用过渡 */
* {
    transition-property: color, background-color, border-color, box-shadow, transform;
    transition-duration: 0.2s;
    transition-timing-function: ease;
}

/* 导航展开收起 */
.nav-subsection {
    max-height: 0;
    overflow: hidden;
    transition: max-height 0.25s ease;
}

.nav-section.expanded .nav-subsection {
    max-height: 500px;
}
```

### 9.2 滚动行为

```css
html {
    scroll-behavior: smooth;
}

/* 滚动条美化 */
::-webkit-scrollbar {
    width: 3px;
}

::-webkit-scrollbar-thumb {
    background: var(--border-medium);
    border-radius: 2px;
}

::-webkit-scrollbar-thumb:hover {
    background: var(--accent-warm);
}
```

---

## 10. 响应式设计

### 10.1 断点

| 断点 | 宽度 | 行为 |
|------|------|------|
| 桌面 | > 1200px | 完整三栏布局 |
| 平板 | 768px - 1200px | 隐藏侧边栏 |
| 手机 | < 768px | 隐藏横向导航，汉堡菜单 |

### 10.2 媒体查询

```css
@media (max-width: 1200px) {
    .sidebar {
        display: none;
    }
    main {
        margin-left: 0;
    }
}

@media (max-width: 768px) {
    header nav {
        display: none;
    }
    .hero h1 {
        font-size: 2.25rem;
    }
}
```

---

## 11. 最佳实践

### 11.1 可访问性

- 所有交互元素支持键盘导航
- 颜色对比度符合 WCAG AA 标准
- 图片提供 alt 文本
- 表单元素关联 label

### 11.2 性能优化

- 使用 CSS 变量减少重复
- 避免过多 box-shadow
- 滚动区域使用 `overflow-y: auto`
- 大型列表考虑虚拟滚动

### 11.3 内容组织

- 每个章节使用语义化的 section 标签
- 章节标题使用 `.section-header` 组件
- 步骤说明使用 `.steps` + `.step-item` 结构
- 代码示例使用 `.code-section` 组件

---

## 12. 文件结构

```
project/
├── index.html              # 主页面
├── css/
│   ├── variables.css       # CSS 变量
│   ├── layout.css          # 布局样式
│   ├── components.css      # 组件样式
│   └── typography.css      # 排版样式
├── js/
│   ├── navigation.js       # 导航逻辑
│   ├── search.js           # 搜索功能
│   └── scroll.js           # 滚动高亮
└── assets/
    └── images/             # 图片资源
```

---

## 版本历史

| 版本 | 日期 | 变更 |
|------|------|------|
| 1.0 | 2026-03-03 | 初始版本，基于 CMP 开发指北项目 |
