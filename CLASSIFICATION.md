# 技能用途与调用导航

按“要解决的问题”选择技能；前端、后端和跨端是实现范围，产品、设计、开发、测试和交付是用途，两者不能互相替代。一个技能可以有主用途和辅助用途，正文只维护一份，目录路径和安装名称保持稳定。

## 用途分类

| 用途 | 核心问题 | 现有内容与入口 | 当前边界 |
| --- | --- | --- | --- |
| 产品与业务规则 | 给谁用、完成什么任务、哪些条件允许、失败后怎么办 | [产品任务](skills/product-task-checkpoints/SKILL.md) 中的角色、任务和成功证据；[交互检查](skills/ui-interaction-checkpoints/SKILL.md) 中的动作/状态/恢复；[后端入口](skills/backend-development-review/SKILL.md) 中的业务不变量 | 覆盖具体功能的任务/行为/验收约定；没有完整的用户研究、需求优先级、市场定位或统计实验设计技能 |
| 交互与可用性 | 用户怎样操作、怎样知道结果、怎样恢复 | [ui-interaction-checkpoints](skills/ui-interaction-checkpoints/SKILL.md)：表单、组件状态、反馈、模态、排序与配置 | 与产品行为、视觉表达、前端实现和验收交叉；不证明后端授权或持久化正确 |
| 视觉与设计系统 | 信息怎样分层、样式怎样一致、效果何时合适 | [ui-quality-checkpoints](skills/ui-quality-checkpoints/SKILL.md)：布局、字体/颜色/间距、主题、阴影、内容密度与动效 | 已有的是视觉规则与实现检查，尚不是完整的品牌、组件资产库或设计系统治理能力 |
| 前端实现与数据交互 | 页面如何把操作、请求、状态和渲染连接起来 | [frontend-development-review](skills/frontend-development-review/SKILL.md) 按需组合视觉、交互和 [web-request-checkpoints](skills/web-request-checkpoints/SKILL.md) | 请求技能跨前后端；当前不是完整的框架架构、状态管理或前端构建工具知识库 |
| 后端业务、接口与数据 | 规则在哪里执行、权限和数据如何保持正确 | [backend-development-review](skills/backend-development-review/SKILL.md)、[请求/API](skills/web-request-checkpoints/SKILL.md)、[身份权限](skills/auth-access-checkpoints/SKILL.md)、[SQL](skills/sql-query-checkpoints/SKILL.md) | 覆盖已有主题及相关失败分支；不是所有业务领域和所有安全漏洞的完整审计库 |
| 架构与可靠性 | 组件为何存在、一致性/容量/故障如何取舍 | [architecture-tradeoff-checkpoints](skills/architecture-tradeoff-checkpoints/SKILL.md)：缓存、异步、服务边界、网关与库存预留 | 条件化取舍与验证方法；没有通用容量数值或必须采用的组件组合 |
| 测试与质量验收 | 怎样用证据判断需求与实现一致 | 前后端入口负责组织，主题技能中的验证方法负责具体检查；详见下表 | 当前是分散在各主题中的验收能力，没有独立 E2E/压测/测试平台技能，也不等同于已自动运行测试 |
| 工程协作与交付 | 改动怎样协作、任务如何编排、版本如何发布恢复 | [Git](skills/git-change-checkpoints/SKILL.md)、[依赖顺序](skills/dependency-order-checkpoints/SKILL.md)、[发布部署](skills/release-deployment-checkpoints/SKILL.md) | 前后端共享；依据项目实际采用的工具选择，不固定某种流水线或容器平台 |

[资料整理技能](skills/curate-programming-ui/SKILL.md) 属于技能库维护，负责筛选、归纳、证据和分类，不是业务项目的开发规范。

分类可以继续演进。只有资料和实际任务支持新的可复用能力时才新增技能；现有缺口不以空目录或泛化清单填补。

## 产品规范、交互规范与视觉规范的边界

| 同一个功能 | 产品与业务约定 | 交互约定 | 视觉约定 | 实现与测试关注点 |
| --- | --- | --- | --- | --- |
| 删除对象 | 谁能删、能否撤销、影响哪些数据 | 是否确认、如何取消、失败如何恢复 | 危险操作与层级怎样清晰表达 | 服务端对象授权、实际副作用、焦点与错误恢复 |
| 配置保存 | 哪些值有效、何时生效、冲突如何处理 | 草稿/预览/保存状态怎样区分 | 表单分组、字段与提示层级 | 服务端校验、并发保存、失败后保留输入与重新读取 |
| 列表加载 | 筛选含义、排序口径、何时算无结果 | 加载/空/错、重试与翻页方式 | 占位尺寸、内容密度与布局稳定 | 旧响应失效、页终点、重复项与查询正确性 |

这是分类示例，不表示所有项目都必须实现删除确认、撤销、自动保存或无限滚动。业务规则可以在前后端共同表现，其中服务端需要落实的约束不能仅靠界面控制。

## 测试与验收去哪里找

