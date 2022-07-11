---
description: 押镖适用于各种服务器，运送货物运送物资，增加游戏时长与游戏乐趣的小方案。
cover: >-
  ../.gitbook/assets/src=http___i0.hdslb.com_bfs_article_643cb3f8d166763b7f2ea894adeffe7b93301acb.jpg&refer=http___i0.hdslb.jpg
coverY: 0
---

# 龙之押镖

## 1.插件介绍 <a href="#1.-cha-jian-jie-shao" id="1.-cha-jian-jie-shao"></a>

|         |                |
| :-----: | :------------: |
| 适用服务端核心 |    1.12.2全核心   |
|   前置插件  |   DragonCore   |
|   可选前置  | PlaceholderAPI |

## 1.插件简介



3.矿车支持多种属性 血量，速度，骑乘，被攻击停留时间，是否无敌，押镖人之间范围，是否能使用提速道具与减速道具。

4.每种矿车自定义模型，自定义范围贴图与镖车头顶贴图与贴图动画

5.支持多种事件命令，如 劫镖后劫镖人命令事件，押镖成功命令事件，押镖失败押镖人命令事件，押镖超时命令事件。

6.可使用bq任务进行配合实现押镖任务，跑环任务等一系列趣味操作。

7.兼容一切属性插件，无论怎么攻击伤害都是1，均衡操作。

## 2.插件展示

![](<../.gitbook/assets/image (13) (1) (1) (1) (1).png>)

![](<../.gitbook/assets/image (10) (1) (1) (1).png>)

![](<../.gitbook/assets/image (9) (1) (1).png>)

## 3.插件命令

```
/dragoncarry|dc add [自定义路径名] &7- &c添加一个路径的点位,没有则创建一个
/dragoncarry|dc remove [自定义路径名] &7- &c移除上一个坐标。
/dragoncarry|dc run [自定义路径名] [镖车名]|青龙局镖车 [玩家]|skyman [运行超时秒]|300 &7- &c运行一个镖车并绑定一个玩家
/dragoncarry|dc run [自定义路径名] [镖车名]|青龙局镖车 [玩家]|skyman [运行超时秒]|300 [启用龙导航]|true &7- &c运行一个镖车并绑定一个玩家
```

## 4.使用说明

![](<../.gitbook/assets/image (8) (1) (1) (1) (1).png>)

1.DrageonCore 模型放到客户端龙核目录。

2.EntityModel.yml复制到龙核服务端内。

3.启动服务器填写插件中授权码。

4.查看配置项配置好你的飙车和触发数据绑定

5.进游戏面朝行驶方向输入 /dragoncarry|dc add test1 (此时就创建了一个test1路径点)

6.面朝第二个拐弯方向输入/dragoncarry|dc add test1 继续添加锚点

7.这些锚点都在插件point文件夹内，需要删除直接右键删除即可。

8./dragoncarry|dc run \[自定义路径名] \[镖车名]|青龙局镖车 \[玩家]|skyman \[运行超时秒]|300 &7- \&c运行一个镖车并绑定一个玩家

9.玩家打自己飙车为加血1，

## 5.配置项

