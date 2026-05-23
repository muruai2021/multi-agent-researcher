# Multi-Agent Research — 多Agent协作深度调研系统

> 10个专业Agent，4阶段流水线，让AI替你完成深度商业调研。

## 概述

Multi-Agent Research 是一个企业级深度调研解决方案。通过主编调度5个Scout并行侦察，Analyst+Critic整合质疑，Writer撰写，2个Reviewer评审定稿，实现从市场分析到可行性评估的全链路覆盖。

**核心特性：**
- 10个专业Agent各司其职
- 4阶段流水线，6-10小时完成深度调研
- 循环迭代直到报告达标
- 支持多种调研类型配置

## 工作流程

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
```

## Agent团队（10个Agent）

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

## 四阶段流水线

| 阶段 | Agent | 时长 | 输出 |
|------|-------|------|------|
| 阶段一 | Scout A-E（并行） | 2-3h | 5个数据包 |
| 阶段二 | Analyst + Critic | 2-3h | 洞察报告+风险矩阵 |
| 阶段三 | Writer | 2-3h | 报告初稿 |
| 阶段四 | Reviewer-A + B | 1-2h | 评审意见 |

**总时长：6-10小时（视复杂度调整）**

## 调研类型配置

| 调研类型 | Scout配置 | 适用场景 |
|----------|-----------|---------|
| 通用商业调研 | A市场+B竞品+C用户+D客户+E案例 | 新项目立项 |
| 产品市场调研 | A需求+B竞品+C用户+D反馈+E产品案例 | 新产品开发 |
| 竞品研究 | A份额+B产品+C评价+D动机+E失败案例 | 竞争策略制定 |
| 用户研究 | A画像+B行为+C需求+D流失+E高满意案例 | 用户体验优化 |

## 触发词

- "调研一下XX市场"
- "帮我做竞品分析"
- "用户研究"
- "/调研 [调研主题]"

## 目录结构

```
multi-agent-research/
├── SKILL.md                  ← 主入口（主编调度）
└── references/
    ├── agents.md               ← 10个Agent系统提示词
    ├── pipeline-multi-agent.md ← 四阶段流水线详解
    ├── scouting-templates.md   ← Scout A-E详细模板
    ├── report-templates.md     ← Writer模板+报告结构
    └── test_pool.md           ← 测试用例池
```

## License

MIT
