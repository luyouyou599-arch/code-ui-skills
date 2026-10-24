# 多租户检索、会话与缓存的数据边界

来源类别：网络媒体。主分类：身份与权限；交叉用途：后端开发、检索与验收。标签：多租户、RAG、上下文、语义缓存。整理日期：2026-10-24。适用于开发或评审多租户知识库和会话功能；需真实身份、数据归属、检索与缓存实现。

原文：[Agent 面试必会题库 31](https://www.xiaohongshu.com/explore/6adb0039000000002403eda8)。完整正文与 9 张图已读：图 1—2 为封面/主题，图 3 为四层隔离，图 4—6 为评分/回答/关键句，图 7 为四层控制点，后续为追问及总结。正文不是评论区总结；未获得实现源码，也未验证任何招聘评分标准。

## 保留及纠正

保留存储/检索、上下文、缓存分别约束，并用跨租户用例检查实际数据路径的思路。相关开发问题是：从哪里取得可信租户、哪些入口能拿到文档和会话、缓存命中能否绕过权限；不是背诵几种隔离组件。

原文“全部缓存都带 tenant_id”“命中必然泄露”“模型无状态因此其余保证即可”等表述过强。区分应用回答缓存与供应商推理计算缓存；应用缓存是否需租户维度取决于结果和权限是否随租户变化，公共内容可明确共享。会话可以在授权范围内持久保存，重点是每次组装的归属校验，不是无条件销毁。namespace、collection 和独立实例也不是同一安全边界，选型需依据具体服务与实际路由权限。

隔离下沉为可强制的访问边界，不等于应用不做授权。按实际风险选择现有共享表/存储策略或分离方式，不强制所有项目增加独立实例或固定字段；不能由 CI 全绿推出完全安全。

## 工程提炼与验证

合并 [auth-access-checkpoints](../skills/auth-access-checkpoints/SKILL.md) 的 [租户检索参考](../skills/auth-access-checkpoints/references/tenant-retrieval-isolation.md)：先绑定可信身份与租户，再检查文档切片、检索、历史/摘要、缓存路径；授权变化后重新判断可见性。整理者补充了同租户低权限、缓存预热后换租户、工作进程交错请求等测试场景；验证时同时查看正常结果、拒绝结果和模型输入前的数据范围，不只看最终回答。

一手核验于 2026-10-24：[OWASP 多租户安全](https://cheatsheetseries.owasp.org/cheatsheets/Multi_Tenant_Security_Cheat_Sheet.html)、[OWASP RAG 安全](https://cheatsheetseries.owasp.org/cheatsheets/RAG_Security_Cheat_Sheet.html) 及 [Pinecone 多租户实现](https://docs.pinecone.io/guides/index-data/implement-multitenancy)。只据这些文档核对上述授权/隔离边界；没有测试目标系统、向量库实例、模型会话或缓存。本笔记不证明某个项目已有漏洞，也不代表完整 Agent 安全审计。
