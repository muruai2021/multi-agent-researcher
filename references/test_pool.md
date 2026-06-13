# Multi-Agent Research — 测试用例池

**技能名称**：multi-agent-research
**测试日期**：2026-05-22
**测试版本**：v1.1.0（多Agent协作版）

---

## 测试用例

### 语法验证

| 用例ID | 测试项 | 输入 | 预期结果 | 通过条件 |
|--------|--------|------|----------|----------|
| TC-SYNTAX-001 | frontmatter格式 | SKILL.md内容 | YAML格式正确 | 以`---`开头结尾 |
| TC-SYNTAX-002 | 必需字段 | frontmatter | 含name/description/version/author/license/platforms/type/metadata | 8字段存在 |
| TC-SYNTAX-003 | description长度 | description内容 | ≤1024字符 | `len <= 1024` |
| TC-SYNTAX-004 | description开头 | description内容 | 以"Use when"开头 | startswith("Use when") |
| TC-SYNTAX-005 | type字段 | frontmatter.metadata | type为workflow | `type == "workflow"` |
| TC-SYNTAX-006 | references/目录 | 目录结构 | 含agents.md/pipeline-multi-agent.md/test_pool.md | 3个核心文件 |

### 功能测试 - Agent识别

| 用例ID | 测试项 | 输入 | 预期结果 | 通过条件 |
|--------|--------|------|----------|----------|
| TC-AGENT-001 | 主编Agent | agents.md检查 | 包含主编职责 | 有调度5个Scout的描述 |
| TC-AGENT-002 | Scout-A存在 | agents.md检查 | 市场分析师 | 有市场规模/CAGR/政策 |
| TC-AGENT-003 | Scout-B存在 | agents.md检查 | 竞品研究员 | 有竞品分析/格局图 |
| TC-AGENT-004 | Scout-C存在 | agents.md检查 | 用户研究员 | 有用户画像/行为路径 |
| TC-AGENT-005 | Scout-D存在 | agents.md检查 | 客户分析师 | 有客户分层/满意度 |
| TC-AGENT-006 | Scout-E存在 | agents.md检查 | 案例研究员 | 有成功/失败案例 |
| TC-AGENT-007 | Analyst存在 | agents.md检查 | 洞察整合师 | 有洞察提炼/机会矩阵 |
| TC-AGENT-008 | Critic存在 | agents.md检查 | 质疑评审官 | 有风险矩阵/时机质疑 |
| TC-AGENT-009 | Writer存在 | agents.md检查 | 报告撰写师 | 有8章报告结构 |
| TC-AGENT-010 | Reviewer-A存在 | agents.md检查 | 数据审计官 | 有Critical/High问题分级 |
| TC-AGENT-011 | Reviewer-B存在 | agents.md检查 | 落地评估官 | 有可行性/创新性评估 |

### 功能测试 - 流水线

| 用例ID | 测试项 | 输入 | 预期结果 | 通过条件 |
|--------|--------|------|----------|----------|
| TC-PIPE-001 | 四阶段定义 | pipeline检查 | 侦察→整合→撰写→评审 | 4个阶段完整 |
| TC-PIPE-002 | Scout并行 | pipeline检查 | 5个Scout并行执行 | Scout A-E并行描述 |
| TC-PIPE-003 | 主编调度 | pipeline检查 | 主编贯穿全程 | 主编在每阶段都有任务 |
| TC-PIPE-004 | 评审循环 | pipeline检查 | 修订→评审循环 | 最多3轮 |
| TC-PIPE-005 | 评审通过标准 | pipeline检查 | Critical=0 + High≤2 | 有明确通过标准 |

### 功能测试 - 触发词

| 用例ID | 测试项 | 输入 | 预期结果 | 通过条件 |
|--------|--------|------|----------|----------|
| TC-TRIGGER-001 | 完整调研触发 | "调研一下XX市场" | 主编调度完整流程 | 触发四阶段 |
| TC-TRIGGER-002 | 竞品分析触发 | "帮我做竞品分析" | Scout-B为主 | Scout-B相关 |
| TC-TRIGGER-003 | 用户研究触发 | "用户研究" | Scout-C为主 | Scout-C相关 |
| TC-TRIGGER-004 | 快速查询触发 | "XX行业市场规模" | Scout-A返回 | 不触发完整流程 |

### 功能测试 - Scout配置

