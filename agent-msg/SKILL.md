---
name: agent-msg
description: 生成 Agent 间通信消息 (ACP)。帮你的 agent 写一封结构清晰、上下文完备的消息给另一个 agent，人工转发即可。用法：/agent-msg [自然语言描述]。
---

# /agent-msg — Agent 间通信 (ACP)

帮用户的 agent 生成结构化消息，用于与其他 agent 沟通。人类负责在 agent 之间复制粘贴传递。

## 触发方式

- `/agent-msg [任何自然语言]`（Claude Code）或 `$agent-msg [任何自然语言]`（Codex）
- 用户粘贴一段 ACP 消息（含 `--- ACP START ---` 标记）到对话中时，自动识别并处理

## ACP 文件夹

本项目的 ACP 运行时文件位于 `acp/`。触发时先读取 `acp/CLAUDE.md` 获取完整使用规范。

## 执行流程

### 首次使用（agent-profile.md 不存在）

自动进入初始化：
1. 快速扫描项目结构，形成认知摘要，展示给用户确认
2. 追问能力边界和沟通规则
3. 生成 `acp/agent-profile.md`

### 日常使用

按 `acp/CLAUDE.md` 中定义的发送/接收流程执行。
