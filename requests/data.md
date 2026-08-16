# 基础数据接口

基地址：`https://er.dakgg.io/api`

这一组接口主要用于拉取静态或低频变化的数据。

## 1. 段位

- 方法：`GET`
- 路径：`/v1/data/tiers`
- 参数：`hl=zh_cn`

示例：

```text
GET https://er.dakgg.io/api/v1/data/tiers?hl=zh_cn
```

## 2. 赛季列表

- 方法：`GET`
- 路径：`/v1/data/seasons`
- 参数：`hl=zh_CN`

示例：

```text
GET https://er.dakgg.io/api/v1/data/seasons?hl=zh_CN
```

## 3. 当前赛季

- 方法：`GET`
- 路径：`/v0/current-season`
- 参数：`hl=zh_CN`

示例：

```text
GET https://er.dakgg.io/api/v0/current-season?hl=zh_CN
```

## 4. 角色列表

- 方法：`GET`
- 路径：`/v1/data/characters`
- 参数：`hl=zh_CN`

示例：

```text
GET https://er.dakgg.io/api/v1/data/characters?hl=zh_CN
```

## 5. 物品列表

- 方法：`GET`
- 路径：`/v1/data/items`
- 参数：`hl=zh-cn`

示例：

```text
GET https://er.dakgg.io/api/v1/data/items?hl=zh-cn
```

## 6. 熟练度 / 武器

- 方法：`GET`
- 路径：`/v1/data/masteries`
- 参数：`hl=zh_cn`

示例：

```text
GET https://er.dakgg.io/api/v1/data/masteries?hl=zh_cn
```

## 7. 潜能技能

- 方法：`GET`
- 路径：`/v1/data/trait-skills`
- 参数：`hl=zh_cn`

## 8. 战术技能

- 方法：`GET`
- 路径：`/v1/data/tactical-skills`
- 参数：`hl=zh_cn`

## 9. 灌注

- 方法：`GET`
- 路径：`/v1/data/infusions`
- 参数：`hl=zh_cn`

## 10. 角色技能

- 方法：`GET`
- 路径：`/v1/data/skills`
- 参数：`hl=zh_cn`

## 批量示例

```text
GET https://er.dakgg.io/api/v1/data/trait-skills?hl=zh_cn
GET https://er.dakgg.io/api/v1/data/tactical-skills?hl=zh_cn
GET https://er.dakgg.io/api/v1/data/infusions?hl=zh_cn
GET https://er.dakgg.io/api/v1/data/skills?hl=zh_cn
```
