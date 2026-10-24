# 按功能选择访问控制检查点

| 使用场景 | 关键决策与易漏项 | 验证方法 |
| --- | --- | --- |
| 新增登录或接入凭据 | 明确身份验证由谁完成，谁校验凭据/签名/有效期，是否复用现有库 | 使用有效、过期、损坏或不属于此应用的凭据，按实际协议核对拒绝行为 |
| 访问用户或租户资源 | 从已验证身份判断资源归属及操作权限，不能信任请求中的用户/租户字段或只做前端限制 | 在测试环境以两个普通身份互换资源 ID，验证拒绝且无越权读取/写入 |
| 新增角色、批量或管理功能 | 验证功能权限与对象权限覆盖全部入口，缺少权限时默认拒绝 | 覆盖普通/管理角色、批量子项以及直接调用后端的场景 |
| 退出、过期或权限被收回 | 明确服务器会话或令牌的失效/撤销策略；客户端删 Cookie 不等于服务器会话失效 | 保留测试凭据后执行退出或变更权限，检查后续请求是否符合定义的失效时限 |
| 接入单点登录 | 确认协议、应用注册、回调、会话边界及本地权限映射，登录共享不代表业务权限共享 | 验证错误回调上下文、登录成功但权限不足、多应用退出范围；使用提供方测试环境 |

以上为条件检查与工程建议，不是已发现的项目缺陷。具体会话时限、验证参数与错误码以项目协议及提供方文档为准。

## 需纠正的概念边界

OAuth 2.0 主要提供委托授权；OIDC 在 OAuth 2.0 上增加身份层。不能将概览中“OAuth 认证”作为完整登录设计，也不能将 JWT 当成独立的认证/撤销策略。API Key、Bearer、JWT、Session 等不处于完全相同的分类层级，应先按业务场景选择职责，再选择表示和传递方式。

## 一手核验

核对日期：2026-10-24。

- [OWASP Authorization](https://cheatsheetseries.owasp.org/cheatsheets/Authorization_Cheat_Sheet.html)：服务端权限验证、对象访问和默认拒绝；用于验证权限检查边界。
- [OWASP Session Management](https://cheatsheetseries.owasp.org/cheatsheets/Session_Management_Cheat_Sheet.html)：会话超时、退出与服务端失效；用于设计生命周期验证。
- [OIDC Core](https://openid.net/specs/openid-connect-core-1_0.html)：身份层与令牌用途；接入时读取项目使用的具体流程与验证规则。
- [RFC 9700](https://www.rfc-editor.org/rfc/rfc9700.html)：OAuth 2.0 当前安全实践。接入 OAuth/OIDC 时核对提供方支持与授权码流程保护，不从旧示意图直接复制流程。

网络媒体来源：[认证方式概览](https://www.xiaohongshu.com/explore/6ab91144000000001802c831)、[SSO 概览](https://www.xiaohongshu.com/explore/69dba3d8000000001b001c46)、[REST API 认证方式图](https://www.xiaohongshu.com/explore/692f0710000000001e011fa4)。仅抽查概览帧，未取得完整音轨或字幕。权限边界、验证场景及标准纠错是整理者补充。尚未进行真实系统认证或越权测试。
