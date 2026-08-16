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
