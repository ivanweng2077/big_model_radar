# OpenClaw 生态日报 2026-05-25

> Issues: 500 | PRs: 500 | 覆盖项目: 15 个 | 生成时间: 2026-05-25 02:51 UTC

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

# **OpenClaw 项目日报 - 2026-05-25**

---

## 1. 今日速览
- OpenClaw 今日活跃度极高：过去24小时共更新 **500条 Issues**（新开/活跃463条，关闭37条）和 **500条 PR**（待合并378条，已合并/关闭122条），同时发布 **2个新版本**（v2026.5.24-beta.2）。
- 核心功能进展集中在 **网关性能优化、消息通道标准化、安全加固**，以及 **Codex工具链修复**。
- 社区讨论热点聚焦于 **多平台支持（Linux/Windows/Android）、消息通道会话管理、权限控制**，以及 **Telegram/Discord/Slack等插件的会话同步问题**。

---

## 2. 版本发布
### **v2026.5.24-beta.2**
#### 主要变更：
- **iMessage 表情反应支持**：  
  新增 `👍`（允许一次）和 `👎`（拒绝）作为审批结果，读取 `channels.imessage.allowFrom` 白名单配置，支持 `/approve <id> allow-always` 手动覆盖。  
  [GitHub 链接](https://github.com/openclaw/openclaw/releases/tag/v2026.5.24-beta.2)

- **网关性能优化**：  
  复用稳定频道目录读取，避免重复边界检查，并轮换 CPU 性能监控文件，防止基准测试累积异常数据。  
  [GitHub 链接](https://github.com/openclaw/openclaw/releases/tag/v2026.5.24-beta.2)

#### 破坏性变更：无  
#### 迁移注意事项：无

---

## 3. 项目进展
### 关键 PR 推进：
- **[PR #86216](https://github.com/openclaw/openclaw/pull/86216)**  
  Telegram/Codex 预压缩路径恢复陈旧线程绑定，避免中断分派前崩溃。
  
- **[PR #85958](https://github.com/openclaw/openclaw/pull/85958)**  
  在 Codex 边界强制压缩失败，修复运行时压缩逻辑与 OpenClaw 保护机制的冲突。

- **[PR #86296](https://github.com/openclaw/openclaw/pull/86296)**  
  引入 ClaWorks 产品层，整合白标化（Stage A）与 CLI 产品化，涉及 185 次提交。

- **[PR #85341](https://OpenClaw 项目日报 - 2026-05-25**

---

## 1. 今日速览
- **高活跃度**：过去24小时共处理 **500条 Issues**（新开/活跃463条，关闭37条）和 **500条 PR**（待合并378条，已合并/关闭122条），同时发布 **2个新版本**（v2026.5.24-beta.2）。
- **核心进展**：聚焦 **网关性能优化（如复用稳定目录读取）、消息通道标准化（Telegram/Discord/Slack会话同步）、安全加固（审批权限控制）**，以及 **Codex工具链修复**。
- **社区热点**：用户最关注 **多平台支持（Linux/Windows/Android）、消息会话管理（如WhatsApp消息补发）、权限隔离（Masked Secrets）**，以及 **Telegram/Discord/Slack插件兼容性**。

---

## 2. 版本发布
### **v2026.5.24-beta.2**
#### 主要变更：
- **iMessage 表情反应审批**：  
  新增 `👍`（允许一次）和 `👎`（拒绝）作为审批结果，读取 `channels.imessage.allowFrom` 白名单，支持 `/approve <id> allow-always` 手动覆盖。  
  [GitHub 链接](https://github.com/openclaw/openclaw/releases/tag/v2026.5.24-beta.2)

- **网关性能优化**：  
  复用稳定频道目录读取，避免重复边界检查，并轮换 CPU 性能监控文件，防止基准测试累积异常数据。  
  [GitHub 链接](https://github.com/openclaw/openclaw/releases/tag/v2026.5.24-beta.2)

#### 破坏性变更：无  
#### 迁移注意事项：无

---

## 3. 项目进展
### 关键 PR 推进：
- **[PR #86216](https://github.com/openclaw/openclaw/pull/86216)**  
  Telegram/Codex 预压缩路径恢复陈旧线程绑定，避免中断分派前崩溃。

- **[PR #85958](https://github.com/openclaw/openclaw/pull/85958)**  
  在 Codex 边界强制压缩失败，修复运行时压缩逻辑与 OpenClaw 保护机制的冲突。

- **[PR #86296](https://github.com/openclaw/openclaw/pull/86296)**  
  引入 ClaWorks 产品层，整合白标化（Stage A）与 CLI 产品化，涉及 185 次提交。

- **[PR #85341](https://github.com/openclaw/openclaw/pull/85341)**  
  移除 Pi 架构，将 Agent/Runtime 功能内化为 OpenClaw 核心，解决模型/SDK 依赖问题。

---

## 4. 社区热点
### 评论最多 Issues/PRs：
- **[Issue #75](https://github.com/openclaw/openclaw/issues/75)**  
  **Linux/Windows Clawdbot Apps**（106条评论）：用户强烈请求跨平台支持（macOS/iOS/Android），目前仅支持 macOS/iOS/移动端。

- **[PR #86297](https://github.com/openclaw/openclaw/pull/86297)**  
  Telegram Android 文档警告：编辑器锁住输入框，阻塞 `/steer` 等中断命令。

- **[Issue #58514](https://github.com/openclaw/openclaw/issues/58514)**  
  Google Chat 群组消息静默忽略（DM正常），影响企业用户场景。

---

## 5. Bug 与稳定性
### 严重 Bug 及修复状态：
| Issue | 描述 | 严重度 | Fix PR |
|-------|------|--------|--------|
| **[#86214](https://github.com/openclaw/openclaw/issues/86214)** | Codex 工具请求中途断开（大型日志文件导致） | ⚠️ 会话丢失 | [#86216](https://github.com/openclaw/openclaw/pull/86216) |
| **[#86184](https://github.com/openclaw/openclaw/issues/86184)** | Telegram 工具成功后返回通用错误提示 | ⚠️ 用户体验 | 待跟进 |
| **[#83959](https://github.com/openclaw/openclaw/issues/83959)** | Codex 启动重试耗尽资源 | 🔴 崩溃循环 | 无 |

---

## 6. 功能请求与路线图信号
### 高优先级需求：
- **多平台支持**（Linux/Windows/Android）：[#75](https://github.com/openclaw/openclaw/issues/75) → 可能纳入下一版本。
- **消息会话补发**（WhatsApp）：[#50093](https://github.com/openclaw/openclaw/issues/50093) → 需验证后合并。
- **权限控制**（Masked Secrets）：[#10659](https://github.com/openclaw/openclaw/issues/10659) → 已有 PR 进行中。

---

## 7. 用户反馈摘要
- **痛点**：  
  - 消息通道一致性（Telegram/Discord/Slack会话同步失败）[#86184](https://github.com/openclaw/openclaw/issues/86184)。  
  - 权限泄露风险（API密钥明文存储）[#10659](https://github.com/openclaw/openclaw/issues/10659)。
- **满意点**：  
  iMessage 表情审批功能（v2026.5.24-beta.2）被积极采用。

---

## 8. 待处理积压
| Issue/PR | 状态 | 备注 |
|----------|-------|------|
| **[#86184](https://github.com/openclaw/openclaw/issues/86184)** | 未修复 | Telegram 工具后返回通用错误，需修复会话路由逻辑。 |
| **[#83959](https://github.com/openclaw/openclaw/issues/83959)** | 无 PR | Codex 启动重试超时，需增加熔断机制。 |
| **[#75](https://github.com/openclaw/openclaw/issues/75)** | 长期开放 | 跨平台支持，需评估技术方案。 |

---

**总结**：OpenClaw 近期在性能、安全、多平台支持上进展显著，但需优先解决会话一致性与权限控制问题，社区反馈积极，版本迭代节奏健康。

---

## 横向生态对比

---

### **1. 生态全景**  
2026年5月，个人AI助手与自主智能体开源生态呈现 **“两极分化+快速迭代”** 态势：  
- **头部项目（如OpenClaw、NanoClaw）** 以高频更新（日均Issues/PR超500条）和版本发布为标志，反映社区对性能优化、安全加固和多平台支持的强烈需求；  
- **长尾项目（如TinyClaw、ZeptoClaw）** 则聚焦功能修复和稳定性，社区反馈较少但技术债务清理积极；  
- **共同趋势**：多通道集成（Telegram/Discord/Slack）、权限控制（Masked Secrets）、工具链健壮性（Codex/MCP）是跨项目核心诉求。

---

### **2. 各项目活跃度对比**
| 项目名称          | Issues (今日) | PRs (今日) | Release | 健康度评估               |
|-------------------|---------------|------------|----------|--------------------------|
| **OpenClaw**      | 463活跃      | 378待合并  | v2026.5.24-beta.2 | ⭐⭐⭐⭐⭐（高活跃度，强社区驱动） |
| **NanoClaw**      | 186活跃      | 322待合并  | 无       | ⭐⭐⭐⭐（开发中，功能扩展）     |
| **Zeroclaw**      | 47活跃       | 45待合并   | 无       | ⭐⭐⭐（基础设施巩固阶段）    |
| **PicoClaw**      | 4活跃        | 10待合并   | Nightly  | ⭐⭐（架构升级期）         |
| **IronClaw**      | 18活跃       | 49待合并   | 无       | ⭐⭐⭐（安全与Reborn集成）   |
| **LobsterAI**     | 0            | 14已合并   | 无       | ⭐⭐⭐⭐（稳定性修复主导）   |
| **QwenPaw**      | 9活跃        | 5待合并    | 无       | ⭐⭐（UI/工具链优化）      |

---

### **3. OpenClaw在生态中的定位**
#### **优势**  
- **性能与安全标杆**：  
  - 网关优化（复用目录读取、CPU监控轮换）、消息通道标准化（iMessage表情审批）、权限控制（`channels.imessage.allowFrom`白名单）等设计被多个项目借鉴。  
- **社区规模**：  
  - 日均Issues/PR超500条，远超同类（如NanoClaw仅14条），反映开发者生态的聚合效应。  

#### **技术路线差异**  
- **多模态集成**：支持Telegram/Discord/Slack会话同步、WhatsApp补发等，而多数项目仅专注单一平台。  
- **企业级能力**：Codex工具链修复、ClaWorks白标化等，适合生产环境部署。

---

### **4. 共同关注的技术方向**
| 需求                | 涉及项目                                                                 | 具体诉求                                                                 |
|---------------------|--------------------------------------------------------------------------|--------------------------------------------------------------------------|
| **多通道集成**      | OpenClaw, NanoClaw, IronClaw                                            | 统一消息路由、会话同步、跨平台兼容性（如Telegram DM静默忽略问题）             |
| **权限控制**        | OpenClaw, NanoClaw, Moltis                                               | Masked Secrets、API密钥加密存储、子代理异步审批门控                          |
| **工具链健壮性**    | OpenClaw, NanoClaw, QwenPaw                                             | Codex压缩逻辑、MCP上下文传递、OpenAI兼容API工具ID一致性                     |
| **稳定性修复**      | Zeroclaw, LobsterAI, AstrBot                                             | Cron任务持久化、消息队列竞争条件、适配器连接池耗尽                           |

---

### **5. 差异化定位分析**
| 项目          | 功能侧重                  | 目标用户               | 技术架构亮点                     |
|---------------|---------------------------|------------------------|----------------------------------|
| **OpenClaw**  | 多通道+企业级安全         | 企业开发者/运维团队     | 网关性能优化、ClaWorks白标化      |
| **NanoClaw**  | Agent协作总线+工具链增强    | 复杂场景开发者         | Reborn集成、多数据库会话共享       |
| **Zeroclaw**  | 基础设施+MCP扩展           | 全栈工程师            | Mastodon/Twilio/Rocket.Chat通道   |
| **IronClaw**  | 安全审计+Reborn           | 合规敏感领域开发者     | ActionRecord强制审计、子代理启动机制 |
| **LobsterAI** | 用户体验+消息队列          | 终端用户/协作工作者    | AI回复期间连续输入、跨Agent搜索    |
| **AstrBot**   | 多平台适配器+文件安全      | 机器人开发者           | QQ分段回复、Telegram连接池恢复     |

---

### **6. 社区热度与成熟度分层**
#### **快速迭代阶段**  
- **OpenClaw**：日均500+ Issues/PR，版本发布，社区驱动型项目。  
- **NanoClaw**：Agent协作总线、多账号微信支持，功能扩展活跃。  
- **IronClaw**：安全与Reborn集成，架构级改进。  

#### **质量巩固阶段**  
- **Zeroclaw**：MCP工具链、多通道扩展，基础设施优化。  
- **LobsterAI**：消息队列、数据库事务，稳定性修复主导。  
- **TinyClaw**：长期未更新，需警惕技术债务。  

---

### **7. 值得关注的趋势信号**
#### **行业趋势提炼**  
1. **多通道集成**：  
   - 从OpenClaw到NanoClaw，用户对Telegram/Discord/Slack会话同步、WhatsApp补发需求激增，反映 **跨平台工作流** 成为刚需。  
2. **权限与数据治理**：  
   - Masked Secrets（OpenClaw/Moltis）、ActionRecord审计（IronClaw）表明 **企业级安全** 是开发者痛点。  
3. **工具链标准化**：  
   - Codex压缩（OpenClaw）、MCP上下文传递（librefang）显示 **可观测性** 和 **协议兼容性** 优先级提升。  
4. **协作能力**：  
   - Agent协作总线（NanoClaw）、消息队列（LobsterAI）指向 **多智能体协同** 场景爆发。  

#### **对开发者的参考价值**  
- **架构建议**：  
  - 若项目涉及多通道或安全，参考OpenClaw的`channels.*`配置模式；  
  - 复杂工具链优先采用IronClaw的ActionRecord审计机制；  
  - 协作场景可借鉴NanoClaw的Agent总线设计。  
- **风险提示**：  
  - 长尾项目（如ZeptoClaw）需警惕维护停滞，建议通过Issue #553等积压项推动社区参与。  

--- 

**总结**：2026年5月的生态呈现 **“头部引领，长尾补位”**，OpenClaw凭借性能与安全成为标杆，而差异化项目（如IronClaw、NanoClaw）在细分领域快速崛起。开发者应关注多通道集成、权限控制和工具链标准化三大方向，避免重复造轮子。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

---

# **NanoBot 项目日报（2026-05-25）**

---

## **1. 今日速览**
- 过去24小时内，NanoBot 保持较高活跃度：**5条新/活跃 Issues**、**19条 PR**（含12条待合并），无新版本发布。
- 核心开发集中在**工具链增强**（如循环检测、Dream系统优化）、**多代理协作**和**Provider配置扩展**，体现对复杂场景的持续迭代。
- 社区讨论热点围绕**大模型行为控制**（如循环调用、温度参数定制）和**用户体验改进**（如WebUI交互）。

---

## **2. 版本发布**
- 无新版本发布。

---

## **3. 项目进展**
### **关键合并/关闭 PR**
| PR # | 类型       | 内容概要                                                                 | 链接 |
|------|------------|--------------------------------------------------------------------------|------|
| #3984 | `fix`     | 修复OpenAI兼容API（如GLM-4.7/Kimi 2.6）中`tool_call_id`与`tool_result`不一致问题 | [详情](https://github.com/HKUDS/nanobot/pull/3984) |
| #3985 | `feat`    | 新增通用工具级循环检测与速率限制硬阻断（Loop Guard v2.0）                  | [详情](https://github.com/HKUDS/nanobot/pull/3985) |
| #3990 | `refactor`| 将Dream系统的两阶段内存合并为单阶段，提升执行效率                           | [详情](https://github.com/HKUDS/nanobot/pull/3990) |
| #3992 | `feat`    | 实现跨代理实例消息总线（Agent Collaboration），支持多代理通信               | [详情](https://github.com/HKUDS/nanobot/pull/3992) |

**推进意义**：  
- **稳定性**：解决工具ID不一致问题（#3984）和循环调用防护（#3985），显著降低生产环境风险。  
- **架构升级**：Dream系统重构（#3990）和跨代理通信（#3992）为分布式任务处理奠定基础。  

---

## **4. 社区热点**
### **最活跃 Issues/PRs**
#### **🔥 Issue #3986: 通用工具级循环检测与速率限制护栏**  
[链接](https://github.com/HKUDS/nanobot/issues/3986)  
- **诉求**：用户反馈大模型频繁陷入重复调用（如`grep`、`list_dir`等），现有机制仅覆盖部分工具。  
- **关联PR**：#3985已提交解决方案，通过硬阻断策略防止无效循环。

#### **🔧 PR #3994: Provider配置注册表驱动化**  
[链接](https://github.com/HKUDS/nanobot/pull/3994)  
- **背景**：Bedrock等Provider需动态传递`region`/`profile`等字段，当前配置方式僵化。  
- **影响**：提升多Provider兼容性，简化WebUI渲染逻辑。

---

## **5. Bug 与稳定性**
| 严重性 | Issue/PR | 描述                                                                 | 状态          |
|--------|----------|----------------------------------------------------------------------|---------------|
| 高     | #3980    | OpenAI兼容API中`tool_call_id`与`tool_result`不匹配（已修复，见#3984） | ✅ Fixed       |
| 中     | #3993    | Anthropic要求内容块必须声明`type`，否则转换失败                       | 🔄 待处理      |

---

## **6. 功能请求与路线图信号**
| 需求类型           | 提案Issue/PR | 潜在影响                          | 优先级 |
|--------------------|--------------|-----------------------------------|--------|
| 子代理采样温度定制 | #3969 → #3975 | 支持不同任务差异化思维模式         | 高     |
| 实时学习机制增强   | #3973        | 解决Dream系统饥饿问题与数据时效性  | 中高   |
| 跨代理消息总线     | #3992        | 实现多代理协同工作流              | 高     |

---

## **7. 用户反馈摘要**
- **痛点**：  
  - 工具重复调用（如`grep`、`read_file`）导致资源浪费（#3986）。  
  - Dream系统依赖静态历史文件，缺乏实时学习能力（#3973）。  
- **满意点**：  
  - WebUI交互优化（如模型预设切换，#3977）提升操作效率。  
  - MCP预设管理（#3979）简化第三方服务集成。

---

## **8. 待处理积压**
| Issue/PR | 状态   | 提醒事项                                                                 |
|----------|--------|--------------------------------------------------------------------------|
| #3993    | OPEN   | Anthropic内容块类型强制要求，需适配`_convert_user_content`逻辑             |
| #3973    | OPEN   | Dream系统需引入增量学习或外部数据源，可能涉及架构调整                     |

---

**总结**：NanoBot 在工具链健壮性和多代理协作方面取得显著进展，同时社区反馈推动了对大模型行为控制的深度优化。建议优先处理Anthropic兼容性问题（#3993）并评估Dream系统重构的可行性。

</details>

<details>
<summary><strong>Zeroclaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

---

# **Zeroclaw 项目日报 | 2026-05-25**

---

## 1. **今日速览**
- **活跃度**：过去24小时内，Zeroclaw 项目共更新 **50条 Issues（47活跃+3关闭）** 和 **50条 PR（45待合并+5已合并）**，显示社区开发活动持续活跃。
- **问题聚焦**：核心议题围绕 MCP 工具链、多模态通道集成、配置安全性和运行时稳定性，反映项目在扩展性与可靠性上的重点投入。
- **无版本发布**：未发布新版本，但多个功能修复和增强已进入代码审查阶段。

---

## 2. **版本发布**
> 无新版本发布。

---

## 3. **项目进展**
### ✅ 合并/关闭的 PR
| PR # | 类型 | 关键进展 |
|------|------|----------|
| [#6893](https://github.com/zeroclaw-labs/zeroclaw/pull/6893) | 功能（XL） | 新增多数据库会话后端（Postgres/Oracle/MySQL/Db2），支持多 Agent 集群状态共享。 |
| [#6833](https://github.com/zeroclaw-labs/zeroclaw/pull/6833) | 功能（S） | 集成 Jina AI 作为 Web Search Provider，扩展搜索能力。 |
| [#6897](https://github.com/zeroclaw-labs/zeroclaw/pull/6897) | 修复（M） | Cron 任务持久化改进，手动执行失败时正确标记为“降级”状态。 |
| [#6882](https://github.com/zeroclaw-labs/zeroclaw/pull/6882) | 修复（S） | 上下文压缩时清理媒体标记，避免截断破坏数据完整性。 |

**总结**：本周推进了基础设施扩展（多数据库）、工具链增强（Jina AI）、任务调度优化（Cron 状态持久化）和运行时稳定性（媒体标记处理），显著提升了生产环境适用性。

---

## 4. **社区热点**
### 🔥 高互动 Issues/PRs
#### **RFC: Work Lanes, Board Automation, and Label Cleanup**  
[#6808](https://github.com/zeroclaw-labs/zeroclaw/issues/6808)  
- **评论数**：6条，涉及工作流自动化、标签清理和看板管理，是治理层讨论最集中的议题之一。  
- **诉求**：用户希望减少维护者手动操作负担，通过轻量级 PR 分路和自动化看板提升协作效率。

#### **tool_filter_groups is a no-op for real MCP tools**  
[#6699](https://github.com/zeroclaw-labs/zeroclaw/issues/6699)  
- **评论数**：6条，暴露 MCP 工具链配置缺陷，影响工具过滤逻辑。  
- **背景**：`tool_filter_groups` 配置未生效，导致 MCP 工具无法按预期被过滤，需紧急修复。

---

## 5. **Bug 与稳定性**
### ⚠️ 严重 Bug 及修复状态
| Issue # | 严重度 | 描述 | 修复状态 |
|--------|--------|------|----------|
| [#6699](https://github.com/zeroclaw-labs/zeroclaw/issues/6699) | 高 | MCP 工具过滤失效，影响工具链安全性 | 🔄 进行中（PR 待合并） |
| [#6302](https://github.com/zeroclaw-labs/zeroclaw/issues/6302) | 高 | Gemini 模型因历史序列违反被拒绝 | 🔄 进行中（PR 待合并） |
| [#6472](https://github.com/zeroclaw-labs/zeroclaw/issues/6472) | 中 | Gateway 无法使用 PostgreSQL 连接池 | 🔄 进行中（PR 待合并） |
| [#5903](https://github.com/zeroclaw-labs/zeroclaw/issues/5903) | 高 | `daemon` 心跳泄漏孤儿进程 | 🔄 进行中（PR 待合并） |

**趋势**：高优先级 Bug 均已有 PR 跟进，但需尽快合并以降低生产风险。

---

## 6. **功能请求与路线图信号**
### 🚀 新功能提案及关联 PR
| Issue # | 需求 | 关联 PR | 进度 |
|--------|------|---------|------|
| [#6423](https://github.com/zeroclaw-labs/zeroclaw/issues/6423) | Mastodon 通道（ActivityPub） | 🔄 进行中 | 自组织网络集成 |
| [#6427](https://github.com/zeroclaw-labs/zeroclaw/issues/6427) | Twilio SMS 通道 | 🔄 进行中 | 短信通信支持 |
| [#6435](https://github.com/zeroclaw-labs/zeroclaw/issues/6435) | Rocket.Chat 通道 | 🔄 进行中 | 开源 Slack 替代方案 |
| [#6437](https://github.com/zeroclaw-labs/zeroclaw/issues/6437) | Zulip 通道 | 🔄 进行中 | 长轮询事件支持 |

**分析**：多通道扩展（Mastodon/Twilio/Rocket/Zulip）是近期重点，满足开发者对去中心化、企业级通信的需求，可能纳入 v0.8.x 路线图。

---

## 7. **用户反馈摘要**
### 📌 痛点与满意度
- **痛点**：  
  - **MCP 工具链配置失效**（[#6699](https://github.com/zeroclaw-labs/zeroclaw/issues/6699)）：用户抱怨工具过滤功能未生效，影响安全策略执行。  
  - **Cron 输出路由缺失**（[#6647](https://github.com/zeroclaw-labs/zeroclaw/issues/6647)）：Telegram 等通道未接收定时任务结果，需增强日志分发。  
- **满意点**：  
  - **多数据库支持**（[#6893](https://github.com/zeroclaw-labs/zeroclaw/pull/6893)）：企业用户赞赏跨节点会话持久化能力。  
  - **文档完善**（[#6898](https://github.com/zeroclaw-labs/zeroclaw/pull/6898)）：Signal/WhatsApp 配置指南获积极反馈。

---

## 8. **待处理积压**
### ⏳ 长期未响应项
| Issue # | 类型 | 状态 | 建议 |
|--------|------|------|------|
| [#6721](https://github.com/zeroclaw-labs/zeroclaw/issues/6721) | Bug (高) | 已认领但未合并 | 需优先解决 `deferred_loading` + `webhook` 静默超时问题 |
| [#6723](https://github.com/zeroclaw-labs/zeroclaw/issues/6723) | Bug (中) | 已认领 | OpenAI 硬编码超时问题，影响配置灵活性 |
| [#6074](https://github.com/zeroclaw-labs/zeroclaw/issues/6074) | 审计 (高) | 进行中 | 批量回滚后恢复代码审计，需跟踪修复 |

---

**总结**：Zeroclaw 本周保持高强度开发节奏，尤其在工具链稳定性、多通道集成和基础设施扩展上取得进展。需重点关注 MCP 工具链 Bug 和通道功能 PR 的快速合并，同时持续监控长期积压项的解决进度。

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

---

# **PicoClaw 项目日报（2026-05-25）**

---

## 1. **今日速览**
- **活跃度**：项目保持较高开发节奏，过去24小时共处理 **14项更新**（4 Issues + 10 PRs），含 **1个新版本发布**（Nightly Build）。  
- **关键进展**：Agent协作总线、Cron工具修复、多账号微信支持等核心功能推进；同时解决工具安全策略和路径校验等稳定性问题。  
- **社区参与**：Issue #28（LM Studio连接请求）和PR #2937（Agent协作）引发较多讨论，显示用户对多模态交互和协作能力的强烈需求。

---

## 2. **版本发布**
- **v0.2.9-nightly.20260525.ab6d3946** ([Release Notes](https://github.com/sipeed/picoclaw/releases/tag/v0.2.9-nightly.20260525.ab6d3946))  
  - **内容**：自动化构建版本，包含未合并的main分支最新改动（如Agent协作总线、Cron工具修复等）。  
  - **注意**：标注为“可能不稳定”，建议生产环境谨慎使用。  
  - **迁移提示**：无破坏性变更，但需测试新功能兼容性。

---

## 3. **项目进展**
### **已合并/关闭 PR**
- **PR #2938** ([链接](https://github.com/sipeed/picoclaw/pull/2938))  
  - **修复**：Cron工具执行时缺少`"action": "run"`参数导致静默失败，回归修复。  
  - **影响**：确保定时任务正常调度，提升可靠性。  

- **PR #2759** ([链接](https://github.com/sipeed/picoclaw/pull/2759))  
  - **优化**：限制检索工具仅作用于当前会话，避免跨会话污染，增强上下文隔离性。  

### **活跃开发中 PR**
- **PR #2937** ([链接](https://github.com/sipeed/picoclaw/pull/2937))  
  - **功能**：引入Agent协作总线，支持多代理间持久化通信、权限控制及会话隔离，是架构级改进。  
  - **意义**：为未来多智能体协作场景奠定基础，可能成为下一版本核心特性。  

---

## 4. **社区热点**
### **高互动 Issue**
- **Issue #28** ([链接](https://github.com/sipeed/picoclaw/issues/28))  
  - **诉求**：用户请求简化与LM Studio的连接流程，目前因技术门槛难以实现。  
  - **背景**：LM Studio作为本地LLM工具链，用户希望无缝集成到PicoClaw生态中，反映对本地化部署友好性的需求。  

### **高评论 PR**
- **PR #2883** ([链接](https://github.com/sipeed/picoclaw/pull/2883))  
  - **功能**：支持微信多账号配置，动态识别`weixin_*`格式密钥，适配多设备场景。  
  - **反馈**：虽暂无直接评论，但属高频需求（微信渠道用户普遍需要多账号切换）。

---

## 5. **Bug 与稳定性**
| **严重程度** | **Issue/PR** | **问题描述** | **修复状态** |
|--------------|--------------|--------------|--------------|
| 🔴 高优先级 | Issue #1042 ([链接](https://github.com/sipeed/picoclaw/issues/1042)) | `exec`工具的`guardCommand`方法误拦截合法命令（如天气查询），正则表达式路径判断过于严格。 | **待修复**（无对应PR，需紧急处理） |
| 🟡 中优先级 | PR #2936 ([链接](https://github.com/sipeed/picoclaw/pull/2936)) | 修复技能缺失二进制文件时的自动过滤，避免系统提示误导用户。 | **已合并** |

---

## 6. **功能请求与路线图信号**
- **Agent协作总线（PR #2937）**：结合Issue #28的LM Studio需求，未来可能扩展为多代理协同调用外部LLM的能力。  
- **多账号支持（PR #2883）**：微信渠道的通用化方案，可能推广至其他社交平台。  
- **工具策略强化（Issue #2837）**：通过`AGENT.md`前端元数据实现细粒度工具权限控制，符合企业级部署需求。

---

## 7. **用户反馈摘要**
- **痛点**：  
  - **工具安全策略过严**（Issue #1042）：用户抱怨合法命令被误拦截，影响基础功能体验。  
  - **多账号管理缺失**（PR #2883）：微信用户需手动切换账号，操作繁琐。  
- **满意点**：  
  - 检索工具会话隔离（PR #2759）获得积极评价，认为提升了上下文准确性。

---

## 8. **待处理积压**
- **Issue #1042** ([链接](https://github.com/sipeed/picoclaw/issues/1042))  
  - **紧急度**：高，涉及核心工具链可用性，需优先修复。  
- **Issue #28** ([链接](https://github.com/sipeed/picoclaw/issues/28))  
  - **长期需求**：LM Studio集成可显著提升本地LLM用户体验，建议纳入下版本规划。

---

**总结**：PicoClaw在架构升级和功能完善上稳步推进，但需关注工具安全性和多账号管理的用户反馈。Agent协作和多平台集成是未来重点方向。

</details>

<details>
<summary><strong>hermesagent</strong> — <a href="https://github.com/NousResearch/hermes-agent">NousResearch/hermes-agent</a></summary>

---

# **HermesAgent 项目日报（2026-05-25）**

---

## 1. **今日速览**
- 过去24小时内，项目活跃度极高：**370条 Issues**（新开/活跃186条，关闭184条）、**500条 PR**（待合并322条，已合并/关闭178条），无新版本发布。
- 社区讨论热点集中在 **OAuth认证问题**、**Telegram DM会话绑定异常**、**Kanban看板401错误** 等核心功能稳定性问题。
- 多个关键Bug已有修复PR提交（如Windows并发实例检测、QQBot交互修复），表明团队正积极响应高优先级问题。

---

## 2. **版本发布**
> 无新版本发布。

---

## 3. **项目进展**
### ✅ **重要合并/关闭的 PR**
| PR # | 类型 | 内容 | 链接 |
|------|------|------|------|
| [#31806](https://github.com/NousResearch/hermes-agent/pull/31806) | Bugfix (Windows) | 修复`hermes update`在Windows下误判并发实例的问题（排除setuptools.exe干扰） | [详情](#) |
| [#31805](https://github.com/NousResearch/hermes-agent/pull/31805) | Bugfix (Mattermost) | 修复Mattermost消息线程路由逻辑，确保状态消息保持在当前线程 | [详情](#) |
| [#31790](https://github.com/NousResearch/hermes-agent/pull/31790) | Feature (Kanban) | 实现Kan看板任务完成时自动重定向至`review`列，适配HERMES_KANBAN_REVIEW配置 | [详情](#) |

**整体推进**：  
- 修复了多个平台（Windows、QQBot、Mattermost）的关键稳定性问题；
- 新增工具链支持（OneDrive读取工具）；
- Kanban看板功能增强，提升协作流程自动化。

---

## 4. **社区热点**
### 🔥 **评论最多/反应最活跃的 Issues**
| Issue # | 标题 | 评论数 | 链接 |
|--------|------|-------|------|
| [#26847](https://github.com/NousResearch/hermes-agent/issues/26847) | xAI OAuth订阅权限异常（标准用户被强制Heavy-only） | 33 | [详情](#) |
| [#29125](https://github.com/NousResearch/hermes-agent/issues/29125) | Claude CLI集成失败（Anthropic模型选择卡死） | 24 | [详情](#) |
| [#24186](https://github.com/NousResearch/hermes-agent/issues/24186) | Kanban看板401 Unauthorized（更新后无法加载） | 6 | [详情](#) |

**诉求分析**：  
- **第三方API权限控制**（xAI、Anthropic）是用户痛点，涉及计费与文档准确性；
- **多平台集成稳定性**（Telegram、Feishu、QQBot）影响用户体验；
- **看板功能中断**反映数据持久化层可能存在问题。

---

## 5. **Bug 与稳定性**
### ⚠️ **按严重程度排序**
| 问题 | 严重性 | 是否已有Fix PR | 链接 |
|------|--------|----------------|------|
| **Telegram DM会话劫持**（新Topic被绑定到旧Topic） | P1 | [#31086](https://github.com/NousResearch/hermes-agent/issues/31086) | [详情](#) |
| **Windows并发实例误报**（setuptools.exe干扰） | P1 | [#31806](https://github.com/NousResearch/hermes-agent/pull/31806) | [详情](#) |
| **Kanban数据库完整性检查崩溃**（WAL模式下） | P2 | [#31795](https://github.com/NousResearch/hermes-agent/pull/31795) | [详情](#) |
| **BTRFS+SQLite COW兼容性问题** | P3 | [#30846](https://github.com/NousResearch/hermes-agent/issues/30846) | [详情](#) |

---

## 6. **功能请求与路线图信号**
### 🔮 **潜在纳入下一版本的功能**
| 需求 | 关联PR | 优先级 |
|------|--------|--------|
| **OneDrive集成**（微软Graph API读取工具） | [#31807](https://github.com/NousResearch/hermes-agent/pull/31807) | P3 |
| **Claude Code订阅专用Provider**（绕过第三方配额限制） | [#31796](https://github.com/NousResearch/hermes-agent/pull/31796) | P3 |
| **终端标题动态显示**（会话名称+思考状态指示） | [#5505](https://github.com/NousResearch/hermes-agent/issues/5505) | P3 |

---

## 7. **用户反馈摘要**
### 😊 **满意点**
- **mempalace外部内存模块**（[#6323](https://github.com/NousResearch/hermes-agent/issues/6323)）获26赞，用户赞赏结构化长记忆能力；
- **自定义Provider协议选择**（[#6209](https://github.com/NousResearch/hermes-agent/issues/6209)）被提出，解决代理网关兼容性痛点。

### ❌ **不满意点**
- **xAI订阅权限异常**（[#26847](https://github.com/NousResearch/hermes-agent/issues/26847)）：标准用户被强制Heavy-only，文档与后端策略不一致；
- **Kanban看板401错误**（[#24186](https://github.com/NousResearch/hermes-agent/issues/24186)）：更新后完全不可用，影响团队协作；
- **Telegram会话劫持**（[#31086](https://github.com/NousResearch/hermes-agent/issues/31086)）：新对话被错误绑定到历史Topic，需紧急修复。

---

## 8. **待处理积压**
### ⏳ **长期未响应的重要Issue/PR**
| 编号 | 标题 | 最后更新时间 | 链接 |
|------|------|--------------|------|
| [#15080](https://github.com/NousResearch/hermes-agent/issues/15080) | Anthropic OAuth 400错误（Claude Max订阅） | 2026-05-24 | [详情](#) |
| [#27228](https://github.com/NousResearch/hermes-agent/issues/27228) | xAI Grok-4.3配额消耗过快（$30计划） | 2026-05-25 | [详情](#) |
| [#31392](https://github.com/NousResearch/hermes-agent/issues/31392) | RFC：子代理异步审批门控（提案阶段） | 2026-05-24 | [详情](#) |

---

**总结**：  
- **健康度**：高活跃度，核心问题快速响应，但需持续关注第三方API权限控制与数据持久化稳定性；
- **建议**：优先修复P1级Bug（Telegram会话劫持、Windows并发检测），同步推进OneDrive和Claude Code集成功能。

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

---

# **NanoClaw 项目日报（2026-05-25）**

---

## **1. 今日速览**
- **活跃度**：过去24小时内，项目保持较高开发节奏，共提交7个PR（含3个已合并），新增1条活跃Issue，无新版本发布。  
- **关键进展**：多个功能修复和CI升级PR进入合并流程，包括Node.js版本升级、权限继承改进及消息ID规范化。  
- **社区参与**：开发者贡献集中，但部分PR尚未获得评论，需关注后续反馈。  
- **健康度评估**：整体正向推进，但存在未解决的严重Bug（Issue #2606）。

---

## **2. 版本发布**
- **无新版本发布**。

---

## **3. 项目进展**
### **已合并/关闭的 PR**
- **[PR #1968](https://github.com/nanocoai/nanoclaw/pull/1968)**  
  - **内容**：实现多Agent独立配置Provider和模型选择，支持Chat驱动的动态配置。  
  - **意义**：核心架构增强，提升多Agent场景下的灵活性和可维护性。  

- **[PR #2344](https://github.com/nanocoai/nanoclaw/pull/2344)**  
  - **内容**：修复测试类型定义问题，解决`pnpm run build`失败问题。  
  - **意义**：确保构建流程稳定性，避免阻塞开发。  

### **待合并的 PR**
- **[PR #2608](https://github.com/nanocoai/nanoclaw/pull/2608)**  
  - **内容**：升级GitHub Actions从Node 20到Node 24，规避2026年6月弃用风险。  
  - **优先级**：高，涉及CI基础设施维护。  

- **[PR #2607](https://github.com/nanocoai/nanoclaw/pull/2607)**  
  - **内容**：将平台消息动作改为使用原始ID而非内部复合ID，兼容第三方API要求。  
  - **影响范围**：消息交互层，需验证外部平台兼容性。  

---

## **4. 社区热点**
- **最活跃 Issue/PR**：  
  - **[Issue #2606](https://github.com/nanocoai/nanoclaw/issues/2606)**  
    - **问题**：`engage_mode: 'always'`被静默丢弃，导致消息无法处理。  
    - **诉求**：修复路由逻辑，确保该模式正确触发Agent响应。  
    - **关联PR**：暂无直接修复，需开发者介入。  

- **高赞 PR**：  
  - **[PR #2345](https://github.com/nanocoai/nanoclaw/pull/2345)**  
    - **功能**：自动导入分组目录下的`CLAUDE.role.md`文件，简化角色配置。  
    - **潜力**：可能成为下一版本“角色管理”功能的候选。  

---

## **5. Bug与稳定性**
| **严重程度** | **问题描述** | **状态** | **链接** |
|--------------|--------------|----------|----------|
| **高** | `engage_mode='always'`静默丢弃消息 | 未修复 | [#2606](https://github.com/nanocoai/nanoclaw/issues/2606) |
| **中** | 测试类型定义冲突导致构建失败 | 已修复 | [#2344](https://github.com/nanocoai/nanoclaw/pull/2344) |

---

## **6. 功能请求与路线图信号**
- **潜在纳入下版本的特性**：  
  - **多Agent动态配置**（PR #1968）：已实现，需进一步集成测试。  
  - **角色文件自动导入**（PR #2345）：用户友好型改进，可能扩展为“模板引擎”。  
  - **平台消息ID标准化**（PR #2607）：跨平台兼容性需求强烈。  

---

## **7. 用户反馈摘要**
- **痛点**：  
  - `engage_mode`逻辑缺陷导致消息丢失（Issue #2606），直接影响用户体验。  
  - 管理员端缺乏批量查询接口（如PR #2604的`/admin/agent-activity`），需优化后台管理效率。  
- **满意点**：  
  - 开发者对Node.js升级（PR #2608）积极响应，体现对长期维护的关注。  

---

## **8. 待处理积压**
- **紧急**：  
  - [Issue #2606](https://github.com/nanocoai/nanoclaw/issues/2606)：需尽快修复，否则影响核心功能。  
- **长期关注**：  
  - [PR #2605](https://github.com/nanocoai/nanoclaw/pull/2605)：权限继承机制改进，需评估与现有系统的兼容性。  

--- 

**总结**：项目处于活跃开发阶段，需优先解决高优先级Bug，同时推进架构增强功能。建议维护者集中资源处理Issue #2606，并加快PR #2608等CI相关变更的合并。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

---

# **IronClaw 项目日报（2026-05-25）**

---

## 1. **今日速览**
- 过去24小时内，IronClaw 项目保持高度活跃：**24条 Issues 更新**（新开/活跃18条，关闭6条），**50条 PR 更新**（待合并49条，已合并1条）。
- 核心安全审计与 Reborn 集成是今日焦点，涉及工具执行路径的强制审计、密钥管理改进等。
- 无新版本发布，但多个关键 PR 推进了架构边界和安全性加固。

---

## 2. **版本发布**
- 无新版本发布。

---

## 3. **项目进展**
### ✅ 合并/关闭的重要 PR
| PR # | 标题 | 关键进展 |
|------|------|----------|
| [#4015](https://github.com/nearai/ironclaw/pull/4015) | `request_signature` 工具 + 认证门控扩展 | 实现 Reborn 循环端到端签名请求，支持托管端认证门控 |
| [#4027](https://github.com/nearai/ironclaw/pull/4027) | 停止测试时提示 OS 密钥访问 | 修复 macOS/Linux 测试环境因密钥链弹窗导致的阻塞问题 |
| [#4026](https://github.com/nearai/ironclaw/pull/4026) | 引擎 V2 效果桥接强制审计 | 确保所有工具调用均通过审计漏斗，生成 `ActionRecord` |
| [#4025](https://github.com/nearai/ironclaw/pull/4025) | 桥接/命令工具执行审计化 | 完成最后一批工具执行路径的审计改造 |

**整体推进**：  
- 完成了 **工具执行路径的全局审计改造**（覆盖聊天、调度器、引擎、桥接等场景），解决了 #4017 的核心安全问题。
- Reborn 集成持续推进，包括子代理启动机制（[#3868](https://github.com/nearai/ironclaw/pull/3868)）、内存产品表面合约（[#3775](https://github.com/nearai/ironclaw/pull/3775)）。

---

## 4. **社区热点**
### 🔥 最活跃的 Issues/PRs
#### **Issues**
- **[#4019](https://github.com/nearai/ironclaw/issues/4019)**  
  *提案：强制执行工具不变性*  
  评论数：1 | 背景：解决交互式聊天工具绕过 `ToolDispatcher::dispatch` 的安全漏洞，确保所有工具调用均通过审计漏斗。  
  - 关联 PR：[#4021](https://github.com/nearai/ironclaw/pull/4021)（CI 边界测试）、[#4023](https://github.com/nearai/ironclaw/pull/4023)（聊天路径审计化）。

- **[#3917](https://github.com/nearai/ironclaw/issues/3917)**  
  *安全审查：`RuntimeCredentialTarget::PathPlaceholder` 是否废弃？*  
  评论数：1 | 争议：URL 路径注入密钥存在泄漏风险，需决策是否移除或强化。

#### **PRs**
- **[#4015](https://github.com/nearai/ironclaw/pull/4015)**  
  评论数：0 | 意义：首次实现 Reborn 循环的签名请求工具，为高价值操作提供托管端认证门控。

---

## 5. **Bug 与稳定性**
| 问题 | 严重程度 | 状态 | 链接 |
|------|----------|------|------|
| 测试环境密钥链弹窗阻塞 | ⚠️ 中等 | 已修复（[#4027](https://github.com/nearai/ironclaw/pull/4027)） | macOS/Linux CI 测试失败 |
| HTTP 响应错误导致运行终止 | ❗ 高 | 修复中（[#4022](https://github.com/nearai/ironclaw/pull/4022)） | 工具错误处理回归 |

---

## 6. **功能请求与路线图信号**
- **Reborn 集成**：  
  - 子代理启动机制（[#3868](https://github.com/nearai/ironclaw/pull/3868)、[#3869](https://github.com/nearai/ironclaw/pull/3869)）可能纳入下一版本。
  - 内存产品表面合约（[#3775](https://github.com/nearai/ironclaw/pull/3775)）已初步实现，后续可扩展更多 Reborn 产品适配器。
- **安全审计**：工具执行路径全链路审计（[#4019](https://github.com/nearai/ironclaw/issues/4019)）为长期安全目标。

---

## 7. **用户反馈摘要**
- **痛点**：  
  - 开发者反馈测试环境密钥链弹窗阻塞（[#4027](https://github.com/nearai/ironclaw/pull/4027)），影响 CI/CD 流程。
  - 用户对工具执行审计的透明性表示满意，但希望进一步细化日志格式（[#4019](https://github.com/nearai/ironclaw/issues/4019)）。
- **满意度**：  
  - Reborn 本地开发环境的 HTTP 能力暴露（[#4016](https://github.com/nearai/ironclaw/pull/4016)）获得初步验证。

---

## 8. **待处理积压**
| Issue/PR | 状态 | 优先级 | 链接 |
|---------|------|--------|------|
| [#3259](https://github.com/nearai/ironclaw/issues/3259) | 未解决 | P2（下游依赖） | crates.io 版本滞后于 GitHub 标签，影响下游消费者 |
| [#3917](https://github.com/nearai/ironclaw/issues/3917) | 待决策 | 安全审查 | URL 路径密钥注入风险需评估 |
| [#3608](https://github.com/nearai/ironclaw/issues/3608) | 开放 | P0（WebUI Beta） | 授权请求门控缺失，需紧急补全 |

---

**总结**：IronClaw 在安全与架构演进上取得显著进展，尤其是工具执行审计化与 Reborn 集成。建议优先处理 [#3259](https://github.com/nearai/ironclaw/issues/3259) 版本同步问题，并尽快决策 [#3917](https://github.com/nearai/ironclaw/issues/3917) 的安全边界变更。

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

---

# **LobsterAI 项目日报（2026-05-25）**

---

## **1. 今日速览**
- LobsterAI 在过去 24 小时内保持高度活跃，共合并 **14 个 PR**，无新 Issues 报告，表明开发团队正集中精力修复和优化现有功能。
- 所有合并的 PR 均涉及关键功能修复，涵盖输入体验、消息队列、定时任务、数据库迁移等核心模块，显著提升了稳定性和用户体验。
- 无新版本发布，但代码库更新密集，说明团队处于迭代优化阶段，未引入重大变更。

---

## **2. 版本发布**
- **无新版本发布**。

---

## **3. 项目进展**
### **关键 PR 合并摘要**
| PR # | 标题 | 修复/改进内容 | 链接 |
|------|------|----------------|------|
| [#1585](https://github.com/netease-youdao/LobsterAI/pull/1585) | 修复设置页输入框按 Enter 键意外关闭问题 | 拦截表单提交行为，避免输入法误触导致设置页保存并关闭 | [详情](#1585) |
| [#1588](https://github.com/netease-youdao/LobsterAI/pull/1588) | 修复定时任务错误提示“未配置 IM 通知通道” | 修正系统提示词逻辑，避免误判已配置的 IM 通道 | [详情](#1588) |
| [#1590](https://github.com/netease-youdao/LobsterAI/pull/1590) | 支持 AI 回复期间连续发送消息（客户端消息队列） | 新增消息排队机制，允许用户在 AI 流式响应时继续输入 | [详情](#1590) |
| [#1593](https://github.com/netease-youdao/LobsterAI/pull/1593) | 移除 OpenClaw cron 配置中的无效字段 `skipMissedJobs` | 解决网关因未知字段校验失败而无法启动的问题 | [详情](#1593) |
| [#1594](https://github.com/netease-youdao/LobsterAI/pull/1594) | 扩展搜索范围至内容和所有 Agent | 修复跨 Agent 会话不可见及仅匹配标题的问题 | [详情](#1594) |
| [#1595](https://github.com/netease-youdao/LobsterAI/pull/1595) | 修复 SQLite 迁移标记逻辑缺陷 | 确保迁移失败后不标记为已完成，支持重试 | [详情](#1595) |
| [#1598](https://github.com/netease-youdao/LobsterAI/pull/1598) | 修复 `getConfig()` 硬编码 `executionMode` 问题 | 读取数据库实际值而非默认值，保证 UI 一致性 | [详情](#1598) |
| [#1599](https://github.com/netease-youdao/LobsterAI/pull/1599) | 修复权限响应广播到两个引擎的问题 | 避免非预期引擎收到权限响应导致混乱 | [详情](#1599) |
| [#1600](https://github.com/netease-youdao/LobsterAI/pull/1600) | 修复定时任务保存后误弹出脏检查对话框 | 优化导航逻辑，避免虚假脏状态提示 | [详情](#1600) |
| [#1601](https://github.com/netease-youdao/LobsterAI/pull/1601) | 修复网关重连后 session 停止冷却丢失 | 保留停止冷却记录，防止意外复活已停止会话 | [详情](#1601) |
| [#1602](https://github.com/netease-youdao/LobsterAI/pull/1602) | 修复消息序列号并发竞争 | 通过事务保证原子性，避免重复序列号 | [详情](#1602) |
| [#1603](https://github.com/netease-youdao/LobsterAI/pull/1603) | 修复 `continueSession` 重复错误消息与异常吞没 | 统一错误处理逻辑，提升可靠性 | [详情](#1603) |
| [#1606](https://github.com/netease-youdao/LobsterAI/pull/1606) | 替换 NetEase Bee 密钥明文为环境变量占位符 | 增强安全性，避免凭据暴露 | [详情](#1606) |
| [#1607](https://github.com/netease-youdao/LobsterAI/pull/1607) | 为 Anthropic/Gemini 流式请求添加 SSE 行缓冲 | 解决 JSON 分块解析失败导致的流式中断 | [详情](#1607) |

**整体推进**：本次更新聚焦于 **稳定性修复**（如消息队列、数据库事务）、**用户体验优化**（如输入交互、搜索功能）和 **安全加固**（密钥管理），项目健康度显著提升。

---

## **4. 社区热点**
- **最活跃 PR**：[#1590](https://github.com/netease-youdao/LobsterAI/pull/1590)（支持 AI 回复期间连续输入）。该 PR 解决了用户反馈的“等待 AI 响应时无法打字”痛点，评论虽少但需求明确，可能成为协作场景的核心功能。
- **高频讨论点**：[#1594](https://github.com/netease-youdao/LobsterAI/pull/1594)（跨 Agent 搜索）。用户期望在复杂工作流中快速检索历史对话，此修复直接提升多 Agent 协作效率。

---

## **5. Bug 与稳定性**
| 问题类型 | 描述 | 严重程度 | 是否已修复 | 链接 |
|----------|------|----------|------------|------|
| **功能异常** | 定时任务错误提示“未配置 IM 通知通道” | 中 | ✅ [#1588](https://github.com/netease-youdao/LobsterAI/pull/1588) | - |
| **数据一致性问题** | 消息序列号并发重复 | 高 | ✅ [#1602](https://github.com/netease-youdao/LobsterAI/pull/1602) | - |
| **安全风险** | NetEase Bee 密钥明文存储 | 高 | ✅ [#1606](https://github.com/netease-youdao/LobsterAI/pull/1606) | - |
| **UI 不一致** | `executionMode` 硬编码值 | 低 | ✅ [#1598](https://github.com/netease-youdao/LobsterAI/pull/1598) | - |

---

## **6. 功能请求与路线图信号**
- **消息队列机制**（[#1590](https://github.com/netease-youdao/LobsterAI/pull/1590)）：用户强烈希望“边聊边写”，该功能可能成为下一版本的重点。
- **跨 Agent 搜索**（[#1594](https://github.com/netease-youdao/LobsterAI/pull/1594)）：多 Agent 协作场景中，全局搜索是刚需，建议优先实现。
- **SSE 流控优化**（[#1607](https://github.com/netease-youdao/LobsterAI/pull/1607)）：兼容更多模型的长文本流式输出，需持续测试。

---

## **7. 用户反馈摘要**
- **痛点**：  
  - 输入法误触导致设置页意外关闭（[#1585](https://github.com/netease-youdao/LobsterAI/pull/1585)）。  
  - 定时任务误报“未配置 IM 通道”（[#1588](https://github.com/netease-youdao/LobsterAI/pull/1588)）。  
- **满意点**：  
  - 消息队列机制（[#1590](https://github.com/netease-youdao/LobsterAI/pull/1590)）被用户视为“生产力飞跃”。  
  - 搜索功能改进（[#1594](https://github.com/netease-youdao/LobsterAI/pull/1594)）获得跨 Agent 协作用户的积极评价。

---

## **8. 待处理积压**
- **长期未响应 Issue/PR**：  
  - [#1585](https://github.com/netease-youdao/LobsterAI/issues/1585)（输入法问题）：虽已修复，但需监控后续用户反馈。  
  - [#1593](https://github.com/netease-youdao/LobsterAI/pull/1593)（OpenClaw 配置兼容性）：需验证生产环境迁移方案。  

---

**总结**：LobsterAI 近期以 **稳定性修复** 和 **用户体验优化** 为核心，代码质量显著提升，尤其在消息队列、搜索、安全领域表现突出。建议持续关注用户反馈，加速推进消息队列和跨 Agent 搜索的落地。

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyclaw">TinyAGI/tinyclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

---

# **Moltis 项目日报（2026-05-25）**

---

## **1. 今日速览**
- 过去24小时内，Moltis 项目保持高度活跃：**关闭8个 Issues** 和 **合并10个 PRs**，无新版本发布。
- 所有 Issues 均属近期提交（5月23日-24日），表明问题响应迅速，社区协作高效。
- PR 集中修复安全、稳定性及用户体验问题，如 MCP 环境变量泄露、模型选择器适配等，体现对核心功能的持续优化。
- 无新增开放 Issue/PR，团队正积极收尾近期任务。

---

## **2. 版本发布**
- **无新版本发布**。

---

## **3. 项目进展**
### **关键合并 PR**
| PR # | 标题 | 链接 | 贡献者 | 摘要 |
|------|------|------|--------|------|
| [#1066](https://github.com/moltis-org/moltis/pull/1066) | feat(agents): support per-agent runtime limits | [🔗](https://github.com/moltis-org/moltis/pull/1066) | @penso | 实现每个 Agent 独立的 `timeout_secs` 和 `max_iterations` 配置，支持子进程运行时限制。 |
| [#1065](https://github.com/moltis-org/moltis/pull/1065) | fix(sandbox): quiet image prebuild logs | [🔗](https://github.com/moltis-org/moltis/pull/1065) | @penso | 优化沙箱镜像预构建日志输出，减少启动时的冗余警告信息。 |
| [#1063](https://github.com/moltis-org/moltis/pull/1063) | fix(mcp): hide stdio env values from status | [🔗](https://github.com/moltis-org/moltis/pull/1063) | @penso | 修复 MCP 服务器通过 `mcp_list` 暴露环境变量的安全问题，改用变量名而非值。 |
| [#1060](https://github.com/moltis-org/moltis/pull/1060) | fix(web): show long model names in picker | [🔗](https://github.com/moltis-org/moltis/pull/1060) | @penso | 改进模型选择器 UI，支持长版本号显示并增加工具提示。 |

**整体推进**：  
本次 PR 覆盖 **Agent 能力边界控制、安全性加固、UI 体验优化**三大方向，显著提升项目的可配置性、稳定性和用户友好度。

---

## **4. 社区热点**
### **最受关注 Issues**
- **[#1054](https://github.com/moltis-org/moltis/issues/1054)**: Env vars from stdio MCP server config are exposed to the LLM via `mcp_list`  
  - **诉求**：用户反馈 MCP 服务器配置的环境变量可能通过 API 泄露给 LLM，存在安全风险。  
  - **解决状态**：已由 PR [#1063](https://github.com/moltis-org/moltis/pull/1063) 修复，将变量名替换为值。

- **[#1052](https://github.com/moltis-org/moltis/issues/1052)**: Model picker does not fit model versions  
  - **诉求**：模型版本号过长导致选择器显示不全，影响用户体验。  
  - **解决状态**：PR [#1060](https://github.com/moltis-org/moltis/pull/1060) 已优化 UI 布局。

---

## **5. Bug 与稳定性**
| Issue # | 问题描述 | 严重程度 | 修复状态 | 链接 |
|---------|----------|----------|----------|------|
| [#1051](https://github.com/moltis-org/moltis/issues/1051) | OpenAI-compatible provider URL 未校验，失败时未记录完整 URL | 中 | PR [#1061](https://github.com/moltis-org/moltis/pull/1061) 已修复 | [🔗](https://github.com/moltis-org/moltis/issues/1051) |
| [#1053](https://github.com/moltis-org/moltis/issues/1053) | 自动会话标题生成失效 | 低 | PR [#1064](https://github.com/moltis-org/moltis/pull/1064) 已修复 | [🔗](https://github.com/moltis-org/moltis/issues/1053) |
| [#1055](https://github.com/moltis-org/moltis/issues/1055) | 聊天工具栏水平滚动溢出 | 中 | PR [#1062](https://github.com/moltis-org/moltis/pull/1062) 已修复 | [🔗](https://github.com/moltis-org/moltis/issues/1055) |

---

## **6. 功能请求与路线图信号**
- **Agent 能力边界控制**（[#1049](https://github.com/moltis-org/moltis/pull/1049)）：  
  用户提出按角色（如儿童/家长）分配不同 Agent 预设的需求，已通过 PR 实现，可能成为未来多租户场景的核心功能。
- **外部 Agent 动态开关**（[#1057](https://github.com/moltis-org/moltis/issues/1057) + [#1059](https://github.com/moltis-org/moltis/pull/1059)）：  
  允许通过配置禁用外部 Agent，增强灵活性，可能纳入下一版本配置管理模块。

---

## **7. 用户反馈摘要**
- **痛点**：  
  - **安全性**：MCP 环境变量泄露（[#1054]）是高频投诉，用户强调隐私保护需求。  
  - **易用性**：模型选择器适配问题（[#1052]）反映用户对清晰界面的期待。  
- **满意点**：  
  - 快速响应（所有 Issues 均在1天内关闭）。  
  - 沙箱日志优化（[#1065]）减少调试噪音，提升开发者体验。

---

## **8. 待处理积压**
- **长期未响应 Issue**：  
  - [#553](https://github.com/moltis-org/moltis/issues/553)（2026-04-04 创建）：  
    *“Per Agent 回环和超时设置”*，虽已关闭但未明确是否实现，需确认是否被后续 PR 覆盖。

---

**总结**：Moltis 项目在 **安全、稳定性、用户体验** 方面取得显著进展，社区协作高效。建议持续监控 Agent 能力边界控制的落地效果，并跟进外部 Agent 配置的集成测试。

</details>

<details>
<summary><strong>QwenPaw</strong> — <a href="https://github.com/agentscope-ai/QwenPaw">agentscope-ai/QwenPaw</a></summary>

---

# **QwenPaw 项目日报 | 2026-05-25**

---

## 1. **今日速览**
- 过去24小时内，QwenPaw 社区保持较高活跃度：**15条 Issues（9新开/活跃，6已关闭）**，**8条 PR（5待合并，3已合并）**，无新版本发布。
- 核心问题集中在 **UI 一致性、工具调用显示异常、定时任务中断、记忆系统优化** 等场景，反映用户对稳定性和功能完整性的持续关注。
- 近期 PR 推进了 **OpenCode 模型端点过滤、控制台样式统一、编码模式支持** 等关键改进，部分修复已进入代码审查阶段。

---

## 2. **版本发布**
> 无新版本发布。

---

## 3. **项目进展**
### ✅ **已合并 PR**
- **[PR #4658](https://github.com/agentscope-ai/QwenPaw/pull/4658)**  
  实现 `prepend_summary` 在记忆检索中的启用，增强上下文关联能力，可能改善知识复用效率。
- **[PR #4657 & #4654](https://github.com/agentscope-ai/QwenPaw/pull/4657)**  
  修复控制台页面风格不一致问题（环境变量页与安全设置页），提升 UI 统一性（关联 Issue #4593, #4619）。

### 🔄 **待合并 PR**
- **[PR #4660](https://github.com/agentscope-ai/QwenPaw/pull/4660)**  
  OpenCode 模型列表按端点动态过滤，避免用户选择错误 API 导致的报错（关联 Issue #4656）。
- **[PR #4655](https://github.com/agentscope-ai/QwenPaw/pull/4655)**  
  优化 Chat V2 会话面板和工具渲染逻辑，可能解决工具调用显示延迟问题（关联 Issue #4644）。
- **[PR #4578](https://github.com/agentscope-ai/QwenPaw/pull/4578)**  
  新增 **VS Code 风格的内嵌编码模式**，集成文件管理与 Git 控制，扩展 Agent 开发能力。

---

## 4. **社区热点**
### 🔥 **最活跃 Issues**
#### [Issue #4644](https://github.com/agentscope-ai/QwenPaw/issues/4644)  
**标题**: *Console UI: tool calls often not displayed until page refresh*  
- **评论数**: 6  
- **痛点**: 除 `read_file` 外，多数工具调用需手动刷新页面才能查看，无错误日志输出。  
- **背景**: 影响实时交互体验，可能阻塞调试流程。

#### [Issue #4650](https://github.com/agentscope-ai/QwenPaw/issues/4650)  
**标题**: *GLM-5.1 via OpenAI-compatible API 不显示思维链*  
- **评论数**: 4  
- **痛点**: 特定模型（如 GLM-5.1）的推理内容未在控制台展示，其他模型正常。  
- **关联 PR**: 可能与 #4655 的渲染优化相关。

#### [Issue #4653](https://github.com/agentscope-ai/QwenPaw/issues/4653)  
**标题**: *定时任务与用户消息共享 session 导致中断*  
- **评论数**: 3  
- **痛点**: 定时任务被用户消息抢占，需隔离执行上下文。  
- **潜在影响**: 自动化流程可靠性问题。

---

## 5. **Bug 与稳定性**
| 严重程度 | Issue/PR | 描述 | 状态 |
|---------|----------|------|------|
| **高** | [#4644](https://github.com/agentscope-ai/QwenPaw/issues/4644) | 工具调用显示异常 | 修复中（PR #4655） |
| **中** | [#4650](https://github.com/agentscope-ai/QwenPaw/issues/4650) | 特定模型思维链缺失 | 待分析（无直接 PR） |
| **中** | [#4653](https://github.com/agentscope-ai/QwenPaw/issues/4653) | 定时任务中断 | 待方案（无 PR） |
| **低** | [#4659](https://github.com/agentscope-ai/QwenPaw/issues/4659) | 空返回 | 待复现 |

---

## 6. **功能请求与路线图信号**
### 📌 **高优先级需求**
- **记忆系统智能化**（[#4652](https://github.com/agentscope-ai/QwenPaw/issues/4652)）  
  用户提出「总结-关联-提醒」机制，避免信息堆砌。已有 PR #4658 部分支持检索优化。
- **操作前规范加载**（[#4651](https://github.com/agentscope-ai/QwenPaw/issues/4651)）  
  建议技能执行时自动加载对应文档，减少人工查找成本。
- **OpenCode 端点过滤**（[#4656](https://github.com/agentscope-ai/QwenPaw/issues/4656)）  
  PR #4660 已提交，预计下版本集成。

---

## 7. **用户反馈摘要**
- **痛点**：  
  - UI 不一致（如语言按钮对齐、下拉箭头样式）影响专业感（Issue #4619）。  
  - 工具调用和思维链显示问题降低调试效率（Issue #4644, #4650）。  
  - 定时任务中断暴露会话管理缺陷（Issue #4653）。  
- **满意点**：  
  - 编码模式（PR #4578）和样式统一（PR #4657）获初步认可。  
  - 记忆检索优化（PR #4658）被标记为“修复”。

---

## 8. **待处理积压**
| Issue/PR | 状态 | 备注 |
|----------|------|------|
| [#4649](https://github.com/agentscope-ai/QwenPaw/issues/4649) | 开放 | 僵尸任务清理，需 APScheduler 配置修复 |
| [#4051](https://github.com/agentscope-ai/QwenPaw/issues/4051) | 已关闭 | DeepSeek 解析问题，需进一步验证 |
| [#4616](https://github.com/agentscope-ai/QwenPaw/issues/4616) | 开放 | Dream Awakening 微信通道异常，需排查 |

---

**总结**：QwenPaw 在功能迭代和用户体验优化上稳步推进，但需重点关注 **工具调用实时性、任务调度隔离、记忆系统智能化** 三大方向。社区反馈积极，建议优先合并 PR #4655 和 #4660 以解决高频痛点。

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>librefang</strong> — <a href="https://github.com/librefang/librefang">librefang/librefang</a></summary>

---

### **librefang 项目日报 | 2026-05-25**

---

#### **1. 今日速览**
- **活跃度**：过去24小时内，项目保持较高开发节奏，共处理 **6个 Issues（1新开/5关闭）** 和 **16个 PR（8待合并/8已合并）**，无新版本发布。
- **核心进展**：重点修复了 CI/CD 稳定性问题、多实例部署的隔离漏洞，并推进了 MCP 上下文传递、Dashboard 功能增强等关键改进。
- **社区参与**：Issues 和 PR 评论量适中，但部分功能请求（如 Feishu WebSocket 支持）仍需进一步讨论。

---

#### **2. 版本发布**
- **无新版本发布**。

---

#### **3. 项目进展**
##### **已合并 PR（关键修复与功能）**
- **[#5693](https://github.com/librefang/librefang/pull/5693)**  
  修复 `audit_retention_test` 因 #5683 引入的软容量限制导致的测试失败，确保审计任务启动逻辑正确性。
  
- **[#5695](https://github.com/librefang/librefang/pull/5695)**  
  解决 `detect-secrets` 扫描因行号漂移导致的误报问题，优化 CI 安全扫描流程。

- **[#5688](https://github.com/librefang/librefang/pull/5688)**  
  修复多机器人部署中 `/commands` 路由忽略 `account_id` 的问题，实现命令隔离（[Issue #5672](https://github.com/librefang/librefang/issues/5672)）。

- **[#5691](https://github.com/librefang/librefang/pull/5691)**  
  调整 `.secrets.baseline` 文件生成规则，避免因格式差异导致 CI 扫描失败。

##### **待合并 PR（高优先级）**
- **[#5699](https://github.com/librefang/librefang/issues/5699)**  
  提出将 MCP 工具调用上下文（如用户身份）传递给服务器，增强权限控制（需进一步设计）。
- **[#5674](https://github.com/librefang/librefang/pull/5674)**  
  修复 Agent Loop 中的数据泄露、状态丢失及解析错误，涉及安全性和性能优化（需代码审查）。

---

#### **4. 社区热点**
- **最活跃 Issue**：[#5689](https://github.com/librefang/librefang/issues/5689)（CI 失败，8条评论）  
  因 PR #5647 的运行时变更导致 macOS 测试失败，团队已快速响应并修复。
- **新功能请求**：[#123](https://github.com/librefang/librefang/issues/123)（Feishu WebSocket 长连接支持）  
  来自外部生态（OpenFang）的需求，可能影响实时消息场景的集成体验。

---

#### **5. Bug 与稳定性**
| **严重性** | **问题描述** | **关联 PR** |
|------------|--------------|-------------|
| 🔴 **高** | 多机器人部署下 `/commands` 路由错误（跨账户泄漏） | [#5688](https://github.com/librefang/librefang/pull/5688) ✅ 修复 |
| 🟡 **中** | `audit_retention_test` 因容量限制失败 | [#5693](https://github.com/librefang/librefang/pull/5693) ✅ 修复 |
| 🟡 **中** | `detect-secrets` 扫描误报（行号漂移） | [#5695](https://github.com/librefang/librefang/pull/5695) ✅ 修复 |

---

#### **6. 功能请求与路线图信号**
- **MCP 上下文传递**（[#5699](https://github.com/librefang/librefang/issues/5699)）：  
  若实现，可显著提升多租户场景下的安全性，建议纳入下一版本。
- **Dashboard 工具分组管理**（[#5680](https://github.com/librefang/librefang/pull/5680)）：  
  用户反馈强烈，已合并，增强 Agent 配置灵活性。
- **Feishu WebSocket 支持**（[#123](https://github.com/librefang/librefang/issues/123)）：  
  需评估协议兼容性，可能作为长期需求跟踪。

---

#### **7. 用户反馈摘要**
- **痛点**：  
  - 多机器人部署时命令路由混乱（[#5672](https://github.com/librefang/librefang/issues/5672)），用户需手动隔离。
  - MCP 工具调用缺乏身份上下文，导致权限控制薄弱（[#5699](https://github.com/librefang/librefang/issues/5699)）。
- **满意度**：  
  Dashboard 工具分组功能（[#5680](https://github.com/librefang/librefang/pull/5680)）获积极评价，简化了复杂配置。

---

#### **8. 待处理积压**
- **长期未响应 Issue**：  
  - [#123](https://github.com/librefang/librefang/issues/123)（Feishu WebSocket 支持）  
    需明确技术可行性，建议优先评估。
- **待合并 PR**：  
  - [#5674](https://github.com/librefang/librefang/pull/5674)（Agent Loop 安全修复）  
    需尽快通过代码审查，防止潜在风险扩散。

---

**总结**：项目在稳定性、安全性和用户体验方面取得显著进展，但需持续关注多实例部署和 MCP 集成的长期需求。建议优先处理积压的 Feishu 支持和 Agent Loop 修复。

</details>

<details>
<summary><strong>openfang</strong> — <a href="https://github.com/RightNow-AI/openfang">RightNow-AI/openfang</a></summary>

# OpenFang 项目日报 (2026-05-25)

---

## 1. **今日速览**
- 项目活跃度中等：过去24小时新增1个活跃Issue和2个待合并PR，无版本发布。  
- 核心问题聚焦于**嵌入驱动兼容性**（Issue #1212）和**长推理任务稳定性优化**（PR #1209/#1213）。  
- 开发者贡献集中来自 `@Coder666`，推动功能迭代，但社区反馈尚未显著增加（总👍/评论数为0）。  
- GitHub 链接：[openfang仓库](https://github.com/RightNow-AI/openfang)  

---

## 2. **版本发布**
- **无新版本发布**。

---

## 3. **项目进展**
- **未合并PR**：  
  - **PR #1213 [feat: Inference time windows]**  
    新增LLM推理时间窗口功能，允许用户限制调用时段（如工作日9AM-5PM），超时时非阻塞暂停。[详情](https://github.com/RightNow-AI/openfang/pull/1213)  
  - **PR #1209 [feat: Long-running local inference support]**  
    针对本地推理后端（如llama.cpp、vLLM）优化超时配置与队列机制，提升长任务可靠性。[详情](https://github.com/RightNow-AI/openfang/pull/1209)  
  *影响*：两项PR均解决关键痛点，但需测试验证后合并。

---

## 4. **社区热点**
- **Issue #1212 [bug: Embedding driver hard-codes providers]**  
  用户报告嵌入驱动仅支持6家云厂商且无法覆盖OpenAI兼容服务（如llama.cpp），导致本地化部署受阻。[链接](https://github.com/RightNow-AI/openfang/issues/1212)  
  *诉求分析*：反映用户对**灵活扩展性**的强烈需求，可能影响自托管场景采用率。

---

## 5. **Bug与稳定性**
- **高优先级回归问题**：  
  - **Issue #1212**：嵌入驱动硬编码提供商列表（破坏性变更），已有修复PR但未合并。  
    *严重性*：阻断性缺陷（影响OpenAI兼容场景）。  
    *状态*：需紧急处理，建议优先合并相关PR。

---

## 6. **功能请求与路线图信号**
- **潜在纳入下一版本的功能**：  
  - **推理时间窗口（PR #1213）**：符合企业合规需求（如成本控制）。  
  - **长任务队列优化（PR #1209）**：填补本地推理场景的技术空白。  
  - **嵌入驱动扩展（Issue #1212）**：需评估是否重构为动态配置模式。

---

## 7. **用户反馈摘要**
- **痛点提炼**：  
  - **兼容性不足**：嵌入驱动缺乏对非Ollama/OpenAI服务的支持（Issue #1212）。  
  - **稳定性瓶颈**：本地推理任务易因超时中断（PR #1209背景）。  
  - **使用场景**：企业用户需严格管控LLM调用时段（PR #1213目标）。  
- **满意度**：现有文档未提及时间窗口功能，可能引发用户困惑。

---

## 8. **待处理积压**
- **长期未响应项**：  
  - **Issue #1212**（创建于2026-05-24）：需维护者确认是否计划重构嵌入驱动架构。  
  - **PR #1209/#1213**：需安排代码审查与集成测试，避免积压。

---

### 总结建议
- **优先级排序**：  
  1. 紧急处理Issue #1212，提供临时解决方案或明确路线图。  
  2. 推进PR #1209/#1213合并，增强本地推理能力。  
- **社区沟通**：在README中补充时间窗口功能的说明，减少用户误解风险。

</details>

<details>
<summary><strong>AstrBot</strong> — <a href="https://github.com/AstrBotDevs/AstrBot">AstrBotDevs/AstrBot</a></summary>

---

# **AstrBot 项目日报（2026-05-25）**

---

## 1. **今日速览**
- 过去24小时内，AstrBot 社区活跃度较高，共更新 **12条 Issues**（新开/活跃10条，关闭2条）和 **9条 PR**（待合并7条，已合并/关闭2条），无新版本发布。
- 核心问题集中在 **平台稳定性**（如 Telegram 适配器连接池耗尽）、**功能扩展**（如 QQ 分段回复支持、文件下载安全加固）及 **API 兼容性**（Anthropic 工具选择格式）。
- 开发者响应迅速，已有多个关键修复和功能增强 PR 提交，表明团队正积极应对社区反馈。

---

## 2. **版本发布**
- **无新版本发布**。

---

## 3. **项目进展**
### ✅ **合并/关闭的 PR**
- **[PR #8318](https://github.com/AstrBotDevs/AstrBot/pull/8318)**  
  - **内容**：修复 `File` 消息段远程下载时文件名未清洗的问题，避免路径异常（如 `/` 或空字节导致目录创建失败）。  
  - **关联 Issue**：[#8317](https://github.com/AstrBotDevs/AstrBot/issues/8317)  
  - **影响范围**：所有依赖文件转发的平台（如 QQ、Telegram）。

- **[PR #8316](https://github.com/AstrBotDevs/AstrBot/pull/8316)**  
  - **内容**：修复 QQ/NapCat 引用消息中媒体段（语音/视频/文件）无法被正确消费的问题。  
  - **关联 Issue**：[#8049](https://github.com/AstrBotDevs/AstrBot/issues/8049)

---

## 4. **社区热点**
### 🔥 **高互动 Issues**
- **[Issue #8314](https://github.com/AstrBotDevs/AstrBot/issues/8314)**  
  - **问题**：Telegram 适配器因连接池耗尽导致静默丢包，需手动重启。  
  - **诉求**：用户希望增加定时重启适配器的自动恢复机制。  
  - **进展**：已有修复 PR [#8320](https://github.com/AstrBotDevs/AstrBot/pull/8320) 提交，预计近期合并。

- **[Issue #8319](https://github.com/AstrBotDevs/AstrBot/issues/8319)**  
  - **问题**：Anthropic API 的 `tool_choice` 参数格式错误（应为 `{"type": "auto"}`，但传入了字符串 `"auto"`）。  
  - **严重性**：P0级，直接影响 Anthropic 提供商可用性。  
  - **进展**：需等待 PR 合并。

---

## 5. **Bug 与稳定性**
### ⚠️ **关键 Bug**
| Issue | 描述 | 状态 |
|-------|------|------|
| [#8314](https://github.com/AstrBotDevs/AstrBot/issues/8314) | Telegram 适配器连接池耗尽导致消息丢失 | **Fix PR 已提交** ([#8320](https://github.com/AstrBotDevs/AstrBot/pull/8320)) |
| [#8317](https://github.com/AstrBotDevs/AstrBot/issues/8317) | 文件下载未清洗文件名导致路径异常 | **Fix PR 已合并** ([#8318](https://github.com/AstrBotDevs/AstrBot/pull/8318)) |
| [#8275](https://github.com/AstrBotDevs/AstrBot/issues/8275) | 启动时报错 `KeyError: 'type'` | 未解决，需进一步排查 |

---

## 6. **功能请求与路线图信号**
### 🔮 **高优先级需求**
- **QQ 分段回复支持**（[#8297](https://github.com/AstrBotDevs/AstrBot/issues/8297)）：  
  用户指出代码中 QQ 平台被屏蔽，但修改后未生效，需深入检查逻辑。已有 PR [#8152](https://github.com/AstrBotDevs/AstrBot/pull/8152) 在增强 SubAgent 能力，可能间接涉及。
  
- **自定义分段符号**（[#8313](https://github.com/AstrBotDevs/AstrBot/issues/8313)）：  
  针对非流式平台的分段回复优化，可提升用户体验，暂无直接 PR。

- **Google Vertex AI 支持**（[#7781](https://github.com/AstrBotDevs/AstrBot/issues/7781)）：  
  用户愿意提交 PR，需跟进。

---

## 7. **用户反馈摘要**
- **痛点**：  
  - Telegram 长时间运行后消息丢失（需自动恢复机制）。  
  - 文件下载安全性不足（路径注入风险）。  
- **满意点**：  
  - 灾害预警插件（[#3927](https://github.com/AstrBotDevs/AstrBot/issues/3927)）集成多数据源，获广泛认可。  
- **场景**：  
  - 群管理插件（如 [#8305](https://github.com/AstrBotDevs/AstrBot/issues/8305)）需求强烈，涉及广告/敏感内容审核。

---

## 8. **待处理积压**
### ⏳ **长期未响应项**
- **关键 Issue**：  
  - [#8275](https://github.com/AstrBotDevs/AstrBot/issues/8275)（启动报错 `KeyError: 'type'`）——需优先排查配置兼容性问题。  
- **低优先级 PR**：  
  - [#8226](https://github.com/AstrBotDevs/AstrBot/pull/8226)（长时记忆重构）——技术复杂度高，需评估进度。

---

**总结**：AstrBot 当前处于高活跃修复期，重点解决平台稳定性和核心功能扩展，社区反馈积极。建议优先合并 Telegram 适配器修复和文件下载安全补丁，同时推进 QQ 分段回复等高频需求。

</details>

---
*本日报由 [Big Model Radar](https://github.com/ivanweng2077/big_model_radar) 自动生成。*