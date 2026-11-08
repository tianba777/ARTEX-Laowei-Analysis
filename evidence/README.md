# 公开证据索引

这些文件仅含派生元数据，不含原程序、知识条目、执行函数体或敏感配置。

| 文件 | 内容 |
| --- | --- |
| [provenance.json](provenance.json) | 样本指纹、构建元数据、分析覆盖和未执行声明 |
| [archive-summary.json](archive-summary.json) | 包目录分组计数和大小；不公开历史运行明细 |
| [application-functions.tsv](application-functions.tsv) | 纠正地址后的 4,347 个应用函数条目；排除运行时及第三方依赖 |
| [decompiled-function-index.tsv](decompiled-function-index.tsv) | 已选定恢复的 168 个唯一函数名称／位置；不含伪代码正文 |
| [type-summary.json](type-summary.json) | 37 个恢复类型的名称、大小及字段数量；不含完整协议结构 |
| [knowledge-columns.json](knowledge-columns.json) | SQLite poc 表字段信息，无记录正文 |
| [knowledge-statistics.json](knowledge-statistics.json) | 448 条知识记录的聚合统计，verified 仅为来源声明 |
| [skill-paths.json](skill-paths.json) | skills 中 127 个文件的路径／大小，不是 127 个独立技能 |
| [embedded-pages.json](embedded-pages.json) | 内嵌 HTML 页面路径／大小，不包含网页脚本或程序 |
| [tool-architectures.json](tool-architectures.json) | 已检查可执行文件的机器架构；不代表启动成功 |
| [SHA256SUMS](SHA256SUMS) | 本次公开文件的指纹，不包含此文件自身 |

地址与字段来自静态恢复，不能作为工作协议或效果证明。原始路由字符串有拼接噪声，未作为可靠的完整接口契约发布。31,903 是真实全程序函数条目数；公开应用索引和选定恢复范围是不同口径。
