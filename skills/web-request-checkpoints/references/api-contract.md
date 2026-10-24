# API 契约与诊断

按当前功能选择检查，不强制既有项目更换版本或分页方案。

| 场景 | 关键决策与易漏项 | 验证方法 |
| --- | --- | --- |
| 新接口或字段 | 明确输入类型、范围、缺省/空值和错误输出；服务端验证与界面即时反馈各自承担职责 | 合法、缺失、错误类型和边界输入；检查业务结果及错误契约 |
| 修改现有接口 | 字段改名、类型或默认语义变化可能影响旧客户端；版本号本身不证明兼容 | 对照已使用的请求/响应，运行旧客户端契约和回归场景 |
| 返回集合 | 明确页大小限制、排序、下一页/终点及条件变更时的游标语义；部分结果不能冒充全部结果 | 首尾页、空页、条件切换、重复排序值及约定中的数据变化 |
| 接收异步回调 | 确认来源验证、事件类型、持久化与处理的边界以及重复投递的副作用 | 在提供方测试环境验证无效签名、重复事件、处理失败；不照搬别的平台响应时限 |
| 接口慢或偶发失败 | 用请求关联信息和时序区分客户端、网络、服务端、数据库与外部依赖 | 比较实际请求与 trace/span；注意并行和嵌套，不能简单把所有耗时相加；按证据选择优化 |

集合接口被用于自动加载/预取时，调用方还需区分查询身份、进行中的请求、失败重试和终点，避免重复请求导致重复追加或筛选改变后混入旧页。用快速触底、迟到响应和失败重试核对；客户端去重不能代替正确的服务端排序与游标语义。工程补充由 [加载配文](https://www.xiaohongshu.com/explore/6aca1855000000001303fcca) 的提前加载场景引出，正文已读，未执行真实分页接口验证。

工程建议以目标接口契约和框架为准。日志与诊断信息要足以关联问题，避免记录完整凭据或无关个人数据。只缺少证据时补观测，不先加入缓存、并行或重试来掩盖问题。

核验日期：2026-10-24。

- [Google AIP-180](https://google.aip.dev/180)：源、传输和语义兼容性；其 Protobuf/Google API 细节不直接套用其他接口。
- [Google AIP-158](https://google.aip.dev/158)：集合分页、游标与结束信号；使用项目自己的契约，不强制 Google 字段名或页大小。
- [OWASP Input Validation](https://cheatsheetseries.owasp.org/cheatsheets/Input_Validation_Cheat_Sheet.html)：跨信任边界与服务端校验。
- [GitHub Webhook 实践](https://docs.github.com/en/webhooks/using-webhooks/best-practices-for-using-webhooks)：来源验证、事件和交付识别是该平台例子；其他平台需核对自己的契约。
- [OpenTelemetry Traces](https://opentelemetry.io/docs/concepts/signals/traces/)：关联操作与分阶段观测。

网络媒体来源：[API 概念矩阵](https://www.xiaohongshu.com/explore/6a70a83c0000000024025e24)、[API 设计图](https://www.xiaohongshu.com/explore/691b46d50000000004028b23)、[慢接口排查图](https://www.xiaohongshu.com/explore/69208e69000000001e0301ac)。仅抽查概览帧，未取得字幕或音轨。上表的工程验证由整理者补充；未执行真实 API 测试。
