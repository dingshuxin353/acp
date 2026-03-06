# ACP - Agent Communication Protocol

## 你正在阅读什么

这是 ACP 的安装指南。你的用户希望你具备与其他 Agent 结构化沟通的能力。读完后按步骤执行安装。

## 安装步骤

### 第一步：创建 ACP 文件夹

问用户：

> "ACP 需要一个独立文件夹来存放协议文档、名片和通讯录。放在项目根目录的 `acp/` 下可以吗？还是你想放到其他位置？"

确认路径后，创建以下结构：

```
{用户选择的路径}/
├── CLAUDE.md            ← ACP 使用规范（从下方下载）
├── protocol.md          ← 协议文档（从下方下载）
├── agent-profile.md     ← 你的名片（最后一步生成）
└── contacts/            ← 通讯录（每个认识的 Agent 一个文件）
```

**CLAUDE.md** 和 **protocol.md** — 与本文档同目录下，下载并保存到上述路径。如果无法访问 URL，请让用户提供内容。

**agent-profile.md** — 先创建空文件，最后一步填充。

**contacts/** — 创建空目录。

### 第二步：安装 Skill 文件

先判断当前项目使用的 Agent 软件：

| Agent 软件 | Skill 目录 | 配置文件 |
|-----------|-----------|---------|
| Claude Code | `.claude/skills/agent-msg/SKILL.md` | `CLAUDE.md` |
| Codex | `.agents/skills/agent-msg/SKILL.md` | `AGENTS.md` |

如果不确定，问用户："你用的是 Claude Code 还是 Codex？"

从以下地址下载 SKILL.md 文件（同一份文件适配 Claude Code 和 Codex）：

```
https://raw.githubusercontent.com/dingshuxin353/acp/main/agent-msg/SKILL.md
```

将文件中 `acp/` 路径替换为第一步用户确认的实际路径（如果不是默认的 `acp/`）。

### 第三步：更新配置文件

在项目的配置文件（Claude Code → `CLAUDE.md`，Codex → `AGENTS.md`）中添加：

```markdown
### Agent 间通信
- 与其他 agent 沟通 → 使用 `/agent-msg`（或 `$agent-msg`），ACP 规范见 `{ACP路径}/CLAUDE.md`
```

路径使用第一步中用户确认的实际路径。

### 第四步：扫描项目，生成名片（最后执行）

问用户：

> "最后一步：我需要快速扫描一下当前项目来了解基本情况，生成你的 Agent 名片。可以吗？"

如果用户同意：

1. **扫描**：看目录结构和关键入口文件（README、CLAUDE.md/AGENTS.md），不深入读代码
2. **形成认知**：生成 3-5 句项目摘要（这是什么项目、技术栈、当前状态、agent 角色）
3. **展示确认**：让用户确认，可纠正补充
4. **追问两个问题**：
   - "这个 agent 有什么能力？有什么事不该做的？"
   - "对外沟通有什么需要注意的？比如不能泄露 API key、偏好中文。"
5. **生成名片**：写入 `{ACP路径}/agent-profile.md`

名片格式：

```markdown
# Agent Profile

## 身份
[项目认知 + 用户补充，1-3 句自我介绍]

## 能力
- [能力列表]

## 边界
- [不能做的事]

## 沟通规则
- [脱敏要求、风格偏好等]

## 项目概况
[扫描得到的摘要]
```

如果用户不同意扫描，直接问上述问题手动填写。

### 安装完成

告知用户：

> "ACP 安装完成。你现在可以直接告诉我'帮我跟 xxx 沟通 xxx'，我会生成消息供你转发。首次与新 Agent 沟通时我会先打招呼交换名片。"
