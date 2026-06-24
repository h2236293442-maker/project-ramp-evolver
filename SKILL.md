---
name: project-ramp-evolver
description: Build fast project onboarding context and evolve reusable project memory across coding sessions. Use at session start, session end, IDE/tool/model handoff, project takeover, or after debugging/fixing work to read or update PROJECT_BRIEF.md and SESSION_EVOLUTION.md with concise context, risks, next actions, and reusable lessons.
---

# Project Ramp Evolver

## Goal
让模型在新会话里快速进入可工作的项目状态，并持续沉淀可复用经验。

## When To Invoke
- 新 IDE / 新会话刚开始，需要快速接手项目
- 会话结束前，需要总结本次变更、坑点、复盘结论
- 跨模型或跨工具切换后，需要统一上下文

## Inputs
- `PROJECT_BRIEF.md`
- `SESSION_EVOLUTION.md`
- 当前工作区最新代码状态

如果文件不存在，先创建模板并引导补全最小必填项。

## File Policy

- Prefer placing both files at the repository root unless the user specifies another path.
- Keep `PROJECT_BRIEF.md` stable and project-level.
- Keep `SESSION_EVOLUTION.md` focused on reusable session lessons, not chat transcripts.
- Never write secrets, private tokens, customer data, or raw credentials.
- Do not update Git remotes, production config, or issue trackers unless the user explicitly asks.

## Workflow
### A) Session Start（快速接手）
1. 读取 `PROJECT_BRIEF.md` 和 `SESSION_EVOLUTION.md`。
2. 输出“可直接开工”的最小上下文：
   - 当前项目目标
   - 关键模块与入口
   - 常见命令与验证路径
   - 当前高风险点与已知坑
3. 生成本会话首轮行动建议（不超过 5 条）。

### B) Session End（经验进化）
1. 总结本次会话的有效改动、故障根因、验证结果。
2. 仅沉淀“可复用经验”到 `SESSION_EVOLUTION.md`：
   - 可复现排障路径
   - 稳定修复策略
   - 防回归检查项
3. 更新 `PROJECT_BRIEF.md` 中的“当前状态/活跃风险/下一步”。

### C) Handoff（跨工具/跨模型交接）
1. 读取已有上下文文件。
2. 输出一段可以复制给下一个模型或工具的 handoff：
   - 当前目标
   - 已完成事项
   - 未完成事项
   - 关键文件
   - 验证结果
   - 注意事项

## Missing File Templates

If `PROJECT_BRIEF.md` is missing, create:

```md
# Project Brief

## Project Goal
- 

## Current Status
- 

## Key Modules
- 

## Common Commands
- Install:
- Run:
- Test:
- Build:

## Active Risks
- 

## Next Steps
- 
```

If `SESSION_EVOLUTION.md` is missing, create:

```md
# Session Evolution

## Reusable Lessons
- 

## Debugging Playbooks
- 

## Stable Fix Patterns
- 

## Regression Checks
- 

## Handoff Notes
- 
```

## Guardrails
- 不自动提交、不自动推送、不自动改远端生产配置。
- 只写与项目长期协作相关的信息，避免一次性噪音。
- 若信息不足，先给最小模板，再继续执行。
- 只沉淀已经验证或高置信度的经验；低置信度内容必须标记 `待确认`。

## Output Format
始终输出三段：
1. `Quick Context`
2. `Action Plan`
3. `Evolution Notes`
