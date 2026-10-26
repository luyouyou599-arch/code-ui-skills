# Code UI Skills

可跨项目复用的计算机基础、编程与 UI 技能库。

用于持续接收文章、图文、视频和项目实例，保留可追溯的知识笔记，并将成熟的方法整合成可复用的 Codex skill。默认以中文整理，保留必要的英文术语。

技能面向两个用途：开发核心功能时，识别相关知识、关键决策与易漏项并验证落实；阐述项目时，快速拆解真实实现中的核心机制、模块关系、取舍与证据。概念解释保留为参考材料。

## 使用方式

直接发送链接即可，也可以附上“重点看哪部分”或“希望用在哪个项目”。每次整理返回：基础分类、核心要点、适用场景、来源覆盖范围，以及新增或更新了哪些技能。

初始分类：计算机基础、编程基础、开发工具与工程实践、Web 与前端、UI 视觉设计、交互与可用性、设计到实现。具体标签随资料增加，不提前建立大量空目录。

只将有实际开发价值且已核验适用性的内容提炼为技能；不以覆盖作品数量为目标。基础知识不因发布时间早就判为过时，资讯和无工程增量的内容不进入技能。

## 按用途找技能

先查看 [技能用途与调用导航](CLASSIFICATION.md)：区分产品与业务、交互、视觉设计、前端实现、后端开发、架构、测试验收、工程协作与交付，并标明现有覆盖和缺口。前端/后端是实现范围，产品/设计/测试是用途；同一技能可以跨用途复用。

产品规范决定功能规则与行为，交互规范决定操作和反馈，视觉规范决定呈现与一致性，测试验收用证据核对实现。产品规则不只属于前端；测试方法也不限于一个独立技能。

## 前端与后端入口

按任务选择入口，由入口根据实际改动读取有关知识点。知识仍统一维护，跨端或工程通用技能不复制两份。

| 分类 | 入口 | 自动选择的知识点 |
| --- | --- | --- |
| 前端 | [frontend-development-review](skills/frontend-development-review/SKILL.md) | 页面视觉、布局与主题、控件状态与反馈、滚动动效、请求与响应、登录交互和相关任务依赖 |
| 后端 | [backend-development-review](skills/backend-development-review/SKILL.md) | 接口边界、业务不变量、访问授权、SQL/ORM、事务、缓存/异步、运行与发布 |
| 通用工程与维护 | Git、依赖编排、资料整理等下方主题技能 | 按具体任务使用，前后端共享 |

后端入口在开发时主动选取相关检查，在验收时以具体代码、失败场景、测试和副作用寻找 bug 或漏洞；发现问题后按任务授权修复或报告。仅做静态审阅、测试未运行或范围未覆盖时明确说明，检查通过不等于项目没有任何缺陷。

本机安装入口及有关主题技能后，可明确要求“使用 backend-development-review 开发并验收这个接口”或“使用 frontend-development-review 检查这次页面改动”。准确的描述也支持 Codex 按任务自动选择；实际选择取决于会话发现的技能与任务上下文，安装本身不会在其他工具或流水线中自动执行检查。仅复制入口目录不包含全部主题知识，跨设备使用需同时安装依赖主题。

## 内容组织

- `sources/`：有真实资料后创建，保存来源笔记及引用位置。
- `skills/`：可复用技能；每个技能有独立的 `SKILL.md`，按需附带参考资料。
- 下方索引：记录已有资料与技能，避免重复整理和技能碎片化。

资料笔记用于理解概念和追溯证据；技能用于指导具体任务，包含触发条件、适用范围、操作方法和结果检查。概念介绍可以先作为笔记积累，不强行生成技能。

## 资料索引

