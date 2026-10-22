# Skills

我的 Agent 技能库（个人维护），日常用于 AI 应用开发。

- **是什么**：11 个可被 AI 编码代理自动加载的 skill，把开发纪律和上线后的排障经验固化成可复用的流程
- **解决什么**：让 Agent 不再「想到哪写到哪」—— 先出计划、测试先行、提交前审查、声称完成前先验证；并沉淀 LLM 应用线上问题的定位方法
- **怎么用**：把对应目录复制到你的代理技能库（见下方安装），或直接读 `SKILL.md` 当作排查清单

一套给 AI 编码代理（Hermes / Claude Code / Codex 等）用的**工作流技能集**：把「先想清楚 → 写计划 → 测试先行 → 系统化排查 → 提交前审查 → 声称完成前先验证」这套纪律固化成可被代理自动加载的 skill。

## 技能清单

| 技能 | 作用 |
|---|---|
| `long-running-agent-timeouts` | 长任务 Agent 的超时、状态回传与降级 —— 假死判定、运行时卡死取证、会话记忆修复、幂等重试 |
| `automation-truth-verification` | 自动化任务的真实性核验 —— 回执级证据分级、`verified` 标记、校准探针对账、连续失败止损 |
| `llm-platform-api-ops` | 平台 Console API 批量运维 —— 鉴权收口、批量上限与分页、写后回读校验、快照回滚、草稿与发布的生效时机 |
| `using-superpowers` | 会话开始时的总入口：怎么找技能、什么时候必须先调用技能 |
| `brainstorming` | 任何创作/新功能/方案之前先做结构化头脑风暴，产出设计稿再动手 |
| `writing-plans` | 有需求但还没碰代码时，把需求写成多步可执行计划 |
| `plan` | 计划模式：把可执行计划写到 `.hermes/plans/`，只规划不执行 |
| `test-driven-development` | 强制 RED → GREEN → REFACTOR，先写测试再写实现 |
| `systematic-debugging` | 四阶段根因调试：先理解 bug，再改代码 |
| `requesting-code-review` | 提交前审查：安全扫描、质量门、自动修复 |
| `verification-before-completion` | 声称「完成/修好了/测试过了」之前，必须先跑验证命令 |

## 目录结构

```
skills/
├── long-running-agent-timeouts/
├── automation-truth-verification/
├── llm-platform-api-ops/
├── brainstorming/            # 含 scripts/（可视化配套）与提示词模板
├── plan/
├── requesting-code-review/
├── systematic-debugging/
├── test-driven-development/
├── using-superpowers/        # 含 references/*-tools.md 各平台工具映射
├── verification-before-completion/
└── writing-plans/
```

每个技能目录下是一个 `SKILL.md`（YAML frontmatter + 正文），可附带 `references/`、`scripts/`、`templates/`、`assets/`。

## 安装

把技能目录复制到你的代理技能库即可（以 Hermes 为例）：

```bash
mkdir -p "$HERMES_HOME/skills/software-development"
cp -r skills/* "$HERMES_HOME/skills/software-development/"
```

装完重载技能清单（Hermes：`/reload-skills` 或开新会话），代理才会按新描述自动触发。

## 说明

- `references/` 下是各代理平台的工具映射，按你用的平台取对应文件
- `brainstorming/scripts/` 是本地可视化配套（Node 起的轻服务），不需要可整目录删掉，不影响 SKILL.md 的流程
- 技能正文为英文，便于代理精确匹配触发条件；本 README 为中文

## 许可

本仓库按 **MIT** 许可分发，全文见 [LICENSE](LICENSE)。

`LICENSE` 中同时保留了本仓库所引用第三方技能的原始版权声明；再分发或二次修改时请一并保留。
