---
sidebar_position: 3
---

# 调用随机节点及PAPI变量

## 调用随机节点

其实动作中还可以插入NeigeItems的[即时声明节点](https://neige7.github.io/NeigeItems-Wiki-Docusaurus/%E9%9A%8F%E6%9C%BA%E8%8A%82%E7%82%B9/%E5%8D%B3%E6%97%B6%E5%A3%B0%E6%98%8E%E8%8A%82%E7%82%B9), 你可以将公有参数与节点嵌套搭配使用, 以ALL模式为例:

```yaml
ALL模式怪物示例:
  Type: ZOMBIE
  Health: 1
  Banker:
    test1:
      LootType: ALL
      LootAction:
      - 'tell: 你对怪物造成了 <damage> 点伤害'
      - 'tell: 你的伤害数值减去1, 不保留小数等于 <fastcalc::<damage>-1>'
      - 'tell: 你的伤害数值减去1, 保留2位小数等于 <fastcalc::<damage>-1_2>'
```

## 调用PAPI变量

推荐使用PAPI节点调用PAPI变量, 比如`%player_name%`对应的PAPI节点为`<papi::player_name>`

但如果你不需要将PAPI变量嵌套进其他节点内部, 你也可以直接书写PAPI变量, 示例如下:

```yaml
PAPI调用示例1:
  Type: ZOMBIE
  Health: 1
  Banker:
    test1:
      LootType: ALL
      LootAction:
      - 'tell: 你叫 %player_name% 对吧? 干得漂亮!'
```

但如果你需要将PAPI变量嵌套进其他节点内部, 你就必须使用PAPI节点:

```yaml
PAPI调用示例1:
  Type: ZOMBIE
  Health: 1
  Banker:
    test1:
      LootType: ALL
      LootAction:
      # <papi::player_level> 通过PAPI获取玩家等级
      # <fastcalc::<papi::player_level>+1> 代表玩家等级+1
      - 'tell: 加油, 你马上就要升到 <fastcalc::<papi::player_level>+1> 级了'
```

:::caution

直接将PAPI变量塞入节点内部是无效的!

错误示例:

```yaml
PAPI调用示例1:
  Type: ZOMBIE
  Health: 1
  Banker:
    test1:
      LootType: ALL
      LootAction:
      - 'tell: 加油, 你马上就要升到 <fastcalc::%player_level%+1> 级了'
```

:::