| 用例ID | 测试项 | 输入 | 预期结果 | 通过条件 |
|--------|--------|------|----------|----------|
| TC-SCOUT-001 | 通用商业配置 | pipeline检查 | 5个Scout全开 | A+B+C+D+E |
| TC-SCOUT-002 | 产品调研配置 | pipeline检查 | A需求+B竞品+C用户+D反馈+E案例 | 按类型配置 |
| TC-SCOUT-003 | 竞品研究配置 | pipeline检查 | A份额+B产品+C评价+D动机+E失败 | 按类型配置 |
| TC-SCOUT-004 | 用户研究配置 | pipeline检查 | A画像+B行为+C需求+D流失+E高满意 | 按类型配置 |

### 边界测试

| 用例ID | 测试项 | 输入 | 预期结果 | 通过条件 |
|--------|--------|------|----------|----------|
| TC-BOUND-001 | 模糊调研主题 | "帮我调研一下" | 主编追问细节 | 不崩溃 |
| TC-BOUND-002 | 超出范围的调研 | "调研量子计算" | 返回+说明限制 | 能处理 |
| TC-BOUND-003 | 3轮修订上限 | 3次评审不通过 | 交付当前版本 | 不无限循环 |

---

## 测试报告模板

```markdown
# 测试报告

**技能名称**：multi-agent-research
**版本**：v1.1.0
**测试日期**：[日期]

## 测试结果汇总

| 测试类型 | 用例数 | 通过 | 失败 | 通过率 |
|----------|--------|------|------|--------|
| 语法验证 | X | X | X | X% |
| Agent识别 | X | X | X | X% |
| 流水线 | X | X | X | X% |
| 触发词 | X | X | X | X% |
| Scout配置 | X | X | X | X% |
| 边界测试 | X | X | X | X% |
| **总计** | **X** | **X** | **X** | **X%** |

## 失败用例

### TC-XXX-XXX
- **问题**：[描述]
- **修复建议**：[建议]

## 结论

- [ ] 语法验证通过
- [ ] 10个Agent定义完整
- [ ] 四阶段流水线正确
- [ ] 触发词覆盖主要场景
- [ ] Scout配置按类型分类
- [ ] **可进入评审阶段**
```

---

## 已发现问题追踪

| 问题 | 严重程度 | 状态 | 备注 |
|------|----------|------|------|
| 原版单文件19KB | P0 | ✅ 已修复 | 拆分到references/目录 |
| frontmatter缺字段 | P0 | ✅ 已修复 | 添加version/author/platforms/type/metadata |
| description不以Use when开头 | P0 | ✅ 已修复 | 重写description |
| 无test_pool.md | P0 | ✅ 已修复 | 已创建 |
| 无references/目录 | P0 | ✅ 已修复 | 已创建5个reference文件 |
| 缺少failure_case_log.md | P0 | ✅ 已修复 | 2026-06-13添加 |
| 缺少self-review-template.md | P0 | ✅ 已修复 | 2026-06-13添加 |
| 缺少错误处理章节 | P1 | ✅ 已修复 | 2026-06-13添加 |
| 缺少边界场景描述 | P1 | ✅ 已修复 | 2026-06-13添加 |

---

## 回归测试用例

| 用例ID | 测试项 | 输入 | 预期结果 | 通过条件 |
|--------|--------|------|----------|----------|
| RE-FM-001 | frontmatter完整性 | 修改frontmatter字段 | 各Agent正常工作 | 字段完整时正常 |
| RE-FM-002 | frontmatter缺失 | 删除任一必填字段 | 报错提示缺失字段 | 有友好错误提示 |
| RE-TRIGGER-001 | 触发词覆盖 | "审查并完善这个skills" | Skill被正确触发 | 触发multi-agent--skills-review |
| RE-TRIGGER-002 | 触发词模糊主题 | "帮我调研一下" | 主编追问细节 | 不崩溃，追问用户 |
| RE-PIPELINE-001 | 四阶段流程 | 完整调研请求 | 四阶段依次执行 | 每阶段有输出 |
| RE-PIPELINE-002 | Scout并行 | 5个Scout任务 | 并行执行 | 同时完成而非顺序 |
| RE-REVIEW-001 | 3轮评审上限 | 3次评审不通过 | 停止循环 | 不无限循环 |
| RE-ERR-001 | 数据矛盾处理 | Scout数据冲突 | Analyst标注矛盾点 | 报告中有说明 |
| RE-ERR-002 | 超时处理 | Scout超时 | 标记数据缺口继续 | 不卡住流程 |
| RE-OUTPUT-001 | 输出物格式 | 完整调研完成 | YAML+Markdown+HTML | 三种格式都生成 |
