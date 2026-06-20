# Changelog · multi-agent-researcher

本文件记录 multi-agent-researcher skill 的所有重要变更。
格式基于 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.1.0/)，
版本号遵循 [语义化版本 2.0.0](https://semver.org/lang/zh-CN/) 规范。

---

## [1.3.0] - 2026-06-20 · 输出模板固化版

### Added（新增）
- **新增 `references/output-template.html`**：基于 sample-report.html 提炼的 Writer 输出模板
  - 风格：Light Editorial（暖白底 + 报纸双线报头 + 4 色 Tier + Lucide SVG）
  - 字体：Plus Jakarta Sans（正文）+ Newsreader（衬线斜体强调）+ JetBrains Mono（数字）
  - 含完整 CSS tokens、19 个 SVG icon、30+ 组件类
  - 8 章 + 附录 A 完整占位符结构
  - 附录 B 组件库速查（Note/Chip/Persona/Icon/Source-card 5 类）
  - 顶部 HTML 注释含详细使用说明、占位符约定、组件清单

### Changed（变更）
- **SKILL.md 目录结构**：增加 `output-template.html` 与 `sample-report.html` 条目
- **`references/report-templates.md`**：增加"模板使用说明"章节，明确文档关系与 Writer 工作流
- **`references/agents.md` Writer Agent**：增加"输出格式规范（强制）"章节，明确唯一指定模板与失败处理
- **`references/test_pool.md`**：从 60 条扩至 71 条，新增 10 条 TC-TPL 输出模板测试 + RE-TPL-001~010 回归测试

### Fixed（修复）
- 无

---

## [1.2.0] - 2026-06-20 · 调度协议与 Checkpoint 版

### Added（新增）
- **SKILL.md 增加「主编调度协议」章节**：明确主编 6 项核心职责 + 5 项决策原则 + 调度恢复机制
- **SKILL.md 增加「Checkpoint 机制」章节**：CP-0 ~ CP-4 五个 Checkpoint 触发点 + 存储规范 + 恢复流程
- **SKILL.md 增加「自我迭代流程」章节**：必做动作 + 可选动作 + 定期自评
- **pipeline-multi-agent.md 增加「失败模式与降级矩阵」**：4 类失败 L1-L4 + 5 个 Agent 降级策略
- **pipeline-multi-agent.md 增加「Checkpoint 机制详解」**：5 个 Checkpoint 触发矩阵 + JSON 格式 + 归档策略
- **pipeline-multi-agent.md 增加「超时分层规范」**：T1 调度 / T2 工作 / T3 阶段 / T4 总超时，4 层独立
- **agents.md 增加「通用协议 1：输出自检清单」**：QC-1 ~ QC-6 六项自检
- **agents.md 增加「通用协议 2：失败回报协议」**：标准 YAML 回报格式 + 主编 5 种响应（RETRY/DOWNGRADE/SKIP/PAUSE/ABORT）
- **agents.md 增加「通用协议 3：跨 Agent 协作规范」**：信息传递格式 + 并行规则 + 资源上限
- **agents.md 增加「通用协议 4：版本兼容」**：所有 Agent 兼容 v1.2.0+
- **主编 Agent 增加「第五步：调度恢复」**：失败类型判断 + 降级路径 + 5 项决策原则
- **test_pool.md 增加 32 条新测试用例**：调度协议 4 + 失败处理 8 + Checkpoint 6 + 超时分层 4 + 通用协议 5 + 边界 1 + 回归 4
- **failure_case_log.md 重建**：从 5 条扩至 18 条，引入 6 类失败模式（L1-L6）分类 + 跨日记录
- **新增 CHANGELOG.md**（本文件）：记录 v1.0.0 → v1.2.0 完整变更历史

### Changed（变更）
- **SKILL.md 错误处理章节升级**：从 4 项异常表扩展为 4 类失败模式 + 4 层超时 + 5 个 Agent 降级 + 边界场景
- **pipeline-multi-agent.md 主编检查清单升级**：增加 Checkpoint 验证项 + 降级情况记录项
- **agents.md 角色描述更新**：主编从 4 步流程扩至 5 步（增加调度恢复）
- **test_pool.md 总用例数**：从 30 条扩至 60 条
- **test_pool.md 失败案例归档策略**：从"两个文件都维护"改为"单向引用 test_pool → failure_case_log"
- **test_pool.md 删除「已发现问题追踪」表**：避免与 failure_case_log.md 重复

### Fixed（修复）
- **10 vs 11 角色矛盾**（FC-011）：SKILL.md / README.md / agents.md / test_pool.md 共 10 处统一为"11 个角色（含主编）"
- **SKILL.md Not For 章节重复**（FC-012）：删除第 160-163 行重复内容
- **failure_case_log.md 与 test_pool.md 数量不一致**（FC-013）：重建为 18 条统一数据源
- **grading.json 路径泄露**（FC-018）：从 `E:\\work\\skills\\...` 修正为 `C:/Users/Administrator/.claude/skills/...`
- **超时分层歧义**（FC-015）：明确 T1 调度超时（2min）与 T2 工作超时（30min）的不同含义
- **非 Scout Agent 无降级**（FC-014）：增加 Analyst/Critic/Writer/Reviewer-A/B 5 个 Agent 的降级矩阵

### Security（安全）
- 修正 grading.json 本地路径泄露（FC-018）
- 附录数据来源使用真实可访问链接（21 个外部 URL）

---

## [1.1.0] - 2026-06-13 · 多 Agent 协作版

### Added（新增）
- **从单文件 19KB 拆分到 references/ 目录**：agents.md / pipeline-multi-agent.md / scouting-templates.md / report-templates.md / test_pool.md
- **新增 failure_case_log.md**：记录 5 条历史问题（FC-001 ~ FC-005）
- **新增 self-review-template.md**：8 大类发布前自审清单
- **frontmatter 字段补全**：version/author/platforms/type/metadata
- **description 重写**：以 "Use when" 开头，符合 Claude Skills 规范
- **中英双语 README.md**

### Fixed（修复）
- 单文件 19KB 过大（FC-001）
- frontmatter 字段缺失（FC-002）
- description 不符合规范（FC-003）
- 缺少 test_pool.md（FC-004）
- 缺少 references/ 目录（FC-005）

---

## [1.0.0] - 2026-05-22 · 初始版本

### Added（新增）
- 10 个 Agent（主编 + 5 Scout + Analyst + Critic + Writer + 2 Reviewer）
- 4 阶段流水线（侦察→整合→撰写→评审）
- 4 种调研类型配置（通用商业/产品/竞品/用户）
- 单一 SKILL.md 文件（约 19KB）
- 基础触发词、错误处理、边界场景

### Known Limitations（已知局限）
- 单文件过大难以维护（已在 v1.1.0 解决）
- frontmatter 字段不完整（已在 v1.1.0 解决）
- 缺少测试用例（已在 v1.1.0 解决）
- 缺少失败案例追踪（已在 v1.1.0 解决）
- 缺少 Checkpoint 机制（已在 v1.2.0 解决）
- 非 Scout Agent 无降级（已在 v1.2.0 解决）
- 超时分层歧义（已在 v1.2.0 解决）

---

## 版本号规则

- **主版本号（X.0.0）**：不兼容的协议变更（如废除通用协议某节）
- **次版本号（0.X.0）**：向下兼容的功能新增（如增加 Checkpoint 机制）
- **修订号（0.0.X）**：向下兼容的问题修复（如修一个 bug）

---

## 升级路径

| 旧版本 | 升级到 v1.2.0 | 兼容性 |
|--------|---------------|--------|
| v1.0.0 → v1.2.0 | 需先升级到 v1.1.0 | 不直接兼容（缺 references/ 结构） |
| v1.1.0 → v1.2.0 | 直接替换 | 兼容（仅新增协议 + 修复 6 处） |

---

## 未来规划

### [1.4.0] - 2026-09-20（计划）
- Agent 性能基线：单 Agent 平均耗时基线建立
- 失败模式自动检测：主编不再手动分类 L1-L4
- 用户调研模板库：常见行业（金融/SaaS/教育）的预置 Scout 配置
- 行业垂直模板：在 output-template.html 基础上提供金融/SaaS/教育 3 个行业的章节定制

### [2.0.0] - 2026-12-20（规划）
- 协议破坏性变更：通用协议 v2.0（增加 Agent 间实时通信）
- 多主编协作：支持大型项目的并行主编（主编 + 副主编）
- AI 自评估：Writer 完成后自动预审（替代部分 Reviewer 工作）
