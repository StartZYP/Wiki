---
cover: >-
  ../.gitbook/assets/src=http___i0.hdslb.com_bfs_article_643cb3f8d166763b7f2ea894adeffe7b93301acb.jpg&refer=http___i0.hdslb.jpg
coverY: 0
---

# 龙之坐骑

### 1.插件介绍 <a href="#1-cha-jian-jie-shao" id="1-cha-jian-jie-shao"></a>

1.支持槽位模式与Gui模式

2.支持飞行与陆地模式

3.支持双人与多人坐骑

4.支持物品技能槽释放MM技能

5.支持世界限制

### 2.图片展示 <a href="#2-tu-pian-zhan-shi" id="2-tu-pian-zhan-shi"></a>

![](http://p.ipedg.com/wp-content/uploads/2022/02/image.png)![](http://p.ipedg.com/wp-content/uploads/2022/02/HDWA7O7EKU0PZOA-1024x693.png)![](http://p.ipedg.com/wp-content/uploads/2022/02/image-1-1024x625.png)![](http://p.ipedg.com/wp-content/uploads/2022/02/7\_85H09IJCZYIAI15-1024x594.png)![](http://p.ipedg.com/wp-content/uploads/2022/02/YER\_X7ZGKLDXMLB@U-1024x613.png)

### 3.命令全解 <a href="#3-ming-ling-quan-jie" id="3-ming-ling-quan-jie"></a>

```
/dragonride | dgr ride - 识别槽位进行骑乘动作
/dragonride | dgr gui - 打开龙坐骑Gui模式的界面。
/dragonride | dgr reload - 重载配置项。
```

### 3.配置使用说明 <a href="#3-pei-zhi-shi-yong-shuo-ming" id="3-pei-zhi-shi-yong-shuo-ming"></a>

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
    CanFly: false
    FlipRideWorld: false # 是否翻转判断RideWorld 翻转就是不允许
    Description: "§e§l【普通】穴居领主掉落率0.5%，配装技能\n §4魔丝毒液-钢刃之抓-千年之魂"
    Texture: "https://tabclass.coding.net/p/minecraftproject/d/ResouceImg/git/raw/master/DragonRide/img1.png"
    RideWorld: #允许骑乘世界列表
      - "world"
  ride2:
    PapiName: "凤凰"
    NoAttack: true
    MoveSeppd: 0.43
    CanFly: true
    FlipRideWorld: false # 是否翻转判断RideWorld 翻转就是不允许
    Description: "§3【稀有】九天凤凰-副本九天之上掉落率0.005%，配装技能\n §4欲火焚身-杀之爪-泯灭武装"
    Texture: "https://tabclass.coding.net/p/minecraftproject/d/ResouceImg/git/raw/master/DragonRide/img2.png"
    RideWorld: #允许骑乘世界列表
      - "world"
  ride3:
    PapiName: "冰龙"
    NoAttack: true
    MoveSeppd: 0.43
    CanFly: true
    FlipRideWorld: false # 是否翻转判断RideWorld 翻转就是不允许
    Description: "§3【稀有】远古冰龙-寒冰洞穴掉落率0.1%，配装技能\n §4寒冰吐息-杀之爪-玄冰盾"
    Texture: "https://tabclass.coding.net/p/minecraftproject/d/ResouceImg/git/raw/master/DragonRide/img3.png"
    RideWorld: #允许骑乘世界列表
      - "world"
  ride4:
    PapiName: "白虎局镖车"
    NoAttack: true
    MoveSeppd: 0.43
    CanFly: true
    FlipRideWorld: false # 是否翻转判断RideWorld 翻转就是不允许
    Description: "§3【稀有】货运押镖-押镖任务100次奖励，配装技能\n §4货物投递-加速-装载"
    Texture: "https://tabclass.coding.net/p/minecraftproject/d/ResouceImg/git/raw/master/DragonRide/img4.png"
    RideWorld: #允许骑乘世界列表
      - "world"
  ride5:
    PapiName: "飞碟"
    NoAttack: true
    MoveSeppd: 0.43
    CanFly: true
    FlipRideWorld: false # 是否翻转判断RideWorld 翻转就是不允许
    Description: "§3【稀有】超时空穿越飞碟-掉落率10%，配装技能\n §4飞碟导弹-飞碟之刃-伪装"
    Texture: "https://tabclass.coding.net/p/minecraftproject/d/ResouceImg/git/raw/master/DragonRide/img4.png"
    RideWorld: #允许骑乘世界列表
      - "world"
```
