<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Multi-Agent Research</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif; line-height: 1.6; color: #24292e; background: #f6f8fa; padding: 20px; }
        .container { max-width: 900px; margin: 0 auto; background: #fff; border-radius: 8px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); overflow: hidden; }
        .header { background: linear-gradient(135deg, #c94b4b 0%, #4b134f 100%); color: #fff; padding: 40px; text-align: center; }
        .header h1 { font-size: 2.5em; margin-bottom: 10px; }
        .header p { font-size: 1.2em; opacity: 0.9; }
        .lang-switch { display: flex; justify-content: center; gap: 10px; padding: 20px; background: #f6f8fa; border-bottom: 1px solid #e1e4e8; }
        .lang-btn { padding: 10px 30px; border: 2px solid #c94b4b; background: #fff; color: #c94b4b; border-radius: 25px; cursor: pointer; font-weight: 600; transition: all 0.3s; }
        .lang-btn:hover { background: #c94b4b; color: #fff; }
        .lang-btn.active { background: #c94b4b; color: #fff; }
        .content { padding: 40px; }
        .content[lang="en"] { display: none; }
        h2 { color: #c94b4b; margin: 30px 0 15px; padding-bottom: 10px; border-bottom: 2px solid #c94b4b; }
        h3 { color: #333; margin: 20px 0 10px; }
        p { margin: 15px 0; }
        ul { margin: 15px 0; padding-left: 25px; }
        li { margin: 8px 0; }
        code { background: #f6f8fa; padding: 2px 6px; border-radius: 3px; font-family: Monaco, monospace; color: #e74c3c; }
        pre { background: #1e1e1e; color: #d4d4d4; padding: 20px; border-radius: 8px; overflow-x: auto; margin: 15px 0; font-size: 14px; }
        pre code { background: none; color: inherit; }
        table { width: 100%; border-collapse: collapse; margin: 15px 0; }
        th, td { border: 1px solid #e1e4e8; padding: 12px; text-align: left; }
        th { background: #c94b4b; color: #fff; }
        tr:nth-child(even) { background: #f6f8fa; }
        .badge { display: inline-block; padding: 4px 12px; border-radius: 20px; font-size: 0.85em; margin: 2px; }
        .badge-primary { background: #c94b4b; color: #fff; }
        .badge-success { background: #27ae60; color: #fff; }
        .footer { text-align: center; padding: 30px; color: #666; border-top: 1px solid #e1e4e8; }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>Multi-Agent Research</h1>
            <p>多Agent协作深度调研系统 | Multi-Agent Deep Research System</p>
        </div>
        <div class="lang-switch">
            <button class="lang-btn active" onclick="switchLang('zh')">中文</button>
            <button class="lang-btn" onclick="switchLang('en')">English</button>
        </div>
        <div class="content" lang="zh">
            <h2>概述</h2>
            <p>Multi-Agent Research 是一个企业级深度调研解决方案。通过主编调度5个Scout并行侦察，Analyst+Critic整合质疑，Writer撰写，2个Reviewer评审定稿，实现从市场分析到可行性评估的全链路覆盖。</p>
            <h3>核心特性</h3>
            <ul>
                <li>10个专业Agent各司其职</li>
                <li>4阶段流水线，6-10小时完成深度调研</li>
                <li>循环迭代直到报告达标</li>
                <li>支持多种调研类型配置</li>
            </ul>
            <h2>工作流程</h2>
            <pre><code>用户说"帮我调研一下XX市场"
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
  Reviewer-B → 可行性评审</code></pre>
            <h2>Agent团队（10个Agent）</h2>
            <table>
                <tr><th>Agent</th><th>身份</th><th>核心职责</th></tr>
                <tr><td>主编</td><td>首席研究员</td><td>解析命题、调度Agent、组装报告</td></tr>
                <tr><td>Scout-A</td><td>市场分析师</td><td>市场规模、增长、政策环境</td></tr>
                <tr><td>Scout-B</td><td>竞品研究员</td><td>竞争格局、竞品优劣势</td></tr>
                <tr><td>Scout-C</td><td>用户研究员</td><td>消费者行为、决策路径</td></tr>
                <tr><td>Scout-D</td><td>客户分析师</td><td>客户画像、忠诚度分析</td></tr>
                <tr><td>Scout-E</td><td>案例研究员</td><td>成功/失败案例参照</td></tr>
                <tr><td>Analyst</td><td>洞察整合师</td><td>多源整合、洞察提炼</td></tr>
                <tr><td>Critic</td><td>质疑评审官</td><td>挑战假设、风险评估</td></tr>
                <tr><td>Writer</td><td>报告撰写师</td><td>完整报告输出</td></tr>
                <tr><td>Reviewer-A</td><td>数据审计官</td><td>数据准确性、逻辑性</td></tr>
                <tr><td>Reviewer-B</td><td>落地评估官</td><td>可行性、创新性评估</td></tr>
            </table>
            <h2>四阶段流水线</h2>
            <table>
                <tr><th>阶段</th><th>Agent</th><th>时长</th><th>输出</th></tr>
                <tr><td>阶段一</td><td>Scout A-E（并行）</td><td>2-3h</td><td>5个数据包</td></tr>
                <tr><td>阶段二</td><td>Analyst + Critic</td><td>2-3h</td><td>洞察报告+风险矩阵</td></tr>
                <tr><td>阶段三</td><td>Writer</td><td>2-3h</td><td>报告初稿</td></tr>
                <tr><td>阶段四</td><td>Reviewer-A + B</td><td>1-2h</td><td>评审意见</td></tr>
            </table>
            <p><span class="badge badge-primary">总时长：6-10小时（视复杂度调整）</span></p>
            <h2>调研类型配置</h2>
            <table>
                <tr><th>调研类型</th><th>Scout配置</th><th>适用场景</th></tr>
                <tr><td>通用商业调研</td><td>A市场+B竞品+C用户+D客户+E案例</td><td>新项目立项</td></tr>
                <tr><td>产品市场调研</td><td>A需求+B竞品+C用户+D反馈+E产品案例</td><td>新产品开发</td></tr>
                <tr><td>竞品研究</td><td>A份额+B产品+C评价+D动机+E失败案例</td><td>竞争策略制定</td></tr>
                <tr><td>用户研究</td><td>A画像+B行为+C需求+D流失+E高满意案例</td><td>用户体验优化</td></tr>
            </table>
        </div>
        <div class="content" lang="en">
            <h2>Overview</h2>
            <p>Multi-Agent Research is an enterprise-level deep research solution. Through Editor-in-Chief orchestrating 5 Scouts in parallel reconnaissance, Analyst+Critic integrating and questioning, Writer drafting, and 2 Reviewers reviewing and finalizing, it achieves full-chain coverage from market analysis to feasibility assessment.</p>
            <h3>Core Features</h3>
            <ul>
                <li>10 specialized agents, each with distinct responsibilities</li>
                <li>4-stage pipeline, 6-10 hours for deep research</li>
                <li>Iterative loops until report meets standards</li>
                <li>Supports multiple research type configurations</li>
            </ul>
            <h2>Workflow</h2>
            <pre><code>User says "Research the XX market for me"
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
  Reviewer-B → Feasibility review</code></pre>
            <h2>Agent Team (10 Agents)</h2>
            <table>
                <tr><th>Agent</th><th>Role</th><th>Core Responsibilities</th></tr>
                <tr><td>Editor-in-Chief</td><td>Chief Researcher</td><td>Parse topics, schedule agents, assemble reports</td></tr>
                <tr><td>Scout-A</td><td>Market Analyst</td><td>Market size, growth, policy environment</td></tr>
                <tr><td>Scout-B</td><td>Competitor Researcher</td><td>Competitive landscape, competitor strengths/weaknesses</td></tr>
                <tr><td>Scout-C</td><td>User Researcher</td><td>Consumer behavior, decision paths</td></tr>
                <tr><td>Scout-D</td><td>Customer Analyst</td><td>Customer profiles, loyalty analysis</td></tr>
                <tr><td>Scout-E</td><td>Case Researcher</td><td>Success/failure case references</td></tr>
                <tr><td>Analyst</td><td>Insights Integrator</td><td>Multi-source integration, insight extraction</td></tr>
                <tr><td>Critic</td><td>Questioning Reviewer</td><td>Challenge assumptions, risk assessment</td></tr>
                <tr><td>Writer</td><td>Report Writer</td><td>Complete report output</td></tr>
                <tr><td>Reviewer-A</td><td>Data Auditor</td><td>Data accuracy, logic</td></tr>
                <tr><td>Reviewer-B</td><td>Feasibility Evaluator</td><td>Feasibility, innovation assessment</td></tr>
            </table>
            <h2>Four-Stage Pipeline</h2>
            <table>
                <tr><th>Stage</th><th>Agents</th><th>Duration</th><th>Output</th></tr>
                <tr><td>Stage 1</td><td>Scout A-E (parallel)</td><td>2-3h</td><td>5 data packages</td></tr>
                <tr><td>Stage 2</td><td>Analyst + Critic</td><td>2-3h</td><td>Insights report + risk matrix</td></tr>
                <tr><td>Stage 3</td><td>Writer</td><td>2-3h</td><td>Report draft</td></tr>
                <tr><td>Stage 4</td><td>Reviewer-A + B</td><td>1-2h</td><td>Review comments</td></tr>
            </table>
            <p><span class="badge badge-primary">Total Duration: 6-10 hours (adjusted by complexity)</span></p>
            <h2>Research Type Configuration</h2>
            <table>
                <tr><th>Research Type</th><th>Scout Configuration</th><th>Applicable Scenarios</th></tr>
                <tr><td>General Business Research</td><td>A:Market + B:Competitor + C:User + D:Customer + E:Case</td><td>New project initiation</td></tr>
                <tr><td>Product Market Research</td><td>A:Demand + B:Competitor + C:User + D:Feedback + E:Product Case</td><td>New product development</td></tr>
                <tr><td>Competitor Research</td><td>A:Share + B:Product + C:Review + D:Motive + E:Failure Case</td><td>Competitive strategy</td></tr>
                <tr><td>User Research</td><td>A:Profile + B:Behavior + C:Demand + D:Churn + E:High Satisfaction</td><td>UX optimization</td></tr>
            </table>
        </div>
        <div class="footer">
            <p>Multi-Agent Research | MIT License</p>
        </div>
    </div>
    <script>
        function switchLang(lang) {
            document.querySelectorAll('.content').forEach(el => {
                el.style.display = el.getAttribute('lang') === lang ? 'block' : 'none';
            });
            document.querySelectorAll('.lang-btn').forEach(btn => {
                btn.classList.remove('active');
            });
            event.target.classList.add('active');
        }
    </script>
</body>
</html>