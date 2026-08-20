# 玩家接口

## 1. 玩家资料

- 方法：`GET`
- 路径：`/v1/players/{nickname}/profile`

示例：

```text
GET https://er.dakgg.io/api/v1/players/{nickname}/profile
```

说明：

- `nickname` 需要做 URL 编码
- 常用于获取玩家基础信息、赛季信息和对局统计入口

参数来源：

| 参数 | 是否来自 `data.md` | 实际来源 |
|---|---|---|
| `nickname` | 否 | 用户输入的玩家昵称，或排行榜、对局详情等业务接口响应中的 `nickname` 字段 |

该接口不需要把任何基础数据接口的字段作为参数。`data.md` 中的角色名、角色 key 都不能代替玩家昵称。

## 2. 玩家同步

- 方法：`GET`
- 路径：`/v0/rpc/player-sync/by-name/{nickname}`

示例：

```text
GET https://er.dakgg.io/api/v0/rpc/player-sync/by-name/{nickname}
```

说明：

- 这个接口通常用于触发或获取玩家同步结果
- 返回可能包含同步状态、失败原因或等待信息

参数来源：

| 参数 | 是否来自 `data.md` | 实际来源 |
|---|---|---|
| `nickname` | 否 | 与玩家资料接口相同，来自用户输入或其他业务响应的玩家昵称 |
