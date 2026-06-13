# Self-Review Template — 自审模板

> 每次发布前使用此模板进行自我审核。

**技能名称**：multi-agent-researcher
**审核人**：[填写]
**审核日期**：YYYY-MM-DD

---

## 发布前检查清单

### 1. 基础信息核对
- [ ] SKILL.md 存在
- [ ] description 以 "Use when" 开头
- [ ] frontmatter 字段完整（name/description/version/author/license/platforms/metadata）
- [ ] type 为 workflow

### 2. 引用文件检查
- [ ] references/agents.md 存在
- [ ] references/pipeline-multi-agent.md 存在
- [ ] references/scouting-templates.md 存在
- [ ] references/report-templates.md 存在
- [ ] references/test_pool.md 存在
- [ ] references/failure_case_log.md 存在
- [ ] references/self-review-template.md 存在

### 3. 触发词验证
- [ ] 完整调研触发词覆盖（调研一下XX市场/帮我做竞品分析/用户研究/项目可行性调研）
- [ ] 快速查询触发词覆盖（XX行业市场规模/竞品对比）
- [ ] 触发词与 description 一致

### 4. 流程完整性
- [ ] 四阶段流程明确（侦察→整合→撰写→评审）
- [ ] 主编调度说明清晰
- [ ] Scout配置矩阵存在
- [ ] 评审循环机制明确（最多3轮）

### 5. Agent定义完整性
- [ ] 主编（Chief Researcher）
- [ ] Scout-A ~ Scout-E（5个Scout）
- [ ] Analyst（洞察整合师）
- [ ] Critic（质疑评审官）
- [ ] Writer（报告撰写师）
- [ ] Reviewer-A（数据审计官）
- [ ] Reviewer-B（落地评估官）

### 6. 测试覆盖
- [ ] test_pool.md 测试用例 ≥ 10条
- [ ] 覆盖语法验证
- [ ] 覆盖Agent识别
- [ ] 覆盖流水线
- [ ] 覆盖触发词
- [ ] 覆盖Scout配置
- [ ] 覆盖边界测试

### 7. 错误处理
- [ ] 有明确的错误处理场景
- [ ] 有边界场景处理说明
- [ ] 模糊调研主题处理方式明确

### 8. 输出物定义
- [ ] Scout数据包（YAML格式）
- [ ] 市场洞察报告（Markdown格式）
- [ ] 完整调研报告（HTML/PDF格式）
- [ ] 评审问题清单（Markdown格式）

---

## 自审结论

| 检查项 | 结果 | 备注 |
|--------|------|------|
| 基础信息 | ✅ / ❌ | |
| 引用文件 | ✅ / ❌ | |
| 触发词 | ✅ / ❌ | |
| 流程完整性 | ✅ / ❌ | |
| Agent定义 | ✅ / ❌ | |
| 测试覆盖 | ✅ / ❌ | |
| 错误处理 | ✅ / ❌ | |
| 输出物 | ✅ / ❌ | |

**自审结论**：✅ 可以发布 / ⚠️ 需要修复 / ❌ 阻塞发布

**需要修复的问题**：
1. [填写问题]
2. [填写问题]

**审核人签名**：________________