| 要验证什么 | 主要技能与实际参考 |
| --- | --- |
| 视觉、长内容、宽窄屏、主题与动效降级 | [视觉检查](skills/ui-quality-checkpoints/references/visual-decisions.md)、[布局与主题](skills/ui-quality-checkpoints/references/layout-and-theme.md) |
| 键盘/触屏、控件状态、消息与恢复 | [控件](skills/ui-interaction-checkpoints/references/controls.md)、[反馈](skills/ui-interaction-checkpoints/references/feedback.md) |
| 校验、验证码、分页衔接与快速状态变化 | [表单与加载](skills/ui-interaction-checkpoints/references/form-and-loading-continuity.md) |
| 配置草稿、预览、排序与保存 | [配置编辑](skills/ui-interaction-checkpoints/references/configuration-editing.md) |
| 请求错误、迟到响应、重试及写入结果 | [请求链路](skills/web-request-checkpoints/references/checkpoints.md)、[HTTP 语义](skills/web-request-checkpoints/references/http-semantics.md)、[后端验收](skills/web-request-checkpoints/references/backend-acceptance.md) |
| 登录过期、对象/租户越权与会话变化 | [身份权限](skills/auth-access-checkpoints/references/decisions.md)、[租户检索/上下文/缓存](skills/auth-access-checkpoints/references/tenant-retrieval-isolation.md) |
| JOIN、计数、过滤、分页结果 | [SQL 结果](skills/sql-query-checkpoints/references/checkpoints.md) |
| 库存预留、重复副作用与中断恢复 | [库存一致性](skills/architecture-tradeoff-checkpoints/references/reservation-consistency.md) |
| 环、缺失前置与任务完成条件 | [依赖顺序](skills/dependency-order-checkpoints/references/decisions.md) |
| 流水线、运行环境、制品和恢复 | [发布](skills/release-deployment-checkpoints/references/release.md)、[容器](skills/release-deployment-checkpoints/references/containers.md) |

验收时先从实际需求确定预期，再选择验证；已执行、未执行与待核实分别记录。知识点的结构检查、资料核验和目标项目的测试通过是三种不同状态，不能互相替代。

## 每个技能的主用途与辅助用途

| 技能 | 角色 / 主用途 | 辅助用途与范围 |
| --- | --- | --- |
| [frontend-development-review](skills/frontend-development-review/SKILL.md) | 前端任务调用入口 | 组织设计、实现和验收，不是一份新的视觉规范 |
| [backend-development-review](skills/backend-development-review/SKILL.md) | 后端任务调用入口 | 组织业务、接口、数据、安全相关检查和验收 |
| [product-task-checkpoints](skills/product-task-checkpoints/SKILL.md) | 产品任务与功能约定 | 支持前后端规则衔接、验收场景与项目目标拆解 |
| [ui-interaction-checkpoints](skills/ui-interaction-checkpoints/SKILL.md) | 交互与可用性 | 支持产品行为约定、前端实现和交互验收 |
| [ui-quality-checkpoints](skills/ui-quality-checkpoints/SKILL.md) | 视觉与设计规则 | 支持前端布局/主题/动效实现及视觉验收 |
| [web-request-checkpoints](skills/web-request-checkpoints/SKILL.md) | 跨端接口与数据交互 | 支持前端请求、后端契约和接口验收 |
| [auth-access-checkpoints](skills/auth-access-checkpoints/SKILL.md) | 后端身份与资源权限 | 支持登录交互、租户检索/记忆/缓存隔离与权限负面测试 |
| [sql-query-checkpoints](skills/sql-query-checkpoints/SKILL.md) | 后端查询与结果正确性 | 支持统计业务口径、数据结果测试和项目拆解 |
| [architecture-tradeoff-checkpoints](skills/architecture-tradeoff-checkpoints/SKILL.md) | 架构与可靠性 | 支持后端机制取舍、失败验证和项目拆解 |
| [dependency-order-checkpoints](skills/dependency-order-checkpoints/SKILL.md) | 任务依赖与工程编排 | 支持初始化/工作流实现及依赖边界验证 |
| [git-change-checkpoints](skills/git-change-checkpoints/SKILL.md) | 工程协作与改动管理 | 支持前后端共同的提交、整合和恢复 |
| [release-deployment-checkpoints](skills/release-deployment-checkpoints/SKILL.md) | 发布与运行交付 | 支持部署验收、运行配置和恢复验证 |
| [curate-programming-ui](skills/curate-programming-ui/SKILL.md) | 技能库维护 | 整理资料、维护技能/分类/入口及证据 |

## 使用分类的方式

讨论需求与行为时，先确认产品约束，再参考交互能力；做界面设计时按需组合视觉和交互；实施时沿前端/后端入口选择有关主题；验收时回到同一功能的预期、实现和证据。分类用于找到知识，不是固定要求每个任务走完所有阶段。

来源笔记原有的主题分类用于追溯资料，与这里的用途视图并存。单个参考文件也可能包含多类内容，执行时只读取匹配当前任务的部分。
