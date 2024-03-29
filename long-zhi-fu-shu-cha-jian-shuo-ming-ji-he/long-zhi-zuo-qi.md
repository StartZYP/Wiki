---
description: 游戏中常见的坐骑系统，RPG游戏必备模块之一。支持海陆空三种飞行状态。
cover: >-
  ../.gitbook/assets/src=http___i0.hdslb.com_bfs_article_643cb3f8d166763b7f2ea894adeffe7b93301acb.jpg&refer=http___i0.hdslb.jpg
coverY: 0
---

# 龙之坐骑

|         |                        |
| :-----: | :--------------------: |
| 适用服务端核心 |        1.12.2全核心       |
|   前置插件  | DragonCore，ProtocolLib |
|   可选插件  |            无           |

## 1.插件介绍 <a href="#1-cha-jian-jie-shao" id="1-cha-jian-jie-shao"></a>

1.支持槽位模式与Gui模式。

2.支持飞行，陆地，水面，三款坐骑。

3.支持双人与单人坐骑。

4.支持物品技能槽释放MM技能。

5.支持世界限制，与wg领地限制。

## 2.使用说明 <a href="#2-tu-pian-zhan-shi" id="2-tu-pian-zhan-shi"></a>

![](<../.gitbook/assets/image (7) (1) (1) (1) (1) (1).png>)

![](<../.gitbook/assets/image (2) (1) (1).png>)

## 3.插件命令 <a href="#3-ming-ling-quan-jie" id="3-ming-ling-quan-jie"></a>

```
/dragonride | dgr ride - 识别槽位进行骑乘动作
/dragonride | dgr gui - 打开龙坐骑Gui模式的界面。
/dragonride | dgr reload - 重载配置项。
```

## 4.使用说明 <a href="#3-pei-zhi-shi-yong-shuo-ming" id="3-pei-zhi-shi-yong-shuo-ming"></a>

![](<../.gitbook/assets/image (12) (1) (1) (1).png>)

1.拿到插件后材质丢进客户端，EntityModel复制到服务端龙核插件对应文件，插件丢进Plugin，重启服务器。

2.填写激活码，后进游戏输入/dgr gui 打开坐骑界面

3.坐骑列表是读取你的权限所生成的，OP默认有所有权限。<-这是GUI模式

4.坐骑槽位模式是先判断 IsLore 是否读取lore&#x20;

5.再读取槽位的 PapiName: "蜘蛛" #槽位中Lore中请包含这个，颜色用§ 龙核渲染实体也配这个

6.最后槽位模式 输入/dgr ride 进行骑乘 可以设置成按键

7.切换模式的时候注意，一定要重启服务器。reload无效。

## 5.配置文件

```
#=====================================================================
##==========================激活码设置 必填=============================
#=====================================================================
Code: ""
#=====================================================================
##==========================启用模式相关配置=============================
#=====================================================================
# 模式1 槽位模式 槽位模式需要设置龙核槽位 并且槽位物品lore需要有PapiName 命令/ride ride
# 模式2 GUI模式 此模式为权限模式 给权限即可给他所有坐骑，权限节点 RideEntity.ride1 这个是可以自定义的
# 这个鸟版本暂时没有Gui懒得做了我日 年后吧卷不动了
model: 2
#=====================================================================
##==========================槽位模式配置=============================
#=====================================================================
#龙核槽位模式配置
Slotname: "坐骑槽位"
# 槽位注意事项，如果你是槽位模式的话
## true识别lore false识别name
IsLore: true
#=====================================================================
##==========================Gui模式配置=============================
#=====================================================================
Max_size: 4


Msg:
  RideMsg: "§e§l已经坐上飞机"
  WorldNoRide: "这个世界不能坐坐骑"
  RideDown: "坐骑下车"
  RideIn: "你正在坐着"
  NeedRide: "兄弟要配戴坐骑哦"

########################################
###########坐骑关联详细设置################
########################################
RideEntity:
  ride1: # 在Gui模式下会判断是否拥有这个权限 RideEntity.ride1
    PapiName: "蜘蛛" #槽位中Lore中请包含这个，颜色用§ 龙核渲染实体也配这个
    NoAttack: true #是否无敌模式
    MoveSeppd: 0.43
    Model: 1 # 1.陆地行走(码) 2.水上行驶(船) 3.天空飞翔(龙)
    Description: "§e§l【普通】穴居领主掉落率0.5%，配装技能\n §4魔丝毒液-钢刃之抓-千年之魂"
    Texture: "https://tabclass.coding.net/p/minecraftproject/d/ResouceImg/git/raw/master/DragonRide/img1.png"
    FlipRideWorld: false # 是否翻转判断RideWorld 翻转就是不允许
    RideWorld: #允许骑乘世界列表
      - "world"
  ride2:
    PapiName: "凤凰"
    NoAttack: true
    MoveSeppd: 0.43
    Model: 3
    Description: "§3【稀有】九天凤凰-副本九天之上掉落率0.005%，配装技能\n §4欲火焚身-杀之爪-泯灭武装"
    Texture: "https://tabclass.coding.net/p/minecraftproject/d/ResouceImg/git/raw/master/DragonRide/img2.png"
    FlipRideWorld: false
    RideWorld:
      - "world"
  ride3:
    PapiName: "冰龙"
    NoAttack: true
    MoveSeppd: 0.43
    Model: 3
    Description: "§3【稀有】远古冰龙-寒冰洞穴掉落率0.1%，配装技能\n §4寒冰吐息-杀之爪-玄冰盾"
    Texture: "https://tabclass.coding.net/p/minecraftproject/d/ResouceImg/git/raw/master/DragonRide/img3.png"
    FlipRideWorld: false
    RideWorld:
      - "world"
  ride4:
    PapiName: "军舰"
    NoAttack: true
    MoveSeppd: 0.43
    Model: 2
    Description: "§3【稀有】货运押镖-押镖任务100次奖励，配装技能\n §4货物投递-加速-装载"
    Texture: "https://tabclass.coding.net/p/minecraftproject/d/ResouceImg/git/raw/master/DragonRide/img4.png"
    FlipRideWorld: false
    RideWorld:
      - "world"
  ride5:
    PapiName: "飞碟"
    NoAttack: true
    MoveSeppd: 0.43
    Model: 3
    Description: "§3【稀有】超时空穿越飞碟-掉落率10%，配装技能\n §4飞碟导弹-飞碟之刃-伪装"
    Texture: "https://tabclass.coding.net/p/minecraftproject/d/ResouceImg/git/raw/master/DragonRide/img4.png"
    FlipRideWorld: false
    RideWorld:
      - "world"
```
