---
description: 适合配合充值点券等一些插件进行兑换礼包操作，RPG服必备神器。
---

# 龙之累计充值

|         |            |
| :-----: | :--------: |
| 适用服务端核心 |  1.12.2全核心 |
|   前置插件  | DragonCore |
|   可选插件  |      无     |

## 1.插件介绍

1.支持自定义界面，纯龙核界面

2.支持命令发放奖励

3.支持配合充值插件进行针对玩家进行充值

4.支持本地存储与Mysql存储支持跨服

## 2.插件展示

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>



<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

## 3.插件命令

```
&7=============== &b龙之累计充值奖励 &7===============
&f/DragonTotalAward|dtta set [玩家名] [点数] &7- &c为某一个玩家设置累计充值点数
&f/DragonTotalAward|dtta take [玩家名] [点数] &7- &c为某一个玩家扣除累计充值点数
&f/DragonTotalAward|dtta add [玩家名] [点数] &7- &c为某一个玩家增加累计充值点数
&f/DragonTotalAward|dtta look [玩家名] &7- &c查看玩家累计充值积分数据
&f/DragonTotalAward|dtta reload &7- &c重载配置项
&f/DragonTotalAward|dtta open [玩家名]&7- &c打开累计充值领取界面
&7=============== &b玩家命令 &7===============
&f/TotalAward|tta open &7- &c打开累计充值领取界面
&7=============== &b龙之累计充值奖励 &7================
```

## 4.使用说明

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

DragonCore 中是贴图文件 把这个放进客户端

另外一个是插件放进plugin启动 等待文件夹生成

DragonTotalAward 进这个文件夹

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

填写激活码后等待验证通过

选择存储模式

配置下方

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

此处配置100 为所需积分点

Name和Lore为礼包界面中的物品 可以配合龙核Icon进行配置礼包贴图等

Lore中支持两种变量 %Status% 已领取 未领取 未达标等三种状态

Cmds 为领取礼包后执行的命令，要给予玩家一些奖励等。

## 5.配置文件
