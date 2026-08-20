# 请求文档索引

这里只放请求相关内容，避免把接口说明、参数表、示例和资源规则全压进一个文件。

## 文件列表

| 文件 | 范围 |
|---|---|
| [data.md](data.md) | 基础数据接口 |
| [user.md](user.md) | 玩家资料与同步 |
| [game.md](game.md) | 对局记录与角色分析 |
| [leaderboard.md](leaderboard.md) | 排行榜 |
| [statistics.md](statistics.md) | 段位分布与角色统计 |
| [open-api.md](open-api.md) | 永恒轮回 Open API |
| [official.md](official.md) | 永恒轮回官网接口 |
| [image.md](image.md) | 图片资源路径规则 |

## 请求格式

- 当前收集的接口均使用 `GET`
- 去重以“主机 + 方法 + 规范化路径”为准；同一路径位于不同主机时视为不同接口
- 查询参数直接拼接到 URL
- 需要注意编码的字段主要是昵称 `nickname`
- 如果某些页面依赖前端渲染数据，返回结果里可能会夹带页面状态对象
