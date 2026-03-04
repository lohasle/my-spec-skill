# My Spec & Skill

规范驱动的前端开发范式 - 技术文档 HTML 页面设计与生成工具集

---

## 📁 项目结构

```
my_spec_skill/
├── README.md                          # 项目说明
├── specs/                             # 规范文档
│   └── tech-doc-html-spec.md          # 技术文档 HTML 页面设计规范
├── skills/                            # AI 技能
│   └── tech-doc-html-generator.md     # 技术文档 HTML 生成器技能
└── examples/                          # 示例文件（待添加）
```

---

## 📋 规范列表

### 1. 技术文档 HTML 页面设计规范

**文件**: `specs/tech-doc-html-spec.md`

**适用场景**:
- 开发指南文档
- API 文档
- 技术手册
- 培训材料

**核心特点**:
- 三栏式布局（Header + Sidebar + Main）
- Mintlify 风格设计
- 温暖橙色系配色
- 完整的组件库
- 搜索功能支持

---

## 🤖 技能列表

### 1. Tech Doc HTML Generator

**文件**: `skills/tech-doc-html-generator.md`

**功能**: 基于《技术文档 HTML 页面设计规范》自动生成符合规范的 HTML 页面

**核心能力**:
- 页面结构生成
- 组件自动生成
- 搜索功能集成
- 导航高亮实现
- 响应式设计支持

**使用方式**:
```
请使用 tech-doc-html-generator 技能生成一个 API 文档页面...
```

---

## 🎨 设计系统

### 颜色

| 变量 | 色值 | 用途 |
|------|------|------|
| `--accent-coral` | #E07A5F | 主强调色 |
| `--accent-warm` | #D4A574 | 次强调色 |
| `--bg-primary` | #FAF9F7 | 页面背景 |
| `--bg-secondary` | #F5F3F0 | 次级背景 |
| `--text-primary` | #1A1A2E | 主文字 |

### 组件

| 组件 | 类名 | 用途 |
|------|------|------|
| 章节标题 | `.section-header` | 文档章节标题 |
| 子标题 | `.subsection-title` | 重要子标题 |
| 代码块 | `.code-section` | 代码示例 |
| 信息框 | `.info-box` | 信息提示 |
| 警告框 | `.warning-box` | 警告提示 |
| 数据表 | `.data-table` | 数据展示 |
| 快速卡片 | `.quick-card` | 快速入口 |

---

## 🚀 快速开始

### 使用规范

1. 阅读 `specs/tech-doc-html-spec.md` 了解设计规范
2. 参考规范中的 CSS 变量和组件样式
3. 使用提供的模板结构编写页面

### 使用技能

1. 在 AI 助手中描述需求
2. AI 将基于技能生成符合规范的 HTML
3. 根据需要调整内容

---

## 📝 示例项目

基于本规范和技能构建的实际项目：

- [👹 以太坊白皮书（中文版）](./examples/ethereum-whitepaper-cn.html) - 下一代智能合约和去中心化应用平台
- [🌐 GitHub Pages Demo](https://lohasle.github.io/my-spec-skill/ethereum-whitepaper-cn.html) - 在线预览

---

## 🚀 在线演示

本项目通过 GitHub Pages 提供在线演示：

👉 **[查看所有示例](https://lohasle.github.io/my-spec-skill/)**

示例列表：
| 示例 | 描述 | 链接 |
|------|------|------|
| 以太坊白皮书 | 中文版技术文档示例 | [查看](https://lohasle.github.io/my-spec-skill/ethereum-whitepaper-cn.html) |
---

## 🔧 自定义

### 修改主题色

```css
:root {
    --accent-coral: #YOUR_COLOR;
    --accent-warm: #YOUR_COLOR;
}
```

### 添加深色模式

```css
:root.dark {
    --bg-primary: #1A1A2E;
    --text-primary: #FFFFFF;
}
```

---

## 📚 参考资料

- [Mintlify](https://mintlify.com/) - 文档平台设计参考
- [Tailwind CSS](https://tailwindcss.com/) - CSS 工具类参考
- [Google Fonts](https://fonts.google.com/) - 字体资源

---

## 📜 许可证

MIT License

---

## 👥 贡献

欢迎提交 Issue 和 Pull Request！

---

## 📅 更新日志

### v1.1.0 (2026-03-04)

- 🌟 新增以太坊白皮书中文版示例
- 🌐 配置 GitHub Pages 支持
- 📚 更新 README.md 文档

### v1.0.0 (2026-03-03)

- 初始版本
- 添加技术文档 HTML 页面设计规范
- 添加 Tech Doc HTML Generator 技能
