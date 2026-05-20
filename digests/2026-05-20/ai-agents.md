# OpenClaw 生态日报 2026-05-20

> Issues: 500 | PRs: 500 | 覆盖项目: 16 个 | 生成时间: 2026-05-20 03:35 UTC

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
过去24小时 OpenClaw 社区活跃度极高，共处理 Issue 更新 500 条、PR 更新 500 条，新增两个 Beta 版本发布。项目整体处于高速迭代阶段，重点围绕会话稳定性、安全增强与多平台支持展开。活跃问题中安全类与回归类 Bug 占比显著，反映用户对生产环境稳定性的高度关注。

---

### 2. **版本发布**

#### v2026.5.19-beta.2 & v2026.5.19-alpha.1
- **核心变更**：
  - Agents 行为规范明确化：修复应默认采用“干净的有界重构、精简内部逻辑、显式插件 SDK/API 废弃路径”。
  - 依赖升级：`@openclaw/proxyline` 更新至 0.3.3；Pi packages 升级至 0.75.1。
  - Node.js 最低支持版本提升至 22.x 线。
- **破坏性变更**：Node.js 22+ 为硬性要求，低于此版本将无法启动。
- **迁移建议**：用户需确保本地开发/部署环境使用 Node.js 22 或更高版本，并检查 Pi 相关插件兼容性。

