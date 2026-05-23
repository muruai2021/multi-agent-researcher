# Multi-Agent Research — 多Agent协作深度调研系统

> 10个专业Agent，4阶段流水线，让AI替你完成深度商业调研。

---

# English Version

# Multi-Agent Research — Multi-Agent Deep Research System

> 10 specialized agents, 4-stage pipeline, let AI complete deep business research for you.

## Overview

Multi-Agent Research is an enterprise-level deep research solution. Through Editor-in-Chief orchestrating 5 Scouts in parallel reconnaissance, Analyst+Critic integrating and questioning, Writer drafting, and 2 Reviewers reviewing and finalizing, it achieves full-chain coverage from market analysis to feasibility assessment.

**Core Features:**
- 10 specialized agents, each with distinct responsibilities
- 4-stage pipeline, 6-10 hours for deep research
- Iterative loops until report meets standards
- Supports multiple research type configurations

## Workflow

```
User says "Research the XX market for me"
         ↓
Editor receives task, parses research topic
         ↓
Stage 1: Parallel reconnaissance (5 Scouts)
  Scout-A → Market data package
  Scout-B → Competitor data package
  Scout-C → User data package
  Scout-D → Customer data package
  Scout-E → Case data package
         ↓
Stage 2: Analysis & Integration (Analyst + Critic)
  Analyst → Market insights report
  Critic → Risk and opportunity matrix
         ↓
Stage 3: Report Writing (Writer)
  Writer → Complete report draft
         ↓
Stage 4: Review & Finalization (Reviewer-A + Reviewer-B)
  Reviewer-A → Data/logic review
  Reviewer-B → Feasibility review
         ↓
      ┌── Review passed? ──┐
      ↓              ↓
     ✅            ❌
  Finalize    Writer revise
                   ↑
            (loop until qualified)
```

## Agent Team (10 Agents)

| Agent | Role | Core Responsibilities |
|-------|------|------------------------|
| Editor-in-Chief | Chief Researcher | Parse topics, schedule agents, assemble reports |
| Scout-A | Market Analyst | Market size, growth, policy environment |
| Scout-B | Competitor Researcher | Competitive landscape, competitor strengths/weaknesses |
| Scout-C | User Researcher | Consumer behavior, decision paths |
| Scout-D | Customer Analyst | Customer profiles, loyalty analysis |
| Scout-E | Case Researcher | Success/failure case references |
| Analyst | Insights Integrator | Multi-source integration, insight extraction |
| Critic | Questioning Reviewer | Challenge assumptions, risk assessment |
| Writer | Report Writer | Complete report output |
| Reviewer-A | Data Auditor | Data accuracy, logic |
| Reviewer-B | Feasibility Evaluator | Feasibility, innovation assessment |

## Four-Stage Pipeline

| Stage | Agents | Duration | Output |
|-------|--------|----------|--------|
| Stage 1 | Scout A-E (parallel) | 2-3h | 5 data packages |
| Stage 2 | Analyst + Critic | 2-3h | Insights report + risk matrix |
| Stage 3 | Writer | 2-3h | Report draft |
| Stage 4 | Reviewer-A + B | 1-2h | Review comments |

**Total Duration: 6-10 hours (adjusted by complexity)**

## Research Type Configuration

| Research Type | Scout Configuration | Applicable Scenarios |
|---------------|---------------------|----------------------|
| General Business Research | A:Market + B:Competitor + C:User + D:Customer + E:Case | New project立项 |
| Product Market Research | A:Demand + B:Competitor + C:User + D:Feedback + E:Product Case | New product development |
| Competitor Research | A:Share + B:Product + C:Review + D:Motive + E:Failure Case | Competitive strategy |
| User Research | A:Profile + B:Behavior + C:Demand + D:Churn + E:High Satisfaction | UX optimization |

## Trigger Words

**Full research triggers:**
- "调研一下XX市场" / "Research the XX market"
- "帮我做竞品分析" / "Help me do competitor analysis"
- "用户研究" / "User research"
- "项目可行性调研" / "Project feasibility research"
- "/调研 [调研主题]" / "/research [topic]"

**Quick queries:**
- "XX行业市场规模" / "XX industry market size"
- "竞品对比" / "Competitor comparison"

## Deliverables

| Deliverable | Format | Description |
|-------------|--------|-------------|
| Scout data packages | YAML | Raw material archive |
| Market insights report | Markdown | Internal decision reference |
| Complete research report | HTML/PDF | External reporting |
| Review issue list | Markdown | Revision basis |

## Directory Structure

```
multi-agent-research/
├── SKILL.md                  ← Main entry (Editor-in-Chief scheduling)
└── references/
    ├── agents.md               ← 10 Agent system prompts
    ├── pipeline-multi-agent.md ← Four-stage pipeline details
    ├── scouting-templates.md   ← Scout A-E detailed templates
    ├── report-templates.md     ← Writer templates + report structure
    └── test_pool.md           ← Test case pool
```

## Related Skills

- `skill-factory` - Skill packaging basics
- `multi-agent-skill-factory` - Multi-agent SOP packaging
- `multi-agent-ecommerce` - E-commerce customer service
- `multi-agent-ui-styles` - UI style design

## License

MIT
