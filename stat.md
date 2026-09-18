# Benchmark 统计（readme 模型集）

调研时间：2026 年 9 月。对应 [readme.md](./readme.md) 目的：从常见旗舰出发，判断**哪些榜值得跟、哪些榜容易让人「下完权重就这」**。

## 统计范围

**模型集（9 款，readme 明文列出）**

| # | 模型 |
|---|------|
| 1 | [Qwen3.8-2.4T-A95B](https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B) |
| 2 | [DeepSeek-V4.1-Flash](https://huggingface.co/deepseek-ai/DeepSeek-V4.1-Flash) |
| 3 | [Hy4-preview](https://huggingface.co/tencent/Hy4-preview) |
| 4 | [Kimi-K3](https://huggingface.co/moonshotai/Kimi-K3) |
| 5 | [GLM-5.3](https://huggingface.co/zai-org/GLM-5.3) |
| 6 | [Ornith-1.5-397B](https://huggingface.co/ornith-ai/Ornith-1.5-397B) |
| 7 | [Qwen3.8-Flash-Next](https://huggingface.co/Qwen/Qwen3.8-Flash-Next) |
| 8 | GPT-6 Astra（闭源 API） |
| 9 | Claude Fable 5（闭源 API） |

readme 中的「其他的旗舰模型」**不纳入**跑分计数；全榜另有数百模型时，仅在备注中说明，不写入「跑分的模型数」。

**列含义**

- **跑分的模型数**：上表 9 款中，该 benchmark 有**可查分数**的个数，记为 **N/9**（缺分常见原因：未评测、未公开、或仅 base/instruct 一侧有表）。
- **表现最好的模型**：仅在上述 9 款里取最高分；括号内为分数及来源类型（AA 独立 / 厂商自报 / 模型卡同表）。
- **排序**：按**值得参考程度**从高到低（综合第三方、工程向、区分度、与部署体验相关性）；参考价值低的考试类、饱和榜、 harness 敏感榜靠后。

**分数口径（斟酌后的统一规则）**

1. 同一 benchmark 优先采用**同一张对照表**里的数字（如 DeepSeek README 对标表、Hy4 附录、GLM-5.3 博客表、Ornith README）。
2. Qwen3.8-2.4T-A95B 若无单独行，暂用 **Qwen3.8-Max 自报**（同源权重），并在备注标明；A95B 有 **Artificial Analysis（AA）** 独立分时优先用 AA。
3. Fable 5 与 Fable 5.1 并存时，readme 写 Fable 5，表中用 **Fable 5** 分数；若仅 5.1 有独立榜条目，备注说明。
4. 不跨 harness 比较时，在备注写明；**不因单榜高低推荐下载某百 G 权重**。

---

## 总表（按值得参考程度排序）

| benchmark | 类型 | 简介 | 跑分的模型数 | 表现最好的模型 | 备注 |
|-----------|------|------|-------------|----------------|------|
| Artificial Analysis Intelligence Index v4.3 | 综合指数 | AA 固定协议合成约 10 项（办公、终端 4.0、科学代码、HLE、长上下文、事实性等） | 7/9 | **GPT-6 Astra**（61.2，AA 独立） | **参考价值：极高**。开源最高多为 **Qwen3.8-2.4T-A95B 57.7**；Kimi 44、GLM-5.3 45、DeepSeek V4.1 40、Flash-Next 39.9。Hy4、Ornith 暂无完整 AA 条目。**选总榜优先信 AA，不信单榜标题。** |
| Artificial Analysis Coding Agent Index v1.1 | 综合指数 | AA 在 Codex / Claude Code / Muse Code 等各自 harness 下测编码 Agent 后合成 | 4/9 | **GPT-6 Astra**（67，AA 独立） | **参考价值：极高**。Fable 5 约 77、Muse/ Sol 更高（未列入本 9 款）。9 款开源里 TB/DeepSWE 分项常与此指数不一致 → 说明「编码 Agent」必须看子榜。** |
| DeepSWE v1.1 | 编码 Agent | 真实 GitHub issue 修复，公开 leaderboard | 9/9 | **DeepSeek-V4.1-Flash**（74.2，厂商表） | **参考价值：极高**。9 款全有分，跨度约 **56～74**（Ornith 56、Flash-Next 58.7、Qwen Max 56.6、Hy4 64.3、GLM 66.9、Kimi 67.5、Fable 69.7、Astra 74.1）。**比 GPQA 更能预测「改仓行不行」。** harness：mini-SWE / Kimi Code / DSH 等不一。 |
| SWE-bench Pro | 编码 | 高难度 SWE、长上下文、修真实仓库 | 7/9 | **Claude Fable 5**（80.0%，厂商/聚合） | **参考价值：高**。Qwen Max 67.7、Ornith 65.1、Hy4 65.7、Kimi 63.3、Flash-Next 62.5；DeepSeek V4.1 无同表。补丁提取与 Agent 循环敏感，**看趋势不看 1pt**。 |
| SWE-bench Verified | 编码 | 社区最常用 SWE 榜之一 | 5/9 | **Claude Fable 5**（95.0%，聚合） | **参考价值：高**。Kimi 86.2、Ornith 86.0、GLM-5.2 83（5.3 未同表）等；名头大但 harness 影响极大，**不宜单独决定下载**。 |
| Terminal-Bench 4.0 | 编码 Agent | 新一代终端难任务（AA Intelligence 子项） | 4/9 | **GPT-6 Astra**（57.9%，OpenAI 表） | **参考价值：高**。GLM-5.3 AA 独立约 41.9%；DeepSeek V4.1 31.2；Kimi 12.6。与 TB2.1 高分并存 → **老终端榜可能偏乐观**；选型应看 3/4 代。 |
| GDPval-AA v2 | Agent / 知识工作 | 模拟金融、法律等工作流，Elo（AA 子评测） | 5/9 | **Claude Fable 5**（1932 Elo，聚合） | **参考价值：高**。GLM-5.3 1769、Qwen Max 1717、Kimi 1686、Hy4 1678；DeepSeek/Ornith/Flash-Next 无同表。**9 款开源彼此极差常 <3%**，难二选一，但能筛弱模型。 |
| Terminal-Bench 3.0 | 编码 Agent | TB 难一代，avg@3、长时容器 | 5/9 | **Claude Fable 5**（33.7%，GLM 对标表） | **参考价值：高**。GPT-5.6 Sol 34.6（未入 9 款）；DeepSeek 30.0、GLM 28.3、Kimi 17.4。整体分低，**区分度优于 TB2.1**。 |
| Humanity's Last Exam（纯文本） | 推理 | 跨学科极难闭卷 | 7/9 | **Claude Fable 5**（59.0% 无工具，聚合） | **参考价值：中高**。Kimi 43.5、Ornith 44.6、Hy4 43.4、Qwen Max 43.6、DeepSeek 36.8、Flash-Next 35.9。比 GPQA 更能拉开差距，仍 ≠ 日常 Agent。 |
| SciCode | 科研编码 | 科学分步编程（AA 常收录） | 4/9 | **Kimi-K3**（58.7，Kimi README / AA） | **参考价值：中高**。Qwen A95B 51.6（AA）；Fable 5.1 更高（未计入 Fable 5 行）。偏科研，与业务 CRUD 距离远。 |
| AutomationBench | Agent | 桌面/工作流自动化（600 任务公开子集） | 6/9 | **DeepSeek-V4.1-Flash**（54.8，厂商表） | **参考价值：中高**。GLM 48.2、Kimi 46.7、Astra 41.4、Qwen 27.3、Fable 17.4（安全降级影响）。厂商 harness 差异大，宜对照 **AutomationBench-AA**。 |
| MCP-Atlas（public） | Agent / 工具 | MCP 工具调用（500 任务级） | 5/9 | **Kimi-K3**（84.2，Hy4 附录） | **参考价值：中**。Hy4 83.7、Qwen Max 81.9、Ornith 80.0；9 款内极差 ~4pt，**接近饱和带**。 |
| Terminal-Bench 2.1 | 编码 Agent | 终端多步任务（最常见宣传榜） | 8/9 | **DeepSeek-V4.1-Flash**（90.6，厂商表） | **参考价值：中**（常见但易误导）。Kimi 88.3、GLM 88.2、Fable 88.0、Ornith 86.1、Qwen Max 86.6、Hy4 85.4；Flash-Next 缺同表。**9 款带内仅 ~5pt**，标题党「碾压」不可信；harness 极不统一。 |
| SWE-bench Multilingual | 编码 | 非英语仓库修复 | 5/9 | **Hy4-preview**（82.9，Hy4 附录） | **参考价值：中**。Flash-Next 81.0、Kimi 80.8、Ornith 79.6；对**多语/中文代码库**仍有意义，区分度一般。 |
| NL2Repo-Bench | 编码 Agent | 自然语言生成可运行仓库 | 6/9 | **DeepSeek-V4.1-Flash**（64.0，厂商表） | **参考价值：中**。Ornith 59.5、Kimi/GLM 58.0、Qwen Max 55.9、Flash-Next 48.1。 |
| BrowseComp | Agent / 搜索 | 开放浏览检索（强依赖搜索策略） | 4/9 | **Kimi-K3**（91.2，Kimi README） | **参考价值：中**。Ornith 86.6；Hy4/GLM 在部分表 85+。**≠ 离线能力**；仅 Kimi/Ornith 等少数有分。 |
| CyberGym | 安全 / Agent | 网络安全演练类 Agent 任务 | 4/9 | **DeepSeek-V4.1-Flash**（88.1，厂商表） | **参考价值：中**（垂直）。GLM 84.5、Kimi 80.0、Fable 83.8。与通用编码不是同一需求。 |
| MathArena Apex 2025 | 数学 | 高难度数学竞赛型 | 5/9 | **Hy4-preview**（74.2，Hy4 附录） | **参考价值：中**。Qwen Max 72.8、Kimi 68.4、DeepSeek 65.6、Flash-Next 缺。9 款内理科**区分度较大**的一榜。 |
| Agents' Last Exam | Agent | 多步工具考试（官方 leaderboard） | 7/9 | **DeepSeek-V4.1-Flash**（31.8，厂商表） | **参考价值：中**。Fable 28.6、GLM 28.5、Kimi 28.3、Qwen 25.4、Hy4 22.8、Flash-Next 25.2。绝对分低，参测仍少。 |
| Toolathlon Verified | Agent | 工具athlon 验证集 | 5/9 | **Kimi-K3**（76.5，Kimi README） | **参考价值：中**。GLM 73.0、Flash-Next 73.5、Qwen 72.5、Ornith 71.2。 |
| AA-LCR v1.1 | 长上下文 | Agent 长上下文推理（AA） | 3/9 | **Qwen3.8-Flash-Next**（79.7，BenchLM/AA 聚合） | **参考价值：中**。Qwen A95B 75.3、Kimi 74.7。仅 3/9 有 AA 同项，其余缺。 |
| FrontierSWE / Frontier-Bench | 编码 | 前沿 SWE 或早期 Frontier-Bench | 4/9 | **Claude Fable 5**（FrontierSWE 88.2%，GLM 表） | **参考价值：中**。Kimi FrontierSWE 81.2、GLM 78.1、Qwen 73.5；Ornith Frontier-Bench v0.1 仅 13.5。**任务定义与版本不一，读脚注。** |
| SWE Atlas — Codebase Q&A | 编码 | 大规模代码库问答 | 4/9 | **Hy4-preview**（64.0，Hy4 附录） | **参考价值：中**。Ornith 55.6、Qwen Max 55.4、Kimi 35.2。 |
| LMArena Coding | 人类偏好 | 众包编码 Elo | 1/9 | **Kimi-K3**（1543，第三方） | **参考价值：中低**（主观）。仅 Kimi 在 9 款内有常引条目；与 DeepSWE 不一致时可解释「分数好但用着别扭」。 |
| AA-Omniscience | 事实性 | 幻觉 / 拒答 / 知识（AA） | 3/9 | **GPT-6 Astra**（相对 Sol 幻觉率大降，AA 文） | **参考价值：中**（可靠性）。Astra 相对 GPT-5.6 Sol 幻觉显著下降；Flash-Next 等有负向 Omniscience 条目。**部署「胡说」问题可瞄此榜。** |
| LiveCodeBench v6 | 编码 | 竞赛题、防污染代码生成 | 3/9 | **Qwen3.8-Flash-Next**（91.9%，模型卡） | **参考价值：中低**。Kimi 等有 LCB 条目；偏竞赛短题，与 Agent 改仓弱相关。 |
| Tau³-Banking | Agent / 金融 | 银行场景工具 Agent（AA） | 2/9 | **Qwen3.8-2.4T-A95B**（49.1%，AA） | **参考价值：低**（垂直）。Kimi 33.4。仅 2/9。 |
| IFBench | 指令遵循 | 复杂格式/约束遵循 | 2/9 | **Qwen3.8-Flash-Next**（81.3，模型卡） | **参考价值：低**。Qwen Max 82.8。对「听话」有用，与百 G 权重价值弱相关。 |
| GPQA Diamond | 推理 / 知识 | 研究生难度科学选择题 | 9/9 | **GPT-6 Astra**（96.0%，OpenAI 表；9 款独立表多为 90～94） | **参考价值：低（饱和）**。9 款几乎全 **90%+**（Kimi 93.5、Ornith 92.8、GLM 91.7、Flash-Next 91.7 等）。**最典型「榜很强、下载就这」误导源之一。** |
| MMLU-Pro | 知识考试 | 多选题知识（多为基础模型表） | 2/9 | **DeepSeek-V4.1-Flash**（74.1，base 表） | **参考价值：低**。Flash-Next 等在别的考试行有分；instruct 旗舰普遍偏高，**与 Agent 部署弱相关**。 |
| C-Eval | 知识考试 | 中文考试集（base） | 1/9 | **DeepSeek-V4.1-Flash**（92.1，base） | **参考价值：低**。仅 base 有分，与 9 款 instruct 部署不对齐。 |
| ProgramBench | 编码 | 竞赛式「Almost Solved」（Vals 等） | 7/9 | **Kimi-K3**（77.8，Kimi README） | **参考价值：慎用**。Hy4/GLM/DeepSeek/Qwen 在同 harness 表约 **17～20%**；Kimi 77.8 为 **Kimi Code**。**禁止**用此榜在 9 款间单分数排序。 |
| PaperBench | Agent / 科研 | 论文复现 Agent（长时） | 1/9 | **Qwen3.8-2.4T-A95B**（93.0，Max 自报） | **参考价值：慎用**。仅 Qwen 有分；Claude Code 5h 级设定。 |
| CoWorkBench | Agent / 办公 | 长程办公 Agent（Qwen 内测） | 1/9 | **Qwen3.8-Flash-Next**（73.9%，模型卡） | **参考价值：慎用**。厂商内测，无 9 款同表。 |
| 腾讯 203 工程任务盲评 | 厂商内测 | 专家盲评均分 /4 | 2/9 | **Hy4-preview**（2.99） | **参考价值：慎用**。Kimi 2.94 为对手分；非公开全榜，**不能外推排名**。 |
| Z.ai Code Bench 等厂商榜 | 厂商内测 | GLM _post-training 内测 | 1/9 | **GLM-5.3**（相对 5.2 +50%，博客） | **参考价值：慎用**。无 9 款横向；仅说明 GLM 迭代幅度。 |

---

## 结论（面向 readme 目的）

### 以后值得重点跟的榜（9 款内也有区分度）

1. **AA Intelligence Index + Coding Agent Index**（第三方、协议固定）  
2. **DeepSWE v1.1**（9/9 有分，跨度大，工程向）  
3. **SWE-bench Pro / Verified**（难，但必读 harness）  
4. **Terminal-Bench 3.0 / 4.0**（识别 TB2.1「虚高」；DeepSeek、Astra、GLM 与 Kimi 分化明显）  
5. **GDPval-AA v2**（办公向；9 款开源彼此极近，用于挡弱模型而非挑最强）  

### 建议降权或跳过

1. **GPQA、MMLU-Pro、C-Eval** 等考试类（9 款 instruct 普遍饱和）  
2. **Terminal-Bench 2.1** 单独决定下载（8/9 有分但带内仅 ~5pt）  
3. **ProgramBench**（同榜 harness 不一致时）  
4. **仅 1/9 有分的厂商长测**（PaperBench、CoWorkBench、LMArena 等）除非你的栈与之一致  

### 9 款模型在「高价值榜」上的粗定位（非购买建议）

| 模型 | 相对强项（高价值榜） | 需注意 |
|------|----------------------|--------|
| Qwen3.8-2.4T-A95B | AA 综合开源领先、GDPval、SWE-Pro、Tau³ | DeepSWE 自报偏低；多分数来自 Max 同表 |
| DeepSeek-V4.1-Flash | DeepSWE、TB2.1、TB3/4、AutomationBench | AA 综合 40；TB2.1 与 TB4 落差大 |
| Hy4-preview | SWE-Multilingual、MathArena、SWE Atlas | AA 未收录；ProgramBench 同表极低 |
| Kimi-K3 | BrowseComp、Toolathlon、SciCode、GPQA 带内最高之一 | TB4 低；成本高；部分榜绑 Kimi Code |
| GLM-5.3 | TB3、DeepSWE、GDPval 开源前列 | TB2.1 与 Kimi 持平；Cyber 向强 |
| Ornith-1.5-397B | TB2.1、SWE-Verified 接近 Opus 自报 | DeepSWE 仅 56；Frontier-Bench 很低；自报待复现 |
| Qwen3.8-Flash-Next | 参数量小、SWE-Multi/LCB/IF 表观强 | AA 综合 ~40；预览架构，非 A95B 替代 |
| GPT-6 Astra | AA 综合 & TB4、DeepSWE、幻觉改善 | 闭源；General AA 仅略升；价高于 Sol |
| Claude Fable 5 | SWE-Pro/Verified、GDPval、HLE 无工具 | TB2.1 低于 Sol/DeepSeek；安全降级影响部分 Agent 榜 |

---

## 数据来源

- 各模型 Hugging Face README / 官方博客（Qwen3.8、DeepSeek V4.1、Hy4、Kimi K3、GLM-5.3、Ornith-1.5、Flash-Next）  
- [Artificial Analysis](https://artificialanalysis.ai/)（Intelligence / Coding Index、子项）  
- [Hy4 附录转录](https://ai-tldr.dev/models/hunyuan-hy4-preview/)  
- OpenAI GPT-6 Astra / GPT-5.6 发布材料（Astra、Fable 5 部分对标）  
- 聚合站（BenchmarkList、BenchLM、LLM Boss）用于补全单模型 AA 分  

## 附录：9 款模型覆盖度（按跑分模型数降序）

| benchmark | 类型 | 跑分的模型数 |
|-----------|------|-------------|
| DeepSWE v1.1 | 编码 Agent | 9/9 |
| GPQA Diamond | 推理 / 知识 | 9/9 |
| Terminal-Bench 2.1 | 编码 Agent | 8/9 |
| Artificial Analysis Intelligence Index v4.3 | 综合指数 | 7/9 |
| SWE-bench Pro | 编码 | 7/9 |
| Humanity's Last Exam（纯文本） | 推理 | 7/9 |
| Agents' Last Exam | Agent | 7/9 |
| ProgramBench | 编码 | 7/9 |
| AutomationBench | Agent | 6/9 |
| NL2Repo-Bench | 编码 Agent | 6/9 |
| SWE-bench Verified | 编码 | 5/9 |
| GDPval-AA v2 | Agent / 知识工作 | 5/9 |
| Terminal-Bench 3.0 | 编码 Agent | 5/9 |
| MCP-Atlas（public） | Agent / 工具 | 5/9 |
| SWE-bench Multilingual | 编码 | 5/9 |
| MathArena Apex 2025 | 数学 | 5/9 |
| Toolathlon Verified | Agent | 5/9 |
| Artificial Analysis Coding Agent Index v1.1 | 综合指数 | 4/9 |
| Terminal-Bench 4.0 | 编码 Agent | 4/9 |
| SciCode | 科研编码 | 4/9 |
| BrowseComp | Agent / 搜索 | 4/9 |
| CyberGym | 安全 / Agent | 4/9 |
| FrontierSWE / Frontier-Bench | 编码 | 4/9 |
| SWE Atlas — Codebase Q&A | 编码 | 4/9 |