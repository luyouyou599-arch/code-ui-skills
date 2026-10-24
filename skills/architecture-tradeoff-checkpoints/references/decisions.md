# 按需选择的架构取舍

| 触发条件 | 关键选择与易漏项 | 应取得的证据 |
| --- | --- | --- |
| 重复读取成本高，考虑加缓存 | 明确允许陈旧多久、谁负责失效、未命中和缓存故障如何处理；不能默认 TTL 就能保证实时一致 | 真实访问模式、命中/未命中路径、写后读取行为与故障测试 |
| 高峰任务压垮处理方，考虑异步 | 用户能否接受稍后完成？如何获取最终状态、限制积压、处理失败与可能的重复投递？入队不等于业务成功 | 生产/消费速率、积压时间、状态流及失败处理记录 |
| 系统慢，考虑扩容或提高并发 | 先区分单次延迟、吞吐量、排队与下游容量；平均吞吐增加不等于尾延迟改善 | 同等负载条件下的阶段耗时、延迟分布和错误率 |
| 考虑拆分微服务 | 是否确有独立部署/扩缩或团队边界需求？考虑跨服务调用、数据一致性与排障成本 | 实际模块依赖、部署频率、数据归属与可观测性；先比较保持单体的方案 |

这些是工程应用建议，不是所有项目必做项。具体指标由项目目标确定，不能将视频中的概念对比当作无需条件的选型结论。

技术依据（2026-10-24 核对）：[Microsoft Cache-Aside](https://learn.microsoft.com/en-us/azure/architecture/patterns/cache-aside) 讨论缓存有效期与不保证一致性的条件；[Queue-Based Load Leveling](https://learn.microsoft.com/en-us/azure/architecture/patterns/queue-based-load-leveling) 讨论削峰、消费能力和积压代价；[Microservices](https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/microservices) 讨论独立部署、数据归属与运维结构。应用到其他平台时沿用问题分析，不照搬 Azure 产品选型。

来源：[十五项系统权衡](https://www.xiaohongshu.com/explore/6a70a7a400000000270234d1)、[十二项架构概念](https://www.xiaohongshu.com/explore/69a43acc000000001a030f74)。仅抽查概览矩阵，未取得字幕或音轨。已选取其中与当前用途直接有关的四组；其余不视为已核验的架构方案。未执行压测、迁移或真实项目行为验证。
