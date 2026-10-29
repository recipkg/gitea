# Gitea 配方（提取中）

```toml
format = "recipkg/1"

[package]
name = "gitea"
version = "0.1.3"
kind = "software"
description = "自托管 Git 协作平台重建配方草案。"
entry = "BUILD_PROMPT.md"

[dependencies.quality]
git = "https://github.com/recipkg/recipkg.git"
rev = "41e5b55c6612a9a5a10e499b5ace6a1a3fed0f2b"
subdir = "recipes/software-quality"

[dependencies.design]
git = "https://github.com/recipkg/design-directions.git"
rev = "6fdba350d1effa2d50dc0185095bb91ca7a699ee"
```

上游 [go-gitea/gitea](https://github.com/go-gitea/gitea/tree/02c03d69d35963e40f9662d4a793a55d78649444)，固定提交 `02c03d69d35963e40f9662d4a793a55d78649444`，上游声明 MIT。仅部分合同已从源码提取，详细缺口和证据见 `COVERAGE.md`；不得声称本草案能够完整重建 Gitea。
