# ei-skill

个人效能工具集 —— 面向程序员的 Claude Code Skills 仓库。

## 什么是 ei-skill？

`ei-skill` 是我在日常工程工作中逐步积累的 Claude Code Skills 集合。每个
Skill 针对一个具体的工程效能痛点，将最佳实践、结构化推理和可复用模板封装
为可直接安装的模块。

核心理念：**让 AI 不仅执行任务，更按照经过验证的专业方法论来执行任务。**

## 已有 Skills

| Skill | 描述 | 触发场景 |
|-------|------|----------|
| [milestone-builder](./milestone-builder/) | 将项目需求转化为成果驱动的里程碑、Checklist、Exit Criteria 和 Evidence Requirements | "帮我制定里程碑计划"、"分解这个 PRD 为里程碑"、"review 我的 milestone" |

## 快速安装

**环境要求**：[Claude Code](https://docs.anthropic.com/en/docs/claude-code) + Git

### 一行命令安装

```bash
# 安装单个 Skill 到当前项目（以 milestone-builder 为例）
git clone --depth 1 https://github.com/Aaron-cdx/ei-skill.git /tmp/ei-skill && mkdir -p .claude/skills && cp -r /tmp/ei-skill/milestone-builder .claude/skills/ && rm -rf /tmp/ei-skill
```

```bash
# 安装单个 Skill 到全局（所有项目可用）
git clone --depth 1 https://github.com/Aaron-cdx/ei-skill.git /tmp/ei-skill && mkdir -p ~/.claude/skills && cp -r /tmp/ei-skill/milestone-builder ~/.claude/skills/ && rm -rf /tmp/ei-skill
```

### PowerShell (Windows)

```powershell
git clone --depth 1 https://github.com/Aaron-cdx/ei-skill.git $env:TEMP/ei-skill; mkdir -p .claude/skills; cp -r $env:TEMP/ei-skill/milestone-builder .claude/skills/; rm -r -fo $env:TEMP/ei-skill
```

### 验证

在 Claude Code 中输入 `/milestone-builder`，如果 Skill 被识别即安装成功。

## 仓库结构

```
ei-skill/
├── README.md                   ← 本文件
├── milestone-builder/          ← Skill: 里程碑构建器
│   ├── SKILL.md                ← Skill 主指令文件
│   ├── README.md               ← Skill 详细文档
│   ├── references/             ← 渐进式加载的参考文档
│   │   ├── milestone-methodology.md
│   │   ├── milestone-categories.md
│   │   └── anti-patterns.md
│   └── examples/               ← 完整输入/输出范例
│       ├── example-ai-agent-platform.md
│       └── example-payment-gateway.md
└── (future skills...)
```

## Skills 说明

### milestone-builder

将模糊的项目目标转化为可执行、可验收、可跟踪的里程碑体系。

**适用人群**：PIC、Tech Lead、Engineering Manager、TPM、PM

**核心能力**：
- 12 步结构化推理流程（从 Success Definition 到 Quality Review）
- 6-Gate 里程碑分类体系（Decision → Risk → Capability → Integration → Validation → Production）
- 三层输出结构：Milestone (Outcome) + Checklist (Activities) + Evidence (Proof)
- 内置 8 种反模式检测与自动修复
- 强制执行风险前置原则（Risk First Planning）

**方法论基础**：
> Milestones are achievements, not activities.
> 每个里程碑 = 关键成果 + 风险被消灭 + 价值被验证

详见 [milestone-builder/README.md](./milestone-builder/README.md)。

## 贡献与规划

如果你有好的 Skill 想法或改进建议，欢迎提 Issue。

计划中的 Skills：
- `code-review-checklist` — 基于项目上下文生成定制化 Code Review Checklist
- `tech-spec-builder` — 从一句话需求生成结构化技术方案文档
- `oncall-handbook` — 事故响应流程与事后复盘模板

## License

MIT
