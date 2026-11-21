# clarify-first

一个跨 AI 工具的「先厘清，再动手」需求采访 Skill。

当你给 AI Agent 提出一个还比较模糊的需求时，它可以防止 Agent 急着直接改代码或一口气甩出冗长问卷，而是强制按照 **「大白话复述 → 一次一问逐轮采访 → 再次大白话复述并等明确确认 → 动手执行」** 的节奏工作。

## 核心特点

- **仅在主动调用时触发**：平时正常对话不打扰，只在你明确点名 `clarify-first` 或要求“先厘清再动手”时生效。
- **先说大白话确认理解**：收到模糊需求后，先用通俗易懂的白话复述一遍，确保没有理解跑偏。
- **每次只问 1 个问题**：确有关键歧义时，一次只抛当前最关键的 1 个问题，优先给出 2–3 个大白话选项（可标推荐项）并允许自由补充；需求够清楚就不硬凑问题。
- **答完最后一题也不能抢跑**：哪怕你刚回答完最后一个问题，Agent 也必须先整合全部回答，再次用大白话复述最终需求（含做什么、不做什么），等你明确回复「确认」后才能动手改代码。
- **跨工具通用**：纯标准 `SKILL.md` 格式，不绑定任何一家 AI 工具的专属指令，适用于 Antigravity、Claude Code、Codex、Cursor、Gemini CLI、GitHub Copilot、OpenCode 等支持 Agent Skills 规范的工具。

## 仓库结构

```text
clarify-first/
├── README.md
├── LICENSE
├── .gitignore
└── skills/
    └── clarify-first/
        └── SKILL.md
```

## 安装方式

### 方式一：使用 Agent Skills CLI 一键安装

```bash
npx skills add Bobs-k/clarify-first
```

### 方式二：手动安装

将本仓库中的 `skills/clarify-first` 目录复制到对应工具的 skills 目录即可：

| 工具 | 全局 Skills 目录 |
| --- | --- |
| 通用共享目录 | `~/.agents/skills/clarify-first` |
| Antigravity | `~/.gemini/config/skills/clarify-first` |
| Claude Code | `~/.claude/skills/clarify-first` |
| Codex | `~/.codex/skills/clarify-first` |
| Cursor | `~/.cursor/skills/clarify-first` |
| Gemini CLI | `~/.gemini/skills/clarify-first` |
| GitHub Copilot | `~/.copilot/skills/clarify-first` |
| OpenCode | `~/.config/opencode/skills/clarify-first` |

也可以放到具体项目的 `.agents/skills/clarify-first` 目录中随仓库共享。

## 使用方法

在对话中主动调用即可，例如：

```text
用 clarify-first 先帮我理清这个需求：我想给现有项目加一个导出功能，但还没想清楚具体形式。
```

或：

```text
先用 clarify-first 采访我：我想重构一下登录流程。
```

## License

[MIT](./LICENSE)
