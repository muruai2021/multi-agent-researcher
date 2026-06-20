# Multi-Agent Research — 测试用例池

**技能名称**：multi-agent-researcher
**测试日期**：2026-06-20
**测试版本**：v1.2.0（多 Agent 协作 + 调度协议 + Checkpoint 版）

---

## 测试用例总览

| 测试类型 | 用例数 | 测试范围 |
|----------|--------|----------|
| 语法验证 | 6 | frontmatter / 目录结构 |
| Agent 识别 | 11 | 11 个角色完整性 |
| 流水线 | 5 | 四阶段流程 |
| 触发词 | 4 | 用户输入识别 |
| Scout 配置 | 4 | 4 种调研类型 |
| 调度协议 | 4 | 主编调度原则 |
| 失败处理 | 8 | 4 类失败 L1-L4 + 5 个 Agent 降级 |
| Checkpoint | 6 | CP-0 ~ CP-4 + 恢复 |
| 超时分层 | 4 | T1-T4 阈值 |
| 通用协议 | 5 | 11 Agent 通用规范 |
| **输出模板** | **10** | **v1.3.0 新增：output-template.html 验证** |
| 边界测试 | 4 | 模糊/超范围/循环上限/L5 追问 |
| **总计** | **71** | - |

---

## 语法验证

| 用例ID | 测试项 | 输入 | 预期结果 | 通过条件 |
|--------|--------|------|----------|----------|
| TC-SYNTAX-001 | frontmatter格式 | SKILL.md内容 | YAML格式正确 | 以`---`开头结尾 |
| TC-SYNTAX-002 | 必需字段 | frontmatter | 含name/description/version/author/license/platforms/type/metadata | 8字段存在 |
| TC-SYNTAX-003 | description长度 | description内容 | ≤1024字符 | `len <= 1024` |
| TC-SYNTAX-004 | description开头 | description内容 | 以"Use when"开头 | startswith("Use when") |
| TC-SYNTAX-005 | type字段 | frontmatter.metadata | type为workflow | `type == "workflow"` |
| TC-SYNTAX-006 | references/目录 | 目录结构 | 含7个核心文件 | agents/pipeline/scouting/report/test_pool/failure_case/self-review |

## 功能测试 - Agent 识别

| 用例ID | 测试项 | 输入 | 预期结果 | 通过条件 |
|--------|--------|------|----------|----------|
| TC-AGENT-001 | 主编Agent | agents.md检查 | 含调度5个Scout + 调度恢复 | 有调度恢复职责 |
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

## 功能测试 - 流水线

| 用例ID | 测试项 | 输入 | 预期结果 | 通过条件 |
|--------|--------|------|----------|----------|
| TC-PIPE-001 | 四阶段定义 | pipeline检查 | 侦察→整合→撰写→评审 | 4个阶段完整 |
| TC-PIPE-002 | Scout并行 | pipeline检查 | 5个Scout并行执行 | Scout A-E并行描述 |
| TC-PIPE-003 | 主编调度 | pipeline检查 | 主编贯穿全程（含阶段零） | 主编在每阶段都有任务 |
| TC-PIPE-004 | 评审循环 | pipeline检查 | 修订→评审循环 | 最多3轮 |
| TC-PIPE-005 | 评审通过标准 | pipeline检查 | Critical=0 + High≤2 | 有明确通过标准 |

## 功能测试 - 触发词

| 用例ID | 测试项 | 输入 | 预期结果 | 通过条件 |
|--------|--------|------|----------|----------|
| TC-TRIGGER-001 | 完整调研触发 | "调研一下XX市场" | 主编调度完整流程 | 触发四阶段 |
| TC-TRIGGER-002 | 竞品分析触发 | "帮我做竞品分析" | Scout-B为主 | Scout-B相关 |
| TC-TRIGGER-003 | 用户研究触发 | "用户研究" | Scout-C为主 | Scout-C相关 |
| TC-TRIGGER-004 | 快速查询触发 | "XX行业市场规模" | Scout-A返回 | 不触发完整流程 |

## 功能测试 - Scout 配置