> 📌 [v2026.5.19-beta.2](https://github.com/openclaw/openclaw/releases/tag/v2026.5.19-beta.2) | [v2026.5.19-alpha.1](https://github.com/openclaw/openclaw/releases/tag/v2026.5.19-alpha.1)

---

### 3. **项目进展**

#### 重要 PR 合并/关闭情况（截至 2026-05-20）
| PR # | 类型 | 主题 | 状态 | 影响 |
|------|------|------|------|------|
| #84347 | Docs | iMessage CLI wrapper 必须流式传输 JSON-RPC stdio | ✅ 已合并 | 提升 iMessage 通道互操作性 |
| #83753 | Commands | Doctor: 将交互式维护检查结构化 | ⏳ 待审核 | 增强诊断可观测性与审计能力 |
| #76091 | Discord | 修复回复时态生命周期一致性 | 👀 准备合并 | 改善用户体验与反馈准确性 |

> 🔧 多个长期悬而未决的会话恢复与消息投递问题正在被系统性解决，如 `/restore` 命令（#51889）和跨会话线程上下文存储（#51163）。

---

### 4. **社区热点**

#### 高热度 Issues（评论数 >10）
| Issue # | 标题 | 评论数 | 核心诉求 |
|--------|------|--------|----------|
| [#75](https://github.com/openclaw/openclaw/issues/75) | Linux/Windows Clawdbot Apps 缺失 | 105 | 跨平台桌面应用支持，对标 macOS/iOS/Android |
| [#67035](https://github.com/openclaw/openclaw/issues/67035) | Windows 聊天 UI 回归：输入丢失、流回复不可见 | 13 | 关键功能退化，影响可用性 |
| [#39604](https://github.com/openclaw/openclaw/issues/39604) | 添加 `tools.web.fetch.allowPrivateNetwork` 配置 | 12 | 允许工具访问内网资源，提升自动化能力 |

> 💬 用户强烈呼吁完善非 Mac 平台支持（尤其 Windows/Linux），同时安全与网络策略灵活性成为高频需求。

---

### 5. **Bug 与稳定性**

#### 严重 Bug 汇总（按优先级排序）
| Issue # | 问题描述 | 影响范围 | 是否已有 Fix PR |
|--------|----------|----------|------------------|
| [#84038](https://github.com/openclaw/openclaw/issues/84038) | `doctor --fix` 错误迁移配置导致 OAuth 失效 + Token 膨胀 | Auth / Data Loss | ❌ 无 |
| [#84059](https://github.com/openclaw/openclaw/issues/84059) | EmbeddedAttemptSessionTakeoverError 致所有嵌入运行失败 | Session State / Message Loss | ❌ 无 |
| [#67035](https://github.com/openclaw/openclaw/issues/67035) | Windows 聊天 UI 输入吞没、流回复不可见 | UI / Message Delivery | ⚠️ 关联 PR 待验证 |

> ⚠️ 多个 P1 级 Bug 集中在会话管理与 UI 渲染层，需紧急响应。部分问题（如 #67035）已有初步修复尝试，但尚未完成测试闭环。

---

### 6. **功能请求与路线图信号**

#### 高潜力 Feature Requests
| Issue # | 功能简述 | 社区支持度 | 关联 PR 进展 |
|--------|----------|------------|-------------|
| [#66944](https://github.com/openclaw/openclaw/issues/66944) | 插件 UI 扩展系统（原生 Control UI 页面注入） | 👍 8 | 无 |
| [#63829](https://github.com/openclaw/openclaw/issues/63829) | 每代理独立 memory-wiki vault 配置 | 👍 7 | 无 |
| [#39604](https://github.com/openclaw/openclaw/issues/39604) | Web Fetch 内网访问开关 | 👍 8 | 讨论中 |

> 📈 插件生态扩展（UI + 安全策略）和细粒度资源控制（成本预算、模型路由）是下一版本重点方向。

---

### 7. **用户反馈摘要**

- **正面反馈**：
  - 对 `/interrupt` 命令（#51163）表示欢迎，认为极大提升了交互体验。
  - 新版 Node.js 22 支持获得开发者认可，认为有助于生态统一。

- **负面反馈**：
  - 大量用户抱怨 Windows 版 UI 回归问题（#67035），称“完全无法正常使用”。
  - `doctor --fix` 自动修复引发意外破坏（#84038），用户希望增加确认机制或白名单。
  - Telegram/Mattermost 等平台消息静默丢弃（#80520, #68113）频发，信任度下降。

---

### 8. **待处理积压**

| Issue/PR # | 类型 | 停滞时长 | 风险提示 |
|-----------|------|----------|----------|
| [#75](https://github.com/openclaw/openclaw/issues/75) | Enhancement | 140+ days | 跨平台桌面应用缺失，影响非 Mac 用户采纳 |
| [#10687](https://github.com/openclaw/openclaw/issues/10687) | Enhancement | 90+ days | 动态模型发现（OpenRouter）长期未落地，落后于竞品 |
| [#8719](https://github.com/openclaw/openclaw/issues/8719) | Security RFC | 110+ days | 安全配置文件 v1.1 涉及架构级变更，需产品决策 |

> 🔔 建议维护者优先评估 #75（跨平台支持）与 #8719（安全模型），二者均为战略级需求。

--- 

*数据截止：2026-05-20 23:59 UTC*  
*分析师：AI 智能体与个人 AI 助手领域开源项目分析师*

---

## 横向生态对比

好的，作为专注于 AI 智能体与个人 AI 助手开源生态的资深技术分析师，我将根据您提供的各项目动态摘要，生成一份横向对比分析报告。

---

### **AI 智能体与个人 AI 助手开源生态横向对比分析报告 (2026-05-20)**

#### **1. 生态全景**

当前，个人 AI 助手/自主智能体开源生态正处于一个**高速迭代与分化并存**的阶段。一方面，核心项目如 OpenClaw、NanoBot、Zeroclaw 等展现出强劲的开发活力，围绕会话稳定性、多模态支持、安全增强及跨平台体验展开密集优化；另一方面，生态内部分化明显，从通用型框架（OpenClaw）到垂直领域工具链（IronClaw, LobsterAI），再到轻量级运行时（Moltis, ZeptoClaw），满足了不同层次开发者和用户的需求。社区普遍关注生产环境稳定性、细粒度资源控制以及更智能的 Agent 协作模式，预示着行业正从概念验证向实际应用落地加速迈进。

#### **2. 各项目活跃度对比**

| 项目名称     | Issues 数 | PR 数 | Release 情况         | 健康度评估 |
| :----------- | :-------- | :---- | :------------------- | :--------- |
| **OpenClaw** | 500       | 500   | v2026.5.19-beta.2 & alpha.1 | 极高活跃，高速迭代 |
| NanoBot      | 31        | 35    | 无                   | 高活跃，稳健推进 |
| Zeroclaw     | 7         | 45    | 无                   | 高活跃，重点重构 |
| PicoClaw     | 8         | 18    | Nightly Build v0.2.8-nightly.20260520.639b3270 | 中活跃，功能完善 |
| hermesagent  | 211       | 500   | 无                   | 极高活跃，快速修复 |
| NanoClaw     | 4         | 23    | 无                   | 高活跃，Bug 响应快 |
| IronClaw     | 24        | 50    | 无                   | 高活跃，架构演进 |
| LobsterAI    | 2         | 31    | 无                   | 高活跃，功能并行 |
| TinyClaw     | 0         | 0     | 无                   | 无活动 |
| Moltis       | 4         | 4     | 无                   | 中活跃，维护性优化 |
| QwenPaw      | 42        | 42    | v1.1.8 & v1.1.8-beta.2 | 极高活跃，版本发布频繁 |
| ZeptoClaw    | 2         | 2     | 无                   | 低活跃，CI/CD 维护 |
| EasyClaw     | 0         | 0     | 无                   | 无活动 |
| librefang    | 18        | 50    | 无                   | 高活跃，架构迁移 |
| openfang     | 2         | 3     | 无                   | 中活跃，集成深化 |
| AstrBot      | 23        | 17    | 无                   | 高活跃，插件生态 |

#### **3. OpenClaw 在生态中的定位**

*   **优势**: OpenClaw 无疑是生态中的**核心参照与领导者**。其庞大的 Issue/PR 处理量、高频的版本发布（Beta/Alpha）、以及对生产环境稳定性的高度关注，使其成为其他项目学习和借鉴的对象。它在会话管理、安全策略、多平台支持（尤其是非 Mac 平台）方面投入巨大，奠定了坚实的生态基础。
*   **技术路线差异**: OpenClaw 的技术路线更偏向于**大而全的通用框架**，强调广泛的兼容性和企业级特性（如安全配置文件 v1.1）。相比之下，NanoBot 更注重性能和多模态能力，Zeroclaw 聚焦于长期记忆与技能系统，IronClaw 则深耕 Reborn 模块和 WebUI 集成，体现出更细分的架构设计。
*   **社区规模对比**: OpenClaw 的社区规模远超其他项目，Issue 和 PR 数量均为最高，反映出其极高的知名度和用户基数。hermesagent 紧随其后，显示出强大的社区粘性。其他项目如 NanoBot、Zeroclaw、IronClaw 也拥有活跃的社区，但规模和影响力相对较小。

#### **4. 共同关注的技术方向**

*   **会话管理与稳定性**: 几乎所有项目都报告了会话相关的 Bug 或功能请求。OpenClaw (#67035, #84059)、NanoBot (#3790, #3884)、Zeroclaw (#6771)、PicoClaw (#2720)、hermesagent (#7233, #20470)、NanoClaw (#2561)、IronClaw (#3447)、LobsterAI (#1698)、librefang (#5195, #5111) 均涉及会话恢复、消息丢失、UI 渲染问题，表明这是当前生态的共性挑战。
*   **多模态与推理能力增强**: NanoBot (#3910, #3916)、PicoClaw (#2755, #2703)、QwenPaw (#4530, #4537)、openfang (#997) 等项目都在积极集成新的图像生成模型、视频支持或推理内容流，反映出对多模态交互能力的强烈需求。
*   **安全与权限控制**: OpenClaw (#84038, #8719)、Zeroclaw (#6293)、IronClaw (#3796)、librefang (#5285)、openfang (#1204) 等项目都在加强安全策略、权限隔离、OAuth 流程等方面的工作，以满足企业级部署的合规性和安全性要求。
*   **跨平台支持与兼容性**: OpenClaw (#75)、NanoBot (#3863)、PicoClaw (#2688)、hermesagent (#28989)、LobsterAI (#1698) 等项目都收到了关于 Windows/Linux 平台支持、特定渠道（微信、飞书）兼容性等反馈，凸显了跨平台一致性的重要性。
*   **Agent 协作与子任务委派**: QwenPaw (#4530)、AstrBot (#8152, #8181)、IronClaw (#3798) 等项目正在探索或已实现子代理（SubAgent）机制，支持 Agent 间的协作与任务委派，这是迈向复杂智能体系统的关键一步。

#### **5. 差异化定位分析**

| 项目名称     | 功能侧重                             | 目标用户                     | 技术架构关键差异                           |
| :----------- | :----------------------------------- | :--------------------------- | :----------------------------------------- |
| **OpenClaw** | 通用 AI 助手框架，企业级特性         | 开发者、企业用户             | 大而全，强调广泛兼容性与生产级稳定性     |
| **NanoBot**  | 高性能多模态 Agent，推理优化         | 开发者、AI 应用构建者        | 注重性能，快速冷启动，多提供商集成        |
| **Zeroclaw** | 长期记忆，技能系统，自主学习能力     | 高级用户、AI 研究者          | 强调“Dream Mode”与技能持久化               |
| **PicoClaw** | 轻量级，多模态，配置灵活             | 个人用户、小型团队           | 模块化，易于定制，强调流式处理能力        |
| **hermesagent**| 强大网关集成，跨平台，工具链丰富     | 开发者、系统集成商           | 强大的 OAuth 与多平台适配器                |
| **NanoClaw** | WhatsApp 深度集成，提及检测          | WhatsApp 重度用户            | 针对特定通讯渠道的深度优化                 |
| **IronClaw** | Reborn 模块，WebUI，企业级协作       | 企业用户、团队协作场景       | 基于 Rust，Reborn 为核心，WebUI v2 为重心  |
| **LobsterAI**| 多 Agent 编排，实时可观测，UI 优化   | 企业用户、复杂工作流管理者   | 多 Agent 协同，强调透明度和可视化         |
| **TinyClaw** | 无活动                               | -                            | -                                          |
| **Moltis**   | Docker 沙箱，WebSocket，轻量级运行时 | 容器化部署用户，轻量级场景   | 基于 Docker/Podman，sidecar 架构           |
| **QwenPaw**  | 桌面应用，插件生态，多模态           | 个人用户、桌面应用爱好者     | Tauri 桌面端，丰富的插件市场               |
| **ZeptoClaw**| CI/CD 自动化，依赖管理               | 内部开发者                   | 自动化工具链维护                           |
| **EasyClaw** | 无活动                               | -                            | -                                          |
| **librefang**| 通道适配器现代化，LLM 驱动优化       | 需要高度定制化通道的用户     | Sidecar 架构，通道迁移标准化               |
| **openfang** | MCP 桥接，工具集暴露，执行环境控制   | 需要与 Claude Code 集成的用户| MCP 桥接为核心，强调工具逻辑统一           |
| **AstrBot**  | 群聊互动，插件生态，虚拟伴侣         | 个人用户、QQ/微信群管理员    | 强调娱乐性、角色扮演与群聊上下文管理       |

#### **6. 社区热度与成熟度**

*   **快速迭代阶段**: OpenClaw、hermesagent、QwenPaw、NanoBot、IronClaw、LobsterAI 等项目处于**快速迭代阶段**，Issue/PR 数量庞大，功能更新频繁，Bug 修复迅速，社区讨论活跃。这些项目代表了当前生态中最前沿的发展方向。
*   **质量巩固阶段**: Moltis、ZeptoClaw、librefang 等项目则更侧重于**质量巩固和架构优化**，Issue 数量相对较少，PR 多为依赖升级、CI/CD 改进、架构迁移等，显示出项目已进入稳定期，重点在于提升代码质量和长期维护性。
*   **平稳发展/维护阶段**: PicoClaw、NanoClaw、openfang、AstrBot 等项目处于**平稳发展阶段**，既有新功能引入，也有 Bug 修复，社区活跃度适中，整体节奏稳健。

#### **7. 值得关注的趋势信号**

*   **从单体 Agent 向分布式、可观测 Agent 系统演进**: LobsterAI 的“多 Agent 编排与子任务实时可观测”、IronClaw 的“EventStreamManager 回放路径”、QwenPaw 的“spawn_subagent”等特性，表明开发者正在构建更复杂的智能体协作网络，而不仅仅是单个强大的 Agent。这对系统的可观测性、协调机制和容错能力提出了更高要求。
*   **对生产环境稳定性和安全性的极致追求**: 几乎所有项目都报告了与生产环境稳定性相关的 Bug（会话崩溃、UI 冻结、意外成本等），并持续加强安全策略、权限控制和沙箱隔离。这反映了 AI 智能体从实验走向实际部署时，对可靠性和安全性的迫切需求。
*   **多模态能力的深度融合与普及**: 从 NanoBot 的 StepFun 图像生成、PicoClaw 的视频媒体支持，到 QwenPaw 的宠物插件，多模态交互已成为标配。未来，如何高效、低成本地处理和理解多源数据将是核心竞争力。
*   **生态开放性与互操作性增强**: OpenClaw 的“干净的有界重构、显式插件 SDK/API 废弃路径”、IronClaw 的“热插拔能力目录发布机制”、openfang 的“MCP 桥接”等举措，都在积极构建更开放的生态系统，促进第三方工具和服务的集成，降低开发门槛。
*   **用户体验精细化与个性化**: AstrBot 的“你画我猜”游戏插件、QwenPaw 的“QwenPaw Pet”桌面宠物、NanoBot 的冷启动优化等，都体现了对终端用户体验的深入关注，从功能性转向情感化和趣味性，以提升用户粘性和满意度。

**对 AI 智能体开发者的参考价值**:
1.  **优先关注会话稳定性与错误恢复**: 在生产环境中，确保 Agent 的会话不丢失、能优雅降级和恢复是首要任务。
2.  **投资多模态处理能力**: 尽早集成图像、音频、视频等多模态输入输出，以提供更丰富的交互体验。
3.  **强化安全与权限模型**: 设计细粒度的权限控制和沙箱机制，防止恶意行为和数据泄露。
4.  **拥抱开放生态与标准**: 考虑使用或贡献于 MCP 等开放标准，以便与其他工具和平台无缝集成。
5.  **重视可观测性与调试工具**: 为 Agent 的行为提供清晰的日志、监控和调试接口，以便于排查问题和优化性能。
6.  **探索 Agent 协作模式**: 对于复杂任务，研究如何让多个 Agent 协同工作，分担职责，提升效率和准确性。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

**NanoBot 项目动态日报（2026-05-20）**

---

### 1. **今日速览**
过去24小时，NanoBot 社区活跃度较高，共处理 Issues 31 条、PRs 35 条，整体响应积极。核心功能持续优化，新增多模态支持与性能提升显著，同时修复了多个关键稳定性问题。无新版本发布，但开发节奏稳健，贡献者参与度良好。

---

### 2. **版本发布**
无新版本发布。

---

### 3. **项目进展**
今日合并/关闭的重要 PR 包括：
- **#3918**：网关冷启动时间从 ~4.6s 优化至 ~480ms，提升用户体验（[链接](https://github.com/HKUDS/nanobot/pull/3918)）
- **#3916 / #3917**：新增 Skywork 和 APIFree 提供商支持，扩展模型生态（[链接](https://github.com/HKUDS/nanobot/pull/3916), [链接](https://github.com/HKUDS/nanobot/pull/3917)）
- **#3910**：集成 StepFun 图像生成能力，支持 step-image-edit-2 等模型（[链接](https://github.com/HKUDS/nanobot/pull/3910)）
- **#3914**：重构图像生成模块为独立子包，提升可维护性（[链接](https://github.com/HKUDS/nanobot/pull/3914)）
- **#3919**：修复 shell 工具中 `restrictToWorkspace` 配置失效问题（[链接](https://github.com/HKUDS/nanobot/pull/3919)）

这些更新强化了多模态处理能力、降低系统延迟，并增强配置灵活性，推动项目向更稳定、易用方向演进。

---

### 4. **社区热点**
最活跃议题聚焦于 **WebUI 显示异常** 与 **会话管理缺陷**：
- **#3790**：WebUI 会话内容打印错乱，需刷新恢复（评论14，最新活跃）[链接](https://github.com/HKUDS/nanobot/issues/3790)
- **#193**：询问是否支持 Ollama API（评论14）[链接](https://github.com/HKUDS/nanobot/issues/193)
- **#3884**：WebUI 对话在首条回复后自动关闭（评论2，今日更新）[链接](https://github.com/HKUDS/nanobot/issues/3884)

反映用户对前端一致性与跨平台兼容性的高度关注，尤其在使用 DeepSeek 等推理模型时表现明显。

---

### 5. **Bug 与稳定性**
按严重程度排序的关键 Bug：
1. **#3790**：WebUI 会话内容渲染错乱（高，影响核心交互）— 暂无 fix PR
2. **#3884**：WebUI 对话首条回复后中断（高，阻断正常使用）— 暂无 fix PR
3. **#3907**：DeepSeek 推理模式下文本逐词换行显示（中，UI 体验差）— 已提交修复思路但未合并
4. **#3863**：微信登录因客户端版本过低失败（中，特定渠道问题）— 无有效解决方案

建议优先处理 WebUI 相关渲染问题，因其直接影响用户留存。

---

### 6. **功能请求与路线图信号**
高频需求集中于以下方向：
- **持久化记忆机制**（#3888）：引入 Mnemon 实现跨会话记忆 → 已有集成提案
- **Ollama 原生支持**（#193）：替代 vLLM 的本地部署方案 → 待评估
- **多智能体协同（Squad）**（#3913）：展示 Nanobot Legion 用例 → 正在推进集成
- **使用量追踪与洞察**（#3921）：添加 `/insights` 命令 → 新 PR 已提交

表明项目正从单体 Agent 向分布式、可观测、可持续运营方向演进。

---

### 7. **用户反馈摘要**
- **正面反馈**：对性能优化（如冷启动提速）表示认可；对新增提供商（Skywork、StepFun）持欢迎态度。
- **负面痛点**：
  - WebUI 在多模型（尤其是 DeepSeek）下表现不稳定；
  - 微信/Feishu 等通道存在兼容性问题；
  - 会话历史无限增长导致“静默崩溃”（#2638, #3029）；
  - MCP 工具更新后未自动刷新（#2325）。

用户普遍期望更健壮的内存管理与更好的跨平台一致性。

---

### 8. **待处理积压**
- **#2604**：提议将内存整理改为异步执行 → 创建于 2026-03-29，超30天未响应，涉及核心架构优化
- **#1123**：163 邮箱 IMAP 安全登录问题 → 创建于 2026-02-24，长期未解决，影响邮件通道可用性
- **#2463**：提示前缀不保留问题 → 虽已关闭，但可能遗留设计缺陷

建议维护者优先审查上述 Issue，避免技术债累积。

--- 

*数据来源：GitHub API · 统计周期：2026-05-19 00:00–2026-05-20 23:59 UTC*

</details>

<details>
<summary><strong>Zeroclaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

**Zeroclaw 项目动态日报（2026-05-20）**

---

### 1. **今日速览**  
过去24小时，Zeroclaw 社区活跃度显著提升：共处理 7 条 Issues（5 新开/活跃，2 已关闭）和 45 条 PR（42 待合并，3 已合并/关闭），无新版本发布。核心开发围绕 v0.8.0 集成分支推进，重点修复内存管理、安全策略及多通道 allowlist 统一化问题。整体项目健康度良好，但存在若干高优先级 Bug 需紧急响应。

---

### 2. **版本发布**  
无新版本发布。当前主力开发分支为 `integration/v0.8.0`，预计将作为 Beta 候选版本发布。

---

### 3. **项目进展**  
- **PR #6776 [CLOSED]**：修复了 Web UI 中 reload banner 未居中的显示问题，提升用户体验一致性。
- **PR #6777 [OPEN]**：修复了 `SqliteMemory::purge_namespace` 错误使用 `category` 列而非 `namespace` 的问题，直接影响内存模块稳定性，已提交至 master 分支。
- **PR #6398 [OPEN]**：v0.8.0 主干 PR，涵盖 Multi-Agent Runtime 与 Schema V3 升级，涉及 30+ 组件，是当前最大规模重构，已进入待合并阶段。

> ✅ 关键进展：内存清理逻辑 bug 已定位并修复，避免数据误删风险。

---

### 4. **社区热点**  
- **Issue #5849**（Dream Mode — Periodic Memory Consolidation & Reflective Learning）：虽仅 10 条评论，但属高优先级功能提案，获官方标记为 `status:accepted`，反映社区对 AI 自主学习能力的高度期待。
- **PR #6398**（v0.8.0 Multi-Agent Runtime & Schema V3）：尽管评论数未显，但被标注为“SEeking APPROVAL”，且关联大量依赖项更新，代表下一代架构演进方向。
- **Issue #6293**（Air-gapped execution mode with companion daemon）：提出隔离执行环境以增强安全性，目前状态为 `blocked`，等待维护者评审，体现用户对企业级安全部署的迫切需求。

> 🔥 热点分析：用户强烈关注长期记忆机制、离线安全运行及技能生态 UX 优化，技术路线正从单机向分布式、可审计方向演进。

---

### 5. **Bug 与稳定性**  
| 严重等级 | Issue / PR | 描述 | 状态 |
|--------|-----------|------|------|
| S1 | #6771（Bug: Multiline Heredocs blocked by SecurityPolicy） | 安全策略误拦截合法 HEREDOC 语法，导致技能无法创建 PR | 已报告，暂无 fix |
| S2 | #6801（Bug: purge_namespace deletes by category column） | 内存清理函数错误操作字段，可能导致数据丢失 | ✅ 已有 fix PR #6777 |

> ⚠️ 注意：S1 级安全策略误判问题可能阻碍用户工作流，建议优先处理。

---

### 6. **功能请求与路线图信号**  
- **Dream Mode（#5849）**：被标记为 `priority:p1` 且 `status:accepted`，表明该项目已进入开发规划，预计纳入未来正式版。
- **ACP Session Restore（#6543）**：虽已关闭，但原问题指出缺失会话恢复能力，暗示协议兼容性将成为 v0.8.x 重点。
- **Skills UX Tracker（#6253）**：明确指向 v0.7.6 技能体系体验优化，覆盖 CLI、沙箱、测试工具链，反映技能作者生态建设加速。

> 📌 信号解读：项目正强化“智能体自主性”与“开发者友好性”双主线，长期记忆与技能系统为下一阶段核心。

---

### 7. **用户反馈摘要**  
- **痛点**：  
  - Homebrew 安装后配置路径解析错误（#6639），影响 macOS 用户部署体验。  
  - 多行 HEREDOC 被安全策略误杀（#6771），暴露策略规则过于宽泛。  
- **满意点**：  
  - 社区对 Dream Mode 概念表示高度兴趣，认为其“赋予 AI 自我反思能力”。  
  - 技能持久化改进（如 WeChat context_tokens 保存）获得积极反馈。  

> 💬 真实声音：用户渴望更智能、更安全、更易用的本地 AI 代理，尤其重视隐私保护与技能扩展自由度。

---

### 8. **待处理积压**  
- **Issue #6293**（Air-gapped execution mode）：自 5 月 3 日提出，状态为 `needs-maintainer-review`，涉及高安全风险架构变更，需维护者尽快响应。  
- **PR #6398**（v0.8.0 主干）：虽已开放评审，但缺乏实质性评论，可能面临合并延迟，建议主动邀请核心贡献者参与审查。

> ⏳ 提醒：两项均为高影响力任务，若长期停滞可能影响版本发布节奏。

--- 

*数据来源：GitHub.com/zeroclaw-labs/zeroclaw | 生成时间：2026-05-20*

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

好的，作为 PicoClaw 项目的分析师，以下是根据您提供的数据生成的项目动态日报。

---

### **PicoClaw 项目动态日报 (2026-05-20)**

**1. 今日速览**

PicoClaw 项目在今日保持了较高的活跃度，共处理了8个 Issue 和 18 个 Pull Request。社区贡献者积极提交代码修复和新功能，同时维护者也及时响应并关闭了多个问题。项目整体进展顺利，重点集中在提升稳定性、增强多模态支持以及优化用户体验上。

**2. 版本发布**

*   **Nightly Build v0.2.8-nightly.20260520.639b3270**
    *   **更新内容:** 这是一个自动构建的夜间版本，包含了最新的代码变更。
    *   **破坏性变更:** 无明确说明。
    *   **迁移注意事项:** 此版本为不稳定版本，建议谨慎使用。用户可参考 [Full Changelog](https://github.com/sipeed/picoclaw/compare/v0.2.8...main) 了解具体变更。

**3. 项目进展**

今日合并/关闭的重要 PR 主要聚焦于以下方面：

*   **增强多模态与推理能力:**
    *   `#2755` (已合并): 为 OpenAI 兼容层添加了 `reasoning_content` 流支持和视频媒体支持，主要服务于 Xiaomi Mimo 提供商的集成。
    *   `#2740` (已合并): 修复了 DeepSeek 流式响应中 `reasoning_content` 被丢弃的问题，提升了思考模式下的兼容性。
    *   `#2703` (已合并): 增加了对 Intel OpenVINO Model Server 的支持，为用户提供了本地 LLM 推理的新选择。
*   **改进会话管理:**
    *   `#2491` (已合并): 添加了 `/status`, `/compact`, `/new` 等会话管理命令，增强了用户对会话上下文的手动控制能力。
    *   `#2788` (开放): 为会话 API 中的消息添加了 `created_at` 时间戳，提高了前端展示的时间准确性。
*   **提升配置与可靠性:**
    *   `#2771` (已关闭): 提出了增强 PicoClaw 配置可靠性和迁移体验的建议，旨在改善配置文件的易用性。
*   **修复关键 Bug:**
    *   `#2688` (已关闭): 修复了 `find /` 命令可以枚举工作区外路径的安全漏洞，加强了沙箱隔离。
    *   `#2753` (已关闭): 解决了从源码构建后 `picoclaw-launcher` 文件缺失的问题，完善了构建流程。
*   **优化性能与功能:**
    *   `#2781` (开放): 优化了技能目录的 token 使用，避免在每个 LLM 请求中重复发送，提升了效率。
    *   `#2892` (已合并): 实现了基于配置的提供者流式传输，并引入了双重 opt-in 模型，增强了流式处理能力。

**4. 社区热点**

*   **Issue #2674 (Codex OAuth 空响应):** 该 Issue 报告了在特定条件下（ChatGPT 后端流式传输）使用 Codex OAuth 时出现空助手响应的问题，并收到了 4 个赞。这表明开发者对特定提供商集成的健壮性有较高期望。[链接](https://github.com/sipeed/picoclaw/issues/2674)
*   **PR #2813 (PID 身份验证):** 针对 Issue #2720 提出的解决方案，旨在防止因 PID 重用导致的崩溃循环。虽然标记为 stale，但其重要性不容忽视。[链接](https://github.com/sipeed/picoclaw/pull/2813)

**5. Bug 与稳定性**

*   **高优先级:**
    *   **#2720 (Singleton PID 检查):** 网关启动时若 PID 文件包含已被无关进程重用的 PID，会导致崩溃循环。这是一个关键的稳定性问题，已有 PR #2813 提出修复方案。[链接](https://github.com/sipeed/picoclaw/issues/2720)
*   **中优先级:**
    *   **#2674 (Codex OAuth 空响应):** 在使用特定提供商时出现空响应，影响功能可用性。[链接](https://github.com/sipeed/picoclaw/issues/2674)
    *   **#2688 (find / 路径枚举):** 安全漏洞，允许枚举文件系统路径，存在潜在风险。[链接](https://github.com/sipeed/picoclaw/issues/2688)
*   **低优先级:**
    *   **#1757 (每小时任务频道错误):** 定时任务执行时出现频道错误，影响自动化流程。[链接](https://github.com/sipeed/picoclaw/issues/1757)

**6. 功能请求与路线图信号**

*   **异步结果传递策略 (#2829):** 用户提出需要显式的异步工具结果传递策略，以避免不必要的父代理轮次。已有 PR #2830 正在实现此功能。[链接](https://github.com/sipeed/picoclaw/issues/2829)
*   **增强配置可靠性 (#2771):** 用户反馈配置文件示例过时，希望改善配置迁移体验。这暗示了未来版本中可能需要更清晰的配置文档和迁移工具。[链接](https://github.com/sipeed/picoclaw/issues/2771)
*   **无限上下文与跨会话记忆 (#2774):** 受外部插件启发，提议实现缓存感知的无限上下文、跨会话内存和历史压缩功能，以支持 Agent 的持续工作能力。[链接](https://github.com/sipeed/picoclaw/issues/2774)

**7. 用户反馈摘要**

*   **痛点:** 用户在使用不同提供商（如 ChatGPT 后端）时遇到兼容性问题（#2674），以及在构建和部署过程中遇到文件缺失问题（#2753）。
*   **使用场景:** 用户利用 PicoClaw 进行定时任务调度（#1757）、多模态交互（#2755, #2703）以及复杂的会话管理（#2491, #2788）。
*   **满意点:** 对新增的会话管理命令（#2491）和性能优化（#2781）表示认可。
*   **不满意点:** 对配置文件示例过时（#2771）和某些 Bug 的存在表示困扰。

**8. 待处理积压**

*   **Issue #2720 (Singleton PID 检查):** 尽管已有 PR #2813 提出修复方案，但该 Issue 本身仍标记为 stale，需要维护者确认并推动合并。[链接](https://github.com/sipeed/picoclaw/issues/2720)
*   **Issue #2674 (Codex OAuth 空响应):** 该 Issue 已活跃一段时间，需要进一步调查和修复。[链接](https://github.com/sipeed/picoclaw/issues/2674)
*   **PR #2813 (PID 身份验证):** 虽然提出了修复方案，但标记为 stale，需要维护者审查并决定是否合并。[链接](https://github.com/sipeed/picoclaw/pull/2813)
*   **PR #2830 (异步结果传递策略):** 该 PR 旨在解决一个重要的功能请求，但目前标记为 stale，需要维护者关注。[链接](https://github.com/sipeed/picoclaw/pull/2830)

</details>

<details>
<summary><strong>hermesagent</strong> — <a href="https://github.com/NousResearch/hermes-agent">NousResearch/hermes-agent</a></summary>

**hermesagent 项目动态日报（2026-05-20）**

---

### 1. **今日速览**  
过去24小时，hermesagent 社区活跃度显著提升：Issues 更新达 211 条（新开/活跃 156），PR 更新 500 条（待合并 369），显示开发节奏加快。无新版本发布，但多个关键 Bug 修复和平台适配持续推进。整体项目处于高活跃迭代期，用户反馈集中集中在网关集成、跨平台兼容性及工具链稳定性方面。

---

### 2. **版本发布**  
*无新版本发布*

---

### 3. **项目进展**  
今日共关闭 131 个 PR，合并若干重要修复：
- **#26093**: 修复了 OAuth 凭证刷新死循环问题（P1），防止因持续 401 错误导致无限重试，提升认证鲁棒性。
- **#27700**: 确保插件发现机制在 Web 工具调用前触发，解决了新安装插件未被识别的问题（P2）。
- **#25347**: 修复了 Gemini 模型并行 tool call 参数拼接错误问题，恢复多工具调用语义完整性（P2）。
- **#24474**: 将 `--skills` 标志正确传递至 ACP 会话，支持技能预加载功能回归（P2）。

此外，多个 Windows 路径解析、TUI 输入防抖、LSP 安全加固等低风险改进已合并，增强跨平台体验与安全性。

---

### 4. **社区热点**  
以下 Issue 评论活跃，反映核心诉求：
- **#4505**: Ollama 原生 `/api/chat` 端点优化提案获 12 条评论，用户希望提升流式响应效率与兼容性（👍2）。
- **#19986**: 建议将非核心技能设为可选安装，减少默认包体积与维护负担（👍3），体现用户对轻量化部署的强烈需求。
- **#9549**: Feishu 表格渲染失败问题持续讨论，涉及 Markdown 转换逻辑缺失（👍5），凸显多平台富文本支持短板。
- **#28056**: 提出为 cron/agent 任务添加“运行中质量门控”与有界重试机制（评论 5），反映生产环境对可靠性的高要求。

这些议题均指向 **平台集成深度优化** 与 **用户体验精细化** 两大方向。

---

### 5. **Bug 与稳定性**  
按严重程度排序的关键 Bug：
- **[P1] #27370**: `conversation_loop.py` 中 `_pool_may_recover_from_rate_limit` 未定义，导致速率限制恢复逻辑崩溃（已关闭，推测由 PR 修复）。
- **[P1] #7233**: Telegram 会话恢复后内部推理块泄露至聊天界面，暴露提示工程缺陷（活跃中，暂无 fix PR）。
- **[P1] #8965**: Ollama Cloud 模型通过代理时 tool call 以 XML 文本输出而非执行，影响自动化流程（活跃中）。
- **[P2] #18482**: Docker 容器内无法创建 home 目录，权限问题阻碍自定义配置（活跃中）。
- **[P2] #20470**: Telegram DM topic 绑定未在会话压缩后更新，引发消息路由死循环（活跃中，已有开发者关注）。

> 注：部分 P1 Bug 可能已被后续 PR 隐式修复，需验证状态。

---

### 6. **功能请求与路线图信号**  
用户明确提出的功能需求包括：
- **Per-user memory isolation in group chats** (#11430)：防止身份混淆，强化隐私保护。
- **Turn-level live time context** (#10421)：提升时间感知准确性，适用于日程管理等场景。
- **TokenTelemetry Plugin for Dashboard** (#26696)：实现跨 Agent 的 token 使用聚合监控。
- **Per-channel profile routing for Discord** (#19809)：单 bot 支持多人格，降低运维成本。

结合近期 PR（如 #29058 引入信念管道反幻觉机制），可预见下一版本将加强 **智能体自治能力** 与 **可观测性**。

---

### 7. **用户反馈摘要**  
- **痛点集中点**：  
  - 文件读写格式污染（#19798）：`read_file` 返回带行号的文本导致 `write_file` 写入异常。
  - Windows 路径不支持（#28989）：媒体提取仅识别 Unix 路径，跨平台体验割裂。
  - 插件生命周期管理混乱（#28661）：会话自动清理导致成就插件计数回滚。
- **满意点**：  
  - 快速响应安全漏洞（#23778 已关闭）；
  - 对 Python <3.10 兼容性问题的修复及时（#21798 获 👍1）。

---

### 8. **待处理积压**  
以下 Issue 长期未获响应，需维护者优先介入：
- **#4505** (Ollama 优化)：自 2026-04-01 提出，12 条评论，涉及核心性能优化，建议评估可行性。
- **#11430** (群聊记忆隔离)：自 04-17 提出，5 条评论，属高价值隐私功能，建议纳入 roadmap。
- **#19986** (技能模块化)：自 05-05 提出，6 条评论，影响安装与维护体验，建议拆分技能包结构。

---

*数据来源：GitHub API @ NousResearch/hermes-agent | 报告时间：2026-05-20*

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

**NanoClaw 项目动态日报（2026-05-20）**

---

### 1. **今日速览**
NanoClaw 在 2026-05-20 保持高度活跃的开发节奏，过去 24 小时内处理了 23 个 PR 更新与 4 个 Issue 闭环，显示出团队对关键问题响应迅速。核心进展集中在 WhatsApp 通道的提及检测修复、权限作用域收紧以及多消息批处理逻辑优化上。整体项目健康度良好，无新版本发布，但多个高优先级 Bug 已获修复或进入合并流程。

---

### 2. **版本发布**
无新版本发布。

---

### 3. **项目进展**
- **PR #2565**（[链接](https://github.com/nanocoai/nanoclaw/pull/2565)）：由 @glifocat 提交的 WhatsApp 群组 @-mention 检测修复已关闭，解决了 Issue #2560 中 `isMention` 硬编码为 `undefined` 的问题，确保路由系统能正确识别并处理提及事件，支持文档化的频道审批 onboarding 流程。
- **PR #2143**（[链接](https://github.com/nanocoai/nanoclaw/pull/2143)）：添加管理员取消命令功能，增强对活跃代理运行的控制能力，已于今日完成合并。
- **PR #2497**（[链接](https://github.com/nanocoai/nanoclaw/pull/2497)）：“Agent Network”特性开发持续推进，本周仍处于开放状态，预计将引入跨代理协作机制。

这些进展显著提升了通道集成可靠性与用户操作安全性。

---

### 4. **社区热点**
当前无评论量突出的 Issue 或 PR。最新 Issue #2550（[链接](https://github.com/nanocoai/nanoclaw/issues/2550)）提出“两级项目上下文加载”需求，反映用户对多项目并行时内存效率的关注；相关讨论虽未展开，但已有 PR #2567 尝试解决 CLAUDE.local.md 自动加载缺失问题，显示社区对本地记忆隔离有强烈诉求。

---

### 5. **Bug 与稳定性**
| 严重程度 | Issue / PR | 描述 | 状态 |
|----------|-----------|------|------|
| High     | #2560     | WhatsApp 群组中 @-mention 未被识别为 `isMention`，导致事件被路由丢弃 | ✅ 已关闭，由 PR #2565 修复 |
| Medium   | #2561     | 上下文压缩后代理无输出，陷入无限重试循环 | ⚠️ 未关闭，暂无公开修复 PR |
| Medium   | #2555     | 多消息批处理触发 Claude Agent SDK 返回合成响应而非调用 API | 🔧 正在修复中，PR #2556 已提交 |

其中 #2561 和 #2555 仍影响部分用户场景，建议优先审查相关 PR 合并进度。

---

### 6. **功能请求与路线图信号**
- **Issue #2550** 提议实现“轻量级索引 + 按需加载 STATUS 文件”的两级项目上下文机制，旨在解决多项目环境下大体积 `.md` 文件性能瓶颈。该需求与现有 PR #2567（导入 CLAUDE.local.md）形成互补，表明项目正探索更智能的记忆管理策略。
- **PR #2497**（Agent Network）持续开发中，暗示未来可能支持分布式代理协同工作流，属于中长期架构演进方向。

---

### 7. **用户反馈摘要**
- **痛点**：用户在多项目环境中抱怨当前全量加载模式导致启动延迟与资源占用过高（#2550）；另有开发者指出 WhatsApp 提及渲染失败严重影响交互体验（#2552, #2560）。
- **满意点**：对快速响应 Bug 修复表示认可，如 #2560 在一天内即获解决方案。
- **使用场景**：典型场景包括远程团队协作（WhatsApp 群组）、个人知识管理（CLAUDE.md 组织）及多任务并行开发（项目上下文切换）。

---

### 8. **待处理积压**
- **Issue #2561**：“代理在上下文压缩后无输出”问题自 5 月 19 日报告至今未关闭，且无对应 PR 公开，需维护者介入评估是否需紧急处理。
- **PR #2497**（Agent Network）：创建于 5 月 15 日，已停滞近一周，建议跟进进度以避免阻塞后续功能集成。

--- 

*数据来源：GitHub NanoClaw 仓库（https://github.com/qwibitai/nanoclaw）*

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

**IronClaw 项目动态日报（2026-05-20）**

---

### 1. **今日速览**  
过去24小时内，IronClaw 保持高度活跃状态：共处理 24 条 Issue 更新（新开/活跃 18 条）和 50 条 PR 更新（待合并 25 条），无新版本发布。项目整体处于快速迭代阶段，重点推进 Reborn 模块的功能落地与 WebUI Beta 路径完善。社区讨论集中于身份权限、工具能力扩展及稳定性优化，技术债清理与架构边界审计同步推进。

---

### 2. **版本发布**  
无新版本发布。

> 注：尽管存在 #3708 的 `ironclaw_common` 0.5.0 和 `ironclaw` 0.28.2 发布 PR，但截至统计时仍未合并，且该 PR 标记为“chore: release”，可能为自动化流程触发但未完成审核。

---

### 3. **项目进展**  
本周期内 **6 个 PR 被关闭**，主要集中在 Reborn 集成测试、扩展生命周期管理和 CLI 清理。其中最具里程碑意义的是：

- **#3797**（已关闭）：将 REPL 工具调用路由至生产级适配器，实现从实验性 REPL 向真实 Reborn AgentLoop 的过渡，标志着 REPL 路径正式进入可维护生产通道。
- **#3792**（已关闭）：将 REPL 的 LLM 认证逻辑迁移至 composition 层，解耦 CLI 与运行时依赖，提升配置灵活性与安全性。
- **#3790**（已关闭）：新增热插拔能力目录发布机制，支持扩展包动态注册能力，为 Notion MCP / GitHub WASM 等第三方工具接入奠定基础。

此外，WebUI v2 路由层（#3747）持续集成中，预计将在近期完成端到端 beta 路径打通。

---

### 4. **社区热点**  
最活跃的议题为 **#3259**（Publish 0.25.0–0.27.0 to crates.io），自 5 月 5 日提出以来持续更新至今日，反映下游用户因 crates.io 未同步最新版本而被锁定在 0.24.0，影响对 wasmtime 28.x CVE 的修复使用。此问题虽非紧急漏洞，但暴露了发布流程脱节，需尽快协调发布策略。

其次，**#3798**（Subagent Spawn for Reborn agent loop）作为新设计提案，提出分阶段实现子智能体 spawn 机制，引发对多智能体协作架构的关注。

PR 方面，**#3747**（WebUI v2 routes with RebornServicesApi）获得最多关注，其目标是构建基于 axum 的稳定 HTTP 接口层，支撑前端直接调用 Reborn 核心服务，被视为产品化关键一步。

---

### 5. **Bug 与稳定性**  
发现一个持续性 E2E 失败问题：**#3447**（Nightly E2E failed），自 5 月 10 日起每日夜间构建均告失败，涉及 Full E2E 和 v2-engine 任务。当前尚无修复 PR，建议排查测试环境或资源竞争问题。

另有一个 UI 配置缺陷：**#3771**（v0.28.2: Improve Configure UI for non-API-key providers and AWS Bedrock），指出 Gemini CLI 等非 API-key 模型无法通过图形界面正确配置，影响用户体验，暂无对应 fix PR。

---

### 6. **功能请求与路线图信号**  
多个 Issue 明确指向下一阶段开发方向：

- **租户级项目 ACL 与分组权限**（#3796）：提出将 project 建模为第一类权限实体，支持跨用户共享，预示即将推出企业级协作功能。
- **Notion MCP / GitHub WASM 能力路径**（#3805, #3806）：作为首批外部工具集成试点，表明平台正加速开放生态建设。
- **EventStreamManager 回放路径完成**（#3809）：强调 durable timeline/replay 对产品级事件流的重要性，关联 WebUI 实时进度展示。

结合现有 Lane 计划（#3800–#3809），可见 Reborn 模块正按“REPL → 扩展能力 → 安全/权限 → 事件流”顺序稳步推进。

---

### 7. **用户反馈摘要**  
- **痛点**：crates.io 版本滞后导致依赖管理混乱（#3259）；非 API-key 模型配置缺失（#3771）；E2E 测试不稳定影响信任度（#3447）。
- **期待**：稳定、可扩展的多租户权限体系；支持主流办公工具（如 Notion、GitHub）的原生集成；更健壮的本地开发体验（REPL 生产对齐）。
- **满意度**：开发者赞赏架构解耦与 facade 设计（如 #3612 评论），认为提升了模块独立性；但对文档完整性存疑（#3773 提及 crate 边界模糊）。

---

### 8. **待处理积压**  
- **#3259**（Publish 0.25.0–0.27.0 to crates.io）：超两周未解决，影响下游生态，需优先处理。
- **#3447**（Nightly E2E failed）：长期未修复，可能掩盖深层测试环境问题，需专人介入。
- **#3773**（Crate boundary & ownership audit）：虽为新开，但涉及 47 个 crate 的治理，属战略级技术债，建议纳入本周 roadmap。

--- 

*数据来源：[https://github.com/nearai/ironclaw](https://github.com/nearai/ironclaw)*

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

LobsterAI 项目在 2026-05-20 保持高度活跃的开发节奏，过去24小时内产生了31条 Pull Request 更新（26条待合并，5条已合并/关闭），同时有2条新的 Issue 被提出。项目整体进展顺利，多个重要功能模块正在并行开发中，社区参与度较高。

### 2. 版本发布
无新版本发布。

### 3. 项目进展
今日合并/关闭的重要 PR 包括：
*   **PR #2013 (CLOSED):** `fix: context window slider snap-to-preset and K/M text input` (作者: @btc69m979y-dotcom) - 此 PR 修复了上下文窗口滑块吸附预设点和文本输入框支持 K/M 简写的问题，提升了用户体验。
*   **PR #2014 (CLOSED):** `fix: weixin qr gaateway restart` (作者: @fisherdaddy) - 修复了微信二维码网关重启的问题。
*   **PR #2012 (CLOSED):** `Feat/2026.5.18 artifacts` (作者: @liugang519) - 此 PR 引入了新的功能或修复，具体细节未完全提供。
*   **PR #2011 (CLOSED):** `feat: subagent session sidebar display and detail view` (作者: @btc69m979y-dotcom) - 此 PR 实现了子代理会话的侧边栏显示和详情视图，增强了多 Agent 编排的可观测性。
*   **PR #680 (CLOSED):** `feat(cowork): 多 Agent 编排与子任务实时可观测` (作者: @Aoxiang-001) - 此 PR 将 OpenClaw 的多 Agent 编排从"黑箱"变为完全透明可观测的体验，用户可以配置 Agent Router 自动向 Worker Agent 派发子任务，并实时展示子任务进度。

这些 PR 的合并表明项目在用户界面优化、核心功能增强以及多 Agent 协作体验方面取得了实质性进展。

### 4. 社区热点
今日讨论最活跃的 Issues/PRs 是：
*   **Issue #1698 [OPEN]:** `有道龙虾启动状态下，安装智企帝王蟹必现gateway端口冲突和进程竞争` (作者: @yy987y) - 此 Issue 报告了一个严重的 Bug，即在特定环境下安装智企帝王蟹会导致 gateway 端口冲突和进程竞争，影响软件正常运行。
*   **Issue #2016 [OPEN]:** `建议增加openhuman引擎功能` (作者: @qxjysd) - 这是一个功能请求，用户希望增加对 openhuman 引擎的支持。
*   **PR #2015 [OPEN]:** `fix: handle openclaw compaction retries and tool result gaps` (作者: @fisherdaddy) - 此 PR 旨在修复 OpenClaw 压缩重试和工具结果间隙的问题，虽然评论数未明确，但其标题表明它可能解决了社区关注的一个关键问题。

### 5. Bug 与稳定性
今日报告的 Bug 按严重程度排列如下：
*   **高严重性:** Issue #1698 报告了“gateway端口冲突和进程竞争”问题，这是一个严重的稳定性问题，导致智企帝王蟹无法正常工作。目前尚无公开的 fix PR 针对此 Issue。
*   **其他 Bug:** 其他 PR 如 #2015 和 #2014 也涉及修复特定功能或错误，但 Issue #1698 是最突出的 Bug。

### 6. 功能请求与路线图信号
今日的功能请求主要集中在：
*   **Issue #2016:** 建议增加 openhuman 引擎功能。这表明社区对扩展支持的 AI 引擎有需求。
*   **PR #1628, #1629, #1631, #1634, #1636, #1637, #1639, #1640, #1641, #1642, #1660, #1661, #1663, #1667:** 这些 PR 涵盖了 UI 优化、用户头像设置、MCP 支持、全局搜索、聊天窗口交互、国际化、工具执行结果复制、右键菜单、日志脱敏、OpenClaw 升级等多个方面的功能增强和改进。这些 PR 表明项目路线图正朝着提升用户体验、增强功能性和系统稳定性方向发展。

### 7. 用户反馈摘要
从 Issues 评论中提炼的真实用户痛点包括：
*   **Issue #1698:** 用户遇到了严重的安装和运行时问题，影响了正常使用，表达了对稳定性的担忧。
*   **Issue #2016:** 用户提出了对新功能（openhuman 引擎）的需求，显示出对更多 AI 模型支持的期望。

### 8. 待处理积压
长期未响应的重要 Issue 或 PR 包括：
*   **Issue #1698:** 自 2026-04-15 创建以来，截至 2026-05-20 仍未关闭，且状态为 OPEN，表明该问题尚未得到解决。
*   **PR #1628, #1629, #1631, #1634, #1636, #1637, #1639, #1640, #1641, #1642, #1660, #1661, #1663, #1667:** 这些 PR 的状态均为 STALE，表明它们已经有一段时间没有更新了，可能需要维护者的关注和审查。

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
过去24小时内，Moltis 项目保持中等活跃度：共处理 4 条 Issue 更新（2 新开/活跃，2 已关闭）和 4 条 PR 更新（2 待合并，2 已合并/关闭），无新版本发布。社区对 Docker 沙箱稳定性及 WebSocket 连接问题持续关注，核心维护者 @penso 主导修复了多个关键问题。整体项目运行平稳，技术债清理持续推进。

---

### 2. **版本发布**  
无新版本发布。

---

### 3. **项目进展**  
今日合并/关闭的重要 PR 包括：

- **[PR #1025](https://github.com/moltis-org/moltis/pull/1025)**（CLOSED）：修复 Docker 沙箱僵尸进程问题，通过启用 `--init` 参数确保子进程被正确回收，提升容器资源管理可靠性。
- **[PR #1023](https://github.com/moltis-org/moltis/pull/1023)**（CLOSED）：优化 WebSocket 超时处理逻辑，避免将 RPC 超时误判为“WebSocket disconnected”，增强用户体验与调试能力。
- **[PR #1026](https://github.com/moltis-org/moltis/pull/1026)**（OPEN）：强化 vault 密码同步机制，实现 auth 与 vault 密码变更的原子性操作，防止配置不一致导致的安全风险。

这些改进显著提升了系统稳定性与安全性，尤其在多后端（Docker/Podman）环境下表现突出。

---

### 4. **社区热点**  
今日最活跃的议题集中在 **#1022** 和 **#1024**，均于昨日创建且无评论，但反映近期用户高频遇到的技术痛点：

- **[Issue #1022](https://github.com/moltis-org/moltis/issues/1022)**：用户在 LLM 模式切换时频繁遭遇“WebSocket disconnected”错误，影响交互连续性。该问题尚无公开解决方案，可能涉及前端重连机制或后端状态同步缺陷。
- **[Issue #1024](https://github.com/moltis-org/moltis/issues/1024)**：指出 `[hooks]` 配置段虽被解析验证，但未在运行时注册，导致自定义钩子失效。此问题直接影响插件扩展能力，属功能性阻塞。

两者均未关联已有 fix PR，需优先响应以维持用户信任。

---

### 5. **Bug 与稳定性**  
按严重程度排序的新增 Bug：

1. **高优先级**：[#1022] WebSocket 断连导致 LLM 模式更新中断（无 fix PR）  
2. **中优先级**：[#1024] hooks 配置未注册（无 fix PR）  

此前报告的 Docker + sandbox 问题（[#423]）已闭环，表明团队对容器化部署问题响应迅速。当前 backlog 中暂无高危崩溃类 Bug。

---

### 6. **功能请求与路线图信号**  
- **[Issue #850](https://github.com/moltis-org/moltis/issues/850)** 提议在 MCP 服务器 OAuth 配置中支持 `client_secret`，虽已关闭，但结合近期安全加固趋势（如 vault 密码同步），推测 OAuth 灵活性将成为下一版本重点。
- **[PR #1005](https://github.com/moltis-org/moltis/pull/1005)** 引入 OpenAI Codex 的 `reasoning_effort` 支持，并保留加密推理内容兼容性，显示项目正加强 AI 模型集成深度，符合行业向高级推理能力演进的方向。

---

### 7. **用户反馈摘要**  
从 Issue 描述中提取的关键反馈：

- **痛点**：Docker 沙箱资源泄漏、WebSocket 超时误报、hooks 配置“静默失效”。
- **使用场景**：企业级多租户部署依赖稳定容器隔离；开发者期望自定义钩子可靠生效；用户重视 OAuth 流程的细粒度控制。
- **满意度**：对已修复的 Docker 问题（[#423]）给予正面评价（👍5）；对新功能如 reasoning effort 表示期待。

---

### 8. **待处理积压**  
- **[Issue #1022]** & **[Issue #1024]**：均为高关注度 Bug，创建不足24小时即进入 backlog，建议列入本周优先级清单。
- **[PR #1026]**：虽已提交，但尚未合并，涉及 vault 安全逻辑变更，需代码审查与回归测试确认。

> 📌 **建议行动项**：  
> - 指派开发者跟进 #1022 与 #1024 的根本原因分析；  
> - 加速 #1026 的合并流程以确保 vault 一致性；  
> - 监控 #1005 是否引发 Codex 实例克隆时的副作用。

--- 

*数据来源：GitHub API / moltis-org/moltis | 生成时间：2026-05-20*

</details>

<details>
<summary><strong>QwenPaw</strong> — <a href="https://github.com/agentscope-ai/QwenPaw">agentscope-ai/QwenPaw</a></summary>

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，我将根据您提供的 GitHub 数据，生成 QwenPaw 项目在 2026-05-20 的动态日报。

---

### **QwenPaw 项目动态日报 (2026-05-20)**

**1. 今日速览**
过去24小时，QwenPaw 项目保持了高度活跃的社区互动和开发节奏。共处理了42条 Issues 更新和42条 PR 更新，并发布了两个新版本（v1.1.8 及 v1.1.8-beta.2），显示出团队在快速迭代和功能完善方面的强劲势头。整体活跃度评估为“极高”，项目正处于一个功能丰富且用户反馈积极的阶段。

**2. 版本发布**
*   **v1.1.8 & v1.1.8-beta.2:**
    *   **新增功能：**
        *   **官方插件分发系统：** 用户现在可以通过网站浏览和下载官方插件，或在控制台的插件管理器中一键安装，极大提升了插件获取和管理的便捷性 ([#4482](https://github.com/agentscope-ai/QwenPaw/pull/4482))。
        *   **QwenPaw Pet 宠物插件：** 引入了一个桌面宠物伴侣插件，为用户提供了更有趣的交互体验。
    *   **性能优化：**
        *   对控制台模型进行了性能优化。
        *   优化了 trace 模块的批处理机制，通过批量追加 inbox trace 事件来减少文件 I/O 操作，提升系统响应速度。
    *   **破坏性变更与迁移注意事项：** 本次更新主要为功能增强和性能优化，未提及重大破坏性变更。但根据历史版本升级说明，若使用桌面端应用（Windows .exe 或 macOS .zip），通常需要卸载并重新安装以应用最新更改。

**3. 项目进展**
*   **重要合并/关闭 PR：**
    *   **#4536 (feat(provider): add OpenCode Go into opencode via meta.base_url_options)：** 成功将 OpenCode Go 模型集成到 OpenCode 提供商中，通过 `meta.base_url_options` 进行端点切换，统一了模型管理，为用户提供了更多免费模型选择。
    *   **#4534 (docs(install): add backup dir) & #4531 (chore(version): update release note of v1.1.8)：** 完成了 v1.1.8 版本的发布文档更新，确保了发布信息的准确性和完整性。
    *   **#4523 (fix(runner): persist /mission and /skill info responses to session me...)：** 修复了 `/mission` 和技能命令的响应在会话重载后消失的问题，提升了用户体验的连贯性。
    *   **#4527 (Introduce QWENPAW_AUTO_INITIALIZATION in deploy/entrypoint.sh)：** 引入了环境变量来控制自动初始化，增强了部署的灵活性，特别是在容器化环境中。
    *   **#4529 (fix(model): hotfix for model setting)：** 针对模型设置问题进行了热修复，提升了系统的稳定性。
    *   **#4526 (feat(provider_manager): add new free models to opencode list)：** 向 OpenCode 列表添加了新的免费模型，丰富了用户的选择。
    *   **#4533 (supplement qwenpaw pet zh descriptions to website for language switch)：** 补充了 QwenPaw Pet 插件的中文描述，支持了多语言切换，体现了对国际化用户体验的关注。
    *   **#4549 (feat(provider): disable URL freeze in OpenCode provider configuration) & #4548 (chore(version): bump patch version to 1.1.8.post1)：** 针对特定 API 配置进行了调整，并更新了补丁版本号。
    *   **#4545 (refactor(console): plugin)：** 重构了插件页面，采用 Tab 切换布局，并改进了插件列表样式、标签国际化及过滤功能，显著提升了插件管理界面的可用性和美观度。
    *   **#4547 (feat(agent): add task_timeout support for background task submissions)：** 为后台任务提交增加了超时支持，提升了系统的健壮性。
    *   **#4520 (feat(console): persist chat input draft across page navigation)：** 实现了聊天输入框草稿的持久化，用户在切换页面时不会丢失正在输入的内容，这是一个非常实用的用户体验优化。
    *   **#4532 (feat(mcp): add OAuth 2.1 authorization flow for remote MCP servers)：** 为远程 MCP 服务器添加了完整的 OAuth 2.1 认证流程，支持 PKCE + DCR，增强了安全性和功能性。
    *   **#4537 (feat(feishu): support group session shared mode)：** 为飞书渠道添加了群组会话共享模式，允许群组成员共享同一会话上下文，解决了之前群组隔离的问题。
    *   **#4530 (feat(subagent): support spawn a (fork) subagent)：** 引入了 `spawn_subagent` 内置工具，使代理能够在自己的工作区内委派子任务，填补了单一会话与调用独立代理之间的功能空白。
    *   **#4464 (feat(e2e): migrate python_e2e into CoPaw with mock infrastructure)：** 将完整的 E2E 测试套件迁移到 CoPaw，并建立了模拟 API 基础设施，为 UI 冒烟测试提供了基础，提升了项目的测试覆盖率和自动化水平。
    *   **#4267 (feat(security): Mac OS file path white list)：** 引入了基于白名单的文件保护机制，结合 macOS `sandbox-exec` 沙箱保护，增强了工具执行的安全性。
    *   **#4518 (feat(skill): Add skill-market, refactor skill hub to httpx)：** 添加了一个统一的技能市场，并重构了技能中心客户端以使用异步 `httpx`，提升了技能搜索和安装的效率和并发能力。
    *   **#3813 (feat: add tauri 2.x desktop app support)：** 增加了对 Tauri 2.x 桌面应用的支持，将现有控制台前端包装在 Tauri webview 中，并以本地进程运行 Python FastAPI 后端，为桌面应用提供了现代化的技术栈支持。
    *   **#4544 (CLOSED: 偶发性飞书发过来的提示词没有在console端显示)：** 修复了飞书渠道偶发性提示词不显示的问题。
    *   **#4542 (CLOSED: 模型连接测试因 max_tokens=1 在部分 API 上失败)：** 修复了模型连接测试因 `max_tokens` 硬编码为 1 而在部分 API 上失败的问题。
    *   **#4512 (CLOSED: tool_result created on init but never used)：** 修复了初始化创建 `tool_result` 文件夹但未被使用的问题。
    *   **#4449 (CLOSED: Model 429 Rate-Limit → zero-downtime reload 永久清空消息队列，Agent 表现"冻结")：** 修复了模型遭遇限流后导致 Agent "冻结"的问题。
    *   **#4485 (CLOSED: 插件工具写入 agent.json 后未被注入 Agent 的 Toolkit)：** 修复了插件工具写入 `agent.json` 后未被注入 Agent 的 Toolkit 的问题。
    *   **#4494 (CLOSED: Console stream stalls mid-generation with misleading "you interrupted me" message)：** 修复了控制台流式输出中途停滞并显示误导信息的问题。
    *   **#4499 (CLOSED: 插件市场预计什么时间发布呢？有计划实现类似codex的宠物系统吗？)：** 已确认插件市场和宠物系统功能已发布。
    *   **#4515 (CLOSED: 429之后卡死其他所有模型调用)：** 修复了 429 错误后导致其他模型调用卡死的问题。
    *   **#2660 (CLOSED: AGENT_ERROR: Task has been cancelled!)：** 修复了任务被取消的错误。
    *   **#3001 (CLOSED: 支持飞书 CardKit 流式输出)：** 已支持飞书 CardKit 流式输出。
    *   **#4174 (CLOSED: If we use an API format like OpenAI, the agent's thoughts aren't collapsed into "thinking.")：** 修复了 OpenAI API 格式下代理思考内容未折叠的问题。
    *   **#4090 (CLOSED: Error messages from the model during the dialogue)：** 增强了对话中模型错误信息的展示。
    *   **#2983 (CLOSED: Line breaks in Markdown tables don't work in the web client.)：** 修复了 Markdown 表格中行内换行符 `<br>` 不生效的问题。
    *   **#3528 (CLOSED: 使用 <br> 时 Markdown 表格自动换行)：** 同样修复了 Markdown 表格中使用 `<br>` 换行的问题。
    *   **#4470 (CLOSED: The plugin interface has an unauthorized remote code execution (RCE) vulnerability)：** 修复了插件接口存在 RCE 漏洞的问题。
    *   **#4430 (CLOSED: 升级 1.1.6 → 1.1.7 是否会丢失之前的配置？)：** 澄清了升级过程中的配置保留情况。
    *   **#4441 (CLOSED: 什么时候模型配置能一键配置opencode go)：** 已支持一键配置 OpenCode Go。
    *   **#4497 (CLOSED: Line breaks in Markdown tables don't work.)：** 再次修复了 Markdown 表格换行问题。
    *   **#3570 (CLOSED: Can the "All Chats" list in the upper right be given pagination functionality?)：** 已添加 "All Chats" 列表的分页功能。
    *   **#4496 (OPEN: 升级到 1.1.7 后，AGENTS.md 加载问题)：** 一个关键 Bug，升级到 1.1.7 后，系统提示词中加载的 AGENTS.md 是内置默认模板，而非工作区中的实际文件内容。
    *   **#4535 (OPEN: /backups returns HTTP 403 when accessed from localhost)：** 访问备份页面时出现 HTTP 403 错误。
    *   **#4543 (OPEN: api调用对话首次流式信息不全)：** API 调用对话首次流式信息返回不全。
    *   **#4541 (OPEN: 启用 Pet 插件后，发送第一条消息会导致主程序闪退)：** 启用 QwenPaw Pet 插件后，发送第一条消息会导致主程序崩溃闪退，这是一个严重的稳定性问题。
    *   **#4539 (OPEN: 免费多模态路由需求)：** 用户强烈希望实现自动多模态路由，无需手动切换模型。
    *   **#4491 (OPEN: Should newly created sub-agents inherit global MCP/ACP config?)：** 关于新子代理是否继承全局配置的讨论。
    *   **#4463 (OPEN: Improve context token estimation with cached prompt usage)：** 建议通过缓存提示词使用情况来改进上下文 token 估算。
    *   **#4454 (OPEN: /mission command causes Console to freeze completely)：** 执行 `/mission` 指令后，控制台界面会完全卡死。
    *   **#4481 (OPEN: 从系统级解决 Windows GBK 编码问题)：** 提出系统性解决 Windows GBK 编码问题的方案。
    *   **#4514 (OPEN: Add Source Tracing / Citation functionality to conversation outputs)：** 建议在对话输出中添加来源追踪/引用功能。
    *   **#4518 (OPEN: feat(skill): Add skill-market, refactor skill hub to httpx)：** 技能市场的开发正在进行中。
    *   **#3813 (OPEN: feat: add tauri 2.x desktop app support)：** Tauri 2.x 桌面应用支持的开发正在进行中。
    *   **#4267 (OPEN: feat(security): Mac OS file path white list)：** macOS 文件路径白名单安全功能的开发正在进行中。
    *   **#4545 (OPEN: refactor(console): plugin)：** 插件页面的重构正在进行中。
    *   **#4520 (OPEN: feat(console): persist chat input draft across page navigation)：** 聊天输入草稿持久化的开发正在进行中。
    *   **#4532 (OPEN: feat(mcp): add OAuth 2.1 authorization flow for remote MCP servers)：** 远程 MCP 服务器 OAuth 2.1 授权流程的开发正在进行中。
    *   **#4537 (OPEN: feat(feishu): support group session shared mode)：** 飞书群组会话共享模式的开发正在进行中。
    *   **#4530 (OPEN: feat (subagent): support spawn a (fork) subagent)：** 子代理支持的开发正在进行中。
    *   **#4464 (OPEN: feat(e2e): migrate python_e2e into CoPaw with mock infrastructure)：** E2E 测试迁移的开发正在进行中。
    *   **#4547 (OPEN: feat(agent): add task_timeout support for background task submissions)：** 后台任务超时的开发正在进行中。
    *   **#4549 (OPEN: feat(provider): disable URL freeze in OpenCode provider configuration)：** OpenCode 提供商的 URL 冻结禁用开发正在进行中。
    *   **#4548 (OPEN: chore(version): bump patch version to 1.1.8.post1)：** 版本号更新的开发正在进行中。
    *   **#4545 (OPEN: refactor(console): plugin)：** 插件页面的重构正在进行中。
    *   **#4520 (OPEN: feat(console): persist chat input draft across page navigation)：** 聊天输入草稿持久化的开发正在进行中。
    *   **#4532 (OPEN: feat(mcp): add OAuth 2.1 authorization flow for remote MCP servers)：** 远程 MCP 服务器 OAuth 2.1 授权流程的开发正在进行中。
    *   **#4537 (OPEN: feat(feishu): support group session shared mode)：** 飞书群组会话共享模式的开发正在进行中。
    *   **#4530 (OPEN: feat (subagent): support spawn a (fork) subagent)：** 子代理支持的开发正在进行中。
    *   **#4464 (OPEN: feat(e2e): migrate python_e2e into CoPaw with mock infrastructure)：** E2E 测试迁移的开发正在进行中。
    *   **#4547 (OPEN: feat(agent): add task_timeout support for background task submissions)：** 后台任务超时的开发正在进行中。
    *   **#4549 (OPEN: feat(provider): disable URL freeze in OpenCode provider configuration)：** OpenCode 提供商的 URL 冻结禁用开发正在进行中。
    *   **#4548 (OPEN: chore(version): bump patch version to 1.1.8.post1)：** 版本号更新的开发正在进行中。
    *   **#4545 (OPEN: refactor(console): plugin)：** 插件页面的重构正在进行中。
    *   **#4520 (OPEN: feat(console): persist chat input draft across page navigation)：** 聊天输入草稿持久化的开发正在进行中。
    *   **#4532 (OPEN: feat(mcp): add OAuth 2.1 authorization flow for remote MCP servers)：** 远程 MCP 服务器 OAuth 2.1 授权流程的开发正在进行中。
    *   **#4537 (OPEN: feat(feishu): support group session shared mode)：** 飞书群组会话共享模式的开发正在进行中。
    *   **#4530 (OPEN: feat (subagent): support spawn a (fork) subagent)：** 子代理支持的开发正在进行中。
    *   **#4464 (OPEN: feat(e2e): migrate python_e2e into CoPaw with mock infrastructure)：** E2E 测试迁移的开发正在进行中。
    *   **#4547 (OPEN: feat(agent): add task_timeout support for background task submissions)：** 后台任务超时的开发正在进行中。
    *   **#4549 (OPEN: feat(provider): disable URL freeze in OpenCode provider configuration)：** OpenCode 提供商的 URL 冻结禁用开发正在进行中。
    *   **#4548 (OPEN: chore(version): bump patch version to 1.1.8.post1)：** 版本号更新的开发正在进行中。
    *   **#4545 (OPEN: refactor(console): plugin)：** 插件页面的重构正在进行中。
    *   **#4520 (OPEN: feat(console): persist chat input draft across page navigation)：** 聊天输入草稿持久化的开发正在进行中。
    *   **#4532 (OPEN: feat(mcp): add OAuth 2.1 authorization flow for remote MCP servers)：** 远程 MCP 服务器 OAuth 2.1 授权流程的开发正在进行中。
    *   **#4537 (OPEN: feat(feishu): support group session shared mode)：** 飞书群组会话共享模式的开发正在进行中。
    *   **#4530 (OPEN: feat (subagent): support spawn a (fork) subagent)：** 子代理支持的开发正在进行中。
    *   **#4464 (OPEN: feat(e2e): migrate python_e2e into CoPaw with mock infrastructure)：** E2E 测试迁移的开发正在进行中。

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

**ZeptoClaw 项目动态日报（2026-05-20）**

---

### 1. **今日速览**  
过去24小时内，ZeptoClaw 项目整体处于低活跃状态。共处理2个依赖更新相关的 Pull Request：一个已完成合并，另一个仍处于待合并状态。无新 Issue 产生或关闭，亦无新版本发布。项目当前重点聚焦于 CI/CD 工具链的维护性升级，未涉及核心功能迭代。整体健康度稳定，但社区互动与用户反馈暂无显著波动。

---

### 2. **版本发布**  
无新版本发布。

---

### 3. **项目进展**  
- **PR #586 已合并**：自动化升级 GitHub Actions 中的 `taiki-e/install-action` 至 v2.75.29，提升构建环境一致性与安全性。该变更属于非功能性维护任务，不影响运行时行为。  
- **PR #591 待合并**：进一步将同一依赖升级至 v2.77.3，涵盖更多工具链支持与安全修复。此 PR 由 Dependabot 自动生成，预计将在近期合并以对齐最新最佳实践。

> 链接：[PR #586](https://github.com/qhkm/zeptoclaw/pull/586) | [PR #591](https://github.com/qhkm/zeptoclaw/pull/591)

---

### 4. **社区热点**  
当前无活跃讨论议题。所有 PR 均由机器人自动发起，无人工评论或互动记录，表明社区对日常维护类变更关注度较低。短期内未见重大争议点或高热度需求浮出水面。

---

### 5. **Bug 与稳定性**  
未报告任何 Bug、崩溃或回归问题。项目运行稳定性良好，依赖项更新未引入已知风险。

---

### 6. **功能请求与路线图信号**  
暂无公开的功能请求 Issue。现有 PR 均为自动化依赖升级，未体现新功能开发意图。结合近期活动模式判断，下一阶段可能仍以基础设施优化为主，而非产品功能扩展。

---

### 7. **用户反馈摘要**  
无用户主动提交的 Issue 或评论，无法提取有效反馈。推测当前用户群体可能集中于开发者内部使用，或对现有功能满意度较高，暂未触发显式反馈机制。

---

### 8. **待处理积压**  
- **PR #591**：虽为自动化生成，但仍需人工审核是否接受其建议的版本跳跃（从 2.75.x 到 2.77.x）。建议维护者尽快完成审查与合并，以保持 CI 环境时效性。  
- 长期 Issue 积压情况未知，因过去24小时无新 Issue 产生，且历史 Issue 列表未提供。建议定期检视 Issue 面板以识别潜在阻塞项。

--- 

*数据来源：GitHub API / ZeptoClaw Repository (https://github.com/qhkm/zeptoclaw)*

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
过去24小时，librefang 项目活跃度较高，共处理 Issue 18条、PR 50条，整体开发节奏稳健。核心进展集中在通道适配器迁移至 sidecar 架构、LLM 驱动优化及内存隔离增强。CI 稳定性面临挑战，3个主要 PR 触发流水线失败，需关注安全扫描与质量门禁问题。

---

### 2. **版本发布**
无新版本发布。

---

### 3. **项目进展**
今日合并/关闭的重要 PR 包括：
- **#5300**：修复 main 分支 CI 回归问题，涵盖 `cargo fmt` 格式漂移、MCP `caller_agent_id` 语义修正及 OpenAPI 基线对齐，恢复主干稳定性。
- **#5298 / #5297**：完成 Rocket.Chat 与 Twitch 通道从内嵌 Rust 适配器向 Python sidecar 的迁移，延续“七连迁”模式，提升可维护性与扩展性。
- **#5295**：为 `SidecarChannelConfig` 补全 `default_agent` 字段，解决 inbound 路由因缺失默认 agent 导致的非确定性分发问题（#5294）。
- **#5285**：确保 wa-gateway 所有 REST 转发携带 kernel Bearer token，避免 401 静默失败，提升 API 安全性。
- **#5254**：修复调度表单中 Cron 选择器误关闭弹窗的问题（#5247），改善用户体验。

这些变更推进了通道架构现代化、配置一致性与 API 可靠性，项目正向更健壮、易扩展的方向演进。

---

### 4. **社区热点**
- **#5299**（Discord sidecar 迁移）：虽评论数未显，但属高影响力破坏性变更，标志通道适配标准化进程加速。
- **#5195**（Telegram 消息注入错误会话）：用户反馈关键场景下消息上下文错乱，影响多轮对话体验，引发对 session 隔离机制的深入讨论。
- **#5275**（提议添加 Codex 运行时）：首次明确提出支持 OpenAI Codex CLI 作为新 runtime，反映用户对轻量级工具链执行环境的需求增长。

> 链接：[#5299](https://github.com/librefang/librefang/pull/5299) | [#5195](https://github.com/librefang/librefang/issues/5195) | [#5275](https://github.com/librefang/librefang/issues/5275)

---

### 5. **Bug 与稳定性**
按严重程度排序：
1. **#5296**（CI failure on PR #5260）：Quality 检查失败，涉及 credential pools 功能，阻塞关键特性合并。
2. **#5290**（Moonshot OCR 误判图片为文档）：图像内容被错误路由至文本提取端点，返回 400 错误，影响视觉理解能力。已有 fix PR #5291。
3. **#5293**（配置页子标签响应式异常）：UI 布局在窄屏下失效，属前端体验问题，暂无 PR。
4. **#5111**（Telegram 桥接网络断连后不重试）：服务僵死需手动重启，属高优先级稳定性缺陷，长期存在。

> 链接：[#5296](https://github.com/librefang/librefang/issues/5296) | [#5290](https://github.com/librefang/librefang/issues/5290) | [#5293](https://github.com/librefang/librefang/issues/5293) | [#5111](https://github.com/librefang/librefang/issues/5111)

---

### 6. **功能请求与路线图信号**
- **Codex 运行时支持**（#5275）：用户明确要求集成 OpenAI Codex CLI 作为可选 runtime，暗示未来可能扩展非 LLM-native 执行环境。
- **MCP 细粒度权限控制**（#5259）：提出按 agent 限制特定 MCP server 的工具访问，呼应企业级多租户需求，与 #5071（per-agent memory isolation）形成协同。
- **credential pools 多密钥轮换**（#4965 已合入）：表明项目正强化生产级密钥管理与容错能力，为高可用部署铺路。

这些请求均与现有 PR 方向一致，预计将逐步纳入后续版本规划。

---

### 7. **用户反馈摘要**
- **痛点集中点**：
  - Telegram 文件+文本分属不同会话（#5195），暴露 session 绑定逻辑缺陷；
  - WhatsApp 语音合成格式错配（#5283），导致接收方无法播放；
  - Dashboard 配置页 UI 响应式问题（#5293），影响移动端操作。
- **满意之处**：
  - Sidecar 迁移显著降低通道代码耦合度，开发者赞赏架构清晰化；
  - Cron 选择器修复（#5254）获即时响应，体现社区协作高效。

---

### 8. **待处理积压**
- **#5111**（Telegram 桥接无自动重连）：自 5月16日提出，至今未闭环，属关键稳定性问题，建议优先安排修复。
- **#5293**（配置页子标签消失）：UI 问题持续存在，影响配置流程，需前端团队介入。
- **#5287**（history_fold 缺少 ResponseFormat::Json）：影响 DeepSeek 等严格输出模型的历史压缩准确性，关联 #4922 预算系统，建议纳入近期迭代。

> 链接：[#5111](https://github.com/librefang/librefang/issues/5111) | [#5293](https://github.com/librefang/librefang/issues/5293) | [#5287](https://github.com/librefang/librefang/issues/5287)

--- 

*数据来源：[librefang GitHub 仓库](https://github.com/librefang/librefang)*

</details>

<details>
<summary><strong>openfang</strong> — <a href="https://github.com/RightNow-AI/openfang">RightNow-AI/openfang</a></summary>

**OpenFang 项目动态日报（2026-05-20）**

---

### 1. **今日速览**  
过去24小时，openfang 项目保持中等活跃度，共新增2个 Issue 和3个 PR。核心焦点集中在 **MCP 桥接工具层重构** 与 **样本代理配置引发的意外成本问题修复**。无新版本发布，但社区对执行环境限制和功能扩展性提出明确诉求。整体进展稳健，技术债清理持续推进。

---

### 2. **版本发布**  
无新版本发布。

---

### 3. **项目进展**  
- **PR #1205**: 将 OpenFang 完整工具集（文件、内存、代理、Shell、Web、Patch）通过 MCP 桥接暴露给 Claude Code 子进程，实现工具逻辑统一。此为“Stage 9 hardening”关键步骤，显著提升外部集成一致性。[链接](https://github.com/RightNow-AI/openfang/pull/1205)  
- **PR #1207**: 直接响应 Issue #1206，禁用三个示例代理配置中的活跃调度策略，避免 v0.6.9 自动加载机制触发后产生非预期 LLM 调用成本。[链接](https://github.com/RightNow-AI/openfang/pull/1207)  
- **PR #997**（持续更新）: 引入原生 Gemini 嵌入模型驱动，支持 API 密钥自动检测与 Google/Gemini 模型兼容，增强多模态能力基础。[链接](https://github.com/RightNow-AI/openfang/pull/997)

> ✅ 三项 PR 均聚焦于 **稳定性加固** 与 **生态集成深化**，尤其 MCP 桥接推进标志着 OpenFang 正从内部工具向协作平台演进。

---

### 4. **社区热点**  
- **Issue #1204**：用户 @OsAlex 质疑 `shell_exec` 执行时间硬编码为 120 秒（单命令上限 30 秒），认为该限制阻碍复杂任务执行，且无法在运行时调整。此反馈反映用户对灵活性的强烈需求。[链接](https://github.com/RightNow-AI/openfang/issues/1204)  
- **Issue #1206** 虽仅1条评论，但引发快速响应（次日即出修复 PR），凸显自动代理加载机制变更带来的用户体验冲击，体现社区对透明性与向后兼容性的重视。[链接](https://github.com/RightNow-AI/openfang/issues/1206)

> 🔥 热点集中于 **执行环境可控性** 与 **默认行为可预测性**，提示未来版本需加强配置文档与升级指引。

---

### 5. **Bug 与稳定性**  
- **高优先级 Bug**: Issue #1206 揭示 v0.6.9 因未预见的自动代理加载导致样本代理持续调用 LLM，造成意外计费。已提交 PR #1207 修复，**待合并**。  
- **中优先级风险**: PR #997 仍在审查中，涉及新嵌入驱动的安全性与兼容性验证，可能影响生产部署稳定性。

> ⚠️ 当前无崩溃类严重故障，但存在 **资源滥用型逻辑缺陷**，需警惕类似回归。

---

### 6. **功能请求与路线图信号**  
- **延长 shell_exec 超时限制**（Issue #1204）：用户明确要求突破 120 秒全局上限，暗示未来可能提供 **分级超时策略** 或 **管理员覆盖机制**。  
- **动态调度开关**（隐含于 Issue #1206）：建议允许用户选择性启用/禁用代理自动加载，而非全有或全无。  
- **Gemini 嵌入支持**（PR #997）：表明项目正积极拓展多厂商 AI 服务集成，强化跨平台能力。

> 📌 结合现有 PR，下一版本可能优先解决 **执行控制粒度** 与 **第三方模型接入** 两大方向。

---

### 7. **用户反馈摘要**  
- **痛点**:  
  - “自动加载代理本意是便利，却导致每小时数十次 LLM 调用，账单激增。”（#1206）  
  - “我需要运行一个需要 45 秒的脚本，但 shell_exec 直接失败，毫无提示。”（#1204）  
- **满意点**:  
  - 社区对问题响应迅速，尤其 #1206 当日即出修复方案，体现开发团队责任感。  
  - Gemini 嵌入支持获开发者欢迎，视为生态扩展利好。

---

### 8. **待处理积压**  
- **PR #997**（创建于 2026-04-06，已超 40 天未合并）：引入 Gemini 嵌入驱动，涉及 API 安全、模型映射及测试覆盖，长期挂起可能延缓多模态功能落地。建议本周内安排代码评审。[链接](https://github.com/RightNow-AI/openfang/pull/997)  
- **Issue #1204** 虽无评论，但属高频使用场景的关键限制，若长期不开放配置选项，可能引发更多同类请求。

--- 

*数据来源：GitHub API | 报告生成时间：2026-05-20*

</details>

<details>
<summary><strong>AstrBot</strong> — <a href="https://github.com/AstrBotDevs/AstrBot">AstrBotDevs/AstrBot</a></summary>

**AstrBot 项目动态日报（2026-05-20）**

---

### 1. **今日速览**  
过去24小时 AstrBot 社区活跃度较高，共处理 Issue 23 条、PR 17 条，新增多个插件提交与功能优化。核心模块持续迭代，尤其在群聊上下文模式、子代理增强及多模态支持方面进展显著。整体项目处于稳定开发节奏中，无重大版本发布。

---

### 2. **版本发布**  
无新版本发布。

---

### 3. **项目进展**  

#### ✅ 合并/关闭的重要 PR：
- **#8237**：修复 Telegram 适配器中回复消息 sender_id 匹配问题，确保 `/` 唤醒前缀在群组内正确触发（[链接](https://github.com/AstrBotDevs/AstrBot/pull/8237)）。
- **#8235**：修正 FAQ 文档中删除字段数量错误（五处误写为六处）（[链接](https://github.com/AstrBotDevs/AstrBot/pull/8235)）。
- **#7509**（已合并）：解决 vLLM Embedding 模型因强制传入维度参数导致的兼容性问题，提升 bge-m3 等模型部署稳定性（[链接](https://github.com/AstrBotDevs/AstrBot/pull/7509)）。

#### 🔧 关键功能推进：
- **群聊消息流上下文模式（flow mode）** 进入开发阶段（PR #8243），支持按消息流增量加载上下文，适配长上下文 LLM，默认保持滑动窗口兼容性。
- **SubAgent 功能增强**（PR #8152）持续推进，支持静态配置与动态通信链路输出，强化多角色协作能力。
- **Metaso 搜索后端集成**（PR #8241）完成接入，提供免费 Web 搜索 API 支持，降低用户使用门槛。

---

### 4. **社区热点**  

#### 🔥 高互动 Issue / PR：
- **[你画我猜游戏插件上线](https://github.com/AstrBotDevs/AstrBot/issues/8254)**：新娱乐插件“你画我猜”提交审核，支持 LLM 出题、手机白板作画、积分排行等功能，获 9 条评论，反映用户对轻量化群聊互动功能的强烈需求。
- **[米游社资讯搬运插件重复提交](https://github.com/AstrBotDevs/AstrBot/issues/8249)**：同一插件多次提交，开发者 @galaxy-b612 强调其自动轮询米游社 API 的实时性与稳定性，体现二次元用户群体对垂直内容服务的期待。
- **[静默调用 SubAgent 模式建议](https://github.com/AstrBotDevs/AstrBot/issues/8181)**：用户 @NekoTumble 提出 SubAgent 应支持“静默调用”以避免角色切换打断沉浸感，该诉求与虚拟伴侣、猫娘等应用场景高度契合，可能影响未来 SubAgent 设计方向。

---

### 5. **Bug 与稳定性**  

| 严重程度 | Issue 编号 | 问题描述 | 是否已有 Fix |
|--------|-----------|--------|------------|
| P0     | [#8223](https://github.com/AstrBotDevs/AstrBot/issues/8223) | 僵尸进程导致单实例重复监听消息，触发双回复 | ✅ 待处理 |
| P1     | [#8242](https://github.com/AstrBotDevs/AstrBot/issues/8242) | 图片转述时错误调用对话模型，致配置失效 | ❌ 无 |
| P1     | [#8251](https://github.com/AstrBotDevs/AstrBot/issues/8251) | 知识库文件删除后仍可被检索 | ❌ 无 |
| P0     | [#8238](https://github.com/AstrBotDevs/AstrBot/issues/8238) | `skills_like` 模式下用户消息与历史记录不一致 | ✅ PR #8240 已修复 |

> **说明**：P0 为阻塞性故障，P1 为重要功能异常。

---

### 6. **功能请求与路线图信号**  

- **静默 SubAgent 调用**（Issue #8181）：用户明确要求避免子代理直接回复用户，建议返回主代理内部处理，此需求在角色扮演类应用中具高优先级，结合 PR #8152 进展，预计纳入 v4.24+ 规划。
- **群聊增强功能扩展**（Issue #8247）：用户提议在平台配置中增加群聊管理增强选项（如消息过滤、权限分级），并主动表示愿提交 PR，显示社区参与度高。
- **EULA 首次提示机制**（PR #7955）：已在启动流程中加入法律条款提醒，反映项目方对用户合规意识的重视，可能推动后续隐私政策完善。

---

### 7. **用户反馈摘要**  

- **正面反馈**：
  - 米游社插件被赞“自动抓取及时准确，节省手动查公告时间”（@galaxy-b612）。
  - 你画我猜插件获称“适合 QQ 群活跃气氛，交互流畅”。
- **负面痛点**：
  - 多模态模型混用导致图片消息处理混乱，用户抱怨“发图就报错，根本没法聊天”（@lililiilyz）。
  - 内置指令缺失（如 `/t2i`）引发困惑，日志提示不准确，影响新手体验（@lingyun14beta）。
  - 配置文件 schema 缺少类型校验，开发者调试困难（@pizeroLOL）。

---

### 8. **待处理积压**  

- **Issue #8223（僵尸进程）**：自 5 月 18 日报告，尚未分配负责人，需排查进程生命周期管理机制。
- **PR #8152（SubAgent 增强）**：创建于 5 月 11 日，仍在审查中，涉及复杂逻辑变更，需进一步测试。
- **Issue #8181（静默调用）**：虽未关闭，但无对应 PR 跟进，属长期待实现功能，建议评估优先级。

---

**数据概览**：  
- Issues 更新：23 条（新开/活跃: 11，已关闭: 12）  
- PR 更新：17 条（待合并: 14，已合并/关闭: 3）  
- Releases：无  

> 本报告基于 GitHub 公开数据生成，覆盖截至 2026-05-20 24:00 UTC。

</details>

---
*本日报由 [Big Model Radar](https://github.com/ivanweng2077/big_model_radar) 自动生成。*