# OpenClaw 生态日报 2026-05-28

> Issues: 373 | PRs: 500 | 覆盖项目: 15 个 | 生成时间: 2026-05-28 02:37 UTC

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

# OpenClaw 项目日报（2026-05-28）

---

## **1. 今日速览**
OpenClaw 今日整体活跃度极高，过去 24 小时共更新 **373 条 Issues**（新开/活跃 178 条，已关闭 195 条），**500 条 PR**（待合并 259 条，已合并/关闭 241 条）。  
两个新版本发布（`v2026.5.26`、`v2026.5.26-beta.2`），主要优化 Gateway 启动性能与回复可见性，并修复内存泄漏、会话状态同步等关键问题。  
社区反馈集中在 **会话消息丢失、工具链阻塞、模型切换异常**，多个高优先级 Bug 已有 PR 跟进。

---

## **2. 版本发布**
### **v2026.5.26**
- **核心改进**：
  - **Gateway 启动优化**：避免重复扫描插件、频道、会话、计费警告、文件系统，减少缓存负载下运行时/会话缓存抖动。
  - **回复可见性分离**：用户可见回复与后台工作解耦，提升响应速度。
  - **内存泄漏修复**：Feishu 监控状态清理不完整（[#48183](https://github.com/openclaw/openclaw/issues/48183)）、Codex OAuth 回退失败（[#86820](https://github.com/openclaw/openclaw/issues/86820)）。
- **破坏性变更**：无重大 API 变更，但需关注 Telegram 插件状态硬上限（1000 行）可能影响旧配置迁移。
- **迁移建议**：升级后运行 `openclaw doctor --fix` 修复会话路由与插件状态。

---

## **3. 项目进展**
| PR 链接 | 类型 | 关键修复/功能 |
|--------|------|--------------|
| [#87458](https://github.com/openclaw/openclaw/pull/87458) | 性能优化 | 去重持久化技能提示，减少磁盘占用 |
| [#87476](https://github.com/openclaw/openclaw/pull/87476) | 会话路由修复 | 外部会话上下文优先，解决 Feishu `sessions_send` 路由问题 |
| [#87481](https://github.com/openclaw/openclaw/pull/87481) | 网关客户端修复 | 广播 `stream:thinking` 事件到 WebSocket 客户端 |
| [#87463](https://github.com/openclaw/openclaw/pull/87463) | 会话持久化 | 统一 `openai-codex` 为 `openai` 会话路由 |

**总结**：今日推进了 **会话路由稳定性、模型切换、插件状态管理** 等核心问题，修复了多个高优先级回归 Bug，项目在会话隔离与资源管理方面显著改善。

---

## **4. 社区热点**
### **最活跃 Issues/PR**
#### **Bug 与崩溃**
- **Native Hook Relay 不可用**（[#87395](https://github.com/openclaw/openclaw/issues/87395)）：Telegram 插件状态硬上限导致写入失败（[#87357](https://github.com/openclaw/openclaw/issues/87357)），已有 PR 修复（[#87481](https://github.com/openclaw/openclaw/pull/87481)）。
- **消息丢失**：Discord 心跳驱动回复阻塞后续心跳（[#83184](https://github.com/openclaw/openclaw/issues/83184)）、Matrix 线程会话键大小写冲突（[#75670](https://github.com/openclaw/openclaw/issues/75670)）。
- **模型切换异常**：Claude 推理默认开启（[#73182](https://github.com/openclaw/openclaw/issues/73182)）、Ollama 代理 SSRF 防御失效（[#81249](https://github.com/openclaw/openclaw/issues/81249)）。

#### **功能请求**
- **Gateway-lite 模式**（[#86881](https://github.com/openclaw/openclaw/issues/86881)）：无需 AI 模型的轻量部署方案，已有 PR 设计中。
- **任务流生命周期钩子**（[#87362](https://github.com/openclaw/openclaw/issues/87362)）：插件可观测性增强。

---

## **5. Bug 与稳定性**
| 严重程度 | Issue 链接 | 描述 | 修复状态 |
|----------|------------|-------|----------|
| **Critical** | [#48183](https://github.com/openclaw/openclaw/issues/48183) | Feishu 内存泄漏 | PR 进行中（[#87458](https://github.com/openclaw/openclaw/pull/87458)） |
| **High** | [#87395](https://github.com/openclaw/openclaw/issues/87395) | Native Hook 间歇性不可用 | PR 进行中（[#87481](https://github.com/openclaw/openclaw/pull/87481)） |
| **High** | [#83184](https://github.com/openclaw/openclaw/issues/83184) | 心跳消息阻塞后续心跳 | PR 进行中（[#87476](https://github.com/openclaw/openclaw/pull/87476)） |
| **Medium** | [#87357](https://github.com/openclaw/openclaw/issues/87357) | Telegram 插件状态硬上限 | PR 进行中（[#87481](https://github.com/openclaw/openclaw/pull/87481)） |

---

## **6. 功能请求与路线图信号**
- **Gateway-lite 模式**（[#86881](https://github.com/openclaw/openclaw/issues/86881)）：轻量级部署需求强烈，已有 PR 设计。
- **会话结束钩子**（[#10142](https://github.com/openclaw/openclaw/issues/10142)）：Temporal 集成场景，需评估实现成本。
- **插件生命周期事件**（[#87362](https://github.com/openclaw/openclaw/issues/87362)）：插件开发者反馈强烈，技术可行性高。

---

## **7. 用户反馈摘要**
- **痛点**：
  - **消息丢失**：Discord/QQBot 会话消息重复（[#39476](https://github.com/openclaw/openclaw/issues/39476)）、WhatsApp 流式文本块覆盖（[#87326](https://github.com/openclaw/openclaw/issues/87326)）。
  - **模型切换异常**：Claude 推理默认开启导致费用激增（[#73182](https://github.com/openclaw/openclaw/issues/73182)）、Gemini 回退错误（[#86820](https://github.com/openclaw/openclaw/issues/86820)）。
- **满意点**：Gateway 启动性能提升（v2026.5.26 文档提及）、会话缓存优化。

---

## **8. 待处理积压**
| Issue/PR | 状态 | 备注 |
|---------|------|------|
| [#87395](https://github.com/openclaw/openclaw/issues/87395) | 活跃 | Native Hook 不可用，需紧急跟进 |
| [#87357](https://github.com/openclaw/openclaw/issues/87357) | 活跃 | Telegram 插件状态硬上限，修复中 |
| [#87326](https://github.com/openclaw/openclaw/issues/87326) | 新报告 | WhatsApp 流式文本块丢失，需验证 |

---

**总结**：OpenClaw 今日以 **会话稳定性、模型切换、插件管理** 为核心，多个高优先级 Bug 已有 PR 推进，社区对轻量部署与插件可观测性需求明确，项目健康度良好，需持续关注 Native Hook 与 Telegram 插件状态修复。

---

## 横向生态对比

---

### **1. 生态全景**  
2026年5月28日，个人AI助手/自主智能体开源生态呈现**高活跃度、强社区驱动、多技术路线并行**的特点：  
- **核心痛点聚焦**：会话稳定性（消息丢失、模型切换）、插件系统兼容性、多平台适配（微信/QQ/飞书等）是各项目的共同挑战；  
- **功能扩展热点**：多模态支持（如图像理解、视频生成）、轻量化部署（Gateway-lite模式）、多提供商集成（Novita/Xiaomi MiMo）成为差异化竞争焦点；  
- **社区协作模式**：用户反馈与开发者修复速度极快（如OpenClaw、AstrBot），部分项目（如NanoClaw）通过RFC推动架构演进，体现生态从“快速迭代”向“质量巩固+长期规划”过渡。

---

### **2. 各项目今日活跃度对比**

| 项目名称          | Issues (新开/活跃) | PRs (待合并) | Release | 健康度评估               |
|-------------------|--------------------|--------------|---------|--------------------------|
| OpenClaw          | 178                | 259          | v2026.5.26 | ⭐⭐⭐⭐⭐（高优先级Bug快速响应，会话路由优化显著） |
| NanoClaw          | 5                  | 18           | 无       | ⭐⭐⭐（RFC推进中，基础问题修复为主） |
| Zeroclaw          | 21                 | 43           | 无       | ⭐⭐⭐⭐（安全隔离与DeepSeek兼容性强） |
| PicoClaw          | 4                  | 6            | Nightly  | ⭐⭐（稳定性修复+ChatStream功能） |
| HermesAgent       | 213                | 500          | 无       | ⭐⭐⭐⭐⭐（Codex/OpenAI崩溃集中爆发，修复中） |
| LobsterAI         | 2                  | 29           | 2026.5.27 | ⭐⭐⭐⭐（媒体生成、Agent ID重构） |
| IronClaw          | 26                 | 21           | 无       | ⭐⭐⭐⭐（Reborn模块/OAuth集成进展显著） |
| AstrBot           | 21                 | 19           | 无       | ⭐⭐⭐⭐（QQ/飞书适配、插件市场活跃） |

> **健康度说明**：⭐为1星（低活跃度），⭐⭐⭐⭐（高活跃+关键问题修复），⭐⭐⭐⭐⭐（全栈优化+社区响应极佳）。

---

### **3. OpenClaw在生态中的定位**
#### **优势**  
- **会话稳定性标杆**：v2026.5.26 版本优化 Gateway 启动性能、回复可见性分离，内存泄漏修复，解决多平台消息丢失问题，被多个项目（如NanoClaw、IronClaw）参考其会话路由设计；  
- **插件系统成熟度**：Telegram硬上限问题修复方案（PR #87481）被Zeroclaw等借鉴，体现模块化治理经验；  
- **社区规模**：Issues/PR数量居首（373 Issues, 500 PRs），开发者参与度高，但需警惕维护者负荷。  

#### **技术路线差异**  
- **分层架构**：Gateway层性能优化 + 插件层状态管理，区别于其他项目（如NanoClaw侧重底层协议，LobsterAI聚焦多模态）；  
- **目标用户**：企业级部署（如IronClaw的GSuite集成）、开发者友好（插件生态如AstrBot）。

---

### **4. 共同关注的技术方向**
| 需求主题                | 涉及项目                                                                 | 具体诉求                                                                 |
|-------------------------|--------------------------------------------------------------------------|--------------------------------------------------------------------------|
| **会话稳定性**          | OpenClaw, NanoClaw, IronClaw, AstrBot                                   | 消息丢失、路由错误、上下文一致性                                          |
| **多提供商集成**        | Zeroclaw, Moltis, AstrBot, QwenPaw                                      | 支持DeepSeek/Xiaomi MiMo/Gemini等第三方模型                               |
| **插件系统优化**        | OpenClaw, NanoClaw, AstrBot                                             | 状态硬上限、生命周期事件、工具链阻塞                                      |
| **轻量化部署**          | OpenClaw, NanoClaw                                                      | Gateway-lite模式、资源占用控制                                            |
| **多模态交互**          | LobsterAI, QwenPaw, AstrBot                                             | 图像/视频生成、`describe_image()`                                        |
| **跨平台适配**          | NanoClaw, AstrBot                                                       | QQ/飞书/微信消息格式、文件上传限制                                       |

---

### **5. 差异化定位分析**
| 项目          | 功能侧重                     | 目标用户               | 技术架构亮点                          |
|---------------|------------------------------|------------------------|---------------------------------------|
| **OpenClaw**  | 会话路由、插件治理           | 企业开发者、插件生态    | 分层架构（Gateway+插件层）             |
| **NanoClaw**  | 底层协议、容器化适配         | 基础设施开发者         | NixOS网络配置优化                      |
| **Zeroclaw**  | 安全隔离、多提供商兼容       | 安全敏感型应用         | WASM插件+Jina AI搜索集成              |
| **PicoClaw**  | 嵌入式场景、实时通信         | 边缘设备开发者         | MQTT TLS验证优化                       |
| **HermesAgent**| Codex/OpenAI崩溃修复        | 多Agent协作场景        | Reborn上下文压缩                       |
| **LobsterAI** | 多模态、技能商店            | 创意工作者、企业用户    | Kling V3视频生成+Agent ID重构           |
| **IronClaw**  | OAuth集成、子代理稳定性      | 企业SSO、自动化流程    | Reborn模块+GSuite登录                  |
| **AstrBot**   | 社交平台插件、多机器人群控    | 开发者、社群管理者     | QQ/飞书消息分段优化                    |
| **QwenPaw**   | 桌面端、GitLab技能源         | 开发者、团队协作       | Tauri 2.x+Web IDE三面板                |

---

### **6. 社区热度与成熟度分层**
#### **快速迭代阶段**（⭐⭐⭐⭐⭐）
- **OpenClaw**：会话路由、插件状态、模型切换问题密集修复，社区反馈驱动开发节奏；  
- **HermesAgent**：Codcr/OpenAI崩溃集中爆发，紧急修复提案激增；  
- **AstrBot**：QQ/飞书适配、插件市场提交频繁，用户与开发者协同度高。  

#### **质量巩固阶段**（⭐⭐⭐⭐）
- **Zeroclaw**：安全隔离、DeepSeek兼容RFC推进，架构决策明确；  
- **IronClaw**：Reborn模块、OAuth集成完成关键里程碑；  
- **NanoClaw**：底层协议优化，RFC推动长期改进。  

#### **稳定期**（⭐⭐⭐）
- **LobsterAI**：媒体生成、Agent ID重构，功能扩展为主；  
- **PicoClaw**：嵌入式场景优化，Nightly Build发布。  

---

### **7. 值得关注的趋势信号**
#### **行业趋势与开发者价值**
1. **会话稳定性优先**：  
   - OpenClaw的Gateway性能优化、NanoClaw的上下文一致性修复，反映企业级用户对**可靠会话**的核心诉求；  
   - 建议开发者参考其会话路由设计（如外部上下文优先策略）。  

2. **多提供商集成**：  
   - Zeroclaw的WASM插件架构、Moltis的Novita/Xiaomi MiMo支持，提示**开放生态**是未来方向；  
   - 推荐采用类似Zeroclaw的Provider注册模块设计。  

3. **轻量化与多模态**：  
   - OpenClaw的Gateway-lite模式、LobsterAI的Kling V3视频生成，表明**边缘计算+创意工具**双赛道；  
   - 可结合PicoClaw的MQTT优化与QwenPaw的Tauri桌面端体验。  

4. **插件系统标准化**：  
   - OpenClaw的状态硬上限修复、NanoClaw的Extism插件重构，呼吁**统一插件生命周期管理**；  
   - 建议维护者制定插件规范（如Zeroclaw的WASMI提案）。  

5. **跨平台适配**：  
   - NanoClaw的NixOS网络配置、AstrBot的QQ/飞书消息格式，凸显**协议兼容性**的重要性；  
   - 可复用NanoClaw的适配器抽象层设计。  

---

**总结**：2026年5月28日的动态显示，生态正经历**从野蛮生长到质量共建**的转型期，开发者应重点关注：  
- **会话可靠性**（OpenClaw）、**多模型支持**（Zeroclaw/Moltis）、**插件治理**（OpenClaw/NanoClaw）三大方向，同时借鉴各项目的RFC流程和紧急修复策略，平衡快速迭代与长期可持续性。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

---

# **NanoBot 项目日报（2026-05-28）**

---

## **1. 今日速览**
- NanoBot 在今日保持高度活跃，共处理 **6 条 Issues**（5 新开/活跃 + 1 关闭）和 **25 条 Pull Requests**（18 待合并 + 7 已合并），无新版本发布。
- 社区贡献者积极提交功能增强（如 Discord 模型切换、GitAgent Protocol 支持）和关键修复（MCP 重连优化、Codex 流超时配置）。
- 用户反馈集中在 **对话历史一致性**、**微信消息限制** 和 **Dream 系统开关配置** 等核心场景，表明项目正在快速迭代以解决实际使用痛点。

---

## **2. 版本发布**
- **无新版本发布**。

---

## **3. 项目进展**
### **已合并 PR（7 条）**
- **[PR #4015](https://github.com/HKUDS/nanobot/pull/4015)**：新增 `OBSERVATION_REFLECTION_PROMPT`，实现 Agent Loop 自循环逻辑，提升工具执行后的上下文反思能力。  
- **[PR #4014 & #4027](https://github.com/HKUDS/nanobot/pull/4014, https://github.com/HKUDS/nanobot/pull/4027)**：修复 MCP 客户端重连机制，解决会话断开后无法自动恢复的问题，并添加回调触发重连。  
- **[PR #4018](https://github.com/HKUDS/nanobot/pull/4018)**：使 Codex 提供商支持 `NANOBOT_STREAM_IDLE_TIMEOUT_S` 环境变量，允许自定义流超时时间。  
- **[PR #4026](https://github.com/HKUDS/nanobot/pull/4026)**：Dockerfile 中集成 GitHub CLI (`gh`) 和 Google Workspace CLI (`gogcli`)，扩展容器内开发工具链。  

### **待合并 PR（18 条）**
- 包括 **Discord 模型切换命令**（[#4031](https://github.com/HKUDS/nanobot/pull/4031)）、**GitAgent Protocol 支持**（[#4030](https://github.com/HKUDS/nanobot/pull/4030)）、**心跳服务重构为 Cron 注册**（[#4023](https://github.com/HKUDS/nanobot/pull/4023)）等，均涉及基础设施改进和用户体验增强。

---

## **4. 社区热点**
### **最活跃 Issue**
- **[Issue #1922](https://github.com/HKUDS/nanobot/issues/1922)**（已关闭）：用户 `Good0007` 开发了 **nanobot-webui**，提供自托管 Web 管理面板，支持多用户、实时聊天和配置管理，获 10 星标和 10 条评论，反映用户对可视化管理的强烈需求。  
- **[Issue #3885](https://github.com/HKUDS/nanobot/issues/3885)**：请求为 Dream 系统作业添加全局开关配置，避免强制注册 cron 作业，已有 PR 提案（需进一步讨论）。  
- **[Issue #4006](https://github.com/HKUDS/nanobot/issues/4006)**：报告对话历史中存在孤立的 `tool result` 消息，违反 OpenAI/Anthropic API 规范，影响严格校验的下游服务。

---

## **5. Bug 与稳定性**
| **严重性** | **问题描述** | **状态** | **关联 PR** |
|-----------|-------------|---------|------------|
| 高 | 对话历史中孤立 `tool result` 消息导致 API 拒绝请求 | 开放 | 无（需修复） |
| 中 | 微信对话最多返回 10 条消息（[Issue #2772](https://github.com/HKUDS/nanobot/issues/2772)） | 开放 | 无 |
| 低 | LLM 流超时错误（[Issue #4013](https://github.com/HKUDS/nanobot/issues/4013)） | 开放 | [PR #4020](https://github.com/HKUDS/nanobot/pull/4020)（已提方案） |

---

## **6. 功能请求与路线图信号**
- **Dream 系统开关配置**（[#3885](https://github.com/HKUDS/nanobot/issues/3885)）可能通过 `agents.defaults.dream.enabled` 字段实现，已在 PR 提案阶段。  
- **微信消息限制突破**（[#2772](https://github.com/HKUDS/nanobot/issues/2772)）需调整上下文 token 分配策略，暂无 PR。  
- **Provider 模型覆盖**（[#4029](https://github.com/HKUDS/nanobot/issues/4029)）允许不同提供商为默认模型和 Dream 模型指定不同模型，可能纳入下一版本。  
- **GitAgent Protocol 支持**（[#4030](https://github.com/HKUDS/nanobot/pull/4030)）作为标准化 Agent 生态的扩展，优先级较高。

---

## **7. 用户反馈摘要**
- **正面反馈**：  
  - nanobot-webui（[#1922](https://github.com/HKUDS/nanobot/issues/1922)）获得广泛认可，用户期待官方集成类似功能。  
- **痛点**：  
  - 微信消息截断（[#2772](https://github.com/HKUDS/nanobot/issues/2772)）影响长对话体验；  
  - Dream 作业强制注册（[#3885](https://github.com/HKUDS/nanobot/issues/3885)）暴露配置粒度不足；  
  - 孤立 `tool result`（[#4006](https://github.com/HKUDS/nanobot/issues/4006)）引发下游兼容性问题。

---

## **8. 待处理积压**
- **长期未响应 Issue**：  
  - [#2772](https://github.com/HKUDS/nanobot/issues/2772)（微信消息限制）：需评估是否引入动态上下文 token 分配或分块传输机制。  
  - [#4006](https://github.com/HKUDS/nanobot/issues/4006)（对话历史一致性）：需设计消息配对校验逻辑，可能涉及存储层改造。  
- **PR 等待合并**：  
  - GitAgent Protocol 相关 PR（[#4030](https://github.com/HKUDS/nanobot/pull/4030)）需测试验证兼容性。

---

**总结**：NanoBot 近期活跃度显著，核心功能（MCP、Agent Loop、WebUI）持续优化，但需优先解决对话历史和微信消息等用户高频痛点。建议维护者关注积压 Issue 并推动关键 PR 合并。

</details>

<details>
<summary><strong>Zeroclaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

---

# **Zeroclaw 项目日报（2026-05-28）**

---

## 1. 今日速览
- **活跃度**：过去24小时内，Zeroclaw 社区活跃度高，共更新 **31条 Issues**（含21条新开/活跃）、**50条 PR**（43条待合并），无新版本发布。  
- **核心焦点**：主要集中在 **DeepSeek API兼容性**、**安全隔离与凭证管理**、**插件系统重构** 三大方向，同时伴随多个 **运行时稳定性修复** 和 **工具链增强**。  
- **健康度评估**：问题响应迅速（如高优先级 Bug 已有对应 PR），但部分长期 Issue（如 #6943 Extism 插件系统冲突）仍需维护者介入。

---

## 2. 版本发布
**无新版本发布**。

---

## 3. 项目进展
### ✅ 合并/关闭的重要 PR
| PR 编号 | 类型       | 关键进展                                                                 |
|--------|------------|--------------------------------------------------------------------------|
| [#6986](https://github.com/zeroclaw-labs/zeroclaw/pull/6986) | 修复 | 修复 WebSocket 聊天会话中 `CanvasStore` 共享问题，确保跨会话状态一致性。 |
| [#6985](https://github.com/zeroclaw-labs/zeroclaw/pull/6985) | 功能 | 新增 `/api/channels` 的 `readiness` 结构化报告，提升网关通道健康度可见性。 |
| [#6980](https://github.com/zeroclaw-labs/zeroclaw/pull/6980) | 修复 | 解决 DeepSeek 推理内容 (`reasoning_content`) 在原生工具请求中的丢失问题。 |

**整体推进**：  
- **安全隔离**：`http_request` 私有主机白名单 (#6977→#6981)、凭证配置分类 (#6982) 等增强。  
- **运行时稳定性**：流式错误恢复机制 (#6983)、WebSocket 连接参数修正 (#6986)。  
- **架构演进**：插件系统重构提案 (#6943)、集成队列跟踪 (#6970) 为长期目标铺路。

---

## 4. 社区热点
### 🔥 最活跃 Issues/PRs
#### **#6059: DeepSeek-V4 API 格式不兼容** ([链接](https://github.com/zeroclaw-labs/zeroclaw/issues/6059))
- **背景**：用户使用 DeepSeek-Pro/Flash 时因 `thinking_mode` 报错，影响核心功能。  
- **诉求**：需适配 DeepSeek 最新 API 规范，已有修复 PR (#6980) 正在推进。  

#### **RFC: 插件系统统一化** (#6489, [#6943](https://github.com/zeroclaw-labs/zeroclaw/issues/6489))  
- **矛盾点**：当前 Extism WASM 插件与集成模块分离，导致开发体验割裂。  
- **信号**：社区明确需求 (#6943) 提议改用 wasmtime + wasip2，简化插件生命周期。  

#### **#6971: 安全 UX 与默认隔离** ([链接](https://github.com/zeroclaw-labs/zeroclaw/issues/6971))  
- **痛点**：用户希望更直观的运行时安全边界（如凭证处理、沙箱隔离），RFC 中提出默认策略。

---

## 5. Bug 与稳定性
| 严重性 | Issue 编号 | 问题描述 | 修复状态 |
|--------|------------|----------|----------|
| S1 (阻塞) | [#6984](https://github.com/zeroclaw-labs/zeroclaw/issues/6984) | 网关令牌轮换未撤销旧令牌，存在安全风险 | 待修复（无 PR） |
| S1 (阻塞) | [#6965](https://github.com/zeroclaw-labs/zeroclaw/issues/6965) | Web UI 聊天中 `canvas` 工具帧推送失败 | 待修复（无 PR） |
| S2 (降级) | [#6976](https://github.com/zeroclaw-labs/zeroclaw/issues/6976) | Web UI WebSocket 缺少 `?agent=` 参数导致断开 | 修复中 (#6986) |
| S2 (降级) | [#6923](https://github.com/zeroclaw-labs/zeroclaw/issues/6923) | OpenAI OAuth 认证未生效 | 待修复（无 PR） |

---

## 6. 功能请求与路线图信号
### 🔮 下一版本候选功能
| 需求 | 关联 PR | 优先级 |
|------|---------|--------|
| **DeepSeek 兼容支持** | [#6980](https://github.com/zeroclaw-labs/zeroclaw/pull/6980) | P1 |
| **插件系统重构** | [#6943](https://github.com/zeroclaw-labs/zeroclaw/issues/6943) | P2（长期） |
| **Jina AI 搜索集成** | [#6833](https://github.com/zeroclaw-labs/zeroclaw/pull/6833) | P2 |
| **TUI 快捷键优化** | [#6950](https://github.com/zeroclaw-labs/zeroclaw/issues/6950) | P2 |

---

## 7. 用户反馈摘要
- **痛点**：  
  - **API 兼容性**：DeepSeek 用户抱怨格式不匹配 (#6059)，影响生产环境使用。  
  - **安全焦虑**：开发者关注凭证泄露风险（如 #6978 嵌套字段未脱敏）。  
  - **工具链割裂**：插件与集成模块分离 (#6489) 增加维护成本。  
- **满意点**：  
  - 社区对 RFC 流程响应积极（如 #6808 工作流自动化提案获快速讨论）。

---

## 8. 待处理积压
| Issue/PR | 状态 | 提醒 |
|---------|------|------|
| [#6943](https://github.com/zeroclaw-labs/zeroclaw/issues/6943) | 开放 | Extism 插件系统架构冲突，需维护者决策。 |
| [#6915](https://github.com/zeroclaw-labs/zeroclaw/issues/6915) | 阻塞 | 技能工具临时权限提升，依赖 #6924 实现。 |
| [#6954](https://github.com/zeroclaw-labs/zeroclaw/issues/6954) | 提案 | 定时任务消息管道路由，需与 #6632 Cron 调度问题联动修复。 |

---

**总结**：Zeroclaw 在 **安全加固** 和 **生态扩展** 上持续发力，但需优先解决 **DeepSeek 兼容性** 和 **插件系统重构** 两大社区痛点。建议维护者聚焦高优先级阻塞项（如 #6984、#6965），并同步推进 RFC 落地。

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

---

# **PicoClaw 项目日报（2026-05-28）**

---

## **1. 今日速览**
- **活跃度**：过去24小时内，项目保持较高活跃状态，共新增 **4个 Issues**、**6个 PRs**（其中 **1个已合并**），并发布 **1个 Nightly Build**。
- **核心进展**：重点修复了 **MQTT TLS验证配置**、**工具调用消息丢失问题**，并优化了 **单例进程检查逻辑**，提升稳定性。
- **社区参与**：Issues 和 PRs 均来自核心贡献者（如 @loafoe、@yuxuan-7814），表明开发团队对关键问题的快速响应。

---

## **2. 版本发布**
- **Nightly Build v0.2.9-nightly.20260528.28ec5793**  
  - **更新内容**：基于 `main` 分支的最新提交构建，包含未稳定测试的改动。  
  - **变更摘要**：[完整日志](https://github.com/sipeed/picoclaw/compare/v0.2.9...main)  
  - **注意事项**：此为自动化构建，可能存在不稳定行为，建议生产环境谨慎使用。

---

## **3. 项目进展**
### **✅ 已合并 PR**
- **[PR #2853](https://github.com/sipeed/picoclaw/pull/2853)**  
  - **功能**：为 Pico 频道添加 **ChatStream 支持**，实现实时令牌流式传输，显著提升长对话体验。  
  - **影响范围**：WebSocket 客户端可即时接收模型生成内容，适用于低延迟场景。

---

## **4. 社区热点**
### **🔥 高关注度 Issues**
#### **Issue #2958: Tool calls dropped during consecutive pico channel requests**  
  - **描述**：连续请求时，Pico 通道的 `tool_calls` 消息仅首次有效，后续被丢弃。  
  - **链接**：[GitHub Issue #2958](https://github.com/sipeed/picoclaw/issues/2958)  
  - **关联修复**：已有 **PR #2957** 提交修复方案（见下文）。  

#### **Issue #2952: 用户反馈多模块改进需求**  
  - **痛点**：  
    - exec 命令默认行为不一致导致报错；  
    - QQ 渠道重启逻辑缺陷；  
    - 模型提供商界面交互需优化（如 Key 复用、一键添加）。  
  - **链接**：[GitHub Issue #2952](https://github.com/sipeed/picoclaw/issues/2952)  
  - **信号**：反映用户对 **易用性** 和 **配置管理** 的强烈诉求。

---

## **5. Bug 与稳定性**
| **严重程度** | **问题描述** | **修复状态** |
|--------------|--------------|--------------|
| 🔴 **高** | MQTT 通道硬编码 `InsecureSkipVerify=true`（MITM 风险） | [PR #2899](https://github.com/sipeed/picoclaw/pull/2899) 已合并 |
| 🟡 **中** | 工具调用消息在流式传输中被过滤丢失 | [PR #2957](https://github.com/sipeed/picoclaw/pull/2957) 待合并 |
| 🟢 **低** | 单例 PID 检查未验证进程身份（可能误杀其他进程） | [PR #2955](https://github.com/sipeed/picoclaw/pull/2955) 待合并 |

---

## **6. 功能请求与路线图信号**
- **优先级高**：  
  - **动态 HTTP 头传递**（[PR #2696](https://github.com/sipeed/picoclaw/pull/2696)）：允许通道上下文动态注入 MCP 请求头，增强灵活性。  
  - **TLS 可配置化**（[PR #2899](https://github.com/sipeed/picoclaw/pull/2899)）：解决安全合规需求。  
- **潜在需求**：  
  - 从 Issue #2952 看，**UI 交互优化**（如 Key 管理、模型列表同步）可能成为下一版本重点。

---

## **7. 用户反馈摘要**
- **痛点**：  
  - **Android 32位系统兼容性缺失**（[Issue #2954](https://github.com/sipeed/picoclaw/issues/2954)）：影响低端设备用户。  
  - **OAuth 流事件忽略**（[Issue #2953](https://github.com/sipeed/picoclaw/issues/2953)）：OpenAI/Codex 认证后返回空响应，需底层协议修复。  
- **满意度**：  
  - ChatStream 功能（PR #2853）获得积极反馈，但部分用户仍需等待稳定版。

---

## **8. 待处理积压**
- **⚠️ 长期未响应 Issue**：  
  - **Issue #2954（Android 32位支持）**：需评估架构适配成本，建议优先处理以扩大用户覆盖。  
- **⚠️ 待合并 PR**：  
  - **PR #2957（工具调用修复）**：直接影响用户体验，建议尽快合并。  
  - **PR #2956（通道状态保留）**：避免配置被意外覆盖的配置问题。

---

**总结**：PicoClaw 近期在 **实时通信** 和 **安全性** 方面取得显著进展，但需持续关注 **跨平台兼容性** 和 **UI 体验优化** 的用户反馈。维护团队响应迅速，项目健康度良好。

</details>

<details>
<summary><strong>hermesagent</strong> — <a href="https://github.com/NousResearch/hermes-agent">NousResearch/hermes-agent</a></summary>

---

# **HermesAgent 项目日报（2026-05-28）**

---

## **1. 今日速览**
- 过去24小时内，**Issues 活跃度极高**：新增/活跃 Issues 213 条，评论总数达 290+，其中 **Codex/OpenAI 相关崩溃问题集中爆发**，引发大量用户反馈。
- **PR 提交量激增**：500 条新 PR，多数为紧急修复和性能优化，表明团队正积极应对近期稳定性问题。
- **无新版本发布**，但社区对 `openai-codex` 的崩溃问题已有多个修复提案（如 #33598、#33390）。

---

## **2. 版本发布**
> **无新版本发布**

---

## **3. 项目进展**
### **关键合并 PR**
| PR | 类型 | 内容 | 链接 |
|----|------|------|------|
| [#33598](https://github.com/NousResearch/hermes-agent/pull/33598) | Bug Fix | 在降级重试前压缩上下文，避免循环超时错误 | [详情](#) |
| [#33390](https://github.com/NousResearch/hermes-agent/pull/33390) | Bug Fix | 修复 Codex 长 Prefill 流处理超时问题 | [详情](#) |
| [#33602](https://github.com/NousResearch/hermes-agent/pull/33602) | Feature | 原生支持 Responses API 的 `web_search` 工具 | [详情](#) |

**进展总结**：  
团队快速响应了 **Codex/OpenAI 流崩溃** 和 **上下文过长** 等核心问题，同时推进了工具链增强（如原生 `web_search`），技术债清理明显。

---

## **4. 社区热点**
### **Top 热门 Issues/PRs**
#### **🔥 最活跃 Issue: #32892 - `openai-codex` 崩溃**
- **问题描述**：ChatGPT 集成后返回 `'NoneType' object is not iterable`，影响所有用户。
- **评论数**：38 条，👍 51，多人复现。
- **关联 PR**：[#33598](https://github.com/NousResearch/hermes-agent/pull/33598) 已提交修复方案。

#### **📌 高频痛点：Codex 流稳定性**
- 多个 Issue (#32373, #32956, #33041) 均指向 `gpt-5.5/gpt-5.3-spark` 的流中断问题，用户反馈“官方 CLI 可用，Hermes 崩溃”。

---

## **5. Bug 与稳定性**
| 严重性 | Issue | 状态 | 修复进度 | 链接 |
|--------|-------|------|----------|------|
| **P2** | [#21444](https://github.com/NousResearch/hermes-agent/issues/21444) | 已关闭 | ✅ PR [#33598](https://github.com/NousResearch/hermes-agent/pull/33598) | [详情](#) |
| **P3** | [#32892](https://github.com/NousResearch/hermes-agent/issues/32892) | 已关闭 | ✅ PR [#33598](https://github.com/NousResearch/hermes-agent/pull/33598) | [详情](#) |
| **P3** | [#33041](https://github.com/NousResearch/hermes-agent/issues/33041) | 已关闭 | 🔄 待验证 | [详情](#) |

**趋势分析**：  
- **Codex 流崩溃占 60%+ 的活跃 Issues**，需优先解决。
- Docker 权限问题 (#23402) 和启动慢 (#5726) 也需跟进。

---

## **6. 功能请求与路线图信号**
| 需求 | 优先级 | 关联 PR | 可能性 |
|------|--------|---------|--------|
| **多 Agent 单进程隔离** (#9514) | P3 | 无 | 高（用户强烈需求） |
| **Telegram 话题路由** (#10143) | P3 | 无 | 中（需架构评估） |
| **原生 `web_search`** (#33602) | P3 | ✅ 已合并 | ✅ 下一版本 |

**信号解读**：  
- **多 Agent 隔离** 是用户明确痛点（如“每个 Agent 独立内存”），可能纳入 v0.15。
- `web_search` 工具链增强已进入开发阶段。

---

## **7. 用户反馈摘要**
- **痛点**：  
  - **Codex 不可用**：“官方 CLI 正常，Hermes 崩溃”（#32892）。  
  - **启动慢**：“Honcho 内存初始化阻塞 60s/步”（#5726）。  
  - **Docker 权限**：“无法创建 home 目录”（#18482）。  
- **满意点**：  
  - 用户对 `web_search` 新功能期待高（#33602 获赞）。

---

## **8. 待处理积压**
| Issue | 状态 | 风险等级 | 链接 |
|-------|------|----------|------|
| [#9514](https://github.com/NousResearch/hermes-agent/issues/9514) | OPEN | 高（多 Agent 需求） | [详情](#) |
| [#5726](https://github.com/NousResearch/hermes-agent/issues/5726) | OPEN | 中（性能瓶颈） | [详情](#) |
| [#33041](https://github.com/NousResearch/hermes-agent/issues/33041) | CLOSED | ⚠️ 需验证修复 | [详情](#) |

**建议**：  
- **优先处理 Codex 流崩溃**，其次优化 Honcho 初始化性能。
- 多 Agent 隔离需求可结合 #33585（Delegate 预路由）协同推进。

--- 

**数据驱动结论**：项目处于 **高活跃修复期**，需聚焦 **Codex 稳定性** 和 **多 Agent 架构**，社区信任度依赖此问题的快速解决。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

---

# **NanoClaw 项目日报（2026-05-28）**

---

## **1. 今日速览**
过去24小时内，NanoClaw 保持中等活跃度：  
- **代码贡献**：9条 PR（5条待合并，4条已关闭），显示开发团队在快速响应问题。  
- **Issue 进展**：1条 Issue 关闭（#80，长期高优先级需求），但无新问题报告，表明当前稳定性良好。  
- **无新版本发布**，功能迭代以修复和优化为主。  
整体状态：**健康且高效推进**，社区参与度稳定。

---

## **2. 版本发布**
**无新版本发布**。

---

## **3. 项目进展**
### **已合并/关闭的 PR（4条）**
| PR # | 标题 | 关键改进 | 链接 |
|------|------|----------|------|
| **#5** | Fix cross-group scheduled tasks getting wrong chat_jid | 修复了跨组定时任务因 IPC 传递错误 JID 导致的逻辑问题，确保任务正确路由到目标群组。 | [详情](https://github.com/nanocoai/nanoclaw/pull/5) |
| **#2629** | feat(container): use `--network=host` and `127.0.0.1` gateway on NixOS | 针对 NixOS 容器网络配置优化，解决 `host.docker.internal` 解析失败问题。 | [详情](https://github.com/nanocoai/nanoclaw/pull/2629) |
| **#2577** | miss pr | 无效 PR（自动关闭）。 | [详情](https://github.com/nanocoai/nanoclaw/pull/2577) |
| **#2623** | miss pr | 无效 PR（自动关闭）。 | [详情](https://github.com/nanocoai/nanoclaw/pull/2623) |

**总结**：主要解决了跨组任务调度、NixOS 容器兼容性等底层问题，提升多环境部署可靠性。

---

## **4. 社区热点**
### **高关注度 Issue (#80)**
- **标题**: Support runtimes/providers other than Claude/Anthropic ([链接](https://github.com/nanocoai/nanoclaw/issues/80))  
- **热度**: 60 👍，33 条评论，创建于 2026-02-04，最后更新于 2026-05-27（已关闭）。  
- **背景与诉求**:  
  用户指出 Anthropic 可能限制非官方客户端使用，呼吁支持 OpenCode、Gemini 等其他开源 AI 提供商。该 Issue 长期存在，最终通过关闭表明已有解决方案或替代路径（如多 Provider 适配）。  
- **信号意义**: 反映用户对生态开放性的强烈需求，未来需持续关注多模型集成进展。

---

## **5. Bug 与稳定性**
**无新 Bug 报告**，以下问题已通过 PR 修复：
- **#5**: 跨组任务调度 JID 错误（已修复）。  
- **#2629**: NixOS 容器网络配置问题（已修复）。  

---

## **6. 功能请求与路线图信号**
### **活跃 PR 中的新功能提案**
| PR # | 标题 | 潜在影响 | 链接 |
|------|------|----------|------|
| **#2624** | feat: per-server disabledTools in McpServerConfig | 允许按服务器禁用特定工具，增强 MCP 配置的灵活性。 | [详情](https://github.com/nanocoai/nanoclaw/pull/2624) |
| **#2628** | fix(cli): honor user-supplied `--id` in `ncl groups create` | 修复 CLI 中 `--id` 参数被忽略的问题，提升用户自定义 ID 的体验。 | [详情](https://github.com/nanocoai/nanoclaw/pull/2628) |

**下一版本候选**：  
- **MCP 服务器细粒度控制**（#2624）可能成为多租户场景的关键需求。  
- **CLI 参数一致性修复**（#2628）可改善开发者体验。

---

## **7. 用户反馈摘要**
从 Issues 评论中提取的关键洞察：
- **痛点**：  
  - Anthropic 政策变化迫使用户寻求替代方案（Issue #80）。  
  - NixOS 用户面临容器网络配置复杂性（PR #2629）。  
- **满意点**：  
  - 对跨组任务调度的修复（PR #5）获得隐式认可（无负面反馈）。  
- **不满意点**：  
  - 部分用户抱怨文档未及时更新（如 `--id` 参数行为，见 PR #2628）。

---

## **8. 待处理积压**
**需关注的长期 Issue/PR**：
- **#2627**（OPEN）：对齐 Slack 与其他平台反应符号规范（[链接](https://github.com/nanocoai/nanoclaw/pull/2627)）。  
  - 涉及多平台兼容性，需测试验证。  
- **#2626**（OPEN）：修复 Signal 服务重启静默失败问题（[链接](https://github.com/nanocoai/nanoclaw/pull/2626)）。  
  - 影响服务自愈能力，建议尽快合并。

---

**总结**：NanoClaw 近期聚焦底层稳定性和多平台适配，社区反馈积极。建议优先处理积压的跨平台兼容性问题，并持续跟踪多 Provider 集成进展。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

---

# IronClaw 项目日报（2026-05-28）

---

## 1. **今日速览**
IronClaw 项目在过去 24 小时内保持高度活跃，共处理 **37 条 Issues**（新开/活跃 26 条，关闭 11 条）和 **50 条 PR**（待合并 21 条，已合并/关闭 29 条）。核心团队在 Reborn 模块、WebUI 重构、GSuite OAuth 集成及子代理（subagent）功能优化方面进展显著。无新版本发布，但多个关键功能已进入实现或测试阶段，整体开发节奏紧凑且目标明确。

---

## 2. **版本发布**
> 无新版本发布。

---

## 3. **项目进展**

### ✅ **重要合并/关闭的 PR**
- **[PR #4110](https://github.com/nearai/ironclaw/pull/4110)**  
  完成 Reborn 上下文压缩（context compaction）第一阶段，新增策略槽、执行器阶段、主机压缩端口、系统推理适配器等，并优化了范围读取逻辑，显著提升性能。
- **[PR #4111](https://github.com/nearai/ironclaw/pull/4111)**  
  实现 Google OAuth 后端集成，支持回调令牌交换和凭证生命周期管理，为 GSuite 登录提供完整支持。
- **[PR #4154](https://github.com/nearai/ironclaw/pull/4154)**  
  改进 Reborn Shell 输出捕获机制，通过临时文件存储大体积输出，避免内存溢出风险。
- **[PR #4089](https://github.com/nearai/ironclaw/pull/4089)**  
  修复子代理（subagent）完成后通知父代理的问题，确保结果正确传递。

这些 PR 推动了 Reborn 模块的核心能力，尤其在压缩、OAuth 集成和子代理稳定性方面取得实质性进展。

---

## 4. **社区热点**

### 🔥 **最活跃的 Issues/PRs**
#### **Issue #3280** ([链接](https://github.com/nearai/ironclaw/issues/3280))  
- **标题**: [Reborn] Add ProductWorkflow and InboundTurnService facade  
- **热度**: 4 条评论，涉及产品层工作流与入站服务门面设计，关联多个子任务（如 #3269, #3193），是 Reborn 架构演进的关键议题。

#### **PR #4124** ([链接](https://github.com/nearai/ironclaw/pull/4124))  
- **标题**: [codex] Add Reborn provider admin facade  
- **热度**: 新增 Reborn 提供商管理门面，统一模型列表/状态/设置操作，减少对 v1 状态的依赖，体现模块化设计思路。

#### **Issue #4116** ([链接](https://github.com/nearai/ironclaw/issues/4116))  
- **标题**: Carry v1 Google/GitHub/NEAR SSO into WebChat v2  
- **背景**: 用户希望将旧版 SSO 行为迁移至新版 WebChat，反映身份验证流程的平滑过渡需求。

这些讨论表明社区对 Reborn 的架构扩展、OAuth 集成和子代理功能有强烈兴趣，推动项目向更灵活、安全的方向发展。

---

## 5. **Bug 与稳定性**

### ⚠️ **报告的问题**
| Issue | 严重性 | 状态 | 修复 PR |
|-------|--------|------|---------|
| [#4084](https://github.com/nearai/ironclaw/issues/4084) | 高 | 已关闭 | [PR #4089](https://github.com/nearai/ironclaw/pull/4089) |
| [#3436](https://github.com/nearai/ironclaw/issues/3436) | 中 | 开放 | 暂无 |

- **主要问题**: 子代理完成时未通知父代理（已修复）、DeepSeek API 返回 400 错误（需进一步排查）。
- **稳定性**: 近期无崩溃事件，但部分功能（如 OAuth 刷新）仍需完善。

---

## 6. **功能请求与路线图信号**

### 🔮 **新功能提案**
- **Reborn 子代理模式优化** (#4147)  
  设计持久化子代理完成交付方案，解决当前后台子代理结果传递不稳定的问题。
- **定时触发器（cron triggers）** (#3873)  
  支持非实时触发的 LLM 工作流（如每日邮件摘要），增强自动化能力。
- **GSuite 令牌刷新与账户健康检查** (#4113)  
  完善 Google OAuth 的生命周期管理，提升生产环境可靠性。

结合现有 PR（如 #4110、#4111），这些功能很可能纳入下一版本，尤其是 Reborn 压缩和 OAuth 集成。

---

## 7. **用户反馈摘要**

### 💬 **痛点与满意度**
- **痛点**:
  - 缺少对话/线程删除功能（[#1907](https://github.com/nearai/ironclaw/issues/1907)）：用户期望清理历史数据的能力。
  - DeepSeek API 错误（[#3436](https://github.com/nearai/ironclaw/issues/3436)）：推理模式配置问题影响用户体验。
- **满意点**:
  - GSuite OAuth 集成（[#4111](https://github.com/nearai/ironclaw/pull/4111)）：用户赞赏企业登录功能的完善。

---

## 8. **待处理积压**

### ⏳ **长期未响应项**
| Issue/PR | 最后更新时间 | 优先级 |
|----------|--------------|--------|
| [#3289](https://github.com/nearai/ironclaw/issues/3289) | 2026-05-28 | 高（Reborn 核心迁移） |
| [#4149](https://github.com/nearai/ironclaw/issues/4149) | 2026-05-27 | 中（运行时上下文注入） |
| [#4153-4152](https://github.com/nearai/ironclaw/issues/4153) | 2026-05-27 | 低（桌面客户端 UX 阻塞） |

建议优先处理 **#3289**（Reborn 认证流程迁移）和 **#4149**（运行时上下文注入），两者直接影响核心体验。

---

**总结**: IronClaw 在 Reborn 模块、OAuth 集成和子代理功能上取得显著进展，社区反馈积极，但需关注长期积压任务和稳定性修复。

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

---

# **LobsterAI 项目日报（2026-05-28）**

---

## **1. 今日速览**
- LobsterAI 过去24小时保持较高活跃度，共提交 **35个 PR**（含29个待合并），新增 **2个 Issues**，发布 **1个新版本（2026.5.27）**。
- 核心功能持续迭代，包括媒体生成、协作会话优化、Agent ID 数据清理等，同时修复多个用户体验问题。
- 社区反馈集中在会员登录稳定性、任务超时处理及 Agent 数据管理，显示用户对长期运行任务和付费功能的依赖度提升。

---

## **2. 版本发布**
### **LobsterAI 2026.5.27**
#### **主要更新**
- **媒体生成支持**：集成 Kling V3 视频生成功能，基于配额授权（[PR #2064](https://github.com/netease-youdao/LobsterAI/pull/2064)）。
- **协作会话优化**：输入框附件点击预览功能（[PR #2061](https://github.com/netease-youdao/LobsterAI/pull/2061)）。
- **Agent ID 重构**：改用短 UUID 替代名称生成，避免数据复活问题（[PR #2065](https://github.com/netease-youdao/LobsterAI/pull/2065)）。
- **Kit 商店与对话集成**：新增专家套件一键安装、会话上下文注入（[PR #2060](https://github.com/netease-youdao/LobsterAI/pull/2060)）。

#### **破坏性变更**
- **Agent ID 生成逻辑变更**：旧版同名 Agent 可能复用 ID 导致数据残留，需确保删除后彻底清理本地文件（[Issue #1903](https://github.com/netease-youdao/LobsterAI/issues/1903)）。

---

## **3. 项目进展**
### **关键合并/关闭 PR**
| PR | 类型 | 内容 | 链接 |
|----|------|------|------|
| #2065 | 修复 | Agent ID 改用短 UUID，解决数据复活问题 | [详情](https://github.com/netease-youdao/LobsterAI/pull/2065) |
| #2061 | 功能 | 协作会话中图片附件点击预览 | [详情](https://github.com/netease-youdao/LobsterAI/pull/2061) |
| #2060 | 功能 | Kit 商店与对话集成 | [详情](https://github.com/netease-youdao/LobsterAI/pull/2060) |

**推进方向**：  
- 数据一致性（Agent ID）、用户体验（媒体交互）、生态扩展（Kit 商店）三大重点同步推进，项目整体向“多模态协作”和“模块化”演进。

---

## **4. 社区热点**
### **最活跃 Issues/PRs**
#### **Issue #1903: 会员登录频繁失败**
- **背景**：付费模型访问受阻，用户截图显示认证流程异常（[链接](https://github.com/netease-youdao/LobsterAI/issues/1903)）。
- **诉求**：需改进登录稳定性，影响付费功能可用性。

#### **PR #2065: Agent ID 数据清理**
- **讨论焦点**：开发者强调数据残留风险，需彻底清理删除后的 Agent 关联文件（[链接](https://github.com/netease-youdao/LobsterAI/pull/2065)）。

---

## **5. Bug 与稳定性**
| 问题 | 严重性 | 状态 | 链接 |
|------|--------|------|------|
| 会员登录失败 | 高 | 未修复 | [#1903](https://github.com/netease-youdao/LobsterAI/issues/1903) |
| 任务超时中断 | 中 | 待分析 | [#2062](https://github.com/netease-youdao/LobsterAI/issues/2062) |
| Agent ID 数据残留 | 高 | 已修复（PR #2065） | [详情](https://github.com/netease-youdao/LobsterAI/pull/2065) |

---

## **6. 功能请求与路线图信号**
- **Kit 商店集成**（PR #2060）：用户可一键安装技能套件，符合“模块化”趋势，预计纳入下一版本。
- **媒体生成配额系统**（PR #2064）：视频生成功能需完善权限管理，后续可能推出订阅制。
- **任务超时监控**（Issue #2062）：用户期望后台任务自动续期或通知机制，需设计解决方案。

---

## **7. 用户反馈摘要**
- **痛点**：  
  - 会员登录不稳定影响付费体验（Issue #1903）。  
  - 长时间任务无状态提示（Issue #2062）。  
- **满意点**：  
  - 图片预览功能（PR #2061）获潜在用户认可。  
  - Agent ID 重构减少数据混乱（PR #2065）。  

---

## **8. 待处理积压**
| Issue/PR | 状态 | 优先级 | 链接 |
|----------|------|--------|------|
| #1903 会员登录 | 开放 | 紧急 | [详情](https://github.com/netease-youdao/LobsterAI/issues/1903) |
| #2062 任务超时 | 开放 | 高 | [详情](https://github.com/netease-youdao/LobsterAI/issues/2062) |

---

**总结**：LobsterAI 在功能迭代和社区响应上表现积极，但需优先解决登录稳定性和任务超时问题，以保障付费用户的核心体验。

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyclaw">TinyAGI/tinyclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

# **Moltis 项目日报 (2026-05-28)**  

---

## **1. 今日速览**  
过去24小时内，Moltis 保持中等活跃度：  
- **Issues 更新**：2条新开（含1个高关注度交互控制问题 + 1个新Bug报告）。  
- **PR 合并**：2条已关闭 PR，分别涉及嵌入维度配置和Novita AI集成，功能扩展进展顺利。  
- **无新版本发布**，但关键功能改进通过PR推进。  
整体状态健康，社区参与度稳定，但需关注未解决的Issue积压。  

---

## **2. 版本发布**  
**无新版本发布**。  

---

## **3. 项目进展**  
### **合并的 PR**  
#### **PR #1074: Configurable embedding dimensions with safe auto-reindex** ([链接](https://github.com/moltis-org/moltis/pull/1074))  
- **功能亮点**：  
  - 新增可选 `dimensions` 配置字段（兼容旧版 `embedding_dimensions` 别名），支持OpenAI兼容嵌入模型的自定义维度设置。  
  - 引入 `reindex_on_dim_change` 标志，允许在维度变更时自动重建索引，提升灵活性。  
- **意义**：解决了用户自定义嵌入维度的需求，避免数据冗余或兼容性问题。  

#### **PR #451: Add Novita AI as OpenAI-compatible provider** ([链接](https://github.com/moltis-org/moltis/pull/451))  
- **功能亮点**：  
  - 集成Novita AI为OpenAI兼容提供商，支持 `moonshotai/kimi-k2.5`、`deepseek/deepseek-v3.2`、`zai-org/glm-5` 三模型。  
  - 通过环境变量 `NOVITA_API_KEY` 或配置文件 `[providers.novita]` 接入。  
- **意义**：丰富多模型支持生态，降低第三方服务接入成本。  

---

## **4. 社区热点**  
### **Issue #235: PTY-based interactive Claude Code CLI control** ([链接](https://github.com/moltis-org/moltis/issues/235))  
- **背景**：当前框架通过子进程调用Claude Code时，因终端检测失效导致无法进入交互模式，阻碍多Agent协同任务。  
- **诉求**：需实现伪终端（PTY）模拟，确保交互式CLI功能正常。  
- **热度**：4条评论，1个👍，反映核心开发者对多Agent工作流的需求。  

---

## **5. Bug与稳定性**  
### **新报告 Issue #1077: "Error: invalid params, user name must be consistent"** ([链接](https://github.com/moltis-org/moltis/issues/1077))  
- **严重性**：中等（影响API调用流程）。  
- **现状**：无关联修复PR，需进一步复现和诊断。  
- **标签**：`bug`，需优先排查参数校验逻辑。  

---

## **6. 功能请求与路线图信号**  
- **高优先级需求**：  
  - **Issue #235**（Claude Code交互控制）：可能需底层PTY库改造，预计需较大开发量。  
  - **嵌入维度配置**（PR #1074）：已通过PR实现，可纳入下一版本默认功能。  
- **潜在方向**：  
  - 更多OpenAI兼容提供商集成（如Novita PR #451 的成功案例）。  

---

## **7. 用户反馈摘要**  
- **痛点**：  
  - 多Agent协作依赖Claude Code交互，但终端检测缺失导致功能受限（Issue #235）。  
  - API参数校验严格性引发错误（Issue #1077）。  
- **满意点**：  
  - 用户对Novita AI集成（PR #451）表示欢迎，认可多模型支持的价值。  

---

## **8. 待处理积压**  
- **长期未响应 Issue**：  
  - **Issue #235**（创建于2026-02-25，持续活跃）：需明确技术方案和排期。  
- **建议行动**：  
  - 维护者应优先评估PTY方案可行性，并同步社区进展。  

--- 

**总结**：Moltis 近期聚焦功能扩展（嵌入维度、Novita AI）和关键问题修复，但需加速解决交互控制瓶颈（Issue #235）以保障多Agent场景体验。

</details>

<details>
<summary><strong>QwenPaw</strong> — <a href="https://github.com/agentscope-ai/QwenPaw">agentscope-ai/QwenPaw</a></summary>

---

# **QwenPaw 项目日报 | 2026-05-28**

---

## 1. 今日速览

- QwenPaw 在今日保持较高活跃度，**Issues 42条（新开/活跃25条）**、**PRs 28条（待合并13条）**，并发布**2个新版本**（v1.1.9正式版及beta分支更新）。
- 社区讨论热点集中在**时间戳显示、文件上传、桌面端稳定性、智能体会话恢复**等核心功能体验问题。
- 多个关键 Bug 已提交修复 PR，如 Git 控制台窗口隐藏、WebSocket 连接问题等，项目正向解决方向推进。
- 新功能开发活跃，包括**Kimi K2.6模型支持、GitLab技能源集成、Xiaomi MiMo Token Plan内置提供商**等。

---

## 2. 版本发布

### **v1.1.9 (正式版)**
- **新增功能**：
  - [Tauri 2.x 桌面应用](https://github.com/agentscope-ai/QwenPaw/pull/3813)：原生支持 macOS & Windows 桌面版，提升跨平台体验。
  - [Web IDE 三面板布局](https://github.com/agentscope-ai/QwenPaw/pull/4655)：增强代码编辑器的文件树与多标签管理。
  - [GitLab 技能源支持](https://github.com/agentscope-ai/QwenPaw/pull/4719)：可直接从 GitLab 仓库加载技能文件。
  - [Xiaomi MiMo Token Plan 内置提供商](https://github.com/agentscope-ai/QwenPaw/pull/4722)：一键接入小米 AI 模型。
- **修复内容**：
  - 修复 Windows 下 `git.exe` 控制台窗口黑屏问题（Coding Mode）。
  - 修正 MiniMax-M2.5 XML 格式思考过程兼容性问题（Issue #4625）。
  - 优化 Feishu 频道线程回复支持（PR #4708）。
- **破坏性变更**：无重大 API 或配置变更。
- **迁移注意事项**：无需用户操作，所有功能向后兼容。

---

## 3. 项目进展

| PR 编号 | 标题 | 影响范围 |
|--------|------|----------|
| [#4728](https://github.com/agentscope-ai/QwenPaw/pull/4728) | 保留 assistant message 中的 reasoning_content | 消息完整性修复 |
| [#4720](https://github.com/agentscope-ai/QwenPaw/pull/4720) | 消息时间戳格式化 | 前端 UI 增强 |
| [#4682](https://github.com/agentscope-ai/QwenPaw/pull/4682) | Kimi K2.6 模型支持 | 模型注册表更新 |
| [#4719](https://github.com/agentscope-ai/QwenPaw/pull/4719) | GitLab 技能源集成 | 技能系统扩展 |

**总结**：今日合并 PR 覆盖模型支持、技能源、UI 交互、稳定性四大领域，显著提升产品完整性与用户体验。

---

## 4. 社区热点

### **🔥 评论最多 Issues**
- **[#2291](https://github.com/agentscope-ai/QwenPaw/issues/2291)**  
  *“Open Tasks: Come Contribute!”*  
  社区贡献者最活跃的协作入口，已有 **63条评论**，推动任务认领与进度同步。

- **[#4662](https://github.com/agentscope-ai/QwenPaw/issues/4662)**  
  *“增加每句话发送时间戳”*  
  **6条评论**，用户强烈希望对话界面增加时间标记，便于回溯与调试。

- **[#4712](https://github.com/agentscope-ai/QwenPaw/issues/4712)**  
  *“CLI 工具无法运行本地命令”*  
  **6条评论**，Windows 子进程通信问题，影响工具链集成体验。

---

## 5. Bug 与稳定性

| Issue/PR | 严重程度 | 状态 | 修复 PR |
|---------|----------|------|---------|
| [#4704](https://github.com/agentscope-ai/QwenPaw/issues/4704) | 高 | macOS 桌面崩溃（SIGSEGV） | ✅ [#4724](https://github.com/agentscope-ai/QwenPaw/pull/4724) |
| [#4712](https://github.com/agentscope-ai/QwenPaw/issues/4712) | 中 | CLI 工具 WebSocket 连接失败 | 🔄 进行中（需进一步验证） |
| [#4731](https://github.com/agentscope-ai/QwenPaw/issues/4731) | 低 | Edge 浏览器启动失败（退出码21） | 🔄 待分析 |

---

## 6. 功能请求与路线图信号

| 需求 | 关联 PR | 优先级 |
|------|---------|--------|
| **时间戳显示** | [#4720](https://github.com/agentscope-ai/QwenPaw/pull/4720) | 高（v1.1.9 已合并） |
| **动态文件大小限制** | [#4734](https://github.com/agentscope-ai/QwenPaw/pull/4734) | 中（待合并） |
| **RBAC 管理员权限** | [#4702](https://github.com/agentscope-ai/QwenPaw/issues/4702) | 企业需求（长期规划） |

---

## 7. 用户反馈摘要

- **痛点**：
  - 会话恢复混乱（[#4733](https://github.com/agentscope-ai/QwenPaw/issues/4733)）：重启后丢失上次会话，影响连续性。
  - 文件管理缺失（[#1492](https://github.com/agentscope-ai/QwenPaw/issues/1492)）：用户需手动查找上传文件，体验割裂。
- **满意点**：
  - Tauri 桌面应用（[#3813](https://github.com/agentscope-ai/QwenPaw/pull/3813)）获积极反馈，跨平台体验提升。
  - GitLab 技能源（[#4719](https://github.com/agentscope-ai/QwenPaw/pull/4719)）简化了技能部署流程。

---

## 8. 待处理积压

| Issue/PR | 状态 | 建议 |
|---------|------|------|
| [#4712](https://agentscope-ai/QwenPaw/issues/4712) | 未关闭 | 需优先验证子进程通信修复方案 |
| [#4731](https://agentscope-ai/QwenPaw/issues/4731) | 新报告 | 排查浏览器启动环境依赖 |
| [#4702](https://agentscope-ai/QwenPaw/issues/4702) | 长期需求 | 规划企业级权限模块 |

---

**总结**：QwenPaw 在功能迭代与稳定性修复双线并进，社区参与度高，但需持续关注会话恢复、工具链集成等核心痛点。v1.1.9 版本为近期重要里程碑，后续将聚焦企业化与用户体验优化。

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>librefang</strong> — <a href="https://github.com/librefang/librefang">librefang/librefang</a></summary>

---

# **librefang 项目日报 | 2026-05-28**

---

## **1. 今日速览**
- 过去24小时内，**Issues 更新13条**（新开/活跃8条，关闭5条），**PR 提交50条**（待合并38条，已合并/关闭12条），整体活跃度较高，尤其在运行时（`runtime`）和渠道适配器（`channels`）模块。
- 无新版本发布，但多个关键修复和功能增强 PR 已进入审查或开发阶段，表明团队正积极解决长期积压问题。
- CI 稳定性问题突出：Windows 环境因 `Instant::now()` 算术操作导致测试失败（[#5726](https://github.com/librefang/librefang/issues/5726)、[#5804](https://github.com/librefang/librefang/issues/5804)），已有 PR 提出修复（[#5808](https://github.com/librefang/librefang/pull/5808)）。

---

## **2. 版本发布**
- **无新版本发布**。

---

## **3. 项目进展**
### **合并/关闭的重要 PR**
| PR 编号 | 类型       | 内容摘要                                                                 | 链接 |
|--------|------------|--------------------------------------------------------------------------|------|
| [#5808](https://github.com/librefang/librefang/pull/5808) | Bug Fix   | 修复 Windows CI 中 `Instant::now() - Duration` 导致的 panic，解决多通道测试失败问题。 | [详情](#) |
| [#5815](https://github.com/librefang/librefang/pull/5815) | Feature   | 实现 `describe_image()` 功能，支持通过 Anthropic/OpenAI/Gemini 等 API 描述图像内容。 | [详情](#) |
| [#5814](https://github.com/librefang/librefang/pull/5814) | Feature   | 新增自托管 STT/TTS 自定义 URL 支持，兼容 OpenAI 兼容接口。                     | [详情](#) |

**进展总结**：  
- **核心功能增强**：图像理解（`describe_image`）、自托管语音服务（STT/TTS）的扩展显著提升了多模态交互能力。  
- **运行时安全加固**：多个 `tool_runner` 子模块（如 `cron`、`fs`、`agent`）修复了输入验证、权限控制、内存泄漏等问题，提升系统鲁棒性。  
- **CI 稳定性改进**：Windows 环境测试失败问题已定位并修复，减少平台差异性风险。

---

## **4. 社区热点**
### **最活跃的 Issues/PRs**
#### **🔥 高评论 Issue**
- **[#5804](https://github.com/librefang/librefang/issues/5804)**  
  **标题**: Main CI failure on PR #5801  
  **背景**: 因 Windows 环境下路径处理逻辑导致 CI 测试失败，影响 PR 合并流程。  
  **关联 PR**: [#5808](https://github.com/librefang/librefang/pull/5808) 已提交修复。

#### **📌 高频功能请求**
- **[#5739](https://github.com/librefang/librefang/issues/5739)**  
  **需求**: 用户希望 Telegram 发送的图片能通过 `describe_image()` 生成描述，而非仅下载为占位符。  
  **进展**: 已由 PR [#5815](https://github.com/librefang/librefang/pull/5815) 实现。

---

## **5. Bug 与稳定性**
| 严重程度 | Issue/PR 编号 | 问题描述                                                                 | 状态               | 修复 PR              |
|----------|----------------|--------------------------------------------------------------------------|--------------------|----------------------|
| ⚠️ 高    | [#5804](https://github.com/librefang/librefang/issues/5804) | Windows CI 路径处理失败，阻塞 PR 合并。                                   | 已修复（[#5808]）   | ✅ 已合并            |
| 🔧 中    | [#5726](https://github.com/librefang/librefang/issues/5726)   | 同 #5804，历史遗留问题。                                                 | 已修复（[#5808]）   | ✅ 已合并            |
| 🔍 低    | [#5795](https://github.com/librefang/librefang/issues/5795)   | Telegram/Matrix 消息重复格式化，显示原始 HTML 标签。                       | 待修复             | 无                  |

---

## **6. 功能请求与路线图信号**
- **图像理解（`describe_image`）**：  
  PR [#5815](https://github.com/librefang/librefang/pull/5815) 直接响应 [#5739](https://github.com/librefang/librefang/issues/5739)，预计下一版本集成。
- **自托管语音服务**：  
  PR [#5814](https://github.com/librefang/librefang/pull/5814) 提供对非 OpenAI 兼容服务的支持，符合用户对灵活性的诉求。
- **多任务协作（Kanban）**：  
  [#5745](https://github.com/librefang/librefang/issues/5745) 提议类似 Hermes-Agent 的任务看板功能，暂无 PR，需进一步讨论。

---

## **7. 用户反馈摘要**
- **痛点**：  
  - **渠道适配问题**：Telegram/Matrix 消息格式混乱（[#5795](https://github.com/librefang/librefang/issues/5795)），用户期望统一渲染逻辑。  
  - **配置体验差**：Feishu/Lark 界面缺少必要交互元素（[#5746](https://github.com/librefang/librefang/issues/5746)），影响部署效率。  
- **满意点**：  
  - 开发者对 `runtime` 模块的安全加固（如工具调用参数校验）表示认可，减少意外崩溃。

---

## **8. 待处理积压**
| Issue/PR 编号 | 问题描述                                                                 | 优先级 |
|--------------|--------------------------------------------------------------------------|--------|
| [#5745](https://github.com/librefang/librefang/issues/5745) | 多任务协作（Kanban）功能，用户强烈需求。                                 | 高     |
| [#5795](https://github.com/librefang/librefang/issues/5795) | 渠道消息重复格式化，影响用户体验。                                       | 中高   |
| [#5746](https://github.com/librefang/librefang/issues/5746) | Feishu/Lark 配置界面缺失关键字段。                                       | 中     |

---

**总结**：  
librefang 在功能扩展（图像、语音）和运行时安全方面取得显著进展，但需持续关注 CI 稳定性和渠道适配一致性。建议优先处理多任务协作（Kanban）和消息渲染问题，以提升用户体验。

</details>

<details>
<summary><strong>openfang</strong> — <a href="https://github.com/RightNow-AI/openfang">RightNow-AI/openfang</a></summary>

# **Openfang 项目日报 (2026-05-28)**  

---

## **1. 今日速览**  
过去24小时内，Openfang 保持中等活跃度：  
- **3个新 PR 提交**（全部待合并），聚焦功能扩展和基础设施改进。  
- **无 Issues 更新**，表明当前问题积压稳定，但需关注待合并 PR 的进展。  
- **无新版本发布**，团队可能处于功能开发或测试阶段。  
整体状态健康，社区贡献者（如 @mvanhorn）持续推动核心功能迭代。  

---

## **2. 版本发布**  
**无新版本发布**。  

---

## **3. 项目进展**  
### **关键 PR 推进**  
1. **[PR #1217](https://github.com/RightNow-AI/openfang/pull/1217)**  
   - **功能**：新增 `/download` 命令支持 Agent 工作区文件列表与下载端点。  
   - **关联 Issue**：[Closes #1070](https://github.com/RightNow-AI/openfang/issues/1070)。  
   - **意义**：提升 Agent 对文件操作的支持能力，增强自动化场景实用性。  

2. **[PR #1216](https://github.com/RightNow-AI/openfang/pull/1216)**  
   - **功能**：集成 `codex_app_server` LLM 驱动及提供商注册模块。  
   - **关联 Issue**：[Closes #1033](https://github.com/RightNow-AI/openfang/issues/1033)。  
   - **意义**：为多 LLM 提供商支持奠定基础，扩展 AI 服务灵活性。  

3. **[PR #1215](https://github.com/RightNow-AI/openfang/pull/1215)**  
   - **功能**：添加 Homebrew Tap 并实现 CI 自动发布公式。  
   - **关联 Issue**：[Closes #889](https://github.com/RightNow-AI/openfang/issues/889)。  
   - **意义**：简化 macOS 用户安装流程，提升开源生态友好度。  

**总结**：本周聚焦 **文件管理、LLM 集成、包分发优化**，核心功能链式推进。  

---

## **4. 社区热点**  
- **最活跃 PR**：#1217（文件下载功能）和 #1216（LLM 驱动）均获零初始反馈，需后续观察用户测试响应。  
- **潜在需求信号**：Homebrew 集成 (#1215) 反映用户对便捷安装的诉求，可能吸引更多开发者参与。  

---

## **5. Bug 与稳定性**  
**无新 Bug 报告**，历史问题未提及回归或崩溃。  

---

## **6. 功能请求与路线图信号**  
- **已覆盖需求**：  
  - 文件操作 (#1070)、LLM 多提供商支持 (#1033) 均被 PR 直接解决。  
  - Homebrew 自动化 (#889) 显著降低用户门槛。  
- **待验证需求**：  
  - 若 #1217 落地，可进一步探索 Agent 与外部存储（如 S3）的深度集成。  

---

## **7. 用户反馈摘要**  
- **痛点**：  
  - 文件管理功能缺失 (#1070) 是早期高频需求，本次 PR 提供了解决方案。  
  - LLM 提供商单一 (#1033) 限制企业定制化，新驱动将缓解此问题。  
- **满意度**：  
  - 基础设施改进（如 Homebrew）未直接涉及用户体验，但长期利好社区增长。  

---

## **8. 待处理积压**  
- **长期未响应 Issue**：  
  - [Issue #889](https://github.com/RightNow-AI/openfang/issues/889)（Homebrew 集成）已通过 PR #1215 解决，建议标记为“已完成”。  
- **待跟进 PR**：  
  - #1215、#1216、#1217 均需维护者尽快合并，避免阻塞下游依赖。  

--- 

**数据结论**：Openfang 近期以功能扩展为主，社区贡献积极，但需加速 PR 合并以提升迭代效率。

</details>

<details>
<summary><strong>AstrBot</strong> — <a href="https://github.com/AstrBotDevs/AstrBot">AstrBotDevs/AstrBot</a></summary>

---

# **AstrBot 项目日报（2026-05-28）**

---

## 1. 今日速览
- 过去24小时内，AstrBot 社区活跃度高，共新增/更新 **36个 Issues**（含 21 条新开/活跃）、**32个 PR**（含 19 条已合并），无新版本发布。
- 核心问题集中在 **插件市场、WebUI 稳定性、平台适配（QQ/飞书）、提供商兼容性**，开发者与用户协作紧密推进修复。
- 整体项目处于 **高活跃修复期**，多个关键 Bug 已有 PR 跟进，社区反馈积极。

---

## 2. 版本发布
> 无新版本发布。

---

## 3. 项目进展
### ✅ 重要合并 PR：
- **[PR #8376](https://github.com/AstrBotDevs/AstrBot/pull/8376)**  
  修复了 QQ 官方机器人发送多文件时仅发送第一个文件的逻辑，解决了群聊消息分段问题，提升 QQ 平台稳定性。
  
- **[PR #8328](https://github.com/AstrBotDevs/AstrBot/pull/8328)**  
  修正 Anthropic API `tool_choice` 参数格式错误，兼容 OpenAI 和 Anthropic 规范，避免 400 错误。

- **[PR #8369](https://github.com/AstrBotDevs/AstrBot/pull/8369)**  
  WebUI 插件详情页增加“直接访问”按钮，优化嵌入页面高度，改善用户体验。

- **[PR #8388](https://github.com/AstrBotDevs/AstrBot/pull/8388)**  
  修复插件详情页缺失的国际化翻译键（`subCommandsCount`），解决界面显示 `[MISSING]` 问题。

---

## 4. 社区热点
### 🔥 评论最多 Issues：
- **[Issue #8381](https://github.com/AstrBotDevs/AstrBot/issues/8381)**  
  **插件发布**：`astrbot_plugin_random_reply`（禁止机器人无限对话），支持多机器人群聊互动控制，获 5 条评论，用户期待更灵活的配置选项。

- **[Issue #8361](https://github.com/AstrBotDevs/AstrBot/issues/8361)**  
  **Bug 报告**：MiMo 模型在普通对话中重复调用 `send_message_to_user`，导致消息刷屏，已有 PR 修复中。

- **[Issue #8319](https://github.com/AstrBotDevs/AstrBot/issues/8319)**  
  **API 兼容性问题**：Anthropic 工具选择参数格式错误，影响第三方提供商集成，开发者正在同步修复。

---

## 5. Bug 与稳定性
| 严重性 | Issue/PR | 描述 | 状态 |
|-------|----------|------|------|
| P0 | [#8319](https://github.com/AstrBotDevs/AstrBot/issues/8319) | Anthropic API 参数格式错误 | ✅ [PR #8328](https://github.com/AstrBotDevs/AstrBot/pull/8328) 已合并 |
| P1 | [#8361](https://github.com/AstrBotDevs/AstrBot/issues/8361) | MiMo 模型消息重复发送 | 🔄 修复中（PR 未公开） |
| P1 | [#8210](https://github.com/AstrBotDevs/AstrBot/issues/8210) | QQ 多文件发送异常 | ✅ [PR #8376](https://github.com/AstrBotDevs/AstrBot/pull/8376) 已合并 |
| P2 | [#8374](https://github.com/AstrBotDevs/AstrBot/issues/8374) | WebUI 404 fallback 白屏 | 🔄 修复中（PR 未公开） |

---

## 6. 功能请求与路线图信号
### 📌 新功能提案：
- **知识库优化**（[#8256](https://github.com/AstrBotDevs/AstrBot/issues/8256)）：  
  用户建议支持动态调整知识库文件上限、API 操作增删文件，已有 PR 讨论中（如 [#8363](https://github.com/AstrBotDevs/AstrBot/pull/8363) 引入 Token 阈值压缩）。

- **分段回复自定义符号**（[#8313](https://github.com/AstrBotDevs/AstrBot/issues/8313)）：  
  针对非流式平台的分段符号可配置，可能纳入下一版本。

- **Xiaomi Mimo 提供商**（[#8312](https://github.com/AstrBotDevs/AstrBot/issues/8312)）：  
  用户强烈需求，已有 PR [#7744](https://github.com/AstrBotDevs/AstrBot/pull/7744) 实现基础支持。

---

## 7. 用户反馈摘要
- **痛点**：  
  - 多机器人群控插件需求旺盛（如 [#8381](https://github.com/AstrBotDevs/AstrBot/issues/8381)），但部分用户抱怨强制密码大小写规则（[#8373](https://github.com/AstrBotDevs/AstrBot/issues/8373)）。
  - QQ/飞书平台历史记录管理混乱（[#8386](https://github.com/AstrBotDevs/AstrBot/issues/8386)），影响用户体验。

- **满意点**：  
  - 开发者响应迅速，多个 Bug 当日有 PR 跟进（如 Anthropic 参数修复）。
  - 插件市场生态活跃，新插件提交频繁（如 [#8384](https://github.com/AstrBotDevs/AstrBot/issues/8384)、[#8383](https://github.com/AstrBotDevs/AstrBot/issues/8383)）。

---

## 8. 待处理积压
- **长期未响应 Issue**：  
  - **WebUI 404 fallback 白屏**（[#8374](https://github.com/AstrBotDevs/AstrBot/issues/8374)）  
  - **MiMo 推理模型上下文注入**（[#8267](https://github.com/AstrBotDevs/AstrBot/issues/8267)）  
  - **知识库 API 操作**（[#8256](https://github.com/AstrBotDevs/AstrBot/issues/8256)）  

---

**总结**：AstrBot 近期开发节奏紧凑，社区反馈驱动性强，重点修复了平台适配、提供商兼容性和 WebUI 稳定性问题，同时积极响应用户对插件生态和功能扩展的需求，项目健康度良好。

</details>

---
*本日报由 [Big Model Radar](https://github.com/ivanweng2077/big_model_radar) 自动生成。*