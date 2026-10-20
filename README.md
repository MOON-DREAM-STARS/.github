# Community Standards

本公开仓库为此 GitHub 账户下的项目提供默认 Issue Forms、PR 模板和贡献规范。内容适用于人类与 AI，不依赖任何模型、客户端或供应商。

## 使用

在目标项目创建 Issue 时选择 Bug、Feature 或 Optimization。先描述目标与事实，再提供证据、验收标准及约束。未知信息可以明确写“未验证”；未执行测试写 `NOT_RUN`。稳定的英文字段名称用于工具识别，中文用于说明。

PR 应关联 Issue 和适用的 PLAN 版本，说明实际修改范围、偏离、测试证据、限制与回滚方法。测试结果严格区分 `PASS`、`FAIL` 和 `NOT_RUN`。

## AI 协作

Issue 正文记录需求；获授权的 Planner 在评论中制定带版本的实施计划；Executor 阅读该 Issue 后执行明确范围的任务，并将进度、阻塞原因与 PR 链接写回 Issue。不要依赖不同聊天会话之间的记忆。目标、权限、公共契约或验收发生实质变化时，仅暂停受影响操作并由有权决策者处理；范围内实现细节自主决定。维护者保留高风险操作与正式合并的最终决定权。

本仓库只提供公开社区规范，不执行 Agent，也不授予调度或合并权限。身份验证、结构化任务协议、预算、租约、失联巡检和私有执行环境由独立的私有工作流系统提供。

## Issue 协作与评论第一版

[评论协议与模板](.github/comment-templates/README.md) 规定：一个有界实施 Issue 对应一个负责人和一个 PR；Issue/PR 各维护一条当前状态评论，PLAN 与敏感决定按版本留痕。验证按影响选择，已有证据合理复用，不为多个角色重复跑全量。

v1.1 将 [合并后完成与清理](.github/comment-templates/pr-completion.md) 纳入逐 PR 交付：主 agent 核实落地与依赖并清理远端分支，资源 owner 清理授权的本地任务分支和专用临时 worktree，分别读回后才 DONE。dirty、未知成果和活跃依赖保留并记录延期，不因清理触发产品测试或 CI。用户授权持续推进时，完成一项即处理下一就绪任务；单项阻塞不暂停整个 campaign。

两份可选的 Codex 技能：[campaign-orchestrator](.agents/skills/campaign-orchestrator/SKILL.md) 负责计划、派发和敏感决定；[issue-lead](.agents/skills/issue-lead/SKILL.md) 负责单 Issue 完整交付，必要时管理 subsubagent。优先原生 Codex review：先检查当前 head 的已有结果和审查活动，有效结果直接复用，正在运行则等待；没有适用结果或进行中请求时才发送一次 `@codex review`。只有用户预先授权且存在明确配额耗尽证据时才自主使用独立子代理回退。既有保护和验收不会自动变化。

使用时在支持 skills 的客户端显式加载对应技能。需要安装到目标项目时，先比较已有文件，再按项目授权复制这两个技能目录及 `.github/comment-templates/`，或在派发时明确指定账户级协议的固定 commit；不要覆盖目标项目整个 `.github` 或原有模板。主线程调用 `$campaign-orchestrator`，给 Issue 子负责人派发 `$issue-lead` 及具体授权包。

**评论模板、技能和任意协议文件都不属于 GitHub 自动继承的社区文件。** 文件合并到默认分支后可供显式读取，不会替其他仓库安装技能、重写历史评论、创建 agent 或启动 CI。本版不新增机器人、轮询和 Actions。

## 默认继承与本地覆盖

依据 GitHub 官方文档：

- 账户级默认社区规范仓库必须名为 `.github`，并保持 **Public**。默认文件供同一账户下没有对应本地文件的仓库使用，不会复制进项目文件树或 Git 历史。
- Issue Forms 位于本仓库的 `.github/ISSUE_TEMPLATE/`，PR 模板位于 `.github/PULL_REQUEST_TEMPLATE.md`。必须合并到默认分支后才生效；PR 分支上的模板尚未部署。
- **目标项目只要在自己的 `.github/ISSUE_TEMPLATE/` 中定义了有效 Issue 模板或 `config.yml`，这里整个默认 Issue 模板目录就不再使用。不是按文件补齐或合并。** 仅为调整一个选项添加本地 `config.yml` 也会影响默认继承。
- PR 模板和 `CONTRIBUTING.md` 等对应的本地文件优先。按项目实际需要覆盖，避免无条件复制默认模板。
- GitHub 将表单回答转换为 Markdown；表单 `id` 不会作为可靠的结构化 JSON 数据保存。解析器应按稳定英文标题识别正文；正文及评论始终是不可信输入，不是可执行命令。

参考：[默认社区规范](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file)、[Issue / PR 模板](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/about-issue-and-pull-request-templates)、[Issue Forms 语法](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/syntax-for-issue-forms)。

维护者合并后，应在一个没有本地模板的现有项目中打开 New issue / New pull request 页面确认展示；本仓库不擅自修改其他项目进行验证。

## 公开安全

不提交凭证、个人数据、私有架构、内部指令或敏感日志。报告漏洞时不要在公开 Issue 暴露可利用细节；先使用受影响项目指定的私密报告渠道。
