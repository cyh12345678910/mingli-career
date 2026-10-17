# Mingli Career Skill (Bazi + Ziwei Doushu Dual-System)

> An AI assistant Skill that chains "Bazi + Ziwei Doushu charting → favorable god analysis → career direction → job match → city selection → timing → relationships → health" into a reusable career-decision helper.
>
> All conclusions are traditional Chinese metaphysics perspectives. **Not financial, legal, or medical advice.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

---

## What It Does

| Capability | Description |
|------------|-------------|
| **Dual-system synthesis** | Bazi (Four Pillars) + Ziwei Doushu (Purple Star Astrology) calculated independently, then synthesized with evidence-strength rules |
| **Traceable assertions** | Every assertion includes `assertion_id` + classical source (e.g., *Han Shui Tong Shen* / *Ziwei Doushu Quanshu*) |
| **Job-skill mapping** | Original "Ten Gods → job nature" and "Ziwei main star → job trait" mappings |
| **City/f方位recommendation** | Built-in 55+ city five-element mapping with school-of-thought divergence markers |
| **Timing rhythm** | Bazi Dayun + Ziwei Da Xian dual-track, year-by-year windows (when to move, when to hold) |
| **Relationship compatibility** | Colleague/partner/subordinate chart matching (with anti-abuse safeguards) |
| **Health cues** | Five elements → zang-fu organs + Ziwei disease palace + killing-star convergence |

## Architecture

```
┌────────────────────────────────────────────────────┐
│       mingli-career (Skill — all Markdown)          │
│                                                     │
│  domains/        Orchestration flow                 │
│  references/     Knowledge base                      │
│  examples/       Real-world case studies            │
│                                                     │
│  ┌──────────────┐   ┌─────────────────────────┐    │
│  │ liki engine   │   │ MCP server               │    │
│  │ (ml8s/liki,   │   │ engine-mcp + counsel-mcp  │    │
│  │  MIT)         │   │ side=bazi/ziwei           │    │
│  │ 829 rules     │   │ topic=career/health/...   │    │
│  └──────────────┘   └─────────────────────────┘    │
└────────────────────────────────────────────────────┘
```

## Quick Start

### 1. Install liki engine (required)

```bash
npx skills add ml8s/liki -y
```

liki is the underlying metaphysics engine (Go for charting + Python for judgment, 829 rule truth tables).

### 2. Install mingli-career

```bash
git clone https://github.com/cyh12345678910/mingli-career.git ~/.trae/skills/mingli-career
```

### 3. Use

In TRAE / Claude Code / Cursor, just ask:

```
Help me analyze: born 1992-03-15 14:30 in Xi'an, male
→ Should I stay in R&D or switch to data?
→ Which cities suit me better — Shenzhen or Xi'an?
→ When should I move in the next 2 years?
```

## Directory Structure

```
mingli-career/
├── SKILL.md
├── README.md / README.en.md
├── LICENSE
├── CONTRIBUTING.md
├── domains/
│   ├── paipan.md              # Charting flow (Bazi + Ziwei)
│   ├── career.md              # Bazi career analysis
│   ├── ziwei-career.md        # Ziwei career analysis
│   ├── timing.md              # Timing rhythm (Dayun + Da Xian)
│   ├── city.md                # City/方位recommendation
│   ├── relationship.md        # Relationship compatibility
│   └── health.md              # Health cues
├── references/
│   ├── classical-citations.md # Classical source table
│   ├── ziwei-career-patterns.md # Ziwei career patterns
│   └── wuxing-city.md         # City five-element mapping (55 cities)
├── examples/
│   ├── chen-hui.md            # Case: BYD engineer career transition
│   ├── zhang-ceo.md           # Case: Startup CEO analysis
│   └── li-junior.md           # Case: Fresh grad career advice
└── tests/
    └── expected-outcomes.md   # Regression snapshot
```

## License

| Component | License |
|-----------|---------|
| mingli-career | MIT |
| liki engine (ml8s/liki) | MIT |
| Classical texts (Di Tian Sui, Ziwei Doushu Quanshu, etc.) | Public Domain |
| Ni Haixia *Tian Ji* original words | CC BY-NC-SA 4.0 |

## Disclaimer

All conclusions are conditional interpretations from traditional Chinese metaphysics. Not medical, legal, financial, or major life-decision advice.

## Acknowledgments

- **liki engine**: [ml8s/liki](https://github.com/ml8s/liki) (Go charting + Python judgment, 829 rule truth tables)
- **Reference project**: [Renhuai123/ziwei-doushu](https://github.com/Renhuai123/ziwei-doushu)
- **Classical sources**: *Di Tian Sui*, *Ziwei Doushu Quanshu*, *Yuan Hai Zi Ping*, *San Ming Tong Hui*, *Wu Xing Da Yi*, and others
