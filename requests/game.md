# 对局与角色分析

## 1. 角色分析页

- 方法：`GET`
- 原始页面：`https://dak.gg/er/characters/{characterKey}`
- 常用查询参数：
  - `hl=zh_CN`
  - `tab=introduction`
  - `teamMode={teamMode}`
  - `matchingMode={matchingMode}`
  - `tier={tier}` 可选

示例：

```text
GET https://dak.gg/er/characters/{characterKey}?hl=zh_CN&tab=introduction&teamMode={teamMode}&matchingMode={matchingMode}&tier={tier}
```

说明：

- 这是页面接口，不是纯 JSON 接口
- 返回内容是由Next.js 生成 json数据位于__NEXT_DATA__中

参数来源：

| 参数 | 是否来自 `data.md` | 对应字段或来源 |
|---|---|---|
| `characterKey` | 是 | 角色列表 `/v1/data/characters` 的 `characters[].key`，例如 `Jackie`；不要传 `characters[].id` 或本地化后的 `name` |
| `hl` | 否 | 调用方选择的语言代码，例如 `zh_CN`、`en`、`kr` |
| `tab` | 否 | 页面固定标签；介绍页使用 `introduction` |
| `teamMode` | 否 | DAK.GG 固定枚举，如 `SQUAD`、`COBALT` |
| `matchingMode` | 否 | DAK.GG 固定枚举，如 `RANK`、`NORMAL`、`COBALT` |
| `tier` | 否 | 统计筛选 slug，如 `in1000`、`diamond_plus`、`mithril_plus`。它不是段位列表 `tiers[].id` 或 `tiers[].key` |

传递示例：先在角色列表中找到 `characters[].id == 1` 的对象，取其 `key == "Jackie"`，再将 `Jackie` 放入 `{characterKey}`。

## 2. 对局记录

- 方法：`GET`
- 路径：`/v1/players/{nickname}/matches`
- 查询参数：
  - `season={seasonType}` 
  - `matchingMode={matchingMode}`
  - `teamMode={teamMode}`
  - `page={page}`

示例：

```text
GET https://er.dakgg.io/api/v1/players/{nickname}/matches?season={seasonType}&matchingMode={matchingMode}&teamMode={teamMode}&page={page}
```

说明：

- `season` 可省略
- `page` 从 1 开始
- 玩家昵称同样需要 URL 编码

参数来源：

| 参数 | 是否来自 `data.md` | 对应字段或来源 |
|---|---|---|
| `nickname` | 否 | 用户输入或其他业务接口响应中的玩家昵称 |
| `season` | 是 | 赛季列表 `/v1/data/seasons` 的 `seasons[].key`，例如 `SEASON_21`；不是数字 `id` |
| `matchingMode` | 否 | 固定枚举：`NORMAL`、`RANK`、`COBALT`、`UNION`、`LONE_WOLF` 或 `ALL` |
| `teamMode` | 否 | 固定枚举：`SOLO`、`DUO`、`SQUAD`、`COBALT` 或 `ALL` |
| `page` | 否 | 调用方维护的分页编号，从 `1` 开始 |

赛季传递链：`data.seasons[].key -> season`。例如选中的赛季对象为 `{"id": 41, "key": "SEASON_21"}` 时，请求参数应为 `season=SEASON_21`。

## 3. 单局详情

- 方法：`GET`
- 路径：`/v1/players/{nickname}/matches/{seasonId}/{gameId}`
- 查询参数：
  - `hl={language}`

示例：

```text
GET https://er.dakgg.io/api/v1/players/{nickname}/matches/{seasonId}/{gameId}?hl=zh_CN
```

说明：

- `nickname` 需要 URL 编码
- `seasonId` 是数字赛季 id，不是 `SEASON_21` 形式的赛季 key
- `gameId` 可从玩家对局记录中取得

参数来源：

| 参数 | 是否来自 `data.md` | 对应字段或来源 |
|---|---|---|
| `nickname` | 否 | 与对局记录请求相同的玩家昵称 |
| `seasonId` | 间接相关 | 首选上一接口返回的 `matches[].seasonId`；排位对局也可与赛季列表的 `seasons[].id` 对照。普通模式通常使用接口返回值，不要自行猜测 |
| `gameId` | 否 | 对局记录响应中的 `matches[].gameId` |
| `hl` | 否 | 调用方选择的语言代码 |

完整传递链：先请求玩家对局记录，再从同一条 `matches[]` 记录同时取出 `seasonId` 和 `gameId`，与原请求的 `nickname` 一起组成详情 URL。不要把 `seasons[].key` 传给 `{seasonId}`。
