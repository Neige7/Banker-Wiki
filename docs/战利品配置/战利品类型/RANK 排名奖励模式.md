---
sidebar_position: 5
---

# RANK 排名奖励模式

## 配置项

| 配置项 | 含义 |
| :----: | :----: |
| LootAction | 排名奖励配置 |
| GuaranteeAction | 掉出排名的玩家得到的奖励 |

## 模式简介

RANK模式下, LootAction中的一条条配置将被视为一条条排名奖励

奖励将根据玩家伤害排名对玩家发放, 示例配置如下:

```yaml
RANK模式怪物示例:
  Type: ZOMBIE
  Health: 1
  Banker:
    test1:
      LootType: RANK
      LootAction:
      - 'tell: 你的伤害占比排名第一'
      - 'tell: 你的伤害占比排名第二'
      - 'tell: 你的伤害占比排名第三'
      GuaranteeAction:
      - 'tell: 再接再厉'
```

假设共有A、B、C、D四名玩家对目标怪物造成过伤害

玩家A伤害占比10%, 排名第四

玩家B伤害占比20%, 排名第三

玩家C伤害占比30%, 排名第二

玩家D伤害占比40%, 排名第一

那么根据伤害排名:

玩家D排名第一, 将收到消息: `你的伤害占比排名第一`

玩家C排名第二, 将收到消息: `你的伤害占比排名第二`

玩家B排名第三, 将收到消息: `你的伤害占比排名第三`

玩家A掉出了前三名, 将得到`GuaranteeAction`配置下的所有奖励(未配置`GuaranteeAction`则无奖励)

示例配置中, 玩家A将收到消息: `再接再厉`

## 私有参数

在公有参数的基础上, SEPARATE模式还提供以下私有参数:

| 参数名 | 含义 |
| :----: | :----: |
| rank | 玩家伤害排名 |
| lootAmount | 奖励总数 |

## 配置示例

```yaml
RANK模式怪物示例:
  Type: ZOMBIE
  Health: 1
  Banker:
    test1:
      LootType: RANK
      LootAction:
      - 'tell: 你的伤害占比排名第一'
      - 'tell: 你的伤害占比排名第二'
      - 'tell: 你的伤害占比排名第三'
      GuaranteeAction:
      - 'tell: 再接再厉'
```
