# Project Ramp Evolver Skill

一个用于“项目快速接手 + 会话经验沉淀”的 skill。它会围绕 `PROJECT_BRIEF.md` 和 `SESSION_EVOLUTION.md` 建立可复用上下文，让新会话、新模型或新工具更快进入项目状态。

## 能做什么

- 新会话开始时，快速读取项目目标、关键模块、常用命令和风险
- 会话结束前，沉淀本次排障路径、修复策略和防回归检查
- 跨工具或跨模型交接时，生成简洁 handoff
- 在上下文文件不存在时，创建最小模板

## 使用方式

把本目录作为 skill 安装到支持 skills 的工具中，然后在项目根目录发起：

```text
使用 project-ramp-evolver，帮我快速接手当前项目。
```

会话结束前可以说：

```text
使用 project-ramp-evolver，总结本次会话并更新项目经验。
```

跨工具交接时可以说：

```text
使用 project-ramp-evolver，生成一份给下一个模型的 handoff。
```

## 核心文件

- `PROJECT_BRIEF.md`：项目级稳定背景，例如目标、模块、命令、风险和下一步
- `SESSION_EVOLUTION.md`：跨会话复用经验，例如排障路径、稳定修复策略和回归检查项

## 设计原则

- 不保存聊天流水账，只沉淀可复用经验
- 不写入密钥、客户数据、token 或私有配置值
- 不自动提交、不自动推送、不改生产配置
- 低置信度信息标记为 `待确认`

## 文件

```text
.
├── SKILL.md
├── agents/openai.yaml
├── README.md
├── LICENSE
└── .gitignore
```

## License

MIT
