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

