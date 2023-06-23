---
sidebar_position: 3
---

# MULTIPACK 打包多次抽取模式

## 配置项

| 配置项 | 含义 |
| :----: | :----: |
| LootAction | 被选中的玩家将得到的奖励 |
| Amount | 抽取的玩家数量 |
| GuaranteeAction | 未被选中的玩家将得到的奖励 |

## 模式简介

本模式下, 所有奖励将作为一个整体, 按照玩家造成的伤害权重抽取一定数量的玩家发放奖励

假设共有A、B、C、D四名玩家对目标怪物造成过伤害

玩家A伤害占比10%

玩家B伤害占比20%

玩家C伤害占比30%

玩家D伤害占比40%

以饼状图表示如下:

![伤害占比](_images/伤害占比.png)

假设`Amount`为2, 将饼状图视作标靶, MULTIPACK模式的处理方式可以理解为先向标靶投掷1次飞镖(红叉表示飞镖落点), 被射中的玩家获得奖励

![伤害占比](_images/抽取1.png)

获得奖励的玩家移出待选池

![伤害占比](_images/伤害占比1.png)

向标靶投掷第2次飞镖

![伤害占比](_images/抽取2.png)

如图所示, 可以很清晰地得到结论, 第一次抽取时:

玩家A伤害占比10%, 10%几率获得奖励

玩家B伤害占比20%, 20%几率获得奖励

玩家C伤害占比30%, 30%几率获得奖励

玩家D伤害占比40%, 40%几率获得奖励

之后玩家A中标, 移出待选池, 第二次抽取时:

玩家B伤害占比20%, 2/9几率获得奖励

玩家C伤害占比30%, 3/9几率获得奖励

玩家D伤害占比40%, 4/9几率获得奖励

之后玩家B中标, 即, 玩家A和玩家B将得到`LootAction`配置下的所有奖励

玩家C、D将得到`GuaranteeAction`配置下的所有奖励(未配置`GuaranteeAction`则无奖励)

## 配置示例

动作写法详见[NeigeItems动作](战利品配置/公有参数.md#neigeitems动作)

```yaml
MULTIPACK模式怪物示例:
  Type: ZOMBIE
  Health: 1
  Banker:
    test1:
      LootType: MULTIPACK
      Amount: 2
      LootAction:
      - 'tell: 恭喜中奖! 你的伤害占比为<fastcalc::<damage>/<totalDamage>*100_1>%'
      GuaranteeAction:
      - 'tell: 很遗憾, 你没有获得奖励. 你的伤害占比为<fastcalc::<damage>/<totalDamage>*100_1>%'
```
