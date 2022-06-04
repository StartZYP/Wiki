---
description: 一款按键召唤一个巨大模型在身后的插件。
cover: >-
  ../.gitbook/assets/src=http___i0.hdslb.com_bfs_article_643cb3f8d166763b7f2ea894adeffe7b93301acb.jpg&refer=http___i0.hdslb.jpg
coverY: 0
---

# 龙之武魂绽放

| 适用服务端核心 |  1.12.2全核心 |
| :-----: | :--------: |
|   前置插件  | DragonCore |
|   可选前置  |      无     |

## 1.插件简介

1.支持龙核任意模型绽放

2.绽放能跟随玩家移动而移动自定义位置

3.绽放可增加属性支持sx+ap两种,

4.绽放支持绽放前命令与绽放后命令，并且同时支持绽放CD 和绽放时长计时

5\. 支持武器模式与龙核槽位模式 支持lore与name释放，

6\. 可以兼容配合魂环插件使其魂兽绽放也绽放魂环。

7\. 支持玩家模型替换 双生武魂 玩家与背后的武魂同时绽放

## 2.图片展示

![](<../.gitbook/assets/image (7) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png>)

![](<../.gitbook/assets/image (5) (1) (1) (1) (1) (1) (1) (1) (1).png>)

## 3.插件命令

```
/dragonsoulshow|dss show &7- &c进行命令模式绽放[配置项未启用命令模式则无效]
/dragonsoulshow|dss reload 重载魂兽绽放。
```

## 4.使用说明



![](<../.gitbook/assets/image (6) (1) (1) (1) (1) (1) (1) (1).png>)

1.Model将此文件丢到客户端文件夹内

2.EntityModel将此文件丢到服务端的龙核配置文件夹内

具体详细配置请看配置项

3.默认模式为 手持武器绽放 关键字为模糊匹配 不启用增加属性 关键字带魂兽key

4.所以你的需要在手持物品上lore add 琥珀千鸟魂兽

5.右键就成功绽放拉



## 5.配置文件

```
###################################
##############请填写激活码###########
###################################
Code: ""
###################################
###########魂兽绽放核心设置###########
###################################
# 填写模式 1启用人物渲染  填写2 启用召唤渲染 填3 启用12两个一起
RenderModel: 1
# 填写 1启用Sx 2启用AP 0不启用 注意 槽位模式不要启用这个，否则双倍叠加属性
Use: 0
#  1为槽位模式 2为主手武器模式 如果选槽位模式 Use则写0防止叠加
Model: 2
#是否命令绽放 武器也可以用这个
IsCmdShow: true
# 如果你是槽位模式请精准匹配此项
SlotName: "武魂真身槽位"
# 语言设置
Msg:
 openMsg: "§e§l绽放成功"
 closeMsg: "§e§l回收成功"
 CdMsg: "冷却中"
 CdCloseMsg: "冷却结束"
#当IsLore为False检测name  为true那么检测Lore
IsLore: true
#此处 是模糊匹配与精准匹配 true是模糊 false是精准 颜色符号用§(实在不理解我也没办法)
IsNameContains: true
# 此处为优化设置，必须包含此key才会进行检测武器或槽位 进行判定武魂绽放
KeyWord: "魂兽"
Data:
  Link1:
    KeyName: "琥珀千鸟魂兽"  #模型名称 此处可以搭配魂环使绽放魂兽同时有魂环绽放 如果武器模式的话也是识别此处
    # 是否发光
    IsGlow: true
    Att: # 属性
      - "攻击 +100"
      - "防御 +500"
    ShowCmd:  #绽放执行命令
      - "tell <Player> 狗儿子你魂兽出来了"
    EndCmd:
      - "tell <Player> 释放结束"
    Timer: "15+1*%player_level%" #绽放时间
    CdTimer: "30-1*%player_level%" #冷却时间
    postionx: 0  #绽放魂兽所站的位置
    postiony: 0
    postionz: 0
  Link2:
    KeyName: "幽冥蜘蛛魂兽"  #模型名称
    # 是否发光
    IsGlow: true
    Att: # 属性
      - "攻击 +1100"
      - "防御 +505"
    ShowCmd: #绽放执行命令
      - "tell <Player> 狗儿子你魂兽出来了"
    EndCmd:
      - "tell <Player> 释放结束"
    Timer: "15+1*%player_level%" #绽放时间
    CdTimer: "30-1*%player_level%" #冷却时间
    postionx: 0
    postiony: 0
    postionz: 0

```

## 6.更新日志

版本: 1.4v 时间: 2022年4月14日 15:36:11

1.新增双生武魂 玩家也能替换武魂模型

版本:1.2v 时间: 2022年4月12日 20:19:26

1.新增papi变量计算绽放公式与CD公式&#x20;

2.修复属性不消失问题
