# OpenClaw 生态日报 2026-05-20

> Issues: 500 | PRs: 500 | 覆盖项目: 16 个 | 生成时间: 2026-05-20 03:26 UTC

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
- [EasyClaw](https://github.com/gaoyangz77/easyclaw)
- [librefang](https://github.com/librefang/librefang)
- [openfang](https://github.com/RightNow-AI/openfang)
- [AstrBot](https://github.com/AstrBotDevs/AstrBot)

---

## OpenClaw 项目深度报告

**OpenClaw 项目动态日报（2026-05-20）**

---

### 1. **今日速览**
过去24小时，OpenClaw 社区活跃度极高，共产生 500 条 Issues 和 PR 更新，其中活跃 Issue 达 439 条，合并 PR 38 个。项目在安全、会话稳定性及多平台支持方面持续推进，同时面临大量关于 API 密钥保护、跨平台兼容性（Linux/Windows）和流式响应中断的反馈。整体生态处于高互动、快速迭代状态。

---

### 2. **版本发布**
本日发布两个 Beta 版本：
- **v2026.5.19-beta.2**  
  - Agents 层明确修复策略应优先采用“清洁有界重构、精简内部逻辑、提供显式插件 SDK/API 废弃路径”。
  - 升级 `@openclaw/proxyline` 至 v0.3.3。
  - Pi 包升级至 v0.75.1，并将 Node.js 最低支持版本提升至 v22。
- **v2026.5.19-alpha.1**  
  内容同 beta.2，为早期测试分支。

> ⚠️ **迁移注意**：Node.js 版本要求已升至 v22，请确保运行环境兼容。

---

### 3. **项目进展**
今日无重大功能合并，但多个关键 PR 进入待审或就绪状态：
- **#84126**：修复 TUI 无法接收 message tool 内部源回复的问题，提升终端用户体验。
- **#84102**：统一 `SendMessage`/`content`/`text` 等别名字段为规范 `message`，避免模型输出被拒绝。
- **#84013**：修复 Telegram 隔离模式下轮询超时阈值未生效的问题，增强消息可靠性。
- **#84151**：解决 systemd 环境下更新助手因 cgroup 限制被杀死的缺陷。

这些改进聚焦于消息传递一致性、系统稳定性与跨平台适配，显著提升了生产环境可用性。

---

### 4. **社区热点**
以下 Issue 评论量最高，反映核心用户关切：
- **[#75] Linux/Windows Clawdbot Apps 缺失**（105 条评论，👍75）  
  用户强烈呼吁补充 Linux 和 Windows 原生应用，以匹配 macOS/iOS/Android 的功能完整性。此为长期未决需求，涉及跨平台架构重构。
- **[#18677] 安全扫描钩子 API 提案**（16 评论）  
  建议引入 `skill:before_install` 事件供安全工具拦截恶意技能安装，属前沿安全能力建设。
- **[#67035] Windows UI 回归问题：输入丢失、流回复不可见**（13 评论）  
  自 v2026.4.14 起出现的严重前端渲染缺陷，影响基础交互体验。

> 💡 趋势分析：用户对 **跨平台一致性** 和 **运行时安全性** 的关注持续升温，尤其关注密钥泄露与技能供应链风险。

---

### 5. **Bug 与稳定性**
按严重程度排序的关键问题：

| 等级 | Issue | 描述 | 是否有 Fix PR |
|------|-------|------|----------------|
| P1   | [#67035](https://github.com/openclaw/openclaw/issues/67035) | Windows 聊天 UI 输入吞字、流回复延迟/消失 | 无 |
| P1   | [#84059](https://github.com/openclaw/openclaw/issues/84059) | 升级后所有嵌入式运行抛出 `EmbeddedAttemptSessionTakeoverError` | 无 |
| P1   | [#83744](https://github.com/openclaw/openclaw/issues/83744) | Discord 进度状态残留导致后续回复被抑制 | 无 |
| P1   | [#80520](https://github.com/openclaw/openclaw/issues/80520) | Telegram 消息静默丢弃，无日志记录 | 无 |

此外，[#84038](https://github.com/openclaw/openclaw/issues/84038)（doctor --fix 误改配置致 token 暴增）已关联 PR 处理中。

> 🔧 当前最紧急：**会话文件锁竞争引发的嵌入式运行崩溃**（#84059），可能影响所有通道的连续对话能力。

---

### 6. **功能请求与路线图信号**
高频功能诉求包括：
- **敏感数据脱敏**（[#64046](https://github.com/openclaw/openclaw/issues/64046)）：配置文件、日志、UI 中明文存储 API key 引发安全担忧。
- **私有网络访问控制**（[#39604](https://github.com/openclaw/openclaw/issues/39604)）：允许 `web_fetch` 访问内网地址，需细粒度开关。
- **插件 UI 扩展系统**（[#66944](https://github.com/openclaw/openclaw/issues/66944)）：让插件可注入 Control UI 原生页面，提升可观测性。
- **MCP 服务器工具透传**（[#80909](https://github.com/openclaw/openclaw/issues/80909)）：MCP 配置的工具始终不出现在 LLM 请求中，阻碍外部工具集成。

结合现有 PR（如 #84409 媒体信任路径优化），可见项目正强化 **安全边界** 与 **可扩展性** 设计方向。

---

### 7. **用户反馈摘要**
- **痛点集中点**：
  - 多语言场景下 TTS/STT 缺乏 agent 级配置（[#66252](https://github.com/openclaw/openclaw/issues/66252)）。
  - 心跳机制变更导致 Telegram 阻塞（[#40611](https://github.com/openclaw/openclaw/issues/40611)）。
  - 浏览器自动化缺乏 CSS 选择器支持，流程繁琐（[#44431](https://github.com/openclaw/openclaw/issues/44431)）。
- **满意度亮点**：
  - 部分用户赞赏新 UI 框架的性能提升（Android PR #84414）。
  - 对模型回退通知机制表示欢迎（PR #69399）。

---

### 8. **待处理积压**
- **[#75] Linux/Windows App 缺失**：创建超5个月，仍无实质性推进，需产品决策优先级。
- **[#10687] 动态模型发现**：OpenRouter 等提供商模型列表频繁变动，静态 catalog 已不适用，亟需自动化发现机制。
- **[#8719] 安全配置文件 v1.1**：提出数据为中心的安全模型，含硬默认策略，长期待技术评审。

> 📌 建议本周会重点讨论上述三项积压项的资源分配。

--- 

*数据来源：GitHub openclaw/openclaw 仓库（截至 2026-05-20）*

---

## 横向生态对比

好的，作为专注于 AI 智能体与个人 AI 助手开源生态的技术分析师，我将基于您提供的数据生成一份横向对比分析报告。

---

### **AI 智能体/个人 AI 助手开源生态横向对比分析报告 (2026-05-20)**

#### **1. 生态全景**

当前，个人 AI 助手与自主智能体开源生态正处于**快速迭代与分化期**。OpenClaw 作为核心参照项目，展现出极高的活跃度与社区参与度，引领着安全、稳定性和跨平台适配的发展方向。与此同时，NanoBot、Zeroclaw、IronClaw 等项目在特定领域（如多模态支持、Reborn 架构、MCP 集成）持续深耕，形成了差异化竞争格局。整个生态呈现出从通用型向垂直场景专业化、从单体架构向分布式协同演进的清晰趋势。

#### **2. 各项目活跃度对比**

| 项目名称 | Issues 数 | PR 数 | Release 情况 | 健康度评估 |
| :------- | :-------- | :---- | :----------- | :--------- |
| **OpenClaw** | 439 (活跃) | 500 | v2026.5.19-beta.2 | **极高活跃度，高互动，快速迭代** |
| NanoBot | 31 | 35 | 无 | **较高活跃度，平稳演进** |
| Zeroclaw | 7 | 46 | 无 (v0.8.0 开发中) | **高度活跃，架构升级关键期** |
| PicoClaw | 8 | 18 | v0.2.8-nightly.20260520 | **稳健节奏，持续功能扩展** |
| hermesagent | 210 | 500 | 无 | **极高活跃度，社区参与度极高** |
| NanoClaw | 4 | 23 | 无 | **高度活跃，WhatsApp 优化密集** |
| IronClaw | 24 | 50 | 无 | **高度活跃，Reborn 模块落地** |
| LobsterAI | 2 | 31 | 无 | **较高活跃度，UI/UX 优化并行** |
| TinyClaw | 0 | 0 | 无 | **无活动** |
| Moltis | 4 | 4 | 无 | **中等活跃度，稳定性维护为主** |
| QwenPaw | 42 | 44 | v1.1.8, v1.1.8-beta.2 | **极高活跃度，新功能发布密集** |
| ZeptoClaw | 0 | 2 | 无 | **低活跃度，依赖更新为主** |
| EasyClaw | 0 | 0 | 无 | **无活动** |
| librefang | 18 | 50 | 无 | **较高活跃度，CI/CD 问题频发** |
| openfang | 2 | 3 | 无 | **中等活跃度，成本与集成优化** |
| AstrBot | 23 | 17 | 无 | **较高活跃度，插件生态活跃** |

#### **3. OpenClaw 在生态中的定位**

*   **优势：**
    *   **核心参照地位：** 作为“核心参照”，OpenClaw 拥有最高的社区活跃度（439条活跃 Issue，500条 PR），是其他项目学习和比较的基准。
    *   **全面性与深度：** 其 Issue 和 PR 覆盖了安全、会话稳定性、多平台支持、API 密钥保护、流式响应中断等几乎所有核心方面，显示出其在功能完备性和技术深度上的领先地位。
    *   **生产环境可用性：** 多个关键 PR 聚焦于消息传递一致性、系统稳定性与跨平台适配，显著提升了其在生产环境中的可用性。
*   **技术路线差异：**
    *   OpenClaw 似乎更侧重于构建一个**高度稳定、安全且跨平台兼容的底层运行时和通信框架**，为上层应用提供坚实的基础。
    *   相比之下，其他项目如 NanoBot 更注重网关性能和多模态支持，Zeroclaw 专注于 Reborn 架构升级，IronClaw 则强调 MCP/WASM 工具集成，QwenPaw 突出插件生态和桌面宠物，AstrBot 强化群聊互动和 SubAgent。
*   **社区规模对比：**
    *   OpenClaw 无疑是**社区规模最大的项目**，其 Issue 和 PR 数量远超其他项目，反映出庞大的用户基础和开发者贡献者群体。

#### **4. 共同关注的技术方向**

*   **安全性与密钥管理：**
    *   **OpenClaw:** API 密钥保护、安全扫描钩子 API 提案 (#18677)。
    *   **hermesagent:** OAuth 令牌刷新失败、网关认证绕过 (#26093)。
    *   **NanoClaw:** channel approval 权限作用域强化 (#2566)。
    *   **IronClaw:** legacy extension v2 清单校验、第三方与内置包权限区分 (#3794, #3795)。
    *   **librefang:** CI 安全扫描失败 (#5296)。
    *   **openfang:** 默认配置安全性、自动代理加载机制的成本问题 (#1206)。
*   **多模态与模型支持：**
    *   **NanoBot:** Skywork 模型支持、StepFun 图像生成服务集成、重构图像生成模块。
    *   **PicoClaw:** Xiaomi Mimo 多模态（含视频）及推理内容流的支持、DeepSeek 流式响应中 reasoning_content 修复。
    *   **hermesagent:** Ollama 集成优化、Gemini 模型并行调用工具参数拼接错误修复。
    *   **QwenPaw:** OpenCode Go 模型集成、免费多模态路由功能请求。
    *   **LobsterAI:** OpenHuman 引擎集成建议。
*   **MCP (Model Context Protocol) 集成：**
    *   **IronClaw:** 推进 OpenFang 工具面通过 MCP 桥接暴露给 Claude Code。
    *   **QwenPaw:** 为远程 MCP 服务器添加 OAuth 2.1 认证流程。
    *   **librefang:** 多密钥轮换机制（credential pools for multi-key per-provider rotation）。
*   **会话管理与持久化：**
    *   **OpenClaw:** 会话文件锁竞争引发的嵌入式运行崩溃 (#84059)、Telegram 消息静默丢弃 (#80520)。
    *   **NanoBot:** WebUI 会话打印错乱 (#3790)、对话自动关闭 (#3884)。
    *   **Zeroclaw:** ACP Session Restore (#6543)。
    *   **PicoClaw:** 命令行会话管理命令 (/status, /compact, /new)。
    *   **hermesagent:** Telegram DM topic binding 未刷新 (#20470)、会话压缩导致循环 (#20470)。
    *   **NanoClaw:** Agent 上下文压缩后输出格式异常 (#2561)。
*   **WebUI/UX 优化：**
    *   **OpenClaw:** Windows UI 回归问题：输入丢失、流回复不可见 (#67035)。
    *   **NanoBot:** WebUI 会话打印错乱 (#3790)、对话自动关闭 (#3884)。
    *   **Zeroclaw:** Web UI reload banner 对齐问题 (#6776)。
    *   **PicoClaw:** 命令行会话管理 UX 增强。
    *   **hermesagent:** TUI 字符重排序、WebUI 设置中心升级。
    *   **QwenPaw:** Markdown 表格渲染缺陷、飞书渠道集成问题。
    *   **LobsterAI:** 子代理会话侧边栏展示与详情页、悬浮滚动按钮。
    *   **AstrBot:** 群聊消息流上下文模式、SubAgent 功能增强。

#### **5. 差异化定位分析**

| 项目名称 | 功能侧重 | 目标用户 | 技术架构 |
| :------- | :------- | :------- | :------- |
| **OpenClaw** | 核心运行时、跨平台通信、安全、稳定性 | 企业级部署、需要高可靠性的开发者 | 模块化、显式插件 SDK/API，Node.js v22+ |
| **NanoBot** | 网关性能、多模态支持、WebUI 体验 | 追求高性能和丰富多模态能力的用户 | 提供者抽象层、Per-file modules |
| **Zeroclaw** | Reborn 架构、Multi-Agent Runtime、Schema V3 | 探索下一代智能体架构的研究者和高级用户 | 零信任运行时体系、模块化、可扩展 |
| **PicoClaw** | 轻量化部署、国产 AI 模型适配、多模态 | Raspberry Pi 等资源受限设备用户、国产模型爱好者 | 配置驱动的提供者级流式输出 |
| **hermesagent** | 高度可定制、CLI/TUI、技能生态 | 开发者、研究人员、重度自定义需求用户 | 高度模块化、插件系统 |
| **NanoClaw** | WhatsApp 通道稳定性、权限边界、Agent Network | WhatsApp 重度用户、寻求分布式智能体的用户 | 跨容器协作、资源共享 |
| **IronClaw** | Reborn 模块、MCP/WASM 工具集成、E2E 测试 | 企业级部署、需要强大工具和测试框架的用户 | 能力组合、身份隔离、生命周期管理 |
| **LobsterAI** | Cowork 协作框架、多 Agent 编排、UI/UX | 团队协作、复杂任务处理的用户 | 子代理会话可视化、多模型供应商兼容性 |
| **TinyClaw** | 无活动 | - | - |
| **Moltis** | Docker 沙箱稳定性、WebSocket 连接 | 容器化部署、MCP 服务实例用户 | Docker 沙箱、RPC over WebSocket |
| **QwenPaw** | 官方插件分发、桌面宠物、模型支持 | 希望丰富功能和娱乐性的普通用户 | 插件市场、MCP 集成、多模型支持 |
| **ZeptoClaw** | GitHub Actions 依赖更新 | 维护者、CI/CD 自动化用户 | 常规依赖更新 |
| **EasyClaw** | 无活动 | - | - |
| **librefang** | 通道适配器迁移、内核修复、密钥管理 | 需要多通道接入和密钥轮换的用户 | Sidecar 模式、配置标准化 |
| **openfang** | 自动代理加载、MCP 桥接、执行环境限制 | 企业级部署、成本控制敏感用户 | MCP 桥接、执行环境限制 |
| **AstrBot** | 群聊互动、SubAgent、插件生态 | 群聊用户、游戏爱好者、垂直场景需求用户 | 插件系统、SubAgent 功能 |

#### **6. 社区热度与成熟度**

*   **快速迭代阶段：**
    *   **OpenClaw:** 极高活跃度，每日数百条 Issue 和 PR，持续快速迭代。
    *   **hermesagent:** 极高活跃度，社区参与度极高，功能快速推进。
    *   **QwenPaw:** 极高活跃度，新版本发布频繁，社区讨论热烈。
    *   **NanoClaw:** 高度活跃，WhatsApp 优化和功能请求响应迅速。
    *   **IronClaw:** 高度活跃，Reborn 模块落地，功能持续推进。
*   **质量巩固阶段：**
    *   **NanoBot:** 较高活跃度，但更侧重于性能和稳定性优化。
    *   **Zeroclaw:** 高度活跃，但处于架构升级关键期，可能更关注新功能的稳定性。
    *   **PicoClaw:** 稳健节奏，持续功能扩展，注重稳定性。
    *   **LobsterAI:** 较高活跃度，UI/UX 优化并行，注重用户体验。
    *   **librefang:** 较高活跃度，但 CI/CD 问题频发，可能需要更多时间巩固质量。
*   **维护性任务为主：**
    *   **ZeptoClaw:** 低活跃度，仅依赖更新。
    *   **EasyClaw, TinyClaw:** 无活动。

#### **7. 值得关注的趋势信号**

*   **MCP 成为核心集成标准：** IronClaw、QwenPaw、librefang 等项目都在积极拥抱 MCP，将其作为工具暴露和集成的标准协议，预示着未来 AI 智能体将更加开放和可互操作。
*   **安全边界与密钥管理日益重要：** 多个项目（OpenClaw, hermesagent, NanoClaw, IronClaw, librefang, openfang）都报告了与安全相关的问题或提出了安全增强功能，表明在生产环境中，安全性和密钥管理已成为不可忽视的核心挑战。
*   **多模态能力持续深化：** NanoBot、PicoClaw、hermesagent、QwenPaw 等项目都在积极扩展对多模态输入（音视频）和图像生成的支持，反映了市场对 AI 理解和处理多样化信息的需求增长。
*   **分布式与协作智能体架构兴起：** Zeroclaw 的 Multi-Agent Runtime、NanoClaw 的 Agent Network、IronClaw 的 Reborn 架构以及 LobsterAI 的多 Agent 编排，都指向了从单体智能体向分布式、协作式智能体系统的演进趋势。
*   **用户体验与交互精细化：** 从 OpenClaw 的 TUI 修复、NanoBot 的 WebUI 优化、QwenPaw 的桌面宠物、LobsterAI 的子代理会话可视化到 AstrBot 的群聊互动插件，都体现了开发者对用户交互体验的持续关注和精细化打磨。
*   **生产环境稳定性与健壮性成为焦点：** 大量 Bug 报告集中在会话管理、进程稳定性、API 调用可靠性等方面，说明项目在走向生产环境时，稳定性和健壮性是需要重点攻克的难题。

**对 AI 智能体开发者的参考价值：**

*   **关注 MCP 生态：** 尽早了解和集成 MCP，将为未来的工具链扩展和与其他 AI 助手的互操作性打下基础。
*   **重视安全与密钥管理：** 在设计之初就应考虑安全的密钥存储、传输和使用机制，避免潜在的安全风险。
*   **规划多模态能力：** 如果应用场景涉及图片、音频、视频等非文本信息，应提前规划多模态处理能力。
*   **探索分布式架构：** 对于复杂任务或需要高可用性的场景，可以考虑采用分布式或协作式智能体架构。
*   **持续优化用户体验：** 无论是 CLI、TUI 还是 WebUI，都应注重交互的流畅性、直观性和错误处理的友好性。
*   **投入资源解决稳定性问题：** 确保核心功能的稳定性和健壮性是吸引和留住用户的关键。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

**NanoBot 项目动态日报（2026-05-20）**

---

### 1. **今日速览**
过去24小时内，NanoBot 社区活跃度较高，共处理了31条 Issue 更新与35条 PR 动态。项目整体运行平稳，无新版本发布，但多个关键功能模块持续优化中。开发者重点推进了网关性能、多模态支持及 WebUI 体验改进，同时积极响应用户反馈的稳定性问题。社区讨论集中于会话管理、MCP 工具集成和跨平台兼容性，显示出项目在复杂场景下的持续演进。

---

### 2. **版本发布**
无新版本发布。

---

### 3. **项目进展**
今日合并的重要 PR 包括：
- **[#3918] feat: optimize gateway cold start from ~4.6s to ~480ms**  
  将网关冷启动时间缩短近90%，显著提升用户体验，尤其在低资源环境或频繁重启场景中表现突出。[链接](https://github.com/HKUDS/nanobot/pull/3918)

- **[#3916] feat(providers): add Skywork first-level support**  
  新增对 Skywork AI 模型（如 skyclaw-v1）的官方支持，扩展了 OpenAI 兼容接口下的可选模型范围。[链接](https://github.com/HKUDS/nanobot/pull/3916)

- **[#3910] feat(image-generation): add StepFun provider support**  
  集成阶跃星辰 StepFun 图像生成服务，支持 step-image-edit-2 等模型，增强多模态能力。[链接](https://github.com/HKUDS/nanobot/pull/3910)

- **[#3914] refactor(image-generation): split providers into per-file modules**  
  重构图像生成模块结构，提升可维护性与扩展性，为后续接入更多提供商奠定基础。[链接](https://github.com/HKUDS/nanobot/pull/3914)

这些进展表明项目正稳步推进架构优化与新能力集成，尤其在性能、多模态和第三方生态方面取得实质性突破。

---

### 4. **社区热点**
最活跃的 Issue 包括：
- **[#3790] WebUI会话-打印内容显示错乱**（14条评论）  
  用户报告在最新源码更新后，WebUI 会话输出出现排版错乱，需刷新页面恢复。此问题影响核心交互体验，可能涉及前端渲染逻辑或流式响应处理缺陷。[链接](https://github.com/HKUDS/nanobot/issues/3790)

- **[#1123] 163.com 邮箱 IMAP "SELECT Unsafe Login" 问题修复方案**（4条评论）  
  深入分析了网易邮箱的安全策略限制，并提出通过发送 `ID` 命令绕过限制的技术方案，体现了用户对邮件通道稳定性的高度关注。[链接](https://github.com/HKUDS/nanobot/issues/1123)

- **[#3884] WebUI - The conversation closes after the first response**（2条评论）  
  新发现的问题：首次回复后对话自动关闭，疑似 WebSocket 连接中断或状态管理异常。[链接](https://github.com/HKUDS/nanobot/issues/3884)

此外，[#3921] `/insights` 命令提案获得关注，反映用户对 token 使用追踪和成本管理的强烈需求。

---

### 5. **Bug 与稳定性**
按严重程度排序的关键 Bug：
1. **[#3790] WebUI 会话打印错乱**（高）— 影响核心交互，暂无公开 fix PR，需优先排查前端渲染逻辑。
2. **[#3884] WebUI 对话自动关闭**（高）— 新发问题，可能与 WebSocket 生命周期管理有关。
3. **[#3863] 微信无法登录（版本过低提示）**（中）— 用户即使升级微信仍报错，推测为 NanoBot 内嵌微信协议兼容性问题，已有 issue 记录但未闭环。
4. **[#3907] DeepSeek 思考模式逐词换行显示**（中）— 流式推理内容未做行缓冲合并，导致 UI 展示混乱，属展示层优化问题。

目前尚无针对 #3790 和 #3884 的修复 PR 提交，建议纳入本周优先级任务。

---

### 6. **功能请求与路线图信号**
- **持久化记忆（Persistent Memory）**：[#3888] 提出集成 Mnemon 实现跨会话记忆，虽为外部集成，但反映用户对长期上下文保留的迫切需求。
- **Token 使用洞察**：[#3921] 提议添加 `/insights` 命令用于查询历史 token 消耗，直接回应社区对成本透明化的诉求。
- **Signal 渠道支持**：[#3852] 新增 Signal 聊天机器人通道，显示项目正积极拓展主流通讯平台覆盖。
- **MPP 支付协议原生支持**：[#2845] 提出内置 Machine Payments Protocol 工具，虽尚未行动，但体现对自动化服务调用的前沿探索。

结合近期 PR，**多模态输入（音视频）** 和 **本地模型部署指南完善** 成为明确路线图方向。

---

### 7. **用户反馈摘要**
- **正面反馈**：用户对网关启动速度优化表示认可；Skywork 等新模型支持受到欢迎；WebUI 设置中心升级提升了配置体验。
- **负面痛点**：
  - 会话历史无限增长导致 bot 无响应（[#2638], [#3029]），暴露内存管理机制缺陷；
  - MCP 工具更新后未自动刷新（[#2325], [#1552]），需手动重启，影响开发效率；
  - Feishu 语音消息下载失败（[#1607]）、Docker 构建依赖 SSH 密钥（[#1699]）等问题反映环境适配不足；
  - Telegram 重复回复（[#1692]）、Ollama API 支持缺失（[#193]）影响多平台一致性。

整体情绪偏向建设性批评，多数用户愿意参与测试并提供详细复现步骤。

---

### 8. **待处理积压**
- **[#2604] Make memory consolidation fully asynchronous / proactive GC**（创建于 2026-03-29，2条评论）  
  提议将内存整理异步化以避免阻塞 LLM 请求，是解决会话膨胀问题的根本方案之一，长期悬而未决。[链接](https://github.com/HKUDS/nanobot/issues/2604)

- **[#2463] Architectural issue: prompt prefix preservation**（创建于 2026-03-25，11条评论）  
  指出当前对话历史存储方式与实际发送给模型的 prompt 不一致，属架构级隐患，虽已标记 stale，仍需评估重构必要性。[链接](https://github.com/HKUDS/nanobot/issues/2463)

建议维护团队在下一迭代周期优先处理上述两项结构性问题，以巩固系统健壮性。

--- 

*数据来源：GitHub API · 统计时间：2026-05-20 00:00–24:00 UTC*

</details>

<details>
<summary><strong>Zeroclaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

**Zeroclaw 项目动态日报（2026-05-20）**

---

### 1. **今日速览**  
ZeroClaw 在今日保持高度开发活跃度，共处理 46 个 PR 更新与 7 个 Issue 动态。核心进展聚焦于 v0.8.0 集成分支的多通道架构优化、内存管理修复及安全策略升级。社区对“技能系统 UX”和“离线执行模式”表现出持续关注，多个高优先级功能请求进入待实现队列。整体项目健康度良好，主干稳定性受控。

---

### 2. **版本发布**  
无新版本发布。当前主力开发分支为 `integration/v0.8.0`，预计将作为 Beta 候选版本进行最终测试。

---

### 3. **项目进展**  
- **PR #6776（已合并）**：修复了 Web UI 中 reload banner 的对齐问题，提升用户体验一致性。  
- **PR #6777（待合并）**：修复了 `SqliteMemory::purge_namespace` 错误使用 `category` 列而非 `namespace` 的问题，直接影响内存清理逻辑的正确性。  
- **PR #6398（待合并）**：v0.8.0 核心功能 —— Multi-Agent Runtime 与 Schema V3 架构升级，涵盖 40+ 模块依赖更新，标志着零信任运行时体系向模块化、可扩展方向迈出关键一步。

> ✅ 项目正稳步推进至 v0.8.0 发布阶段，主要架构变更集中在运行时抽象层与跨通道通信协议标准化。

---

### 4. **社区热点**  
- **Issue #5849**：提出“Dream Mode”——空闲时自动进行记忆 consolidation 与 reflective learning，获 10 条评论，反映用户对长期知识沉淀与智能体自主进化的强烈期待。  
- **Issue #6293**：呼吁引入 air-gapped execution mode 与 companion daemon over unix socket，强调企业级安全隔离需求，目前状态为 `blocked`，需维护者介入评估可行性。  
- **PR #6398**：作为 v0.8.0 基石，虽评论数较少但影响深远，涉及全栈重构，作者 @singlerider 明确标注“寻求批准”，社区可在此提交具体反馈。

> 🔍 热点背后诉求：增强 AI 智能体的自主认知能力（Dream Mode）、强化生产环境安全性（Air-Gap）、统一多通道身份验证机制（AllowlistAspect 迁移）。

---

### 5. **Bug 与稳定性**  
| 严重等级 | Issue/PR | 描述 | 状态 |
|--------|--------|------|------|
| S2 | [Issue #6801](https://github.com/zeroclaw-labs/zeroclaw/issues/6801) | `purge_namespace` 误删 `category` 列数据 | ✅ 已有 Fix PR #6777 |
| S1 | [Issue #6771](https://github.com/zeroclaw-labs/zeroclaw/issues/6771) | SecurityPolicy 阻止自身技能调用（HEREDOC 被拦截） | ⚠️ 暂无公开修复方案 |

> 💡 建议：S1 级安全策略自指问题需紧急审查，可能暴露沙箱规则过度严格的设计缺陷。

---

### 6. **功能请求与路线图信号**  
- **Dream Mode（#5849）**：虽未列入 v0.8.0，但其“周期性记忆整合”理念与现有 cron/heartbeat 机制兼容，有望纳入后续 v0.9.x。  
- **ACP Session Restore（#6543）**：已由社区贡献者实现并关闭，表明 ACP v1 协议支持正在加速落地。  
- **AllowlistAspect 统一迁移计划（系列 PRs）**：来自 ICSE 2027 M1 研究项目的系统性重构，目标减少 147 LOC 重复代码，提升可维护性，预示未来将全面推广共享 aspect 架构。

> 📌 下一版本重点方向：技能系统 UX 优化（#6253）、多通道认证统一化、离线安全执行环境。

---

### 7. **用户反馈摘要**  
- **正面反馈**：  
  - “v0.8.0 的 gateway 启动方式更清晰，env var 注入比 CLI flag 更灵活。”（PR #6803 上下文）  
  - “Homebrew 安装后配置路径终于正确了，之前一直找不到 config 文件。”（关联 PR #6639）  

- **负面痛点**：  
  - “SecurityPolicy 太敏感，连自己写的 PR 脚本都用不了，感觉像在裸奔。”（Issue #6771）  
  - “WeChat 重启后又要扫 QR 码，context_tokens 没存住。”（Issue #6238 背景）  

> 🎯 真实场景揭示：本地部署用户急需配置路径标准化；企业用户担忧沙箱逃逸风险；移动端集成者关注会话持久化。

---

### 8. **待处理积压**  
- **[Issue #6293] Air-gapped Execution Mode**：创建超 50 天，状态仍为 `blocked`，涉及 enclave 安全与 MCP 代理架构，需核心维护者 @singlerider 或安全团队介入决策。  
- **[Issue #5849] Dream Mode**：创建 32 天，虽获社区热捧但缺乏技术负责人认领，建议分配至 memory/knowledge 工作组跟进。  

> ⏳ 提醒：上述两项均为高影响力长期议题，若持续无进展可能影响社区信心。

--- 

*数据来源：GitHub API / zeroclaw-labs/zeroclaw (截至 2026-05-20)*

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

**PicoClaw 项目动态日报（2026-05-20）**

---

### 1. **今日速览**

过去24小时内，PicoClaw 项目保持较高活跃度：共处理 8 条 Issue 更新与 18 条 PR 动态，其中 5 个 Issue 已关闭、9 个 PR 成功合并，整体开发节奏稳健。发布了一个 nightly 构建版本 v0.2.8-nightly.20260520.639b3270，表明持续集成流程运行正常。社区反馈集中在身份验证、异步工具交付及配置可靠性等核心模块，技术讨论深入且具建设性。项目在稳定性与功能扩展之间取得良好平衡，无明显阻塞性问题。

---

### 2. **版本发布**

**Nightly Build 发布**
- **版本号**: `v0.2.8-nightly.20260520.639b3270`
- **类型**: 自动化夜间构建（不稳定，谨慎使用）
- **变更范围**: 基于 `main` 分支从 `v0.2.8` 以来的全部提交
- **完整日志**: [Full Changelog](https://github.com/sipeed/picoclaw/compare/v0.2.8...main)

> 注：此为非稳定构建，适用于测试新功能或验证修复，不建议用于生产环境。

---

### 3. **项目进展**

本周期内共有 **9 个 PR 被合并/关闭**，涵盖关键功能增强与稳定性修复：

| PR # | 标题 | 类型 | 影响 |
|------|------|------|------|
| [#2761](https://github.com/sipeed/picoclaw/pull/2761) | feat(subagent): support agent_id on sync subagent | 功能 | 同步子代理支持显式指定 agent_id，提升任务路由灵活性 |
| [#2755](https://github.com/sipeed/picoclaw/pull/2755) | feat(providers): add streaming reasoning_content and video media support | 功能 | 新增对 Xiaomi Mimo 多模态（含视频）及推理内容流的支持 |
| [#2740](https://github.com/sipeed/picoclaw/pull/2740) | fix(deepseek): capture reasoning_content from streaming | Bug Fix | 修复 DeepSeek 流式响应中 reasoning_content 丢失问题 |
| [#2703](https://github.com/sipeed/picoclaw/pull/2703) | Add Intel OpenVINO Model Server support | 功能 | 支持本地 LLM 推理通过 Intel OpenVINO Model Server |
| [#2491](https://github.com/sipeed/picoclaw/pull/2491) | Add session management commands: /status, /compact, /new | UX 增强 | 用户可通过命令手动管理会话上下文生命周期 |
| [#2892](https://github.com/sipeed/picoclaw/pull/2892) | Support streaming | 架构改进 | 实现配置驱动的提供者级流式输出机制（双 opt-in） |
| [#2888](https://github.com/sipeed/picoclaw/pull/2888) | Fix/tool config load image reaction | Bug Fix | 修复工具配置加载时图片反应异常问题 |

这些进展显著提升了多模态支持、本地部署能力、会话控制粒度及流式体验，尤其在国产 AI 模型适配方面迈出重要一步。

---

### 4. **社区热点**

当前最受关注的问题为 **#2674**（Codex OAuth 返回空响应），已有 5 条评论和 4 个点赞，反映用户对 OpenAI 生态兼容性深度依赖。其次为 **#2720**（PID 身份校验缺失导致崩溃循环），虽无高赞但涉及系统稳定性，维护者已提交修复 PR [#2813](https://github.com/sipeed/picoclaw/pull/2813)。此外，**#2829** 提出的“异步结果投递策略”引发关于子代理行为一致性的讨论，相关 PR [#2830](https://github.com/sipeed/picoclaw/pull/2830) 正在推进中，显示社区对复杂代理协作机制的强烈需求。

---

### 5. **Bug 与稳定性**

按严重程度排序的关键问题如下：

1. **[HIGH] #2720** - Singleton PID 检查未验证进程身份，导致 stale PID 引发重启循环  
   → **状态**: 已提交修复 PR [#2813](https://github.com/sipeed/picoclaw/pull/2813)（待合并）

2. **[MEDIUM] #2674** - Codex OAuth 模式下 ChatGPT 后端流式响应为空  
   → **状态**: 无公开修复 PR，需进一步调查 OpenAI API 变更

3. **[LOW] #2688** - `find /` 命令绕过沙箱路径限制，存在信息泄露风险  
   → **状态**: 已关闭（标记为 stale，暂未处理）

建议优先合并 PID 身份验证修复，以增强守护进程可靠性。

---

### 6. **功能请求与路线图信号**

多个 Issue 和 PR 指向未来版本方向：

- **配置迁移体验优化** (#2771)：提议更新示例配置文件并完善 V2→V3 迁移引导，预示即将发布新版默认配置模板。
- **跨会话记忆与上下文压缩** (#2774)：受 magic-context 插件启发，提出无限上下文缓存方案，可能推动长期记忆模块开发。
- **异步工具结果投递策略** (#2829 + PR #2830)：明确引入 `delivery_mode` 参数，标志异步代理通信机制将标准化。
- **Web UI 模型名持久化** (PR #2897)：确保历史记录中保留模型信息，改善用户体验一致性。

上述需求均具备较高实现优先级，预计将在近期版本中逐步落地。

---

### 7. **用户反馈摘要**

- **痛点集中点**：
  - Raspberry Pi Zero W 等资源受限设备上的性能瓶颈（#1757 提及 Telegram 频道错误）
  - 配置文件格式混乱，缺乏清晰迁移指引（#2771）
  - 子代理异步结果重复注入父代理（#2829）

- **满意之处**：
  - 对国产模型（如 GLM、Zai）的 OpenAI 兼容层支持广受好评（PR #82）
  - 多模态（视频理解）能力快速落地（PR #2755）
  - 命令行会话管理功能实用性强（PR #2491）

用户普遍认可项目在轻量化部署与多平台适配方面的努力，但对生产环境稳定性仍有期待。

---

### 8. **待处理积压**

以下 Issue/PR 超过两周未获实质性回应，需关注：

- **#2688**（安全漏洞）：文件系统枚举风险，建议尽快评估并修复
- **#2771**（配置体验）：涉及核心 UX，延迟处理可能影响新用户上手
- **#2829**（异步策略）：虽有关联 PR，但 Issue 本身仍需明确设计决策
- **#2720**（PID 安全）：尽管有 PR，但 Issue 描述详细，建议补充测试用例

建议维护团队在下一迭代周期优先处理安全与配置类问题，以提升整体健壮性与可用性。

--- 

*报告生成时间：2026-05-20*  
*数据来源：GitHub.com/sipeed/picoclaw*

</details>

<details>
<summary><strong>hermesagent</strong> — <a href="https://github.com/NousResearch/hermes-agent">NousResearch/hermes-agent</a></summary>

好的，作为 AI 智能体与个人 AI 助手领域的项目分析师，以下是根据您提供的数据生成的 **hermesagent 项目动态日报（2026-05-20）**。

---

### hermesagent 项目动态日报 (2026-05-20)

#### 1. 今日速览
hermesagent 项目在 2026-05-20 表现出极高的活跃度，过去 24 小时内产生了 210 条 Issues 更新和 500 条 PR 更新。项目整体状态健康，社区参与度极高，开发者正在积极修复 Bug、优化集成并推进新功能。尽管没有新版本发布，但代码库仍在快速演进。

#### 2. 版本发布
无新版本发布。

#### 3. 项目进展
今日合并/关闭的重要 PR 数量较少，但仍有部分关键修复和功能实现：
*   **#29052 [CLOSED] [type/docs, comp/tools, tool/web, provider/xai, P3] docs(web-search): document xAI Web Search backend**
    *   **链接:** https://github.com/NousResearch/hermes-agent/pull/29052
    *   **说明:** 文档化了对 xAI Web Search 后端的支持，完善了用户和开发者的配置指南。
*   **#24474 [CLOSED] [type/bug, comp/cli, comp/acp, tool/skills, P2] fix(acp): pass --skills flag through to ACP sessions**
    *   **链接:** https://github.com/NousResearch/hermes-agent/pull/24474
    *   **说明:** 修复了 `hermes acp` 命令中 `--skills` 标志被忽略的问题，提升了命令行工具的可用性。
*   **#25376 [CLOSED] [type/bug, comp/gateway, P2, javascript] fix(web): AutoField list type renders objects as [object Object]**
    *   **链接:** https://github.com/NousResearch/hermes-agent/pull/25376
    *   **说明:** 修复了设置界面中 `fallback_providers` 字段渲染为 `[object Object]` 的问题，防止配置损坏。
*   **#25347 [CLOSED] [type/bug, comp/agent, provider/gemini, P2] fix(agent): repair concatenated JSON tool_call arguments from Gemini parallel calls**
    *   **链接:** https://github.com/NousResearch/hermes-agent/pull/25347
    *   **说明:** 修复了 Gemini 模型并行调用时工具参数拼接错误的问题，确保工具调用能正确解析。
*   **#26093 [CLOSED] [type/bug, comp/agent, area/auth, P1] fix(auth): cap consecutive credential refresh attempts to prevent infinite 401 loop**
    *   **链接:** https://github.com/NousResearch/hermes-agent/pull/26093
    *   **说明:** 修复了认证凭证刷新导致的无限 401 循环问题，提升了系统的稳定性。
*   **#27627 [CLOSED] [type/bug, comp/cli, P2] fix(cli): wire /indicator slash command to a handler**
    *   **链接:** https://github.com/NousResearch/hermes-agent/pull/27627
    *   **说明:** 修复了 `/indicator` 斜杠命令未被处理的问题，使其功能正常。
*   **#27700 [CLOSED] [type/bug, comp/plugins, tool/web, P2] fix(web_tools): trigger plugin discovery before registry dispatch (#27683)**
    *   **链接:** https://github.com/NousResearch/hermes-agent/pull/27700
    *   **说明:** 修复了插件发现未在注册表分发前触发的问题，确保 web 工具能正确加载新插件。

#### 4. 社区热点
今日讨论最活跃的 Issue 主要集中在以下几个方面：
*   **Ollama 集成优化 (#4505):** 用户希望使用 Ollama 的原生 `/api/chat` 端点而非 OpenAI 兼容端点，以获得更好的流式传输体验。此 Issue 有 12 条评论，表明社区对此优化有较高期待。
*   **非核心技能可选化 (#19986):** 用户提议将默认安装中的非核心技能设为可选，以减少安装包大小和维护负担。此 Issue 有 6 条评论和 3 个点赞，显示出对轻量化安装的强烈需求。
*   **Docker 权限问题 (#18482):** 用户在 Docker 环境中遇到创建 home 目录的权限问题，此 Issue 有 5 条评论，反映了容器化部署的挑战。
*   **Feishu 表格渲染 (#9549):** Feishu 平台上的 Markdown 表格无法正确渲染，此 Issue 有 5 条评论和 5 个点赞，表明这是一个影响用户体验的显著问题。
*   **Cron/Agent 运行质量门 (#28056):** 提议在 Cron 或 Agent 运行时添加质量门和重试机制，以确保任务完成。此 Issue 有 5 条评论，显示出对自动化任务可靠性的关注。

#### 5. Bug 与稳定性
今日报告的 Bug 涵盖了多个组件和平台，按严重程度排列如下：
*   **P1 (高优先级):**
    *   **Telegram DM topic binding 未刷新 (#20470):** 会话压缩导致 Telegram DM topic 绑定未更新，引发预压缩循环。已有 6 个点赞，表明影响较大。
    *   **Telegram 内部推理块泄露 (#7233):** 更新后 Telegram 会话中泄露了内部推理内容。
    *   **Ollama 云模型工具调用渲染为 XML (#8965):** 使用 Ollama 云模型时，工具调用未能执行，而是以 XML 形式输出。
    *   **read_file/write_file 文件污染 (#19798):** `read_file` 返回的行号信息会污染 `write_file` 写入的文件内容。
    *   **custom:llmgateway 工具调用失败 (#24523):** 在使用 `custom:llmgateway` 且启用流式传输时，工具调用失败。
*   **P2 (中等优先级):**
    *   **Windows 路径媒体标签未解析 (#28989):** Windows 路径的图片无法被正确识别和发送。
    *   **Docker 入口脚本 UID 映射不完整 (#27221):** 当 `HERMES_UID` 改变时，`entrypoint.sh` 未能正确更新所有目录的所有权。
    *   **WhatsApp 回复上下文丢失 (#28823):** WhatsApp 回复消息的 `quotedMessageId` 未传递给 Agent。
    *   **Kanban Dashboard 批量重新分配失效 (#28968):** Kanban 仪表板中批量任务的重新分配功能无法正常工作。
    *   **Python <3.10 类型错误崩溃 (#21798):** 在 Python 3.9 及以下版本中，由于 `X | None` 类型提示导致崩溃。
*   **P3 (低优先级):**
    *   **hermes-achievements 生命周期计数器回归 (#28661):** 会话自动修剪后，成就插件的生命周期进度丢失。
    *   **LINE 内联按钮批准提示 (#29053):** LINE 平台的危险命令批准需要文本输入，而其他平台有按钮 UI。

#### 6. 功能请求与路线图信号
今日的功能请求反映了用户对 Hermes Agent 的期望和未来的发展方向：
*   **Per-user memory isolation in group chats (#11430):** 用户希望在群聊中为每个用户实现内存隔离，以防止身份混淆。这暗示了未来对多用户场景下更精细权限和隐私控制的需求。
*   **Turn-level live time context (#10421):** 用户希望 Agent 能在每轮对话中获得当前日期和时间，以提升时间感知能力。这表明对 Agent 实时性和上下文理解能力的增强。
*   **TokenTelemetry Plugin for Integration into Hermes Dashboard (#26696):** 用户提议添加 TokenTelemetry 插件，以提供跨多个 Agent 的 token 使用情况的可视化。这指向了未来对 Agent 集群管理和资源监控的重视。
*   **Rich Spreadsheet Skill (#4438):** 用户希望有一个专门用于处理 Excel/CSV 文件的 Rich Spreadsheet 技能，简化数据处理流程。这反映了用户对 Agent 工具集专业化和易用性的追求。
*   **Per-channel profile routing for Discord (#19809):** 用户希望在单个 Discord 机器人实例中支持不同频道的路由到不同的 Agent 配置文件，以节省资源。这表明了对 Agent 灵活部署和资源优化的需求。
*   **Hermes Session Selector - Professional Session Resume Interface (#12406):** 用户提议一个专业的会话选择器界面，以改善会话恢复的用户体验。这指向了未来对用户界面和交互体验的持续改进。

#### 7. 用户反馈摘要
从 Issues 评论中提炼的真实用户痛点包括：
*   **集成复杂性:** 用户在使用不同 LLM 提供商（如 Ollama, Gemini, custom:llmgateway）时遇到了各种兼容性问题，如工具调用失败、流式传输中断等。
*   **平台特定问题:** 多个平台（Telegram, WhatsApp, Feishu, LINE, QQBot）都报告了特定功能缺失或 Bug，例如消息上下文丢失、Markdown 渲染问题、WebSocket 连接问题等。
*   **Docker 部署挑战:** 用户在 Docker 环境中遇到权限问题、UID 映射不完整等，影响了容器的正常运行。
*   **CLI 和 TUI 体验:** 用户反馈了 CLI 命令处理、TUI 字符重排序等问题，影响了交互体验。
*   **技能与工具集:** 用户希望有更多内置技能（如电子表格处理），并希望非核心技能可选化，以减少安装包大小。
*   **认证与授权:** 用户遇到了 OAuth 令牌刷新失败、网关认证绕过等问题，影响了服务的可用性。
*   **性能与稳定性:** 用户报告了会话压缩导致的循环、无限 401 循环等问题，影响了系统的稳定性和响应速度。

#### 8. 待处理积压
以下是一些长期未响应的重要 Issue 或 PR，提醒维护者关注：
*   **Ollama 集成优化 (#4505):** 自 2026-04-01 创建，已有 12 条评论，但尚无明确进展。
*   **非核心技能可选化 (#19986):** 自 2026-05-05 创建，已有 6 条评论和 3 个点赞，但尚未解决。
*   **Docker 权限问题 (#18482):** 自 2026-05-01 创建，已有 5 条评论，但问题仍未解决。
*   **Feishu 表格渲染 (#9549):** 自 2026-04-14 创建，已有 5 条评论和 5 个点赞，但尚未修复。
*   **Cron/Agent 运行质量门 (#28056):** 自 2026-05-18 创建，已有 5 条评论，但尚无进展。
*   **Per-user memory isolation in group chats (#11430):** 自 2026-04-17 创建，已有 5 条评论，但尚未实现。
*   **Turn-level live time context (#10421):** 自 2026-04-15 创建，已有 4 条评论和 3 个点赞，但尚未实现。
*   **TokenTelemetry Plugin for Integration into Hermes Dashboard (#26696):** 自 2026-05-16 创建，已有 4 条评论，但尚无进展。
*   **Rich Spreadsheet Skill (#4438):** 自 2026-04-01 创建，已有 3 条评论，但尚未实现。
*   **Per-channel profile routing for Discord (#19809):** 自 2026-05-04 创建，已有 3 条评论，但尚无进展。
*   **Hermes Session Selector - Professional Session Resume Interface (#12406):** 自 2026-04-19 创建，已有 2 条评论和 4 个点赞，但尚未实现。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

**NanoClaw 项目动态日报（2026-05-20）**

---

### 1. **今日速览**  
NanoClaw 在 2026-05-20 保持高度活跃的开发节奏，过去 24 小时内处理了 23 个 PR 更新（含 5 个合并/关闭）和 4 个 Issue 动态。核心团队持续聚焦 WhatsApp 通道稳定性、权限边界强化及多消息批处理逻辑优化，整体项目健康度良好，无重大版本发布但修复类贡献密集。

---

### 2. **版本发布**  
无新版本发布。

---

### 3. **项目进展**  
- **已合并关键修复**：  
  - [#2565](https://github.com/nanocoai/nanoclaw/pull/2565) 修复了 WhatsApp 群组中 @-mention 检测失效问题，通过引入 `contextInfo.mentionedJid` 实现精准识别，解决了文档化 onboarding 流程阻塞问题。  
  - [#2143](https://github.com/nanocoai/nanoclaw/pull/2143) 新增管理员主动终止 agent 运行命令，提升运维可控性。  
- **高优先级功能推进**：  
  - [#2497](https://github.com/nanocoai/nanoclaw/pull/2497) "Agent Network" 特性进入深度开发阶段，支持跨容器协作与资源共享，预计将重构现有单 Agent 架构。  
  - [#2490](https://github.com/nanocoai/nanoclaw/pull/2490) 引入 LiteLLM 提供商抽象层，增强 LLM 模型兼容性，为未来多云支持铺路。

---

### 4. **社区热点**  
- **最高关注 Issue**：[#2555](https://github.com/nanocoai/nanoclaw/issues/2555) 揭示 multi-message batch envelope 导致 Claude Agent SDK 返回合成响应而非真实 API 调用，引发对消息封装机制透明度的担忧。  
- **最活跃 PR**：[#2567](https://github.com/nanocoai/nanoclaw/pull/2567) 提出 `CLAUDE.local.md` 自动加载缺失问题，反映用户对本地记忆持久化的强烈需求。  
- **安全焦点**：[#2566](https://github.com/nanocoai/nanoclaw/pull/2566) 强化 channel approval 权限作用域，防止越权授权，体现社区对访问控制一致性的重视。

---

### 5. **Bug 与稳定性**  
| 严重程度 | Issue/PR | 描述 | 状态 |
|----------|--------|------|------|
| High     | #2560 (CLOSED) | WhatsApp 群组 @-mention 未设置 `isMention`，导致路由丢弃事件 | ✅ 已修复（#2565） |
| Medium   | #2561 (CLOSED) | Agent 上下文压缩后输出格式异常，触发无限重试 | ⚠️ 需进一步验证 |
| Medium   | #2555 (OPEN)   | 批量消息包致 SDK 返回 `<synthetic>` 响应 | 🔧 正在修复（#2556） |

> 所有高严重性 Bug 均已有对应 PR 提交或合并，项目稳定性维护响应及时。

---

### 6. **功能请求与路线图信号**  
- **两阶段项目上下文加载**（#2550）：用户呼吁轻量索引 + 按需加载 STATUS 文件，以支持多项目并行工作流，暗示未来将推出“项目沙盒”或命名空间隔离能力。  
- **WhatsApp 格式化技能**（#2553）：显式添加容器级技能以规范提及语法，表明平台正从通用通信向垂直场景协议适配演进。  
- **Agent Network**（#2497）：长期投入资源，预示下一代架构将从单体 Agent 转向分布式智能体协同体系。

---

### 7. **用户反馈摘要**  
- **痛点集中点**：  
  - WhatsApp 提及渲染失败影响通知体验（#2552, #2554）；  
  - 多项目环境下上下文污染导致效率下降（#2550）；  
  - 批量消息处理时缺乏明确错误反馈（#2555）。  
- **积极信号**：  
  - 用户对权限细粒度控制表示认可（#2566）；  
  - 管理员终止命令获好评（#2143）。  

---

### 8. **待处理积压**  
- **长期悬置 Issue**：[#1723](https://github.com/nanocoai/nanoclaw/pull/1723)（4月10日提交）——数据库适配器层重构，涉及核心数据抽象，建议优先评审以避免技术债务累积。  
- **阻塞性 PR**：[#815](https://github.com/nanocoai/nanoclaw/pull/815) 标记为 Blocked，渐进式消息流式编辑功能停滞，需确认是否仍属 roadmap 优先级。

--- 

*数据来源：GitHub NanoClaw 仓库（https://github.com/qwibitai/nanoclaw）*

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

**IronClaw 项目动态日报（2026-05-20）**

---

### 1. **今日速览**

过去24小时内，IronClaw 项目保持高度活跃状态：共处理 Issue 更新 24 条、PR 更新 50 条，无新版本发布。核心开发聚焦于 Reborn 模块的功能落地与 WebUI Beta 路径完善，多个高优先级 Lane 任务启动推进。社区讨论集中于 crate 边界治理、E2E 测试框架重构及依赖升级，整体进展稳健且方向明确。

---

### 2. **版本发布**

无新版本发布。

---

### 3. **项目进展**

本周期内合并/关闭的关键 PR 包括：

- **#3792**（已关闭）：将 REPL LLM 认证逻辑迁移至 `ironclaw_reborn_composition`，实现 CLI 与运行时解耦，提升配置灵活性。
- **#3790**（已关闭）：新增热能力目录发布机制，支持 Extension Manifest v2 包动态注册能力，为 MCP/WASM 工具集成奠定基础。
- **#3788**（已关闭）：默认 HostPortCatalog 接入扩展发现流程，确保标准端口（如 HTTP egress）在能力解析阶段被正确识别。
- **#3797**（已关闭）：完成 REPL 工具通过生产级适配器路由，打通本地开发与真实产品路径的鸿沟。
- **#3794 / #3795**（已关闭）：强化 legacy extension v2 清单校验，区分第三方与内置包权限，增强安全性。

上述变更显著推进了 Reborn 架构中“能力组合”、“身份隔离”和“生命周期管理”三大支柱的建设，REPL 黄金路径基本成型。

---

### 4. **社区热点**

当前最受关注的问题为 **#3259**（Publish 0.25.0–0.27.0 to crates.io），自 5 月 5 日提出以来持续更新至今日，反映下游用户因 crates.io 未同步最新 tag 而被锁定在旧版本的痛点。尽管已有 6 条评论，但尚无官方回应，存在潜在生态断裂风险。

另一热点是 **#3702**（Reborn E2E 测试框架重设计），由 @henrypark133 发起，旨在建立统一的二进制端到端测试体系以覆盖 agent-loop 核心逻辑。该 Issue 关联 88 个测试文件分类工作，体现团队对测试一致性与可维护性的高度重视。

此外，**#3798**（Subagent Spawn 设计）作为今日新 Issue，提出分阶段实现子智能体 spawn 机制，包含合约定义、调度机制和集成验证三阶段，显示项目正探索多智能体协作能力。

---

### 5. **Bug 与稳定性**

- **#3447**（Nightly E2E failed）：昨日夜间自动化 E2E 测试失败，涉及 `Full E2E / E2E (v2-engine)` 任务，尚未有修复 PR 提交。建议排查环境或依赖变更影响。
- **#3771**（Configure UI 缺陷）：非 API-key 提供商（如 Gemini CLI）的配置界面缺失登录指引，属用户体验问题，暂无相关 fix PR。

目前无高危崩溃报告，系统稳定性总体良好。

---

### 6. **功能请求与路线图信号**

多个 Issue 强烈指向下一版本的核心方向：

- **租户级项目 ACL**（#3796）：要求将 project 作为一等权限实体，支持跨用户共享，预示权限模型将从扁平向 RBAC 演进。
- **Notion MCP / GitHub WASM 能力路径**（#3805, #3806）：明确规划首批外部工具集成方案，标志 Reborn 正式开放生态扩展。
- **EventStreamManager 回放路径**（#3809）：强调 durable timeline 对 WebUI 实时交互的重要性，是产品化关键一步。

结合近期 PR 可见，**Reborn WebUI Beta 发布路径已基本就绪**，预计将在未来 2–4 周内进入可试用阶段。

---

### 7. **用户反馈摘要**

从 Issue 评论中提取的真实诉求包括：

- 下游 Rust 项目因 crates.io 版本滞后无法升级，被迫使用含 CVE 风险的 wasmtime 绑定（#3259）；
- WebUI 错误信息缺乏结构化分类，导致前端难以统一处理（#3628 提及）；
- REPL 当前仅调用底层 AgentLoop，无法体验新能力组合带来的实际效果（#3800 用户期待）；
- 非技术用户希望简化模型配置流程，尤其是无 API key 的本地模型（#3771）。

整体反馈偏向建设性，集中在接口稳定性、文档透明度和易用性提升。

---

### 8. **待处理积压**

- **#3259**（crates.io 发布滞后）：自 5 月 5 日提出，超两周未获响应，影响下游生态健康，需优先协调发布流程。
- **#3702**（E2E 框架重设计）：虽已启动，但缺乏详细实施计划与责任归属，可能延缓测试覆盖率目标达成。
- **#3447**（Nightly E2E 失败）：持续未闭环，需查明根本原因并恢复 CI 可靠性。

建议本周内安排专项会议处理上述三项积压项。

--- 

*数据来源：GitHub.com/nearai/ironclaw | 生成时间：2026-05-20*

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

**LobsterAI 项目动态日报（2026-05-20）**

---

### 1. **今日速览**  
过去24小时内，LobsterAI 保持较高开发活跃度，共处理 **31 条 PR 更新**（26 待合并，5 已合并），同时新增 **2 条活跃 Issue**。项目整体处于功能迭代与稳定性优化并行阶段，核心模块如 renderer、cowork、main 持续获得改进。无新版本发布，但近期 PR 密集反映社区对用户体验和系统健壮性的高度关注。

---

### 2. **版本发布**  
无新版本发布。

---

### 3. **项目进展**  
今日共 **5 个 PR 被合并或关闭**，主要集中在 UI/UX 优化、子代理会话管理及日志安全增强：

- **[#2013](https://github.com/netease-youdao/LobsterAI/pull/2013)**（CLOSED）：修复上下文窗口滑块吸附逻辑及 K/M 文本输入支持，提升参数设置精度与易用性。
- **[#2014](https://github.com/netease-youdao/LobsterAI/pull/2014)**（CLOSED）：解决微信二维码网关重启异常问题，增强 IM 模块稳定性。
- **[#2012](https://github.com/netease-youdao/LobsterAI/pull/2012)**（CLOSED）：新增 artifacts 功能支持，扩展任务产物管理能力。
- **[#2011](https://github.com/netease-youdao/LobsterAI/pull/2011)**（CLOSED）：实现子代理会话侧边栏展示与详情页，完善多 Agent 编排的可观测性与交互体验。
- **[#680](https://github.com/netease-youdao/LobsterAI/pull/680)**（CLOSED）：完成“多 Agent 编排与子任务实时可观测”核心功能落地，标志着从“黑箱”向透明化协作的重大突破。

这些进展显著推进了 **Cowork 协作框架的成熟度** 和 **用户界面的精细化控制能力**。

---

### 4. **社区热点**  
当前最活跃的 Issue 为 **[#1698](https://github.com/netease-youdao/LobsterAI/issues/1698)**，描述有道龙虾与智企帝王蟹共存时的 gateway 端口冲突问题，属必现 Bug，影响多产品协同部署场景；另一新 Issue **[#2016](https://github.com/netease-youdao/LobsterAI/issues/2016)** 建议增加 openhuman 引擎支持，反映用户对多样化 AI 后端集成的强烈诉求。两者均暂无关联 PR，需优先响应。

---

### 5. **Bug 与稳定性**  
- **[#1698](https://github.com/netease-youdao/LobsterAI/issues/1698)**：**高优先级**。gateway 端口竞争导致智企帝王蟹鉴权失败，已确认复现路径清晰，但尚无修复 PR。建议评估是否涉及底层服务隔离机制缺陷。
- 其他 Issue 均为功能建议，未报告运行时崩溃或数据丢失类问题，系统整体运行稳定。

---

### 6. **功能请求与路线图信号**  
- **OpenHuman 引擎集成**（[#2016](https://github.com/netease-youdao/LobsterAI/issues/2016)）为新提出需求，结合近期对多模型供应商图标（[#1628](https://github.com/netease-youdao/LobsterAI/pull/1628)）和 Qwen 控制台迁移（[#1667](https://github.com/netease-youdao/LobsterAI/pull/1667)）等适配工作，表明项目正强化 **多平台 API 兼容性**，该需求极可能纳入下一版本。
- 用户普遍期待更细粒度的 **工具结果复制**（[#1640](https://github.com/netease-youdao/LobsterAI/pull/1640)）、**全局搜索去 Agent 限制**（[#1634](https://github.com/netease-youdao/LobsterAI/pull/1634)）等功能，均已由社区提交 PR，预计将快速进入合并流程。

---

### 7. **用户反馈摘要**  
- **痛点集中点**：多产品共存环境下的资源冲突（端口/进程竞争）暴露了部署架构的耦合风险，需加强沙箱或命名空间隔离设计。
- **满意点**：子代理会话可视化（[#680](https://github.com/netease-youdao/LobsterAI/pull/680)）和悬浮滚动按钮（[#1636](https://github.com/netease-youdao/LobsterAI/pull/1636)）获广泛认可，体现团队对交互细节的重视。
- **使用场景洞察**：用户频繁提及会议转录、文档摘要等垂直场景，驱动了对个性化 Agent 描述的动态展示（[#1660](https://github.com/netease-youdao/LobsterAI/pull/1660)）的需求。

---

### 8. **待处理积压**  
- **[#1698](https://github.com/netease-youdao/LobsterAI/issues/1698)**：自 2026-04-15 创建，持续活跃至今，涉及核心服务冲突，**建议本周内指派开发者排查 gateway 服务注册机制**。
- 多个标记为 `stale` 的 PR（如 [#1628](https://github.com/netease-youdao/LobsterAI/pull/1628)、[#1634](https://github.com/netease-youdao/LobsterAI/pull/1634)）虽内容优质但长期未合并，**建议维护者审查其依赖项并推动合并**，避免技术债累积。

--- 

*数据来源：GitHub @netease-youdao/LobsterAI (截至 2026-05-20)*

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyclaw">TinyAGI/tinyclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

**Moltis 项目动态日报（2026-05-20）**

---

### 1. **今日速览**  
过去24小时内，Moltis 项目保持中等活跃度：共处理 4 条 Issue 更新（2 新开/活跃，2 已关闭）和 4 条 PR 更新（2 待合并，2 已合并/关闭）。无新版本发布，但核心功能维护持续推进。社区反馈集中在 Docker 沙箱稳定性与 WebSocket 连接异常问题，整体项目运行平稳，修复响应及时。

---

### 2. **版本发布**  
无新版本发布。

---

### 3. **项目进展**  
今日共 **2 个 PR 被合并或关闭**，均为关键稳定性修复：

- **[PR #1025] fix(sandbox): reap docker sandbox zombies**  
  ✅ 已合并  
  修复了 Docker 沙箱中僵尸进程累积问题，通过启用 `--init` 参数确保子进程正确回收。此变更提升了容器隔离环境的资源管理可靠性，尤其适用于长期运行的 MCP 服务实例。  
  🔗 https://github.com/moltis-org/moltis/pull/1025

- **[PR #1023] fix(web): avoid false websocket disconnect timeouts**  
  ✅ 已合并  
  解决了客户端 RPC 超时误报为“WebSocket disconnected”的问题，保留原有 5 秒超时机制的同时优化了错误提示信息，便于开发者定位慢请求端点。  
  🔗 https://github.com/moltis-org/moltis/pull/1023

这两项修复显著增强了系统在高负载或网络波动下的鲁棒性，体现了团队对生产环境稳定性的重视。

---

### 4. **社区热点**  
今日最活跃的 Issue 为 **#1022** 和 **#1024**，均于昨日提交且无评论，反映新近出现的技术问题：

- **[Issue #1022] [Bug]: Getting "WebSocket disconnected" during LLM modes update**  
  用户报告在切换 LLM 模式时频繁触发虚假断开连接警告，可能与 PR #1023 所修复的误报机制有关，需进一步验证是否为新场景下的回归。  
  🔗 https://github.com/moltis-org/moltis/issues/1022

- **[Issue #1024] [Bug]: [hooks] config section parsed + validated but never registered at runtime**  
  指出 `hooks` 配置段虽通过校验却未被实际加载，暴露了配置解析与运行时注册之间的脱节，可能影响插件扩展能力。  
  🔗 https://github.com/moltis-org/moltis/issues/1024

两者均属功能性缺陷，尚未关联到具体 PR，建议纳入近期排查优先级。

---

### 5. **Bug 与稳定性**  
今日新增 **2 个 Bug 报告**，严重程度中等：

| Issue | 类型 | 描述 | 状态 | 相关 PR |
|------|------|------|------|--------|
| [#1022](https://github.com/moltis-org/moltis/issues/1022) | 连接稳定性 | LLM 模式更新时误报 WebSocket 断开 | 开放 | 无 |
| [#1024](https://github.com/moltis-org/moltis/issues/1024) | 配置失效 | hooks 配置未生效 | 开放 | 无 |

此前报告的 Docker 沙箱问题（[#423](https://github.com/moltis-org/moltis/issues/423)）已于今日关闭，表明基础环境问题已缓解。

---

### 6. **功能请求与路线图信号**  
今日无新功能请求，但存在一个历史增强提案：

- **[Issue #850] Support client_secret in MCP server OAuth override config**  
  提议在 MCP 服务器配置中支持 `client_secret` 字段以强化 OAuth 流程安全性。该 Issue 自 4 月提出至今未获响应，暂无对应 PR，短期内纳入计划可能性较低。  
  🔗 https://github.com/moltis-org/moltis/issues/850

当前开发重心仍聚焦于稳定性和兼容性维护，新功能推进节奏保守。

---

### 7. **用户反馈摘要**  
从 Issue 内容提炼以下真实痛点：

- **Docker 集成体验不佳**：用户多次提及沙箱容器管理混乱、僵尸进程堆积，影响自动化部署流程（见 #423）。
- **配置语义模糊**：`hooks` 配置项“通过验证却不执行”引发困惑，反映文档或实现逻辑存在断层（见 #1024）。
- **错误信息误导性强**：WebSocket 超时被错误标记为“disconnected”，干扰故障排查（见 #1022）。

整体反馈偏向技术细节层，未见极端负面情绪，说明社区具备较强技术素养。

---

### 8. **待处理积压**  
以下 Issue 超过 30 天未更新，需关注响应情况：

- **[Issue #850] Support client_secret in MCP server OAuth override config**  
  创建于 2026-04-23，距今已 27 天，无维护者回复或进展。涉及安全增强需求，建议分配优先级评估可行性。  
  🔗 https://github.com/moltis-org/moltis/issues/850

建议维护团队在下次迭代评审中讨论该 Issue 的技术成本与收益。

--- 

*数据截止：2026-05-20 00:00 UTC*

</details>

<details>
<summary><strong>QwenPaw</strong> — <a href="https://github.com/agentscope-ai/QwenPaw">agentscope-ai/QwenPaw</a></summary>

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，我将根据您提供的 GitHub 数据生成一份结构清晰的 QwenPaw 项目日报。

---

### **QwenPaw 项目动态日报 (2026-05-20)**

**总体评估：** QwenPaw 项目在今日保持高度活跃状态，社区参与度强劲。新版本 v1.1.8 的发布带来了插件生态的重大进展，同时围绕模型支持、UI/UX 优化和稳定性修复的讨论持续升温。项目整体发展势头良好，功能迭代与用户反馈形成了良性循环。

---

#### **1. 今日速览**

*   项目在过去24小时内展现出极高的活跃度，共处理了42条 Issues 更新和44条 PR 更新，表明开发团队和社区成员都在积极贡献。
*   发布了两个新版本（v1.1.8 和 v1.1.8-beta.2），重点引入了官方插件分发系统和 QwenPaw Pet 桌面宠物插件，显著丰富了应用生态。
*   社区对模型兼容性（如 ChatGPT-5.5）、飞书渠道集成以及 Markdown 表格渲染等功能的讨论尤为热烈，反映了用户对功能完善性的高度关注。
*   多个 Bug 报告集中在升级后系统提示词加载异常、API 调用流式信息不全以及特定环境下 HTTP 403 错误等问题，显示出新版本在特定场景下的稳定性仍需加强。

#### **2. 版本发布**

*   **v1.1.8**
    *   **更新内容：**
        *   **✨ Added:**
            *   **Official Plugin Distribution:** 引入了官方插件分发功能，用户可以通过网站浏览和下载插件，或通过控制台插件管理器一键安装。
            *   **QwenPaw Pet:** 新增了一个名为 QwenPaw Pet 的桌面宠物陪伴插件。
    *   **破坏性变更：** 无明确提及。
    *   **迁移注意事项：** 对于使用桌面应用的用户，需要卸载并重新安装最新版本。
*   **v1.1.8-beta.2**
    *   **更新内容：**
        *   **refactor(console): Model performance optimization:** 对控制台进行了模型性能优化。
        *   **perf(trace): batch append inbox trace events to reduce file I/O:** 优化了追踪功能，通过批量追加收件箱追踪事件来减少文件I/O操作。
        *   **add qwenpaw pet plug:** 添加了 QwenPaw Pet 插件。

#### **3. 项目进展**

*   **重要 PR 合并/关闭：**
    *   **#4536 feat(provider): add OpenCode Go into opencode via meta.base_url_options:** 成功合并，实现了将 OpenCode Go 模型集成到 OpenCode 提供程序中，通过 `meta.base_url_options` 切换 API 端点，为用户提供了更多免费模型选择。
    *   **#4523 fix(runner): persist /mission and /skill info responses to session me…:** 成功合并，修复了 `/mission` 和技能信息响应在会话重载后消失的问题，提升了用户体验的连贯性。
    *   **#4527 Introduce QWENPAW_AUTO_INITIALIZATION in deploy/entrypoint.sh:** 成功合并，允许在部署时禁用自动初始化，提高了容器化部署的灵活性。
    *   **#4529 fix(model): hotfix for model setting:** 成功合并，解决了模型设置相关的热修复问题。
    *   **#4526 feat(provider_manager): add new free models to opencode list:** 成功合并，向 OpenCode 列表添加了新的免费模型。
    *   **#4531 chore(version): update release note of v1.1.8:** 成功合并，更新了 v1.1.8 版本的发布说明。
    *   **#4533 supplement qwenpaw pet zh descriptions to website for language switch:** 成功合并，为 QwenPaw Pet 插件补充了中文描述，以支持语言切换。
    *   **#4534 docs(install): add backup dir:** 成功合并，在文档中添加了备份目录相关信息。
    *   **#4485 [invalid] [Bug]: 插件工具写入 agent.json 后未被注入 Agent 的 Toolkit:** 被标记为无效，但此问题揭示了插件工具在运行时未被正确导入的潜在风险。
    *   **#4449 [question] [BUG] Model 429 Rate-Limit → zero-downtime reload 永久清空消息队列，Agent 表现"冻结":** 被关闭，但此问题描述了模型限流导致 Agent "冻结" 的严重情况，需要后续关注。
    *   **#4494 [bug] Console stream stalls mid-generation with misleading "you interrupted me" message:** 被关闭，但此问题描述了控制台流式输出卡顿并显示误导信息的 bug。
    *   **#4542 [bug] 模型连接测试因 max_tokens=1 在部分 API 上失败（如 B.AI）:** 被关闭，但此问题指出了模型连接测试的硬编码限制问题。
    *   **#4512 [question]: 初始化创建 tool_result 但未被使用:** 被关闭，但此问题揭示了工具结果目录命名不一致的困惑。
    *   **#4515 [bug] 429之后卡死其他所有模型调用:** 被关闭，但此问题描述了 429 错误后模型调用卡死的问题。
    *   **#2660 [bug] AGENT_ERROR: Task has been cancelled!:** 被关闭，但此问题描述了任务被取消的错误。
    *   **#3001 [Feature]: 支持飞书 CardKit 流式输出（参考钉钉 AI Card 实现）:** 被关闭，但此功能是飞书渠道的重要增强。
    *   **#4174 [bug] If we use an API format like OpenAI, the agent's thoughts aren't collapsed into "thinking.":** 被关闭，但此问题是 UI 展示优化的需求。
    *   **#3528 [bug] 使用 <br> 时 Markdown 表格自动换行:** 被关闭，但此问题是 Markdown 渲染的常见问题。
    *   **#2983 [bug] Line breaks in Markdown tables don't work in the web client. This should result in a line break.**: 被关闭，但此问题是 Markdown 渲染的常见问题。
    *   **#4499 [question] 插件市场预计什么时间发布呢？有计划实现类似codex的宠物系统吗？:** 被关闭，但此问题反映了用户对插件市场和宠物系统的期待。
    *   **#4430 升级 1.1.6 → 1.1.7 是否会丢失之前的配置？:** 被关闭，但此问题涉及升级过程中的数据保留，是用户关心的重点。
    *   **#4441 什么时候模型配置能一键配置opencode go:** 被关闭，但此问题反映了用户对便捷配置的需求。

#### **4. 社区热点**

*   **#4496 [OPEN] [bug, invalid] [Bug]: 升级到 1.1.7 后，系统提示词中加载的 AGENTS.md 是内置的默认模板，而非工作区中的实际文件内容。** ([链接](https://github.com/agentscope-ai/QwenPaw/issues/4496))
    *   **热度：** 评论数最多 (11)，👍 数 0。
    *   **诉求分析：** 用户在升级后遇到系统提示词加载错误，期望能正确加载工作区中的自定义 AGENTS.md 文件，而非内置默认模板。这直接关系到用户个性化配置的可用性，是核心功能体验的关键问题。
*   **#4474 [OPEN] [question] [Question]: 现在支持chatgpt-5.5吗？** ([链接](https://github.com/agentscope-ai/QwenPaw/issues/4474))
    *   **热度：** 评论数 7，👍 数 0。
    *   **诉求分析：** 用户询问是否支持 ChatGPT-5.5 模型，反映了用户对最新模型支持的强烈需求和对 QwenPaw 模型生态的关注。
*   **#4535 [OPEN] [bug] [Bug]: `/backups` returns HTTP 403 when accessed from localhost** ([链接](https://github.com/agentscope-ai/QwenPaw/issues/4535))
    *   **热度：** 评论数 6，👍 数 0。
    *   **诉求分析：** 用户在本地访问备份功能时遇到 HTTP 403 权限错误，这表明 WebUI 的访问控制策略可能存在缺陷或配置不当，影响本地开发和调试体验。
*   **#4543 [OPEN] [bug] [Bug]: api调用对话首次流式信息不全** ([链接](https://github.com/agentscope-ai/QwenPaw/issues/4543))
    *   **热度：** 评论数 4，👍 数 0。
    *   **诉求分析：** 用户在 API 调用时遇到首次流式信息不完整的问题，这影响了实时交互的体验，尤其是在需要快速响应的场景下。
*   **#4541 [OPEN] [bug] [Bug]: 启用 Pet 插件后，发送第一条消息会导致主程序闪退 (ConnectTimeout)** ([链接](https://github.com/agentscope-ai/QwenPaw/issues/4541))
    *   **热度：** 评论数 2，👍 数 2。
    *   **诉求分析：** 用户报告启用 QwenPaw Pet 插件后，发送第一条消息会导致程序崩溃，这是一个严重的稳定性问题，直接影响新功能的可用性。

#### **5. Bug 与稳定性**

*   **高严重性：**
    *   **#4541 [OPEN] [bug] [Bug]: 启用 Pet 插件后，发送第一条消息会导致主程序闪退 (ConnectTimeout)** ([链接](https://github.com/agentscope-ai/QwenPaw/issues/4541)) - 程序崩溃，严重影响用户体验和新功能推广。
    *   **#4496 [OPEN] [bug, invalid] [Bug]: 升级到 1.1.7 后，系统提示词中加载的 AGENTS.md 是内置的默认模板，而非工作区中的实际文件内容。** ([链接](https://github.com/agentscope-ai/QwenPaw/issues/4496)) - 核心功能失效，影响用户个性化配置。
*   **中严重性：**
    *   **#4535 [OPEN] [bug] [Bug]: `/backups` returns HTTP 403 when accessed from localhost** ([链接](https://github.com/agentscope-ai/QwenPaw/issues/4535)) - 本地功能访问受限，影响开发和调试。
    *   **#4543 [OPEN] [bug] [Bug]: api调用对话首次流式信息不全** ([链接](https://github.com/agentscope-ai/QwenPaw/issues/4543)) - 影响 API 交互的实时性和完整性。
*   **低严重性：**
    *   **#4497 [OPEN] [bug] [Bug]: I'm writing this for the 3rd time. Line breaks in Markdown tables don't work. <br> should result in a line break.** ([链接](https://github.com/agentscope-ai/QwenPaw/issues/4497)) - Markdown 渲染问题，影响文档展示。
    *   **#4544 [OPEN] [question] [Question]: 偶发性飞书发过来的提示词没有在console端显示** ([链接](https://github.com/agentscope-ai/QwenPaw/issues/4544)) - 飞书渠道集成问题，影响特定场景下的功能。
*   **已有 Fix PR：** 目前没有针对 #4541 和 #4496 的公开 Fix PR，这两个问题需要优先处理。

#### **6. 功能请求与路线图信号**

*   **#4539 [OPEN] [Feature Request] 免费多模态路由：发图/视频/语音时自动切换视觉模型，像豆包一样无需手动干预** ([链接](https://github.com/agentscope-ai/QwenPaw/issues/4539))
    *   **分析：** 此功能请求非常具体且符合当前 AI 发展趋势，即自动识别输入内容类型并调用合适的模型。结合近期对模型支持和多模态能力的重视，此功能很可能被纳入下一版本的路线图。
*   **#3570 [OPEN] [enhancement] [Feature]: Can the "All Chats" list in the upper right be given pagination functionality?** ([链接](https://github.com/agentscope-ai/QwenPaw/issues/3570))
    *   **分析：** 随着聊天数量增长，性能优化是必然需求。此请求针对 UI 性能，是提升大规模用户使用体验的重要方向。
*   **#4514 [OPEN] [enhancement] [Feature]: Add Source Tracing / Citation functionality to conversation outputs** ([链接](https://github.com/agentscope-ai/QwenPaw/issues/4514))
    *   **分析：** 源追踪和引用功能是提升 AI 可信度和可追溯性的关键特性，尤其在企业级应用中尤为重要。此请求反映了用户对 AI 输出透明度的需求。
*   **#4518 [OPEN] feat(skill): Add skill-market, refactor skill hub to httpx** ([链接](https://github.com/agentscope-ai/QwenPaw/pull/4518))
    *   **分析：** 此 PR 正在推进技能市场的统一化和异步化，这是未来扩展生态的重要一步，预示着 QwenPaw 将向更丰富的插件和技能生态系统发展。
*   **#4532 [OPEN] [Under Review] feat(mcp): add OAuth 2.1 authorization flow for remote MCP servers** ([链接](https://github.com/agentscope-ai/QwenPaw/pull/4532))
    *   **分析：** 此 PR 为远程 MCP 服务器添加 OAuth 2.1 认证流程，是提升安全性和远程工具集成的关键步骤，表明 QwenPaw 正在积极拥抱 MCP 生态。

#### **7. 用户反馈摘要**

*   **痛点：**
    *   **升级兼容性问题：** 用户普遍担心升级是否会丢失配置（#4430），以及升级后某些功能异常（#4496），这反映了用户对稳定性和向后兼容性的高度关注。
    *   **Markdown 渲染缺陷：** 用户反复报告 Markdown 表格内换行符 `<br>` 无法正常工作（#4497, #2983, #3528），这影响了文档和代码展示的准确性。
    *   **API 交互体验：** 用户遇到 API 调用时流式信息不全（#4543）和首次调用后宠物插件导致闪退（#4541）的问题，这些直接影响了自动化脚本和插件功能的可靠性。
    *   **特定渠道集成：** 飞书渠道的偶发性提示词未显示（#4544）和模型连接测试失败（#4542）等问题，显示了第三方服务集成的复杂性。
*   **满意/不满意：**
    *   **新功能期待：** 用户对官方插件分发系统（#4499）和 QwenPaw Pet 宠物插件表现出浓厚兴趣，但也急切想知道何时能正式发布（#4499）。
    *   **模型支持：** 用户询问 ChatGPT-5.5 支持情况（#4474），以及对 OpenCode Go 的一键配置需求（#4441），表明他们对模型生态的丰富性和易用性有较高期望。
    *   **UI/UX 优化：** 用户提出分页功能（#3570）和上下文 token 估算优化（#4463）等建议，显示出他们对性能和效率的持续追求。

#### **8. 待处理积压**

*   **#4496 [OPEN] [bug, invalid] [Bug]: 升级到 1.1.7 后，系统提示词中加载的 AGENTS.md 是内置的默认模板，而非工作区中的实际文件内容。** ([链接](https://github.com/agentscope-ai/QwenPaw/issues/4496))
    *   **提醒：** 此 Issue 已存在较长时间，且评论数较多，是核心功能问题，需尽快确认并修复。
*   **#4541 [OPEN] [bug] [Bug]: 启用 Pet 插件后，发送第一条消息会导致主程序闪退 (ConnectTimeout)** ([链接](https://github.com/agentscope-ai/QwenPaw/issues/4541))
    *   **提醒：** 此 Issue 是新发现的严重稳定性问题，直接影响新功能的可用性，需立即排查和修复。
*   **#4497 [OPEN] [bug] [Bug]: I'm writing this for the 3rd time. Line breaks in Markdown tables don't work. <br> should result in a line break.** ([链接](https://github.com/agentscope-ai/QwenPaw/issues/4497))
    *   **提醒：** 此 Issue 是长期存在的 Markdown 渲染问题，用户多次报告，需持续跟进并解决。
*   **#3570 [OPEN] [enhancement] [Feature]: Can the "All Chats" list in the upper right be given pagination functionality?** ([链接](https://github.com/agentscope-ai/QwenPaw/issues/3570))
    *   **提醒：** 此 Issue 提出了重要的性能优化需求，随着聊天数量增长，此问题将愈发凸显，建议纳入中期规划。
*   **#4463 [OPEN] [Feature]: Improve context token estimation with cached prompt usage** ([链接](https://github.com/agentscope-ai/QwenPaw/issues/4463))
    *   **提醒：** 此 Issue 提出了上下文 token 估算的优化方案，有助于提升性能和用户体验，值得关注。

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

**ZeptoClaw 项目动态日报（2026-05-20）**

---

### 1. **今日速览**  
过去24小时内，ZeptoClaw 项目整体处于低活跃状态。GitHub Actions 依赖项更新成为唯一活动焦点：一条 PR 已合并，另一条仍在等待审查。无新 Issue 产生，也无版本发布，表明当前开发节奏以维护性任务为主。项目稳定性良好，社区互动未出现显著波动。

---

### 2. **版本发布**  
无新版本发布。

---

### 3. **项目进展**  
- **PR #586 已合并**：自动升级 GitHub Actions 中的 `taiki-e/install-action` 至 v2.75.29，属于常规依赖更新，提升 CI/CD 工具链安全性与兼容性。  
- **PR #591 待合并**：进一步将同一依赖升级至 v2.77.3，由 Dependabot 自动生成，旨在同步上游最新补丁与功能。该 PR 创建于昨日（2026-05-19），截至今日仍未获人工审核，可能因缺乏维护者响应或需进一步测试验证。

> 链接：[PR #586](https://github.com/qhkm/zeptoclaw/pull/586) | [PR #591](https://github.com/qhkm/zeptoclaw/pull/591)

---

### 4. **社区热点**  
当前无活跃 Issue 或高关注度讨论。所有 PR 均由机器人发起，无用户评论或反馈，反映社区参与度较低。潜在风险在于自动化依赖更新若长期无人审核，可能影响 CI 流程透明度与信任度。

---

### 5. **Bug 与稳定性**  
未报告任何 Bug、崩溃或回归问题。项目运行稳定，无紧急修复需求。

---

### 6. **功能请求与路线图信号**  
暂无新功能请求或明确路线图信号。近期所有变更均为基础设施优化，暗示当前阶段聚焦于系统健壮性与自动化维护，而非核心功能演进。

---

### 7. **用户反馈摘要**  
无直接用户评论或 Issue 反馈。鉴于项目为开源 AI 智能体助手领域工具，推测其目标用户为开发者或研究人员，但当前缺乏公开使用场景反馈，难以评估实际用户体验痛点。

---

### 8. **待处理积压**  
- **PR #591**：依赖升级请求已存在一天，尚未被人工审核。建议维护者优先处理此类安全/兼容性更新，避免累积技术债务。  
- 整体 Issue/PR 积压较少，但自动化工具生成的变更若长期依赖机器人处理，可能削弱社区协作感知。

--- 

*数据来源：GitHub API · 生成时间：2026-05-20 08:00 UTC*

</details>

<details>
<summary><strong>EasyClaw</strong> — <a href="https://github.com/gaoyangz77/easyclaw">gaoyangz77/easyclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>librefang</strong> — <a href="https://github.com/librefang/librefang">librefang/librefang</a></summary>

**librefang 项目动态日报（2026-05-20）**

---

### 1. **今日速览**

过去24小时，librefang 项目活跃度较高，共处理 50 个 PR 更新与 18 个 Issue，其中 CI 失败问题频发，主要集中在安全扫描与质量检查环节。核心贡献者 @houko 和 @f-liva 持续推动通道适配器迁移与内核修复工作。整体开发节奏稳健，但稳定性需关注。

---

### 2. **版本发布**

无新版本发布。

---

### 3. **项目进展**

**重要合并/关闭 PR：**

- **[#5300](https://github.com/librefang/librefang/pull/5300)**：修复了 main 分支因 `cargo fmt` 漂移、MCP caller_agent_id 语义错误及 OpenAPI 基线不一致导致的 CI 中断问题，恢复主分支绿色状态。
- **[#5299](https://github.com/librefang/librefang/pull/5299)**：将 Discord 适配器从进程内迁移至 Python sidecar，提升可维护性与扩展性。
- **[#5298](https://github.com/librefang/librefang/pull/5298)**：完成 Rocket.Chat 通道适配器的 sidecar 化改造，延续 Telegram/Gotify/Mastodon 等通道的统一架构演进。
- **[#5297](https://github.com/librefang/librefang/pull/5297)**：Twitch IRC 适配器同样迁移至 sidecar 模式，强化跨平台消息处理能力。
- **[#5295](https://github.com/librefang/librefang/pull/5295)**：为 `SidecarChannelConfig` 添加 `default_agent` 字段，解决 inbound routing 路由丢失问题（关联 #5294）。

这些变更标志着项目正系统性推进“通道去耦合化”与“配置标准化”，显著提升系统健壮性与运维友好度。

---

### 4. **社区热点**

**最活跃 Issue / PR：**

- **[#5296](https://github.com/librefang/librefang/issues/5296)**：PR #5260（feat(kernel): credential pools for multi-key per-provider rotation）的 CI 失败仍在持续，尽管该功能对生产环境密钥管理至关重要，但当前 Security 与 Quality 检查均未通过，引发开发者对合并风险的担忧。
- **[#5195](https://github.com/librefang/librefang/issues/5195)**：用户报告 Telegram 文件+文本消息被错误注入 `auto_memorize` 会话而非目标频道会话，导致上下文断裂。此问题已存在多日，反映 sidecar 迁移后会话隔离机制可能存在缺陷。
- **[#5290](https://github.com/librefang/librefang/issues/5290)**：Moonshot LLM 驱动在处理图像 MIME 类型时误用 OCR 接口，返回 400 错误。虽已有 PR #5291 快速响应，但仍暴露驱动层对非文本文件类型的识别不足。

这些议题集中体现了用户对**跨会话一致性**、**LLM 驱动兼容性**及**CI/CD 可靠性**的高关注度。

---

### 5. **Bug 与稳定性**

| 严重程度 | Issue / PR | 描述 | 状态 |
|--------|-----------|------|------|
| 高     | [#5296](https://github.com/librefang/librefang/issues/5296) | PR #5260 的 CI 持续失败（Security & Quality），阻碍关键功能合并 | 开放 |
| 中     | [#5195](https://github.com/librefang/librefang/issues/5195) | Telegram 消息路由错乱，文本与文件分属不同会话 | 开放，无 fix PR |
| 中     | [#5290](https://github.com/librefang/librefang/issues/5290) | Moonshot 驱动错误调用 OCR 端点于图片文件 | 已提交 PR #5291（待 review） |
| 低     | [#5293](https://github.com/librefang/librefang/issues/5293) | 配置页子标签响应异常，UI 显示问题 | 开放 |

> **稳定性提示**：main 分支近期多次出现 CI red 状态，主要由格式化漂移与安全扫描失败引起，建议合并前加强本地 lint 检查。

---

### 6. **功能请求与路线图信号**

- **[#5275](https://github.com/librefang/librefang/issues/5275)**：提议集成 Codex 作为运行时，支持将工具循环卸载至 OpenAI Codex CLI，实现执行环境切换。此需求呼应了“多运行时支持”趋势，可能预示未来 runtime 抽象层将更灵活。
- **[#5259](https://github.com/librefang/librefang/issues/5259)**：要求在 Agent 创建向导中为每个 MCP 服务器指定细粒度工具权限，避免权限过度授予。结合近期 PR 对 MCP 集成的强化，此功能有望在下一版本中落地。
- **[#4965](https://github.com/librefang/librefang/issues/4965)**：多密钥轮换机制虽已接近完成（PR #5260），但因 CI 阻塞暂未合并，预计将成为 v0.15 或 v0.16 的核心特性。

---

### 7. **用户反馈摘要**

- **正面反馈**：用户赞赏 sidecar 迁移带来的模块解耦与部署灵活性，尤其认可 Discord/Rocket.Chat/Twitch 等新通道的快速接入能力。
- **负面痛点**：
  - 多个用户抱怨 Dashboard 会话 URL 无法自动 pinned，影响多任务操作体验（[#5199](https://github.com/librefang/librefang/issues/5199)）。
  - Telegram 桥接在网络波动后无法自愈，需手动重启（[#5111](https://github.com/librefang/librefang/issues/5111)）。
  - 配置页面 UI 在小屏下子标签不可见，交互设计有待优化（[#5293](https://github.com/librefang/librefang/issues/5293)）。

---

### 8. **待处理积压**

- **[#5195](https://github.com/librefang/librefang/issues/5195)**：自 5 月 17 日提出，涉及核心会话路由逻辑，影响用户体验，建议优先排查 sidecar 会话绑定机制。
- **[#5111](https://github.com/librefang/librefang/issues/5111)**：Telegram 桥接重连机制缺失，属基础设施级缺陷，长期未解决，影响服务可用性。
- **[#4922](https://github.com/librefang/librefang/pull/4922)**：provider-aware token budgeting 功能已开发近两周，处于 needs-changes 状态，需审查预算计算逻辑是否准确。

---

**总结**：librefang 正处于架构升级关键期，sidecar 迁移稳步推进，但 CI 稳定性与核心 Bug 修复仍需投入。建议团队聚焦于会话隔离、LLM 驱动兼容性及配置 UI 优化三大方向，以巩固产品竞争力。

</details>

<details>
<summary><strong>openfang</strong> — <a href="https://github.com/RightNow-AI/openfang">RightNow-AI/openfang</a></summary>

**OpenFang 项目动态日报（2026-05-20）**

---

### 1. **今日速览**  
过去24小时，OpenFang 项目保持中等活跃度，共新增2个 Issue 和3个 PR。核心焦点集中在 v0.6.9 引入的自动代理加载机制引发的成本问题修复，以及 MCP 桥接工具链的深度集成。整体开发节奏稳健，无重大版本发布，但关键基础设施（如代理调度与执行环境限制）正经历主动优化。

---

### 2. **版本发布**  
无新版本发布。

---

### 3. **项目进展**  
- **PR #1207**: 修复了因 v0.6.9 自动启动代理功能导致的样本代理配置中激进调度策略触发意外 LLM 调用问题。该 PR 直接响应 Issue #1206，通过禁用三个示例代理中的 `[schedule]` 段来规避成本风险。[链接](https://github.com/RightNow-AI/openfang/pull/1207)  
- **PR #1205**: 推进 OpenFang 工具面（file/memory/agent/shell/web/patch）全面通过 MCP 桥接暴露给 Claude Code 子进程，实现工具逻辑统一化与审计加固（Stage 9）。此变更标志着与 Claude Code 生态深度集成的关键里程碑。[链接](https://github.com/RightNow-AI/openfang/pull/1205)  
- **PR #997**: 长期维护的 Gemini 原生嵌入驱动支持仍在更新中，最近更新于今日，涉及 API 密钥自动检测与模型配置优化，预计将增强多模态处理能力。[链接](https://github.com/RightNow-AI/openfang/pull/997)

---

### 4. **社区热点**  
- **Issue #1206**: 用户报告升级至 v0.6.9 后出现未预期的 LLM 计费激增，根源在于新启用的自动代理加载机制激活了原本静默的示例代理调度任务。此问题引发对默认配置安全性的关注。[链接](https://github.com/RightNow-AI/openfang/issues/1206)  
- **Issue #1204**: 用户对 `shell_exec` 执行时间硬上限（120秒）表示不满，认为限制了复杂任务的灵活性，尤其影响需要长时间运行的自动化脚本场景。开发者已明确此为设计约束，暂无调整计划。[链接](https://github.com/RightNow-AI/openfang/issues/1204)

---

### 5. **Bug 与稳定性**  
- **高优先级 Bug**: Issue #1206 揭示 v0.6.9 在生产环境中可能因默认代理调度导致非预期资源消耗，已被 PR #1207 快速响应并修复。建议受影响用户尽快合并该 PR 或手动移除相关代理配置。  
- **中优先级限制**: Issue #1204 反映 `shell_exec` 执行时长限制对用户工作流的制约，虽非崩溃类问题，但构成功能性瓶颈，目前无缓解方案。

---

### 6. **功能请求与路线图信号**  
- **MCP 工具集成深化**: PR #1205 表明项目正加速将 OpenFang 核心能力（如 agent/shell/web 工具）标准化为 MCP 接口，预示未来将强化与 AI 编程助手（如 Claude Code）的无缝协作能力。  
- **嵌入模型扩展**: PR #997 持续完善 Gemini 支持，结合此前 Google Cloud 相关适配，显示项目在多厂商 LLM 生态兼容性上的战略投入。

---

### 7. **用户反馈摘要**  
- **痛点**: 用户普遍担忧默认配置的安全性与可预测性，尤其在自动行为（如代理自启动）方面缺乏透明控制选项。  
- **使用场景**: 多数反馈来自企业级部署场景，强调成本控制与执行稳定性；个人开发者则更关注工具灵活性与扩展性。  
- **满意度**: 对 MCP 桥接等架构级改进给予积极评价，但对硬性执行限制（如 shell_exec 超时）表达明显 frustration。

---

### 8. **待处理积压**  
- **PR #997 (Gemini Embedding Driver)**: 创建于 2026-04-06，历时超40天仍未合并，涉及底层驱动重构与测试覆盖，需维护者评估优先级并推动终审。[链接](https://github.com/RightNow-AI/openfang/pull/997)  
- **Issue #1204 (shell_exec 超时限制)**: 虽非阻塞性问题，但作为高频功能限制，长期未获解决方案，可能影响用户体验一致性，建议纳入下一版本 UX 评审。

--- 

*数据来源：GitHub API @ 2026-05-20 | 分析师：AI 智能体 & 个人 AI 助手领域开源项目分析师*

</details>

<details>
<summary><strong>AstrBot</strong> — <a href="https://github.com/AstrBotDevs/AstrBot">AstrBotDevs/AstrBot</a></summary>

**AstrBot 项目动态日报（2026-05-20）**

---

### 1. **今日速览**
AstrBot 在过去24小时内保持较高社区活跃度，共处理 **23 条 Issue**（11 条活跃/新开，12 条已关闭）和 **17 条 PR**（14 条待合并，3 条已合并/关闭）。无新版本发布，但核心功能持续优化，插件生态活跃，开发者协作紧密。整体项目健康度良好，处于稳定迭代阶段。

---

### 2. **版本发布**
无新版本发布。

---

### 3. **项目进展**
今日合并/关闭的重要 PR 包括：
- **#8233**（已合并）：升级 `pnpm/action-setup` 至 6.0.8，属于依赖项更新，提升构建流程稳定性。
- **#7509**（已合并）：修复 vLLM Embedding 兼容性问题，解决新版 vLLM 部署 bge-m3 等模型时因强制传入维度参数导致的请求失败问题，显著增强多模态支持能力。
- **#8235**（已合并）：修正 FAQ 删除说明中的字段数量错误（从五处改为六处），提升文档准确性。

此外，多个新功能 PR 持续推进：
- **#8243**（群聊消息流上下文模式）：新增 `flow` 模式，允许长上下文模型按消息流增量接收上下文，默认仍为滑动窗口，不影响现有用户行为。
- **#8152**（SubAgent 功能增强）：支持静态配置与动态调用 SubAgent，提升复杂任务处理能力，响应 Issue #6954。
- **#8241**（Metaso 搜索后端）：新增免费 Web 搜索后端，每日 100 次查询，支持自定义 API Key 轮询，降低用户使用门槛。

---

### 4. **社区热点**
最活跃的 Issue 为 **#8254**（你画我猜游戏插件），发布于今日，已有 9 条评论，描述其支持 LLM 出题、手机白板作画、积分排行榜等功能，反映用户对轻量级群聊互动娱乐的高需求。  
另一热点 **#8249**（米游社资讯搬运插件）同样获 9 条评论，聚焦原神玩家对实时官方资讯推送的强烈诉求，体现垂直场景插件的实用价值。  
此外，**#8181**（SubAgent 静默调用模式建议）虽仅 2 条评论，但提出“保持单一角色沉浸感”的关键体验优化点，可能影响未来多代理交互设计方向。

---

### 5. **Bug 与稳定性**
高优先级 Bug 如下：
- **#8251**（知识库文件删除后仍可被调取）：标记为 bug，area:core，评论 4 条，尚未有 fix PR。用户反馈即使删除文件或未绑定知识库，AI 仍可访问旧数据，存在信息泄露风险。
- **#8223**（异常僵尸进程导致消息监听重复）：标记为 p0，area:core，评论 0 条，尚未有 fix PR。现象为单条消息触发两次回复，且调用不同 API，严重影响服务一致性。
- **#8242**（图片转述模型失效）：标记为 p1，area:provider，评论 0 条，尚未有 fix PR。用户发送图片时错误调用对话模型而非专用图片模型，导致报错。
- **#8238**（skills_like 模式下消息不一致）：评论 1 条，已有 fix PR #8240 提交，正在审查中。

---

### 6. **功能请求与路线图信号**
- **静默调用 SubAgent**（Issue #8181）：用户建议在沉浸式角色场景中启用子代理结果不直接展示于聊天界面，仅返回主代理，以维持角色一致性。此需求与 PR #8152（SubAgent 增强）形成呼应，预示未来可能支持更精细的代理通信控制。
- **群聊消息流上下文模式**（PR #8243）：新增 `flow` 模式，为长上下文模型提供增量上下文感知能力，标志项目向高效大模型集成演进。
- **Metaso 搜索后端**（PR #8241）：新增免费 Web 搜索选项，降低使用门槛，反映项目在工具链扩展上的积极布局。

---

### 7. **用户反馈摘要**
- **正面反馈**：用户对插件生态高度认可，如“你画我猜”和“米游社资讯搬运”插件获热烈讨论，体现社区对实用、垂直场景功能的欢迎。
- **负面痛点**：
  - 知识库管理混乱（#8251）：用户期望删除操作彻底生效，避免误读历史数据。
  - 僵尸进程问题（#8223）：影响服务稳定性，用户报告实例重复启动、消息重复处理，需紧急修复。
  - 配置提示误导（#8043）：警告信息提及 `/t2i` 指令，但该指令不存在，造成困惑，需统一日志与实际功能。

---

### 8. **待处理积压**
- **#8251**（知识库数据残留）：创建于 2026-05-19，尚无进展，属核心功能缺陷，建议优先排查缓存或索引同步机制。
- **#8223**（僵尸进程）：创建于 2026-05-18，p0 优先级，影响生产环境稳定性，需尽快定位进程生命周期管理漏洞。
- **#8181**（静默调用 SubAgent）：长期功能建议，虽评论数少但触及多代理交互核心体验，建议纳入 roadmap 评估。

--- 

*数据来源：GitHub.com/AstrBotDevs/AstrBot，统计时间：2026-05-20*

</details>

---
*本日报由 [Big Model Radar](https://github.com/ivanweng2077/big_model_radar) 自动生成。*