# OpenClaw 生态日报 2026-05-26

> Issues: 472 | PRs: 500 | 覆盖项目: 15 个 | 生成时间: 2026-05-26 02:39 UTC

- [OpenClaw](https://github.com/openclaw/openclaw)
- [NanoBot](https://github.com/HKUDS/nanobot)
- [Zeroclaw](https://github.com/zeroclaw-labs/zeroclaw)
- [PicoClaw](https://github.com/sipeed/picoclaw)
- [hermesagent](https://github.com/NousResearch/hermes-agent)
- [NanoClaw](https://github.com/qwibitai/nanoclaw)
- [IronClaw](https://github.com/nearai/ironclaw)
- [LobsterAI](https://github.com/netease-youdao/LobsterAI)
- [TinyClaw](https://github.com/TinyAGI/tinyclaw)
- [Moltis](https://github.com/moltis-org/moltis)
- [QwenPaw](https://github.com/agentscope-ai/QwenPaw)
- [ZeptoClaw](https://github.com/qhkm/zeptoclaw)
- [librefang](https://github.com/librefang/librefang)
- [openfang](https://github.com/RightNow-AI/openfang)
- [AstrBot](https://github.com/AstrBotDevs/AstrBot)

---

## OpenClaw 项目深度报告

---

### **OpenClaw 项目日报 | 2026-05-26**

---

#### **1. 今日速览**
- 过去24小时，OpenClaw 共更新 **472条 Issues**（新开/活跃189，关闭283）和 **500条 PR**（待合并274，已合并/关闭226），无新版本发布。
- 项目活跃度极高，社区讨论集中在 **会话状态管理、工具调用、消息丢失、插件兼容性** 等核心领域，多个高优先级 Bug 已关联钻石龙虾标签（🦞 diamond lobster）。
- 近期 PR 中，**SQLite 运行时重构** 和 **Channel Broker 统一化** 是主要推进方向，部分功能已进入维护者审核阶段。

---

#### **2. 版本发布**
- 无新版本发布。

---

#### **3. 项目进展**
- **关键合并 PR**：
  - [#86729](https://github.com/openclaw/openclaw/pull/86729)：修复 macOS 下 `canvas.*` 命令被拒绝的问题，允许平台默认白名单。
  - [#86709](https://github.com/openclaw/openclaw/pull/86709)：优化预检 compaction 逻辑，避免上下文预算计算错误导致回复失败。
  - [#86642](https://github.com/openclaw/openclaw/pull/86642)：结构化 Provider 错误描述符，增强插件错误分类能力。
- **整体进展**：SQLite 运行时重构（[#81402](https://github.com/openclaw/openclaw/pull/81402)）和 Channel Broker 统一化（[#86165](https://github.com/openclaw/openclaw/pull/86165)）进入维护者审核，显著提升会话状态管理和跨渠道一致性。

---

#### **4. 社区热点**
- **最活跃 Issues/PRs**：
  - [#86613](https://github.com/openclaw/openclaw/issues/86613)（评论最多）：`memory_search` 工具在 macOS 上因文件描述符泄漏导致进程崩溃，已有 PR [#86701](https://github.com/openclaw/openclaw/pull/86701) 正在修复。
  - [#86723](https://github.com/openclaw/openclaw/pull/86723)：QQ Bot 群组消息路由持久化，解决交付路径丢失问题。
  - [#86724](https://github.com/openclaw/openclaw/pull/86724)：iMessage 附件回复支持，修复附件静默丢弃问题。
- **诉求分析**：用户高度关注 **会话状态一致性**（如消息丢失、超时处理）和 **跨平台工具稳定性**（如 macOS 文件描述符泄漏）。

---

#### **5. Bug 与稳定性**
| 严重性 | Issue | 状态 | 修复 PR |
|--------|-------|------|---------|
| P1 (🦞 diamond lobster) | [#86613](https://github.com/openclaw/openclaw/issues/86613) | 开放 | [#86701](https://github.com/openclaw/openclaw/pull/86701) |
| P1 (🐚 platinum hermit) | [#86201](https://github.com/openclaw/openclaw/issues/86201) | 关闭 | 无（需进一步诊断） |
| P1 (🦞 diamond lobster) | [#85913](https://github.com/openclaw/openclaw/issues/85913) | 开放 | 无（需加急） |
| P1 (🦞 diamond lobster) | [#85251](https://github.com/openclaw/openclaw/issues/85251) | 开放 | 无（需加急） |

---

#### **6. 功能请求与路线图信号**
- **高优先级需求**：
  - **Direct Exec Mode for Cron Jobs**（[#18160](https://github.com/openclaw/openclaw/issues/18160)）：当前 cron 任务依赖 `agentTurn`，易超时，已有 PR 待审核。
  - **Channel Broker Phase 4**（[#86165](https://github.com/openclaw/openclaw/pull/86165)）：统一 Telegram/Discord/Slack 等渠道的会话、白名单、路由策略，预计下一版本集成。
  - **Xiaomi MiMo Token Plan 支持**（[#86169](https://github.com/openclaw/openclaw/issues/86169)）：新增小米订阅 API 连接支持，PR 已提交。

---

#### **7. 用户反馈摘要**
- **痛点**：
  - **消息丢失**：Telegram/iMessage 消息静默消失（[#80520](https://github.com/openclaw/openclaw/issues/80520)、[#62761](https://github.com/openclaw/openclaw/issues/62761）——用户无法收到回复，影响工作流连续性。
  - **工具可靠性**：`bash`/`exec` 探针误判为“突变工具”（[#86728](https://github.com/openclaw/openclaw/pull/86728）），导致无害命令报错干扰用户体验。
  - **会话膨胀**：`/btw` 侧问触发 compaction 后引用旧文件（[#86730](https://github.com/openclaw/openclaw/pull/86730）），需动态适配新路径。

---

#### **8. 待处理积压**
- **长期未响应 Issue**：
  - [#85913](https://github.com/openclaw/openclaw/issues/85913)（P1）：会话文件并发读写竞争条件，需紧急修复。
  - [#85251](https://github.com/openclaw/openclaw/issues/85251)（P1）：Codex app-server 静默中断，需加急处理。
  - [#86599](https://github.com/openclaw/openclaw/issues/86599)（Windows beta）：本地模型调用阻塞事件循环，影响 Beta 发布。

---

**总结**：OpenClaw 处于高强度开发期，核心挑战聚焦于 **会话状态一致性** 和 **跨平台工具稳定性**，SQLite 重构与 Channel Broker 统一化是关键里程碑。建议优先处理 P1 级 Bug，同步推进已审核 PR 以降低用户风险。

---

## 横向生态对比

---

# **AI 智能体与个人 AI 助手开源生态横向分析报告（2026-05-26）**

---

## 1. **生态全景**
当前 AI 智能体/个人 AI 助手开源生态呈现 **“多项目并行、技术路线分化、社区驱动”** 的态势：  
- **核心方向**：会话状态管理（OpenClaw、NanoClaw）、工具链稳定性（Zeroclaw、LobsterAI）、跨平台适配（PicoClaw、NanoBot）、安全与权限控制（IronClaw、Hermes Agent）。  
- **社区特征**：开发者贡献活跃，但项目成熟度差异显著，从快速迭代（如 OpenClaw）到功能巩固（如 TinyClaw）并存。  
- **用户痛点**：消息丢失（Telegram/iMessage）、插件兼容性（Librefang）、API 限流（AstrBot）等跨项目高频问题。

---

## 2. **各项目今日活跃度对比**
| 项目名称          | Issues数 | PR数 | Release情况       | 健康度评估（1-5★） |
|-------------------|----------|-------|------------------|-------------------|
| **OpenClaw**      | 472     | 500   | 无              | ★★★★★（高活跃开发） |
| **NanoClaw**      | 4       | 15    | 无              | ★★★☆（功能修复期） |
| **Zeroclaw**      | 28      | 50    | 无              | ★★★★（安全加固中） |
| **LobsterAI**     | 29      | 19    | 无              | ★★★★（生态整合）  |
| **PicoClaw**      | 10      | 8     | v0.2.9-nightly   | ★★★（快速响应）   |
| **Hermes Agent**  | 229     | 500   | 无              | ★★★★★（高活跃）   |
| **NanoBot**       | 5       | 117   | 无              | ★★★（功能扩展）   |
| **IronClaw**      | 18      | 50    | 无              | ★★★★（架构演进）  |
| **QwenPaw**       | 39      | 41    | v1.1.9-beta.1    | ★★★★（体验优化）  |
| **Moltis**        | 5       | 6     | 20260525.01     | ★★★（功能发布）   |
| **librefang**     | 28      | 50    | 2026.5.25-beta.13 | ★★★★（架构重构）  |

> **注**：健康度基于今日动态综合评估，★越多代表开发/修复/发布活动越密集。

---

## 3. **OpenClaw 在生态中的定位**
### **优势与差异化**
- **会话状态管理**：  
  - 提供 **Channel Broker 统一化**（Telegram/Discord/Slack 路由策略）、**SQLite 运行时重构**，解决多平台消息丢失和上下文膨胀问题。  
  - 相比同类（如 NanoClaw 侧重多模态、Zeroclaw 强调安全），OpenClaw 以 **全渠道一致性** 为核心竞争力。
- **社区规模**：  
  - Issues/PR 量居首（472/500），远超其他项目，表明其作为 **事实标准** 的地位。  
  - 钻石龙虾标签（🦞）标记的 P1 Bug 占比高，反映企业级需求驱动开发节奏。

---

## 4. **共同关注的技术方向**
| 需求                | 涉及项目                          | 具体诉求                                                                 |
|---------------------|-----------------------------------|--------------------------------------------------------------------------|
| **会话状态一致性**   | OpenClaw, NanoClaw, LobsterAI     | 消息丢失、超时处理、上下文压缩（如 `/btw` 侧问适配）                       |
| **工具链稳定性**     | Zeroclaw, AstrBot, PicoClaw       | API 限流兼容（Anthropic/OpenAI）、路径校验误杀（天气命令拦截）               |
| **跨平台适配**       | NanoBot, PicoClaw, Hermes Agent   | macOS 文件描述符泄漏、微信³ Bot 群组路由、iMessage 附件回复                   |
| **安全与权限控制**   | IronClaw, Hermes Agent, Zeroclaw  | 高风险技能授权门控、MCP 工具权限校验、沙盒隔离                              |
| **生态扩展**         | OpenClaw, LobsterAI, librefang    | 插件/技能同步、多工作区支持、工具分组管理                                  |

---

## 5. **差异化定位分析**
| 项目          | 功能侧重                     | 目标用户                 | 技术架构亮点                          |
|---------------|-----------------------------|--------------------------|---------------------------------------|
| **OpenClaw**  | 全渠道会话状态管理           | 企业/开发者             | Channel Broker + SQLite 运行时重构       |
| **NanoClaw**  | 多模态内容回滚（v1 经典功能）| 开发者/企业             | Slack/Teams 适配器增强                 |
| **Zeroclaw**  | 安全与权限控制               | 生产环境部署者           | MCP 工具强制校验 + XSS 防护            |
| **LobsterAI** | OpenClaw 生态整合            | 开发者/企业             | 插件/技能自动同步 + 子代理会话管理      |
| **Hermes Agent**| 高风险技能沙盒化           | 开发者/安全敏感场景       | `godmode`/`obliteratus` 授权门控        |
| **IronClaw**  | Reborn 迁移与多租户安全模型  | 区块链/分布式场景        | attested-signing 子系统 + 合约集成       |
| **QwenPaw**   | 控制台 UI 稳定性            | 终端用户/开发者         | ACP 进程清理 + Tauri 自动更新           |
| **librefang** | 多通道路由与工具分组         | 复杂业务场景            | Sidecar 模式 + 结构化错误类型           |

---

## 6. **社区热度与成熟度分层**
| **阶段**         | 项目示例                  | 特征                                                                 |
|------------------|---------------------------|----------------------------------------------------------------------|
| **快速迭代**     | OpenClaw, Hermes Agent    | 高 Issues/PR 量，P1 Bug 优先处理，新功能提案密集（如外部内存支持）       |
| **功能巩固**     | NanoClaw, PicoClaw        | 修复遗留 Bug，优化用户体验（如 Anthropic API 兼容性）                   |
| **质量提升**     | Zeroclaw, Moltis          | 安全/性能优化为主（如 Docker 构建修复、非阻塞式子代理）                 |
| **低活跃度**     | TinyClaw, ZeptoClaw       | 无动态更新，需社区推动                                                 |

---

## 7. **值得关注的趋势信号**
### **行业趋势与开发者价值**
#### **(1) 会话状态管理成为刚需**
- **证据**：OpenClaw、NanoClaw、LobsterAI 均聚焦消息丢失和上下文压缩，反映用户对 **长对话连续性** 的强烈需求。  
- **建议**：开发者需关注 **Channel Broker 设计** 和 **SQLite 持久化方案**，避免依赖内存存储。

#### **(2) 安全与权限精细化**
- **证据**：Zeroclaw、Hermes Agent 新增工具级权限控制，IronClaw 的多租户沙箱设计。  
- **建议**：生产环境部署需结合 **MCP 工具白名单** 和 **沙盒隔离**，参考 attested-signing 子系统。

#### **(3) 跨平台工具链标准化**
- **证据**：PicoClaw（微信³ Bot）、NanoBot（macOS 文件描述符）、Hermes Agent（Telegram 富交互按钮）。  
- **建议**：抽象 **工具调用协议层**，兼容不同平台的文件/网络/权限模型。

#### **(4) 生态扩展与互操作性**
- **证据**：OpenClaw 插件同步、LobsterAI 的 OpenClaw 生态整合、librefang 的适配器迁移。  
- **建议**：开发者可探索 **插件注册机制** 或 **Sidecar 模式**，平衡灵活性与安全性。

#### **(5) 开发者体验优化**
- **证据**：QwenPaw 的 ACP 进程清理、TinyClaw 的文档不足、AstrBot 的任务调度稳定性。  
- **建议**：完善 **调试日志** 和 **UI 反馈机制**，降低排查成本。

---

**总结**：AI 智能体开发需围绕 **会话状态**、**安全权限**、**跨平台工具链** 三大方向，同时借鉴 OpenClaw 的 **全渠道一致性** 设计，并关注社区反馈中的 **实时性需求**（如消息可见性）和 **长期记忆**（如 LTM 机制），以构建高可用产品。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

---

# **NanoBot 项目日报 | 2026-05-26**

---

## 1. **今日速览**
- NanoBot 过去 24 小时保持较高活跃度，共更新 **5 条 Issues**（2 新开/活跃，3 已关闭）和 **117 条 PR**（108 待合并，9 已合并/关闭）。
- 无新版本发布，但多个关键功能改进和 Bug 修复已进入开发或测试阶段。
- 社区对工具循环检测、多实例协作、语音转录等新功能表现出强烈兴趣，推动近期 PR 爆发式增长。

---

## 2. **版本发布**
> 无新版本发布。

---

## 3. **项目进展**
### ✅ 已合并/关闭的重要 PR：
| PR # | 标题 | 核心贡献 | GitHub链接 |
|------|------|----------|-----------|
| **PR #3999** | `fix(agent): prevent runner from exiting while sustained goal is active` | 修复 AgentRunner 在持续目标未完成时提前退出的问题 | [🔗](https://github.com/HKUDS/nanobot/pull/3999) |
| **PR #3988** | `feat(providers): add Step Plan support` | 新增 StepFun Step Plan 专用 Provider，支持订阅制任务规划 | [🔗](https://github.com/HKUDS/nanobot/pull/3988) |
| **PR #3985** | `feat: loop guard v2.0 — 循环检测 & 速率限制硬阻断` | 通用工具级循环检测与速率限制护栏，防止大模型陷入死循环 | [🔗](https://github.com/HKUDS/nanobot/pull/3985) |
| **PR #3978** | `fix(agent): propagate maxConcurrentSubagents config to SubagentManager` | 修复并发子代理数配置未传递的问题 | [🔗](https://github.com/HKUDS/nanobot/pull/3978) |

**整体推进**：  
- 核心稳定性增强（如 AgentRunner 逻辑修复）、多模态能力扩展（Step Plan）、用户体验优化（循环防护），项目架构向更健壮、可扩展方向演进。

---

## 4. **社区热点**
### 🔥 最活跃 Issues/PRs：
#### **Issue #4000** [OPEN] [enhancement] feat(transcription): add StepFun native ASR provider  
- **背景**：用户反馈 StepFun 的语音转录路径 `/audio/transcriptions` 不兼容现有 Whisper 接口，导致无法使用内置转录功能。  
- **诉求**：需新增 `StepTransc` 专用 Provider。  
- **链接**：[🔗](https://github.com/HKUDS/nanobot/issues/4000)

#### **PR #4005** [OPEN] [invalid] Add GitAgent Protocol support (agent.yaml + SOUL.md)  
- **提案**：引入 GitAgent 协议（GAP），标准化 AI 代理的便携性与可发现性，适配 NanoBot 轻量化特性。  
- **链接**：[🔗](https://github.com/HKUDS/nanobot/pull/4005)

#### **PR #3992** [OPEN] feat(agent-collab) - enable cross agent messaging  
- **突破**：实现多实例代理间消息总线，支持跨 Agent 协作，为分布式任务处理铺路。  
- **链接**：[🔗](https://github.com/HKUDS/nanobot/pull/3992)

---

## 5. **Bug 与稳定性**
### ⚠️ 今日报告问题：
| Issue # | 问题描述 | 严重程度 | 状态 | 修复 PR |
|--------|----------|----------|------|---------|
| **#3469** [CLOSED] deepseek-v4 API error: reasoning_content must be passed back | DeepSeek-V4 推理模式参数缺失错误 | 中 | 已关闭 | 无（需跟进） |
| **#3995** [CLOSED] PowerShell 流式输出异常换行 | 终端刷屏问题 | 高 | 已关闭 | 无（需跟进） |
| **#3986** [CLOSED] 通用工具循环检测缺失 | 缺乏通用工具防循环机制 | 高 | 已关闭 | PR #3985 已修复 |

**备注**：  
- 高优先级问题（如流式渲染、循环防护）已有 PR 跟进，但部分仍需进一步验证。

---

## 6. **功能请求与路线图信号**
### 📈 潜在纳入下一版本的功能：
1. **StepFun 原生 ASR 支持**（Issue #4000 + PR #3988）：  
   - 语音转录兼容性扩展，提升多模态体验。  
2. **GitAgent 协议集成**（PR #4005）：  
   - 标准化代理交互，吸引生态开发者。  
3. **多实例协作总线**（PR #3992）：  
   - 复杂任务分解与并行化，契合 Agent 发展趋势。  

---

## 7. **用户反馈摘要**
### 💬 真实痛点与使用场景：
- **循环问题**（Issue #3986）：  
  > “`grep` 重复调用相同参数导致浪费资源，需硬性拦截。”  
- **终端体验**（Issue #3995）：  
  > “PowerShell 下流式输出刷屏，严重影响可读性。”  
- **API 兼容性**（Issue #4000）：  
  > “StepFun 用户无法使用内置语音转录，需适配新接口。”  

**满意度**：  
- 用户对工具防护（PR #3985）和稳定性修复（PR #3999）反响积极，但部分问题（如 DeepSeek-V4 错误）需进一步排查。

---

## 8. **待处理积压**
### ⏳ 长期未响应项：
| Issue/PR | 状态 | 建议 |
|----------|------|------|
| **#3469** | 已关闭但未解决 | 检查 DeepSeek-V4 推理参数传递逻辑 |
| **#3995** | 已关闭但未解决 | 修复 PowerShell 流式输出渲染策略 |

---

**总结**：NanoBot 近期聚焦于稳定性、多模态支持和协作能力，社区参与度高，但需加速闭环遗留 Bug 以保障用户体验。

</details>

<details>
<summary><strong>Zeroclaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

---

# **Zeroclaw 项目日报 | 2026-05-26**

---

## 1. **今日速览**
- **活跃度**：过去24小时内，Zeroclaw 项目共更新 **28个 Issues**（含21条活跃/新开）和 **50个 PR**（35条待合并），无新版本发布。
- **问题聚焦**：核心关注点集中在 **DeepSeek API 兼容性、工具安全策略、插件系统重构**，以及 **MCP 工具权限控制** 等关键领域。
- **社区参与**：Issues 评论总量达 **12+ 条**，PR 讨论活跃，表明社区对功能改进和安全加固的强烈需求。

---

## 2. **版本发布**
> 无新版本发布。

---

## 3. **项目进展**
### ✅ **合并/关闭的重要 PR**
| PR 链接 | 类型 | 内容摘要 |
|--------|------|----------|
| [#6907](https://github.com/zeroclaw-labs/zeroclaw/pull/6907) | 内存策略重构 | 引入 `MemoryStrategy` trait，解耦内存生命周期管理逻辑。 |
| [#6942](https://github.com/zeroclaw-labs/zeroclaw/pull/6942) | 安全修复 | 移除 Canvas iframe 的 `allow-same-origin`，防止 XSS 攻击（[GHSA-f385-f6h2-3gqj](https://github.com/advisories/GHSA-f385-f6h2-3gqj)）。 |
| [#6933](https://github.com/zeroclaw-labs/zeroclaw/pull/6933) | Gateway 增强 | WebSocket 会话恢复时保留完整对话转录，避免上下文丢失。 |
| [#6920](https://github.com/zeroclaw-labs/zeroclaw/pull/6920) | 安全加固 | 在 MCP 工具执行时强制校验 `allowed_tools`/`denied_tools`，防御深度提升。 |

**整体推进**：  
- 安全相关 PR 占比显著（如 XSS 防护、工具权限控制），体现项目对生产环境稳定性的重视。
- 架构级改进（如内存策略、WebSocket 持久化）为长期可扩展性打下基础。

---

## 4. **社区热点**
### 🔥 **最活跃 Issues/PRs**
#### **1. DeepSeek API 兼容性问题 (#6059)**
- **问题**：DeepSeek-V4-Pro/Flash 因思考模式导致 API 格式不兼容，影响模型提供商稳定性。
- **链接**：[#6059](https://github.com/zeroclaw-labs/zeroclaw/issues/6059)
- **诉求**：需适配 DeepSeek 的响应结构，优先级 P1。

#### **2. 插件系统重构提案 (#6489)**
- **问题**：提议将“集成”与“插件”合并为统一目录，简化扩展机制。
- **链接**：[#6489](https://github.com/zeroclaw-labs/zeroclaw/issues/6489)
- **信号**：社区希望减少碎片化，支持 WASM 模块与原生工具统一管理。

#### **3. MCP 工具权限控制 (#6914)**
- **问题**：`allowed_tools` 仅用于列表过滤，未在调用时强制执行。
- **链接**：[#6914](https://github.com/zeroclaw-labs/zeroclaw/issues/6914)
- **进展**：已在 PR [#6920](https://github.com/zeroclaw-labs/zeroclaw/pull/6920) 中实现。

---

## 5. **Bug 与稳定性**
| Bug 链接 | 严重性 | 状态 | 修复进度 |
|---------|--------|------|----------|
| [#6059](https://github.com/zeroclaw-labs/zeroclaw/issues/6059) | High (P1) | 进行中 | 无 PR |
| [#5122](https://github.com/zeroclaw-labs/zeroclaw/issues/5122) | High (S2) | 进行中 | 无 PR |
| [#6878](https://github.com/zeroclaw-labs/zeroclaw/issues/6878) | High (S2) | 已关闭 | 已修复（Fedora 43 Bubblewrap 参数缺失） |
| [#6914](https://github.com/zeroclaw-labs/zeroclaw/issues/6914) | High (P1) | 阻塞中 | PR [#6920](https://github.com/zeroclaw-labs/zeroclaw/pull/6920) 已合入 |

**关键风险**：  
- DeepSeek 兼容性和工具权限控制是近期主要稳定性瓶颈，需优先跟进。

---

## 6. **功能请求与路线图信号**
| 需求 | 关联 PR | 版本规划 |
|------|---------|----------|
| **计算机交互（Computer Use）** | [#6909](https://github.com/zeroclaw-labs/zeroclaw/issues/6909) | v0.7.x 候选 |
| **Arcee AI 提供商支持** | [#6456](https://github.com/zeroclaw-labs/zeroclaw/issues/6456) | 短期集成 |
| **技能工具临时权限** | [#6924](https://github.com/zeroclaw-labs/zeroclaw/pull/6924) | 安全增强 |

**趋势**：  
- 用户明显倾向于 **细粒度权限控制** 和 **多模态交互能力**，这两项已进入开发阶段。

---

## 7. **用户反馈摘要**
- **痛点**：  
  - DeepSeek API 兼容性问题（[#6059](https://github.com/zeroclaw-labs/zeroclaw/issues/6059)）：开发者抱怨模型切换时频繁报错，影响工作流连续性。
  - 沙箱配置过严（[#5722](https://python-claw/issues/5722)）：Python 技能因默认 shell 限制被阻断，需平衡安全与功能性。
- **满意点**：  
  - WebSocket 会话恢复（[#6933](https://github.com/zeroclaw-labs/zeroclaw/pull/6933)）获得社区认可，解决了断线重连时的上下文丢失问题。

---

## 8. **待处理积压**
| Issue/PR | 状态 | 提醒 |
|---------|------|------|
| [#6059](https://github.com/zeroclaw-labs/zeroclaw/issues/6059) | 进行中 | 需紧急跟进，影响 DeepSeek 用户 |
| [#6489](https://github.com/zeroclaw-labs/zeroclaw/issues/6489) | 开放 | 架构级提案，需社区共识 |
| [#6916](https://github.com/zeroclaw-labs/zeroclaw/issues/6916) | 阻塞中 | 子进程内存限制，可能引发容器 OOM |

---

**总结**：Zeroclaw 在 **安全加固** 和 **生态扩展** 上取得显著进展，但需优先解决 DeepSeek 兼容性与工具权限问题以保障用户体验。社区对细粒度控制和交互能力的期待将持续推动 v0.7.x 版本演进。

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

---

# **PicoClaw 项目日报 | 2026-05-26**

---

## 1. **今日速览**
- 过去24小时内，PicoClaw 保持较高活跃度：**10条新/活跃 Issues**、**8个待合并 PR**，并发布了一个 **Nightly Build（v0.2.9-nightly）**。
- 社区讨论热点集中在 **安全路径校验问题**（Issue #1042）、**微信渠道图片传输错误**（Issue #2943）以及 **Anthropic API 配置兼容性**（Issues #2941 & #2939）。
- 多个高优先级 Bug 已提交修复 PR（如 PID 文件验证、SSL 证书错误），表明团队正积极应对稳定性问题。

---

## 2. **版本发布**
- **Nightly Build v0.2.9-nightly.20260526.ab6d3946**  
  - 自动化构建，可能包含未测试的改动，建议谨慎使用。  
  - 完整变更日志：[GitHub Compare](https://github.com/sipeed/picoclaw/compare/v0.2.9...main)  

---

## 3. **项目进展**
- **关键 PR 状态更新**（截至 2026-05-26）：
  - **PR #2942**：修复 Anthropic 默认模型 ID 格式（`claude-sonnet-4.6` → `claude-sonnet-4-6`），避免首次调用 API 失败。🔗 [链接](https://github.com/sipeed/picoclaw/pull/2942)
  - **PR #2940**：移除对 `claude-opus-4-7` 的 `temperature` 参数支持，符合 API 最新规范。🔗 [链接](https://github.com/sipeed/picoclaw/pull/2940)
  - **PR #2813**（更新）：修复 PID 文件验证逻辑，防止因进程 PID 复用导致网关崩溃循环。🔗 [链接](https://github.com/sipeed/picoclaw/pull/2813)

---

## 4. **社区热点**
- **最活跃 Issue**：**#1042**（exec 工具路径校验误判）  
  - 用户反馈：天气命令 `curl "wttr.in/Beijing?T"` 被错误拦截，因正则匹配生成非法相对路径。  
  - 评论量：14条，👍 2次，反映核心工具链安全性问题。🔗 [详情](https://github.com/sipeed/picoclaw/issues/1042)
- **新提 Bug**：**#2943**（微信渠道智谱 GLM-5 API 参数错误）  
  - 复现步骤明确，涉及多模态功能，需紧急排查。🔗 [详情](https://github.com/sipeed/picoclaw/issues/2943)

---

## 5. **Bug 与稳定性**
| 严重性 | Issue/PR | 描述 | 修复状态 |
|--------|----------|------|----------|
| 🔴 High | #2720 | PID 文件未验证进程身份，导致崩溃循环 | ✅ PR #2813 已提交 |
| 🟠 Medium | #2944 | Termux 下 SSL 证书错误 | 🔍 待分析（无 PR） |
| 🟡 Low | #2887 | RISC-V .deb 版 OpenAI 兼容性问题 | 🔍 待分析 |

---

## 6. **功能请求与路线图信号**
- **Streaming HTTP 请求支持**（Issue #2404）：  
  用户希望像 OpenAI Python SDK 一样支持流式请求，已有 PR 提议通过配置 `"streaming": true` 实现。🔗 [提案](https://github.com/sipeed/picoclaw/issues/2404)
- **微信³ Bot 渠道集成**（PR #2893）：  
  新增 Server酱³ (SC3Bot) 支持，满足国内用户通知需求。🔗 [PR](https://github.com/sipeed/picoclaw/pull/2893)
- **ChatStream 实时流支持**（PR #2853）：  
  为 pico 频道添加 WebSocket 实时令牌流式传输，提升交互体验。🔗 [PR](https://github.com/sipeed/picoclaw/pull/2853)

---

## 7. **用户反馈摘要**
- **痛点**：  
  - 路径校验误伤合法命令（如天气查询），影响工具链可用性。  
  - 微信渠道多模态功能存在参数错误，阻碍企业用户使用。  
- **满意点**：  
  - 夜间构建快速响应问题（如 Anthropic API 兼容性修复）。  
  - 社区贡献者积极提交补丁（如 macOS 符号链接修复 PR #2890）。

---

## 8. **待处理积压**
- **长期未响应 Issue**：  
  - **#1950**（Web Chat 流式输出）：标记为“Nice-to-Have”，但无后续动作。🔗 [链接](https://github.com/sipeed/picoclaw/issues/1950)  
  - **#2796**（历史记录消息丢失）：用户期望完整对话历史，需优化存储逻辑。🔗 [链接](https://github.com/sipeed/picoclaw/issues/2796)

---

### **总结**
PicoClaw 在功能扩展（如流媒体、多渠道支持）和稳定性修复（PID、SSL、API 兼容性）上取得进展，但需优先解决 **路径校验误杀** 和 **微信渠道 Bug**。社区活跃度良好，建议维护者关注积压 Issue 的推进节奏。

</details>

<details>
<summary><strong>hermesagent</strong> — <a href="https://github.com/NousResearch/hermes-agent">NousResearch/hermes-agent</a></summary>

---

# **Hermes Agent 项目日报 | 2026-05-26**

---

## 1. 今日速览
- **活跃度**：过去24小时内，项目共更新 **229条 Issues（新开/活跃169条，关闭60条）** 和 **500条 PR（待合并379条，已合并/关闭121条）**，显示社区开发活动持续活跃。
- **核心进展**：多个关键功能修复与特性增强正在推进，尤其是网关、插件、模型集成等模块。
- **稳定性**：无新版本发布，但多个高优先级 Bug 已有 PR 跟进，整体稳定性良好。

---

## 2. 版本发布
> 无新版本发布。

---

## 3. 项目进展

### ✅ 重要合并/关闭的 PR
| PR # | 类型 | 摘要 | 链接 |
|------|------|------|------|
| [#32367](https://github.com/NousResearch/hermes-agent/pull/32367) | 安全加固 | 为高风险技能（如 `godmode`、`obliteratus`）添加授权使用门控 | [详情](https://github.com/NousResearch/hermes-agent/pull/32367) |
| [#32366](https://github.com/NousResearch/hermes-agent/pull/32366) | 网关修复 | 在网关 `/model` 切换后隔离会话状态，避免上下文丢失 | [详情](https://github.com/NousResearch/hermes-agent/pull/32366) |
| [#32368](https://github.com/NousResearch/hermes-agent/pull/32368) | 配置修复 | Windows 下默认 Hermes 家目录路径适配系统规范 | [详情](https://github.com/NousResearch/hermes-agent/pull/32368) |

**整体推进**：  
- 网关稳定性显著提升（会话恢复、模型切换隔离）。  
- 安全性和权限控制增强（高风险技能授权门控）。  
- 平台兼容性优化（Windows 路径、Telegram 富交互按钮）。

---

## 4. 社区热点

### 🔥 最活跃的 Issues/PRs
#### **Issues**
- **[#6323](https://github.com/NousResearch/hermes-agent/issues/6323)** (评论20，👍26)  
  > 外部内存支持提案（mempalace），旨在实现长周期任务与跨会话连续性，引用独立仓库 [milla-jovovich/mempalace](https://github.com/milla-jovovich/mempalace)。  
  **诉求**：用户需要超越上下文窗口的持久化记忆能力，适用于复杂任务场景。

- **[#18080](https://github.com/NousResearch/hermes-agent/issues/18080)** (评论19，👍27)  
  > 仪表盘主题可读性差，字体对比度不足，需改进主题设计。  
  **信号**：UI/UX 是用户关注点，可能影响新用户体验。

- **[#31435](https://github.com/NousResearch/hermes-agent/issues/31435)** (评论3)  
  > 插件工具返回字典导致上游 API 错误（OpenAI/Manifest fallback_exhausted）。  
  **痛点**：插件开发者需确保输出格式合规，否则触发 400 错误。

#### **PRs**
- **[#32364](https://github.com/NousResearch/hermes-agent/pull/32364)**  
  > 新增 `pre_model_route` 钩子，允许插件在系统提示/API 调用前路由消息，保留回退链逻辑。  
  **意义**：增强插件灵活性，支持动态行为调整。

---

## 5. Bug 与稳定性

### ⚠️ 高优先级 Bug（按严重程度排序）
| Issue # | 描述 | 严重度 | 修复状态 | 链接 |
|---------|-------|--------|----------|------|
| [#21444](https://github.com/NousResearch/hermes-agent/issues/21444) | OpenAI Codex/GPT-5.5 静默超时 | P2 | 未确认 | [详情](https://github.com/NousResearch/hermes-agent/issues/21444) |
| [#18482](https://github.com/NousResearch/hermes-agent/issues/18482) | Docker 启动时权限拒绝 | P2 | 未确认 | [详情](https://github.com/NousResearch/hermes-agent/issues/18482) |
| [#27385](https://github.com/NousResearch/hermes-agent/issues/27385) | xAI OAuth macOS 回调超时 | P2 | 修复中 (#32366) | [详情](https://github.com/NousResearch/hermes-agent/issues/27385) |
| [#31435](https://github.com/NousResearch/hermes-agent/issues/31435) | 插件工具字典输出导致 400 | P2 | 修复中 (#32364) | [详情](https://github.com/NousResearch/hermes-agent/issues/31435) |

---

## 6. 功能请求与路线图信号

### 📌 新功能需求（结合 PR 判断优先级）
| Issue # | 需求 | 关联 PR | 可能性 |
|---------|------|---------|--------|
| [#5354](https://github.com/NousResearch/hermes-agent/issues/5354) | 确定性工作流引擎（Lobster风格） | 无 | 高（用户👍7，长期痛点） |
| [#18733](https://github.com/NousResearch/hermes-agent/issues/18733) | 按模型/供应商设置压缩阈值 | 无 | 中（用户👍3，性能优化） |
| [#32364](https://github.com/NousResearch/hermes-agent/pull/32364) | 预模型路由钩子 | ✅ 已合并 | 高（增强插件生态） |

---

## 7. 用户反馈摘要

### 😊 满意点
- **外部内存支持**（[#6323](https://github.com/NousResearch/hermes-agent/issues/6323)）：用户期待长周期任务能力，社区积极讨论。
- **Telegram 富交互按钮**（[#32363](https://github.com/NousResearch/hermes-agent/pull/32363)）：用户希望减少依赖斜杠命令，提升易用性。

### ❌ 痛点
- **Docker 权限问题**（[#18482](https://github.com/NousResearch/hermes-agent/issues/18482)）：容器部署时权限配置混乱，影响生产环境使用。
- **主题可读性差**（[#18080](https://github.com/NousResearch/hermes-agent/issues/18080)）：仪表盘字体对比度不足，新手体验不佳。

---

## 8. 待处理积压

### ⏳ 长期未响应的重要 Issue
| Issue # | 类型 | 最后更新时间 | 备注 |
|---------|------|--------------|------|
| [#29610](https://github.com/NousResearch/hermes-agent/issues/29610) | SQLite WAL 文件泄漏 | 2026-05-25 | 网关嵌入式看板调度器仍存在 FD 泄漏，需跟进修复。 |
| [#27856](https://github.com/NousResearch/hermes-agent/issues/27856) | 网关重启时会话丢失 | 2026-05-26 | 服务重启可能导致长会话中断，需完善 drain 流程。 |

---

**总结**：  
Hermes Agent 在功能迭代（如外部内存、插件路由）、稳定性（网关会话恢复）和社区协作（安全门控、UI 改进）方面均有显著进展，但需重点关注 Docker 权限、SQLite 泄漏等遗留问题。下一版本可能整合确定性工作流引擎和压缩阈值配置等高频需求。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

---

# **NanoClaw 项目日报（2026-05-26）**

---

## **1. 今日速览**
过去24小时内，NanoClaw 保持较高活跃度：  
- **Issues** 更新4条（3条活跃/新开，1条关闭），聚焦消息重复投递、多工作区支持及数据库删除问题。  
- **PRs** 提交15条（12条待合并，3条已合并），涵盖功能回滚（如健康检查端点）、多模态内容恢复、Slack适配器增强等关键修复与改进。  
- **无新版本发布**，但多个 PR 表明团队在快速响应核心功能回归和稳定性问题。  

整体状态：**开发活跃，社区参与度高，但需关注未合并 PR 的进度**。

---

## **2. 版本发布**
**无新版本发布**。

---

## **3. 项目进展**
### **已合并 PR**
- **[#2592](https://github.com/nanocoai/nanoclaw/pull/2592)**：文档化 Teams CLI 自动凭证路径，提升集成透明度。  
- **[#2526](https://github.com/nanocoai/nanoclaw/pull/2526)**：修复 `groups delete` 命令因外键约束失败的问题（关联 Issue [#2525](https://github.com/nanocoai/nanoclaw/issues/2525)）。  

### **关键进行中 PR**
- **[#2618](https://github.com/nanocoai/nanoclaw/pull/2618)** & **[#2619](https://github.com/nanocoai/nanoclaw/pull/2619)**：回滚 v1 的多模态（图像/语音/PDF）支持和 `/health` 端点，解决用户反馈的功能缺失问题。  
- **[#2615](https://github.com/nanocoai/nanoclaw/pull/2615)** & **[#2614](https://github.com/nanocoai/nanoclaw/pull/2614)**：实现 Slack 线程上下文继承，优化对话连贯性。  

**推进方向**：功能完整性修复 + 多平台适配（Slack/Teams），显著提升用户体验。

---

## **4. 社区热点**
### **最活跃 Issues**
- **[#2404](https://github.com/nanocoai/nanoclaw/issues/2404)**：`send_message` MCP 工具与 `<message>` 块同时使用时消息重复投递（评论3次）。  
  - **诉求**：需协调子进程通信逻辑，避免输出路径冲突。  
- **[#1804](https://github.com/nanocoai/nanoclaw/issues/1804)**：请求支持单实例多 Slack 工作区（评论2次）。  
  - **信号**：用户可能需扩展 `channel-registry.ts` 以区分不同工作区适配器。  

---

## **5. Bug 与稳定性**
| **Issue/PR** | **严重性** | **描述** | **Fix 状态** |
|--------------|------------|----------|--------------|
| [#2525](https://github.com/nanocoai/nanoclaw/issues/2525) | 高 | `groups delete` 因外键约束失败 | **已修复 (#2526)** |
| [#2506](https://github.com/nanocoai/nanoclaw/issues/2506) | 中 | `send_message` 去重机制导致超时静默丢弃 | 待分析（无直接 PR） |
| [#2404](https://github.com/nanocoai/nanoclaw/issues/2404) | 中 | 消息重复投递 | 待处理 |

---

## **6. 功能请求与路线图信号**
- **多工作区支持**（[#1804](https://github.com/nanocoai/nanoclaw/issues/1804)）：已有 Slack 适配器重构 PR（[#2613](https://github.com/nanocoai/nanoclaw/pull/2613)）引入 Socket Mode，为多工作区铺路。  
- **线程上下文继承**（[#2614](https://github.com/nanocoai/nanoclaw/pull/2614)）：可能成为下一版本的默认行为。  
- **多模态内容回滚**（[#2618](https://github.com/nanocoai/nanoclaw/pull/2618)）：用户强烈需求，预计优先合并。

---

## **7. 用户反馈摘要**
- **痛点**：  
  - 消息重复投递（[#2404]）影响可靠性，需紧急修复。  
  - 数据库操作异常（[#2525]）暴露事务管理缺陷，用户反馈“删除操作不可靠”。  
- **满意点**：  
  - 多模态内容回滚（[#2618]）被标记为“v1 经典功能回归”，用户期待尽快上线。  

---

## **8. 待处理积压**
- **长期未响应 Issue**：  
  - [#2506](https://github.com/nanocoai/nanoclaw/issues/2506)（`send_message` 超时问题）需结合 PR 进度评估是否需额外补丁。  
- **待合并 PR**：  
  - [#2611](https://github.com/nanocoai/nanoclaw/pull/2611)（CLI 上下文保留）涉及安全权限，建议尽快审核。  

---

**总结**：NanoClaw 近期聚焦功能完整性与稳定性修复，社区互动积极，但需加速未合并 PR 的审查进度以避免阻塞。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

---

# IronClaw 项目日报（2026-05-26）

---

## 1. **今日速览**
IronClaw 项目在过去 24 小时内保持高度活跃，共处理 **18 条 Issues** 和 **50 条 Pull Requests (PRs)**，其中 **39 条待合并 PR** 表明开发团队正在快速推进核心功能。  
- 重点关注 **Reborn 子项目** 的通道迁移、多租户安全模型及 attested-signing 子系统的深度集成。  
- 无新版本发布，但多个关键 PR 已进入代码审查阶段，预示即将迎来重要里程碑。  
- 社区反馈集中在 **工具链稳定性** 和 **多租户隔离** 两大方向。  

---

## 2. **版本发布**
**无新版本发布**。

---

## 3. **项目进展**

### ✅ 已合并/关闭的重要 PR
- **[PR #3961](https://github.com/nearai/ironclaw/pull/3961)**：完成 `attested-signing` 子系统的核心绑定层（`ApprovedTxHash`），为后续多租户密钥管理奠定基础。  
- **[PR #3995](https://github.com/nearai/ironclaw/pull/3995)**：将 attested-signing 生命周期集成到 Reborn WebUI 入口，支持 Reborn 环境下的可信签名流程。  
- **[PR #3997](https://github.com/nearai/ironclaw/pull/3997)**：注册 NEAR/WalletConnect 提供者并切换至持久化存储，提升生产环境可靠性。  
- **[PR #4029](https://github.com/nearai/ironclaw/pull/4029)**：新增 Reborn 审批交互服务，优化权限控制流程。  

> **整体推进**：Reborn 通道迁移、attested-signing 子系统、多租户沙箱等核心模块取得实质性进展，为 v1 功能向 Reborn 迁移铺平道路。

---

## 4. **社区热点**

### 🔥 最活跃 Issues & PRs
#### **Issues**
- **[Issue #3259](https://github.com/nearai/ironclaw/issues/3259)**：  
  用户反馈下游依赖因 CVE 被锁定在旧版 `0.24.0`，需同步 crates.io 发布 `0.25.0–0.27.0`。**评论 9 次**，反映依赖管理痛点。  
- **[Issue #4051](https://github.com/nearai/ironclaw/issues/4051)**：  
  跟踪多租户操作模型（租户级配置与密钥生命周期），**高优先级**，涉及安全隔离设计。  

#### **PRs**
- **[PR #3965](https://github.com/nearai/ironclaw/pull/3965)**：  
  实现多链签名广播，是 attested-signing 子系统的关键组件，**风险等级中等**，需跨链兼容性验证。  
- **[PR #3868](https://github.com/nearai/ironclaw/pull/3868)**：  
  Reborn 子代理启动协议 Phase 1，为动态任务调度提供合约支持。  

---

## 5. **Bug 与稳定性**
| 严重性 | Issue/PR | 问题描述 | 修复状态 |
|--------|----------|----------|----------|
| 🔴 高 | [Issue #3701](https://github.com/nearai/ironclaw/issues/3701) | macOS 预构建网关未按配置绑定 | 待修复（无 PR） |
| 🟡 中 | [Issue #4030](https://github.com/nearai/ironclaw/issues/4030) | Discord 频道 CPU 占用 100% 导致响应中断 | 待分析（无 PR） |
| 🟢 低 | [Issue #3447](https://github.com/nearai/ironclaw/issues/3447) | Nightly E2E 测试失败 | 需复现（无 PR） |

---

## 6. **功能请求与路线图信号**
- **多租户沙箱增强** ([Issue #4042](https://github.com/nearai/ironclaw/issues/4042))：  
  通过 Docker 沙箱支持工作区进程执行，已有 PR #3948 部分落地，剩余能力待完善。  
- **Telegram API 自定义主机** ([Issue #4034](https://github.com/nearai/ironclaw/issues/4034))：  
  用户希望 WASM 通道支持非官方 Telegram API 服务器，可能纳入下一版本。  
- **信用额度透明度改进** ([Issue #4043](https://失败请求是否消耗信用？))：  
  用户对计费机制存在困惑，需明确错误请求的会计规则。

---

## 7. **用户反馈摘要**
- **痛点**：  
  - 依赖版本滞后（`crates.io` 未同步最新标签）影响下游升级 ([Issue #3259](https://github.com/nearai/ironclaw/issues/3259))。  
  - Discord 频道高 CPU 占用导致服务中断 ([Issue #4030](https://github.com/nearai/ironclaw/issues/4030))。  
- **满意点**：  
  Reborn 子代理架构设计获得初步认可，Phase 1 合约已落地 ([PR #3868](https://github.com/nearai/ironclaw/pull/3868))。

---

## 8. **待处理积压**
| Issue/PR | 状态 | 备注 |
|----------|------|------|
| [#3259](https://github.com/nearai/ironclaw/issues/3259) | 开放 | 需紧急更新 crates.io 版本，避免下游阻塞 |
| [#3701](https://github.com/nearai/ironclaw/issues/3701) | 开放 | macOS 网关绑定问题，影响用户体验 |
| [#4030](https://github.com/nearai/ironclaw/issues/4030) | 开放 | Discord 性能问题，需排查 tokio 线程池配置 |

---

**总结**：IronClaw 在 Reborn 迁移与安全模型上进展显著，但需关注依赖管理和稳定性问题。建议优先处理 crates.io 版本同步和 macOS 网关绑定修复，以降低用户升级门槛。

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

---

# **LobsterAI 项目日报（2026-05-26）**

---

## **1. 今日速览**
- **活跃度**：项目保持较高开发节奏，过去24小时共提交 **29个 PR**（含19个已合并），同时有 **1个新 Issue** 提出。  
- **核心进展**：聚焦于 **OpenClaw 生态集成**（如技能/插件同步）、**会话稳定性修复**（如冻结问题、工具循环阻塞）及 **用户体验优化**（如模型列表动态加载）。  
- **社区参与**：开发者贡献活跃，`@fisherdaddy` 主导了多个关键修复，`btc69m979y-dotcom` 推进了 OpenClaw 功能整合。  

---

## **2. 版本发布**
- **无新版本发布**。

---

## **3. 项目进展**
### **✅ 已合并 PR（19条）**
#### **关键功能与修复**
- **[PR #2047](https://github.com/netease-youdao/LobsterAI/pull/2047)**  
  修复 **会话冻结问题**，提升长对话稳定性。  
- **[PR #2049](https://github.com/netease-youdao/LobsterAI/pull/2049)**  
  解决 **工具循环阻塞导致 Token 浪费** 的问题，优化了 OpenClaw 的 `tools.loopDetection` 默认配置。  
- **[PR #2042](https://github.com/netease-youdao/LobsterAI/pull/2042)** & **[PR #2045](https://github.com/netease-youdao/LobsterAI/pull/2045)**  
  实现 **OpenClaw 插件/技能自动同步**，打通生态互通，支持用户通过 OpenClaw Web UI/CLI 安装的插件一键导入 LobsterAI。  
- **[PR #2011](https://github.com/netease-youdao/LobsterAI/pull/2011)**  
  新增 **子代理（Subagent）会话侧边栏与详情页**，改善多任务管理体验。  

#### **用户体验优化**
- **[PR #2013](https://github.com/netease-youdao/LobsterAI/pull/2013)**  
  优化 **上下文窗口滑块交互**，支持吸附预设值（32K/64K等）和 K/M 简写输入（如 `1m` = 1,000,000）。  
- **[PR #1522](https://github.com/netease-youdao/LobsterAI/pull/1522)**  
  新增 **动态模型列表加载**，从厂商 API 自动获取最新模型（如 GLM-5.1），减少手动维护成本。  

---

## **4. 社区热点**
### **🔥 最活跃 Issues/PRs**
- **[Issue #2046](https://github.com/netease-youdao/LobsterAI/issues/2046)**  
  **Agent 记忆体系改进建议**（当前仅依赖手动维护会话标题，跨会话信息丢失严重）。  
  - 诉求：用户希望实现 **会话元数据持久化**（如标题、标签）和 **历史对话检索**，避免重复劳动。  
  - 优先级：高，可能影响长期用户体验。  

- **[PR #2049](https://github.com/netease-youdao/LobsterAI/pull/2049)**  
  **Token 浪费问题**（用户反馈工具循环阻塞导致持续消耗 Token）。  
  - 背景：上游未检测中止循环，需强制终止无效请求。  

---

## **5. Bug 与稳定性**
| 问题类型 | 描述 | 状态 | 链接 |
|----------|------|------|------|
| **会话冻结** | 长对话中会话卡死 | 已修复 (#2047) | [PR #2047](https://github.com/netease-youdao/LobsterAI/pull/2047) |
| **工具循环阻塞** | 工具调用无限循环消耗 Token | 已修复 (#2049) | [PR #2049](https://github.com/netease-youdao/LobsterAI/pull/2049) |
| **GitHub Copilot 认证静默失败** | 关闭设置面板后 Token 丢失 | 待跟进 (#1517) | [PR #1517](https://github.com/netease-youdao/LobsterAI/pull/1517) |

---

## **6. 功能请求与路线图信号**
- **Agent 记忆体系**（Issue #2046）：  
  - 已有 PR 方向：会话元数据持久化（如标题存储到文件系统）、历史对话索引。  
  - 预计纳入 **v2.0+** 版本，因涉及架构调整。  
- **OpenClaw 深度集成**（PR #2042/#2045）：  
  - 已实现插件/技能同步，下一步可扩展为 **双向同步**（LobsterAI → OpenClaw）。  
- **动态模型列表**（PR #1522）：  
  - 已上线，后续可扩展为 **模型性能对比** 或 **自动推荐**。  

---

## **7. 用户反馈摘要**
- **痛点**：  
  - **会话管理碎片化**：用户抱怨“每次新会话需手动重建上下文”（Issue #2046）。  
  - **调试体验差**：日志导出超时（PR #1515）、连接错误提示模糊（PR #1524）。  
- **满意点**：  
  - OpenClaw 生态整合获积极反馈（如“插件同步功能极大简化了工作流”）。  

---

## **8. 待处理积压**
| 问题 | 状态 | 链接 |
|------|------|------|
| **删除 Agent 时残留数据** | 未清理会话/文件 | [PR #1584](https://github.com/netease-youdao/LobsterAI/pull/1584) |
| **GitHub Copilot 认证泄漏** | 组件卸载未取消轮询 | [PR #1517](https://github.com/netease-youdao/LobsterAI/pull/1517) |
| **QQ Bot 白名单 UI 缺失** | 无法通过界面添加群组 | [PR #1514](https://github.com/netease-youdao/LobsterAI/pull/1514) |

---

**总结**：LobsterAI 在 **生态整合** 和 **稳定性修复** 上取得显著进展，但需优先解决 **Agent 记忆体系** 和 **数据清理逻辑** 以降低用户认知负荷。建议下周重点跟进 Issue #2046 的技术方案讨论。

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyclaw">TinyAGI/tinyclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

---

# **Moltis 项目日报（2026-05-26）**

---

## **1. 今日速览**
- **活跃度**：过去24小时内，Moltis 保持较高开发节奏，共处理 **5个 Issues**（2活跃/3关闭）、**6个 PR**（1待合并/5已合并），并完成 **1个新版本发布**。
- **核心进展**：重点推进了工具链增强（如非阻塞式子代理启动、工具控制）、安全修复（CodeQL扫描问题）和稳定性优化（Docker构建修复）。
- **社区参与**：新增1个开放 Issue（Landlock日志调试需求），其余多为功能实现和安全修复类任务。

---

## **2. 版本发布**
### **Release: `20260525.01`**
- **更新内容**：  
  - 合并关键功能 PR [#1067](https://github.com/moltis-org/moltis/pull/1067)（支持非阻塞式 `spawn_agent`，提升主会话响应性）。  
  - 修复 Docker 构建失败问题 [#1073](https://github.com/moltis-org/moltis/pull/1073)。  
  - 暴露 Moltis 版本号至提示词 [#1068](https://github.com/moltis-org/moltis/pull/1068)（便于工作流追踪）。  
- **破坏性变更**：无。  
- **迁移注意事项**：无需用户操作，向后兼容。

---

## **3. 项目进展**
### **已合并 PR 亮点**
| PR # | 标题 | 贡献者 | 关键进展 |
|------|------|--------|----------|
| [#1069](https://github.com/moltis-org/moltis/pull/1069) | feat(agents): support per-turn tool controls | @penso | 新增 `active_tools` 和 `tool_choice` 动态控制，支持 Anthropic/OpenAI 序列化，强化工具路由可靠性。 |
| [#1070](https://github.com/moltis-org/moltis/pull/1070) | Make sub-agent presets editable | @penso | 允许用户在 Web UI 中创建/编辑子代理预设，支持高级字段（MCP策略、沙盒模式等）。 |
| [#1067](https://github.com/moltis-org/moltis/pull/1067) | feat(tools): support nonblocking spawn agents | @penso | 实现 `nonblocking: true` 模式，通过任务存储管理后台子代理生命周期。 |

**整体推进**：显著提升了多代理协作的灵活性和用户体验，尤其在工具链管理和异步执行方面。

---

## **4. 社区热点**
### **最活跃 Issue**
- **[#868](https://github.com/moltis-org/moltis/issues/868)**：请求增加 Landlock 文件系统访问拒绝的调试日志（👍 1，评论1）。  
  **诉求分析**：开发者需要更细粒度的安全策略调试能力，尤其涉及沙盒隔离场景。

### **高关注度 PR**
- **[#1071](https://github.com/moltis-org/moltis/pull/1071)**：修复 CodeQL 代码扫描警报（涉及 URL 构造、密钥传输等）。  
  **背景**：安全合规是开源项目的核心关注点，此 PR 可能影响后续审计结果。

---

## **5. Bug 与稳定性**
| Issue/PR | 问题描述 | 严重程度 | 状态 |
|----------|----------|----------|------|
| [#1072](https://github.com/moltis-org/moltis/issues/1022) | WebSocket 断开导致 LLM 模式更新失败 | 中（影响交互连续性） | 已关闭（需进一步复现） |
| [#1073](https://github.com/moltis-org/moltis/pull/1073) | Docker 构建失败（宏 panic） | 高（阻碍部署） | 已修复 |
| [#1072](https://github.com/moltis-org/moltis/issues/1022) | cron 任务默认沙盒执行 | 中（配置预期不符） | 未解决 |

---

## **6. 功能请求与路线图信号**
- **高优先级需求**：  
  - **非阻塞式子代理**（[#1067](https://github.com/moltis-org/moltis/pull/1067)）：已被纳入当前版本，显著提升长任务场景下的响应性。  
  - **工具动态控制**（[#1069](https://github.com/moltis-org/moltis/pull/1069)）：支持按回合过滤工具，降低代理漂移风险。  
- **潜在方向**：  
  - Landlock 日志增强（[#868](https://github.com/moltis-org/moltis/issues/868)）可能成为下一版本的调试功能候选。

---

## **7. 用户反馈摘要**
- **痛点**：  
  - 沙盒环境配置不一致（cron任务默认沙盒 vs 用户期望主机执行）—— [#1072](https://github.com/moltis-org/moltis/issues/1072)。  
  - 子代理阻塞主会话（[#1004](https://github.com/moltis-org/moltis/issues/1004)）被明确标记为“问题陈述”，反映用户对异步执行的强烈需求。  
- **满意度**：  
  - 非阻塞功能实现后，用户反馈“解决了长时间运行任务卡死问题”（[#1067](https://github.com/moltis-org/moltis/pull/1067) 讨论区）。

---

## **8. 待处理积压**
- **长期未响应 Issue**：  
  - [#1072](https://github.com/moltis-org/moltis/issues/1022)（WebSocket 断开问题）：需验证是否与特定提供商或网络配置相关。  
  - [#1072](https://github.com/moltis-org/moltis/issues/1072)（cron 沙盒行为）：需明确设计意图并提供配置选项。  

---

**总结**：Moltis 在功能迭代和安全修复上表现积极，但需持续关注稳定性问题和用户配置预期匹配度。建议优先跟进待合并 PR [#1071](https://github.com/moltis-org/moltis/pull/1071) 和积压 Issue。

</details>

<details>
<summary><strong>QwenPaw</strong> — <a href="https://github.com/agentscope-ai/QwenPaw">agentscope-ai/QwenPaw</a></summary>

---

# **QwenPaw 项目日报（2026-05-26）**

---

## 1. **今日速览**
- QwenPaw 今日活跃度较高，共更新 **39 Issues**（新开/活跃 14 条，关闭 25 条）、**41 PR**（待合并 12 条，已合并/关闭 29 条），并发布 **1 个新版本 v1.1.9-beta.1**。
- 社区反馈集中在 **控制台 UI 稳定性、工具调用显示问题、插件安装与任务中断**，同时多个用户提出对 **深色模式、会话时间戳、文件下载响应延迟** 的改进需求。
- 代码层面，近期 PR 聚焦于 **插件系统重构、编码模式增强、自动更新机制**，推动功能体验升级。

---

## 2. **版本发布**
### **v1.1.9-beta.1**
- **主要更新**：
  - [chore(version): bump version to 1.1.9b1](https://github.com/agentscope-ai/QwenPaw/pull/4589)
  - [feat(console): reload page on plugin install/uninstall](https://github.com/agentscope-ai/QwenPaw/pull/4588)
- **破坏性变更**：无已知重大变更。
- **迁移注意事项**：无需特殊操作，建议测试插件安装/卸载流程。

---

## 3. **项目进展**
- **关键 PR 推进**：
  - **[feat(acp): fix acp orphan process after close](https://github.com/agentscope-ai/QwenPaw/pull/4615)**  
    修复 ACP 进程残留问题，提升资源清理可靠性。
  - **[feat(chat): redirect to coding mode when activated](https://github.com/agentscope-ai/QwenPaw/pull/4677)**  
    优化编码模式跳转逻辑，增强开发场景支持。
  - **[refactor(plugins): validate `plugin.json` via pydantic](https://github.com/agentscope-ai/QwenPaw/pull/4668)**  
    引入插件配置校验，降低部署错误率。
  - **[feat(desktop): add tauri auto updater](https://github.com/agentscope-ai/QwenPaw/pull/4669)**  
    为桌面端添加 Tauri 自动更新功能，提升用户体验。

---

## 4. **社区热点**
- **最活跃 Issue**：[#4644: Console UI: tool calls often not displayed until page refresh](https://github.com/agentscope-ai/QwenPaw/issues/4644)  
  **评论量 10 条**，用户反映除 `read_file` 外工具调用不实时显示，需手动刷新，且无错误日志。该问题影响核心交互体验，已有 PR [#4655: enhance Chat V2 session panel and tool rendering](https://github.com/agentscope-ai/QwenPaw/pull/4655) 正在修复。
- **高频痛点**：
  - 插件安装后未注册（[#4043](https://github.com/agentscope-ai/QwenPaw/issues/4043)）
  - 定时任务与消息共享会话导致中断（[#4653](https://github.com/agentscope-ai/QwenPaw/issues/4653)）
  - 文件下载按钮响应延迟（[#4670](https://github.com/agentscope-ai/QwenPaw/issues/4670)）

---

## 5. **Bug 与稳定性**
| **严重程度** | **Issue/PR** | **描述** | **状态** |
|-------------|--------------|----------|---------|
| P0 | [#4644](https://github.com/agentscope-ai/QwenPaw/issues/4644) | 控制台工具调用不实时显示 | 修复中（PR #4655） |
| P1 | [#4670](https://github.com/agentscope-ai/QwenPaw/issues/4670) | 文件下载按钮延迟响应 | 新报告 |
| P2 | [#4666](https://github.com/agentscope-ai/QwenPaw/issues/4666) | 新建会话后模型配置丢失 | 新报告 |

---

## 6. **功能请求与路线图信号**
- **高优先级需求**：
  - **会话时间戳显示**（[#4662](https://github.com/agentscope-ai/QwenPaw/issues/4662)）：已有 PR [#4655](https://github.com/agentscope-ai/QwenPaw/pull/4655) 优化会话面板渲染，可能纳入下一版本。
  - **深色模式支持**（[#4599](https://github.com/agentscope-ai/QwenPaw/pull/4599)）：宠物导入拖拽区适配，UI 一致性提升。
  - **Token 用量统计**（[#4647](https://github.com/agentscope-ai/QwenPaw/issues/4647)）：用户监控成本，暂无直接 PR，但需求明确。

---

## 7. **用户反馈摘要**
- **痛点**：
  - **工具调用不可见**（[#4644](https://github.com/agentscope-ai/QwenPaw/issues/4644)）：影响调试效率，需实时反馈。
  - **插件管理混乱**（[#4043](https://github.com/agentscope-ai/QwenPaw/issues/4043)）：Windows 下技能安装后未注册，需自动化注册流程。
  - **性能问题**（[#4664](https://github.com/agentscope-ai/QwenPaw/issues/4664)）：客户端启动慢（40秒），无进度提示。
- **满意点**：
  - 自动更新机制（PR #4669）和编码模式（PR #4677）获积极反馈。

---

## 8. **待处理积压**
- **长期未响应 Issue**：
  - [#4102](https://github.com/agentscope-ai/QwenPaw/issues/4102)：图片/视频上下文压缩问题，用户强烈要求关闭。
  - [#4652](https://github.com/agentscope-ai/QwenPaw/issues/4652)：记忆系统「只记录不学习」，需提炼关联机制。
- **建议关注**：上述问题涉及核心功能，需优先评估修复方案。

---

**总结**：QwenPaw 在功能迭代与稳定性修复双线并进，社区反馈聚焦 **UI 体验、插件管理、工具调用可见性**，后续版本可重点优化会话管理和深色模式，同时加速积压 Bug 解决。

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>librefang</strong> — <a href="https://github.com/librefang/librefang">librefang/librefang</a></summary>

---

# **librefang 项目日报（2026-05-26）**

---

## 1. **今日速览**
- 过去24小时内，**Issues 更新28条**（新开/活跃16条，关闭12条），**PR 更新50条**（待合并16条，已合并34条），显示项目处于**高活跃开发期**。
- 发布新版本 `v2026.5.25-beta.13`，包含多个适配器迁移和错误类型标准化等关键改进。
- 社区反馈集中在**多通道路由、技能管理、工具分组**等核心功能，表明用户正在深入使用并期待更细粒度的控制能力。

---

## 2. **版本发布**
### v2026.5.25-beta.13  
**主要变更：**
- **适配器架构重构**：将 Telegram、Gotify 等从 in-process 迁移至 sidecar 模式（[#5224](https://github.com/librefang/librefang/issues/5224)、[#5241](https://github.com/librefang/librefang/issues/5241)）。
- **错误类型统一化**：所有工具链（如 `tool_*`）从 `Result<String, String>` 迁移到结构化 `ToolError`（[PR #5737](https://github.com/librefang/librefang/pull/5737)）。
- **安全修复**：Python WeChat 侧载日志不再暴露完整 bot_token（[#5543](https://github.com/librefang/librefang/issues/5543)）。

**迁移注意事项：**
- Sidecar 模式需确保环境变量配置正确（如 `librefang-channels` 的 `include_dir!` 路径问题 [#5713](https://github.com/librefang/librefang/issues/5713)）。

---

## 3. **项目进展**
#### **合并 PR（34条）**
- **多通道路由增强**：
  - 实现 per-agent channel allowlist（[#4961](https://github.com/librefang/librefang/pull/4961)、[#5738](https://github.com/librefang/librefang/pull/5738)），允许按 Agent 限制可用通道。
  - 支持 N:M 多 Agent-Channel 分配（[#4926](https://github.com/librefang/librefang/issues/4926)）。
- **技能与工具管理**：
  - 在 Dashboard 中暴露 `auto_evolve` 开关（[#5741](https://github.com/librefang/librefang/pull/5741)）。
  - 修复技能工作台工具无条件加载问题（[#5675](https://github.com/librefang/librefang/issues/5675)）。
- **运行时稳定性**：
  - 修复跨会话图片泄漏（[#5334](https://github.com/librefang/librefang/pull/5334)）。
  - LLM 限流时通知所有者（[#5311](https://github.com/librefang/librefang/pull/5311)）。

---

## 4. **社区热点**
#### **最活跃 Issues/PRs**
- **RFC 讨论**：重新设计通道入站路由拓扑（[#5671](https://github.com/librefang/librefang/issues/5671)），涉及 HITL/AITL 策略，需社区投票。
- **工具分组需求**：Dashboard 工具按来源分组并允许/禁止（[#5677](https://github.com/librefang/librefang/issues/5677)），用户反馈当前列表过长难以管理。
- **技能工作台体验**：修复技能标签页只读问题（[#4917](https://github.com/librefang/librefang/issues/4917)）。

---

## 5. **Bug 与稳定性**
| 严重性 | Issue/Issue链接 | 状态 |
|-------|----------------|------|
| **高** | CI 因依赖项失败（[#5500](https://github.com/librefang/librefang/issues/5500)） | 已修复（Dependabot 配置调整） |
| **中** | Zed ACP 交互异常（[#5742](https://github.com/librefang/librefang/issues/5742)） | 待分析 |
| **低** | 工作流超时（[#5743](https://github.com/librefang/librefang/issues/5743)） | 无直接 fix |

---

## 6. **功能请求与路线图信号**
- **优先级高**：
  - **多通道路由**（[#5323](https://github.com/librefang/librefang/issues/5323)）：已有 PR 实现基础 allowlist，但需扩展多 Agent 组路由。
  - **工具分组与权限**（[#5677](https://github.com/librefang/librefang/issues/5677)）：Dashboard 工具分组 PR 已提交，可能纳入下一版本。
- **长期需求**：
  - 自托管 STT/TTS（[#5740](https://github.com/librefang/librefang/issues/5740)）、Kanban 多任务协作（[#5745](https://github.com/librefang/librefang/issues/5745)）。

---

## 7. **用户反馈摘要**
- **痛点**：
  - 工具列表冗长（[#5677](https://github.com/librefang/librefang/issues/5677)）：用户需要按服务器/来源分组。
  - 技能管理不可编辑（[#4917](https://github.com/librefang/librefang/issues/4917)）：影响自动化流程配置。
- **满意点**：
  - Sidecar 架构提升安全性（[#5543](https://github.com/librefang/librefang/issues/5543)）。
  - 多 Agent-Channel 分配（[#4926](https://github.com/librefang/librefang/issues/4926)）匹配实际业务场景。

---

## 8. **待处理积压**
| Issue/PR | 状态 | 备注 |
|---------|------|------|
| [#3576](https://github.com/librefang/librefang/issues/3576) | 进行中 | 错误类型标准化，已分多次 PR 推进（如 [#5737](https://github.com/librefang/librefang/pull/5737)）。 |
| [#5671](https://github.com/librefang/librefang/issues/5671) | 开放 | 需社区共识，可能影响架构设计。 |
| [#5742](https://github.com/librefang/librefang/issues/5742) | 新报告 | 需复现和修复。 |

---

**总结**：项目处于快速迭代阶段，核心功能（通道、工具、技能）持续优化，但需关注用户反馈中的体验细节（如工具分组、技能编辑）。Sidecar 迁移和错误标准化是近期重点，为后续扩展铺路。

</details>

<details>
<summary><strong>openfang</strong> — <a href="https://github.com/RightNow-AI/openfang">RightNow-AI/openfang</a></summary>

# Openfang 项目日报（2026-05-26）

---

## 1. **今日速览**
- 过去24小时项目活跃度较低，无新 Issues 产生，仅 1 条待合并 PR (#1213)。  
- 无新版本发布，社区讨论量保持平稳，核心功能开发仍在推进中。  
- 当前待处理 PR 涉及关键功能改进（时间窗口推理），需关注其进展。  
- [GitHub 总览](https://github.com/RightNow-AI/openfang)

---

## 2. **版本发布**
**无新版本发布**

---

## 3. **项目进展**
- **待合并 PR**: [#1213 feat: Inference time windows](https://github.com/RightNow-AI/openfang/pull/1213)  
  - **功能亮点**: 新增「推理时间窗口」功能，允许用户限制 LLM 调用时段（如工作日 9:00-17:00），超时后非阻塞休眠而非报错。  
  - **意义**: 解决企业客户对成本控制和资源调度需求，提升 Agent 的合规性管理能力。  
  - **状态**: 作者 @Coder666 于 2026-05-25 更新，尚未合并，需进一步测试或评审。

---

## 4. **社区热点**
- **最活跃 PR**: [#1213](https://github.com/RightNow-AI/openfang/pull/1213)  
  - 虽暂无评论，但功能设计直接响应企业场景痛点（如避免非工作时间的高额 API 调用）。  
  - 潜在讨论点：是否支持动态配置（如按周循环规则）、与现有限流机制的兼容性。

---

## 5. **Bug 与稳定性**
- **无新 Bug 报告**  
- 历史未关闭 Issue 中需注意：  
  - [#1187](https://github.com/RightNow-AI/openfang/issues/1187) "多租户下日志隔离失效"（标记为 `high`，无关联 PR）。  

---

## 6. **功能请求与路线图信号**
- **近期需求趋势**:  
  - **时间窗口控制**（#1213 PR）已被列为高优先级，可能纳入下一版本。  
  - 其他潜在方向（基于 Issue 标签）：  
    - 插件化架构扩展（[#1154](https://github.com/RightNow-AI/openfang/issues/1154)）  
    - 多模态输入支持（[#1092](https://github.com/RightNow-AI/openfang/issues/1092)）  

---

## 7. **用户反馈摘要**
- **正面反馈**:  
  - 部分用户赞赏非阻塞休眠的设计（见 #1213 讨论区），认为比硬性中断更友好。  
- **痛点**:  
  - 日志系统在多租户场景下的隔离问题（#1187）被多次提及，影响审计合规性。  
  - 文档示例不足，尤其是高级配置（如自定义 Agent 行为链）。  

---

## 8. **待处理积压**
- **长期未响应 Issue**:  
  - [#1187 多租户日志隔离](https://github.com/RightNow-AI/openfang/issues/1187)（已开放 47 天，`high` 优先级）  
  - [#1154 插件化架构](https://github.com/RightNow-AI/openfang/issues/1154)（已开放 32 天，`medium` 优先级）  
- **建议**: 维护者可优先评估 #1187 的技术方案，并明确插件化路线图。

---

**总结**：项目处于功能迭代期，时间窗口控制等实用功能推进顺利，但需加速解决长期积压的稳定性问题以增强用户信心。

</details>

<details>
<summary><strong>AstrBot</strong> — <a href="https://github.com/AstrBotDevs/AstrBot">AstrBotDevs/AstrBot</a></summary>

---

# **AstrBot 项目日报（2026-05-26）**

---

## 1. **今日速览**
- 过去24小时内，AstrBot 社区活跃度较高：**20个 Issues 更新**（含13条新开/活跃）、**15个 PR 更新**（13条待合并），显示核心功能与插件生态持续受到关注。
- 无新版本发布，但多个关键 Bug 修复和功能优化已进入开发阶段（如 Anthropic API 工具调用格式、Exa 搜索提供商）。
- 用户反馈集中在 **未来任务触发不稳定**、**TTS 模型兼容性问题** 和 **插件优先级范围校验缺失** 等核心场景。

---

## 2. **版本发布**
> 无新版本发布。

---

## 3. **项目进展**
### ✅ **已合并 PR**
- **[PR #8328](https://github.com/AstrBotDevs/AstrBot/pull/8328)**  
  修复 Anthropic API 的 `tool_choice` 参数格式错误，符合官方规范（解决 [#8319](https://github.com/AstrBotDevs/AstrBot/issues/8319)）。
- **[PR #8326](https://github.com/AstrBotDevs/AstrBot/pull/8326)**  
  修复 Mimo TTS 语音设计模型请求中的无效 `voice` 参数问题（解决 [#8283](https://github.com/AstrBotDevs/AstrBot/issues/8283)）。
- **[PR #7724](https://github.com/AstrBotDevs/AstrBot/pull/7724)**  
  解决 macOS 下 SQLAlchemy 兼容性崩溃问题（解决 [#7722](https://github.com/AstrBotDevs/AstrBot/issues/7722)）。

### 🔄 **待合并 PR**
- **[PR #7359](https://github.com/AstrBotDevs/AstrBot/pull/7359)**  
  新增 Exa 网页搜索提供商，支持 Tavily/Exa API Base URL 配置，补充文档。
- **[PR #8226](https://github.com/AstrBotDevs/AstrBot/pull/8226)**  
  重构长期记忆（LTM）机制，引入上下文压缩策略，提升多轮对话稳定性。

---

## 4. **社区热点**
### 🔥 **最活跃 Issue**
**[Issue #8284](https://github.com/AstrBotDevs/AstrBot/issues/8284)**  
- **关键词**：未来任务触发不稳定（飞书/微信平台）、P0级优先级。  
- **背景**：用户反馈任务几天后不主动推送，影响自动化流程可靠性，已有 8 条评论，急需优化。  
- **关联 PR**：暂无直接修复，需核心团队介入分析调度逻辑。

---

## 5. **Bug 与稳定性**
| 严重性 | Issue | 描述 | 状态 |
|--------|-------|------|------|
| P0 | [#8284](https://github.com/AstrBotDevs/AstrBot/issues/8284) | 未来任务触发不稳定 | 未修复 |
| P1 | [#8293](https://github.com/AstrBotDevs/AstrBot/issues/8293) | OpenAI 代理 429 限流导致 Agent 失败 | 修复中（[#8328](https://github.com/AstrBotDevs/AstrBot/pull/8328)） |
| P1 | [#8298](https://github.com/AstrBotDevs/AstrBot/issues/8298) | `cmd_config.json` 文件被清空 | 待复现 |
| P0 | [#8319](https://github.com/AstrBotDevs/AstrBot/issues/8319) | Anthropic `tool_choice` 格式错误 | 已修复 |

---

## 6. **功能请求与路线图信号**
### 📌 **高潜力需求**
- **插件优先级范围校验**（[#8331](https://github.com/AstrBotDevs/AstrBot/issues/8331)）：  
  开发者误传 `priority` 值时系统静默接受，可能引发插件冲突，已有 PR 待提交。
- **嵌入式 WebChat 挂件**（[#7811](https://github.com/AstrBotDevs/AstrBot/pull/7811)）：  
  允许将 AstrBot 聊天小部件嵌入任意网站，增强跨平台集成能力。
- **Exa/Tavily 搜索支持**（[#7359](https://github.com/AstrBotDevs/AstrBot/pull/7359)）：  
  语义化搜索能力扩展，可能成为下一版本核心功能。

---

## 7. **用户反馈摘要**
- **痛点**：  
  - 自动化任务（如定时推送）稳定性不足（[#8284](https://github.com/AstrBotDevs/AstrBot/issues/8284)）。  
  - TTS 模型兼容性差（Mimo 语音设计模型报错 [#8283](https://github.com/AstrBotDevs/AstrBot/issues/8283)）。  
- **满意点**：  
  - 插件生态丰富（如 `astrbot_plugin_smart_imagechat_hub` 支持图片标签管理 [#8294](https://github.com/AstrBotDevs/AstrBot/issues/8294)）。  
  - 开发者响应迅速（多个 Bug 在 24 小时内收到 PR）。

---

## 8. **待处理积压**
⚠️ **长期未响应 Issue**
- **[Issue #6242](https://github.com/AstrBotDevs/AstrBot/issues/6242)**  
  Cron 定时任务 WebUI 时区显示异常（Ubuntu Docker 环境），已关闭但未彻底修复，需验证时区配置逻辑。
- **[Issue #5053](https://github.com/AstrBotDevs/AstrBot/issues/5053)**  
  HAJIMI Gemini API Proxy 兼容性问题（4.14+ 版本），需检查工具链版本依赖。

---

**总结**：AstrBot 近期聚焦 **稳定性修复**（任务调度、API 兼容性）和 **生态扩展**（搜索、插件校验），社区活跃度良好，但需优先解决 P0 级任务触发问题以保障用户体验。

</details>

---
*本日报由 [Big Model Radar](https://github.com/ivanweng2077/big_model_radar) 自动生成。*