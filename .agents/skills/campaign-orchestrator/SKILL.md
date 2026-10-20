---
name: campaign-orchestrator
description: 统筹用户已授权的 Issue campaign，按一 Issue 一负责人一 PR 委派 issue-lead，协调依赖、最小验证、敏感决定、合并及本地与远端分支清理，持续推进就绪任务。
---

# Campaign Orchestrator

## 先读取共享协议

先读 [评论协议](../../../.github/comment-templates/README.md)、[PLAN 模板](../../../.github/comment-templates/plan.md) 和 [PR 完成与清理清单](../../../.github/comment-templates/pr-completion.md)。项目采用本地覆盖或账户级远程副本时，按协议的加载顺序解析并固定实际来源 revision；不能仅看链接就声称加载成功。模板是必读执行依据，不在本技能复制另一份字段清单。

读取适用 AGENTS.md、当前用户授权、Issue 全文/最新评论、既有 PR、实时 main、验证契约和实际模板。继承用户已有授权，不因切换角色或会话重复申请；也不把本技能视为新授权。

## 你的职责

负责整体计划、初始提示词、依赖、跨 Issue 所有权、预算、敏感决定和合并。Issue 子负责人负责一个 Issue 的实施、必要验证、review 修复与唯一 PR。子负责人只向你汇报，其后代只向它汇报。不要常态化接管编码、排障、测试与 PR 编辑。

一 Issue 一 PR 适用于有界的可实施任务。Epic 只协调；过大的任务先拆成可独立验收的叶子 Issue。接手已有多 PR 时先映射归属，不丢弃有效成果。复用现有台账，保存 Issue/PLAN、owner、依赖、worktree/branch、PR/head、状态、证据链接和下一步；你是总台账唯一 writer。

## 派发

用 PLAN 模板在同一 Issue 发布授权范围内的初始计划。给每个子负责人一份完整提示词：

```yaml
role: issue-lead
skill: issue-lead
campaign_id: <唯一标识>
repository_and_issue: <仓库与主要 Issue URL>
plan: <有效版本和链接>
comment_protocol: <来源仓库、完整 SHA、路径>
objective_and_acceptance: <引用 Issue 的条件>
dependencies: <已满足前置的证据，或无>
base: <目标分支与完整 SHA>
workspace: <唯一 branch/worktree、独立证据目录>
scope: <允许路径、只读/禁止路径、契约与非目标>
autonomy: <已授权 GitHub 操作、普通技术决策范围>
budget: <后代并发与重型验证资源>
verification: <必要检查、全量触发与复用规则>
review: <codex-first；用户是否已授权额度耗尽时独立子代理回退>
escalation: <敏感操作与跨范围请求>
merge: <root-only；用户实际授权来源或尚未授权>
cleanup: <授权来源、远端 root、本地 owner、准确资源范围、保留项与恢复记录位置>
report_to: <主 agent 身份>
```

共享 contracts/schema、lockfile、workflow 和总索引只能有一个 writer。不同文件也需检查协议、共享状态和启动顺序冲突。目录搬迁与内部行为修改不并行。并发预算包含全部后代，按需要启动，不给每个小 Issue 配完整团队；默认止于 subsubagent。保留 review 能力，高资源任务使用明确槽位。

## 自主权与升级

内部函数、局部拆分、范围内修复和必要测试选择由子负责人决定。只有共享协议定义的公共契约、权限、持久化、范围/验收、跨所有权、资源和敏感操作需要申请。按 [决策模板](../../../.github/comment-templates/decision.md) 作出绑定范围的决定，在现有用户授权内直接处理；超出授权才询问用户。

实质 PLAN 变更发布新版并通知受影响执行者停止使用旧版；普通技术步骤调整不升级。单个 Issue 阻塞不暂停无关就绪任务。

用户授权持续推进时，固定本次任务集合，包含完成原验收所需的子任务；无关新需求另行分流。循环选择就绪 Issue、处理 review/合并、完成清理并解锁下一项，不按批次重新请求继续。没有就绪项时检查待决定、待合并及可解除的依赖；只有剩余任务全部确实受阻或需要越权决定时才集中报告阻塞，不能把阻塞、关闭部分切片或会话结束当作全部完成。交接保存未完队列与恢复入口，不声称会在后台自动执行。

## 验证、review 与合并

执行共享协议的最小验证规则。子负责人是证据负责人，reviewer 只针对疑点复现，你不默认重跑测试或再做一遍完整代码 review。必要全量集中在稳定候选，不重复等价 full/ci。旧强制门禁若需缩减，在授权内协调契约迁移，生效前如实保留阻塞。

优先原生 Codex review，先查当前 head 是否已有有效结果或进行中的审查，避免 PR 自动审查和显式 @codex review 重复触发。只有有真实配额耗尽证据且用户已授权回退时，子负责人可自主调用未参与实现的 subsubagent reviewer。回退不冒充原生 approval，不自动满足 required check；不固定或伪称运行模型。pending、网络错误和审查 findings 不触发配额回退。

收到 [PR 交付记录](../../../.github/comment-templates/pr-delivery.md) 后检查：范围、依赖、验收、证据适用性、review findings、真实保护状态和用户合并授权。符合条件时，由你执行普通合并，禁止后代 merge/auto-merge 或绕过保护。合并决定绑定 head/base，变化后重新评估。用户已授权时不逐 PR 再次确认；未授权时先完成可审查结果再请求决定。

核对实际 merged 状态和最终落地 SHA，完成适用的合并后检查，然后逐 PR 执行共享清单；合入临时 stack base 不等于已落地最终目标。你负责全局依赖核验及远端删除，通知资源 owner 清理已授权的本地分支和专用临时 worktree，接收各项读回证据。已有清理授权不逐 PR 再问，不代替 owner 猜测本地是否安全。

更新总台账的清理队列；相关 PR 合并、关闭、base 调整或消费者退出后，重新处理受影响的延期项。尚有 PENDING/DEFERRED 时不标整个 PR 交付 DONE，但继续无关就绪任务。全部适用清理项收尾后，通知固定评论当前 owner 原位更新 DONE；除非先明确交接 owner，否则不直接编辑其评论。父 Issue 和 Epic 仍须核对全部原验收，不能因切片 PR 完成自动关闭。验收满足后停止顺带优化，不把无关新发现继续叠入同一 PR。

## 评论与交接

使用共享协议的定位、单 writer、去重和读回规则。主 agent 写 PLAN 和敏感决定，子负责人维护固定 Issue/PR 状态；你不并发修改其评论。仅为重要事件追加，不逐条转发工具输出。不重写历史 bot/user 评论。

交接只保留当前状态、授权决定、证据链接、comment ID/owner、延期清理与下一步。只按共享清单清理授权资源；保留未知资源、用户原修改、独有成果及尚有消费者的分支/worktree。技能不改变产品运行时的 authority 或单 writer 边界。
