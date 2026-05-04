# APP文案生成器

帮助产品经理为手机系统应用编写专业文案，覆盖功能命名、Slogan、营销话术、交互提示和版本更新日志。

## 触发条件

当用户请求为手机系统应用编写文案时触发，包括但不限于：

- 功能/按钮/设置项命名
- 宣传 Slogan / 一句话卖点
- 营销话术（应用商店描述、官网介绍、社交媒体推广）
- 交互提示文案（空状态、错误提示、权限申请说明、操作反馈）
- 版本更新日志 / Release Notes
- 文案风格调优、字数调整、多版本生成

不适用于：第三方 App 的文案需求（除非用户特别说明）、纯技术文档写作。

## 使用流程

### 第一步：收集用户输入

触发时必须向用户确认以下信息（可一次性提问，缺省时引导补充）：

| 输入项 | 说明 | 示例 |
|--------|------|------|
| **应用名称** | 哪个系统应用 | "照片"、"备忘录"、"设置" |
| **功能模块** | 针对什么功能 | "AI 修图"、"智能分类"、"云同步" |
| **产出类型** | 需要什么类型的文案 | 功能命名 / Slogan / 营销话术 / 交互提示 / 更新日志 |
| **目标平台** | 面向哪个系统 | Apple / Android / 全平台 / 不限 |
| **侧重点** | 想凸显什么 | "AI 能力"、"安全性"、"便捷性"、"生态协同" |
| **风格偏好** | 文案调性 | 科技感 / 亲和力 / 专业严谨 / 简洁有力 / 情感共鸣 |
| **约束条件** | 字数、格式等限制 | "不超过 20 字"、"需要 3 个版本" |

**缺省处理：** 用户未指定平台和风格时，默认全平台通用，产出 3 个版本供选择。

### 第二步：选择参考规范

根据产出类型和目标平台加载对应的参考文件：

- 功能命名 → `references/naming-conventions.md` + `references/terminology.md`
- Slogan / 营销话术 → `references/tone-guide.md` + `assets/examples/good-copies.md`
- 交互提示 → `references/naming-conventions.md` + `references/tone-guide.md`
- 更新日志 → `references/tone-guide.md`

同时参考 `references/case-library.md` 中 Apple / Google / Huawei 的现有案例。

### 第三步：生成文案

遵循以下核心原则：

1. **对齐目标平台风格**：根据用户指定的平台（Apple/Android/全平台），选择对应的用词和语气
2. **参考竞品但不抄袭**：借鉴三大平台的表达思路，转化为目标应用语境
3. **多版本输出**：每次至少提供 3 个版本，标注各自的特点和适用场景
4. **标注依据**：关键用词选择附上规范依据

### 第四步：质量检查

生成后运行 `scripts/copy-validator.py` 进行基础质量检查（字数超限、禁用词、格式规范、术语一致性），并将检查结果一并展示给用户。

## 文件结构

```
app-copywriter/
├── SKILL.md
├── references/
│   ├── naming-conventions.md    # 命名规范（通用 + 各平台差异）
│   ├── tone-guide.md            # 语气调性指南（4 种语气分层 + 场景匹配表）
│   ├── terminology.md           # 通用术语表 + 各平台用词差异
│   └── case-library.md          # Apple / Google / Huawei 案例库 + 对比总结
├── assets/
│   ├── templates/
│   │   ├── slogan-template.md
│   │   ├── app-desc-template.md
│   │   ├── feature-copy-template.md
│   │   ├── microcopy-template.md
│   │   └── release-notes-template.md
│   └── examples/
│       └── good-copies.md       # 优秀案例
└── scripts/
    └── copy-validator.py        # 文案质量检查
```
