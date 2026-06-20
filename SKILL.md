---
name: multi-agent-researcher
description: Use when 需要执行深度调研任务：市场分析、竞品研究、用户洞察、项目可行性等。一键触发11Agent协作（含主编）：主编调度→5Scout并行侦察→Analyst+Critic整合质疑→Writer撰写→2Reviewer评审定稿，循环迭代直到报告达标。
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

> 11个专业Agent（含主编），4阶段流水线，让AI替你完成深度商业调研。

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

## Agent团队配置（11个角色，含主编）

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
├── CHANGELOG.md                 ← 版本变更历史
├── sample-report.html           ← 输出报告样例（实际跑出的报告参考）
└── references/
    ├── agents.md                  ← 11个角色系统提示词
    ├── pipeline-multi-agent.md    ← 四阶段流水线详解
    ├── scouting-templates.md      ← Scout A-E详细模板
    ├── report-templates.md        ← Writer模板+报告结构（Markdown 规范）
    ├── output-template.html       ← Writer 报告输出 HTML 模板（Light Editorial 风格，含占位符与组件库）
    ├── test_pool.md              ← 测试用例池
    ├── failure_case_log.md       ← 失败案例追踪
    └── self-review-template.md   ← 自审模板
```

## 主编调度协议（核心规范）

主编是 11 个角色中**唯一具有调度权**的角色，必须严格遵守以下协议：

### 调度原则
1. **串行阶段、阶段内并行**：阶段一/二/四内部允许并行 Agent；阶段三必须串行（避免 Writer 写作冲突）。
2. **同步等待、显式确认**：每个 Agent 返回结果后必须显式校验再进入下一阶段，不允许"乐观地"跳过校验。
3. **Checkpoint 必触发**：每个阶段结束后**自动**触发 Checkpoint（详见下文），不依赖 Agent 主动汇报。
4. **失败优先降级、不静默跳过**：任何 Agent 失败都必须走降级路径（见错误处理表），禁止默认"忽略并继续"。

### 主编的 6 项核心职责
1. 解析命题、明确调研类型与深度
2. 调度 5 个 Scout 并行（阶段一）
3. 调度 Analyst + Critic 并行（阶段二）
4. 调度 Writer（阶段三）
5. 调度 2 个 Reviewer 并行（阶段四）
6. **调度恢复**（新增）：当任一 Agent 失败时，决定降级路径并记录

## Checkpoint 机制（断点恢复）

为防止工作中断导致整个调研失败，引入 Checkpoint 机制：

### Checkpoint 触发点
| 阶段 | 触发时机 | 持久化内容 |
|------|----------|-----------|
| **CP-0** | 用户命题解析完成后 | 调研命题、类型配置、深度、时间约束 |
| **CP-1** | 阶段一完成后 | 5 个 Scout 数据包 + 缺失标记 |
| **CP-2** | 阶段二完成后 | Analyst 洞察 + Critic 风险矩阵 |
| **CP-3** | 阶段三完成后 | Writer 报告初稿 |
| **CP-4** | 阶段四完成后 | 评审问题清单 + 定稿状态 |

### 存储规范
- Checkpoint 存于 `references/sessions/{project_id}/checkpoint-{N}.json`
- 每个 Checkpoint 包含：阶段名、产出物哈希、生成时间、下一阶段入口
- 主编恢复时读取最近一个 Checkpoint，从下一阶段重入

### 恢复流程
```
工作中断
  ↓
启动恢复（主编重新激活）
  ↓
扫描 references/sessions/ 找到最近 Checkpoint
  ↓
验证 Checkpoint 完整性（哈希对比）
  ↓
