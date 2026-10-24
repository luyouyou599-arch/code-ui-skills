# 内容布局、深色主题与浮层层级

主分类：UI 视觉设计 / 设计到实现。标签：响应式、容器、语义变量、主题、阴影。适用于具有真实内容和尺寸变化的网页设计与实现；需能查看组件样式。来源类别：网络媒体。整理日期：2026-10-24。

以下 3 份完整正文已读，附图未逐张完整核验。

| 原文 | 正文定位 |
| --- | --- |
| [自动布局不是在对齐，是在算关系](https://www.xiaohongshu.com/explore/6acf554a0000000001009352) | 容器的方向、间距、内边距、对齐与 Hug/Fill/Fixed |
| [🌑 深色模式不是把白改黑，4 个值全得换](https://www.xiaohongshu.com/explore/6ad60ee00000000029012c0d) | 背景、文字、层级、主色四段及浅深色例表 |
| [🎯 阴影别乱加，3 层就够了](https://www.xiaohongshu.com/explore/6adb43ae0000000033010da2) | L0—L3 层级示例和偏移/模糊公式 |

提炼为内容与容器尺寸关系、语义色共同切换和表面/菜单/模态层级表达。原文把自动布局直接等同 Flexbox、Hug 等同 fit-content、Fill 等同 flex:1 的说法不能一一照搬，实际还受最小内容宽度、换行、父容器约束等影响。

阴影必须朝下、固定三层、偏移大于模糊一半，以及深色禁止纯黑/纯白属于该案例的风格建议，不能升级成通用技术规范。以真实背景上的对比、品牌和设备结果判断，补上主题设置优先级、控件状态与长文案/窄屏验证。

合并 [ui-quality-checkpoints](../skills/ui-quality-checkpoints/SKILL.md) 的 [布局与主题参考](../skills/ui-quality-checkpoints/references/layout-and-theme.md)。2026-10-24 核对 MDN min-width、prefers-color-scheme 与 W3C 对比要求；工程建议和验证方法为整理者补充，未实测目标页面。不操作 Figma 文件，也未核验具体 Figma 版本的菜单或快捷键。
