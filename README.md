# pstack-coding

一个适用于 Codex 的中文编码 Skill，整理自 Lauren Tan 的公开 pstack 工作流。

## 安装

将本仓库克隆到 Codex 用户级 skills 目录：

```powershell
git clone https://github.com/YujianGuo/pstack-coding-skill.git "$HOME/.codex/skills/pstack-coding"
```

要让 Skill 在每次编码任务中默认加载，可在 `~/.codex/AGENTS.md` 中加入：

```markdown
## Default coding workflow

For each task that writes or changes code, including fixes, refactors, tests, and scripts, load and follow the `pstack-coding` skill before implementing. If it is absent from the skills list, read `~/.codex/skills/pstack-coding/SKILL.md` directly. Use it alongside applicable project-specific skills and the user's current instructions.
```

## 工作流

- 先明确验收条件，再按仓库现有设计完成最小完整改动。
- 通过真实入口和可复查证据验证行为。
- 将有证据表明会重复的问题转为架构约束、类型、lint、CI 或回归测试。

完整指引见 [`SKILL.md`](SKILL.md)。

## 来源与许可

本 Skill 根据 [Cursor pstack](https://github.com/cursor/plugins/tree/main/pstack) 的公开资料整理，尤其参考其 `correct` Skill 和验证指南。此仓库提供独立的 Codex Skill，不包含 Cursor 官方插件代码，也不代表 Cursor 或 Lauren Tan。

本仓库按 MIT License 发布，并保留上游 pstack 的原始版权声明。详见 [`LICENSE`](LICENSE)。
