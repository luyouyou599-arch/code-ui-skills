# Git 场景决策

| 场景 | 核心决策与易漏项 | 验证 |
| --- | --- | --- |
| 一个功能准备提交 | 区分未暂存、已暂存和未跟踪文件；提交边界对应一个可理解的改动 | status、diff 与 diff --cached，必要时核对新增文件 |
| 获取协作者更新 | fetch 下载信息；pull 还会按参数/配置整合。先看本地是否有未保存改动与历史分叉 | 核对分支、上游与配置，整合后查看提交图与功能结果 |
| 整理提交历史 | merge 与 rebase 的取舍涉及拓扑、提交身份及协作依赖；不为整齐而改写他人已依赖的历史 | 查看哪些提交已共享、项目规范是否允许重写 |
| 撤销错误 | restore 针对文件/暂存内容；reset 可能移动引用并影响索引/工作区；revert 创建反向提交 | 先确定目标与保留内容，再检查差异、历史及回归结果 |
| 拣选补丁 | cherry-pick 选择提交，不保证连带依赖完整 | 检查依赖及已有等价改动，验证目标分支行为 |

资料与核验（2026-10-24）：六条视频的命令图、提交图及区域数据流已合并；具体命令使用以下官方依据，不直接复制示意图拼写。

- [Recording Changes](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository)：工作区、暂存区和提交边界。
- [git-diff](https://git-scm.com/docs/git-diff)：比较不同状态。
- [git-pull](https://git-scm.com/docs/git-pull)：拉取与整合，具体参数以项目版本和配置为准。
- [Rebasing](https://git-scm.com/book/en/v2/Git-Branching-Rebasing)：提交重写与共享依赖。
- [git-restore](https://git-scm.com/docs/git-restore)、[git-revert](https://git-scm.com/docs/git-revert)：恢复文件和反向提交的区别。

视频来源：[每日 Git 命令](https://www.xiaohongshu.com/explore/6ad8d84b000000002d0064dd)、[十条核心命令](https://www.xiaohongshu.com/explore/6abe2c8a000000001203454e)、[十项协作能力](https://www.xiaohongshu.com/explore/6a7f3c600000000022010b4c)、[pull/fetch 对比](https://www.xiaohongshu.com/explore/69985ee20000000028020015)、[工作原理图](https://www.xiaohongshu.com/explore/693ec6ab000000001e007c38)、[场景与命令](https://www.xiaohongshu.com/explore/69247b9e000000001f00f982)。仅抽查概览帧，未取得字幕或音轨。检查表是工程提炼，不是视频逐字转录。

在隔离临时仓库中已验证：restore --staged 取消暂存但保留工作区修改；revert 新增反向提交并保留原有提交链。尚未对真实项目的冲突解决、共享历史整合或交付流程做行为验证。
