---
description: 龙之药水是RPG服必备插件,独立按键,兼容所有属性的恢复系统,并且支持二次开发。
---

# 龙之药水



|         |                                           |
| :-----: | :---------------------------------------: |
| 适用服务端核心 |                 1.12.2全核心                 |
|   前置插件  |                 DragonCore                |
|   可选前置  | SX-Attribute,AttributePlus,ItemLoreOrigin |

## 1.插件介绍

1.插件支持多槽位单槽位按键使用药水.

2.支持多种模式药水1 自用普通药水 2 普通持续性药水 3 自他用普通药水 4 自他用持续性药水 5 范围普通药水 6 范围持续性图腾药水

3.支持冷却CD以及Js脚本判断,高度自由。

4.支持血量公式蓝量公式,同时支持药水使用时的音乐播放。

5.支持全属性架构,支持Api扩展

6.自定义消耗，药水使用前后命令执行

## 2.插件展示

\[此插件本身就是一个药水具体要看配置项]

\[使用由配置者决定效果]

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

## 3.插件命令

```

&7=============== &e龙之药水 &7===============
/DragonPotions|dpot reload &7- &c重载药水插件
=============== &e龙之药水 &7================
=============== &e龙之药水-物品库 &7================
/DragonPotions|dpot list &7- &c查看物品库(鼠标点击获取 ,按住Shift获取一组)
/DragonPotions|dpot AddItem [物品别名] &7- &c手持物品添加进物品库（删除请再ItemData中删除）
/DragonPotions|dpot Get [物品别名] &7- &c获取物品库的物品
/DragonPotions|dpot Get [物品别名] [玩家名] &7- &c获取物品库的物品给某一个人
=============== &e龙之药水-物品库 &7================

```

## 4.使用说明

1.将插件材质包放进客户端。

2.插件丢进plugin中,重启服务端生成DragonPotions文件

3.在文件中config.yml里填写你的code.

4.了解大致目录

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

5\. Potions目录只要是药水存储目录 Scirpt主要是使用药水判断逻辑js脚本

6.ItemData.yml主要是药水物品存放目录,支持废弃老物品，也就是让老物品失效。

7.Lang.yml文件主要是语言配置文件

8.Config.yml主要是配置项文件

9.创建药水等同于在Potions里面创建一个yml文件

10.例子中的药水有六大种类 请复制对应药水进行修改来操作。

11.药水可以通过MM或者物品库来取

12.请仔细阅读药水中的配置 来决策。
