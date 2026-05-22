# OpenClaw 生态日报 2026-05-22

> Issues: 500 | PRs: 500 | 覆盖项目: 15 个 | 生成时间: 2026-05-22 02:46 UTC

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

**OpenClaw 项目动态日报（2026-05-22）**

---

### 1. **今日速览**
过去24小时 OpenClaw 社区活跃度极高，共处理 Issue 更新 500 条、PR 更新 500 条，发布两个新版本（v2026.5.20 及 beta 版），涵盖 exec 权限模型重构与 Discord 语音会话增强。整体项目处于高速迭代阶段，安全性和多平台支持成为核心焦点。

---

### 2. **版本发布**

#### **v2026.5.20**  
- **关键变更**：
  - **Exec Approvals 重大调整**：废弃旧版 `cat SKILL.md && printf ... && <skill-wrapper>` 兼容路径，强制技能文件必须通过 `read` 工具加载，仅真实可执行文件自动加入白名单，显著提升安全性。
  - **Discord 语音增强**：允许语音会话跟随已配置的 Discord 用户进入语音频道，改善协作体验。
- **破坏性变更**：旧技能加载方式失效，需迁移至新规范。
- **迁移建议**：所有自定义技能需移除遗留包装逻辑，改用标准 `read` 工具调用；Discord 配置中需明确指定 `voiceFollowUsers` 字段。

