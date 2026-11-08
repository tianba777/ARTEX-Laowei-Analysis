# 调用逻辑与连接边界

以下是架构层面的调用关系，不是可直接执行的流程、操作手册或完整协议实现。

## 知识库

管理／导入入口 → 知识存储 → Search／Get → Agent 参考结果；另有 KBPreflightBlock 生成运行参考块，Get 关联复用计数，Add 保存新条目，发现相关入口负责候选整理或回填。

依据：SQLite 结构、`kb.Client`、`SearchOptions`、`Result`、`ToolSet.kbSearch/kbGet/kbAdd`、`KBPreflightBlock`、`scheduleKBBackfill/kbBackfillFinding`。这些入口都有实现证据，但不能据此声称每一种 Agent 都会在每一轮自动检索。专门的 `seedKBCuratorAgent` 只确认注册入口，具体触发规则未穷尽。

## Skill 与工作流参考

意图分类 → `chainskel.ForIntent` → `intentCats/Section` → 选择相关参考段；另有 `RefsGuideForIntent`、`PivotHintsForIntent` 和 `VerifierChecklist`。

`ForIntent` 中到 `intentCats/Section` 的调用可在选定伪代码中确认。Planner/Worker 的 SkillPreflight 入口可以确认存在；它们与每个运行入口、工具可见性和失败处理的完整关系尚未全部恢复。不能把“文件已复制”当作“自动加载规则已移植”。

## WebShell 与远程会话

管理登记／检查 → 持久化记录及会话对象 → 执行或文件操作入口 → 结果／审计。专属聊天入口创建关联的对话；记录、对话、执行器是不同层。

管理层有部分函数体证据，会话层有类型和函数证据。传输兼容、并发、超时及会话恢复没有端到端实测。只实现地址登记不会得到远程执行能力。

## C2

监听管理、会话状态、任务申请／审批、任务队列、结果／文件记录属于同一专用子系统。可确认 `SetApprover/ApproveTask`、任务 Store 和 `ApplyResults` 等入口；管理 handler、部分结果处理和恢复函数已选定恢复。

没有执行监听、连接或远端任务，也没有公开可复用的通信实现。不能从这些入口推断全部任务都受同一审批条件覆盖，或认定队列与回传已稳定工作。

## 隧道与内网

Tunnel 模块存在计划／探测、部署、验证、健康、撤销、清理各阶段。内网拓扑函数的选定伪代码可见其聚合资产、会话和隧道记录；`recon` 负责解析观察数据。Worker 另有内网运行环境解析接入点。

“模块存在”“拓扑可展示”“Worker 会实际使用连接”必须分别验证。目前没有完成全链路动态证明，不发布部署细节或自动横向执行实现。

## 临时分发与外部资源

Stage Manager 管理临时内容、下载事件和回收；会话、隧道等模块存在与分发相关的字段。VPS、Penelope 有各自的管理和连接入口，不能与一般 MCP 接口或普通本机 Shell 混为同一能力。

## 仍缺的调用证明

需要进一步证明的是：每个入口真实装配了哪些工具、调用者身份和任务范围如何传递、审批覆盖范围、失败与取消如何传播、重启后对象是否恢复、数据是否被重复消费。报告不把函数名连线直接等同于这些问题已经解决。
