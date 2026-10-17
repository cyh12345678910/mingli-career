# 贡献指南

感谢你想为 mingli-career 做出贡献！本仓库是一个 **Skill 编排层 + 知识库**（纯 Markdown），底层排盘和判断由 liki 引擎（ml8s/liki）完成。

## 贡献类型

| 类型 | 适合什么 | 建议 |
|------|----------|------|
| **Bug 修复** | 断语逻辑错误、古籍出处错误、城市归属错误 | 附复现步骤（具体出生信息 + 哪一条断语有问题） |
| **内容补充** | 新增案例、扩充城市映射、补古籍出处 | 附核校原文（或 `⚠️ 待核` 标记） |
| **文档改进** | README 不清楚、术语说明不够 | 改完提 PR 就行 |
| **新 domain** | 新的职业决策维度 | 先提 Issue 讨论 scope，免得浪费时间 |

## 开发环境

本仓库不需要构建——它全是 Markdown 文件。

```bash
# 克隆
git clone https://github.com/cyh12345678910/mingli-career.git
cd mingli-career

# 可选：用 liki 引擎验证断语逻辑
npx skills add ml8s/liki -y

# 可选：跑 markdown lint（需要安装 markdownlint-cli）
npm install -g markdownlint-cli
markdownlint '**/*.md'
```

## PR 模板

见 `.github/PULL_REQUEST_TEMPLATE.md`。基本要求：

1. **改动说明**：你改了什么、为什么
2. **断语依据**：如果涉及命理断语，说明依据的古籍原文或 liki 规则表条目
3. **城市/出处类改动**：必须附核校来源，存疑处标 `⚠️ 待核`

## 红线

以下改动建议先提 Issue 讨论：

- **排盘口径相关**（比如改喜用神判断逻辑、改大运起法）——这些应该由 liki 引擎决定
- **删除/重排整个 domains/** 结构——会影响 Skill 的编排流程
- **扩展到八字/紫微之外的体系**（奇门、六爻等）——先讨论 scope

## 测试策略

本仓库没有代码，"测试"就是 **回归快照**：

- `tests/expected-outcomes.md` 里有 3 个固定八字的"预期输出"
- 改 `domains/` 文件后，Agent 应该能对这 3 个八字产出和快照一致（或合理收敛）的结果
- 如果 Agent 输出和快照差距很大，检查你改的 domain 是否引入了新的误导性指令

## 报告 Issue

好的 Issue 格式：

```
标题：[Bug] XX 断语与实际不符

复现步骤：
1. 出生信息：1990-05-20 12:00 北京出生，男
2. 操作：问"我适合什么行业"
3. 实际输出：XXX
4. 预期输出：XXX

依据：
- liki assertion_id：BZ-CAREER-023
- 古籍原文：《滴天髓·XX》"XXX"
```

## 行为准则

- 保持尊重
- 命理是传统文化，不同流派论法不同，不要用"我的流派就是对的"来否定别人
- 断语出处存疑的标 `⚠️ 待核` 就好，不用强行定论
