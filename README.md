# 命理职业决策 Skill（八字 + 紫微斗数双体系）

> 把"八字 + 紫微排盘 → 喜用神/格局 → 职业方向 → 岗位契合 → 城市方位 → 行动时机 → 人际关系 → 健康提示"整条链路封装成可复用的决策助手。
>
> 命理结论为传统文化视角，仅供参考，不构成职业、投资或医疗建议。

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Bazi](https://img.shields.io/badge/八字-✓-blue)]()
[![Ziwei](https://img.shields.io/badge/紫微斗数-✓-purple)]()
[![Liki](https://img.shields.io/badge/引擎-liki-emerald)]()

---

## ✨ 核心亮点

| 能力 | 说明 |
|------|------|
| **双体系合参** | 八字（四柱十神）+ 紫微斗数（十四主星、四化、格局）并列计算，分侧定案，裁决规则遵循 liki 引擎 |
| **断语可溯源** | 每条断语标注经典出处（《滴天髓》《紫微斗数全书》等），Agent 输出时自动附带 |
| **岗位契合度** | 原创"十神→岗位性质""紫微主星→岗位特质"映射，直接回答"这个岗位我适不适合" |
| **城市方位推荐** | 内置 55+ 城市五行归属表，含流派分歧标注（如西安论金还是土） |
| **时机节奏** | 八字大运 + 紫微大限双轨，逐年窗口（何时内转、何时跳槽、何时忌动） |
| **人际关系合盘** | 同事/合伙人/下属的命理合参，避免"合盘不好就离职"的滥用 |
| **健康提示** | 五行→脏腑 + 紫微疾厄宫 + 杀星集中地支→脏腑，均为职业辅助维度 |

---

## 🏗️ 架构

```
┌─────────────────────────────────────────────────────────┐
│                  mingli-career (Skill)                  │
│                                                         │
│  domains/          编排层（纯 Markdown，不写代码）       │
│  ├── paipan.md     排盘流程（八字+紫微）                 │
│  ├── career.md     八字职业分析                          │
│  ├── ziwei-career.md 紫微职业分析                        │
│  ├── timing.md     时机节奏（大运+大限双轨）             │
│  ├── city.md       城市方位推荐                          │
│  ├── relationship.md 合盘/人际关系                        │
│  └── health.md     健康提示                              │
│                                                         │
│  references/       知识库                                │
│  ├── classical-citations.md 古籍出处表                   │
│  ├── ziwei-career-patterns.md 紫微格局库                 │
│  └── wuxing-city.md 城市五行表（55 城）                   │
│                                                         │
│  examples/         真实案例（3 个）                      │
│                                                         │
│  ┌─────────────────┐  ┌──────────────────────────┐      │
│  │ liki 引擎        │  │ MCP Server              │      │
│  │ (ml8s/liki, MIT) │  │ engine-mcp + counsel-mcp│      │
│  │ Go 排盘 + Python │  │ side=bazi/ziwei          │      │
│  │ 判断层（829 条   │  │ topic=career/health/...  │      │
│  │  规则真值表）    │  │ assertion_id + 经典出处   │      │
│  └─────────────────┘  └──────────────────────────┘      │
└─────────────────────────────────────────────────────────┘
```

---

## 🚀 快速开始

### 1. 安装 liki 引擎（必须）

```bash
npx skills add ml8s/liki -y
```

liki 是本 Skill 的底层命理引擎（Go 排盘 + Python 判断层，829 条规则真值表，每条断语标注经典出处）。

### 2. 安装 mingli-career

```bash
# 方式 A：直接 clone 到技能目录
git clone https://github.com/cyh12345678910/mingli-career.git ~/.trae/skills/mingli-career

# 方式 B：复制 SKILL.md + domains/ + references/ 到技能目录
```

### 3. 使用

在 TRAE / Claude Code / Cursor 中直接对话：

```
帮我算一下，1992-03-15 14:30 西安出生，男
→ 我现在在比亚迪做研发，适合继续留还是跳槽？
→ 我适合去哪些城市？深圳和西安哪个好？
→ 这两年什么时候适合动？
→ 我的合盘适合和什么样的人合伙？
```

---

## 📂 目录结构

```
mingli-career/
├── SKILL.md                          # 技能主入口（必读）
├── README.md / README.en.md          # 中英文说明
├── LICENSE                           # MIT
├── CONTRIBUTING.md                   # 贡献指南
├── .github/
│   ├── workflows/ci.yml              # CI：markdown lint + 回归快照
│   └── PULL_REQUEST_TEMPLATE.md      # PR 模板
├── domains/                          # 领域流程（Agent 按此编排）
│   ├── paipan.md                     # 八字 + 紫微双体系排盘流程
│   ├── career.md                     # 八字职业方向分析（十神→职业）
│   ├── ziwei-career.md               # 紫微职业方向分析（主星/格局→职业）
│   ├── timing.md                     # 时机节奏（八字大运 + 紫微大限）
│   ├── city.md                       # 城市/方位推荐（双体系合参）
│   ├── relationship.md               # 合盘/人际关系分析
│   └── health.md                     # 健康提示（职业辅助维度）
├── references/                       # 知识库（Agent 断语依据）
│   ├── classical-citations.md        # 古籍出处表（十神+紫微格局）
│   ├── ziwei-career-patterns.md      # 紫微职业格局库
│   └── wuxing-city.md                # 城市五行映射表（55 城，含流派标注）
├── examples/                         # 真实案例
│   ├── chen-hui.md                   # 案例 1：比亚迪研发工程师转岗决策
│   ├── zhang-ceo.md                  # 案例 2：创业型 CEO 八字+紫微分析
│   └── li-junior.md                  # 案例 3：应届生职业起步建议
└── tests/                            # 回归快照（防改 domain 文件后逻辑漂移）
    └── expected-outcomes.md
```

---

## 🔓 开源边界

| 内容 | 开源？ | 说明 |
|------|--------|------|
| **domains/** 编排层 | ✅ MIT | 纯 Markdown，定义 Agent 编排流程 |
| **references/** 知识库 | ✅ MIT | 城市映射、古籍出处、格局库——可自由复用 |
| **SKILL.md + README** | ✅ MIT | 文档 |
| **liki 引擎** | ✅ MIT | 底层排盘与判断引擎（ml8s/liki），双体系合参规则由 liki 定义 |
| **断语库/真值表** | ⚠️ 由 liki 提供 | 829 条规则真值表在 liki counsel 层，每条标注经典出处 |
| **倪海厦《天纪》原话** | ❌ 非商用 | 如需单独使用倪师原话，按 CC BY-NC-SA 4.0 处理（见 ziwei-doushu 仓库） |
| **断语出处古籍** | ✅ 公有领域 | 《滴天髓》《紫微斗数全书》等均为古籍公版 |

**一句话**：你可以自由使用本 Skill 的所有 Markdown 编排层和知识库。排盘和判断由 liki 引擎完成（MIT），不需要你自己实现。

---

## 📜 协议

| 组件 | 协议 | 说明 |
|------|------|------|
| mingli-career（本仓库） | [MIT](./LICENSE) | 自由使用、修改、分发、商用 |
| liki 引擎 | MIT | ml8s/liki |
| 断语出处古籍 | Public Domain | 《滴天髓》《紫微斗数全书》《渊海子平》《三命通会》等 |
| 倪海厦《天纪》原话 | CC BY-NC-SA 4.0 | 引用时注明出处，不可单独商用 |

---

## 🗓️ 维护节奏

- **本仓库**：编排层 + 知识库的补充和修订，随开发者节奏更新
- **liki 引擎**：跟随 ml8s/liki 的发版节奏，关注其 CHANGELOG
- **Issue**：会看，但回复可能不及时；带复现步骤（具体出生信息 + 哪一条断语有问题）的 issue 优先处理
- **PR**：欢迎。改动编排层逻辑的，请说明依据；改动古籍出处的，请附上核校原文

---

## 🤝 贡献

详见 [CONTRIBUTING.md](./CONTRIBUTING.md)。

---

## ⚠️ 声明

命理结论为传统文化视角的**条件性解读**，不构成医疗诊断、法律建议、金融投资预测或重大人生决策。使用本 Skill 进行任何决策前，请结合自身实际综合判断。

---

## 🙏 致谢

- **liki 引擎**：[ml8s/liki](https://github.com/ml8s/liki)（Go 排盘 + Python 判断层，829 条规则真值表，每条标注经典出处）
- **古籍来源**：《滴天髓》《子平真诠》《渊海子平》《三命通会》《穷通宝鉴》《紫微斗数全书》《紫微斗数全集》《五行大义》《地理辨正》
- **参考项目**：[Renhuai123/ziwei-doushu](https://github.com/Renhuai123/ziwei-doushu)（倪海厦《天纪》教学体系的紫微斗数排盘系统，开源了 67.5 万命盘 × 13 维解读数据集）
- **倪海厦《天纪》**：紫微斗数部分 1848 条原话，详见 [nihai-tianji-corpus](https://github.com/Renhuai123/nihai-tianji-corpus)

---

## 📮 联系方式

- 提问题、提修复：GitHub Issues
- 交流、讨论：GitHub Discussions
- 欢迎 Star ⭐ 和 Fork 🔀
