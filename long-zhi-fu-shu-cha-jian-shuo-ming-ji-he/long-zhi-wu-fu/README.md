---
cover: >-
  ../../.gitbook/assets/src=http___i0.hdslb.com_bfs_article_643cb3f8d166763b7f2ea894adeffe7b93301acb.jpg&refer=http___i0.hdslb.jpg
coverY: 0
description: 迎新春集五福活动插件，也可以作为卡牌集合插件，玩法可以自创。
---

# 龙之五福

|         |                        |
| :-----: | :--------------------: |
| 适用服务端核心 |        1.12.2全核心       |
|   前置插件  | DragonCore，ProtocolLib |
|   可选前置  |            无           |

## 1.插件简介

1.支持任意五种物品合成，完全自定义。

2.合成总量有计数。

3.实时刷新排行榜系统，观察集福总数。

4.支持Bc跨服数据共享数据。

5.支持合成后任意命令执行，配合达到你的目的。

## 2.插件展示

![](<../../.gitbook/assets/image (8) (1) (1) (1).png>)

![](<../../.gitbook/assets/image (10) (1).png>)

## 3.插件命令

```
/DragonFiveFu |dff set [福标识符] 例:fu1 手持物品设置福.(设置五次,五个不同标识符)不要带颜色符号
/DragonFiveFu |dff get [福标识符] 获取设置的五福。
/DragonFiveFu |dff get <Player> [福标识符] 让某个玩家获得五福获取设置的五福。
/DragonFiveFu |dff gui 打开五福Gui拖拽五福。
```

## 4.使用说明

![](<../../.gitbook/assets/image (2).png>)

1.拿到插件丢进plugin目录中运行，生成配置项，填写激活码。看到验证成功后。

2.itemlcon粘贴进龙核内。DragonCore放进客户端内。

3.进服首先设置五福，手持五个物品。

4.手持福1 输入命令/DragonFiveFu set fu1

5.手持福2 输入命令/DragonFiveFu set fu1 (以此类推设置五个)

6.获取五福输入命令/DragonFiveFu get fu1

7.你设置的福可以搭配mm 使得年兽掉落五福或者更多玩法。

8.设置好五福后打开五福界面 /DragonFiveFu |dff gui

9.如果想删除配置的五福的话，清理FiveFu.dat文件即可。



## 5.配置项

```
# 激活码
Code: ""

#跨服请将此文件夹填写到同一个路径，我会把玩家数据写进此路径
SavePath: ""
# 到达固定次数将获得的奖励
CmdDo:
  5:
    - "bc <Player> 成功合成了<Num>次,送他五百块"
    - "eco give <Player> 500"
  10:
    - "bc <Player> 成功合成了<Num>次,送他一千块"
    - "eco give <Player> 1000"


everynumcmd:
  - "tell <Player>你成功集齐了五福合成了,这是第几<Num>合成"
  - "eco give <Player> 10"


```

