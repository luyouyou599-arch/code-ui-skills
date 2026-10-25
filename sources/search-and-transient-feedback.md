# 搜索状态衔接与限时消息的恢复路径

来源类别：网络媒体。主分类：交互与可用性；交叉：前端实现与验收。整理日期：2026-10-25。面向实现搜索/筛选、结果排序和消息反馈的开发者，需要用户任务、组件状态、接口契约及可撤销业务规则。

## 实际读取范围

- [搜索与筛选演示](https://www.xiaohongshu.com/explore/6adc85f2000000003101e4df)：完整配文已读；01:38 视频仅抽查 00:40 联想更新、01:20 排序切换画面。未读取完整字幕或音轨；不能当作完整视频已读。配文的四种情境为搜索展开、联想标签、筛选面板与结果排序。
- [Toast 与阅读时间](https://www.xiaohongshu.com/explore/6adc9f310000000033023c83)：完整正文与全部 3 张配图已读；分别为长短消息对照、字数与时长建议、错误与普通反馈的区分。

## 来源事实与条件化处理

搜索来源建议展开、增删联想、滑入面板及平滑重排。这些是视觉方案，不证明搜索更快或转化提升；是否采用应由任务和设备决定。提炼为展开/关闭时焦点与查询保持、建议与当前输入对应、筛选草稿与已应用条件分离，以及排序后仍能操作正确对象。键盘、异步乱序和业务验证为整理者工程推导。

Toast 来源提出 2/3/5 秒、固定字数、单行、同屏一条与直接替换等硬规则；本库不采纳为通用标准。“Toast 是唯一自动消失组件”也不成立。保留信息应短且贴合结果、重要错误持续可找回的思路；补充带撤销消息不能因时长到期或下一条通知覆盖而失去唯一操作路径，撤销需绑定正确对象。

## 一手核验与去向

2026-10-25 核对 [APG Combobox](https://www.w3.org/WAI/ARIA/apg/patterns/combobox/) 的可编辑建议与选择/关闭行为；仅适用于确实构成 combobox 的输入，不将标签或独立结果列表都套为 combobox。核对 [MDN 减少动态效果](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-motion) 的减少非必要动效偏好。

核对 [WCAG 2.2.1](https://www.w3.org/WAI/WCAG22/Understanding/timing-adjustable.html) 的时间限制与等价非限时路径说明，以及 [WCAG 4.1.3](https://www.w3.org/WAI/WCAG22/Understanding/status-messages.html) 的不抢焦点状态通知。不能据此要求所有 Toast 常驻；有其他方式访问同一信息/功能与唯一限时入口应分别判断。

合并到 [ui-interaction-checkpoints](../skills/ui-interaction-checkpoints/SKILL.md) 的 [搜索衔接](../skills/ui-interaction-checkpoints/references/search-state-continuity.md) 与 [消息反馈](../skills/ui-interaction-checkpoints/references/feedback.md)。不新增技能；未在真实项目验证键盘、读屏、撤销或请求乱序，未测量效率收益。
