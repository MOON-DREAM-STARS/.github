<!-- agent-comment:decision:v1 -->
<!-- 事件记录：先读取 README.md。申请和决定分别追加；禁止原位把 REQUESTED 改成 APPROVED。 -->

## Coordination Decision — <唯一 Decision ID>

- Type: <CONTRACT_CHANGE / SCOPE_CHANGE / MERGE>
- Issue / PR: <链接>
- PLAN Revision: <适用版本及链接>
- State: <REQUESTED / APPROVED / REJECTED / SUPERSEDED>
- Actor: <申请者或实际决策者>
- Authority: <可信授权来源；申请不等于获准>
- Related Record: <所回复的申请或被替代决定链接；首次申请写 None>
- Agent Run ID: <本次执行标识>
- Recorded: <带时区的 ISO 8601>

### Proposed Action
<精确接口、行为、允许路径或候选 head/base；不得泛化为无限授权>

### Reason and Impact
<事实、变更理由、受影响消费者、验收或依赖>

### Verification and Rollback
<最小必要验证与恢复方式；不适用须说明>

### Decision
<待决定写 Pending；已决定写允许/拒绝范围、条件、决策者及依据>

### Validity
<绑定的 PLAN/契约版本、候选 head/base，以及失效或重新评估条件>

<!-- 评论不是身份验证、GitHub formal approval 或分支保护的替代品。 -->