> 🔗 [Release v2026.5.20](https://github.com/openclaw/openclaw/releases/tag/v2026.5.20)

#### **v2026.5.20-beta.2**  
内容与正式版一致，用于预发布验证。

---

### 3. **项目进展**

今日无高优先级 PR 合并或关闭，但多个关键修复已进入待审状态：

- **#85110**：修复 Codex 子任务仅返回进度文本时误判为成功的问题，防止消息丢失（P1，已提交证明）。
- **#83722**：确保同通道块回复在工具执行前送达，解决用户错过前置提示的问题（P1，AI 辅助生成）。
- **#84007**：子代理思考级别继承机制完善，提升多代理场景一致性（P2）。
- **#85160**（已关闭）：Codex 本地压缩失败信息透出，增强调试能力（维护者主导）。

项目正稳步推进稳定性与用户体验优化，尤其在消息流控制与错误处理方面取得实质性进展。

---

### 4. **社区热点**

以下 Issue/PR 评论活跃，反映社区关注重点：

| 类型 | ID | 主题 | 热度 | 链接 |
|------|----|------|------|------|
| Issue | #75 | Linux/Windows 桌面应用缺失 | 🔥 105 评论 | [链接](https://github.com/openclaw/openclaw/issues/75) |
| Issue | #9443 | 请求预编译 Android APK | 📱 24 评论 | [链接](https://github.com/openclaw/openclaw/issues/9443) |
| Issue | #39604 | 支持私有网络访问的 web_fetch 工具 | 🔒 12 评论 | [链接](https://github.com/openclaw/openclaw/issues/39604) |
| PR | #85164 | Discord 进度草稿显示助手注释 | 💬 待评审 | [链接](https://github.com/openclaw/openclaw/pull/85164) |

**分析**：跨平台客户端（尤其移动端与 Windows/Linux）需求强烈；安全边界扩展（如私有网络访问、密钥掩码）成为高频诉求，体现用户对生产环境部署的重视。

---

### 5. **Bug 与稳定性**

按严重程度排序的重要 Bug：

1. **[P1] #84059**：嵌入式代理运行因会话文件锁释放异常崩溃（影响所有嵌入场景）。✅ 已有修复方向（#84007 相关）。
2. **[P1] #40540**：Windows 下 `openclaw update` 命令 EBUSY 错误，阻碍自更新。⚠️ 尚无公开 PR。
3. **[P1] #38327**：Google Vertex/Gemini 模型升级后出现“undefined/null to object”错误。⚠️ 需回归测试。
4. **[P1] #84880**：v2026.5.19 仍拒绝非-off thinking 参数于子代理 spawn。❌ 此前修复不完整。

> 注：标 ✅ 表示存在关联 PR 或解决方案；⚠️ 表示问题确认但无立即修复；❌ 表示修复未生效。

---

### 6. **功能请求与路线图信号**

用户提出的高价值功能需求包括：

- **跨平台原生应用**（#75, #9443）：macOS/iOS/Android 已有，Linux/Windows 成最大缺口。
- **细粒度权限控制**：
  - 路径级 RWX 权限（#39979）
  - 能力基权限模型（#12678）
  - 文件系统沙箱（#7722）
- **会话管理增强**：
  - 会话快照保存/加载（#13700）
  - 自动内存持久化（#40418）
- **安全合规**：
  - 掩码 secrets（#10659）
  - AWS Secrets Manager 集成（#13610）

结合现有 PR 可见，**安全加固**与**多模态交互支持**（Slack Block Kit、Feishu 图片保留）将是下一版本重点方向。

---

### 7. **用户反馈摘要**

- **正面反馈**：
  - 新版 exec approvals 更清晰，减少误授权风险（#6615 获 7 赞）。
  - Discord 语音跟随功能实用性强（#85164 开发者积极回应）。
- **负面痛点**：
  - Cron 作业无法追加写入共享文件，导致数据静默丢失（#40001）。
  - Telegram 私信误入主会话，污染心跳通道（#41165）。
  - Feishu 图片在回复中丢失媒体附件（#41744）。

用户普遍期望 OpenClaw 向“企业级可靠代理平台”演进，强调**数据完整性**、**权限最小化**与**多云部署能力**。

---

### 8. **待处理积压**

以下 Issue/PR 长期未获响应，需维护者优先介入：

| 类型 | ID | 标题 | 最后更新 | 影响 |
|------|----|------|----------|------|
| Issue | #75 | Linux/Windows 桌面应用缺失 | 2026-05-21 | 核心功能缺口 |
| Issue | #6731 | Safe/Unsafe ClawdBot 模式 | 2026-05-21 | 安全架构升级 |
| Issue | #10659 | 掩码 secrets 防泄露 | 2026-05-21 | 高危安全需求 |
| PR | #85183 | 保留更新时的配置意图 | 2026-05-22 | 破坏性更新防护 |

> 建议本周内安排维护者集中处理上述事项，尤其是 #75 和 #10659，涉及产品战略与用户信任。

--- 

*数据来源：GitHub API / OpenClaw Repository (github.com/openclaw/openclaw)*

---

## 横向生态对比

好的，作为专注于 AI 智能体开源生态的技术分析师，我将基于您提供的数据生成一份横向对比分析报告。

---

### **AI 智能体与个人 AI 助手开源生态横向对比分析报告 (2026-05-22)**

#### **1. 生态全景**

当前，个人 AI 助手与自主智能体开源生态正处于高速迭代与分化阶段。OpenClaw 作为核心参照项目，引领着安全、多平台支持与多 Agent 协作的演进方向。与此同时，NanoBot、Zeroclaw、PicoClaw 等项目在特定领域（如 WebUI 优化、TUI 重构、轻量级部署）展现出差异化竞争力。社区普遍关注企业级可靠性、跨平台集成及细粒度权限控制，预示着该生态正从概念验证向生产就绪稳步过渡。

#### **2. 各项目活跃度对比**

| 项目名称     | Issues 数 | PR 数 | Release 情况       | 健康度评估 |
| :----------- | :-------- | :---- | :----------------- | :--------- |
| **OpenClaw** | 500       | 500   | v2026.5.20, Beta   | ⭐⭐⭐⭐⭐ (极高) |
| NanoBot      | 12        | 21    | 无                 | ⭐⭐⭐⭐☆ (高)   |
| Zeroclaw     | 22        | 50    | 无                 | ⭐⭐⭐⭐☆ (高)   |
| PicoClaw     | 9         | 27    | Nightly v0.2.8     | ⭐⭐⭐⭐☆ (高)   |
| hermesagent  | 数百      | 数百  | 无                 | ⭐⭐⭐⭐☆ (高)   |
| NanoClaw     | 3         | 20    | 无                 | ⭐⭐⭐☆☆ (中高) |
| IronClaw     | 24        | 46    | 无 (v0.27.0 滞后)  | ⭐⭐⭐☆☆ (中高) |
| LobsterAI    | 0 (新)    | 12    | 无                 | ⭐⭐⭐☆☆ (中)   |
| TinyClaw     | 0         | 0     | 无                 | ⭐⭐☆☆☆ (低)   |
| Moltis       | 7         | 5     | 无                 | ⭐⭐⭐☆☆ (中)   |
| QwenPaw      | 26        | 29    | 无                 | ⭐⭐⭐☆☆ (中)   |
| ZeptoClaw    | 0         | 0     | 无                 | ⭐☆☆☆☆ (极低) |
| librefang    | 50        | 50    | 无                 | ⭐⭐⭐⭐☆ (高)   |
| openfang     | 0 (新)    | 2     | 无                 | ⭐⭐☆☆☆ (低)   |
| AstrBot      | 16        | 12    | 无                 | ⭐⭐⭐☆☆ (中)   |

*   **健康度评估说明：** ⭐ 数量表示活跃度和稳定性，5星为最高。
*   **OpenClaw** 和 **hermesagent** 表现出极高的活跃度，Issue 和 PR 数量庞大，表明其社区参与度和开发速度处于领先地位。
*   **NanoBot**, **Zeroclaw**, **PicoClaw**, **librefang** 也保持了较高的活跃度，显示出稳健的发展态势。
*   **IronClaw** 虽然 Issue 和 PR 数量可观，但存在依赖链断裂风险，影响其健康度评分。
*   **LobsterAI**, **Moltis**, **QwenPaw**, **AstrBot** 等项目的活跃度相对稳定，但 Issue/PR 数量较少，可能处于功能完善或特定开发周期。
*   **TinyClaw** 和 **ZeptoClaw** 今日无活动，需持续观察其后续动态。

#### **3. OpenClaw 在生态中的定位**

*   **优势：**
    *   **核心地位与影响力：** OpenClaw 是“核心参照”项目，其 Issue 和 PR 数量远超其他项目，表明其在社区中具有标杆性和广泛的影响力。
    *   **安全与多平台支持：** 项目将“安全性”和“多平台支持”作为核心焦点，通过 Exec Approvals 重构和 Discord 语音增强等更新，展现了其在企业级应用和复杂部署场景下的技术深度。
    *   **高速迭代：** 每日发布新版本，涵盖关键功能和安全改进，体现了其快速响应社区需求和技术趋势的能力。
*   **技术路线差异：**
    *   OpenClaw 更侧重于构建一个功能强大、安全可靠、多平台兼容的通用型 AI 智能体框架，强调技能加载、权限模型和多 Agent 协作。
    *   相比之下，NanoBot 更注重 WebUI 体验和 LLM 提供商兼容性；Zeroclaw 则聚焦于 TUI 架构重构和多 Agent 运行时优化；PicoClaw 偏向轻量级部署和 Telegram 集成。
*   **社区规模对比：**
    *   OpenClaw 的社区规模明显大于其他项目，这从其庞大的 Issue 和 PR 数量以及广泛的讨论热度可见一斑。

#### **4. 共同关注的技术方向**

*   **多平台集成与适配：** 几乎所有项目都致力于支持多种通信渠道（Telegram, Discord, WeChat, Feishu, WhatsApp, Slack 等）和云平台（NEAR AI Cloud, Google Vertex/Gemini, xAI Grok, Moonshot, Novita AI 等），以满足不同用户的使用场景。
*   **企业级可靠性与安全性：**
    *   **权限控制：** OpenClaw 的 Exec Approvals 重构、IronClaw 的 Reborn 架构迁移、librefang 的安全审计修复，均体现了对细粒度权限控制和最小化授权原则的重视。
    *   **数据完整性：** OpenClaw 和 NanoBot 都提到了对会话快照、内存持久化的需求，以确保数据不丢失。
    *   **密钥管理：** librefang 的掩码 secrets 需求和 AWS Secrets Manager 集成建议，反映了企业对敏感信息管理的关注。
*   **多 Agent 协作与运行时优化：** OpenClaw、Zeroclaw、PicoClaw、hermesagent 等项目都在积极扩展多 Agent 场景下的能力，包括子代理思考级别继承、多 Agent 运行时、并行任务编排等。
*   **WebUI/TUI 用户体验优化：** NanoBot、Zeroclaw、QwenPaw、AstrBot 等项目都在不断改进其图形用户界面或终端用户界面，以提升交互效率和易用性。
*   **API 兼容性与错误处理：** 多个项目报告并修复了与第三方 LLM API（如 Gemini, DeepSeek, Moonshot/Kimi）的兼容性问题，强调了健壮的错误处理和配置管理的重要性。

#### **5. 差异化定位分析**

*   **功能侧重：**
    *   **OpenClaw:** 通用性强，功能全面，注重安全性和多平台支持，适合需要高度定制化和企业级部署的用户。
    *   **NanoBot:** 以 WebUI 为核心，强调 LLM 提供商兼容性和开发者体验，适合快速原型开发和轻量级应用。
    *   **Zeroclaw:** 专注于 TUI 架构和多 Agent 运行时，适合偏好命令行操作和复杂多智能体工作流的用户。
    *   **PicoClaw:** 轻量级、易于部署，强调 Telegram 集成和 NEAR AI Cloud 支持，适合个人开发者和小型团队。
    *   **hermesagent:** 功能丰富，集成度高，支持多种平台和技能，适合需要强大功能和灵活性的高级用户。
    *   **NanoClaw:** 专注于容器化部署和 MCP 工具集成，适合希望利用现有容器基础设施的用户。
    *   **IronClaw:** 企业级 SaaS 平台方向，强调 Reborn 架构、成本预算、细粒度治理，适合大型企业客户。
    *   **LobsterAI:** 以 UI 体验和国际化为主，适合注重界面友好和中文支持的用户。
    *   **Moltis:** 专注于 Docker 环境下的稳定性和云服务商支持，适合容器化部署场景。
    *   **QwenPaw:** 强调技能市场和前端优化，适合需要丰富技能生态和良好交互体验的用户。
    *   **librefang:** 以安全审计和性能优化为核心，适合对安全性和性能有极高要求的用户。
    *   **openfang:** 专注于多云推理支持和本地推理稳定性，适合避免 vendor lock-in 和重视私有化部署的用户。
    *   **AstrBot:** 插件生态和群管功能突出，适合需要高度自定义和智能内容治理的用户。
*   **目标用户：**
    *   **OpenClaw, hermesagent, IronClaw:** 企业级用户、大型组织、需要高度定制化和安全性的开发者。
    *   **NanoBot, PicoClaw, LobsterAI, QwenPaw, AstrBot:** 个人开发者、小型团队、注重易用性和快速上手的用户。
    *   **Zeroclaw, Moltis, NanoClaw, openfang:** 偏好特定部署方式（TUI, Docker, 多云）的开发者和运维人员。
    *   **librefang:** 对安全性和性能有极致要求的用户。
*   **技术架构：**
    *   **OpenClaw:** 模块化设计，强调技能加载和权限模型。
    *   **NanoBot:** 以 WebUI 为中心，后端服务分离。
    *   **Zeroclaw:** Rust 语言，TUI 与守护进程分离，RPC 通信。
    *   **PicoClaw:** 轻量级，易于集成和部署。
    *   **hermesagent:** 复杂的 CLI 工具链和网关通信，支持多种 init 进程。
    *   **NanoClaw:** 容器化，MCP 工具集成。
    *   **IronClaw:** 企业级架构，Reborn 运行时，Lane 化管理。
    *   **LobsterAI:** 前端 UI 优化，后端引擎稳定性。
    *   **Moltis:** Docker 环境适配，Twilio 集成。
    *   **QwenPaw:** 技能市场，前端异步请求。
    *   **librefang:** 安全审计，性能优化，SDK 集成。
    *   **openfang:** 多云推理支持，本地推理超时机制。
    *   **AstrBot:** 插件系统，CLI 命令，跨平台兼容性。

#### **6. 社区热度与成熟度**

*   **快速迭代阶段：**
    *   **OpenClaw, hermesagent:** 这些项目 Issue 和 PR 数量巨大，社区讨论热烈，持续发布新版本，处于快速迭代和功能扩展阶段。
    *   **NanoBot, Zeroclaw, PicoClaw, librefang:** 同样保持较高活跃度，功能不断完善，处于稳健发展期。
*   **质量巩固阶段：**
    *   **IronClaw:** 虽然 Issue 和 PR 数量不少，但存在依赖链断裂风险，且部分 Bug 长期未解决，表明其在某些方面需要加强质量控制和发布流程。
    *   **LobsterAI, Moltis, QwenPaw, AstrBot:** 这些项目整体活跃度稳定，Bug 和 Feature Request 得到及时处理，处于功能完善和质量巩固阶段。
*   **观察期：**
    *   **TinyClaw, ZeptoClaw:** 今日无活动，需要持续关注其后续动态，判断其是否进入休眠或转型期。
    *   **openfang:** 虽有功能 PR，但整体活跃度较低，处于早期发展阶段。

#### **7. 值得关注的趋势信号**

*   **企业级 SaaS 平台的兴起：** IronClaw 的 Reborn 架构迁移、成本预算框架、细粒度权限控制等特性，强烈暗示了 AI 智能体开源项目正在向企业级 SaaS 平台演进的趋势。这要求项目不仅提供强大的功能，还需具备高可用性、可扩展性、安全合规性和完善的治理能力。
*   **多云与异构计算支持的强化：** 多个项目（OpenClaw, PicoClaw, Moltis, openfang）都在积极集成 NEAR AI Cloud、Google Vertex/Gemini、xAI Grok 等云推理服务，以及对 Ollama、Codex 等本地/边缘计算平台的支持。这表明开发者越来越重视避免 vendor lock-in，并充分利用异构计算资源。
*   **TUI 与 WebUI 的融合探索：** Zeroclaw 的 TUI 架构重构和独立运行，以及 OpenClaw 对 Discord 语音会话的增强，都反映了用户对更灵活、更高效的交互方式的需求。未来可能会出现更多 TUI 与 WebUI 优势互补的设计。
*   **安全合规成为核心竞争力：** librefang 的大量安全审计修复、OpenClaw 的 Exec Approvals 重构、IronClaw 的 Reborn 安全边界，都凸显了安全合规不再是附加功能，而是吸引企业级用户的关键门槛。
*   **多 Agent 协作的深水区挑战：** 尽管多 Agent 协作是热点，但项目中仍暴露出诸如 CPU 占用率高、重复 LLM 调用、Agent 间通信效率等问题。这表明多 Agent 协作仍处于探索阶段，需要更深入的系统级优化和更成熟的协调机制。
*   **对“后台行为透明化”的普遍诉求：** NanoBot 的 Dream 作业全局开关需求，反映了用户对系统内部运作机制的透明度和可控性的强烈期待。未来的 AI 智能体框架需要提供更清晰的配置选项和状态反馈，让用户能够更好地理解和掌控其行为。

**对 AI 智能体开发者的参考价值：**

*   **选择合适的项目：** 根据自身需求（企业级 vs. 个人开发、多云支持、TUI/WebUI 偏好、特定平台集成）选择最匹配的开源项目。
*   **关注安全实践：** 将安全合规作为开发的首要考虑因素，学习并借鉴领先项目（如 OpenClaw, librefang）的安全设计和最佳实践。
*   **拥抱多云生态：** 在设计系统时，优先考虑多云和异构计算支持，以提高系统的弹性和灵活性。
*   **重视用户体验：** 无论是 WebUI 还是 TUI，都应不断优化交互体验，提升用户满意度和工作效率。
*   **积极参与社区：** 开源项目的发展离不开社区的贡献，积极参与 Issue 讨论、PR 提交和问题反馈，有助于推动项目进步并获得更快的支持。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

**NanoBot 项目动态日报（2026-05-22）**

---

### 1. **今日速览**
过去24小时内，NanoBot 社区活跃度较高，共处理 Issue 12条、PR 21条，整体进展平稳。WebUI 相关 Bug 修复和性能优化成为重点方向，同时新增多个 LLM 提供商支持。项目暂无新版本发布，但功能迭代持续活跃。

---

### 2. **版本发布**
无新版本发布。

---

### 3. **项目进展**
今日共合并/关闭 PR 14 项，其中重要更新包括：
- **#3944**：修复了 WebUI 会话刷新时新聊天被意外清除的问题（关联 Issue #3884），提升了用户体验稳定性。
- **#3940**：解决了 Moonshot API 对 Kimi 系列模型因同时传递 `reasoning_effort` 和 `thinking` 参数导致的请求失败问题。
- **#3927**：新增 Novita AI 作为内置 LLM 提供商，扩展了 OpenAI 兼容生态。
- **#3923**：引入结构化 `apply_patch` 工具，显著提升代码编辑工作流的可靠性与安全性。
- **#3684**：修复微信通道中消息静默丢失问题，增强通道健壮性。

这些改进覆盖了 WebUI 交互、API 兼容性、工具链优化及多平台集成，项目在可用性与开发者体验方面稳步前进。

---

### 4. **社区热点**
当前最受关注的功能需求集中在 **Dream 系统作业的可控性** 和 **WebUI 性能优化**：
- **Issue #3885**（enhancement）：用户强烈呼吁为 Dream 记忆整理任务添加全局开关配置，避免即使禁用后仍自动注册 Cron 作业，影响资源与 Token 消耗。此诉求反映用户对“后台行为透明化”的核心期待。
- **PR #3952**（feat(memory)）：针对长期记忆冗余问题提出 MECE 结构化提示优化方案，虽未合并，但引发对记忆系统效率的深度讨论。
- **PR #3953 / #3951**：通过分批渲染侧边栏、保留折叠状态 DOM 结构等方式提升 WebUI 响应速度，获得积极反馈。

链接：  
[#3885](https://github.com/HKUDS/nanobot/issues/3885) | [#3952](https://github.com/HKUDS/nanobot/pull/3952) | [#3953](https://github.com/HKUDS/nanobot/pull/3953)

---

### 5. **Bug 与稳定性**
今日报告的关键 Bug 如下（按严重程度排序）：

| Issue | 描述 | 状态 | 是否已有 Fix |
|------|------|------|--------------|
| #3956 | 使用 `read_file` 读取图片后，Anthropic API 因 content 为 list 格式返回 400 错误 | CLOSED | ✅ 已修复（见 PR #3940 逻辑延伸） |
| #3931 | `restrictToWorkspace=true` 导致外部 curl 等命令被安全守卫误拦截 | CLOSED | ✅ 已修复（PR #3933） |
| #3028 | 心跳机制重复创建定时任务，导致问候语重复发送且无法读取上下文 | OPEN | ❌ 尚无有效解决方案 |
| #3945 | WebUI 中出现 duplicate `tool_call_id` 导致对话中断 | CLOSED | ✅ 快速修复 |

最突出的问题是 **#3028**：心跳任务重复注册，既浪费资源又破坏用户体验，需重构事件调度逻辑。

---

### 6. **功能请求与路线图信号**
用户明确提出以下新功能需求，预示未来版本可能纳入：
- **Dream 作业全局开关**（#3885）：已有初步实现思路，预计将在下个版本中作为可配置项推出。
- **xAI Grok OAuth 支持**（PR #3936）：正在开发中，将降低用户使用门槛，强化多模态 AI 接入能力。
- **Ollama / OpenAI Codex 图像生成支持**（PR #3946, #3954）：扩展 multimodal 能力，满足创意类 Agent 应用场景。
- **BM25-lite 技能路由**（PR #3865）：旨在减少系统提示 token 开销，提升推理效率，符合轻量化部署趋势。

---

### 7. **用户反馈摘要**
从 Issue 评论中提取的真实痛点包括：
- **不可控的后台行为**：多位用户抱怨 Dream 技能“即使配置禁用仍运行”，认为缺乏透明度与自主权（#3885, #3948）。
- **WebUI 访问限制**：嵌入式 WebUI 默认仅允许 localhost 访问，Docker 外无法使用，阻碍远程协作（#3876）。
- **API 兼容性问题**：Moonshot/Kimi 等平台对参数组合敏感，现有抽象层未能完全适配（#3939）。
- **性能卡顿**：长对话历史下侧边栏加载缓慢，影响操作流畅度（#3953 反馈）。

正面反馈集中于 **Novita AI 支持** 和 **微信消息防丢机制**，显示社区对生态扩展与稳定性提升的认可。

---

### 8. **待处理积压**
以下 Issue 或 PR 建议优先跟进：

- **#3028**（OPEN, 46天未更新）：心跳任务重复创建问题长期存在，影响系统资源管理与用户体验，需设计更优雅的任务调度机制。
- **#3885**（OPEN, 5天）：Dream 开关需求明确且具高优先级，应尽快实现并测试。
- **#3876**（CLOSED but 涉及 Docker 网络穿透）：虽已关闭，但实际部署中仍普遍存在，建议补充文档或提供环境变量覆盖选项。

---

**总结**：NanoBot 今日在稳定性、多平台支持与用户体验上取得进展，尤其在 WebUI 与执行工具链方面有实质性优化。核心挑战在于提升后台任务可控性与解决跨平台 API 兼容性。建议下一阶段聚焦 Dream 系统可配置化与心跳机制重构。

</details>

<details>
<summary><strong>Zeroclaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

**Zeroclaw 项目动态日报（2026-05-22）**

---

### 1. **今日速览**

过去24小时内，Zeroclaw 项目活跃度显著提升，共处理 **22 条 Issues** 与 **50 条 PRs**，其中待合并 PR 达 46 项，表明开发团队正加速推进功能迭代。核心焦点集中在 **TUI（终端用户界面）架构重构**、**多 Agent 运行时优化** 及 **第三方 Provider 兼容性增强**。整体项目健康度良好，但存在若干高优先级 Bug 需紧急修复。

---

### 2. **版本发布**

无新版本发布。

---

### 3. **项目进展**

今日合并/关闭的重要 PR：

- **[#6839] feat(runtime): RPC dispatch layer and Unix socket transport**  
  ✅ 已合并  
  该 PR 实现了 ZeroClaw 守护进程的底层 RPC 通信层，支持通过 Unix 套接字直接与 TUI 客户端通信，绕过了原有的 HTTP/WebSocket 网关，为后续 TUI 独立运行奠定基础。此变更属于基础设施升级，不影响现有用户接口。  
  🔗 https://github.com/zeroclaw-labs/zeroclaw/pull/6839

- **[#6398] feat!: multi-agent runtime and schema V3**  
  ✅ 已合并  
  此前提交的“多 Agent 运行时”重大更新已完成合并，标志着项目正式进入多智能体协同工作流阶段。此版本包含大量破坏性 API 变更（Schema V3），建议用户在升级前查阅迁移指南。  
  🔗 https://github.com/zeroclaw-labs/zeroclaw/pull/6398

此外，多个长期悬而未决的功能性 PR 仍在推进中，如技能管理 API（#6700）、Jira 集成（#6481）等，显示项目正系统性扩展工具生态。

---

### 4. **社区热点**

最活跃议题集中于 **TUI 相关设计与实现**：

- **[#6826] ZeroClaw TUI**（创建于 2026-05-21）  
  提出构建独立终端界面作为主要操作入口，强调与 Web Dashboard 功能对齐，服务于 headless 服务器和 enclave 部署场景。
  
- **[#6823] TUI ACP Bridge**  
  定义 TUI 与守护进程间的 JSON-RPC 协议桥接机制，确保低延迟交互。

- **[#6821] Move crates/zeroclaw-tui to apps/tui**  
  反映项目结构规范化需求，将 TUI 从 `crates/` 移至 `apps/` 目录，符合 Rust 项目最佳实践。

这些议题由核心维护者 @singlerider 主导，形成连贯路线图，预示 TUI 将成为下一阶段重点交付模块。

---

### 5. **Bug 与稳定性**

按严重程度排序的关键问题：

| Issue | 严重性 | 描述 | 状态 |
|------|--------|------|------|
| [#6059] Incompatible with DeepSeek-V4 API format | S2 (degraded) | DeepSeek 模型在 thinking mode 下返回格式不兼容，导致解析失败 | 进行中 |
| [#6699] tool_filter_groups is a no-op for real MCP tools | S1 (blocked) | MCP 工具过滤逻辑失效，影响多工具环境配置 | 已接受，待修复 |
| [#6847] WhatsApp channel not showing QR | S1 (blocked) | 新 Whatsapp 频道初始化时无法显示二维码，阻碍用户接入 | 新建，暂无进展 |
| [#6844] slack bot_token needs config file | S1 (blocked) | Slack token 必须写入配置文件，不支持环境变量，违反安全实践 | 新建 |
| [#6841] vision_provider silently ignored | S1 (blocked) | 多模态图像输入被路由至 fallback provider，视觉功能失效 | 新建 |

其中，[#6699] 已有初步修复方向，预计将在近期提交补丁。其余问题尚无对应 PR，需开发者介入。

---

### 6. **功能请求与路线图信号**

用户及贡献者提出多项具前瞻性价值的需求：

- **jina.ai 作为 web_search provider**（#6827）：提升免费层搜索能力，降低外部依赖成本。
- **NEAR AI Cloud 支持**（#6842）：拓展去中心化 AI 推理生态接入。
- **文件上传协议**（#6819）：支持二进制文件传输，增强 agent 工作空间交互能力。
- **会话级运行时参数覆盖**（#6817）：允许临时调整模型、温度等参数而不重启服务，提升运维灵活性。

结合当前 PR 活动，上述功能极有可能纳入未来 0.80+ 版本发布计划。

---

### 7. **用户反馈摘要**

- **正面反馈**：  
  用户对项目整体架构表示认可，尤其赞赏多 Agent 支持与模块化设计。有用户称：“这是目前唯一能稳定运行多智能体协作的工具。”（源自 #6846 评论）

- **负面痛点**：
  - Windows 最小化构建体积过大（#6836），期望从 26MB 降至 ~6MB；
  - Slack/WhatsApp 等通道的身份验证方式僵化，缺乏环境变量支持；
  - DeepSeek 等新模型适配滞后，API 变更响应慢；
  - TUI 尚未正式发布，终端用户仍依赖 Web UI，操作效率受限。

---

### 8. **待处理积压**

以下重要议题超过两周未获实质性回应：

- **[#5779] feat(security): add gated_commands TOTP gate for shell tool**  
  自 2026-04-15 提出，涉及高危命令的二次认证机制，影响安全性关键路径。当前状态为 `needs-maintainer-review`，建议优先处理。  
  🔗 https://github.com/zeroclaw-labs/zeroclaw/pull/5779

- **[#5987] feat: nix package -> add (contains rust app + web ui)**  
  Nix 包管理集成长期停滞，影响 Linux 发行版打包分发。  
  🔗 https://github.com/zeroclaw-labs/zeroclaw/pull/5987

建议维护团队评估资源投入，避免技术债务累积。

--- 

*报告生成时间：2026-05-22*  
*数据来源：GitHub API / zeroclaw-labs/zeroclaw*

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

**PicoClaw 项目动态日报（2026-05-22）**

---

### 1. **今日速览**
过去24小时，PicoClaw 保持高度活跃状态：共处理 9 条 Issue 更新（7 条已关闭）和 27 条 PR 更新（11 条已合并），并发布了一个 nightly 构建版本 v0.2.8-nightly.20260522。社区贡献频繁，涵盖功能增强、依赖升级与多平台集成优化。整体项目健康度良好，迭代节奏稳定。

---

### 2. **版本发布**
今日发布 **nightly 版本 v0.2.8-nightly.20260522.5bbebb5f**，为自动化构建版本，可能包含实验性功能或未充分测试的变更。建议用户谨慎使用生产环境。完整变更日志见：[Full Changelog](https://github.com/sipeed/picoclaw/compare/v0.2.8...main)。

> ⚠️ 注意：此版本非稳定 release，适用于开发测试用途。

---

### 3. **项目进展**
本周合并的关键 PR 包括：
- **#2914**：新增请求级上下文策略（`request-scoped context policies`），通过 `agents.defaults.turn_profile` 实现全局 turn 控制，提升灵活性与可配置性。
- **#2779 / #2776 / #2772**：完善 Telegram 论坛主题支持，修复消息路由丢失问题，确保子话题内工具调用与回复正确归属。
- **#2778**：引入 `working_summary` 工具反馈模式，在聊天界面实时显示任务进度，提升用户体验透明度。
- **#2917**：新增 NEAR AI Cloud 作为 OpenAI 兼容 LLM 提供商，扩展模型生态支持。

这些改进显著增强了多 Agent 协作、跨平台通信及开发者自定义能力。

---

### 4. **社区热点**
最活跃的议题为：
- **#629**（已关闭）：关于 LLM 调用失败无重试机制的问题，引发 15 条评论，反映对服务健壮性的高期待。
- **#2702**（已关闭）：多用户频道中对话历史缺乏发送者标识，影响群聊场景下的上下文清晰度。
- **#2916**（开放）：提出 CPU/内存/IO 性能优化方案，虽仅 2 条评论，但涉及底层架构优化，具长期价值。

此外，**#2901**（GPT4Free 原生支持）虽未获评论，但被标记为“Feature”，显示社区对低成本推理后端的需求强烈。

---

### 5. **Bug 与稳定性**
今日关闭的 Bug 报告如下（按严重程度排序）：
1. **#2795**：对话历史仅保留最后一条用户消息，其余被截断 → **已有修复**（关联 PR 未直接标注，但属近期会话压缩逻辑调整范围）。
2. **#2787**：Session API 返回的消息缺少独立时间戳，统一使用 session.updated → **需跟进**，暂无对应 PR。
3. **#2798**：Telegram PDF 流数据异常导致会话中断 → **已关闭**，推测由特定文件类型处理缺陷引起，需验证是否彻底解决。

总体来看，核心功能稳定性良好，边缘场景（如大文件传输、多用户会话）仍需关注。

---

### 6. **功能请求与路线图信号**
用户明确提出以下重要需求：
- **子 Agent 角色隔离**（#2775）：要求子 Agent 加载专属系统提示而非继承根 AGENT.md，避免身份混淆 → **已有技术讨论**，但未形成 PR。
- **FUNDING.yml 支持**（#2912）：呼吁建立捐赠渠道，反映社区希望长期资助项目发展的意愿。
- **GPT4Free 原生支持**（#2901）：明确请求将 g4f 作为一等公民 provider → **已有 PR 待审**（#2901 本身为 Issue，相关实现可能在后续 PR 中）。

结合当前 PR 趋势，下一版本有望强化多 Agent 治理、降低成本敏感型部署支持。

---

### 7. **用户反馈摘要**
- **痛点集中点**：
  - 多用户环境下历史消息归属不清（#2702）
  - 子 Agent 角色混乱影响任务分工（#2775）
  - PDF/Telegram 等富媒体处理不稳定（#2798）
- **满意之处**：
  - 工具反馈机制（如 working_summary）提升交互感知（#2778）
  - 持续扩展 LLM 提供商支持（Anthropic、NEAR AI 等）
- **使用场景**：
  - 个人开发者运行轻量级本地推理节点
  - 企业部署多角色 AI 工作流（Planner/Builder/Auditor 等）

---

### 8. **待处理积压**
- **#2775**（子 Agent 角色继承问题）：创建于 5 月 5 日，已关闭但标记“stale”，需确认是否完全解决或需文档补充。
- **#2787**（消息时间戳缺失）：长期存在的基础 API 缺陷，影响调试与审计能力，建议优先纳入维护计划。
- **#2662**（统一供应商文档）：文档类 PR 开放超一个月，虽非紧急，但有助于降低新用户上手门槛。

建议维护团队定期审查此类“stale”标签项，避免技术债累积。

--- 

*数据来源：GitHub Repository sipeed/picoclaw | 生成时间：2026-05-22*

</details>

<details>
<summary><strong>hermesagent</strong> — <a href="https://github.com/NousResearch/hermes-agent">NousResearch/hermes-agent</a></summary>

好的，作为 AI 智能体与个人 AI 助手领域的开源项目分析师，以下是根据您提供的数据生成的 **hermesagent** 项目动态日报。

---

### hermesagent 项目动态日报 (2026-05-22)

#### 1. 今日速览
hermesagent 项目在 2026-05-22 表现出极高的活跃度，Issue 和 PR 的更新数量均达到数百条。社区讨论热烈，主要集中在功能增强、平台集成（如 Telegram、Feishu）以及核心代理工具的稳定性改进上。整体来看，项目正处于一个快速迭代和功能扩展的阶段，维护者响应迅速，多个关键 Bug 已有修复方案。

#### 2. 版本发布
*   无新版本发布。

#### 3. 项目进展
今日合并/关闭的重要 PR 较少，但新提交的 PR 数量庞大，显示出开发团队的高效推进。以下是一些值得关注的 PR：
*   **#30183**: 修复了子代理在执行 `delegate_task` 时可能被用户中断的问题，提升了多任务处理的稳定性。
*   **#30175**: 解决了 Gemini API 模式下配置错误导致的问题，增强了配置的健壮性。
*   **#30176**: 引入了针对本地可靠性的强化措施，包括 `hermes doctor --operator` 检查，并改进了 Kanban DB 的初始化路径。
*   **#30177**: 修复了 `platform_toolsets` 配置不生效的问题，确保不同平台上的工具集正确启用。
*   **#30180**: 为自托管设置添加了 JWT 凭证注入功能，提升了安全性。
*   **#30181**: 修复了 CLI 会话结束后进程无法正常退出的问题，避免了资源泄漏。
*   **#30182**: 恢复了 ACP 会话中命名自定义提供者的持久化，改善了会话恢复体验。
*   **#30164**: 修复了 Feishu 平台在回复消息时意外创建话题的问题。
*   **#30167**: 为 Feishu 平台实现了 CardKit 流式卡片支持，提升了交互体验。
*   **#30163**: 新增了 `autonomous-ai-agents` 技能，用于并行任务编排。
*   **#30136**: 引入了 s6 作为 Docker 镜像的新 init 进程，增强了容器化部署的可靠性。

这些 PR 涵盖了从核心代理行为、CLI 工具链、网关通信到特定平台集成的广泛领域，表明项目正在稳步向前发展。

#### 4. 社区热点
今日最活跃的 Issue 和 PR 反映了用户对以下方面的关注：
*   **Telegram 集成与自动化 (#21587)**: 用户期待利用 Telegram 最新的 AI Bot 功能，如 Guest Bots 和 Bot-to-Bot 交互，以增强 Hermes Agent 在多 Agent 协作和团队工作流中的应用。
*   **xAI OAuth 认证问题 (#26847)**: 关于 xAI OAuth 对标准 SuperGrok 订阅者返回 HTTP 403 的错误报告，凸显了第三方服务集成中的认证复杂性。
*   **Dashboard 主题可读性 (#18080)**: 用户反馈当前主题在字体选择和色彩对比度上存在不足，影响了长时间使用的舒适度。
*   **NeuTTS 安装失败 (#3002)**: 一个关于依赖项 `pip` 缺失导致的安装失败的 Bug，表明在某些环境中基础依赖管理仍需完善。
*   **Homebrew 安装缺少内置技能 (#24360)**: 用户指出通过 Homebrew 安装的 Hermes Agent 缺少 `skills/` 文件夹，建议官方 Homebrew 版本应与源码版本保持一致。
*   **viking_remember 工具数据未持久化 (#17998)**: 该工具声称成功记录记忆，但实际上并未写入 OpenViking，这是一个影响核心记忆功能的严重 Bug。
*   **Claude CLI 集成问题 (#29125)**: 用户报告 Hermes 无法通过 Claude CLI 正常工作，涉及 Anthropic 模型的选择和 token 处理。
*   **内存工具替换/删除操作失败 (#21844)**: 该 Bug 已被标记为重复并关闭，但反映了用户对核心记忆工具稳定性的担忧。
*   **中文本地化需求 (#24252, #12961)**: 社区成员主动提出并提供中文简化版翻译补丁，显示出对中文用户群体的强烈支持意愿。

#### 5. Bug 与稳定性
今日报告的 Bug 主要集中在以下几个方面，按严重程度排列：
*   **P1 (高优先级)**:
    *   **#14036**: `--tui` 模式与 `byterover` 内存提供程序组合时，网关进程会在中途退出，导致会话不可用。此问题已有修复 PR (#30176)。
    *   **#20470**: Telegram DM 主题绑定在会话压缩后未刷新，导致预检压缩循环。此问题已有修复 PR (#30176)。
    *   **#29285**: `auth.json` 中的 `active_provider` 字段会静默覆盖 `config.yaml` 中的 `model.provider`，导致配置失效。此问题已有修复 PR (#30182)。
    *   **#29177**: 后台进程阻塞会话空闲/每日重置，导致会话无限累积。此问题已有修复 PR (#30181)。
    *   **#23450**: Hermes v0.13.0 向 OpenAI GPT-4o 发送了不支持的 `include` 参数，导致 API 调用失败。此问题已有修复 PR (#30125)。
*   **P2 (中等优先级)**:
    *   **#17998**: `viking_remember` 工具创建空会话，数据从未持久化。此问题已有修复 PR (#30177)。
    *   **#26058**: Discord 的 `auto_thread` 功能在 `free_response_channels` 中被禁用，影响了合法用例。此问题已有修复 PR (#30176)。
    *   **#28863**: `terminal.docker_extra_args` 配置项在 `_terminal_env_map` 桥接中丢失。此问题已有修复 PR (#30176)。
    *   **#29481**: `hermes doctor` SSH 检查忽略了配置的 SSH 用户/端口/密钥。此问题已有修复 PR (#30176)。
    *   **#20244**: Gemini 模型出现 HTTP 500 内部错误，影响与 Google 模型的通信。此问题已有修复 PR (#28438)。
    *   **#26172**: `hermes update` 命令在 fork 仓库上可能报告“已是最新”，即使上游有更新。此问题已有修复 PR (#30176)。
*   **P3 (低优先级)**:
    *   **#7237**: 长文本响应被截断，提示输出长度限制。此问题已有修复 PR (#30176)。
    *   **#3002**: NeuTTS 安装失败，因 `pip` 模块缺失。此问题已有修复 PR (#30176)。
    *   **#24860**: Dashboard Chat 中 Ctrl+V 粘贴和图像粘贴功能损坏。此问题已有修复 PR (#30176)。
    *   **#19287**: Telegram 图片以文件路径形式传递，而非原生 vision 内容，模型无法看到像素。此问题已有修复 PR (#30176)。
    *   **#29610**: Kanban 调度器仍存在 sqlite/WAL 文件描述符泄漏。此问题已有修复 PR (#30176)。
    *   **#11197**: `install.sh` 脚本需要 `xz-utils` 依赖。此问题已有修复 PR (#30176)。

#### 6. 功能请求与路线图信号
今日的功能请求和 PR 强烈暗示了项目的未来发展方向：
*   **多平台深度集成**: 对 Telegram、Feishu、WeCom 等平台的新特性支持和 Bug 修复，表明项目正致力于成为更强大的跨平台 AI 代理枢纽。
*   **增强的 Agent 能力**: 新增的 `parallel-orchestration` 技能和 `delegate_task` 的改进，显示了对复杂任务分解和多 Agent 协作能力的持续投入。
*   **用户体验优化**: 对 Dashboard 主题、CLI 工具链、桌面 GUI 启动器的改进，以及对中文本地化的支持，都指向提升用户友好性和可访问性的目标。
*   **安全与可靠性**: 引入 JWT 凭证注入、s6 init 进程、以及 `hermes doctor --operator` 检查，体现了对系统安全性和稳定性的高度重视。
*   **开发者工具**: 对 `hermes update` 命令的改进和对外部 Kanban worker lanes 的支持，旨在提升开发者和高级用户的效率。

#### 7. 用户反馈摘要
从 Issues 评论中提炼的真实用户痛点包括：
*   **安装与依赖管理**: 用户在不同 Linux 发行版上遇到 `xz-utils` 缺失和 `pip` 模块缺失的问题，反映出基础环境依赖的脆弱性。
*   **平台特定问题**: Telegram 和 Discord 等平台的集成问题（如图片处理、线程管理）是用户关注的重点，直接影响使用体验。
*   **配置复杂性**: 用户抱怨 `auth.json` 和 `config.yaml` 之间的配置冲突，以及某些配置项（如 `docker_extra_args`）的静默丢失，增加了上手难度。
*   **API 兼容性与稳定性**: 与 OpenAI、Gemini、xAI 等第三方 API 的兼容性问题频发，影响了 Hermes Agent 的核心功能。
*   **功能期望**: 用户希望 Hermes Agent 能提供更丰富的内置技能（如电子表格处理）、更好的主题定制、以及对新兴平台特性的快速跟进。
*   **本地化需求**: 中文用户群体对官方中文支持的呼声很高，社区成员甚至主动提供了翻译补丁。

#### 8. 待处理积压
*   **#18080 (Improved Themes for Dashboard)**: 这是一个长期存在的 Issue，用户对 Dashboard 主题的可读性提出了持续关注。虽然已有 PR 提及对此类问题的修复，但该 Issue 本身仍未关闭，表明可能需要更全面的 UI/UX 重构或新的主题设计方案。
*   **#21587 (Telegram Guest Bots, Bot-to-Bot, Stickers and Chat Automation)**: 此 Issue 提出的 Telegram 新功能具有前瞻性，但目前尚未有对应的 PR 被合并，可能需要进一步评估和规划。
*   **#24252 (Chinese (Simplified) localization)**: 尽管已有社区贡献的补丁集，但官方尚未正式采纳或将其纳入主分支，这可能是一个需要维护者更多关注和支持的长期需求。
*   **#15602 (google-workspace skill: add multi-account support)**: 对于拥有多个 Google Workspace 账户的用户来说，这是一个重要的功能增强点，但目前尚无明确的实现计划或 PR。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

**NanoClaw 项目动态日报（2026-05-22）**

---

### 1. **今日速览**
NanoClaw 在 2026-05-22 保持高活跃度，过去 24 小时内新增 3 个 Issue 和 20 个 PR 更新，其中 10 个已合并/关闭。项目整体进展迅速，重点集中在 Signal 认证修复、Telegram 集成及 Codex 全栈支持等关键功能推进上。无新版本发布，但社区对多平台适配和稳定性提升需求强烈。

---

### 2. **版本发布**
无新版本发布。

---

### 3. **项目进展**
今日共 **10 个 PR 被合并或关闭**，涵盖以下重要进展：

- **#1781**: 集成 Composio MCP 实现 Gmail/Calendar OAuth 托管服务，显著简化 GCP 配置流程（[链接](https://github.com/nanocoai/nanoclaw/pull/1781)）
- **#1780**: 新增 5 个容器技能（client-profile, design-avatar, telegram-ads, olx-research, olx-ad-generator），强化营销与客户端自动化能力（[链接](https://github.com/nanocoai/nanoclaw/pull/1780)）
- **#1757**: 新增 `send_file` MCP 工具，支持向聊天发送文件（图片/文档）（[链接](https://github.com/nanocoai/nanoclaw/pull/1757)）
- **#1749**: 修复 agent-runner 缓存逻辑，确保所有 `.ts` 文件变更触发重新加载，避免容器运行旧代码（[链接](https://github.com/nanocoai/nanoclaw/pull/1749)）
- **#1747 / #1737**: 分别集成 Todoist 和 Google Calendar MCP，扩展生产力工具链（[Todoist](https://github.com/nanocoai/nanoclaw/pull/1747), [Calendar](https://github.com/nanocoai/nanoclaw/pull/1737)）
- **#2576**: 修复 SDK 模式下 assistant text block 被误抑制的问题，恢复中间思考过程可见性（[链接](https://github.com/nanocoai/nanoclaw/pull/2576)）
- **#2577**: 优化 deshi 通道上下文注入机制，从 SQLite 直接读取 session_routing 数据，减少冗余字段（[链接](https://github.com/nanocoai/nanoclaw/pull/2577)）

这些合并表明项目正系统性增强工具集成、容器稳定性和用户体验。

---

### 4. **社区热点**
今日最活跃议题为 **#2583**（restartService 静默失效）、**#2582**（signal-auth 死锁）和 **#2581**（JSON 字段名不兼容 signal-cli 0.13+），均由 @snymanpaul 提交，反映 macOS launchd 服务管理与 signal-cli 升级带来的兼容性挑战。

同时，**PR #2585**（Telegram 频道支持 via grammy）成为焦点，提出者 @rwifeng 强调其完整功能覆盖（文本/媒体/命令/状态指示），被视为跨平台消息通道的重要扩展（[链接](https://github.com/nanocoai/nanoclaw/pull/2585)）。

---

### 5. **Bug 与稳定性**
#### 严重 Bug（需立即关注）：
1. **#2583**: `launchctl kickstart -k` 在 plist 未加载时静默失败，导致服务重启无效（[链接](https://github.com/nanocoai/nanoclaw/issues/2583)）  
   → **已有修复 PR #2584** 针对 signal-auth 问题，可能间接缓解此场景。

2. **#2582**: `signal-auth listAccounts` 在无超时设置下与 daemon 配置文件锁冲突，引发死锁（[链接](https://github.com/nanocoai/nanoclaw/issues/2582)）  
   → 尚无对应 fix PR，建议引入 spawnSync 超时机制。

3. **#2581**: signal-cli ≥0.13 返回 JSON 中 `account` 字段变为 `number`，导致认证误判“无账户”（[链接](https://github.com/nanocoai/nanoclaw/issues/2581)）  
   → **已有修复 PR #2584** 明确处理此问题（[链接](https://github.com/nanocoai/nanoclaw/pull/2584)）。

---

### 6. **功能请求与路线图信号**
用户持续推动以下方向：
- **多 AI 编码 CLI 支持**：PR #2580（Codex-only 安装）、#2474（AI-coding-CLI 选择器）显示项目正构建统一抽象层以支持 Claude Code、Codex 等多后端（[链接](https://github.com/nanocoai/nanoclaw/pull/2580)）。
- **Telegram 深度集成**：PR #2585 及历史 #1780 中的 telegram-ads 技能表明 Telegram 作为核心通信渠道地位巩固。
- **MCP 生态扩展**：Gmail、Calendar、Todoist 等 MCP 工具集中上线，反映“Agent-as-a-Tool”架构成熟化趋势。

---

### 7. **用户反馈摘要**
- **痛点**：Signal 认证流程在 macOS 上易受 launchd 状态影响，且 signal-cli 升级破坏向后兼容性；SDK 模式下用户无法看到中间推理过程，体验割裂。
- **满意点**：Composio 集成极大降低 OAuth 配置复杂度；`send_file` 工具和容器技能增强了实际工作流实用性。
- **使用场景**：多数反馈来自企业级部署环境，关注稳定性、跨平台一致性及自动化任务可靠性。

---

### 8. **待处理积压**
- **#2582**（signal-auth 死锁）：虽无直接 fix，但属高优先级生产环境问题，建议评估是否纳入近期迭代。
- **#2361**（tighten codex provider contracts）：长期未合并，涉及核心抽象层重构，可能影响后续多 CLI 支持扩展。
- **#2337**（surface skill catalog to non-Claude providers）：与 #2580 关联紧密，若 Codex 全栈支持落地，此 PR 应加速推进。

--- 

*数据来源：GitHub API · 统计周期：2026-05-21 00:00 至 2026-05-22 23:59 UTC*

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

**IronClaw 项目动态日报（2026-05-22）**

---

### 1. **今日速览**
过去24小时内，IronClaw 项目保持高度活跃状态：共处理 Issue 更新 24 条、PR 更新 46 条，其中 11 个 Issue 和 21 个 PR 已关闭。核心焦点集中在 Reborn 架构迁移的关键路径推进上，包括产品级认证合约构建、技能上下文适配及成本预算框架落地。整体开发节奏稳健，无重大版本发布，但基础设施层持续夯实。

---

### 2. **版本发布**
无新版本发布。当前最新 GitHub 标签为 `ironclaw-v0.27.0`（发布于 2026-04-29），而 crates.io 仍仅支持至 `0.24.0`，存在依赖链断裂风险（见 Issue #3259）。建议下游用户关注该问题并考虑临时锁定依赖版本。

---

### 3. **项目进展**
**关键合并与关闭 PR：**
- **#3831**（已关闭）：完成 staged secret egress 框架，确立生产环境凭据路由机制，MCP 凭证仅限 `tools/call` 通道使用，提升安全性。
- **#3852**（已关闭）：修复 before-inbound policy 调用超时与日志脱敏问题，增强 WebUI Beta 的消息准入控制稳定性。
- **#3855**（已关闭）：将通用扩展安装状态迁移至 `ironclaw_extensions` crate，解耦产品适配器逻辑，统一生命周期管理。

这些变更强化了 Reborn 运行时边界安全性和模块化程度，为后续 Lane 4–10 的集成奠定基础。

---

### 4. **社区热点**
最活跃议题集中于 **Reborn 产品面迁移** 与 **WebUI Beta 功能完善**：
- **#3031**（EPIC: Reborn product surface migration）持续更新，定义跨服务兼容性保障机制，关联多个子任务（如 #3020, #3022）。
- **#3846**（Question: notify_channels 继承来源渠道）反映用户在多平台（Telegram/REPL）创建任务时的行为困惑，凸显 UI 一致性需求。
- **#3865**（新 PR）提出 auth contracts 实现，获初步关注，体现社区对标准化身份流程的期待。

讨论热度表明用户对 Reborn 迁移透明度和 WebUI 操作直觉性高度敏感。

---

### 5. **Bug 与稳定性**
发现 3 类关键问题：
1. **高优先级**：Nightly E2E 失败（#3447），涉及数据库连接或测试环境不稳定，尚无 fix PR，需排查 CI 配置。
2. **中优先级**：Failed Mission Retry 按钮失效（#3839），返回 `fired:false`，疑似后端状态同步异常，暂无 PR。
3. **低优先级**：Channel 徽章视觉不一致（#3840），属 UI 样式问题，可纳入后续优化迭代。

建议优先处理 E2E 稳定性与 Mission 重试逻辑。

---

### 6. **功能请求与路线图信号**
- **Slack ProductAdapter MVP**（#3857）明确列入 Lane 10，预示即将支持 Slack 原生集成。
- **Per-channel tool filtering**（#1378 PR 长期开放）显示多租户/多通道部署场景下工具可见性控制将成为标准能力。
- **Cost-based budgets**（#3841 PR）落地 USD 级资源配额，呼应企业级成本控制需求。

以上均指向 IronClaw 向企业级 SaaS 平台演进的战略方向。

---

### 7. **用户反馈摘要**
- **痛点**：WebUI 中 mission 来源渠道继承规则不清晰（#3846）；channel 徽章缺乏图标区分（#3840）。
- **满意点**：Reborn 技能系统模块化设计获得开发者认可（#3854 PR 评论提及“clean separation”）。
- **场景诉求**：企业客户需要细粒度预算控制（#3841）与 OAuth 流程标准化（#3810）。

反馈集中于 **降低认知负荷** 与 **增强企业级治理能力**。

---

### 8. **待处理积压**
- **#3259**（crates.io 版本滞后）：自 2026-05-05 提出，影响下游依赖，超 17 天未响应，需协调发布流程。
- **#1378**（per-channel tool filtering）：PR 创建于 2026-03-18，超 65 天未合并，涉及复杂路由逻辑，需重新评估优先级。
- **#3447**（Nightly E2E 持续失败）：自 5 月 10 日起反复出现，可能反映测试套件脆弱性，需专项治理。

建议本周内安排 backlog grooming 会议处理上述事项。

--- 

*数据来源：GitHub.com/nearai/ironclaw | 生成时间：2026-05-22*

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

**LobsterAI 项目动态日报（2026-05-22）**

---

### 1. **今日速览**
过去24小时，LobsterAI 项目整体活跃度保持平稳。共处理了12条 Pull Request，其中9条仍在待合并状态，3条已完成合并或关闭。无新 Issues 产生，表明当前开发重点集中在功能迭代与稳定性优化上。项目暂无新版本发布，处于持续集成与测试阶段。

---

### 2. **版本发布**
无新版本发布。

---

### 3. **项目进展**
今日共完成3个 PR 的合并/关闭：
- **#2026**：修复了因 `dreaming` 配置中 `model` 和 `timezone` 属性不符合 OpenClaw JSON schema 导致的网关启动崩溃问题。此修复提升了系统启动稳定性，尤其对 OpenClaw 引擎用户至关重要。
- **#2025 & #2024**：由 @fisherdaddy 提交的 UI 重构与设置优化类 PR，涉及 IM Bot 管理界面重设计与网关重启逻辑优化，虽摘要未详述，但结合标签推测为前端体验增强类更新。

这些合并表明项目正稳步推进核心模块的稳定性与用户体验优化。

---

### 4. **社区热点**
目前无活跃讨论的 Issues 或 PR。所有开放 PR 均标记为 `[stale]`，最后更新集中于 2026-05-21，说明近期社区互动较少，可能处于开发节奏调整期。

---

### 5. **Bug 与稳定性**
今日无新增 Bug 报告。但多个长期存在的 PR 涉及关键稳定性问题：
- **#2026** 已修复因配置属性非法导致的网关崩溃（高严重性），现状态为 CLOSED。
- **#1544** 提出 GitHub Copilot OAuth 轮询未在设置关闭时终止，可能导致资源泄漏（中严重性），尚无合并。
- **#1543** 指出审批对话框硬编码中文字符串，破坏国际化一致性（中严重性），已有修复方案但未合并。

建议优先处理 #1544 与 #1543，以提升多语言支持与认证流程健壮性。

---

### 6. **功能请求与路线图信号**
多个长期 PR 显示用户对以下功能有明确需求：
- **系统通知机制**（#1536）：希望在 Cowork 会话完成或失败时收到原生通知，提升任务感知能力。
- **消息收藏/书签**（#1538）：支持对 AI 回复进行标记，便于长对话检索。
- **会话标签分类**（#1542）：自定义标签与筛选功能，增强会话组织能力。
- **引擎启动超时交互**（#1546）：提供取消与日志查看选项，改善卡死体验。

这些功能均围绕“提升用户体验”与“增强任务可管理性”展开，预计将在下一版本中逐步落地。

---

### 7. **用户反馈摘要**
从 PR 描述中可见真实痛点：
- 用户反馈切换至英文模式后，危险操作审批对话框仍显示中文，严重影响使用体验（#1543）。
- 定时任务修改通知渠道后无法正确重置为“不通知”，暴露表单初始化逻辑缺陷（#1547）。
- Agent 技能更新后徽章未即时刷新，需手动切换 Agent 才能生效，影响操作效率（#1545）。

整体反馈聚焦于 **国际化一致性、UI 响应及时性、配置持久化准确性** 三大方向。

---

### 8. **待处理积压**
以下 PR 已停滞超一个月，需维护者关注：
- **#1536**：Cowork 会话完成通知（[链接](https://github.com/netease-youdao/LobsterAI/pull/1536)）
- **#1538**：AI 消息收藏功能（[链接](https://github.com/netease-youdao/LobsterAI/pull/1538)）
- **#1540**：记忆模块编辑按钮翻译缺失（[链接](https://github.com/netease-youdao/LobsterAI/pull/1540)）
- **#1542**：会话标签系统（[链接](https://github.com/netease-youdao/LobsterAI/pull/1542)）
- **#1543**：审批对话框国际化（[链接](https://github.com/netease-youdao/LobsterAI/pull/1543)）
- **#1544**：OAuth 轮询未终止（[链接](https://github.com/netease-youdao/LobsterAI/pull/1544)）
- **#1545**：Agent 技能同步延迟（[链接](https://github.com/netease-youdao/LobsterAI/pull/1545)）
- **#1546**：引擎启动超时交互（[链接](https://github.com/netease-youdao/LobsterAI/pull/1546)）
- **#1547**：定时任务通知渠道重置异常（[链接](https://github.com/netease-youdao/LobsterAI/pull/1547)）

建议召开一次内部评审会议，评估优先级并分配负责人推进。

--- 

*数据来源：GitHub API · LobsterAI (netease-youdao/LobsterAI)*

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyclaw">TinyAGI/tinyclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

**Moltis 项目动态日报（2026-05-22）**

---

### 1. **今日速览**  
过去24小时内，Moltis 项目活跃度较高，共新增7条 Issue 和5条 PR，无新版本发布。社区对 Docker 环境下的功能稳定性及语音/文件处理能力提出多项改进需求，同时开发者正积极修复关键 Bug 并扩展云服务商支持。整体进展稳健，但需关注容器化部署中的兼容性问题。

---

### 2. **版本发布**  
无新版本发布。

---

### 3. **项目进展**  
- **PR #1035**: 修复了 Docker 环境下浏览器沙箱路径解析失败的问题，通过自动检测宿主机数据挂载提升容器兼容性（[链接](https://github.com/moltis-org/moltis/pull/1035)）。
- **PR #1034**: 修正了 Twilio 语音收集（gather）逻辑，确保 SpeechResult 和 Digits 在通话进行中正确处理，避免语音响应中断（[链接](https://github.com/moltis-org/moltis/pull/1034)）。
- **PR #1031**: 新增 NEAR AI Cloud 作为 OpenAI 兼容的 LLM 提供商，支持模型发现与 TEE 能力展示（[链接](https://github.com/moltis-org/moltis/pull/1031)）。
- **PR #1005 [CLOSED]**: 已合并，为 Codex 提供者添加 reasoning_effort 参数透传，增强推理过程可控性（[链接](https://github.com/moltis-org/moltis/pull/1005)）。

---

### 4. **社区热点**  
- **Issue #977**：用户报告在 Docker/LXC 环境中浏览器沙箱无法创建 `/data/browse` 目录，已有4条评论讨论解决方案，反映生产环境部署痛点（[链接](https://github.com/moltis-org/moltis/issues/977)）。
- **Issue #1038**：外部贡献者提交 NEXUS 预测市场 API 实现，集成 x402 支付与 Agentic Market 验证，引发对 Moltis 生态集成的兴趣（[链接](https://github.com/moltis-org/moltis/issues/1038)）。

---

### 5. **Bug 与稳定性**  
按严重程度排序：
1. **#977**（高）：Docker 下浏览器沙箱权限错误，影响核心工具链运行；已有 PR #1035 提供修复方案。
2. **#1037**（中）：`send_image` 和 `send_document` 在 Docker 中失效，疑似路径映射问题；暂无对应 PR。
3. **#1032**（中）：Twilio 电话呼叫中 agent 仅问候不响应输入，属语音交互逻辑缺陷；PR #1034 已提交修复。
4. **#1030**（低）：OpenAI TTS 强制要求 `response_format=opus`，与 Speaches 库冲突；需配置层适配。

---

### 6. **功能请求与路线图信号**  
- **Piper TTS 音频转换支持**（#1029）：建议将 Piper 语音合成结果转换为标准音频格式，可能纳入下一版本的多模态输出优化。
- **Web UI 任意文件上传**（#1036）：允许用户通过界面直接上传附件，提升交互灵活性，与现有文件发送功能形成闭环。
- **NEAR AI Cloud 集成**（PR #1031）：表明项目正扩展多云 LLM 支持，未来或增加更多异构计算后端。

---

### 7. **用户反馈摘要**  
- **痛点集中点**：Docker/Kubernetes 部署场景下文件系统权限与路径映射问题频发（#977, #1037），暴露容器化适配不足。
- **使用场景**：企业用户依赖 Vault 加密存储密钥，但希望可选禁用以简化调试（#1033）；开发者偏好统一 TTS 输出格式（#1030）。
- **满意度**：Twilio 语音修复获积极预期（#1032），NEAR AI 支持被赞“及时”（PR #1031）。

---

### 8. **待处理积压**  
- **Issue #977**：自2026-05-06起持续活跃，涉及核心沙箱机制，虽已有 PR 但未关闭，建议尽快合并测试。
- **Issue #1037**：新近报告但无进展，若与 #977 同源则应关联处理。

--- 

*数据来源：GitHub.com/moltis-org/moltis | 生成时间：2026-05-22*

</details>

<details>
<summary><strong>QwenPaw</strong> — <a href="https://github.com/agentscope-ai/QwenPaw">agentscope-ai/QwenPaw</a></summary>

好的，作为 QwenPaw 项目的分析师，这是为您生成的 2026-05-22 项目动态日报。

---

### **QwenPaw 项目日报 (2026-05-22)**

**1. 今日速览**

过去24小时，QwenPaw 项目活跃度较高，社区互动频繁。共处理了26条 Issues 和 29条 PR，显示出开发者和用户群体持续的关注与贡献。整体状态健康，但存在一些需要优先处理的稳定性问题。

**2. 版本发布**

*   无新版本发布。

**3. 项目进展**

今日合并/关闭的重要 PR 主要围绕功能增强和问题修复展开：

*   **技能市场与前端优化:** PR #4518 完成了技能市场的初步构建，并重构了技能中心客户端以支持异步请求，提升了用户体验。PR #4591 对技能验证逻辑进行了完善，增强了工作区的健壮性。
*   **控制台体验提升:** PR #4520 和 #4598 解决了聊天页面输入框内容在切换页面后丢失的问题，显著改善了用户交互体验。
*   **核心功能修复:** PR #4576 修复了 WeChat iLink 通道的消息去重失效和无限重试问题，这是一个关键的稳定性修复。PR #4597 确保了通过 API 发送的 WeChat 消息失败时能正确报告，提高了系统的可靠性。
*   **测试与部署:** PR #4609 修复了 `test_mcp.py` 中的 bug，保证了测试流程的顺畅。PR #4608 回滚了一个关于自动初始化的变更，可能是出于稳定性考虑。

**4. 社区热点**

今日讨论最活跃的 Issue 是 **#4559: 超过40多个agent后 页面访问明显变慢**。该问题反映了用户在多 Agent 场景下对性能优化的迫切需求，评论中提到了具体的卡顿现象和期望的解决方案。

另一个热点是 **#4556: Voice transcription uses browser native Speech API instead of configured Whisper provider**。此问题指出了语音转录功能的一个关键缺陷，即配置未生效，导致用户无法使用自托管的 Whisper 服务，评论数量也较多，表明这是一个普遍困扰用户的功能点。

**5. Bug 与稳定性**

今日报告的 Bug 主要集中在特定通道（WeChat, DingTalk）和模型兼容性上，严重程度中等：

*   **高优先级:**
    *   **#4556:** 语音转录配置失效。已有 PR #4601 正在解决。
    *   **#4586:** DingTalk 频道中文文件名编码问题。已有 PR #4600 正在解决。
    *   **#4605:** Gemini/Gemma 模型 `max_tokens` 参数校验错误。此问题已获赞，需尽快修复。
*   **中优先级:**
    *   **#4612:** WeChat 通道图片发送不稳定。此问题较新，暂无对应 PR。
    *   **#4616:** Dream awakening 任务错误。此问题较新，暂无对应 PR。

**6. 功能请求与路线图信号**

用户提出了多项功能请求，显示出对更强大、更稳定、更易用的工具的期待：

*   **长期记忆与上下文管理 (#4551):** 用户强烈建议实现基于 DAG 的无损上下文压缩机制，以解决长期对话中信息丢失的问题。这指向了下一代 Agent 框架的核心能力。
*   **插件与钩子支持 (#4613):** 用户希望引入 `register_agent_hook` 等机制，以增强插件的灵活性和控制力，这为未来的扩展性铺平了道路。
*   **浏览器自动化稳定性 (#4584):** 用户希望将浏览器自动化工具从 `browser-use` 切换到更稳定的 `@playwright/cli`，这表明当前方案存在稳定性问题，是未来优化的重点方向。
*   **UI/UX 统一性 (#4593):** 用户对控制台页面风格不统一提出了建议，这属于用户体验层面的优化，有助于提升产品的专业感。

**7. 用户反馈摘要**

*   **痛点:** 多 Agent 性能瓶颈、特定通道（WeChat, DingTalk）的文件和图片发送不稳定、模型切换导致记忆丢失、浏览器自动化连接不稳定、UI 风格不统一。
*   **满意点:** 开发者社区响应迅速，许多 Bug 和 Feature Request 都有对应的 PR 在处理，体现了良好的开源协作氛围。
*   **不满意点:** 部分核心功能（如语音转录、文件发送）的配置未能按预期生效，影响了用户体验。

**8. 待处理积压**

*   **#3054: onebot频道定时任务无法发送到群** (Open for 55+ days): 这是一个历史较久的 Bug，涉及 onebot 频道的定时任务，需要关注其进展或寻求新的解决方案。
*   **#4559: 超过40多个agent后 页面访问明显变慢** (Open for 2+ days): 这是一个高优先级的性能问题，影响用户体验，建议尽快分配资源进行优化。

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>librefang</strong> — <a href="https://github.com/librefang/librefang">librefang/librefang</a></summary>

好的，作为一位 AI 智能体与个人 AI 助手领域的开源项目分析师，我将根据您提供的 GitHub 数据，为您生成一份关于 librefang 项目的动态日报。

---

### **librefang 项目动态日报 (2026-05-22)**

**1. 今日速览**

过去24小时，librefang 项目保持了极高的活跃度，共处理了100条 Issues 和 PRs（50条 Issues，50条 PRs）。项目整体状态健康，开发团队正积极修复大量高严重性安全问题，并推进多项性能优化和功能增强。CI/CD 流程稳定，但存在一些因依赖更新导致的临时性问题。

**2. 版本发布**

*   无新版本发布。

**3. 项目进展**

今日合并/关闭的重要 PR 表明项目在关键领域取得了显著进展：

*   **安全审计修复 (Critical/High):**
    *   **#5329:** 修复了 41 个端点返回通用错误信息的问题，这是一个关键的本地化问题。
    *   **#5330:** 修复了审计导出功能因认证方式变更而导致的 401 错误。
    *   **#5331:** 通过引入 `count_sessions()` 方法，解决了仪表盘轮询时性能瓶颈问题。
    *   **#5352:** 为 webhook URL 注册添加了 SSRF 防护，提升了 API 安全性。
    *   **#5320:** 修复了辅助 LLM 调用中 `response_format` 设置不当的问题，确保与严格输出格式的提供商兼容。
*   **功能增强:**
    *   **#5319:** 修复了配置页面子标签的 UI 问题，提升了用户体验。
    *   **#5326:** 优化了 `/api/status` 和 `/api/dashboard/snapshot` 的路由性能。
    *   **#5324:** 修复了审计页面导出功能的认证问题。
*   **SDK & 集成:**
    *   **#5268:** 修复了 WhatsApp 网关初始化查询阻塞的问题。
    *   **#5229:** 修复了 WhatsApp 回复上下文信息丢失的问题。

这些修复和优化表明项目正在稳步解决其安全性和性能方面的核心挑战。

**4. 社区热点**

今日最活跃的 Issue 是 CI 取消通知 (#5391)，该 Issue 详细报告了 PR #5318 上 Windows 测试失败的情况，并附有详细的日志链接，体现了社区对构建稳定性和测试覆盖率的关注。

另一个值得关注的开放 Issue 是 #5492，用户报告了安全漏洞报告链接失效的问题，这提醒维护者需要定期检查和更新项目安全策略文档中的链接。

**5. Bug 与稳定性**

今日报告的 Bug 主要集中在以下几个方面：

*   **高严重性安全问题 (High):**
    *   **#5503:** OIDC 认证回调函数记录了用户的邮箱（PII），存在隐私泄露风险。
    *   **#5332:** SQLite 数据库文件权限设置不当，可能导致敏感数据泄露。
    *   **#5511:** 跨代理通信 (`comms_send`) 未记录到哈希链审计日志中，存在安全盲区。
    *   **#5508:** 注册表内容注册接口返回了绝对文件系统路径，可能泄露系统信息。
    *   **#5507:** 自定义频道适配器可能与内部系统会话 ID 冲突，存在安全风险。
*   **性能问题 (High):**
    *   **#5502:** `extract_text_content` 函数在热路径上频繁分配内存，影响性能。
*   **测试与 CI 问题 (Medium):**
    *   **#5513:** 一个集成测试因为消息大小限制变更而失败。
    *   **#5500:** Dependabot PRs 在部署到 Cloudflare Pages 时失败，原因是认证 token 为空。
    *   **#5499:** main 分支上的 `cargo fmt` 检查失败，且 SDK 目录存在漂移。

这些问题大多已被识别并提交了对应的修复 PR，表明项目拥有强大的自检和响应机制。

**6. 功能请求与路线图信号**

今日的功能请求较少，但 PR #5480 (feat(runtime): owner-notify triage gate) 是一个重要的功能增强，它引入了“所有者通知”机制，允许代理在处理来自非所有者的消息前进行分类和通知，这对于构建更智能的“接待员”或“管家”式代理非常有价值。这表明项目正在向更高级别的自动化和智能代理交互方向发展。

**7. 用户反馈摘要**

从 Issues 中可以提炼出以下用户痛点：

*   **UI/UX 体验:** 用户反馈了配置页面的子标签显示问题和通知中心的键盘导航缺失，这表明前端界面仍有改进空间，尤其是在可访问性方面。
*   **安全合规:** 用户对 PII 泄露、数据库权限、SSRF 等安全问题表现出高度关注，这反映了企业级用户对安全合规性的严格要求。
*   **API 稳定性与错误处理:** 用户报告了 API 返回通用错误信息、认证失败等问题，说明 API 的错误处理和文档需要进一步完善。
*   **集成与兼容性:** 用户在 WhatsApp 集成、LLM 提供商兼容性等方面遇到的问题，表明项目在第三方服务的适配和稳定性上仍需持续投入。

**8. 待处理积压**

目前没有发现长期未响应的重要 Issue 或 PR。所有高严重性的 Issue 都已迅速得到响应并提交了修复 PR，显示了项目维护团队的高效和负责。

</details>

<details>
<summary><strong>openfang</strong> — <a href="https://github.com/RightNow-AI/openfang">RightNow-AI/openfang</a></summary>

**openfang 项目动态日报（2026-05-22）**

---

### 1. **今日速览**  
过去24小时内，openfang 项目整体活跃度较低，无新 Issues 提交或关闭，但有两个重要功能型 PR 处于待合并状态。项目在持续扩展云推理支持与本地推理稳定性方面稳步推进，暂无版本发布或重大社区讨论热点。整体运行平稳，开发节奏保持稳定推进。

---

### 2. **版本发布**  
无新版本发布。

---

### 3. **项目进展**  
今日无合并或关闭的 Pull Requests。当前有两个重要功能 PR 正在等待审核：

- **[#1210](https://github.com/RightNow-AI/openfang/pull/1210)**：新增对 NEAR AI Cloud 的支持，作为内置的 OpenAI 兼容推理提供商，支持 `NEARAI_API_KEY` 认证及默认端点。该功能将显著扩展项目的多平台兼容性，尤其利好使用 NEAR 生态的开发者。
- **[#1209](https://github.com/RightNow-AI/openfang/pull/1209)**：增强长时本地推理的可靠性，引入可配置的超时机制与 busy-agent 队列管理，解决自托管模型响应慢导致的阻塞问题。此改进提升了系统在复杂任务场景下的鲁棒性。

两项更新均聚焦于提升推理层的可扩展性与稳定性，标志着项目正从基础功能向生产就绪方向演进。

---

### 4. **社区热点**  
目前无活跃 Issue 或高互动 PR。两个待合并 PR 虽未收到评论反馈，但其技术价值已获内部认可。建议关注未来是否出现关于 NEAR AI 集成使用体验或本地推理超时策略的用户反馈。

---

### 5. **Bug 与稳定性**  
未报告新的 Bug、崩溃或回归问题。项目在当前阶段未暴露明显稳定性风险，系统运行状态良好。

---

### 6. **功能请求与路线图信号**  
用户通过 PR 间接表达了以下需求：
- 增加更多主流云推理平台支持（如 NEAR AI），反映用户对多云兼容性的强烈诉求；
- 优化本地推理性能与资源调度机制，表明自托管部署场景日益增多。

结合现有 PR 可见，下一版本可能重点加强“多后端支持”与“本地推理可靠性”两大方向，形成更完整的 Agent 基础设施能力。

---

### 7. **用户反馈摘要**  
暂无直接来自 Issue 的评论反馈。但从 PR 内容推断，潜在用户群体包括：
- 希望避免 vendor lock-in 的企业级开发者；
- 偏好私有化部署、重视延迟与数据控制的团队；
- 正在构建多模态 Agent 应用的研究人员。

目前尚无负面情绪表达，整体反馈倾向积极建设性。

---

### 8. **待处理积压**  
- **PR #1210**（NEAR AI 支持）：创建于 2026-05-21，已一天未获 review，建议维护者优先处理以加速生态扩展。
- **PR #1209**（长时推理优化）：创建于 2026-05-20，接近完成，建议尽快安排 review 以提升本地部署体验。

建议维护者在近期集中处理这两项关键功能提交通知。

--- 

*数据来源：GitHub @RightNow-AI/openfang | 分析时间：2026-05-22*

</details>

<details>
<summary><strong>AstrBot</strong> — <a href="https://github.com/AstrBotDevs/AstrBot">AstrBotDevs/AstrBot</a></summary>

**AstrBot 项目动态日报（2026-05-22）**

---

### 1. **今日速览**
AstrBot 在过去24小时内保持较高活跃度，共处理 Issue 更新 16 条、PR 更新 12 条，无新版本发布。社区反馈集中在插件生态扩展与核心稳定性优化，开发者响应积极，多个高优先级 Bug 已提交修复方案。整体项目运行平稳，功能迭代持续推进。

---

### 2. **版本发布**
无新版本发布。

---

### 3. **项目进展**
今日合并/关闭的重要 PR 包括：
- **#8272**（已合并）：新增 CLI 命令用于修改 AstrBot 仪表盘密码，解决用户忘记密码或自动更新后无法登录的问题（关联 Issue #8268）。
- **#8245**（已合并）：修复日志中错误提示不存在的指令（如 `/t2i`），引导用户使用正确指令或扩展。
- **#8185**（已合并）：修复 Windows 下非 ASCII 路径导致的 Faiss 索引读写失败问题，提升跨平台兼容性。

此外，多个功能增强 PR 仍在审查中，如 ChatUI 指令候选功能（#8279）、CLI 文档完善（#8280）等，显示项目正加强用户体验与运维支持。

---

### 4. **社区热点**
最活跃 Issue 为 **#8080**（11 条评论，9 个点赞），用户 @FFFold 强烈呼吁优化上下文管理策略，指出默认设置对新手极不友好，易导致 API 费用激增。该问题反映核心配置逻辑需更清晰引导与默认值调整。

另一热点为 **#8266**（14 条评论），新发布的群管插件 `astrbot_plugin_group_guardian` 获得关注，集成 AI 审核与 28 项群管功能，体现社区对智能内容治理的需求上升。

---

### 5. **Bug 与稳定性**
高优先级 Bug 如下：
- **#8056**（P0）：AstrBot 运行一段时间后 CPU 占用率达 100%，主线程 epoll_wait 忙等，疑似事件循环死锁。暂无 fix PR，需紧急排查。
- **#8047**：QQ 平台单条消息触发两次 LLM 调用，返回不同回复，影响体验。尚无解决方案。
- **#8282**：MCP DuckDuckGo 搜索时报类型错误（int vs ProviderRequest），SSE 流中断。属近期引入问题，需接口对齐。

其余 Bug 如语音引用报错（#8049）、启动 KeyError（#8275）等均有初步复现报告，部分可能由配置异常或依赖版本引起。

---

### 6. **功能请求与路线图信号**
用户明确提出多项功能增强需求：
- **插件指令调用机制**（#8281）：希望 Agent 能调用插件提供的指令（如查询余额），暗示未来需构建统一指令执行框架。
- **ChatUI 指令提示**（#8277）：建议添加输入时自动弹出可用命令列表，提升 Web 端交互效率，已有 PR #8279 实现中。
- **阿里云百炼 STT 支持**（#8271）：建议复用 TTS 架构扩展语音识别能力，体现对多模态服务集成的重视。

结合现有 PR，下一版本可能强化插件生态与 WebUI 交互体验。

---

### 7. **用户反馈摘要**
- **痛点集中**：上下文管理默认值不合理（#8080）、CPU 资源泄漏（#8056）、重复 LLM 调用（#8047）是高频抱怨点，均涉及核心调度逻辑。
- **满意点**：新群管插件功能丰富（#8266）、CLI 密码重置便捷（#8272）获正面评价。
- **使用场景**：企业微信对接（#5817）、Docker 部署、多平台适配（QQ/企业微信）为主要部署方式，用户对稳定性与易用性双重期待。

---

### 8. **待处理积压**
- **#8056**（CPU 占用问题）：自 5 月 7 日报告至今未解决，影响生产环境部署，建议优先分配资源排查事件循环逻辑。
- **#5817**（企业微信无回复）：自 3 月起持续存在，虽收到消息但未响应，可能涉及消息队列处理缺陷，需平台适配器专项审查。
- **#6325**（Dashboard 部署流程）：PR 创建超两月未合并，涉及 GitHub Pages 自动化部署，可能阻碍新用户上手，建议跟进。

--- 

*数据来源：[AstrBot GitHub Repository](https://github.com/AstrBotDevs/AstrBot)*

</details>

---
*本日报由 [Big Model Radar](https://github.com/ivanweng2077/big_model_radar) 自动生成。*