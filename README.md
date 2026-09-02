# su-architecture-first

<p align="center">
  <strong>English</strong> · <a href="./README.zh-CN.md">简体中文</a>
</p>

A lightweight architecture-first Agent Skill for engineering work—from small fixes and ordinary features to recurring failures and system changes.

It helps an AI agent working on engineering locate the real goal, owning layer, source of truth, root cause, correct change type, and validation evidence before changing the system. The depth scales with the work: clear local changes get a quick pass; ambiguous, recurring, cross-layer, or high-risk changes get a full review.

## What it does

- Confirms the outcome before solving a nearby problem.
- Inspects the existing system and its authoritative sources.
- Locates the owning layer and responsible object.
- Treats recurring failures as structural until evidence says otherwise.
- Checks deletion and consolidation before adding logic.
- Distinguishes delete, refactor, implement, hide, copy, and UI work.
- Defines acceptance and regression evidence before mutation.
- Keeps internal AI and workflow complexity out of normal user work.
- Closes the loop for visible outputs, execution, return, and saving.
- Uses only as much architecture representation as the decision needs.

The Skill is complete on its own. Its runtime core is plain `SKILL.md` plus Markdown references, using relative links and no scripts, MCP servers, absolute local paths, vendor-only tools, private overlay, or companion Skill. Clients that support file-based Agent Skills can use the same folder unchanged; only installation, discovery, and tool permissions vary by client.

Clients without a native Skill loader can still use the repository as an instruction bundle: attach the files and ask the agent to read `SKILL.md` first. In that mode, persistence and automatic activation depend on the client.

## Trigger it

Natural language works across compatible agents:

```text
Architecture first: confirm the goal, owning layer, change type, and validation, then continue.
```

```text
架构优先：先确认目标、责任层、变更类型和验证方式，然后继续。
```

Explicit syntax varies by client:

| Agent client | Support mode | Explicit use |
|---|---|---|
| Codex CLI / IDE | Native Skill | `$su-architecture-first ...` or open `/skills` and select it |
| Claude Code | Native Skill | `/su-architecture-first ...` |
| GitHub Copilot CLI | Native Skill | `/su-architecture-first ...` |
| Gemini CLI | Native Skill | Ask in natural language; use `/skills list` to verify discovery |
| OpenCode | Native Skill | Ask in natural language; the agent loads the Skill when relevant |
| WorkBuddy | Native Skill | Say `Use su-architecture-first: ...` after importing the Skill package |
| Qoder / Qoder CLI | Native Skill | Type `/` and select the Skill, or use `/su-architecture-first ...` in Qoder CLI |
| QwenWork / 千问办公 | Native Skill | Type `/` and select the Skill, or say `使用 su-architecture-first：...` |
| Doubao desktop / 豆包桌面端 | Instruction bundle | Attach the repository files, then say `Read SKILL.md first and use architecture-first reasoning: ...` |
| Other file-capable agents | Native Skill or instruction bundle | Install the folder when supported; otherwise attach it and invoke it in natural language |

The description also supports automatic activation for recurring problems, accumulated patches, conflicting state, unclear responsibility, or internal complexity leaking into the user experience.

## Quick install

Give this one sentence to an agent that can access GitHub and install local Skills:

```text
Install the Agent Skill from https://github.com/doublesq97-ui/su-architecture-first for my user account, keep the whole skill directory together, and verify that su-architecture-first is discoverable.
```

## Manual install

Some compatible clients discover personal Skills from `~/.agents/skills/`; others use their own directory or an import screen:

```bash
git clone https://github.com/doublesq97-ui/su-architecture-first ~/.agents/skills/su-architecture-first
```

| Agent client | Personal Skill location or installer |
|---|---|
| [Codex](https://developers.openai.com/codex/skills) | `~/.agents/skills/su-architecture-first` |
| [Claude Code](https://code.claude.com/docs/en/slash-commands) | `~/.claude/skills/su-architecture-first` |
| [Gemini CLI](https://geminicli.com/docs/cli/tutorials/skills-getting-started/) | `gemini skills install https://github.com/doublesq97-ui/su-architecture-first` |
| [GitHub Copilot](https://docs.github.com/en/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/add-skills) | `~/.agents/skills/su-architecture-first` |
| [OpenCode](https://opencode.ai/docs/skills) | `~/.agents/skills/su-architecture-first` |
| [WorkBuddy](https://cloud.tencent.com/document/product/1831/134432) | Open **Experts · Skills · Connectors → Add Skill → Upload Skill**, then import the repository folder or ZIP |
| [Qoder](https://docs.qoder.com/qoder/skills) | Open **Extensions → Skills → Add Skills → Upload Skill** and import a ZIP; Qoder CLI can use `~/.qoder/skills/su-architecture-first` |
| [QwenWork / 千问办公](https://help.aliyun.com/zh/qwenwork/skills) | Give the repository URL to QwenWork, or place the folder at `~/.qwenworkcn/skills/su-architecture-first` |
| [Doubao desktop / 豆包桌面端](https://www.doubao.com/download/desktop) | Use the repository as an instruction bundle by uploading its files; a native persistent `SKILL.md` installer is not currently documented |

Keep `SKILL.md`, `agents/`, and `references/` together, then reload the client if it does not discover the Skill immediately.

## Example requests

For a small, clear change:

```text
架构优先：给设置页增加导出按钮。目标和归属明确的话，快速判断后直接做。
```

For a recurring problem:

```text
Use $su-architecture-first to find why this task state keeps diverging, choose the owning layer, and define regression evidence before changing code.
```

For an authorized implementation:

```text
直接开工，但先做最小充分的架构判断；不要重复询问实施授权。
```

## References

The core decision path stays in `SKILL.md`. Focused references load only when needed:

- system layers and sources of truth;
- structural diagnosis for recurring problems;
- change-type classification and ordering;
- acceptance and regression design;
- AI workbench and Chat-first patterns.

Chinese reading copies are available in [docs/zh-CN](docs/zh-CN/), including a [Chinese version of the Skill body](docs/zh-CN/SKILL.zh-CN.md). The root English `SKILL.md` remains the single discoverable Skill.

Tested with realistic product and engineering scenarios.

## License

This project is licensed under the [MIT License](LICENSE).

Copyright © 2026 Su 𝕏 @Sukiea1008 / doublesq.