```
#####################
#######激活码道具#####
#####################
Code: "" #验证
#####################
#######核心配置项#####
#####################
MaxSpeed: 0.5 #镖车最大移动速度
RangeTime: 4 # 4秒检测一次提醒范围超出
ShowRange: 10 #倒计时可视范围
Lang:
  RideMsg: "&e&l[龙之押镖]§b§l成功骑乘上镖车"
  CarryDie: "&e&l[龙之押镖]§b§l押镖车车死亡（劫运）"
  CarryTimeout: "&e&l[龙之押镖]§b§l押镖车运送已超时。"
  SafeTime: "&e&l[龙之押镖]§b§l当前为安全时间押镖，镖车无敌。"
  NoItemRide: "&e&l[龙之押镖]§b§l想骑乘镖车必须空手。"
  Attack: "&e&l[龙之押镖]§b§l你的镖车正在遭受攻击，停止向前。"
#####################
#######加速道具#######
#####################
ItemConfig:
  IsLore: true #true识别Lore False识别Name
  Name: "速卡" #匹配的文字 模糊匹配 颜色用§ 比如加速卡  这个会自动匹配上
  StarChar: "速度:" # 此处只识别lore中搜寻 比如速度:-0.05点 对着镖车右键使用 会窃取-0.05 作为镖车增量
  EndChar: "点"
############# ########
#######镖车全局配置#####
#####################
otherattackvalue: 1 #其他玩家打镖车伤害
myattackvalue: 3 #自己打镖车回复值

############# ########
#######镖车配置#######
#####################
CarryEntity:
  Ride1:
    Name: 青龙局镖车 #此处填写镖车渲染名称
    SafeTime: "18:00~19:00" #安全时间 在这个时间段镖车直接无敌 无法攻击镖车
    #范围环 玩家出了这个环押镖就失败了 此处配合押镖车的Range
    CarryRangetexture:
      TexturePath: "CarryModel/Hoop.png"
      BindAnimation: "action1" #动画组 此处跟动画组联动
      x: 0
      y: 0.1
      z: 0
      rotatex: 90 # 偏转度数
      rotatey: 0
      rotatez: 0
    #头顶部Texture镖车显示的图片
    TimeHeadtexture:
      TexturePath: "[text]%Player%的镖车倒计时%Time%秒"
      IsFollow: false #顶部是否跟随视角
      width: 0.1
      height: 0.2
      BindAnimation: "" #动画组 此处跟动画组联动 不写就是不加动画
      x: 0.05  # 时间文字显示 为了保证摆放在你想要的位置
      y: 3.0 #这个会加上实体自身身高
      z: -0.1
      rotatex: 0 # 偏转度数
      rotatey: 0
      rotatez: 0
    CarryHeadtexture:
      TexturePath: "CarryModel/title.png"
      IsFollow: false #顶部是否跟随视角
      width: 2.8
      height: 0.8
      BindAnimation: "" #动画组 此处跟动画组联动 不写就是不加动画
      x: 0  # 时间文字显示 为了保证摆放在你想要的位置
      y: 3.0 #这个会加上实体自身身高
      z: 0
      rotatex: 0 # 偏转度数
      rotatey: 0
      rotatez: 0
    IsNoAttack: true # 货物是否无敌
    IsUseCard: true #是否可以使用加速减速卡
    Heath: 500.0 #血量 无敌则血量无效
    Speed: 0.11 # 镖车基础速度
    Range: 8.0 # 距离货物最远距离 超出则押镖失败 不要设置太大，小心区块未加载
    IsRide: true # 是否能骑乘上货物
    StopTime: 5 # 押镖车被攻击时需要停留时间
    StartDoCmd:
      - "tell %Player% 押运开始，快跟上你的车车吧"
      - "tell %Player% 押运开始，请跟随押运车前往咸阳城"
    RobberyDoCmd:
      - "tell %Player% 你成功劫下了,朱雀镖车"
      - "say %Player% 奖励您6担粮食，请快去【天人城】王铺处兑换"
    TimeOutDoCmd:
      - "tell %Player% 你押运超时押运失败了"
      - "say %Player% 距离镖车"
    Success:
      - "say %Player% 成功了哦"
      - "say %Player% 成功了哦"
    Fail:
      - "say %Player% 失败了哦"
      - "say %Player% 失败了哦"
  Ride2:
    Name: 朱雀局镖车 #此处填写镖车渲染名称
    SafeTime: "18:00~19:00"
    #范围环 玩家出了这个环押镖就失败了 此处配合押镖车的Range
    CarryRangetexture:
      TexturePath: "CarryModel/Hoop.png"
      BindAnimation: "action1" #动画组 此处跟动画组联动
      x: 0
      y: 0.1
      z: 0
      rotatex: 90 # 偏转度数
      rotatey: 0
      rotatez: 0
    #头顶部Texture镖车显示的图片
    TimeHeadtexture:
      TexturePath: "[text]%Player%的镖车倒计时%Time%秒"
      IsFollow: false #顶部是否跟随视角
      width: 0.1
      height: 0.2
      BindAnimation: "" #动画组 此处跟动画组联动 不写就是不加动画
      x: 0.05  # 时间文字显示 为了保证摆放在你想要的位置
      y: 3.0 #这个会加上实体自身身高
      z: -0.1
      rotatex: 0 # 偏转度数
      rotatey: 0
      rotatez: 0
    CarryHeadtexture:
      TexturePath: "CarryModel/title.png"
      IsFollow: false #顶部是否跟随视角
      width: 2.8
      height: 0.8
      BindAnimation: "" #动画组 此处跟动画组联动 不写就是不加动画
      x: 0  # 时间文字显示 为了保证摆放在你想要的位置
      y: 3.0 #这个会加上实体自身身高
      z: 0
      rotatex: 0 # 偏转度数
      rotatey: 0
      rotatez: 0
    IsNoAttack: true # 货物是否无敌
    IsUseCard: true #是否可以使用加速减速卡
    Heath: 1000.0 #血量 无敌则血量无效
    Speed: 0.15 # 镖车基础速度
    Range: 10.0 # 距离货物最远距离 超出则押镖失败
    IsRide: true # 是否能骑乘上货物
    StopTime: 5 # 押镖车被攻击时需要停留时间
    StartDoCmd:
      - "tell %Player% 押运开始，快跟上你的车车吧"
      - "tell %Player% 押运开始，请跟随押运车前往咸阳城"
    RobberyDoCmd:
      - "tell %Player% 你成功劫下了,朱雀镖车"
      - "say %Player% 奖励您6担粮食，请快去【天人城】王铺处兑换"
    TimeOutDoCmd:
      - "tell %Player% 你押运超时押运失败了"
      - "say %Player% 距离镖车"
    Success:
      - "say %Player% 恭喜您已成功将镖车押镖到朱雀镖局"
      - "say %Player% §e§l[押镖系统]§b已将20张银票送至您的口袋，请立即去【镖局张琳】兑换"
    Fail:
      - "say %Player% 失败了哦"
      - "say %Player% 失败了哦"
  Ride3:
    Name: 玄武局镖车 #此处填写镖车渲染名称
    SafeTime: "18:00~19:00"
    #范围环 玩家出了这个环押镖就失败了 此处配合押镖车的Range
    CarryRangetexture:
      TexturePath: "CarryModel/Hoop.png"
      BindAnimation: "action1" #动画组 此处跟动画组联动
      x: 0
      y: 0.1
      z: 0
      rotatex: 90 # 偏转度数
      rotatey: 0
      rotatez: 0
    #头顶部Texture镖车显示的图片
    TimeHeadtexture:
      TexturePath: "[text]%Player%的镖车倒计时%Time%秒"
      IsFollow: false #顶部是否跟随视角
      width: 0.1
      height: 0.2
      BindAnimation: "" #动画组 此处跟动画组联动 不写就是不加动画
      x: 0.05  # 时间文字显示 为了保证摆放在你想要的位置
      y: 3.0 #这个会加上实体自身身高
      z: -0.1
      rotatex: 0 # 偏转度数
      rotatey: 0
      rotatez: 0
    CarryHeadtexture:
      TexturePath: "CarryModel/title.png"
      IsFollow: false #顶部是否跟随视角
      width: 2.8
      height: 0.8
      BindAnimation: "" #动画组 此处跟动画组联动 不写就是不加动画
      x: 0  # 时间文字显示 为了保证摆放在你想要的位置
      y: 3.0 #这个会加上实体自身身高
      z: 0
      rotatex: 0 # 偏转度数
      rotatey: 0
      rotatez: 0
    IsNoAttack: true # 货物是否无敌
    IsUseCard: true #是否可以使用加速减速卡
    Heath: 1500.0 #血量 无敌则血量无效
    Speed: 0.18 # 镖车基础速度
    Range: 10.0 # 距离货物最远距离 超出则押镖失败
    IsRide: true # 是否能骑乘上货物
    StopTime: 5 # 押镖车被攻击时需要停留时间
    StartDoCmd:
      - "tell %Player% 押运开始，快跟上你的车车吧"
      - "tell %Player% 押运开始，请跟随押运车前往咸阳城"
    RobberyDoCmd:
      - "tell %Player% 你成功劫下了,朱雀镖车"
      - "say %Player% 奖励您6担粮食，请快去【天人城】王铺处兑换"
    TimeOutDoCmd:
      - "tell %Player% 你押运超时押运失败了"
      - "say %Player% 距离镖车"
    Success:
      - "say %Player% 成功了哦"
      - "say %Player% 成功了哦"
    Fail:
      - "say %Player% 失败了哦"
      - "say %Player% 失败了哦"
  Ride4:
    Name: 白虎局镖车 #此处填写镖车渲染名称
    SafeTime: "18:00~19:00"
    #范围环 玩家出了这个环押镖就失败了 此处配合押镖车的Range
    CarryRangetexture:
      TexturePath: "CarryModel/Hoop.png"
      BindAnimation: "action1" #动画组 此处跟动画组联动
      x: 0
      y: 0.1
      z: 0
      rotatex: 90 # 偏转度数
      rotatey: 0
      rotatez: 0
    #头顶部Texture镖车显示的图片
    TimeHeadtexture:
      TexturePath: "[text]%Player%的镖车倒计时%Time%秒"
      IsFollow: false #顶部是否跟随视角
      width: 0.1
      height: 0.2
      BindAnimation: "" #动画组 此处跟动画组联动 不写就是不加动画
      x: 0.05  # 时间文字显示 为了保证摆放在你想要的位置
      y: 3.0 #这个会加上实体自身身高
      z: -0.1
      rotatex: 0 # 偏转度数
      rotatey: 0
      rotatez: 0
    CarryHeadtexture:
      TexturePath: "CarryModel/title.png"
      IsFollow: false #顶部是否跟随视角
      width: 2.8
      height: 0.8
      BindAnimation: "" #动画组 此处跟动画组联动 不写就是不加动画
      x: 0  # 时间文字显示 为了保证摆放在你想要的位置
      y: 3.0 #这个会加上实体自身身高
      z: 0
      rotatex: 0 # 偏转度数
      rotatey: 0
      rotatez: 0
    IsNoAttack: true # 货物是否无敌
    IsUseCard: true #是否可以使用加速减速卡
    Heath: 2000.0 #血量 无敌则血量无效
    Speed: 0.25 # 镖车基础速度
    Range: 12.0 # 距离货物最远距离 超出则押镖失败 也是渲染圈圈的大小
    IsRide: true # 是否能骑乘上货物
    StopTime: 5 # 押镖车被攻击时需要停留时间
    StartDoCmd:
      - "tell %Player% 押运开始，快跟上你的车车吧"
      - "tell %Player% 押运开始，请跟随押运车前往咸阳城"
    RobberyDoCmd:
      - "tell %Player% 你成功劫下了,朱雀镖车"
      - "say %Player% 奖励您6担粮食，请快去【天人城】王铺处兑换"
    TimeOutDoCmd:
      - "tell %Player% 你押运超时押运失败了"
      - "say %Player% 距离镖车"
    # 超出范围执行命令
    Success:
      - "say %Player% 成功了哦"
      - "say %Player% 成功了哦"
    Fail:
      - "say %Player% 失败了哦"
      - "say %Player% 失败了哦"

###################################
##########押镖车贴图动画组配置#########
###################################
animationList:
  action1:
    # 旋转动画设置
    RotateAnimation:
      delay: 0
      angle: 360.0
      duration: 6000
      cycleCount: 1
      fixed: true
      resetTime: 1
  action2:
    # 旋转动画设置
    RotateAnimation:
      delay: 0
      angle: 360.0
      duration: 6000
      cycleCount: 1
      fixed: true
      resetTime: 1
    # 上下动画设置
    TranslateAnimation:
      delay: 0
      distance: 1.1
      duration: 3000
      cycleCount: 1
      fixed: true
    # 缩放动画设置
    ScaleAnimation:
      delay: 0
      cycleCount: 1
      fixed: false
      fromScale: 3.0
      toScale: 1.0
      duration: 3000
```
