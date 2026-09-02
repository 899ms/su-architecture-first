# su-architecture-first

<p align="center">
  <strong>English</strong> · <a href="./README.zh-CN.md">简体中文</a>
</p>

A lightweight architecture-first Agent Skill for engineering work—from small fixes and ordinary features to recurring failures and system changes.

It helps an AI coding agent locate the real goal, owning layer, source of truth, root cause, correct change type, and validation evidence before changing the system. The depth scales with the work: clear local changes get a quick pass; ambiguous, recurring, cross-layer, or high-risk changes get a full review.

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

The Skill is complete on its own. It requires no private overlay, personal file, external service, companion Skill, or specific agent host.

## Trigger it

Natural language works across compatible agents:

```text
Architecture first: confirm the goal, owning layer, change type, and validation, then continue.
```

```text
架构优先：先确认目标、责任层、变更类型和验证方式，然后继续。
```

Explicit syntax varies by client:

| Agent client | Explicit use |
|---|---|
| Codex CLI / IDE | `$su-architecture-first ...` or open `/skills` and select it |
| Claude Code | `/su-architecture-first ...` |
| GitHub Copilot CLI | `/su-architecture-first ...` |
| Gemini CLI | Ask in natural language; use `/skills list` to verify discovery |
| OpenCode | Ask in natural language; the agent loads the Skill when relevant |

The description also supports automatic activation for recurring problems, accumulated patches, conflicting state, unclear responsibility, or internal complexity leaking into the user experience.

## Quick install

Give this one sentence to an agent that can access GitHub and install local Skills:

```text
Install the Agent Skill from https://github.com/doublesq97-ui/su-architecture-first for my user account, keep the whole skill directory together, and verify that su-architecture-first is discoverable.
```

## Manual install

Most compatible clients discover personal Skills from `~/.agents/skills/`:

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
