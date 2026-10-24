# 任务可发现性、恢复与操作效率

来源类别：网络媒体；媒介：视频配文。主分类：交互与可用性；交叉：产品规则、视觉层级、前端验收。整理日期：2026-10-24。适用于列表、选择、帮助、提交、批量管理与日期选择；需要用户任务、真实业务限制和组件行为。

## 来源及实际读取范围

- 网络媒体：[页面空着，别只写暂无数据](https://www.xiaohongshu.com/explore/6adc5558000000002b003441)
- 网络媒体：[九种车型摆一排，反而叫不上车](https://www.xiaohongshu.com/explore/6adb4f97000000002c010339)
- 网络媒体：[帮助文档写了40篇，用户还是不会](https://www.xiaohongshu.com/explore/6ad9fb90000000002c03abf1)
- 网络媒体：[报错只写「发布失败」，等于没说](https://www.xiaohongshu.com/explore/6ad8b29a000000002c014879)
- 网络媒体：[外卖结算页，会员按钮比下单还亮？](https://www.xiaohongshu.com/explore/6ad8ad3d0000000024034b92)
- 网络媒体：[删30个表情包，要点120下？](https://www.xiaohongshu.com/explore/6ad60d18000000002902c4e0)
- 网络媒体：[后两位是8K还是BK？别让人记](https://www.xiaohongshu.com/explore/6ad0b5b80000000015015558)
- 网络媒体：[想住两晚，退房却点了周日？](https://www.xiaohongshu.com/explore/6acf134b000000001c00f444)

以上 8 篇均完整读取正文配文，未完整观看视频、未核验虚构 App 的演示结果。定位分别为配文中的空状态三处改动、车型选择三处改动、帮助三处改动、错误恢复三处改动、结算层级三处改动、操作近路三处改动、识别三处示例、日期防错卡片。

## 保留的来源要点

- 空页面区分首次无内容与搜索无匹配；说明当前原因和合理下一步，避免让空状态成为多按钮广告。
- 选项比较保持价格、时间等字段口径一致；常用项与其他项分层时，其他项仍能找到。推荐应服务用户，不能统一默认最贵选项。
- 帮助使用用户词汇、放在卡点附近、给可执行步骤；反复出现的帮助请求可能反映入口本身不清楚。
- 错误指出对象和可行改法，保留未出错的输入；页面当前任务决定主要操作与信息层级，不能删掉金额、地址等必要确认信息。
- 高频操作考虑近路，多对象考虑批量；保留可发现的普通入口，不让手势成为唯一方法。让必要上下文可见，减少跨页记忆，历史偏好允许清理。
- 日期选择展示实际日期和晚数，使用户在提交前发现意图与所选范围不一致。

## 条件化与技能去向

合并到 [交互技能](../skills/ui-interaction-checkpoints/SKILL.md) 的 [任务与恢复参考](../skills/ui-interaction-checkpoints/references/task-recovery.md)；操作层级同时补充 [视觉技能](../skills/ui-quality-checkpoints/SKILL.md)。参考中的事件顺序、批量部分失败、权限、时区及验证用例为整理者工程推导。

不将“默认选一个”“仅三个选项”“四次删除”“自动纠错优于报错”写成通用规则。不可推断用户意图时保留主动选择；不能用改变日期等静默修正隐藏有意义的决定。来源点按次数不是实测效率收益。

2026-10-24 核对 [NN/g 可用性原则](https://www.nngroup.com/articles/ten-usability-heuristics/)、[空状态](https://www.nngroup.com/articles/empty-state-interface-design/)；并核对 [WCAG 3.3.4](https://www.w3.org/WAI/WCAG22/Understanding/error-prevention-legal-financial-data.html) 的适用范围与可逆、校验或确认选择，不能扩写为所有操作必须弹确认。未运行目标 App、读屏或真实用户测试。
