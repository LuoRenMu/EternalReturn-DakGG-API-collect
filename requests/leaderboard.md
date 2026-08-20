# 排行榜接口

## 1. 排行榜

- 方法：`GET`
- 路径：`/v0/leaderboard`
- 参数：
  - `page={page}`
  - `seasonKey={seasonType}`
  - `serverName={serverName}`
  - `teamMode={teamMode}`
  - `hl=zh_CN`

示例：

```text
GET https://er.dakgg.io/api/v0/leaderboard?page={page}&seasonKey={seasonType}&serverName={serverName}&teamMode={teamMode}&hl=zh_CN
```

说明：

- 这是典型的分页查询接口
- 排名、服务器和队伍模式共同决定结果集

参数来源：

| 参数 | 是否来自 `data.md` | 对应字段或来源 |
|---|---|---|
| `page` | 否 | 调用方维护的分页编号，从 `1` 开始 |
| `seasonKey` | 是 | 赛季列表 `/v1/data/seasons` 的 `seasons[].key`；若先按 `seasons[].id` 选择赛季，需要在同一对象上转换为 `key` |
| `serverName` | 否 | 固定服务器值：`seoul`、`asia2`、`asia3`、`ohio`、`frankfurt`、`saopaulo`、`global` |
| `teamMode` | 否 | 固定队伍模式：`SOLO`、`DUO`、`SQUAD`、`COBALT` 或 `ALL` |
| `hl` | 否 | 调用方选择的语言代码 |

赛季转换示例：界面保存了 `seasonId=41` 时，在 `seasons[]` 中查找 `id == 41`，再把同一对象的 `key` 作为 `seasonKey`。即 `seasons[].id -> 查找对象 -> seasons[].key -> seasonKey`。

## 2. 单角色排行榜

- 方法：`GET`
- 路径：`/v0/leaderboard/characters/{characterKey}`
- 参数：
  - `seasonKey={seasonType}`
  - `teamMode={teamMode}`
  - `sortType={sortType}`
  - `page={page}`
  - `hl=zh_CN`

示例：

```text
GET https://er.dakgg.io/api/v0/leaderboard/characters/{characterKey}?seasonKey={seasonType}&teamMode={teamMode}&sortType={sortType}&page={page}&hl=zh_CN
```

说明：

- `characterKey` 使用角色 key，例如 `Jackie`
- `page` 从 1 开始
- `sortType` 决定排行榜的排序指标

参数来源：

| 参数 | 是否来自 `data.md` | 对应字段或来源 |
|---|---|---|
| `characterKey` | 是 | 角色列表 `/v1/data/characters` 的 `characters[].key` |
| `seasonKey` | 是 | 赛季列表 `/v1/data/seasons` 的 `seasons[].key` |
| `teamMode` | 否 | 当前已知值为 `SQUAD`、`COBALT`；钴协议通常配合 `seasonKey=NORMAL` |
| `sortType` | 否 | 固定排序枚举：`MATCH_COUNT`、`TIER`、`WIN_RATE` |
| `page` | 否 | 调用方维护的分页编号，从 `1` 开始 |
| `hl` | 否 | 调用方选择的语言代码 |

这里有两个直接的基础数据传递关系：`characters[].key -> characterKey`，以及 `seasons[].key -> seasonKey`。
