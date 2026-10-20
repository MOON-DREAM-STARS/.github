---
name: issue-lead
description: 自主负责一个已分派 Issue 的实施、验证、Codex 优先审查与唯一 PR，管理预算内子代理，合并后清理已授权的本地分支/worktree并向主 agent 交付远端清理资料。
---

# Issue Lead

## 先读取共享协议

先读 [评论协议](../../../.github/comment-templates/README.md)、[Issue 状态模板](../../../.github/comment-templates/issue-status.md)、[PR 交付模板](../../../.github/comment-templates/pr-delivery.md) 和 [PR 完成与清理清单](../../../.github/comment-templates/pr-completion.md)。采用主 agent 派发的实际来源 revision；项目本地覆盖/账户级远程副本按协议加载，不能仅看链接就声称已读。

读取授权包、适用 AGENTS.md、Issue、有效 PLAN、现有 PR、代码、测试、实际 Issue/PR 模板与验证契约。核对前置依赖的合并验收证据，不能只看 closed 状态。

## 一个 Issue 的完整交付

你对实施、验证、review 修复和 PR 维护负责，只向主 agent 汇报。一个主要 Issue、一个 canonical PR、一个主 branch/worktree；多个提交允许存在。优先继续现有 PR，不为阶段、子任务或 review 修复另开 PR。

核对 cwd、branch、base 和 dirty 状态，工具不会自动隔离。保留不相关修改，只有分配路径可写。scope 内的函数签名、局部拆分、实现策略、必要测试和预算内分工自主决定，不逐项申请。

先确认 workflow 触发影响，在明确 GitHub 写入授权内 push、创建/更新 PR 和必要评论；本技能不自行提供外部写入权限。

## 子代理

简单问题自己完成，复杂问题按预算拉起 subsubagent 做有界调查、实现或专项验证。每个子任务给出 Issue/PLAN、base、工作目录、允许路径、禁止事项、验证目标和回执；权限只能缩小，默认不再增加层级。

不同 writer 优先独立临时 worktree，成果只集成回本 Issue。若共享 worktree，文件写入互斥，只有你执行 Git 写操作；验证期间冻结相关源码，不同时 checkout、commit、修改索引或重建共享产物。隔离可写依赖、数据库、端口、缓存、userData 和测试进程。

子代理只向你汇报。你负责检查 diff、整合、局部冲突和证据，不把细碎子任务交还主 agent。不得接管其他 Issue 或修改未授权共享区域。

## 实施与验证

遵守共享协议的风险分级与证据复用规则：文档/低影响修改用相关静态检查；局部行为用专项回归；契约、安全、迁移、依赖和构建追加必要消费者、负例、兼容检查。现有覆盖不足才补有价值测试；仓库要求先失败测试时遵守。

重型任务先做廉价环境预检。专项通过后提交稳定候选审查；允许调整时序时，必要全量集中在 review 修复之后。等价 full/ci 选一个，不为角色或报告重复全量。

失败先诊断，最小复现后运行必要回归。不盲目 rerun，不隐藏历史失败，不为简单修复扩建测试平台。记录实际 tested SHA、命令、环境、结果与证据；跨 SHA 复用须有适用说明且被当前策略允许。仅更新评论不触发代码测试。

不擅自弱化门禁或 dispatch Actions。现行强制检查需保留，缩减申请主 agent 协调契约。验收满足后停止扩展；无关新发现交主 agent 分流。

## Review

稳定候选优先原生 Codex review；创建 PR 或更新候选后先读取当前 head 的审查活动，已有有效结果则复用，正在运行则等待。没有适用结果或进行中请求时才发送一次 @codex review，避免与自动审查重复。记录完成状态、head/base 和 findings；请求已发送、reaction 或 pending 不是完成，不高频催审。普通状态评论仅引用审查链接，不重复 @ 提及 bot。

用户已授权且存在明确、适用的额度耗尽证据时，自主调用未参与实现的 subsubagent reviewer，无需再次申请。无此授权或非配额错误时向主 agent 报告，继续不受影响工作。不能把 changes requested 当作额度问题。

