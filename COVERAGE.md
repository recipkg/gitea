# 来源与范围

- 上游 [Gitea](https://github.com/go-gitea/gitea/tree/02c03d69d35963e40f9662d4a793a55d78649444)，提交 `02c03d69d35963e40f9662d4a793a55d78649444`；README 和 LICENSE 声明 MIT。第三方组件及资源另查各自许可。
- 已阅读 README、`routers/api/v1/repo/issue.go` 中创建和编辑、`modules/structs/issue.go` 中表单字段、`services/issue/issue.go` 的创建事务与通知、`routers/api/v1/repo/pull.go` 的合并入口及 `tests/integration/api_issue_test.go` 的正文版本测试。它们是源码/测试证据，不是本次运行结果。
- 已从固定提交构建后端，隔离实测私有仓库、Git HTTP、只读协作、议题权限及正文版本冲突和正常重启，见 `API-GIT-OBSERVED.md`；没有构建前端或从配方独立重建。其他认证和权限、完整 Git 功能、全部 API/数据库、UI、actions、包管理、安全与故障恢复未完整提取或验收。主分支提交可能与发布版本有差异。
- 本轮在上游源码目录运行 `go test ./modules/markup/csv`，通过；此测试仅覆盖该 CSV 标记模块，不能证明议题接口或完整服务可用。
