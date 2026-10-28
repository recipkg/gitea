# 来源与范围

- 上游 [Gitea](https://github.com/go-gitea/gitea/tree/02c03d69d35963e40f9662d4a793a55d78649444)，提交 `02c03d69d35963e40f9662d4a793a55d78649444`；README 和 LICENSE 声明 MIT。第三方组件及资源另查各自许可。
- 已阅读 README、`routers/api/v1/repo/issue.go` 中创建和编辑、`modules/structs/issue.go` 中表单字段、`services/issue/issue.go` 的创建事务与通知、`routers/api/v1/repo/pull.go` 的合并入口及 `tests/integration/api_issue_test.go` 的正文版本测试。它们是源码/测试证据，不是本次运行结果。
- 未启动源实例或完成从配方的独立重建；认证、完整 Git 功能、所有 API/数据库/权限、UI、actions、包管理、安全与恢复未完整提取或验收。主分支提交可能与发布版本有差异。
- 本轮在上游源码目录运行 `go test ./modules/markup/csv`，通过；此测试仅覆盖该 CSV 标记模块，不能证明议题接口或完整服务可用。
