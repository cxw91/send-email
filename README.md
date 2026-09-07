# send-email

> WorkBuddy 交互式邮件群发技能：从 Excel 联系人列表中选择收件人并发送个性化邮件。

## 简介

`send-email` 是一个面向 WorkBuddy 的智能体技能，提供交互式邮件群发能力。它从本地的 Excel 联系人列表中读取收件人，支持点名快速匹配、动态新增联系人，并通过 Agent Mail 或 SMTP 发送带变量替换的个性化邮件。

## 功能特性

- **联系人管理**：默认读取 `docs/contacts.xlsx`（不存在则自动创建，列：姓名、邮箱）。
- **点名即查**：用户直接指定收件人时，先按姓名精确匹配再模糊匹配；未命中则提示补充邮箱并自动归档。
- **交互式多选**：未点名时通过勾选面板浏览并选择收件人，支持「全选」。
- **个性化模板**：邮件正文支持 `{姓名}`、`{邮箱}` 等变量，按联系人自动替换。
- **发送确认**：Agent Mail 返回 `CONFIRMATION_REQUIRED` 时，展示摘要并要求用户确认后再发送。
- **发送节奏控制**：每封邮件间隔 0.5 秒，发送后报告成功/失败列表。

## 技术栈

- 纯 Markdown 技能描述（SKILL.md），无外部依赖。
- 运行依赖 WorkBuddy 的 Excel 读写能力与 Agent Mail / SMTP 连接器。

## 快速开始

### 环境要求

- 已安装 WorkBuddy 并连接 Agent Mail（或配置 SMTP）连接器。
- 需要可写权限的本地目录用于存放 `docs/contacts.xlsx`。

### 安装

将本目录放入 WorkBuddy 的技能目录（如 `~/.workbuddy/skills/send-email/`），重启或刷新技能列表即可启用。

### 使用

在对话中提到「发邮件」「邮件群发」或「给 XX 发邮件」即会自动激活本技能，按提示选择收件人、编辑内容并发送。

## 项目结构

```text
send-email/
├── SKILL.md        # 技能定义与执行步骤
├── README.md       # 本文件
└── docs/           # 数据目录（默认存放 contacts.xlsx，首次使用时创建）
```

## License

未指定。
