---
name: critical-thinking-askingq
description: |
  批判性思维分析框架，基于《学会提问》(Asking the Right Questions) 的核心思维模型。
  当用户需要评估论点、分析文章/新闻/观点、识别谬误、判断证据质量、做重要决策、
  或审视某个主张是否可信时，必须激活此 skill。
  触发关键词：帮我分析这个观点、这个说法靠谱吗、这篇文章有道理吗、我该怎么看待这件事、
  论证是否成立、反驳这个观点、证据充分吗、这个结论合理吗、帮我批判性地看待。
  只要用户需要对任何信息进行深度批判性评估，就应加载此 skill。
version: 1.0.0
author: Claude (Anthropic) for NousResearch/hermes-agent
license: MIT
metadata:
  hermes:
    tags: [CriticalThinking, Analysis, Reasoning, Logic, Argumentation, 批判性思维]
    related_skills: []
---

# 批判性思维框架（Asking the Right Questions）

本 skill 将 Neil Browne & Stuart Keeley《学会提问》的核心方法论转化为可操作的分析流程。目标：帮助用户像**淘金者**一样主动筛选信息，而非像海绵一样被动吸收。

---

## When to Use

任何涉及以下场景时加载本 skill：

- 评估一篇文章、新闻报道、社交媒体内容的可信度
- 分析某个论证或主张是否成立
- 识别论证中的逻辑谬误
- 判断支撑论点的证据质量
- 帮助用户做重要决策前梳理论据
- 用户明确要求"批判性分析"某内容

---

## Quick Reference

| 分析维度 | 核心追问 | 详细步骤 |
|---------|---------|---------|
| 结论识别 | 作者想证明什么？ | 见 `references/ten-steps.md` §1 |
| 理由识别 | 给出了哪些支撑？ | 见 `references/ten-steps.md` §2 |
| 假设挖掘 | 隐含了哪些前提？ | 见 `references/ten-steps.md` §3 |
| 谬误识别 | 推理是否有效？ | 见 `references/fallacies.md` |
| 证据评估 | 证据有多可靠？ | 见 `references/ten-steps.md` §5 |
| 歧义识别 | 关键词是否模糊？ | 见 `references/ten-steps.md` §6 |
| 信息完整性 | 有没有被隐藏的信息？ | 见 `references/ten-steps.md` §7 |
| 替代原因 | 还有哪些可能解释？ | 见 `references/ten-steps.md` §8 |
| 统计审查 | 数字真的说明了问题吗？ | 见 `references/ten-steps.md` §9 |
| 形成判断 | 我应该接受还是拒绝？ | 见 `references/ten-steps.md` §10 |

---

## Procedure

### 场景一：分析文章 / 新闻

1. **加载** `references/ten-steps.md`，按第 1 → 2 → 3 → 4 → 5 步依次执行
2. 对每一步，在文本中寻找对应要素
3. 给出综合评价：论证强度（强 / 中 / 弱）+ 主要问题（≤3条）

### 场景二：评估具体主张

1. 重点走第 3（假设）、第 5（证据）、第 8（替代原因）三步
2. 加载 `references/fallacies.md` 快速比对谬误类型
3. 输出：假设清单 + 证据评级 + 替代解释列表

### 场景三：辅助用户决策

1. 加载 `references/ten-steps.md` 中的**决策框架模板**（§10）
2. 填写各项，呈现各方依据
3. **不替用户做决定**，只清晰呈现结构

### 场景四：快速谬误识别

1. 加载 `references/fallacies.md`
2. 逐一比对，输出：谬误名称 + 解释 + 改进建议

---

## Pitfalls

- **不要替用户得出结论**——批判性思维的目标是帮用户看清，而非裁判
- **不要只找缺点**——也要指出论证中有力的部分，保持平衡
- **不要混淆描述性与规定性论题**——两者分析路径不同（详见 `references/ten-steps.md` §1）
- **统计数据陷阱**：百分比必须追问基数，"平均值"必须追问是均值/中位数/众数
- **相关 ≠ 因果**：这是最常见的描述性假设错误，见 `references/ten-steps.md` §8

---

## Verification

分析完成后确认：

- [ ] 已明确区分结论与理由
- [ ] 已识别至少1个隐含假设
- [ ] 已检查常见谬误类型
- [ ] 已评估主要证据的可靠性
- [ ] 已提出至少1个替代解释（如适用）
- [ ] 输出结构清晰，用户可独立核查推理过程

---

## Output Format

- **简洁场景**：直接指出结论、关键假设、最主要的问题（≤3点），prose 格式
- **深度分析**：按需加载参考文件，逐项展开，最后给综合判断
- **决策辅助**：填写决策框架模板，以结构化形式呈现
- **语气**：提问而非裁判；用"这里存在一个值得注意的假设……"而非"这个论证是错的"
