# su-architecture-first

<p align="center">
  <a href="./README.md">English</a> · <strong>简体中文</strong>
</p>

一个轻量的架构优先 Agent Skill，面向所有使用 AI Agent 做工程的人：从小修复、普通功能和局部重构，到复发故障与系统级改造都可以使用。

它帮助 Agent 在改动系统前确认真实目标、责任层、唯一事实源、根因、正确的变更类型和验证证据。分析深度随任务调整：清楚的局部变更只做快速判断；含糊、复发、跨层或高风险的变更才做完整分析。

## 它能做什么

- 先确认结果，避免解决成相邻但不同的问题。
- 检查现有系统和权威事实源。
- 定位真正负责的层与对象。
- 在证据证明并非如此前，把复发问题优先当作结构问题调查。
- 增加逻辑前，先检查有证据证明错误、过时、重复或已被替代的逻辑能否安全移除；删除从来不是自动答案。
- 区分删除、重构、实现、隐藏、文案修改和 UI 优化。
- 改动前定义验收与回归证据。
- 不把 AI 与工作流的内部复杂度转嫁给普通用户。
- 让用户可见的产物、执行、返回与保存形成闭环。
- 只使用当前决策真正需要的架构表达深度。

这个 Skill 本身就是完整能力。运行核心只有 `SKILL.md` 和 Markdown 参考资料，全部使用相对路径；不含脚本、MCP 服务、本机绝对路径、厂商专用工具、私人增强或配套 Skill。支持文件型 Agent Skill 的客户端可以原样使用同一个文件夹，不同平台主要只差安装入口、发现机制和工具权限。

尚未提供原生 Skill 加载器的客户端，也可以把仓库作为指令包使用：上传这些文件，并要求 Agent 先读取 `SKILL.md`。在这种模式下，能否长期保存和自动触发取决于客户端本身。

## 主动触发

兼容的 Agent 都可以使用自然语言：

```text
架构优先：先确认目标、责任层、变更类型和验证方式，然后继续。
```

```text
Architecture first: confirm the goal, owning layer, change type, and validation, then continue.
```

不同客户端的显式触发方式并不完全相同：

| Agent 客户端 | 支持方式 | 显式使用方式 |
|---|---|---|
| Codex CLI / IDE | 原生 Skill | `$su-architecture-first ...` |
| Claude Code | 原生 Skill | `/su-architecture-first ...` |
| GitHub Copilot CLI | 原生 Skill | `/su-architecture-first ...` |
| Gemini CLI | 原生 Skill | 说：`使用 su-architecture-first：...`，或直接用自然语言提出 |
| OpenCode | 原生 Skill | 用自然语言提出；相关时由 Agent 加载 Skill |
| WorkBuddy | 原生 Skill | 导入 Skill 包后说：`使用 su-architecture-first：...` |
| Qoder / Qoder CLI | 原生 Skill | 输入 `/` 后选择该 Skill；Qoder CLI 也可使用 `/su-architecture-first ...` |
| 千问办公 / QwenWork | 原生 Skill | 输入 `/` 后选择该 Skill，或说：`使用 su-architecture-first：...` |
| 豆包桌面端 | 指令包 | 上传仓库文件后说：`先读取 SKILL.md，再用架构优先的方法处理……` |
| 其他可读取文件的 Agent | 原生 Skill 或指令包 | 支持安装时安装整个文件夹；否则上传文件并用自然语言调用 |

当任务出现复发问题、补丁累积、状态冲突、责任不清，或内部复杂度泄漏到用户体验时，Skill 描述也支持自动触发。

## 一句话安装

把下面这句话发给能够访问 GitHub 并安装本地 Skill 的 Agent：

```text
请把 https://github.com/doublesq97-ui/su-architecture-first 里的 Agent Skill 安装到我的个人 Skill 目录，完整保留整个 Skill 文件夹，并确认 su-architecture-first 已能被发现。
```

## 手动安装

部分兼容客户端从 `~/.agents/skills/` 发现个人 Skill，其他客户端使用自己的目录或导入界面：

```bash
git clone https://github.com/doublesq97-ui/su-architecture-first ~/.agents/skills/su-architecture-first
```

| Agent 客户端 | 个人 Skill 位置或安装命令 |
|---|---|
| [Codex](https://developers.openai.com/codex/skills) | `~/.agents/skills/su-architecture-first` |
| [Claude Code](https://code.claude.com/docs/en/slash-commands) | `~/.claude/skills/su-architecture-first` |
| [Gemini CLI](https://geminicli.com/docs/cli/tutorials/skills-getting-started/) | `gemini skills install https://github.com/doublesq97-ui/su-architecture-first` |
| [GitHub Copilot](https://docs.github.com/en/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/add-skills) | `~/.agents/skills/su-architecture-first` |
| [OpenCode](https://opencode.ai/docs/skills) | `~/.agents/skills/su-architecture-first` |
| [WorkBuddy](https://cloud.tencent.com/document/product/1831/134432) | 打开「专家·技能·连接器 → 添加技能 → 上传技能」，导入仓库文件夹或 ZIP |
| [Qoder](https://docs.qoder.com/qoder/skills) | 打开「Extensions → Skills → Add Skills → Upload Skill」导入 ZIP；Qoder CLI 也可放到 `~/.qoder/skills/su-architecture-first` |
| [千问办公 / QwenWork](https://help.aliyun.com/zh/qwenwork/skills) | 直接把仓库链接发给千问办公，或把文件夹放到 `~/.qwenworkcn/skills/su-architecture-first` |
| [豆包桌面端](https://www.doubao.com/download/desktop) | 上传仓库文件，把它作为指令包使用；目前官方尚未说明原生、持久化的 `SKILL.md` 安装入口 |

请保持 `SKILL.md`、`agents/` 和 `references/` 在同一个目录中。如果客户端没有立即发现 Skill，重新加载一次。

## 请求示例

小而明确的改动：

```text
架构优先：给设置页增加导出按钮。目标和归属明确的话，快速判断后直接做。
```

反复出现的问题：

```text
用 su-architecture-first 找出任务状态反复不一致的原因，确认责任层，并在改代码前定义回归证据。
```

已经授权的实施：

```text
直接开工，但先做最小充分的架构判断；不要重复询问实施授权。
```

## 参考资料

稳定的判断主线保留在 `SKILL.md`。以下参考资料只在对应情况出现时加载：

- 系统分层与唯一事实源；
- 复发问题的结构性诊断；
- 变更类型与实施顺序；
- 验收与回归设计；
- AI 工作台与 Chat-first 模式。

完整中文对照内容位于 [docs/zh-CN](docs/zh-CN/)，其中包括 [Skill 本体中文对照版](docs/zh-CN/SKILL.zh-CN.md)。仓库根目录的英文 `SKILL.md` 始终是唯一会被发现的 Skill。

已使用真实的产品与工程场景进行测试。

## 许可证

本项目使用 [MIT License](LICENSE)。

Copyright © 2026 Su 𝕏 @Sukiea1008 / doublesq.