| 用例ID | 测试项 | 输入 | 预期结果 | 通过条件 |
|--------|--------|------|----------|----------|
| TC-SCOUT-001 | 通用商业配置 | pipeline检查 | 5个Scout全开 | A+B+C+D+E |
| TC-SCOUT-002 | 产品调研配置 | pipeline检查 | A需求+B竞品+C用户+D反馈+E案例 | 按类型配置 |
| TC-SCOUT-003 | 竞品研究配置 | pipeline检查 | A份额+B产品+C评价+D动机+E失败 | 按类型配置 |
| TC-SCOUT-004 | 用户研究配置 | pipeline检查 | A画像+B行为+C需求+D流失+E高满意 | 按类型配置 |

## 功能测试 - 调度协议（新增）

| 用例ID | 测试项 | 输入 | 预期结果 | 通过条件 |
|--------|--------|------|----------|----------|
| TC-DISPATCH-001 | 串行阶段约束 | 阶段三Writer | Writer串行执行 | 不与其他Agent并行 |
| TC-DISPATCH-002 | 阶段内并行 | 阶段一5个Scout | Scout A-E 同时启动 | 时间戳偏差 < 5s |
| TC-DISPATCH-003 | 同步等待校验 | 任何Agent返回 | 主编显式校验后才进下阶段 | 不允许乐观跳过 |
| TC-DISPATCH-004 | Checkpoint必触发 | 阶段一完成 | 自动触发CP-1 | references/sessions/ 出现 checkpoint-1.json |

## 功能测试 - 失败处理（新增）

| 用例ID | 测试项 | 输入 | 预期结果 | 通过条件 |
|--------|--------|------|----------|----------|
| TC-FAIL-001 | L1 调度失败 | 模拟 Agent 启动超时 | 重试1次 → 跳过 | 报告中含 `[L1: 跳过]` |
| TC-FAIL-002 | L2 数据缺失 | Scout 数据包为空 | 标记缺口 + 旁证 | 报告中含 `[L2: 数据缺口]` |
| TC-FAIL-003 | L3 输出不合格 | Reviewer 标 Critical | Writer 修订 ≤ 3 轮 | 第 4 轮强制交付 |
| TC-FAIL-004 | L4 资源耗尽 | Token 超限 | 保存 CP + 询问用户 | 触发暂停 + 询问 |
| TC-FAIL-005 | Analyst 失败 | Analyst 调度失败 | 主编代行洞察 | 报告含 `[降级: 主编代行]` |
| TC-FAIL-006 | Writer 失败 | Writer 调度失败 | 主编用模板拼简版 | 报告含 `[降级: 简版报告]` |
| TC-FAIL-007 | Reviewer-A 失败 | Reviewer-A 失败 | 跳过数据审计 | 报告含 `[降级: 数据未审计]` |
| TC-FAIL-008 | 2+ Agent 同时失败 | Analyst + Critic 都失败 | 触发 CP + 询问用户 | 强制要求用户决策 |

## 功能测试 - Checkpoint（新增）

| 用例ID | 测试项 | 输入 | 预期结果 | 通过条件 |
|--------|--------|------|----------|----------|
| TC-CP-001 | CP-0 触发 | 命题解析完成 | checkpoint-0.json 存在 | 含命题/类型/配置 |
| TC-CP-002 | CP-1 触发 | 5 Scout 完成 | checkpoint-1.json 存在 | 含 5 数据包哈希 |
| TC-CP-003 | CP-2 触发 | Analyst+Critic 完成 | checkpoint-2.json 存在 | 含洞察+风险矩阵 |
| TC-CP-004 | CP-3 触发 | Writer 报告初稿完成 | checkpoint-3.json 存在 | 含报告初稿 |
| TC-CP-005 | CP-4 触发 | 评审完成 | checkpoint-4.json 存在 | 含评审+定稿状态 |
| TC-CP-006 | 中断恢复 | 工作中断后重新激活 | 从最近 CP 恢复 | next_stage 正确 |

## 功能测试 - 超时分层（新增）

