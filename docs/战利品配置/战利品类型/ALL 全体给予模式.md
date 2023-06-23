---
sidebar_position: 1
---

# ALL 全体给予模式

## 配置项

| 配置项 | 含义 |
| :----: | :----: |
| LootAction | 造成过伤害的玩家将得到的奖励 |

## 模式简介

本模式下, 所有对目标MM怪物造成过伤害的玩家, 均可获得奖励

## 配置示例

动作写法详见[NeigeItems动作](战利品配置/公有参数.md#neigeitems动作)

```yaml
ALL模式怪物示例:
  Type: ZOMBIE
  Health: 1
  Banker:
    test1:
      LootType: "All"
      LootAction:
      - 'tell: 你击杀了一只怪物'
```
