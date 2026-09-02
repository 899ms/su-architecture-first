# su-architecture-first

<p align="center">
  <a href="./README.md">English</a> · <strong>简体中文</strong>
</p>

一个轻量的架构优先 Agent Skill，面向所有使用 AI 编码 Agent 做工程的人：从小修复、普通功能和局部重构，到复发故障与系统级改造都可以使用。

它帮助 Agent 在改动系统前确认真实目标、责任层、唯一事实源、根因、正确的变更类型和验证证据。分析深度随任务调整：清楚的局部变更只做快速判断；含糊、复发、跨层或高风险的变更才做完整分析。

## 它能做什么

- 先确认结果，避免解决成相邻但不同的问题。
- 检查现有系统和权威事实源。
- 定位真正负责的层与对象。
- 在证据证明并非如此前，把复发问题优先当作结构问题调查。
- 增加逻辑前先检查是否应该删除或合并。
- 区分删除、重构、实现、隐藏、文案修改和 UI 优化。
- 改动前定义验收与回归证据。
- 不把 AI 与工作流的内部复杂度转嫁给普通用户。
- 让用户可见的产物、执行、返回与保存形成闭环。
- 只使用当前决策真正需要的架构表达深度。

这个 Skill 本身就是完整能力，不依赖私人增强、个人文件、外部服务、配套 Skill 或特定 Agent 客户端。

## 主动触发

兼容的 Agent 都可以使用自然语言：

```text
架构优先：先确认目标、责任层、变更类型和验证方式，然后继续。
```

```text
Architecture first: confirm the goal, owning layer, change type, and validation, then continue.
```

不同客户端的显式触发方式并不完全相同：

| Agent 客户端 | 显式使用方式 |
|---|---|
| Codex CLI / IDE | `$su-architecture-first ...`，或打开 `/skills` 后选择它 |
| Claude Code | `/su-architecture-first ...` |
| GitHub Copilot CLI | `/su-architecture-first ...` |
| Gemini CLI | 用自然语言提出；用 `/skills list` 检查是否已发现 |
| OpenCode | 用自然语言提出；相关时由 Agent 加载 Skill |

当任务出现复发问题、补丁累积、状态冲突、责任不清，或内部复杂度泄漏到用户体验时，Skill 描述也支持自动触发。

## 一句话安装

把下面这句话发给能够访问 GitHub 并安装本地 Skill 的 Agent：

```text
请把 https://github.com/doublesq97-ui/su-architecture-first 里的 Agent Skill 安装到我的个人 Skill 目录，完整保留整个 Skill 文件夹，并确认 su-architecture-first 已能被发现。
```

## 手动安装

多数兼容客户端都能从 `~/.agents/skills/` 发现个人 Skill：

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