| 用例ID | 测试项 | 输入 | 预期结果 | 通过条件 |
|--------|--------|------|----------|----------|
| TC-TIMEOUT-001 | T1 调度超时 | 模拟 Agent 2 分钟无响应 | 重试 1 次 → 标记 L1 | 行为符合规范 |
| TC-TIMEOUT-002 | T2 工作超时 | Scout 工作 30 分钟 | 跳过 + 标记缺口 | 报告中明确缺口 |
| TC-TIMEOUT-003 | T3 阶段超时 | 阶段一 3 小时未完成 | 触发 CP + 询问用户 | 强制要求决策 |
| TC-TIMEOUT-004 | T4 总超时 | 整个流程 24h | 强制交付 + 剩余问题 | 不再继续 |

## 功能测试 - 通用协议（新增）

| 用例ID | 测试项 | 输入 | 预期结果 | 通过条件 |
|--------|--------|------|----------|----------|
| TC-PROTO-001 | QC-1 输出格式 | 任何 Agent 输出 | 符合 YAML/Markdown 模板 | 字段完整 |
| TC-PROTO-002 | QC-2 数据来源 | 任何数字 | 含 `[来源:...]` 标注 | 无来源则修正 |
| TC-PROTO-003 | 失败回报格式 | Agent 失败 | YAML 格式含 status/type/context | 主编 2 分钟内决策 |
| TC-PROTO-004 | 跨阶段串行 | 阶段一未完成 | 阶段二不启动 | 严格串行 |
| TC-PROTO-005 | 资源上限 | 单 Agent > 50K tokens | 触发 L4 失败 | 立即回报 |

## 功能测试 - 输出模板（新增 v1.3.0）

| 用例ID | 测试项 | 输入 | 预期结果 | 通过条件 |
|--------|--------|------|----------|----------|
| TC-TPL-001 | 模板存在 | 检查 `references/output-template.html` | 文件存在且可读 | 文件 > 10KB |
| TC-TPL-002 | 模板占位符 | 搜索 `{{` 出现次数 | ≥ 30 个 | 8 章 + 附录 A 完整 |
| TC-TPL-003 | 模板无具体内容 | 搜索 "AI 编程助手" | 0 次 | 模板为占位符形式 |
| TC-TPL-004 | 模板无 emoji | Unicode emoji 字符 | 0 个 | 通过 |
| TC-TPL-005 | 模板含完整 CSS | `<style>` 块 | 含 Light Editorial tokens | 4 色 Tier 完整 |
| TC-TPL-006 | 模板含 SVG icons | `<symbol id="i-` | ≥ 15 个 | 覆盖常用 icon |
| TC-TPL-007 | 模板含组件库 | 附录 B 章节 | 含 stat/bar/persona/note/chip 示例 | Writer 可参考 |
| TC-TPL-008 | Writer 使用模板 | 触发完整调研 | 输出 `references/output/{id}/report.html` | 基于模板生成 |
| TC-TPL-009 | 占位符替换 | 检查输出 report.html | `{{` 出现次数 = 0 | 全部已替换 |
| TC-TPL-010 | 删除组件库 | 检查输出 report.html | 不含 "组件库速查" 章节 | 附录 B 已删除 |

## 边界测试

| 用例ID | 测试项 | 输入 | 预期结果 | 通过条件 |
|--------|--------|------|----------|----------|
| TC-BOUND-001 | 模糊调研主题 | "帮我调研一下" | 主编追问细节（最多3次） | 不崩溃 |
| TC-BOUND-002 | 超出范围的调研 | "调研量子计算" | 返回+说明限制 | 能处理 |
| TC-BOUND-003 | 3轮修订上限 | 3次评审不通过 | 交付当前版本 | 不无限循环 |
| TC-BOUND-004 | L5 用户追问上限 | 用户 3 次仍未明确 | 提供 3 路径让用户选 | 不再追问第 4 次 |

---

## 测试报告模板

