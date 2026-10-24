# 库存预留的原子性与恢复边界

主分类：系统设计。标签：后端、并发、库存、Redis、数据库。面向实现库存或名额功能的开发者；需理解事务与业务结果。来源类别：网络媒体。整理日期：2026-10-24。

原文：[数据库 update 减 1，秒杀会超卖吗？](https://www.xiaohongshu.com/explore/6ab3d5fc00000000120376c5)。视频 02:31，正文只有标签。实际抽查：01:12 画面提出活动前初始化 Redis 库存；01:47 画面明确分离查询/扣减的竞争及将判断和扣减放进原子脚本；另见数据库行锁排队插图但未核对其精确时间。未完整观看或获取字幕/音轨。

保留“检查和修改不可被并发穿插”的核心，不从片段推导唯一选型。Redis 原子脚本不是与订单数据库之间的共同事务，也不自动保证同一用户请求不重复扣减；活动结束回写的示意不足以证明中断时可恢复。

补充为已有 [architecture-tradeoff-checkpoints](../skills/architecture-tradeoff-checkpoints/SKILL.md) 的 [库存一致性参考](../skills/architecture-tradeoff-checkpoints/references/reservation-consistency.md)，用于数据归属、请求去重、预留释放、补偿与对账取舍。后几项为整理者工程推导；2026-10-24 以 Redis Lua 官方文档和 PostgreSQL 18 隔离文档核验边界。未执行 Redis、数据库并发、负载或故障测试，不将示例容量当作真实指标。
