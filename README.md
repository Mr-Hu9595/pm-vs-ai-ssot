# PM VS AI 单一事实源知识库系统

> PM vs AI — Single Source of Truth Knowledge Base
> 人指挥 AI 干活并留痕的可复用知识库系统（Claude Code Skill）

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

当开发由"人（PM）通过提示词调度 AI 执行者（Claude / Codex / 其他 agent）干活"主导时，最大的风险不是代码写错，而是**工作过程不可追溯、知识沉淀在对话里、AI 换一个会话就失忆**。

这套系统把项目的文档组织成一个**单一事实源知识库**：

- 每项工作 = 唯一编号任务文档 + 主索引 + 提示词归档 + 收工交接
- 可追溯：任何工作，通过文档和索引都能还原"做了什么、为什么、怎么做的"
- 跨会话不丢失：长期记忆 + 断点续传，AI 第二天开机不失忆
- 事前检查：开机过清单，主动发现问题而不是被动收记录

## 核心原则

1. **代码 / 实际状态 > 文档** —— 文档是快照，代码是真相
2. **索引永远最新** —— 每次任务后必更新主索引，索引滞后 = 知识丢失第一步
3. **一切工作留痕** —— 任务报告、提示词、决策、交接，全部落盘
4. **事前检查 > 事后记录** —— 主动跑检查清单
5. **诚实记录** —— 不捏造、不兜底、不确定就问

## 快速开始

1. 安装 Skill：
   - 项目级：复制到 `<你的项目>/.claude/skills/pm-vs-ai-ssot/`
   - 全局：复制到 `~/.claude/skills/pm-vs-ai-ssot/`
2. 按 `references/templates/` 初始化文档目录结构
3. 每次任务走闭环：**写提示词 → 归档提示词 → 下发执行 → 执行报告 → 独立验收 → 任务文档 → 更新索引 → 收工交接**

## 目录结构

```
<项目根>/
├── docs/
│   ├── index.md                    # 主索引（SSOT 入口）
│   ├── preflight-checklist.md      # 开机检查清单
│   ├── tasks/
│   │   ├── index.md                # 任务表格
│   │   ├── AGENTS.md               # 文档系统子规范
│   │   ├── T<NNN>-<slug>.md        # 任务报告
│   │   └── T<NNN>-prompt.md        # 提示词归档
│   ├── conversations/              # 会话记录
│   ├── breakpoints/                # 任务级断点
│   └── handovers/                  # 每日收工交接
└── .claude/
    └── memory/                     # 长期记忆 + MEMORY.md 索引
```

## 核心工作流（8 步）

```
立项 → 归档提示词 → 下发执行 → 执行报告 → 独立验收 → 任务文档 → 更新索引 → 收工交接
```

关键点：

- **提示词归档要"下发前"就做**，不是任务做完才补——这是最高频的失守点
- **独立验收**：看实际代码 / git / 数据，不盲信执行者报告
- **收工交接**用【收工日期】命名，桌面只留最新一份，历史份入库
- **记忆**每条一个文件 + 一个索引，只记非显然的事实

## 模板清单

`references/templates/` 提供 6 个可直接套用的模板：

| 模板 | 用途 |
|---|---|
| `task-report-template.md` | 任务报告骨架 |
| `prompt-archive-template.md` | 提示词归档骨架（含分界线） |
| `handover-template.md` | 每日收工交接骨架 |
| `index-template.md` | 主索引骨架 |
| `preflight-checklist-template.md` | 开机检查清单骨架 |
| `memory-template.md` | 记忆条目骨架 |

## 适用场景

- 个人用 AI agent（Claude Code / Codex / OpenClaw 等）辅助开发的中大型项目
- 团队"人 + AI"混合开发，需要留痕与追溯
- 多 agent 并行、需要交接与断点续传的项目

## 关联

- 可与 [Claude Code](https://claude.com/claude-code) 的 Skills / 记忆系统配合使用
- 方法论不绑定任何特定工具，纯 markdown 体系，可平移到任意文档站 / 代码仓库

## License

[MIT](LICENSE)
