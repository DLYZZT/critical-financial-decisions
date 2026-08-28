# Critical Financial Decisions Skill

孙割财务决策 Skill：专门处理“钱付得起，但到底该不该给”的高影响决定。

本项目根据孙割财务决策核心思路整理为可复用、可审计的通用决策框架。“孙割同款”仅为网络化描述；本项目与孙宇晨或任何其他现实人物、机构不存在关联，也不把虚构案例当作对现实人物的事实陈述。

## 设计目标

- 面向普通家庭、创业者、富裕家庭、高净值人士和家族办公室；
- 不按身份拍脑袋，而按财务脆弱度与结构重大性切换审查模式；
- 强制区分“付得起”和“该不该做”；
- 对大额消费、亲友借款、赠与、投资、担保、房产、婚姻财产、生育医疗、企业纾困和继承给出统一决策流程；
- 输出可以直接交给律师、税务师、银行、信托顾问或财务负责人。

## 目录

```text
critical-financial-decisions/
├── SKILL.md
├── README.md
├── references/
│   ├── wealth-modes.md
│   ├── red-flags-and-controls.md
│   ├── scenario-playbooks.md
│   └── legal-tax-research.md
├── assets/
│   ├── decision-report-template.md
│   └── decision-record.schema.json
├── examples/
│   ├── ordinary-household-family-loan.md
│   ├── affluent-family-property.md
│   └── uhnw-relationship-transfer.md
└── evals/
    └── cases.json
```

## 安装

### npx skills（推荐）

本仓库根目录包含标准 `SKILL.md`，可以被 [`skills`](https://github.com/vercel-labs/skills) CLI 直接发现和安装。

在已克隆的仓库目录中安装：

```bash
npx skills add . --skill critical-financial-decisions
```

只安装到 Codex，并跳过交互确认：

```bash
npx skills add . --skill critical-financial-decisions -a codex -y
```

全局安装到 Codex：

```bash
npx skills add . --skill critical-financial-decisions -a codex -g -y
```

也可以直接从 GitHub 远程安装：

```bash
npx skills add DLYZZT/critical-financial-decisions --skill critical-financial-decisions -a codex -g -y
```

安装前仅检查是否能正确发现技能：

```bash
npx skills add . --list
```

### Codex

复制到个人技能目录：

```bash
mkdir -p ~/.agents/skills
cp -R critical-financial-decisions ~/.agents/skills/
```

也可以放到项目的：

```text
<repo>/.agents/skills/critical-financial-decisions/
```

### Claude Code

复制到：

```bash
mkdir -p ~/.claude/skills
cp -R critical-financial-decisions ~/.claude/skills/
```

### 其他 Agent Skills 客户端

把整个目录放入该客户端的技能搜索路径。不要只复制 `SKILL.md`，否则场景手册、模板和 JSON Schema 无法按需读取。

## 调用示例

```text
请使用 critical-financial-decisions 分析：
我税后月收入 3 万，存款 20 万，父母希望我为弟弟的 80 万经营贷担保。我是否应该签？
```

```text
请使用 critical-financial-decisions 进入家族办公室模式：
这笔跨境赠与不影响净值，但收款人要求打到其亲属公司，请给出做/不做结论和最小结构。
```

## 维护建议

- 法律、税务、监管和产品规则不要写死在技能中；运行时按辖区检索最新官方来源；
- 将组织自己的金额审批线、双签人、受托机构和法务联系人补充到单独的内部参考文件；
- 使用 `evals/cases.json` 回归测试，避免模型重新出现“反正付得起就给”“无法判断所以不下结论”等问题。
