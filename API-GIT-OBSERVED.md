# 私有仓库、Git 和议题：固定源码样本

上游 [Gitea 固定提交 `02c03d69d35963e40f9662d4a793a55d78649444`](https://github.com/go-gitea/gitea/tree/02c03d69d35963e40f9662d4a793a55d78649444)，Linux amd64，以 Go `go1.27.3-X:nodwarf5`、`CGO_ENABLED=0 go build -p 2` 构建后端；构建版本字符串为 `development`，Go 构建元数据指向该提交。使用源码目录中的动态模板，**没有构建前端资源**。测试用一次性 HOME、SQLite、回环 HTTP、Git 仓库及两个虚构账户；关闭 SSH、注册、邮件和 Gravatar，HTTP Basic 使用测试密码。进程未置于操作系统或网络沙箱，不连接真实项目或凭据。

## 私有仓库和议题

- Alice 创建私有仓库，匿名用户及未授权 Bob 请求仓库均返回 404；Bob 在未授权时创建议题也返回 404。Alice 用 Git HTTP 推送提交；Bob 授权前克隆失败。
- Alice 授予 Bob 只读协作权限后，Bob 可读仓库并克隆，克隆的提交 ID 和文件内容与推送一致。该样本未测试 SSH、其他权限组合、匿名公开仓库或全部 Git 命令。
- Alice 发起无标题议题请求返回 422。只读 Bob 可以创建议题、编辑自己议题的正文；创建时随请求附带已存在的标签 ID，成功响应和随后读取的标签列表均为空，另行添加标签返回 403。Bob 编辑 Alice 议题的正文返回 403。只说明该仓库、账户和配置的观察，不推断所有议题权限。
- Alice 创建正文为 `first` 的议题，返回 201 和 `content_version`；携带当前版本更新为 `second` 返回 201，版本增加。携带旧版本尝试写入 `stale` 返回 409，随后读取仍为 `second`；省略版本更新为 `third` 返回 201。未测试多字段更新的原子性或所有竞争时序。
- 正常终止并重启同一进程配置后，Bob 仍可读取双方议题的最后正文，并能重新克隆推送的同一提交。该样本不是崩溃、断电、备份恢复或安全隔离证明。

可运行样本：[standard-library-verification 的 `test_gitea.py`](https://github.com/recipkg/standard-library-verification/blob/main/tests/test_gitea.py)。需显式指定候选可执行文件；若使用非嵌入构建，另指定静态资源源码目录。测试仅覆盖固定上游后端的选定路径，不是完整功能、UI 或独立重建验收。
