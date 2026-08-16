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
- 返回内容里通常需要从页面状态中提取结构化数据

## 2. 对局记录

- 方法：`GET`
- 路径：`/v1/players/{nickname}/matches`
- 查询参数：
  - `season={seasonType}` 可选
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

## 常见拆分点

- 如果后续要补赛季筛选、分页、房间号分析，建议单独拆文件
- 对局接口通常变化更快，单独维护比放在总文件里更稳妥
