# 查询场景检查

| 使用场景 | 决策与遗漏影响 | 验证 |
| --- | --- | --- |
| 主对象关联多条明细 | 输出单位是主对象还是明细？JOIN 可能放大行数，影响总数、金额和分页 | 用零条、一条、多条明细对比业务期望 |
| 保留没有匹配关系的对象 | 外连接的右侧条件放 ON 或 WHERE 会改变保留行 | 使用无匹配样本检查是否丢失主对象 |
| 分组统计 | 过滤是针对原始行还是聚合结果？统计的是对象数还是连接行数？ | 手算小样本再对照，不默认 COUNT(*) 等于业务对象数 |
| 列表分页 | 指定能唯一确定先后的排序；相同业务排序值需要明确次序 | 固定数据下跨页检查重复/遗漏；动态写入还需另行评估一致性策略 |
| UPDATE/DELETE 等写入 | 目标、条件和预期影响范围是否明确 | 按实际环境选用预览、事务或回滚验证，不拿生产数据做教学实验 |

核验依据（2026-10-24）：[PostgreSQL 18 Table Expressions](https://www.postgresql.org/docs/18/queries-table-expressions.html) 说明连接与过滤/分组；[LIMIT/OFFSET](https://www.postgresql.org/docs/18/queries-limit.html) 说明确定排序与大 OFFSET 成本。项目使用其他数据库时复核其支持与语法。

来源：[十项 SQL 操作](https://www.xiaohongshu.com/explore/6ac27841000000001802c142)、[四类 JOIN](https://www.xiaohongshu.com/explore/6a5e34a4000000000103007e)。仅抽查操作概览与连接图，未取得字幕或音轨。上表边界样本和工程判断为整理者补充。

已用 SQLite 内存样例验证：右侧过滤放 ON 可保留无匹配主记录，放 WHERE 会删除不满足条件的记录；一对多 JOIN 行数可多于业务对象数。未验证目标项目查询、PostgreSQL 实际执行计划或性能。
