<!-- agent-comment:pr-delivery:v1 -->
<!-- 固定评论：先读取 README.md；原始失败/review 证据继续保留，不能因更新而删除。 -->

## Delivery Status

- Issue: <唯一主要 Issue>
- Owner: <Issue 子负责人>
- Agent Run ID: <本次执行标识>
- PLAN Revision: <版本及链接>
- Candidate Head: <完整 SHA>
- Target Base: <分支及核验时的完整 SHA>
- State: <READY / IN_PROGRESS / BLOCKED / IN_REVIEW / MERGE_PENDING / DONE>
- Record Revision: <从 1 开始递增>
- Updated: <带时区的 ISO 8601>

### Acceptance
| Criterion | Result | Evidence |
| --- | --- | --- |
| <验收条件> | <已满足／未满足／未核验> | <可读取的证据或限制> |

### Tests and Verification
| Status | Command / Check | Evidence | Commit / Environment |
| --- | --- | --- | --- |
| NOT_RUN | <检查> | <未运行原因；执行后填写真实结果；复用须注明依据> | <实际被测 SHA 与环境，或未执行> |

<!-- Status 仅允许 PASS、FAIL、NOT_RUN；BLOCKED 写成 NOT_RUN 并解释，不掩盖已执行失败。 -->

### Review
- Source: <CODEX / SUBSUBAGENT / MIXED / PENDING>
- Reviewed Scope: <每个来源对应的 reviewer、head/base 与覆盖范围；未完成写 Pending>
- Evidence: <审查链接或可读取回执>
- Blocking Findings: <剩余项、已解决记录，或无>
- Quota Fallback: <N/A；或用户授权依据、配额证据及适用窗口>

### Remaining Work
None / <剩余动作、required checks、未知保护状态、负责人和 blocker>

### Requested Action
None / <需要主 agent 作出的具体决定及申请链接>

### Completion and Cleanup
- Merge: <未合并；或 PR merged、merge SHA、最终目标落地证据>
- Post-merge Verification: <待执行；或必要检查结果/证据复用依据>
- Cleanup Authority: <授权依据、资源范围及保留项；无权限写 DEFERRED>

| Resource | Repository / Ref or Path / Tip | Owner | Status | Evidence / Recovery | Blocker / Trigger / Next Action |
| --- | --- | --- | --- | --- | --- |
| Remote branch | <仓库、remote、完整 ref、删除前 SHA> | <主 agent> | PENDING | <读回与恢复来源> | <阻塞、重查触发及下一步；无则 None> |
| Local branch | <环境/仓库、完整 ref、删除前 SHA> | <资源 owner> | PENDING | <读回与恢复来源> | <阻塞、重查触发及下一步；无则 None> |
| Temporary worktree | <环境/仓库、worktree、branch/HEAD> | <资源 owner> | PENDING | <内容/消费者核验、移除读回、证据保存位置> | <阻塞、重查触发及下一步；无则 None> |

<!-- 按实际资源逐行登记，包括后代资源；没有该类资源写 N/A 和具体理由。
清理 Status 仅用 PENDING/CLEANED/DEFERRED/N/A，不与测试 PASS/FAIL/NOT_RUN 混用。
所有适用资源收尾、实际落地及必要验收满足后才 DONE；细则见 pr-completion.md。
公开评论的环境/path 使用无敏感信息的标识，必要完整定位保存在获授权的证据位置。 -->
