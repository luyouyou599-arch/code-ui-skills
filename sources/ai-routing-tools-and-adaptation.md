# AI 任务适配、路由与执行的局部补读

来源类别：网络媒体；主分类：开发工具与工程实践 / AI 验收。整理日期：2026-10-24。面向已有模型、检索、分类或工具功能的开发者，需实际任务、失败例、调用记录和项目约束。

**读取状态：4 篇均未完整读取。** 下表列离散画面，不代表这些时间点之间连续观看；未获得完整音轨或逐句字幕。仅把已观察线索与一手依据支持的检查点并入技能，整篇阅读任务继续待补读。配文均简短，不能独立支持技术结论。评论区 AI 总结未用作依据。

| 原文 | 时长 | 累计确认画面 | 实际可保留的来源线索 |
| --- | --- | --- | --- |
| [微调与 RAG](https://www.xiaohongshu.com/explore/6ad746cd000000002901168d) | 03:06 | 00:00、00:12、00:57、01:51、01:53、02:43 | 白板及字幕涉及两种方法、准备成本和专业任务；“99% 公司用不到微调”无核验依据，不采用 |
| [RAG 准确性](https://www.xiaohongshu.com/explore/6ace082b000000000a0226b5) | 04:06 | 00:00、01:08、01:13、01:20、02:27、02:34、03:35 | 可见检索架构、生成侧、上下文完整与兜底分层线索；手写细项并未全部读清，不补写为完整方案 |
| [Function Call](https://www.xiaohongshu.com/explore/6aca0d09000000001303f322) | 02:37 | 00:00、00:07、00:40、00:57、01:12、01:18、02:12、02:25 | 自然语言地点到函数参数的示例及 Tools/LLM/Function 关系；00:40 字幕提及多个工具，01:12 提及描述；视频未完整读取，具体执行契约以下方文档为准 |
| [意图识别](https://www.xiaohongshu.com/explore/6ac8733e000000001403901a) | 04:59 | 00:00、00:10、01:50、02:08、02:39、02:56、04:21 | 白板区分意图识别与生成/推理，并有不同处理分工示意；未验证性能、准确率、必要模型或代理数量 |

## 合并的开发用途

合并到 [AI 功能评测技能](../skills/ai-workflow-evaluation-checkpoints/SKILL.md) 的 [适配、路由与执行参考](../skills/ai-workflow-evaluation-checkpoints/references/adaptation-routing-execution.md)，不新增技能。

工程补充强调：先按失败原因比较提示、资料检索与任务训练的作用；对检索结果与回答完整性分别判断；分类必须测未知/歧义与误路由；工具参数生成与执行结果分开验收。可执行的测试样本、权限与副作用检查是整理者推导，不声称这些视频已完整讲授。

## 一手核验与边界

2026-10-24 实际读取：

- [Google Cloud 应用开发](https://docs.cloud.google.com/docs/ai-ml/generative-ai/develop-generative-ai-application)：核对检索补充上下文与任务调优的用途；不将二者强分为互斥选择，也不把特定调优方案写成默认要求。
- [Microsoft RAG evaluators](https://learn.microsoft.com/en-us/azure/foundry/concepts/evaluation-evaluators/rag-evaluators?view=foundry)：区分检索过程、回答依据一致性与完整性。方法不绑定其评分器或默认阈值。
- [Claude 工具执行契约](https://platform.claude.com/docs/en/agents-and-tools/tool-use/how-tool-use-works)：自定义客户端工具由应用执行并回传结果；服务端托管工具另有执行方，不能笼统说所有工具均由客户端运行。
- [TypeSafe 意图路由](https://docs.typesafe.ai/patterns/intent-routing) 与 [confidence](https://docs.typesafe.ai/confidence)：核对分类到确定代码/专门模型/人工路径，以及按任务风险验证阈值；confidence 不作为正确率证明，示例数字不直接入门禁。

未调用模型或第三方业务工具，未运行评测、训练或真实项目回归。阅读缺口仍是完整视频内容，不用官方资料替代后宣称视频已读完。

## 2026-10-26 补读

重新打开四篇视频，新增离散画面如上表；不是连续字幕阅读。微调、RAG 与意图识别的新增画面未形成足够的新增结论，保留原有条件与未验证项。Function Call 的工具数量和描述线索，结合 [官方工具定义文档](https://platform.claude.com/docs/en/agents-and-tools/tool-use/define-tools) 核对用途、输入和限制，将相邻工具误选、无需调用及缺参任务的对照样本合并至现有 AI 验收技能。工具描述的检查与样本设计属于整理者工程推导，不声称视频已完整讲授。

页面无可读字幕轨，本次受支持的视频下载也未成功；仍未取得连续字幕或完整音轨。四篇均继续待补读，未新增“完整视频已读”状态。未调用模型或运行工具选择评测；只做资料核验及技能结构检查。