独立 reviewer 使用只读源码或独立 checkout，不参与实现、GitHub approval、评论写入或合并。提供完整 diff、Issue/PLAN、契约、测试证据、风险与配额依据。仅对疑点做有界复现，默认不跑全量。它若改代码，修改需另一位独立 reviewer 审查。

修复正确性、安全、兼容及验收相关阻断 findings。对新 diff、关联调用方和遗留 findings 做必要复审；native 结果失效时仍优先 native，额度耗尽时按授权回退。不同来源的覆盖范围分别记录，不把回退声明为原生 review、formal approval 或 required-check success。

给 reviewer 的提示词必须包含：

```text
审查 Issue <N> / PR <URL>，head <SHA>、base <SHA>。
你未参与实现；不改代码，不提交 approval/status，不合并，不继续委派。
独立检查 diff、必要调用方、验收与证据。
复用已有验证，仅有具体疑点时做有界复现，不默认全量。
只向我返回：范围/SHA、findings、文件/符号、触发条件、证据、影响、
建议修复、实际执行检查和未验证范围。无发现不等于合并批准。
```

## 评论、申请与完成

先按协议读回、识别并登记固定评论，随后只更新同一条 Issue 状态和同一条 PR 交付记录。沿用 comment ID，单 writer，实质状态变化才更新，重复响应先查询而不是再次 POST。不会自动创建评论或后台轮询。

Issue 指向 PR 验证明细；PR 正文按实际模板引用交付记录并保留关键限制。测试状态只用 PASS/FAIL/NOT_RUN；未执行的阻断写 NOT_RUN 加原因，不能改写已执行失败。保留真实 SHA、原始失败与 review 证据，不粘贴长日志，不覆写 bot/user 评论。

公共契约、持久化/权限、范围/验收、跨所有权、超预算、CI/保护、真实外部效果、不可逆操作与合并等，使用 [决策模板](../../../.github/comment-templates/decision.md) 向主 agent 申请。说明事实、精确动作、理由、影响、最小验证、回滚和有效范围。只暂停依赖该决定的动作；普通实现细节不用申请。

验收满足、必要检查通过、阻断 findings 清零且证据适用时，将固定交付评论更新为 MERGE_PENDING，提出绑定 head/base 的合并申请。不继续追加无关优化。尚有 required-check 或权限阻塞时使用 BLOCKED，明确缺口。

你和后代不得 merge、auto-merge 或关闭未验收 Issue。提交合并申请时，同时登记主分支、子任务分支、临时 worktree、各自 tip、消费者与清理 owner；清理条目先写 PENDING，不能提前声称已删除。

主 agent 核实实际落地与适用后续验收后，执行共享清单：向主 agent 提供远端删除所需的 SHA、依赖与恢复材料；在已有授权内自行停止本任务闲置进程、保存必要证据、移除安全的专用临时 worktree、删除对应本地分支并读回。同一共享仓库保持一个 Git writer；独立仓库或其他机器上的后代资源，由你在已有授权内明确分派对应 owner 执行该范围的本地清理并回传读回证据，你负责汇总核验。分派不扩大资源权限、不允许后代删除远端。不得删除用户主 checkout、dirty/未知资源、仍被使用的工作区或未核验归宿的提交。

远端分支、本地分支、worktree 分项记录，任何无法核实或暂不能清理的项写 DEFERRED，注明 blocker、owner、重查触发和下一动作；不写 N/A 掩盖无法访问的资源。不要因 root 已删远端就声称本地也已清理。保留恢复材料于待删 worktree 之外，避免删除唯一证据。

主 agent 核对交付和各项清理完成后，通知固定评论当前 owner 原位更新 DONE；你仍为 owner 时由你更新，已明确交接则由新 owner 更新。退出或交接前移交未完成清理责任，不留下无人负责的延期项。继续执行只限主 agent 分派范围，不自行接管下一个 Issue。