从下一阶段重入，复用已完成产出
```

## 错误处理（升级版）

### 4 类失败模式与降级矩阵

| 失败类型 | 检测信号 | 降级路径 | 决策人 |
|----------|----------|----------|--------|
| **L1 调度失败** | Agent 调度超时（2 分钟） | 自动重试 1 次，仍失败则跳过 | 主编 |
| **L2 数据缺失** | Scout 数据包为空 | 标记缺口 + 用其他 Scout 旁证 | 主编 |
| **L3 输出不合格** | Reviewer 标 Critical | Writer 修订（最多 3 轮） | 主编 |
| **L4 资源耗尽** | Token / 速率超限 | 保存 Checkpoint + 暂停 + 提示用户 | 主编 + 用户 |

### 超时分层（重要！修正 LOG/STA 歧义）

| 超时类型 | 默认阈值 | 含义 | 触发动作 |
|----------|----------|------|----------|
| **调度超时** | 2 分钟 | Agent 启动 / 心跳超时 | 重试 1 次 → 标记 L1 |
| **工作超时** | 30 分钟 | Agent 单次任务执行 | 自动跳过 + 标记数据缺口 |
| **阶段超时** | 视复杂度 | Scout 2-3h / Analyst 1-2h / Writer 2-3h / Reviewer 1-2h | 触发 Checkpoint + 询问用户 |
| **总超时** | 24 小时 | 整个调研流程 | 强制交付当前版本 + 剩余问题清单 |

### 非 Scout Agent 失败处理（关键新增）

| Agent | 失败影响 | 降级策略 |
|-------|----------|----------|
| **Analyst 失败** | 无洞察整合 | 用 Scout 原始数据 + 主编直出洞察初稿 |
| **Critic 失败** | 无风险质疑 | 主编代行质疑（基于经验 + 触发词"挑战假设"） |
| **Writer 失败** | 无报告 | 主编用 Scout + Analyst 输出 + 模板拼接 Markdown 简版 |
| **Reviewer-A 失败** | 无数据审计 | 跳过数据审计轮次，标记"数据未审计" |
| **Reviewer-B 失败** | 无可行性评估 | 跳过可行性轮次，标记"可行性未评估" |
| **任意 2+ Agent 失败** | 调研质量不可控 | 触发 Checkpoint + 暂停 + 询问用户是否继续 |

### 边界场景处理

| 场景 | 处理方式 |
|------|----------|
| 调研主题模糊（"帮我调研一下"） | 主编追问：行业/产品/竞品/用户？调研深度？ |
| 超出范围（法律/财务/实时新闻） | 明确说明限制，建议转介专业人士 |
| 数据不足 | 标注数据缺口，说明估算或假设前提 |
| 调研对象无公开信息 | 说明调研局限，建议实地访谈补充 |
| 用户多次追问仍未明确（3 次上限） | 提供 3 个最可能的解读路径，让用户选其一 |

## 自我迭代流程

每次调研任务完成后，触发以下自我迭代动作：

### 必做（自动）
1. 记录本次 Checkpoint 总数、各阶段实际耗时
2. 对比预期耗时与实际耗时，识别超时阶段
3. 统计失败 Agent 数量、类型、降级路径
4. 更新 `references/failure_case_log.md`

### 可选（主编评估）
1. 是否发现新的失败模式？→ 加入 failure_case_log
2. 是否触发新的边界场景？→ 加入 SKILL.md 错误处理表
3. 是否有流程冗余？→ 优化 pipeline
4. 是否有用户重复问题？→ 优化触发词

### 定期（每 5 次任务）
1. 主编自评：使用 `references/self-review-template.md` 完整跑一次
2. 更新 `grading.json` 评分
3. 决定是否升级版本（参见 `CHANGELOG.md`）

## 验证清单

- [ ] description以"Use when"开头
- [ ] frontmatter包含完整字段（含type: workflow）
- [ ] references/目录包含agents.md + pipeline-multi-agent.md
- [ ] test_pool.md在references/目录下
- [ ] 11个角色（含主编）定义清晰
- [ ] 4阶段流程覆盖完整
- [ ] 错误处理机制完整
- [ ] 边界场景覆盖
- [ ] 主编调度协议明确（含调度恢复职责）
- [ ] Checkpoint 机制定义（CP-0 ~ CP-4）
- [ ] 4 类失败模式（L1-L4）有降级路径
- [ ] 非 Scout Agent 失败有降级策略
- [ ] 超时分层（调度/工作/阶段/总）明确
