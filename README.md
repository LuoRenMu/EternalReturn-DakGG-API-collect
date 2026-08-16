# EternalReturn-DakGG-API-collect

DAK.GG 永恒轮回相关接口的整理文档。

这个仓库的目标很简单：

1. 记录目前已经整理到的请求路径、参数和返回入口。
2. 把请求样例拆到独立文件，避免所有内容堆在一个 README 里。
3. 维持和 `bilibili-api-collect` 类似的结构风格，入口页只负责索引。

## 说明

- 默认基地址：`https://er.dakgg.io/api`
- 当前整理的接口大多为 `GET`
- 由于来源是公开网页和前端可见接口，字段和路径可能随站点更新而变化
- 请不要把这类文档当成稳定契约，实际对接时要保留容错

## 目录

| 文件 | 内容 |
|---|---|
| [requests/README.md](requests/README.md) | 请求文档总索引 |
| [requests/data.md](requests/data.md) | 基础数据接口 |
| [requests/user.md](requests/user.md) | 账号与玩家接口 |
| [requests/game.md](requests/game.md) | 对局与角色分析接口 |
| [requests/leaderboard.md](requests/leaderboard.md) | 排行榜接口 |
| [requests/statistics.md](requests/statistics.md) | 统计接口 |
| [requests/image.md](requests/image.md) | 图片资源规则 |

## 约定

- `hl` 参数统一表示语言环境，常见值为 `zh_CN` 或 `zh_cn`
- 路径中的 `nickname`、`characterKey`、`serverName`、`teamMode`、`matchingMode` 等字段按接口要求传入
- 本仓库只整理请求与资源规则，不额外封装 SDK

## 贡献

如果你继续补充接口，建议按下面的粒度拆分：

1. 一个业务域一个文件
2. 一个请求示例一个小节
3. 新增字段时优先补充参数说明，再补充响应结构

## 许可

本仓库采用 AGPL-3.0 许可。请在遵守许可的前提下使用和传播。
