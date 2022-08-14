# DevOps 工具鉴宝之 Atlassian Jira

从 DevOps 角度，体验 Atlassian 全家桶核心用户场景和产品功能，了解大型企业的需求管理和研发工具链落地实施。

## background (5 min)

- product introduction

Atlassian 提供面向企业业务流程的协同办公产品，作为一家 SaaS 公司，不雇佣一个销售人员，仅通过口碑获客，市值达 10 亿美金级别，极其罕见。

创办于 2002 年，截止 2015 年 12 月，Atlassian 已经有 79 家财富 100 强客户，273 家财富 500 强客户。不依靠任何一个销售人员，就能将占领过半的财富 500 强客户。

2019《财富》未来 50 强榜单公布，Atlassian 排名第 6。

- user case

客户分布全球，目前每月约 250 万活跃用户。

## Jira configuration story (10 min - yy)

- plan 如何规划
- process 如何实施
- result 效果展示

## jira delivery story (40 min)

### requirement management (yy)

- product roadmap (gantt)
- PRD in confluence => user story => backlog
- scrum board (kanban)
- active sprint
  - 拉取分支时，自动更新 Jira Story 卡片到 In Progress 状态
  - PR Merged 时，自动更新 Jira Story 卡片到 Resolved 状态
- kanban
- close sprint (1 released, 1 undone)
- retrospective

### development integration (toby)

- select user story as example
- create feature branch
- IDE integration with Jira and Bitbucket
- commit convention
- code push & code review in bitbucket (jira in progress)
- Bitbucket pipeline (provided by atlassian)
  - build
  - test
  - scan
  - publish
  - deploy
- fix review comment and push again, resolve review tasks
- merge to master branch (jira revolved)
- CD triggered in master branch, go to staging environment
- pause prod deployment & gating
- start regression testing in staging (mention testing plugin)
- release management => change ticket
- validate ticket and go production
- close jira

### deployment management (yy)

- Jira Service Management：变更管理：
- 在 CD 中，到 Production 部署时，会自动创建线上变更申请单；
- CD 关联的代码仓库对应的服务变更的 Approvers 收到审批提醒
- Service Approvers 审批通过
- CD 生产环境部署继续
- CD 生成环境部署完成（成功），Jira Story 卡片自动更新到 Done 状态
