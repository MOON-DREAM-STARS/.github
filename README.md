# Community Standards

本公开仓库为此 GitHub 账户下的项目提供默认 Issue Forms、PR 模板和贡献规范。内容适用于人类与 AI，不依赖任何模型、客户端或供应商。

## 使用

在目标项目创建 Issue 时选择 Bug、Feature 或 Optimization。先描述目标与事实，再提供证据、验收标准及约束。未知信息可以明确写“未验证”；未执行测试写 `NOT_RUN`。稳定的英文字段名称用于工具识别，中文用于说明。

PR 应关联 Issue 和适用的 PLAN 版本，说明实际修改范围、偏离、测试证据、限制与回滚方法。测试结果严格区分 `PASS`、`FAIL` 和 `NOT_RUN`。

## AI 协作

Issue 正文记录需求；获授权的 Planner 在评论中制定带版本的实施计划；Executor 阅读该 Issue 后执行明确范围的任务，并将进度、阻塞原因与 PR 链接写回 Issue。不要依赖不同聊天会话之间的记忆。计划变更或事实冲突时，先暂停并重新取得授权。维护者保留高风险操作与正式合并的最终决定权。

本仓库只提供公开社区规范，不执行 Agent，也不授予调度或合并权限。身份验证、结构化任务协议、预算、租约、失联巡检和私有执行环境由独立的私有工作流系统提供。

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
