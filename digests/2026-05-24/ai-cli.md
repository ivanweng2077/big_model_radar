# AI CLI 工具社区动态日报 2026-05-24

> 生成时间: 2026-05-24 02:42 UTC | 覆盖工具: 7 个

- [Claude Code](https://github.com/anthropics/claude-code)
- [OpenAI Codex](https://github.com/openai/codex)
- [Gemini CLI](https://github.com/google-gemini/gemini-cli)
- [GitHub Copilot CLI](https://github.com/github/copilot-cli)
- [Kimi Code CLI](https://github.com/MoonshotAI/kimi-cli)
- [OpenCode](https://github.com/anomalyco/opencode)
- [Qwen Code](https://github.com/QwenLM/qwen-code)
- [Claude Code Skills](https://github.com/anthropics/skills)

---

## 横向对比

---

# **2026-05-24 AI CLI 工具横向对比分析报告**

---

## 1. **生态全景**
当前 AI CLI 工具已进入**多模型、多场景深度集成**阶段，核心趋势表现为：  
- **本地化与全球化并行**：Claude Code、OpenAI Codex 等主流工具积极支持新兴市场货币（如印度卢比），而 Gemini、Qwen 等侧重本地化部署；  
- **安全与沙盒化需求爆发**：OpenCode、Claude Code 的 Agent 权限控制成为高频议题；  
- **MCP 生态标准化**：GitHub Copilot、Kimi Code 等均围绕 MCP 工具链展开优化，推动 AI 与本地/云端工具的深度协同。

---

## 2. **各工具活跃度对比**

| 工具名称          | Issues (今日) | PRs (今日) | Release 情况               |
|-------------------|---------------|------------|----------------------------|
| Claude Code       | 10            | 10         | v2.1.150（内部改进）       |
| OpenAI Codex      | 10            | 10         | 无新发布                   |
| Gemini CLI        | 10            | 10         | 无新发布                   |
| GitHub Copilot CLI| 10            | 1          | v1.0.52（修复非交互式命令） |
| Kimi Code         | 5             | 7          | 无新发布                   |
| OpenCode          | 10            | 10         | 无新发布                   |
| Qwen Code         | 10            | 10         | v0.16.1-nightly & v0.16.1   |

> *注：Issues/PRs 统计为当日新增或高互动条目*

---

## 3. **共同关注的功能方向**

| 需求领域           | 涉及工具                                                                 |
|--------------------|--------------------------------------------------------------------------|
| **本地化定价**     | Claude Code（印度卢比）、OpenAI Codex（新兴市场支付痛点）                 |
| **性能优化**       | Claude Code（Cowork VM 包体积）、Gemini CLI（AST 感知文件读取）           |
| **MCP 集成改进**   | GitHub Copilot（插件市场同步）、Kimi Code（项目级 MCP 配置）              |
| **会话管理**       | OpenAI Codex（历史会话恢复）、Gemini CLI（会话元数据加载失败）            |
| **安全沙盒化**     | OpenCode（Agent 权限限制）、Claude Code（OAuth 刷新循环）                |
| **UI/UX 体验**    | GitHub Copilot（滚动条/复制粘贴）、Kimi Code（快捷键/思考模式控制）       |

---

## 4. **差异化定位分析**

| 工具名称          | 功能侧重                     | 目标用户                  | 技术路线                     |
|-------------------|-----------------------------|---------------------------|------------------------------|
| **Claude Code**   | Anthropic 生态集成、Cowork   | 企业级开发者、全栈团队     | 云原生 + 桌面应用混合架构     |
| **OpenAI Codex**  | 多 Agent 协作、TUI 一致性   | 开源社区、合规场景         | 渐进式迁移到 app-server 后端  |
| **Gemini CLI**    | AST 感知文件索引、Auto Memory| Google 开发者、代码导航    | 基于 V8 引擎的轻量化工具链    |
| **GitHub Copilot**| VS Code 扩展、MCP 插件市场   | 企业开发者、远程协作       | 插件化 + 云同步架构           |
| **Kimi Code**     | Shell-Agent 互通、会话共享   | 自动化工作流工程师         | Loguru + PTY 进程隔离设计     |
| **OpenCode**      | 沙盒化 Agent、语音输入      | 安全敏感场景、多模态开发   | 混合推理 + 多模型代理框架     |
| **Qwen Code**     | Mode B 本地部署、Feishu 适配 | 私有化部署、中国开发者     | 双模（CLI/TUI）+ 协议兼容层   |

---

## 5. **社区热度与成熟度**

| 工具名称          | 活跃度指标                          | 成熟度阶段               |
|-------------------|-------------------------------------|--------------------------|
| **Claude Code**   | 高（10 Issues + 10 PRs）           | 快速迭代（企业级优化）    |
| **OpenAI Codex**  | 高（10 Issues + 10 PRs）           | 稳定维护（功能完善期）    |
| **Gemini CLI**    | 高（10 Issues + 10 PRs）           | 快速迭代（性能攻坚）      |
| **GitHub Copilot**| 中（10 Issues + 1 PR）             | 企业功能完善期            |
| **Kimi Code**     | 中（5 Issues + 7 PRs）             | 交互优化阶段              |
| **OpenCode**      | 高（10 Issues + 10 PRs）           | 安全/多模态探索期         |
| **Qwen Code**     | 高（10 Issues + 10 PRs）           | 生产化准备期（Mode B）    |

> **结论**：  
> - **Claude Code/OpenAI/Gemini/Qwen** 处于**快速迭代**阶段，聚焦性能与安全；  
> - **GitHub Copilot/Kimi** 进入**企业级功能完善**期，解决跨平台与协作问题；  
> - **OpenCode** 在**多模态与沙盒化**领域探索，社区反馈密集但尚未形成稳定版本。

---

## 6. **值得关注的趋势信号**

### （1）**本地化部署与全球化服务并存**
- **现象**：Qwen Code 的 Mode B 本地部署需求激增，Claude Code 支持印度卢比定价，反映开发者对**可控性**和**成本透明**的双重诉求。  
- **建议**：开发者需评估工具链的**混合架构能力**（如云+本地 Agent）。

### （2）**MCP 生态成为标准接口**
- **现象**：GitHub Copilot、Kimi Code 均强化 MCP 工具链管理，OpenAI Codex 推进 `app-server` 后端集成。  
- **建议**：优先选择支持**标准化工具注册**和**元数据传递**的工具，避免厂商锁定。

### （3）**安全与沙盒化是刚需**
- **现象**：OpenCode 的 Agent 权限限制、Claude Code 的 OAuth 问题，显示用户对**最小权限原则**的强烈需求。  
- **建议**：关注工具的**沙箱隔离策略**（如 macOS seatbelt 兼容方案）。

### （4）**长上下文与性能优化**
- **现象**：Gemini CLI 的 AST 感知、Qwen Code 的内存泄漏修复，表明**大模型上下文管理**是技术难点。  
- **建议**：测试工具的**上下文压缩算法**和**流式处理**能力。

### （5）**多模态交互兴起**
- **现象**：OpenCode 的语音输入提案、Qwen 的 Feishu 适配器，推动**自然语言+代码**的无缝切换。  
- **建议**：评估工具的**多模态输入输出**支持（如语音/图像/文本）。

---

**总结**：2026年 AI CLI 工具正从“单一模型调用”向**多模型协同、安全沙盒、本地化部署、MCP 生态**四大方向演进，开发者需结合自身场景（如企业合规/个人效率）选择匹配工具，并重点关注**协议兼容性**和**调试工具链**的成熟度。

---

## 各工具详细报告

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills 社区热点

> 数据来源: [anthropics/skills](https://github.com/anthropics/skills)

---

### **Claude Code Skills 社区热点报告（截至 2026-05-24）**

---

#### **1. 热门 Skills 排行**  
| **Skill Name** | **功能描述** | **讨论热度** | **状态** | **链接** |
|----------------|-------------|--------------|----------|---------|
| **document-typography** | 解决 AI 生成文档的排版问题（孤行、寡妇段落、编号对齐等） | 高（PR #514，0 👍但摘要被多次引用） | Open | [GitHub](https://github.com/anthropics/skills/pull/514) |
| **AppDeploy** | 直接部署全栈 Web 应用至公开 URL，支持生命周期管理 | 高（PR #360，0 👍但功能需求明确） | Open | [GitHub](https://github.com/anthropics/skills/pull/360) |
| **AURELION Suite** | 结构化认知框架（Kernel/Advisor/Agent/Memory），用于专业知识管理 | 高（PR #444，多技能打包提交） | Open | [GitHub](https://github.com/anthropics/skills/pull/444) |
| **ServiceNow Platform** | 覆盖 ITSM、ITOM、SecOps、FSM 等全流程的 ServiceNow 助手 | 高（PR #568，企业级需求明确） | Open | [GitHub](https://github.com/anthropics/skills/pull/568) |
| **codebase-inventory-audit** | 代码库清理与文档审计（识别废弃代码、文档缺口） | 中高（PR #147，技术治理需求） | Open | [GitHub](https://github.com/anthropics/skills/pull/147) |
| **testing-patterns** | 全栈测试模式指南（单元测试、React 组件测试等） | 中（PR #723，开发者痛点） | Open | [GitHub](https://github.com/anthropics/skills/pull/723) |

---

#### **2. 社区需求趋势**  
从 Issues 提炼的核心方向：  
- **工作流自动化**（如 AppDeploy、ServiceNow 集成）  
- **代码质量与安全**（`codebase-inventory-audit`、`skill-quality-analyzer`）  
- **文档优化**（`document-typography`、`shodh-memory` 持久化上下文）  
- **企业级工具链**（SAP-RPT-1-OSS、ServiceNow）  
- **开发者体验**（`testing-patterns`、`skill-creator` 改进）  

**关键 Issue**：  
- [#228](https://github.com/anthropics/skills/issues/228) 组织内 Skills 共享功能缺失（13 条评论，7 👍）  
- [#189](https://github.com/anthropics/skills/issues/189) `example-skills` 插件重复加载问题（6 评论，8 👍）  

---

#### **3. 高潜力待合并 Skills**  
以下 PR 评论活跃且功能完整，可能近期落地：  
- **`AURELION Suite`** (#444)：结构化认知框架，适合复杂项目管理。  
- **`ServiceNow Platform`** (#568)：企业级 IT 运维全覆盖，需求明确。  
- **`codebase-inventory-audit`** (#147)：代码治理刚需，技术团队高频痛点。  
- **`AppDeploy`** (#360)：降低部署门槛，全栈开发者期待。  

---

#### **4. Skills 生态洞察**  
**当前核心诉求**：  
> **“企业级工具链整合” + “开发者效率提升”**——社区迫切希望 Skills 能无缝衔接主流平台（如 ServiceNow、SAP）、自动化重复任务（部署/测试），同时解决文档和代码库的标准化问题（排版、审计）。安全与权限控制（如 SharePoint 集成）也是高频需求。

---

---

# **Claude Code 社区动态日报 | 2026-05-24**

---

## **1. 今日速览**
- 社区聚焦于 **定价本地化（印度卢比）**、**桌面应用崩溃与性能问题**，以及 **Sonnet 4.6 上下文窗口显示异常**。
- 多个 PR 补充了 **故障排查文档**，覆盖 Cowork、OAuth、终端滚动等场景，提升用户自助修复能力。

---

## **2. 版本发布**
- **v2.1.150**：内部基础设施改进，无用户可见变更。  
  [Release Notes](https://github.com/anthropics/claude-code/releases/tag/v2.1.150)

---

## **3. 社区热点 Issues（Top 10）**

| # | Issue ID | 标题 | 重要性 & 社区反应 |
|----|---------|------|------------------|
| 1 | [#17432](https://github.com/anthropics/claude-code/issues/17432) | **印度卢比定价计划需求** | 👍 392，评论 169。用户强烈呼吁支持本地货币定价，对标 OpenAI/Gemini，反映新兴市场支付痛点。 |
| 2 | [#26224](https://github.com/anthropics/claude-code/issues/26224) | **CLI 冻结/卡顿（5-20分钟）** | 👍 130，评论 102。高频崩溃问题，影响生产力，需紧急修复。 |
| 3 | [#22543](https://github.com/anthropics/claude-code/issues/22543) | **Cowork 生成 10GB VM 包导致性能下降** | 👍 175，评论 69。用户反馈严重性能退化，需优化资源管理逻辑。 |
| 4 | [#42776](https://github.com/anthropics/claude-code/issues/42776) | **Windows 桌面重启失败（进程锁文件）** | 👍 26，评论 78。安装后残留文件导致崩溃，影响 Windows 用户体验。 |
| 5 | [#61734](https://github.com/anthropics/claude-code/issues/61734) | **Sonnet 4.6 上下文窗口显示错误（200K vs 实际 1M）** | 👍 1，评论 14。v2.1.150 回归问题，影响大模型功能体验。 |
| 6 | [#37323](https://github.com/anthropics/claude-code/issues/37323) | **VS Code 扩展缺失 `/btw` 命令** | 👍 60，评论 13。跨终端/IDE 功能一致性需求。 |
| 7 | [#61028](https://github.com/anthropics/claude-code/issues/61028) | **Cowork 会话轮次限制（100）中断自动化项目** | 👍 0，评论 12。长任务流程被意外终止，需增加配置选项。 |
| 8 | [#61415](https://github.com/anthropics/claude-code/issues/61415) | **macOS 权限模式切换失败** | 👍 4，评论 15。权限管理 Bug，影响安全策略配置。 |
| 9 | [#61931](https://github.com/anthropics/claude-code/issues/61931) | **Opus 4.7 反复猜测 API 端点** | 👍 0，评论 3。上下文过大时行为异常，需优化指令优先级。 |
| 10 | [#61920](https://github.com/anthropics/claude-code/issues/61920) | **订阅状态识别失败（VS Code）** | 👍 0，评论 3。授权同步问题，影响付费用户访问。 |

---

## **4. 重要 PR 进展（Top 10）**

| PR ID | 内容 | 链接 |
|------|------|------|
| [#61757](https://github.com/anthropics/claude-code/pull/61757) | **Cowork 导致 Office 插件失效的排查文档** | 新增故障场景与临时解决方案。 |
| [#61738](https://github.com/anthropics/claude-code/pull/61738) | **Sonnet 4.6 上下文窗口显示错误的排查** | 修复 v2.1.150 的回归问题。 |
| [#61745](https://github.com/anthropics/claude-code/pull/61745) | **终端滚动重置（xterm.js 已知问题）** | 提供替代终端建议。 |
| [#61741](https://github.com/anthropics/claude-code/pull/61741) | **Git worktree 清理后的僵尸进程脚本** | 新增清理脚本解决残留问题。 |
| [#61739](https://github.com/anthropics/claude-code/pull/61739) | **FleetView 僵尸会话条目** | 修复 TUI 退出后未清理的会话记录。 |
| [#61722](https://github.com/anthropics/claude-code/pull/61722) | **上下文摘要伪造用户同意** | 防止模型擅自执行未授权操作。 |
| [#61731](https://github.com/anthropics/claude-code/pull/61731) | **Agents 面板导航导致上下文降级** | 修复 1M→200K 的静默降级问题。 |
| [#61729](https://github.com/anthropics/claude-code/pull/61729) | **终端无限滚动/ENOBUFS崩溃** | 缓解渲染缓冲区溢出风险。 |
| [#61705](https://github.com/anthropics/claude-code/pull/61705) | **`-p` 头显会话计费免责声明** | 明确计费规则，避免用户误解。 |
| [#61708](https://github.com/anthropics/claude-code/pull/61708) | **更新后模型标识符无效** | 修复区域 API 兼容性问题。 |

---

## **5. 功能需求趋势**
- **本地化定价**（如印度卢比）：新兴市场刚需。
- **性能优化**：Cowork 资源占用、CLI 卡顿、VM 包体积过大。
- **IDE 集成**：VS Code 扩展功能对齐（如 `/btw`）。
- **大模型支持**：Sonnet 4.6 上下文窗口异常、Opus 4.7 行为逻辑问题。
- **故障排查**：OAuth、Cowork、终端滚动等场景的文档补充。

---

## **6. 开发者关注点**
- **稳定性**：频繁崩溃（Windows/macOS）、会话丢失、进程泄漏。
- **权限与安全**：权限模式切换失败、OAuth 刷新循环。
- **计费透明性**：头显会话计费规则不清晰。
- **工具链兼容性**：Office/Excel 插件冲突、Cursor 扩展会话无法打开。
- **调试支持**：社区急需更多故障排查指南和脚本工具。

--- 

**数据来源**：[GitHub Issues/PRs](https://github.com/anthropics/claude-code)

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

---

# OpenAI Codex 社区动态日报 | 2026-05-24

---

## **今日速览**
- 无新版本发布，但社区活跃度高，共新增 33 个 PR、50+ Issues（含高评论量 Issue）。
- 核心关注点集中在 **Windows 沙箱权限问题**、**会话/上下文管理**、**MCP 集成改进** 和 **UI/UX 体验优化**。
- 开发者对 `gpt-5.5` 模型稳定性及多 Agent 协作功能反馈积极，但也暴露了若干关键 Bug。

---

## **版本发布**
> 无新 Release。

---

## **社区热点 Issues**

| # | 标题 | 重要性 & 社区反应 |
|----|------|------------------|
| **[#20161](https://github.com/openai/codex/issues/20161)** | [CLOSED] 手机号验证失效导致 SSO 登录异常 | 高频用户痛点，98 👍，147 条评论。反映身份认证流程存在严重缺陷，影响 Pro 订阅用户体验。 |
| **[#18993](https://github.com/openai/codex/issues/18993)** | [OPEN] VS Code 扩展无法打开历史会话记录 | 47 👍，27 条评论。IDE 集成功能回归性故障，影响开发者工作流连续性。 |
| **[#23381](https://github.com/openai/codex/issues/23381)** | [OPEN] CLI 误报网络安全警告阻断正常开发 | 17 条评论，涉及政府/GSM 项目，安全策略误伤引发争议。 |
| **[#24086](https://github.com/openai/codex/issues/24086)** | [OPEN] Mac mini M4 + Studio Display 锁屏后计算机使用失败 | 1 👍，5 条评论。硬件兼容性需紧急修复。 |
| **[#24269](https://github.com/openai/codex/issues/24269)** | [OPEN] `/Goal` 指令始终失败 | 1 👍，4 条评论。新功能 Goal 的稳定性问题。 |
| **[#23245](https://github.com/openai/codex/issues/23245)** | [OPEN] 桌面端对话输出垂直抖动 | 2 👍，4 条评论。UI 渲染性能优化需求。 |
| **[#24050](https://github.com/openai/codex/issues/24050)** | [OPEN] Windows 沙箱触发 UAC 安装检测 | 3 👍，4 条评论。沙箱权限设计缺陷影响 Windows ARM64 用户。 |
| **[#22705](https://github.com/openai/codex/issues/22705)** | [OPEN] iOS 移动端会话元数据加载失败 | 8 👍，3 条评论。移动端会话恢复问题。 |
| **[#19315](https://github.com/openai/codex/issues/19315)** | [OPEN] Windows 沙箱下 Git worktree 操作需重复授权 | 1 👍，3 条评论。沙箱权限粒度需调整。 |
| **[#24282](https://github.com/openai/codex/issues/24282)** | [OPEN] 设置目标后线程标题生成失败 | 3 条评论。数据库写入逻辑 Bug。 |

---

## **重要 PR 进展**

| # | PR 标题 | 关键内容 |
|----|--------|----------|
| **[#24154](https://github.com/openai/codex/pull/24154)** | 实验性添加 turn 额外上下文 | 允许客户端在会话中注入临时外部状态（如浏览器自动化上下文），无需用户提示。 |
| **[#23618](https://github.com/openai/codex/pull/23618)** | 实现持久化队列存储 | 解决异步输入（queued follow-ups）丢失问题，新增 SQLite 队列存储层。 |
| **[#24166](https://github.com/openai/codex/pull/24166)** | app-server 支持 turn 级 MCP 元数据 | 为工具调用传递服务器特定元数据（如搜索位置信息），避免全局暴露敏感信息。 |
| **[#24257](https://github.com/openai/codex/pull/24257)** | TUI 配置清理：插件市场同步 | 修复 TUI 与 app-server 插件状态不同步问题，确保远程模式下配置一致性。 |
| **[#24266](https://github.com/openai/codex/pull/24266)** | TUI 清理：插件提及更新 | 统一插件列表来源，避免本地配置与服务器状态冲突。 |
| **[#24265](https://github.com/openai/codex/pull/24265)** | TUI 清理：MCP 库存同步 | 修复 MCP 服务器状态显示滞后问题，提升实时性。 |
| **[#24255](https://github.com/openai/codex/pull/24255)** | TUI 清理：可信项目配置 | 通过 app-server 持久化信任决策，避免本地配置绕过。 |
| **[#24254](https://github.com/openai/codex/pull/24254)** | TUI 清理：OSS 提供者选择 | 将 OSS 提供商配置写入路径改为 app-server API，保证一致性。 |
| **[#24126](https://github.com/openai/codex/pull/24126)** | 建议引擎（next-prompt）核心实现 | 构建独立的核心建议引擎，用于后续 UI/API 集成。 |
| **[#24121](https://github.com/openai/codex/pull/24121)** | 本地使用量存储（1/4） | 为 token 使用报告建立本地存储基础，支持细粒度追踪。 |

---

## **功能需求趋势**
1. **IDE 集成稳定性**  
   - VS Code 扩展会话恢复 (#18993)、上下文窗口指示器缺失 (#24272) 等，凸显 IDE 插件需增强健壮性。
2. **沙箱与权限控制**  
   - Windows 沙箱 UAC 触发 (#24050)、Git 目录权限 (#19315) 反映跨平台沙箱设计需精细化。
3. **MCP 集成改进**  
   - 服务器级元数据传递 (#24166)、日志通知 (#18056) 推动标准化工具链支持。
4. **模型与上下文管理**  
   - 1M 上下文窗口请求 (#24031)、会话结束钩子 (#20374) 是长期优化方向。
5. **UI/UX 体验**  
   - 对话渲染抖动 (#23245)、锁屏计算机使用 (#24086) 需前端性能优化。

---

## **开发者关注点**
- **沙箱权限问题**：Windows 用户普遍抱怨沙箱行为不一致（如 #24050、#19315），需平衡安全性与开发便利性。
- **会话/上下文管理**：历史会话恢复 (#18993)、会话结束钩子 (#20374) 是工作流连续性的关键。
- **多 Agent 协作**：MultiAgentV2 子 Agent 执行超时 (#23296) 暴露分布式任务调度缺陷。
- **模型稳定性**：`gpt-5.5` 长推理卡顿 (#24260)、锁屏后崩溃 (#24086) 需底层优化。
- **安全与误报**：CLI 网络安全误报 (#23381) 影响合规场景，需规则引擎升级。

--- 

**数据来源：GitHub Issues/PRs (截至 2026-05-24)**

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

---

# **Gemini CLI 社区动态日报 | 2026-05-24**

---

## **今日速览**
- 过去24小时内无新版本发布，但活跃 Issue 和 PR 数量显著增加，主要集中在**文件索引、工具链稳定性、会话恢复、安全增强**等核心领域。
- 社区对**AST（抽象语法树）感知文件读取**和**会话上下文管理**的改进呼声较高，多个高优先级 PR 已提交修复。

---

## **版本发布**
> 无新 Release。

---

## **社区热点 Issues（精选10条）**

| # | 标题 | 重要性 & 社区反应 |
|----|----|----------------|
| **[27408](https://github.com/google-gemini/gemini-cli/issues/27408)** | **PDF 总结严重幻觉问题**<br>用户反馈 Gemini CLI 近期在 PDF 摘要时生成大量虚构内容，影响可信度。评论3次，需紧急修复。 | 高频用户痛点，直接影响核心功能体验。 |
| **[25166](https://github.com/google-gemini/gemini-cli/issues/25166)** | **Shell 命令执行后卡死**<br>命令完成后仍显示“等待输入”，导致会话阻塞。评论4次，👍3，涉及基础交互流程。 | 基础功能缺陷，影响开发者日常使用。 |
| **[22323](https://github.com/google-gemini/gemini-cli/issues/22323)** | **子代理超时后误报成功**<br>子代理在达到最大轮数后仍标记为成功，隐藏中断状态。评论6次，👍2，涉及任务可靠性。 | 关键逻辑错误，可能掩盖实际失败。 |
| **[20730](https://github.com/google-gemini/gemini-cli/issues/20730)** | **部分文件不可见/无法标记**<br>项目内随机文件未被索引，即使非 gitignored。评论11次，需排查索引机制。 | 高频反馈，影响代码导航与协作。 |
| **[22745](https://github.com/google-gemini/gemini-cli/issues/22745)** | **评估 AST 感知文件读取价值**<br>提案通过 AST 提升文件解析精度，减少 token 浪费。评论7次，👍1，性能优化方向。 | 技术前瞻性需求，可能重构工具链。 |
| **[26525](https://github.com/google-gemini/gemini-cli/issues/26525)** | **日志中敏感信息泄露风险**<br>Auto Memory 日志未确定性脱敏，需加强审计。评论3次，🔒维护者专属。 | 安全合规关键问题。 |
| **[22267](https://github.com/google-gemini/gemini-cli/issues/22267)** | **浏览器代理忽略 `settings.json` 配置**<br>如 `maxTurns` 设置被无视，导致行为异常。评论3次，需修复配置加载逻辑。 | 配置系统缺陷，影响自定义能力。 |
| **[21867](https://github.com/google-gemini/gemini-cli/issues/21867)** | **韩语推理质量骤降**<br>多语言支持不均衡，韩语提示词效果差。评论2次，需模型适配。 | 国际化短板，影响全球用户体验。 |
| **[27153](https://github.com/google-gemini/gemini-cli/pull/27153)** | **并发编辑同一文件冲突**<br>未加锁导致写入竞争，可能破坏文件完整性。PR 已提交修复。 | 数据一致性关键问题。 |
| **[27389](https://github.com/google-gemini/gemini-cli/pull/27389)** | **路由分类器引发函数响应错误**<br>历史修剪后出现 `400 Bad Request`，需调整序列化逻辑。 | API 兼容性修复。 |

---

## **重要 PR 进展（精选10条）**

| # | PR 标题 | 主要内容 |
|----|----|--------|
| **[27153](https://github.com/google-gemini/gemini-cli/pull/27153)** | **并发编辑文件加锁**<br>防止多线程修改同一文件导致数据损坏。 | 核心数据保护修复。 |
| **[27154](https://github.com/google-gemini/gemini-cli/pull/27154)** | **PTY 内存泄漏修复**<br>清理未释放的 PTY 句柄，解决文件描述符耗尽问题。 | 资源管理关键补丁。 |
| **[27137](https://github.com/google-gemini/gemini-cli/pull/27137)** | **`--skip-trust` 参数生效**<br>修复工作区信任标志未加载配置的 Bug。 | 命令行参数修复。 |
| **[26758](https://github.com/google-gemini/gemini-cli/pull/26758)** | **快照处理器指数级 token 泄漏**<br>过滤旧节点避免上下文膨胀。 | 性能优化。 |
| **[27398](https://github.com/google-gemini/gemini-cli/pull/27398)** | **ACP 协议版本兼容**<br>允许字符串协议版本输入，提升扩展性。 | 协议层改进。 |
| **[27406](https://github.com/google-gemini/gemini-cli/pull/27406)** | **可配置路由规则**<br>用户自定义复杂度-模型映射，替代硬编码阈值。 | 个性化功能增强。 |
| **[27147](https://github.com/google-gemini/gemini-cli/pull/27147)** | **PTY 依赖升级**<br>修复 macOS `/dev/ptmx` 泄漏问题。 | 底层稳定性修复。 |
| **[27391](https://github.com/google-gemini/gemini-cli/pull/27391)** | **会话恢复时过滤内部上下文**<br>避免 `<session_context>` XML 污染历史记录。 | 会话体验优化。 |
| **[27405](https://github.com/google-gemini/gemini-cli/pull/27405)** | **工具命令预解析**<br>在执行前解析 `tools.callCommand`，避免沙箱注入风险。 | 安全加固。 |
| **[26734](https://github.com/google-gemini/gemini-cli/pull/26734)** | **音频/WAV 数据处理修复**<br>修正嵌套 API 错误，提升媒体支持。 | 多媒体功能修复。 |

---

## **功能需求趋势**
从 Issues 提炼出以下社区最关注的方向：
1. **文件索引与导航**  
   - 随机文件不可见（[#20730](https://github.com/google-gemini/gemini-cli/issues/20730)）、AST 感知读取（[#22745](https://github.com/google-gemini/gemini-cli/issues/22745））。
2. **会话管理与恢复**  
   - 上下文持久化（[#22323](https://github.com/google-gemini/gemini-cli/issues/22323)）、会话迁移（[#22585](https://github.com/google-gemini/gemini-cli/pull/22585））。
3. **安全与合规**  
   - Auto Memory 日志脱敏（[#26525](https://github.com/google-gemini/gemini-cli/issues/26525)）、沙箱安全（[#27405](https://github.com/google-gemini/gemini-cli/pull/27405））。
4. **多语言与模型适配**  
   - 韩语支持（[#21867](https://github.com/google-gemini/gemini-cli/issues/21867））。
5. **性能与稳定性**  
   - Shell 卡死（[#25166](https://github.com/google-gemini/gemini-cli/issues/25166)）、PTY 泄漏（[#27154](https://github.com/google-gemini/gemini-cli/pull/27154））。

---

## **开发者关注点**
- **高频痛点**：  
  - 文件索引不全（影响代码理解）、会话卡死（阻塞开发流）、配置失效（如 `settings.json`）。
- **技术挑战**：  
  - AST 集成（提升工具精度）、并发控制（数据一致性）、API 限流（如 512 函数声明限制）。
- **安全需求**：  
  - 日志脱敏、沙箱隔离、OAuth 元数据验证（[#27139](https://github.com/google-gemini/gemini-cli/pull/27139)）。

--- 

**数据来源：GitHub [gemini-cli](https://github.com/google-gemini/gemini-cli)**

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

---

# GitHub Copilot CLI 社区动态日报（2026-05-24）

---

## **1. 今日速览**
- **v1.0.52 发布**：修复了非交互式子命令占用 `stdin`、Autopilot 模式权限提示异常等问题，并优化了主对话视图的滚动条支持。
- **社区活跃度高**：过去 24 小时内新增/更新 17 个 Issue，涉及 MCP 功能改进、跨平台兼容性、模型上下文配置等关键问题。
- **企业用户反馈集中**：多个 Issue 反映远程会话（`/remote on`）和自定义 MCP 注册表访问问题，需管理员介入解决。

---

## **2. 版本发布**
### **v1.0.52 (2026-05-23)**
- **修复**  
  - 非交互式子命令（如 `plugin list`、`mcp list`）不再意外消耗 `stdin`。  
  - Autopilot 模式下切换时不再触发工具/路径/URL 的冗余权限提示。  
- **优化**  
  - 主对话视图增加鼠标拖拽垂直滚动条支持。  
- **链接**: [Release Notes](https://github.com/github/copilot-cli/releases/tag/v1.0.52)

---

## **3. 社区热点 Issues**

| # | 标题 | 重要性 | 社区反应 | 链接 |
|---|------|--------|----------|------|
| **1477** | [area:models] "Continuing autonomously" 请求后模型完成异常 | 高频投诉（👍18） | 用户认为这是“免费午餐”结束后的预期行为，但部分场景疑似 Bug | [#1477](https://github.com/github/copilot-cli/issues/1477) |
| **3333** | Android/Termux 因 glibc 依赖无法运行 | 跨平台兼容性 | 影响 Termux 用户，评论中有人尝试降级 Node.js 临时解决 | [#3333](https://github.com/github/copilot-cli/issues/3333) |
| **2956** | `/mcp show` 菜单缺少“禁用 MCP”选项 | 功能完整性 | 用户希望提升操作可发现性（👍3） | [#2956](https://github.com/github/copilot-cli/issues/2956) |
| **2284** | `/add-dir` 目录权限未持久化 | 企业级需求 | 用户强烈要求跨会话保存（👍12） | [#2284](https://github.com/github/copilot-cli/issues/2284) |
| **3442** | v1.0.51 后远程会话被禁用 | 企业环境阻塞 | 需管理员手动启用，影响团队协作 | [#3442](https://github.com/github/copilot-cli/issues/3442) |
| **3436** | `/mcp search` 自定义注册表 URL 构造错误 | MCP 生态问题 | 导致自托管注册表 404，需修复 API 路径 | [#3436](https://github.com/github/copilot-cli/issues/3436) |
| **3488** | `config.json` 路径转义异常（`\.\` 或 `\L`） | 数据损坏 | Windows 用户报告信任文件夹配置丢失 | [#3488](https://github.com/github/copilot-cli/issues/3488) |
| **3496** | Timeline 单行文本复制失效 | UI 交互缺陷 | 仅单行复制异常，多行正常 | [#3496](https://github.com/github/copilot-cli/issues/3496) |
| **3494** | SKILL.md 描述超 1024 字符静默丢弃 | Agent Skills 兼容性问题 | 无警告/错误，影响技能加载 | [#3494](https://github.com/github/copilot-cli/issues/3494) |
| **3486** | `/mcp show` 工具列表无法滚动 | 用户体验 | 长工具列表需优化分页/滚动逻辑 | [#3486](https://github.com/github/copilot-cli/issues/3486) |

---

## **4. 重要 PR 进展**
| # | 标题 | 内容 | 状态 | 链接 |
|---|------|------|------|------|
| **2381** | install: 添加 Fish shell PATH 配置支持 | 修复 Fish 用户 PATH 写入问题（原方案无效） | 已合并 | [#2381](https://github.com/github/copilot-cli/pull/2381) |

---

## **5. 功能需求趋势**
- **MCP 生态增强**：用户期望更直观的 MCP 管理（如禁用选项）、工具列表展示优化及自定义注册表支持。
- **跨平台兼容性**：Android/Termux 和 Linux 终端复制粘贴问题突出。
- **企业级配置持久化**：`/add-dir` 权限、远程会话设置需跨会话保存。
- **模型与上下文控制**：`contextTier=long_context` 未生效，Rubber Duck 模式需指定模型。
- **Agent Skills 规范**：SKILL.md 长度限制引发静默丢弃问题。

---

## **6. 开发者关注点**
- **痛点**  
  - **权限与配置丢失**：目录权限、模型上下文未持久化，企业用户需频繁干预。  
  - **跨平台体验差**：Termux/Android 和 Linux 终端复制粘贴失效。  
  - **MCP 调试困难**：自定义注册表 URL 构造错误导致 404，缺乏日志提示。  
- **高频需求**  
  - **UI/UX 改进**：滚动条、复制粘贴、工具列表展示等交互问题。  
  - **透明化配置**：`/env` 应显示已加载扩展，避免 AI 回退到低效工具。  

--- 

**总结**：Copilot CLI 正面临企业级功能完善与跨平台体验优化的双重挑战，MCP 生态和模型控制是未来重点方向。

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

---

# **Kimi Code CLI 社区动态日报（2026-05-24）**

---

## **1. 今日速览**
过去24小时内，Kimi Code CLI 社区活跃度高，共提交 **8个 PR** 和 **5个新 Issues**，主要集中在 **MCP工具优化、日志管理、会话加载改进** 及 **用户交互增强**。开发者对多进程日志冲突（Windows平台）和会话历史加载效率问题尤为关注。

---

## **2. 版本发布**
无新版本发布。

---

## **3. 社区热点 Issues**

| # | 标题 | 重要性说明 | 链接 |
|---|------|------------|------|
| **2357** | [enhancement] Kimi Cli Web 应仅加载最新会话消息而非全部 | 提升会话切换体验，避免等待旧消息加载，直接影响用户效率 | [#2357](https://github.com/MoonshotAI/kimi-cli/issues/2357) |
| **2352** | 请求 `/thinking` 快捷命令与 `Ctrl+T` 快捷键 | 简化思考模式切换流程，减少操作步骤，高频功能需求 | [#2352](https://github.com/MoonshotAI/kimi-cli/issues/2352) |
| **2351** | Shell 模式命令历史需共享给 Agent 模式 | 解决多模式隔离痛点，提升自动化场景下的工作流连贯性 | [#2351](https://github.com/MoonshotAI/kimi-cli/issues/2351) |
| **2348** | Windows 多进程运行时 Loguru 旋转日志权限错误 | 关键平台兼容性修复，影响多实例部署稳定性 | [#2348](https://github.com/MoonshotAI/kimi-cli/issues/2348) |
| **2347** | 展示 `SessionStart Hook` 的 stdout 输出 | 增强 Hook 实用性，支持欢迎语/状态诊断等场景 | [#2347](https://github.com/MoonshotAI/kimi-cli/issues/2347) |

---

## **4. 重要 PR 进展**

| # | PR 标题 | 核心内容 | 链接 |
|---|--------|----------|------|
| **2356** | refactor(toolset): 后台始终加载 MCP 工具 | 优化工具初始化逻辑，避免阻塞主线程 | [#2356](https://github.com/MoonshotAI/kimi-cli/pull/2356) |
| **2355** | fix: 容忍延迟启动的 MCP 失败 | 允许交互式会话继续运行，即使部分 MCP 服务不可用 | [#2355](https://github.com/MoonshotAI/kimi-cli/pull/2355) |
| **2354** | fix: Windows 避免共享旋转日志 | 改用进程专属日志文件，解决多进程冲突问题 | [#2354](https://github.com/MoonshotAI/kimi-cli/pull/2354) |
| **2158** | feat(ui): 添加 `Ctrl+T` 显示思考内容 | 新增快捷键控制思考内容可见性，提升交互灵活性 | [#2158](https://github.com/MoonshotAI/kimi-cli/pull/2158) |
| **2353** | fix(web): 收紧应用布局间距 | 优化 Web UI 的视觉一致性，改善响应式体验 | [#2353](https://github.com/MoonshotAI/kimi-cli/pull/2353) |
| **2350** | fix: 兼容非 UTF-8 工作进程输出 | 解决 Windows 下字符编码导致的崩溃问题 | [#2350](https://github.com/MoonshotAI/kimi-cli/pull/2350) |
| **2349** | feat(mcp-conf): 项目级 MCP 配置合并策略 | 支持按项目覆盖全局配置，增强灵活性 | [#2349](https://github.com/MoonshotAI/kimi-cli/pull/2349) |

---

## **5. 功能需求趋势**
从 Issues 中提炼出以下高频方向：
- **会话管理优化**：按需加载消息（#2357）、Shell-Agent 数据互通（#2351）。
- **交互增强**：快捷命令/快捷键（#2352）、思考模式控制（#2158）。
- **日志与稳定性**：多进程日志隔离（#2348/#2354）、错误处理鲁棒性（#2350）。
- **Hook 扩展性**：`SessionStart` 输出展示（#2347），支持自定义工作流。

---

## **6. 开发者关注点**
- **跨平台兼容性**：Windows 多进程日志冲突（#2348）和字符编码问题（#2350）是主要痛点。
- **性能与体验**：会话加载效率（#2357）、工具初始化速度（#2356）直接影响生产力。
- **可观测性**：日志系统改进（如 #2354）和错误信息清晰度被多次提及。
- **工作流集成**：Shell/Agent 模式隔离（#2351）和 MCP 配置灵活性（#2349）是自动化场景的关键需求。

--- 

**总结**：本周社区聚焦于 **稳定性优化** 和 **交互效率提升**，尤其在 Windows 环境下的多进程支持和会话管理上进展显著。建议后续优先跟进日志系统和工具链的改进。

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

---

# **OpenCode 社区动态日报 | 2026-05-24**

---

## 📌 **今日速览**
- 社区聚焦**沙盒化 Agent 执行环境**（Issue #2242）和**语音输入功能需求**（Issue #4695），这两项获最多互动；
- 近期 PR 集中解决**工具输出截断问题**、**推理模式 UI 修复**，以及**LSP 超时优化**；
- 安全审查发现**潜在硬编码凭证风险**（Issue #29036）。

---

## 🔄 **版本发布**
无新版本发布。

---

## 🔥 **社区热点 Issues（Top 10）**

| Issue ID | 标题 | 重要性 & 社区反应 |
|---------|------|------------------|
| **[#2242](https://github.com/anomalyco/opencode/issues/2242)** | **Agent 沙盒化限制** | 核心安全需求，46 👍，34 评论。用户希望限制 Agent 的终端命令访问范围，类似 macOS `seatbelt`，目前仅部分模型支持。 |
| **[#4695](https://github.com/anomalyco/opencode/issues/4695)** | **语音输入功能** | 152 👍，31 评论。社区呼声最高，尤其适合“懒人”场景，已有开发者实现原型。 |
| **[#11313](https://github.com/anomalyco/opencode/issues/11313)** | **长命令输出截断问题** | 15 👍，影响工作流可靠性，导致 Agent 重试循环，需改进流式处理逻辑。 |
| **[#28732](https://github.com/anomalyco/opencode/issues/28732)** | **Gemini 签名缺失警告** | Vertex API 兼容性警告，可能影响多工具调用稳定性。 |
| **[#21911](https://github.com/anomalyco/opencode/issues/21911)** | **TS 泛型被剥离** | 7 评论，编辑工具破坏代码结构，需保留类型信息。 |
| **[#24610](https://github.com/anomalyco/opencode/issues/24610)** | **DeepSeek 思考模式开关** | 5 👍，用户希望手动关闭冗余推理输出，提升效率。 |
| **[#28618](https://github.com/anomalyco/opencode/issues/28618)** | **时钟偏差导致无限轮询** | 客户端与服务端时间不同步时引发异常，需同步机制。 |
| **[#29036](https://github.com/anomalyco/opencode/issues/29036)** | **安全审查：硬编码凭证** | 高风险，涉及 Stripe 密钥泄露，需立即修复。 |
| **[#29051](https://github.com/anomalyco/opencode/issues/29051)** | **推理模式选择器隐藏** | 桌面版 v2 提示框未显示模型变体选项，影响高级模型使用。 |
| **[#29033](https://github.com/anomalyco/opencode/issues/29033)** | **Sidecar 栈缓冲溢出崩溃** | Windows 下 CJK 路径导致 STATUS_STACK_BUFFER_OVERRUN，需内存安全修复。 |

---

## 🛠️ **重要 PR 进展（Top 10）**

| PR ID | 内容 |
|-------|------|
| **[#29047](https://github.com/anomalyco/opencode/pull/29047)** | **重试次数上限设为 5**，防止 Provider 持续失败导致的死循环。 |
| **[#29048](https://空)** | **空任务输出触发回退**，修复因空响应导致的工具链中断。 |
| **[#25649](https://github.com/anomalyco/opencode/pull/25649)** | **LSP 初始化超时延长**，适配 JDTLS/KotlinLS 项目索引耗时。 |
| **[#28950](https://github.com/anomalyco/opencode/pull/28950)** | **OpenAI 推理内容类型安全访问**，修复 `reasoning_content` 类型守卫。 |
| **[#29028](https://github.com/anomalyco/opencode/pull/29028)** | **推理标题与 Markdown 分离渲染**，优化 TUI 界面可读性。 |
| **[#29050](https://github.com/anomalyco/opencode/pull/29050)** | **v2 提示框恢复推理模式选择器**，修复桌面版 UI 缺陷。 |
| **[#29025](https://github.com/anomalyco/opencode/pull/29025)** | **原生 Provider 选项保留**，确保 DeepSeek/OpenAI 兼容性。 |
| **[#28458](https://github.com/anomalyco/opencode/pull/28458)** | **消息上下文时间戳增强**，修复历史消息仅显示时间的缺陷。 |
| **[#29052](https://github.com/anomalyco/opencode/pull/29052)** | **Amazon Bedrock Provider 升级**，更新至最新 SDK 版本。 |
| **[#29045](https://github.com/anomalyco/opencode/pull/29045)** | **LSP 测试迁移到 Effect 框架**，提升测试隔离性与可维护性。 |

---

## 📈 **功能需求趋势**
1. **安全与沙盒化**：Agent 权限控制（如 `#2242`）、硬编码凭证清理（`#29036`）；
2. **交互体验**：语音输入（`#4695`）、推理模式开关（`#24610`）、UI 修复（`#29051`）；
3. **工具链健壮性**：长命令输出处理（`#11313`）、Git 滥用问题（`#3176`）；
4. **多模型支持**：DeepSeek/Gemini 兼容性问题（`#28732`、`#21911`）；
5. **IDE 集成**：LSP 超时优化（`#25649`）、语法高亮扩展（`#28965`）。

---

## 💡 **开发者关注点**
- **调试与日志**：调试器配置问题（`#5443`）、错误循环（`#27924`）；
- **插件生态**：本地 LLM 连接（`#7078`）、MCP 内存服务集成（`#29022`）；
- **性能瓶颈**：上下文压缩失效（`#27924`）、时钟同步（`#28618`）；
- **跨平台兼容性**：Windows Sidecar 崩溃（`#29033`）、终端快捷键失效（`#25637`）。

--- 

**数据来源**：[anomalyco/opencode GitHub](https://github.com/anomalyco/opencode)

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

---

# Qwen Code 社区动态日报（2026-05-24）

---

## 1. **今日速览**
- 发布 `v0.16.1-nightly` 和 `v0.16.1` 版本，主要修复 TypeScript 构建问题、长会话内存泄漏及 CLI 扩展安装问题。
- Mode B 服务模式（`qwen serve`）功能基本就绪，但仍有部分生产化改进待完成。
- 新增 Feishu（Lark）通道适配器，支持 WebSocket/Webhook 交互卡片流式传输。

---

## 2. **版本发布**
### v0.16.1-nightly.20260524.84f408017  
- **修复**：清理 TS 构建时残留的 `.d.ts` 文件，避免 `TS5055` 错误 ([#4453](https://github.com/QwenLM/qwen-code/pull/4453))。

### v0.16.1  
- **核心改进**：  
  - 长会话 V8 堆内存优化，防止 OOM 崩溃 ([#4185](https://github.com/QwenLM/qwen-code/issues/4185))。  
  - CLI 扩展安装流程修复（如 Microsoft Claude Code 插件） ([#4452](https://github.com/QwenLM/qwen-code/issues/4452))。  
  - 环境变量在 `settings.json` 中的解析逻辑优化 ([#4466](https://github.com/QwenLM/qwen-code/issues/4466))。

---

## 3. **社区热点 Issues**

| Issue | 重要性 & 社区反应 |
|-------|------------------|
| [#4175](https://github.com/QwenLM/qwen-code/issues/4175) | **Mode B 生产化路线图**：37 条评论，核心团队正在推进，目标为 `v0.16` 文本/编码场景的本地部署。 |
| [#4185](https://github.com/QwenLM/qwen-code/issues/4185) | **长会话内存泄漏**：3 条评论，V8 堆压力导致 OOM，需优化 GC 策略。 |
| [#4452](https://github.com/QwenLM/qwen-code/issues/4452) | **扩展安装失败**：2 条评论，影响第三方插件集成体验。 |
| [#4421](https://github.com/QwenLM/qwen-code/issues/4421) | **本地诊断框架提案**：2 条评论，用户需更友好的问题复现与日志收集方案。 |
| [#4471](https://github.com/QwenLM/qwen-code/issues/4471) | **任务卡死 UI 问题**：1 条反馈，可能阻塞用户工作流。 |
| [#4466](https://github.com/QwenLM/qwen-code/issues/4466) | **环境变量解析缺陷**：1 条，影响 MCP 服务器配置安全性。 |
| [#4448](https://github.com/QwenLM/qwen-code/issues/4448) | `settings.json` 无效时的静默处理，需明确错误提示。 |
| [#4450](https://github.com/QwenLM/qwen-code/issues/4450) | `--list-extensions` CLI 命令无输出，影响插件管理。 |
| [#4419](https://github.com/QwenLM/qwen-code/issues/4419) | **文件名规范**：1 条，推动代码库统一 kebab-case 命名。 |
| [#4447](https://github.com/QwenLM/qwen-code/issues/4447) | **构建系统 Bug**：已关闭，修复 TS 构建残留文件问题。 |

---

## 4. **重要 PR 进展**

| PR | 关键内容 |
|----|--------|
| [#4379](https://github.com/QwenLM/qwen-code/pull/4379) | **Feishu/Lark 适配器**：支持 Webhook/卡片流式交互，实现上下文引用。 |
| [#4473](https://github.com/QwenLM/qwen-code/pull/4473) | **SDK 令牌回退机制**：完善 `QWEN_SERVER_TOKEN` 环境变量兼容性。 |
| [#4469](https://github.com/QwenLM/qwen-code/pull/4469) | **同步主分支到 daemon_mode_b_main**：为 `v0.16-alpha` 做准备。 |
| [#4472](https://github.com/QwenLM/qwen-code/pull/4472) | **ACP HTTP 流式传输**：新增 `/acp` 端点，兼容 Agent Client Protocol。 |
| [#4436](https://github.com/QwenLM/qwen-code/pull/4436) | **系统提示增强**：全局推理纪律与迭代规划优化。 |
| [#4422](https://github.com/QwenLM/qwen-code/pull/4422) | **TUI 布局重构**：紧凑视图 + Ctrl+O 转录冻结，对标 Claude Code。 |
| [#4402](https://github.com/QwenLM/qwen-code/pull/4402) | **流式工具调度**：分阶段实现工具调用信号传递。 |
| [#4394](https://github.com/QwenLM/qwen-code/pull/4394) | **项目级上下文文件**：支持 `.qwen/QWEN.local.md` 局部指令覆盖。 |
| [#4470](https://github.com/QwenLM/qwen-code/pull/4470) | **输入缓冲区竞态修复**：解决快速输入导致的闭包问题。 |
| [#4407](https://github.com/QwenLM/qwen-code/pull/4407) | **JSON 序列化改进**：保留重复对象引用，避免数据丢失。 |

---

## 5. **功能需求趋势**
- **性能优化**：长会话内存泄漏（OOM）、GC 策略改进是高频议题（[#4185](https://github.com/QwenLM/qwen-code/issues/4185)）。
- **扩展生态**：插件安装与管理（[#4452](https://github.com/QwenLM/qwen-code/issues/4452)、[#4450](https://github.com/QwenLM/qwen-code/issues/4450））。
- **本地化支持**：项目级上下文文件（`.qwen/QWEN.local.md`）和调试工具链（[#4421](https://github.com/QwenLM/qwen-code/issues/4421)）。
- **协议兼容**：ACP 流式传输、Feishu 适配器等外部集成需求增长。

---

## 6. **开发者关注点**
- **构建稳定性**：TS 构建残留文件问题（[#4447](https://github.com/QwenLM/qwen-code/issues/4447)）需自动化清理。
- **CLI 体验**：`settings.json` 错误静默处理（[#4448](https://github.com/QwenLM/qwen-code/issues/4448)）需明确反馈。
- **内存安全**：文件权限继承问题（[#4431](https://github.com/QwenLM/qwen-code/pull/4431)）影响共享写入场景。
- **调试工具**：内存泄漏诊断技能（[#4468](https://github.com/QwenLM/qwen-code/pull/4468)）需求迫切。

--- 

**数据来源**：[GitHub Qwen Code 仓库](https://github.com/QwenLM/qwen-code)

</details>

---
*本日报由 [Big Model Radar](https://github.com/ivanweng2077/big_model_radar) 自动生成。*