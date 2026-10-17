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

<!-- 实际合并后在 Acceptance/Evidence 中记录落地 SHA 与适用的后续验证，再使用 DONE。 -->
