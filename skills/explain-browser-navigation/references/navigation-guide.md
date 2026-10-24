# 网页导航讲解参考

## 主线与职责

下表是 HTTPS over TCP 新连接、获取 HTML 文档时的简化教学框架。可使用虚构的 `https://example.com/` 举例，不需访问该站。

| 阶段 | 通俗解释 | 产出或作用 |
| --- | --- | --- |
| 确定目标 | 浏览器理解用户要访问哪个地址 | 后续请求的目标 |
| DNS | 把域名这个名字对应到网络地址 | 可用于连接的地址信息；可能取自缓存 |
| TCP | 在两端建立可靠传输连接 | SYN → SYN-ACK → ACK 建连 |
| TLS | 核验服务器身份并建立受保护的通信 | 后续数据的安全传输；不要编造固定协商轮次 |
| HTTP | 请求资源，接收状态、响应头与内容 | 响应可能来自服务器或缓存 |
| 渲染 | 将文档和样式等资源处理成画面 | DOM/CSSOM、样式计算、布局、绘制和必要的合成 |

DNS、TCP、TLS 和渲染的职责参考 [MDN：浏览器如何工作](https://developer.mozilla.org/en-US/docs/Web/Performance/Guides/How_browsers_work) 的 Navigation、Parsing、Render 小节。只采用阶段职责，不采用其固定 TLS 往返次数示例。

## 改变流程的条件

- **DNS 缓存**：已有地址信息时可能不需要再次查询；不要与缓存网页内容混淆。
- **HTTP 缓存**：可直接复用的响应可能省去网络传输，需要重新验证的缓存仍可能联网。见 [MDN：HTTP 缓存](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Caching)。
- **连接复用**：已有可用连接时，不必为每个资源重新建连。讲具体行为时以协议和实际请求记录为准。
- **HTTP/3**：HTTP 运行在 QUIC 上，不能沿用“TCP 三次握手再 TLS”的独立阶段模型。见 [RFC 9114](https://www.rfc-editor.org/rfc/rfc9114.html) 的 1、3 节。
- **返回内容与处理**：不是所有响应都返回 HTML，也不是所有服务端都访问数据库。HTML 解析过程中会发现其他资源；资源加载、脚本执行和渲染存在交错，不能描述成所有文件下载完才开始显示。[MDN：浏览器如何工作](https://developer.mozilla.org/en-US/docs/Web/Performance/Guides/How_browsers_work) 的 Response、Parsing、Render 小节可进一步核对。

## 可用的理解检查

选择与问题相关的一两个追问，不必全部出题：

- 已经缓存了 IP，为什么仍可能需要网络请求？
- 已拿到 HTML，为什么页面还没显示好？
- 同一页面请求多张图片，为什么未必发生多次握手？
- 用 HTTP/3 时，原来的哪部分讲解需要改写？

## 来源映射与验证状态

选题及六阶段视觉骨架来自“编程人生”的[小红书视频](https://www.xiaohongshu.com/explore/6acb819f000000001500c451)。抽查约 00:01、00:06、00:11、00:14 画面；未取得音轨或字幕。上述细化与分支是整理者结合技术文档的补充，不归为视频原话。

核对日期：2026-10-24。HTTP/3 依据 RFC 9114；TLS 不预设具体版本或固定轮次。技能入口与参考文件已检查，未进行网络实验或独立执行测试。