| 资料 | 主分类 | 关联技能 | 状态 |
| --- | --- | --- | --- |
| [请求一个 URL 后发生了什么](sources/url-request-browser-journey.md) | 计算机基础 / 计算机网络 | web-request-checkpoints | 已整合；视频关键帧抽查与文档核验 |
| [HTTP 方法与响应](sources/http-methods-and-status.md) | Web 与前端 / API | web-request-checkpoints | 4 份来源合并，含标准纠错 |
| [Git 协作与改动](sources/git-workflow-decisions.md) | 开发工具与工程实践 / Git | git-change-checkpoints | 6 份来源合并，官方语义核验 |
| [SQL 查询结果](sources/sql-query-correctness.md) | 数据库 | sql-query-checkpoints | 2 份来源合并，部分边界样例验证 |
| [任务依赖](sources/task-dependency-order.md) | 编程基础 / 图算法 | dependency-order-checkpoints | 拓扑片段与边界样例验证 |
| [架构机制与取舍](sources/architecture-tradeoffs.md) | 系统设计 | architecture-tradeoff-checkpoints | 2 份概览合并，条件化提炼 |
| [API 契约与诊断](sources/api-contract-and-diagnostics.md) | Web 与前端 / API | web-request-checkpoints | 3 份概览补充现有技能 |
| [请求入口职责](sources/gateway-boundaries.md) | 系统设计 | architecture-tradeoff-checkpoints | 2 份概览补充现有技能 |
| [身份与访问权限](sources/authentication-and-access.md) | 身份与权限 | auth-access-checkpoints | 3 份概览合并，一手语义核验 |
| [发布与容器运行](sources/release-and-container-decisions.md) | 发布部署 | release-deployment-checkpoints | 6 份概览合并，版本边界核验 |
| [界面一致性与视觉效果](sources/ui-quality-and-effects.md) | UI 视觉设计 | ui-quality-checkpoints | 2 份资料合并，设计建议条件化核验 |
| [后端代码验收](sources/backend-code-acceptance.md) | 开发工具与工程实践 | web-request-checkpoints | 视频局部抽查，补充验收证据 |
| [组件状态与反馈](sources/frontend-component-states.md) | 交互与可用性 | ui-interaction-checkpoints | 6 份完整正文，已补读配图，条件化纠错与工程补充 |
| [布局、主题与层级](sources/layout-theme-elevation.md) | UI 视觉设计 / 设计到实现 | ui-quality-checkpoints | 3 份完整正文及配图，补充布局和主题验证 |
| [滚动动效决策](sources/scroll-motion-decisions.md) | Web 与前端 / 交互 | ui-quality-checkpoints | 3 份完整配文，未完整观看视频 |
| [库存预留一致性](sources/reservation-consistency.md) | 系统设计 | architecture-tradeoff-checkpoints | 1 份视频局部画面，原子性边界核验 |
| [内容密度、显示稳定与操作反馈](sources/interface-detail-decisions.md) | UI / 交互 | ui-quality-checkpoints、ui-interaction-checkpoints | 4 份正文合并，未取得所称源码或完整演示 |
| [表单与加载连续性](sources/form-and-loading-continuity.md) | 交互 / Web 与前端 | ui-interaction-checkpoints、web-request-checkpoints | 3 份完整配文，未完整读取演示 |
| [配置编辑与保存](sources/configuration-editing.md) | 交互 / Web 与前端 | ui-interaction-checkpoints、web-request-checkpoints | 1 份视频部分画面，含工程边界补充 |
| [产品任务与成功标准](sources/product-task-and-success.md) | 产品与业务规则 | product-task-checkpoints | 3 份正文/配文及图文，补充任务基线与失败样本 |
| [视觉角色与尺度一致性](sources/visual-role-consistency.md) | UI 视觉设计 | ui-quality-checkpoints | 7 份正文与配图合并，固定数值条件化 |
| [加载反馈选择与禁用原因](sources/loading-feedback-selection.md) | 交互与可用性 | ui-interaction-checkpoints | 2 份正文及配图，补充阶段/成功边界 |
| [多租户检索、会话与缓存](sources/tenant-context-isolation.md) | 身份与权限 / 后端 | auth-access-checkpoints | 1 份正文及 9 图，一手边界核验，未运行系统测试 |
| [可见目标与标签热区](sources/visible-and-clickable-targets.md) | 交互与可用性 | ui-interaction-checkpoints | 完整配文与视频局部画面，一手核验 |
| [AI 功能评测证据](sources/ai-workflow-evaluation.md) | 测试 / AI 工程 | ai-workflow-evaluation-checkpoints | 3 份来源：局部视频、完整配文及官方文档；未运行模型评测 |
| [AI 适配、路由与执行](sources/ai-routing-tools-and-adaptation.md) | AI / 测试 | ai-workflow-evaluation-checkpoints | 4 份视频局部知识已整合，补充工具描述与误选验收；完整视频均待补读，未运行模型测试 |
| [任务可发现性、恢复与效率](sources/task-recovery-and-efficiency.md) | 交互 / 产品 / 前端 | ui-interaction-checkpoints、ui-quality-checkpoints | 8 份完整配文，未完整读取视频；条件化合并 |
| [搜索衔接与限时消息](sources/search-and-transient-feedback.md) | 交互 / 前端验收 | ui-interaction-checkpoints | 搜索完整配文与局部视频、Toast完整正文与3图；一手核验，未运行组件测试 |
| [运行时安全更新](sources/runtime-security-updates.md) | 工程交付 / 后端运行安全 | release-deployment-checkpoints | 完整配文及官方公告核验；未执行升级 |
| [代码评审证据与收敛](sources/review-evidence-and-convergence.md) | 工程协作 / 测试 | git-change-checkpoints | 完整配文及一手工程记录；未实测评审器 |

## 技能索引

