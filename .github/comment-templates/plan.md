<!-- agent-comment:plan:v1 -->
<!-- 版本事件：先读取 README.md。实质变更发布新 revision，链接旧版；不要无痕改写授权。 -->

## PLAN — <Revision>

- Issue: <唯一主要 Issue>
- Owner: <负责派发的主 agent>
- Authority: <真实用户/维护者授权依据；本评论不创造授权>
- Protocol Revision: <评论协议来源仓库、完整 commit SHA、路径>
- Supersedes: <旧 PLAN 链接，首次为 None>
- Agent Run ID: <执行标识>
- Recorded: <带时区的 ISO 8601>

### Objective and Acceptance
<引用 Issue 的目标与验收，不维护矛盾副本>

### Scope and Autonomy
- Allowed: <可写路径、普通自主决策、已授权 GitHub 操作>
- Non-Goals: <禁止范围、不变量与契约>
- Escalation: <需要主 agent 决定的边界>

### Dependencies and Ownership
<前置证据、子负责人、共享文件唯一 owner、主 branch/worktree、子代理与资源预算>

### Cleanup Ownership and Scope
<真实授权依据；主 agent 负责远端删除，本地资源 owner 负责本地分支/专用 worktree；
仓库/remote/ref/path 与登记位置、保留项、消费者、待删 worktree 外的恢复和证据位置。
跨机器逐项指定 owner；无权限不得从 PLAN 推导授权。>

### Implementation Steps
<有限步骤；范围内技术细节由子负责人决定，无需逐项重新申请>

### Verification Strategy
<必要检查、全量触发条件、证据复用依据、Codex 优先及配额回退授权状态>

### Completion and Pause Conditions
<停止扩展与申请合并的条件、合并权限来源；实际落地/必要验收及逐项清理后才 DONE；
延期清理的 owner 与重查触发；阻塞只暂停受影响动作，继续其他已授权就绪任务>
