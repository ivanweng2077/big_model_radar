# AI 开源趋势日报 2026-05-23

> 数据来源: GitHub Trending + GitHub Search API | 生成时间: 2026-05-23 02:32 UTC

---

---

# **AI 开源趋势日报（2026-05-23）**

---

## **今日速览**
- **Agent 工具爆发**：今日 Trending 榜单中，多个 AI Agent 相关项目（如 `claude-plugins-official`、`codegraph`、`oh-my-pi`）获得显著增长，表明开发者对「智能体+工具链」集成需求激增。
- **RAG 生态活跃**：主题搜索中 RAG 类项目（如 `dify`、`ragflow`）占据头部，凸显企业级知识管理工具的热度。
- **本地化与隐私优先**：如 `anything-llm`、`LEANN` 等强调本地部署和隐私保护的项目持续受关注，反映用户对数据自主权的重视。

---

## **各维度热门项目**

### **🔧 AI 基础工具**
1. **[vllm-project/vllm](https://github.com/vllm-project/vllm)**  
   - Stars: 80.7k (+)  
   - 高性能推理引擎，支持多模型并行，优化显存利用率，适合生产环境部署。

2. **[ollama/ollama](https://github.com/ollama/ollama)**  
   - Stars: 172.6k (+)  
   - 轻量级本地大模型运行框架，支持多种模型一键部署，降低本地使用门槛。

3. **[firecrawl/firecrawl](https://github.com/firecrawl/firecrawl)**  
   - Stars: 123.1k (+)  
   - 基于 AI 的网页抓取与清洗工具，为 Agent 提供结构化数据输入。

---

### **🤖 AI 智能体/工作流**
1. **[NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent)**  
   - Stars: 163.2k [topic:ai-agent]  
   - 自进化智能体框架，支持多模态任务，社区最活跃的 Agent 项目之一。

2. **[ruvnet/ruflo](https://github.com/ruvnet/ruflo)**  
   - Stars: 54.2k [topic:ai-agent]  
   - 企业级 Agent 编排平台，集成 Claude Code/Codex，支持多智能体协同。

3. **[shareAI-lab/learn-claude-code](https://github.com/shareAI-lab/learn-claude-code)**  
   - Stars: 62.0k [topic:ai-agent]  
   - 从零构建 Claude Code 风格 Agent 的脚手架，适合快速原型开发。

---

### **📦 AI 应用**
1. **[FinceptTerminal/FinceptTerminal](https://github.com/Fincept-Corporation/FinceptTerminal)**  
   - Stars: 367 (+)  
   - 金融领域 AI 分析终端，整合市场数据与决策工具，面向量化投资场景。

2. **[santifer/career-ops](https://github.com/santifer/career-ops)**  
   - Stars: 46.7k [topic:ai-agent]  
   - AI 驱动的求职系统，支持技能匹配与简历生成，覆盖全链路招聘流程。

3. **[zhayujie/CowAgent](https://github.com/zhayujie/CowAgent)**  
   - Stars: 44.7k [topic:ai-agent]  
   - 微信/钉钉等多平台接入的超级 AI 助理，支持主动规划与长期记忆。

---

### **🧠 大模型/训练**
1. **[jingyaogong/minimind](https://github.com/jingyaogong/minimind)**  
   - Stars: 50.4k [topic:llm-model]  
   - 从 0 训练 64M 参数小模型，展示低成本微调可行性。

2. **[skyzh/tiny-llm](https://github.com/skyzh/tiny-llm)**  
   - Stars: 4.2k [topic:llm-model]  
   - Apple Silicon 上轻量化 LLM 推理教程，适合边缘设备部署。

3. **[open-compass/opencompass](https://github.com/open-compass/opencompass)**  
   - Stars: 7.0k [topic:llm-model]  
   - 多模型评测平台，支持 100+ 数据集，推动模型性能对比研究。

---

### **🔍 RAG/知识库**
1. **[langgenius/dify](https://github.com/langgenius/dify)**  
   - Stars: 142.3k [topic:rag]  
   - 企业级 RAG 平台，支持 Agent 工作流与可视化开发。

2. **[infiniflow/ragflow](https://github.com/infiniflow/ragflow)**  
   - Stars: 81.1k [topic:rag]  
   - 融合 Agent 能力的领先 RAG 引擎，支持复杂上下文管理。

3. **[mem0ai/mem0](https://github.com/mem0ai/mem0)**  
   - Stars: 56.5k [topic:rag]  
   - 通用内存层，为 Agent 提供持久化知识存储与检索。

---

## **趋势信号分析**
- **Agent 工具链爆发**：今日 Trending 中 7 个项目涉及 Agent 插件、代码图谱、CLI 集成（如 `claude-plugins-official`、`oh-my-pi`），反映开发者正加速将 Agent 嵌入开发全流程，尤其是与 Claude Code 生态的深度绑定。
- **新兴技术栈**：首次登榜的 `RuView`（WiFi 信号转空间感知）和 `Understand-Anything`（交互式知识图谱）展示了 AI 在边缘计算与代码理解中的创新应用。
- **行业关联**：近期 Anthropic 发布 Claude 3.5 后，其官方插件目录（`claude-plugins-official`）和第三方工具（`codegraph`）迅速升温，印证了生态工具链的协同效应。

---

## **社区关注热点**
- **`oh-my-pi` (https://github.com/can1357/oh-my-pi)**  
  — 终端级 AI 编码代理，支持哈希锚点编辑与子代理协作，适合本地开发场景。
- **`LEANN` (https://github.com/yichuan-w/LEANN)**  
  — 设备端高效 RAG 方案，97% 存储节省，推动隐私敏感领域的落地。
- **`dify` (https://github.com/langgenius/dify)**  
  — 企业级 RAG+Agent 一体化平台，支持低代码配置，适合快速构建业务系统。
- **`firecrawl` (https://github.com/firecrawl/firecrawl)**  
  — 网页数据清洗工具，为 Agent 提供高质量结构化输入，解决信息获取瓶颈。

--- 

**总结**：今日 AI 开源生态呈现「Agent 工具链爆发 + RAG 企业级落地 + 本地化部署」三大主线，开发者需重点关注智能体与知识管理的融合方向。

---
*本日报由 [Big Model Radar](https://github.com/ivanweng2077/big_model_radar) 自动生成。*