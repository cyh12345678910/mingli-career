# 命理职业决策（mingli-career）

一个基于八字排盘的 **TRAE / Claude Code 技能（Skill）**，把"排盘 → 喜用神 → 职业方向 → 岗位契合 → 城市/方位推荐 → 行动时机"整条链路封装成可复用的决策助手。

> 命理结论为传统文化视角，仅供参考，不构成职业、投资或医疗建议。

## 它能做什么

- **职业方向**：根据十神结构判断适合的技术型 / 管理型 / 自主型路线
- **岗位契合度**：把岗位性质映射到十神（如"测试=印忌、研发=食伤+偏印用"），判断当前岗位是否"顺势"
- **城市/方位推荐**：内置「喜用神 → 方位 → 城市五行」映射表，推荐发展城市并提示避忌城市
- **行动时机**：结合大运流年给出"攻/守"窗口（何时内转、何时跳槽、何时忌动）

## 安装

```bash
# 1. 先安装排盘引擎 liki-bazi
npx skills add ml8s/liki/skills/liki-bazi -y

# 2. 安装本技能
# 方式 A：直接 clone 到技能目录
git clone https://github.com/<your-name>/mingli-career.git .trae/skills/mingli-career

# 方式 B：复制 SKILL.md 与 domains/ references/ 到 .trae/skills/mingli-career/
```

## 使用

在 TRAE / Claude Code 中直接对话即可：

```
算八字，1990-05-20 12:00 北京出生，男
→ 我适合什么行业？创业还是打工？
→ 我适合往哪个方向发展？哪些城市和我五行更合？
→ 今年适合跳槽还是内转？
```

## 目录结构

```
mingli-career/
├── SKILL.md              # 技能主入口
├── README.md
├── LICENSE               # MIT
├── domains/
│   ├── paipan.md         # 排盘流程（依赖 liki-bazi）
│   ├── career.md         # 事业方向分析
│   ├── city.md           # 城市/方位推荐流程
│   └── timing.md         # 时机节奏（大运流年窗口）
└── references/
    └── wuxing-city.md    # 五行 → 方位 → 城市映射表
```

## 依赖

- [liki-bazi](https://github.com/ml8s/liki)（排盘引擎，MIT）——本技能不自行排盘，复用其天文历算引擎与断语库

## 致谢

- 排盘引擎：[ml8s/liki](https://github.com/ml8s/liki)（MIT）
- 城市五行映射为传统文化视角的归纳整理，具体论法因流派而异

## License

[MIT](LICENSE)
