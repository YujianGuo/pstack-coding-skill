---
name: pstack-coding
description: Use for coding tasks that write or change code, including features, bug fixes, refactors, tests, and scripts. Fit the change to the existing codebase, verify the requested behavior with runnable evidence, and turn recurring mistakes into enforceable checks. Applies to 编码、修 bug、重构、写测试和脚本.
---

# pstack 编码工作流

每次编码都走「确认验收条件 → 实现最小完整改动 → 验证真实行为」。小改动可以直接完成这三步。跨模块、行为敏感或分阶段的改动，先确认受影响的调用方和当前阶段的验收范围，再动手。

## 把正确的实现变成最容易走的路径

- 从正常入口追到实现和依赖方。根据仓库现行约定和实际代码确定改动边界，优先沿用能保持行为的 API、类型和模块。用户明确授权的行为变化以外，保留现有调用方的契约。
- 修 bug 时，能低成本重现就先跑出原来的失败，再用同一路径验证修复。补测试时，覆盖已有测试遗漏的具体回归，并确认断言能在坏实现上失败。避免给每个小改动机械地加测试或抽象。
- 既有 workaround 可能被后续 Agent 当作范例。发现和本次改动直接相关的坏范例时，在授权范围内处理，避免为局部问题扩大重构。

## 让证据对应验收条件

- 根据改动选择能证明行为的最小检查。命令行改动跑真实命令并检查输出和退出码，界面改动跑实际用户路径并按需保留截图或录屏，写入改动通过正常入口读回。性能改动用相同条件比较基线和改动版，并检查输出一致性。
- 复用仓库已有的测试、lint、类型检查及运行工具。必要时补一个可重复运行的短命令或脚本。按影响范围扩大验证，确保最终检查覆盖实际交付的 diff。
- 报告改动、执行过的关键命令及结果。区分静态检查、模拟测试与真实运行覆盖的范围。检查受环境或权限所限时，说明哪项行为尚待验证。分阶段任务按当前获准的阶段验收和交付。

## 让同一类错误难以重现

遇到有证据表明会重复的错误，按适用层级选一道能持续执行的检查。先用 API、模块边界或类型消除不合法路径。需要静态识别时用 lint 或 CI，并在诊断中指出正确入口。行为问题用针对性的回归测试。只有需要判断的约定才适合写进说明或提示词。

新增约束前，核对已有检查和合法用法。用一次真实旧失败验证新检查能拦截它，再验证正确路径通过。仓库级规则或 CI 的变更若超出任务范围，报告拟加的检查及其依据。

来源为 Lauren Tan 的 [pstack](https://github.com/cursor/plugins/blob/main/pstack/README.md)，重点参考 [correct](https://github.com/cursor/plugins/blob/main/pstack/skills/correct/SKILL.md) 和 [Verify and ship](https://github.com/cursor/plugins/blob/main/pstack/docs/guide/06-verify-and-ship.md)。
