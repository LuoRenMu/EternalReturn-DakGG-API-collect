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
