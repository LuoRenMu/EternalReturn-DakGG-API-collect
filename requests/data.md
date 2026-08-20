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

<details>
<summary>response</summary>

```json
{
  "characters": [
    {
      "id": 1, // 角色 id (数据传输常用于改key)
      "key": "Jackie", // 角色 key
      "name": "杰琪",
      "imageName": "Jackie_S000",
      "imageUrl": "//cdn.dak.gg/assets/er/game-assets/12.2.0/CharProfile_Jackie_S000.png",
      "communityImageUrl": "//cdn.dak.gg/assets/er/game-assets/12.2.0/CharCommunity_Jackie_S000.png",
      "maxHp": 940, //初始角色数值
      "maxVp": 0,
      "attackPower": 36,
      "defense": 50,
      "hpRegen": 1.28,
      "vpRegen": 0,
      "attackSpeed": 0.1,
      "moveSpeed": 3.5,
      "levelUpStat": {
        "maxHp": 95,
        "maxVp": 0,
        "attackPower": 4.7,
        "defense": 3,
        "hpRegen": 0.077,
        "vpRegen": 0
      },
      "weaponTypes": [ //武器列表 
        {
          "id": 15,
          "key": "OneHandSword"
        }
        // ... 其他可用武器
      ],
      "masteries": ["OneHandSword", "TwoHandSword", "Axe", "DualSword"], 
      "masteryStats": [
        {
          "type": "Axe",
          "options": [
            {
              "key": "AttackSpeedRatio",
              "value": 0.03
            }
          ]
        }
      ],
      "skins": [
        {
          "id": 1001000,
          "name": "杰琪",
          "grade": 1,
          "imageName": "Jackie_S000",
          "imageUrl": "//cdn.dak.gg/assets/er/game-assets/12.2.0/CharResult_Jackie_S000.png"
        }
      ],
      "charArcheTypes": ["Warrior", "None"] // 角色定位
    }
    // ... 其他角色
  ]
}
```
</details>

## 5. 物品列表

- 方法：`GET`
- 路径：`/v1/data/items`
- 参数：`hl=zh-cn`

示例：

```text
GET https://er.dakgg.io/api/v1/data/items?hl=zh-cn
```

<details>
<summary>response</summary>

```json
{
  "items": [
    {
      "id": 101101, // 物品 id
      "name": "剪刀",
      "tooltip": "一般 / 材料\n\n发现场所 : 码头(18)...",
      "imageUrl": "https://cdn.dak.gg/assets/er/game-assets/12.2.0/ItemIcon_101101.png",
      "type": "Misc", // 物品大类
      "miscItemType": "Material", // 材料类物品才会出现
      "grade": "Common",
      "spawnAreas": [10, 60, 70, 120, 140, 190, 200]
    },
    {
      "id": 101201,
      "name": "军刀",
      "tooltip": "高级 / 短剑\n\n攻击力 +10...",
      "imageUrl": "https://cdn.dak.gg/assets/er/game-assets/12.2.0/ItemIcon_101201.png",
      "type": "Weapon",
      "weaponType": "OneHandSword", // 武器类物品才会出现
      "grade": "Uncommon",
      "makeMaterial1": 101104,
      "makeMaterial2": 108101,
      "makeMaterials": [101104, 108101]
    }
    // ... 其他物品；不同物品类型包含的字段可能不同
  ]
}
```
</details>

## 6. 熟练度 / 武器

- 方法：`GET`
- 路径：`/v1/data/masteries`
- 参数：`hl=zh_cn`

示例：

```text
GET https://er.dakgg.io/api/v1/data/masteries?hl=zh_cn
```

<details>
<summary>response</summary>

```json
{
  "masteries": [
    {
      "id": 1, // 熟练度或武器类型 id
      "key": "Glove",
      "name": "拳套",
      "iconUrl": "https://cdn.dak.gg/assets/er/game-assets/12.2.0/Ico_Ability_Glove.png"
    }
    // ... 其他熟练度
  ]
}
```
</details>

## 7. 潜能技能

- 方法：`GET`
- 路径：`/v1/data/trait-skills`
- 参数：`hl=zh_cn`

<details>
<summary>response</summary>

```json
{
  "traitSkillGroups": [
    {
      "key": "Havoc",
      "name": "破坏型",
      "tooltip": "强化攻击 & 持续性伤害",
      "imageUrl": "https://cdn.dak.gg/assets/er/game-assets/12.2.0/TraitSkillIcon_Havoc02.png"
    }
    // ... 其他潜能分组
  ],
  "traitSkills": [
    {
      "id": 7000201, // 潜能技能 id
      "name": "绝对武力",
      "tooltip": "使用普攻或独立技能命中同一实验体3次时，将额外造成真实伤害并降低目标的防御力。",
      "group": "Havoc", // 对应 traitSkillGroups.key
      "type": "Core",
      "imageUrl": "https://cdn.dak.gg/assets/er/game-assets/12.2.0/TraitSkillIcon_7000200.png",
      "active": true,
      "traitSortOrder": 101
    }
    // ... 其他潜能技能
  ]
}
```
</details>

## 8. 战术技能

- 方法：`GET`
- 路径：`/v1/data/tactical-skills`
- 参数：`hl=zh_cn`

<details>
<summary>response</summary>

```json
{
  "tacticalSkills": [
    {
      "id": 30, // 战术技能 id
      "name": "闪灵",
      "tooltip": "使用后向指定位置移动一段距离。...",
      "imageUrl": "https://cdn.dak.gg/assets/er/game-assets/12.2.0/VSkillIcon_4000000.png"
    }
    // ... 其他战术技能
  ]
}
```
</details>

## 9. 区域列表

- 方法：`GET`
- 路径：`/v1/data/areas`
- 参数：`hl=zh_cn`

示例：

```text
GET https://er.dakgg.io/api/v1/data/areas?hl=zh_cn
```

说明：

- 返回地图区域的基础资料
- 区域 id 可与物品响应中的 `spawnAreas` 对照使用

## 10. 灌注

- 方法：`GET`
- 路径：`/v1/data/infusions`
- 参数：`hl=zh_cn`

<details>
<summary>response</summary>

```json
{
  "infusions": [
    {
      "id": 1, // 灌注条目 id
      "productType": "Trait", // 关联数据类型
      "productId": 7910101 // 关联数据 id
    }
    // ... 其他灌注条目
  ]
}
```
</details>

## 11. 角色技能

- 方法：`GET`
- 路径：`/v1/data/skills`
- 参数：`hl=zh_cn`

<details>
<summary>response</summary>

```json
{
  "skills": [
    {
      "id": 1001100, // 技能 id
      "name": "鲜血盛宴",
      "tooltip": "无消耗\n\n杰琪使用普攻或技能造成伤害时...",
      "characterId": 1, // 对应 characters.id
      "maxLevel": 2,
      "slot": "T", // 技能槽位，如 T、Q、W、E、R
      "imageUrl": "https://cdn.dak.gg/assets/er/game-assets/12.2.0/SkillIcon_1001300.png",
      "videoUrl": "https://er-data.dakgg.net/skill/jackie_t.mp4"
    }
    // ... 其他角色技能
  ]
}
```
</details>

## 批量示例

```text
GET https://er.dakgg.io/api/v1/data/trait-skills?hl=zh_cn
GET https://er.dakgg.io/api/v1/data/tactical-skills?hl=zh_cn
GET https://er.dakgg.io/api/v1/data/areas?hl=zh_cn
GET https://er.dakgg.io/api/v1/data/infusions?hl=zh_cn
GET https://er.dakgg.io/api/v1/data/skills?hl=zh_cn
```
