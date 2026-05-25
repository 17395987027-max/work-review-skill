# work-review

> 任务复盘 Skill —— 自动从重复失败中提炼教训，写入记忆文档。

## 场景

Agent 执行任务时反复失败、多次换方案、用户持续不满意——这些是"该记一卦"的信号。这个 skill 在任务结束后自动复盘，把教训写进 `CLAUDE.md`，防止下次再踩同一个坑。

## 触发条件

- 同一任务反复 ≥ 2 次，用户仍不满意
- 同一问题尝试 ≥ 3 种方案才解决
- 用户明确表达不满（"太慢了""又错了"等）

## 写入策略

严格控制记忆文档膨胀：

| 规则 | 说明 |
|------|------|
| 每次最多 2 行 | 新陷阱或新命令，其余合并到已有条目 |
| 能合就不增 | 已有类似陷阱则更新原行，不新增 |
| 超 80 行先删 | 写入前检查，必要时删旧补新 |
| 用户确认 | 展示修改计划，用户同意后才写入 |

## 安装

```bash
npx skills add minhlucvan/work-review-skill
```

或手动：

```bash
git clone https://github.com/你的用户名/work-review-skill.git ~/.claude/skills/work-review
```

## 结构

```
work-review/
├── README.md
├── SKILL.md
└── LICENSE
```

## 许可

MIT
