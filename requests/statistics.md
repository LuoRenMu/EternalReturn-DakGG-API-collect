# 统计接口

## 1. 段位分布

- 方法：`GET`
- 路径：`/v0/statistics/tier-distribution`
- 参数：
  - `teamMode={teamMode}`
  - `hl=zh_CN`

示例：

```text
GET https://er.dakgg.io/api/v0/statistics/tier-distribution?teamMode={teamMode}&hl=zh_CN
```

参数来源：

| 参数 | 是否来自 `data.md` | 实际来源 |
|---|---|---|
| `teamMode` | 否 | 固定枚举：`SOLO`、`DUO`、`SQUAD`、`COBALT` 或 `ALL` |
| `hl` | 否 | 调用方选择的语言代码 |

此接口不接收段位列表中的 `tiers[].id`。返回结果里的 `tierType` 才可与 `/v1/data/tiers` 的 `tiers[].id` 对照，用于取得段位名称和图片。

## 2. 角色统计

- 方法：`GET`
- 路径：`/v1/character-stats`
- 参数：
  - `dt=7`
  - `matchingMode={matchingMode}`
  - `teamMode={teamMode}`
  - `tier={tier}`

示例：

```text
GET https://er.dakgg.io/api/v1/character-stats?dt=7&matchingMode={matchingMode}&teamMode={teamMode}&tier={tier}
```

说明：

- `dt` 在这里是固定统计窗口
- `tier` 用于限定段位区间

参数来源：

| 参数 | 是否来自 `data.md` | 实际来源 |
|---|---|---|
| `dt` | 否 | 统计时间窗，来源项目使用 `3` 或 `7`；使用 `patch` 查询时传 `dt=0` |
| `matchingMode` | 否 | 固定枚举，常用 `RANK` 或 `COBALT` |
| `teamMode` | 否 | 固定枚举，排位常用 `SQUAD`，钴协议使用 `COBALT` |
| `tier` | 否 | 固定筛选 slug：`in1000`、`diamond_plus`、`mithril_plus`、`meteorite_plus`、`platinum_plus`、`gold`、`silver`、`bronze`、`iron` |
| `patch` | 否 | 可选版本号；与 `tier`/普通 `dt` 查询互斥，使用时通常为 `dt=0&patch={patch}` |
| `hl` | 否 | 调用方选择的语言代码 |

注意：`tier` 筛选值不是 `/v1/data/tiers` 返回的 `tiers[].key`。基础段位数据主要用于把统计响应中的段位 id 转成名称、完整图片和圆形图标，而不是直接生成此请求的 `tier` 参数。
