# pstack-coding-skill

一个面向 Codex 的 pstack 风格编码工作流，支持作为 Codex 插件安装，也保留独立 Skill 文件供手动安装。

这是基于公开 Cursor pstack 资料整理的 Codex 适配版，仅打包一个编码 Skill；不包含完整 Cursor 插件，也不代表 Cursor 或 Lauren Tan。

## 作为 Codex 插件安装

在终端添加插件市场：

    codex plugin marketplace add YujianGuo/pstack-coding-skill

然后在 Codex 中打开插件浏览器（/plugins），选择 pstack coding 市场并安装 pstack-coding。安装后新开一个对话。

## 手动安装为 Skill

将根目录的 SKILL.md 放到：

    ~/.codex/skills/pstack-coding/SKILL.md

想在每个编码任务中明确强制使用，可在 ~/.codex/AGENTS.md 中加入：

    ## Default coding workflow
    For each task that writes or changes code, including fixes, refactors, tests, and scripts, load and follow the pstack-coding skill before implementing. If it is absent from the skills list, read ~/.codex/skills/pstack-coding/SKILL.md directly. Use it alongside applicable project-specific skills and the user's current instructions.

## 工作流

- 先明确验收条件，再按现有代码结构完成最小完整改动。
- 通过真实入口和可复查证据验证行为。
- 将有证据表明会重复的问题转为架构约束、类型、lint、CI 或回归测试。

插件目录中的 skills/pstack-coding/SKILL.md 是插件打包版本；根目录的 SKILL.md 适合手动安装。

## 来源与许可

本项目根据 [Cursor pstack](https://github.com/cursor/plugins/tree/main/pstack) 的公开资料整理，重点参考 correct Skill 与验证指南。MIT 许可保留上游版权声明，详见 LICENSE。