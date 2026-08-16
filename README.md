# EternalReturn-DakGG-API-collect

DAK.GG 永恒轮回相关接口的整理文档。


## 说明
- 默认基地址：`https://er.dakgg.io/api`
- 当前整理的接口大多为 `GET`
- 由于来源是公开网页和前端可见接口，字段和路径可能随站点更新而变化
- 请不要把这类文档当成稳定契约，实际对接时要保留容错
- v0/v1/v2表示API不同版本号，对应请求参数与响应都不同


## 目录

| 文件 | 内容 |
|---|---|
| [requests/README.md](requests/README.md) | 请求文档总索引 |
| [requests/data.md](requests/data.md) | 基础数据接口 |
| [requests/user.md](requests/user.md) | 账号与玩家接口 |
| [requests/game.md](requests/game.md) | 对局与角色分析接口 |
| [requests/leaderboard.md](requests/leaderboard.md) | 排行榜接口 |
| [requests/statistics.md](requests/statistics.md) | 统计接口 |

## 约定

- `hl` 参数统一表示语言环境，常见值为 `zh_CN` 或 `kr`、`en`
- 路径中的 `nickname`、`characterKey`、`serverName`、`teamMode`、`matchingMode` 等字段按接口要求传入
- 本仓库只整理请求与资源规则，不额外封装 SDK


## 许可

本仓库的所有数据都来自Nimble Neuron