```markdown
# 测试报告

**技能名称**：multi-agent-researcher
**版本**：v1.3.0
**测试日期**：[日期]
**测试范围**：71 条用例

## 测试结果汇总

| 测试类型 | 用例数 | 通过 | 失败 | 通过率 |
|----------|--------|------|------|--------|
| 语法验证 | 6 | X | X | X% |
| Agent 识别 | 11 | X | X | X% |
| 流水线 | 5 | X | X | X% |
| 触发词 | 4 | X | X | X% |
| Scout 配置 | 4 | X | X | X% |
| 调度协议 | 4 | X | X | X% |
| 失败处理 | 8 | X | X | X% |
| Checkpoint | 6 | X | X | X% |
| 超时分层 | 4 | X | X | X% |
| 通用协议 | 5 | X | X | X% |
| 输出模板 | 10 | X | X | X% |
| 边界测试 | 4 | X | X | X% |
| **总计** | **71** | **X** | **X** | **X%** |

## 失败用例

### TC-XXX-XXX
- **问题**：[描述]
- **关联失败模式**：[L1-L6]
- **修复建议**：[建议]

## 关联失败案例

详见 `failure_case_log.md` 中编号 FC-XXX 的条目。

## 结论

- [ ] 71 条用例全部通过（或失败率 < 5%）
- [ ] 11 个 Agent（含主编）定义完整
- [ ] 调度协议明确
- [ ] 失败处理 4 类 L1-L4 + 5 Agent 降级覆盖
- [ ] Checkpoint CP-0 ~ CP-4 + 恢复机制
- [ ] 超时分层 T1-T4 明确
- [ ] 输出模板 output-template.html 可用
- [ ] Writer 基于模板生成 0 emoji 报告
- [ ] **可发布 v1.3.0**
```

---

## 回归测试用例

| 用例ID | 测试项 | 输入 | 预期结果 | 通过条件 |
|--------|--------|------|----------|----------|
| RE-FM-001 | frontmatter完整性 | 修改frontmatter字段 | 各Agent正常工作 | 字段完整时正常 |
| RE-FM-002 | frontmatter缺失 | 删除任一必填字段 | 报错提示缺失字段 | 有友好错误提示 |
| RE-AGENT-FAIL-001 ~ 005 | 非 Scout 降级 | 模拟 5 个 Agent 失败 | 触发对应降级策略 | 报告含正确标记 |
| RE-TIMEOUT-001 ~ 004 | 超时分层 | 模拟 T1-T4 | 触发对应动作 | 行为符合规范 |
| RE-CP-001 ~ 005 | Checkpoint 触发 | 模拟阶段完成 | CP-0 ~ CP-4 触发 | JSON 文件存在 |
| RE-CP-006 | 中断恢复 | 模拟工作中断 | 从最近 CP 恢复 | 复用已完成产出 |
| RE-TPL-001 ~ 010 | 模板使用 | 触发完整调研 | 基于 output-template.html 输出 | 占位符全替换、emoji=0 |
| RE-ERR-001 | 数据矛盾处理 | Scout数据冲突 | Analyst标注矛盾点 | 报告中有说明 |
| RE-ERR-002 | Scout 超时处理 | Scout T2 超时 | 标记数据缺口继续 | 不卡住流程 |
| RE-OUTPUT-001 | 输出物格式 | 完整调研完成 | YAML+Markdown+HTML | 三种格式都生成 |
| RE-DISPATCH-001 ~ 004 | 调度协议 | 4 个调度场景 | 行为符合协议 | 主编不偏离协议 |
| RE-PROTO-001 ~ 005 | 通用协议 | 5 个协议场景 | Agent 按协议执行 | 无协议违反 |
| RE-CHANGELOG-001 | CHANGELOG 存在 | 检查文件 | 存在且记录 v1.0-v1.2 | 完整 |

---

## 测试用例编号规则

- **TC-XXX-NNN**：常规测试用例（Test Case）
- **RE-XXX-NNN**：回归测试用例（Regression）
- **TC-FAIL-NNN**：失败处理测试
- **TC-CP-NNN**：Checkpoint 测试
- **TC-TIMEOUT-NNN**：超时测试
- **TC-PROTO-NNN**：协议测试
- **TC-DISPATCH-NNN**：调度协议测试
- **TC-BOUND-NNN**：边界测试

---

> **注意**：失败案例归档已迁移到 `failure_case_log.md`，本文件不再维护"已发现问题追踪"表，避免数据不一致。两个文件保持单向引用（test_pool → failure_case_log）。
