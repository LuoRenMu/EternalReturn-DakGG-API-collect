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

<details>
<summary>response</summary>

```json
{
  "tiers": [
    {
      "id": 0, // 段位id 数据交互常用该字段 
      "key": "Unrank",  // 段位key(用处未知)
      "name": "段位未鉴定", // 段位
      "imageUrl": "//cdn.dak.gg/assets/er/images/rank/full/0.png", // 图片
      "iconUrl": "//cdn.dak.gg/assets/er/images/rank/round/0.png" // 图片
    }
    // .... 其他数据
  ]
}
```
</details>


## 2. 赛季列表

- 方法：`GET`
- 路径：`/v1/data/seasons`
- 参数：`hl=zh_CN`

示例：

```text
GET https://er.dakgg.io/api/v1/data/seasons?hl=zh_CN
```

<details>
<summary>response</summary>

```json
{
  "seasons": [
    {
      "id": -1,   // 赛季id(在官方的api中常用于该字段)
      "key": "LEGACY", //段位 key (在dakgg中常用于数据交互)
      "name": "Legacy" // 段位名 根据hl参数变动
    },
    {
      "id": 0,
      "key": "NORMAL",
      "name": "一般"
    },
    {
      "id": 1,
      "key": "SEASON_1",
      "name": "EA赛季 S1"
    },
    // ... more
    {
      "id": 41,
      "key": "SEASON_21",
      "name": "赛季 S12",  
      "isCurrent": true  // 当为false时该字段不显示(建议保守编码)
    }
  ]
}
```
</details>

## 3. 当前赛季

- 方法：`GET`
- 路径：`/v0/current-season`
- 参数：`hl=zh_CN`

示例：

```text
GET https://er.dakgg.io/api/v0/current-season?hl=zh_CN
```
<details>
<summary>response</summary>
与上面相同 区别在于key 变为了 type   

```json
{
  "id": 41, 
  "type": "SEASON_21",
  "name": "赛季 S12"
}
```
</details>


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
