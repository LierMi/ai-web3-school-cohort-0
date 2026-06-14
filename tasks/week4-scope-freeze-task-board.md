# Week 4｜Build Sprint｜Scope Freeze 与任务看板

**任务**：确认 Week 4 最小可验证主流程，并完成任务看板拆分  
**学分**：10  
**完成时间**：2026-06-14  
**项目**：Digital Pompeii｜数字庞贝  
**项目仓库**：https://github.com/10yu7ian/digital-pompeii  
**参考材料**：本地 `Week4_Sprint_Plan.md`、`Minimum_Closed_Loop.md`

## 1. Scope Freeze

Week 4 只做一个最小可验证主流程：

> 合约地址 / 事故案例 → AI Agent 链上调查 → 结构化 JSON → 博物馆展品展示 → Demo 讲解

本周不扩展复杂功能，不追求完整商业系统，不做实时链上监控。优先保证评委能在 3–5 分钟内看懂：

- 项目解决什么问题
- AI Agent 如何调查链上事故
- Web3 证据如何被复核
- 博物馆式展示如何服务公共教育
- 哪些是真实完成，哪些是 mock / cut

## 2. 最小可验证主流程

1. 用户进入 Digital Pompeii 首页。
2. 首页展示真实链上事故展品卡片。
3. 用户点击一个案例进入详情页。
4. 页面展示事故死因、损失金额、证据强度、合约地址、技术尸检和策展说明。
5. 用户打开 Agent Investigation Console，查看 AI 验尸官多轮调查日志。
6. Demo 中说明链上数据来源、GLM-5.1 调用位置、证据可复查方式和当前风险边界。

验证标准：

- 浏览器可以打开博物馆页面。
- 至少 1 个真实案例可以完整展示。
- Agent 调查日志可以被回放或展示。
- README 能说明本地运行方式、架构、数据来源和风险边界。
- 不提交私钥、助记词、API Key、token、`.env` 等敏感信息。

## 3. Must-have

| 任务 | Owner | Deadline | 验证方式 | 状态 |
| --- | --- | --- | --- | --- |
| 前端接通 `data/exhibits.json`，首页展示真实展品 | Riso | Week 4 Day 4 | 浏览器能看到展品卡片 | 已完成 |
| 点击展品进入详情页，展示真实字段 | Riso | Week 4 Day 4 | `death_cause`、`evidence`、合约地址、损失金额正常渲染 | 已完成 |
| 至少 1 个案例用真实 GLM / Agent 调查流程跑通 | Clara | Week 4 Day 5 | `runs/` 中有 JSONL 调查日志，且输出单案 JSON | 已完成 |
| 生成合并展品数据 `data/exhibits.json` | Clara | Week 4 Day 5 | 前端能读取并渲染多案例数据 | 已完成 |
| Agent 调查日志回放面板 | Riso | Week 4 Day 6 | 能看到工具调用、假设提出、修正和最终结案过程 | 已完成 |
| README 补全架构、运行方式、GLM 调用位置、Web3 证明和安全边界 | Clara / Riso | Week 4 Day 7 | 评委可通过 README 理解项目并本地运行 | 已完成 |
| 3–5 分钟 Demo Story / 路演脚本 | Riso | Week 4 Day 7 | 脚本覆盖问题、主流程、技术亮点、mock / 风险边界 | 已完成 |
| 提交前敏感信息检查 | Riso / Clara | Week 4 Day 7 | `.env` 不入库，README 不暴露 key / token / 私钥 | 已完成 |

## 4. Should-have

| 任务 | Owner | Deadline | 验证方式 | 状态 |
| --- | --- | --- | --- | --- |
| 跑通 5 个真实链上事故案例 | Clara | Week 4 Day 6 | `data/` 中包含 5 个案例 JSON，`exhibits.json` 合并成功 | 已完成 |
| 增加事实核查文档 `FACT_CHECK.md` | Clara / Riso | Week 4 Day 7 | 关键金额、死因、时间和外部资料有核查记录 | 已完成 |
| 优化博物馆视觉体验 | Riso | Week 4 Day 5–7 | 页面具有“灾难博物馆 / 链上废墟”氛围 | 已完成 |
| 增加“入坑前，先体检”免费合约体检入口 | Riso | Week 4 Day 7 | 用户可粘贴合约地址获得风险提示 | 已完成 |
| 增加 OpenTimestamps 报告哈希凭证 | Clara | Week 4 Day 7 | `data/*.json.ots` 可作为可选存证材料 | 已完成 |

## 5. Nice-to-have

| 任务 | Owner | Deadline | 验证方式 | 状态 |
| --- | --- | --- | --- | --- |
| 3D 沉浸式展馆 | Riso | Post-hackathon | 可在浏览器中沉浸式浏览事故展品 | 延后 |
| 社区共同策展 | Riso / Clara | Post-hackathon | 研究者或审计员可提交新事故档案 | 延后 |
| 更完整的资金流可视化 | Clara / Riso | Post-hackathon | 能展示攻击资金路径图 | 延后 |
| 防猝死指数 Anti-Sudden-Death Index | Clara / Riso | Post-hackathon | 对新项目输出结构化风险评分 | 延后 |
| 钱包 / dApp 签名前提醒 | Clara / Riso | Post-hackathon | 在授权、mint、swap、bridge 前给出风险提示 | 延后 |

## 6. Cut / Mock 决策

| 功能 | 决策 | 原因 | 替代方案 |
| --- | --- | --- | --- |
| 现场实时跑完整 Agent 调查 | Mock / 预生成 | 真实 API 和 Etherscan 可能受限速、网络和 token 成本影响 | 使用已生成的 `runs/` JSONL 日志回放 |
| WebSocket 实时调查流 | Cut | 时间不足，且不是最小主流程必须项 | 使用静态 runs 日志模拟调查过程 |
| 完整 3D 展馆 | Cut | 会消耗大量前端时间，影响主流程稳定性 | 保留 2D 黑暗博物馆风格 |
| 付费系统 / 商业闭环 | Cut | 黑客松阶段重点是验证问题和技术主流程 | README 中说明商业路线 |
| 完整审计能力 | Cut | 项目定位不是替代专业审计 | 明确为“风险信号层”和“事故解释层” |
| 批量实时监控新项目 | Cut | 超出 Week 4 范围 | 作为下一步路线 |

## 7. 红线

以下内容没有 fallback，必须完成：

1. 博物馆页面能展示真实展品。
2. 至少一个案例有可复查的 Agent 调查日志。
3. README 说明项目主流程、技术架构、运行方式和风险边界。
4. 不提交 `.env`、API Key、私钥、助记词、token 或其他敏感信息。
5. Demo 只讲一个主流程，不发散到未完成的大功能。

## 8. 最终状态

Week 4 的 Scope Freeze 已完成。项目最终选择围绕“链上灾难博物馆 + AI 验尸官 + 调查日志回放 + 免费合约体检”这一条主流程进行展示。

已完成内容足够支撑 Demo Day：

- 有线上 Demo。
- 有项目 README。
- 有 5 个真实链上事故案例。
- 有 Agent 调查日志。
- 有事实核查材料。
- 有明确 cut / mock 边界。

## 可复查材料链接

- 项目仓库：https://github.com/10yu7ian/digital-pompeii
- 线上 Demo：https://digital-pompeii.vercel.app
- README：https://github.com/10yu7ian/digital-pompeii/blob/main/README.md
- Demo Script：https://github.com/10yu7ian/digital-pompeii/blob/main/DEMO_SCRIPT.md