来源索引：[网络媒体资料](sources/media-index.md)（按主题合并，保留必要原文链接与实际读取范围）。

| 技能 | 主用途 / 角色 | 具体能力 | 状态 |
| --- | --- | --- | --- |
| [frontend-development-review](skills/frontend-development-review/SKILL.md) | 前端调用入口 | 前端开发与验收按需调用入口 | 已做结构与路由检查，未在真实项目试用 |
| [backend-development-review](skills/backend-development-review/SKILL.md) | 后端调用入口 | 后端开发与验收按需调用入口 | 已做结构与路由检查，未在真实项目试用 |
| [ai-workflow-evaluation-checkpoints](skills/ai-workflow-evaluation-checkpoints/SKILL.md) | AI 功能评测 / 回归 | 按任务定义样本、判定和过程证据 | 资料与结构检查，未在真实项目试用 |
| [product-task-checkpoints](skills/product-task-checkpoints/SKILL.md) | 产品任务 / 验收约定 | 角色、任务结果、业务规则与验证证据 | 资料与结构检查，未在真实项目验证 |
| [curate-programming-ui](skills/curate-programming-ui/SKILL.md) | 技能库维护 | 将编程、UI 资料分类、提炼并整合为技能 | 已用于首份视频资料整理，未完成独立执行测试 |
| [web-request-checkpoints](skills/web-request-checkpoints/SKILL.md) | 跨端接口 / 数据交互 | 开发请求与页面加载功能时检查关键决策、遗漏项，并拆解项目实现与依据 | 已核对资料和结构，尚未在真实开发项目中验证 |
| [git-change-checkpoints](skills/git-change-checkpoints/SKILL.md) | 工程协作 | 提交、同步、整合与撤销的场景决策 | 资料与结构检查，部分命令行为实验 |
| [sql-query-checkpoints](skills/sql-query-checkpoints/SKILL.md) | 后端查询 / 数据正确性 | JOIN、过滤、计数与分页的结果正确性 | 小型 SQL 边界样例验证 |
| [dependency-order-checkpoints](skills/dependency-order-checkpoints/SKILL.md) | 工程编排 | 依赖方向、缺失节点、环和任务完成条件 | 标准库边界样例验证 |
| [architecture-tradeoff-checkpoints](skills/architecture-tradeoff-checkpoints/SKILL.md) | 架构 / 可靠性 | 缓存、异步、容量与服务边界的取舍 | 资料与结构检查，未在真实项目验证 |
| [auth-access-checkpoints](skills/auth-access-checkpoints/SKILL.md) | 后端身份 / 权限 | 身份来源、对象授权、会话/SSO 与多租户检索隔离 | 资料与结构检查，未运行真实系统测试 |
| [release-deployment-checkpoints](skills/release-deployment-checkpoints/SKILL.md) | 发布 / 运行交付 | 流水线、制品、运行环境、就绪与版本恢复 | 资料与结构检查，未运行发布或容器实验 |
| [ui-quality-checkpoints](skills/ui-quality-checkpoints/SKILL.md) | 视觉设计 / 前端呈现 | 界面层级、样式一致性、可读性与装饰动效取舍 | 资料与结构检查，未在真实页面试用 |
| [ui-interaction-checkpoints](skills/ui-interaction-checkpoints/SKILL.md) | 交互 / 产品行为 | 控件状态、表单校验、异步反馈和模态选择 | 正文及一手资料核验，未在真实组件试用 |

## 跨项目使用

本库是统一维护源；用户级技能目录 `~/.agents/skills/` 可以通过符号链接引用库内技能，避免多个项目各存一份而版本不一致。

macOS / Linux 安装示例：

```sh
git clone https://github.com/luyouyou599-arch/code-ui-skills.git
cd code-ui-skills
mkdir -p "$HOME/.agents/skills"
ln -s "$PWD/skills/curate-programming-ui" "$HOME/.agents/skills/curate-programming-ui"
```

若目标名称已存在，先检查已有技能；不要覆盖。后续新增的主题技能可按同样方式单独安装。

在本机其他项目中，可以选择该技能，或明确要求“使用 curate-programming-ui 整理这份资料并加入技能库”。名称与任务匹配时也可由 Codex 自动选择；如果新技能未出现，重启 Codex 后再检查。

主题技能保留通用方法，执行时读取目标项目的规范与需求。源目录需保留；移动库后要更新链接。跨项目不等于跨设备同步，其他电脑或云端环境需要另外安装。

配置依据：[OpenAI 官方技能文档](https://learn.chatgpt.com/docs/build-skills)。

## 来源与复用

来源笔记保留原始链接及引用位置，以提炼与改写为主。来源中的图片、视频、代码和文字各自遵循原作者的授权；公开链接不代表这些内容可任意再分发。
