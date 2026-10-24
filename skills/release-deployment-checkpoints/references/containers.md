# 容器运行决策

| 使用场景 | 决策及遗漏影响 | 验证 |
| --- | --- | --- |
| 打包并运行应用 | 区分镜像、容器实例、镜像仓库与运行环境；核对启动参数、配置与所需平台 | 对照构建/运行配置和实例版本，不以本机一次运行证明跨环境兼容 |
| 访问容器服务 | EXPOSE 记录监听意图，实际发布端口、绑定地址和进程监听是不同配置 | 对照端口映射、绑定和目标环境访问结果 |
| 保存数据库或上传内容 | 明确数据位于可写容器层还是独立持久化存储；替换实例不能默认为数据仍在 | 在隔离测试环境验证替换后的数据和挂载配置；不拿实际持久化数据做清理实验 |
| 判断实例是否可以承接流量 | 进程运行、启动成功、存活和就绪各自代表什么？不能用不相干的探测代替关键依赖验证 | 对照实际平台检查机制，验证初始化未完成及依赖故障下的流量行为 |
| 评估增加编排层 | 确认多实例恢复、调度或发布需求是否值得额外运维成本；先比较已有部署方式 | 使用项目容量和维护约束作依据，不因资料出现 K8s 就引入它 |

核验日期：2026-10-24。

- [Docker 容器概念](https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-a-container/)：容器与隔离进程/共享内核的关系；不使用示意表中固定“开销百分比”作为性能结论。
- [Docker 端口](https://docs.docker.com/get-started/docker-concepts/running-containers/publishing-ports/) 与 [存储](https://docs.docker.com/engine/storage/)：端口映射及容器生命周期之外的数据存储。
- [Kubernetes 探测](https://kubernetes.io/docs/concepts/workloads/pods/probes/)：startup、liveness、readiness 的不同用途。仅在项目使用 Kubernetes 时采用其具体行为。
- [Kubernetes Deployment](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)：版本推进与回退；不能将 Deployment 回退理解为自动恢复数据库内容。

[Kubernetes 容器运行时](https://kubernetes.io/docs/setup/production-environment/container-runtimes/) 要求兼容 CRI 的运行时；不能从概览图推断当前集群必须使用 Docker Engine，具体连接与支持取决于版本。

网络媒体来源：[容器命令概览](https://www.xiaohongshu.com/explore/6ac27920000000001802c432)、[容器工作机制](https://www.xiaohongshu.com/explore/696c8d79000000000e03f317)、[Docker 与 K8s 图解](https://www.xiaohongshu.com/explore/690e1764000000000301f539)。仅保留已读概览中的机制与使用场景，具体检查结合官方文档提炼。未实际启动容器或验证集群行为。
