---
name: multi-agent-researcher
description: Use when 需要执行深度调研任务：市场分析、竞品研究、用户洞察、项目可行性等。一键触发10Agent协作：主编调度→5Scout并行侦察→Analyst+Critic整合质疑→Writer撰写→2Reviewer评审定稿，循环迭代直到报告达标。
version: 1.1.0
author: Muru AI
license: MIT
platforms: [linux, macos, windows]
type: workflow
metadata:
  hermes:
    tags: [multi-agent, research, market-analysis, competitor-analysis, user-insight, workflow]
    related_skills: [skill-factory, multi-agent-skill-factory, multi-agent-ecommerce, multi-agent-ui-styles]
business_domain: 市场研究 · 商业分析
complexity: high
status: production
---

# Multi-Agent Research — 多Agent协作深度调研系统

> 10个专业Agent，4阶段流水线，让AI替你完成深度商业调研。

## 工作流概览

```
用户说"帮我调研一下XX市场"
         ↓
主编接收任务，解析调研命题
         ↓
阶段一：并行侦察（5个Scout）
  Scout-A → 市场数据包
  Scout-B → 竞品数据包
  Scout-C → 用户数据包
  Scout-D → 客户数据包
  Scout-E → 案例数据包
         ↓
阶段二：分析整合（Analyst + Critic）
  Analyst → 市场洞察报告
  Critic → 风险与机会矩阵
         ↓
阶段三：报告撰写（Writer）
  Writer → 完整报告初稿
         ↓
阶段四：评审定稿（Reviewer-A + Reviewer-B）
  Reviewer-A → 数据/逻辑评审
  Reviewer-B → 可行性评审
         ↓
      ┌── 评审通过？ ──┐
      ↓              ↓
     ✅            ❌
  定稿        Writer修订
                   ↑
            （循环直到达标）
```

## Agent团队配置（10个Agent）

| Agent | 身份 | 核心职责 |
|-------|------|---------|
| 主编 | 首席研究员 | 解析命题、调度Agent、组装报告 |
| Scout-A | 市场分析师 | 市场规模、增长、政策环境 |
| Scout-B | 竞品研究员 | 竞争格局、竞品优劣势 |
| Scout-C | 用户研究员 | 消费者行为、决策路径 |
| Scout-D | 客户分析师 | 客户画像、忠诚度分析 |
| Scout-E | 案例研究员 | 成功/失败案例参照 |
| Analyst | 洞察整合师 | 多源整合、洞察提炼 |
| Critic | 质疑评审官 | 挑战假设、风险评估 |
| Writer | 报告撰写师 | 完整报告输出 |
| Reviewer-A | 数据审计官 | 数据准确性、逻辑性 |
| Reviewer-B | 落地评估官 | 可行性、创新性评估 |

详细Agent模板见 [references/agents.md](references/agents.md)。

## 四阶段流水线

| 阶段 | Agent | 时长 | 输出 |
|------|-------|------|------|
| 阶段一 | Scout A-E（并行） | 2-3h | 5个数据包 |
| 阶段二 | Analyst + Critic | 2-3h | 洞察报告+风险矩阵 |
| 阶段三 | Writer | 2-3h | 报告初稿 |
| 阶段四 | Reviewer-A + B | 1-2h | 评审意见 |

**总时长：6-10小时（视复杂度调整）**

详细流程见 [references/pipeline-multi-agent.md](references/pipeline-multi-agent.md)。

## 调研类型配置

| 调研类型 | Scout配置 | 适用场景 |
|----------|-----------|---------|
| 通用商业调研 | A市场+B竞品+C用户+D客户+E案例 | 新项目立项 |
| 产品市场调研 | A需求+B竞品+C用户+D反馈+E产品案例 | 新产品开发 |
| 竞品研究 | A份额+B产品+C评价+D动机+E失败案例 | 竞争策略制定 |
| 用户研究 | A画像+B行为+C需求+D流失+E高满意案例 | 用户体验优化 |

详细Scout模板见 [references/scouting-templates.md](references/scouting-templates.md)。

## 触发词

**完整调研触发：**
- "调研一下XX市场"
- "帮我做竞品分析"
- "用户研究"
- "项目可行性调研"
- "/调研 [调研主题]"

**快速查询：**
- "XX行业市场规模"
- "竞品对比"

## 输出物

| 交付物 | 格式 | 说明 |
|--------|------|------|
| Scout数据包 | YAML | 原始素材存档 |
| 市场洞察报告 | Markdown | 内部决策参考 |
| 完整调研报告 | HTML/PDF | 对外汇报 |
| 评审问题清单 | Markdown | 修订依据 |

## Not For
- 实时新闻查询（用web search工具）
- 法律/财务专业意见（需专业人士）
- 一次性的简单问题

## 目录结构

```
multi-agent-research/
├── SKILL.md                     ← 主入口（主编调度）
├── grading.json                 ← 审核评分结果
└── references/
    ├── agents.md                  ← 10个Agent系统提示词
    ├── pipeline-multi-agent.md    ← 四阶段流水线详解
    ├── scouting-templates.md      ← Scout A-E详细模板
    ├── report-templates.md        ← Writer模板+报告结构
    ├── test_pool.md              ← 测试用例池
    ├── failure_case_log.md       ← 失败案例追踪
    └── self-review-template.md   ← 自审模板
```

## 错误处理

### 主编调度异常
| 异常场景 | 处理方式 |
|----------|----------|
| Scout数据包缺失 | 追问用户补充背景信息，最多3次 |
| 某Scout超时 | 并行超时2分钟，自动跳过，标记数据缺口 |
| 数据矛盾 | 标注矛盾点，由Analyst判断采用哪个数据源 |
| 评审不通过（3轮） | 交付当前版本，列出剩余问题清单 |

### 边界场景处理
| 场景 | 处理方式 |
|------|----------|
| 调研主题模糊（"帮我调研一下"） | 主编追问：行业/产品/竞品/用户？调研深度？ |
| 超出范围（法律/财务/实时新闻） | 明确说明限制，建议转介专业人士 |
| 数据不足 | 标注数据缺口，说明估算或假设前提 |
| 调研对象无公开信息 | 说明调研局限，建议实地访谈补充 |

### Not For
- 实时新闻查询（用web search工具）
- 法律/财务专业意见（需专业人士）
- 一次性的简单问题

## 验证清单

- [ ] description以"Use when"开头
- [ ] frontmatter包含完整字段（含type: workflow）
- [ ] references/目录包含agents.md + pipeline-multi-agent.md
- [ ] test_pool.md在references/目录下
- [ ] 10个Agent角色定义清晰
- [ ] 4阶段流程覆盖完整
- [ ] 错误处理机制完整
- [ ] 边界场景覆盖
