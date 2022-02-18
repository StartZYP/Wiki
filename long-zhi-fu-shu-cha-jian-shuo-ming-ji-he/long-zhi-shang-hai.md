---
description: 支持ap与sx伤害渲染，类似于冒险岛伤害装扮系统。
cover: >-
  ../.gitbook/assets/src=http___i0.hdslb.com_bfs_article_643cb3f8d166763b7f2ea894adeffe7b93301acb.jpg&refer=http___i0.hdslb.jpg
coverY: 0
---

# 龙之伤害

|         |                           |
| :-----: | :-----------------------: |
| 适用服务端核心 |         1.12.2全核心         |
|   前置插件  | DragonCore，PlaceholderAPI |
|   可选前置  |    sx2.0属性，sx3.0属性，Ap属性   |

## 1.插件简介

1.龙之伤害支持ap与sx属性插件，ap支持暴击特殊字体。

&#x20;2.支持设置漂浮动画，只要你能想到的，就能做到。

&#x20;3.支持龙核槽位与GUI模式，可以显示描述。

&#x20;4.高度定制化伤害浮动特性。详情请看下面配置项。

&#x20;5.主要根据权限来判定、攻击是否暴击来显示不同伤害图片。

&#x20;6.新增手持模式支持判定武器lore识别伤害打出颜色，支持默认伤害贴图。

7.支持未命中贴图。

## 2.插件展示

![](<../.gitbook/assets/image (1) (1).png>)

![](<../.gitbook/assets/image (6) (1) (1) (1) (1).png>)

![](<../.gitbook/assets/image (7) (1) (1) (1) (1) (1) (1).png>)

![](<../.gitbook/assets/image (4) (1) (1).png>)

![](<../.gitbook/assets/image (5) (1) (1) (1).png>)

## 3.插件指令

```
/dragonattack | datk gui - 打开龙之伤害Gui模式的界面。
/dragonattack | datk reload 重载配置项。
```

## 4.使用说明

#### papi变量

```
%attack_title% 当前正在使用的攻击数字名称
```

1.拿到插件后先将材质放入龙核材质包

2.再将插件丢进plugin中运行一次，生成默认配置项。

3.仔细阅读配置项中说明，调配并优化你所想要的设置。

4.默认启用配置是Ap属性和Gui模式

5.进游戏直接输入命令/datk gui 就可以打开

6.想自己更好的配置请仔细读配置项

## 5.配置项

```
###################################
##############请填写激活码###########
###################################
Code: ""
###################################
###########攻击系统核心设置###########
###################################
# 填写 1启用SX 2启用AP 0 用原版 只有ap与sx2.0.3有暴击事件
Use: 2
#  1为槽位模式 2为GUI模式会打开GUI 3手持模式 如果选槽位模式 Use则失效
Model: 2
# 是否是用文字 不使用图片 切记如果设置此处那么将无法展示图片伤害 伤害直接文字显示
IsText: false
# 伤害显示范围 例如你在打架周围人距离你多少格能看到这个攻击数字，优化作用非常强
range: 10.0
# 单个伤害的宽度、高度
width: 0.7
height: 1.5
# 未命中时候 图片高度
MissHeight: 3.2
# 未命中时候 图片宽度
MissWidth: 6.5
#是否跟随怪物实体
IsFollowEntity: false
#是否跟随观看玩家视角而旋转
IsFollow: true
# 消失时间秒 只能整数
OutTime: 3
# 数字浮动随机范围 比如第一个攻击60 第二个70 不让他们重叠 需要设置空间半径随机
FloatNumSpace: 1.2
# 是否发光
IsGlow: true
# 普通伤害材质路径
PathNormal: "attack/{textureResName}/normal/{num}.png"
# 暴击伤害材质路径 #{num}为攻击数字动态的
PathCrit: "attack/{textureResName}/crit/{num}.png"
# 权限根节点
#组合攻击图片资源配置 会自动拼接判断权限 如Attack.link1
Permission: "Attack."
# 攻击数字基础相对定位
Position:
  x: 0
  y: -1.0
  z: 0
  rotatex: 0 # 偏转度数
  rotatey: 0
  rotatez: 0
# 语言lang 配置
Msg:
  UpTitle: "§4§l成功配戴上{Attack}~"
  DownTitle: "§b§l成功卸下{Attack}~"
  NoPermission: "§e§l你没有权限配戴这个{Attack}"
###################################
###########槽位模式单独配置###########
###################################
# 槽位注意事项，如果你是槽位模式的话
## true识别lore false识别name 【手持模式也识别此处】
IsLore: true
# 手持模式武器要包含关键字key 必须有这个才会判定为手持伤害皮肤的武器 具体加载什么皮肤请看link1中name字符
HandKey: "伤害"
#自定义槽位名称
DragonSlotName: "额外槽位1"
###################################
##########Gui界面参数配置#############
###################################
Max_size: 4 #每页展示几个
###################################
##########攻击图片资源配置#############
###################################
# 这个是默认伤害数字 如果不需要请置空 打出伤害直接就是这个默认的
defaultattack: link1
Resources:
  #材质路径与权限配置 权限 Attack.link1 由此权限槽位和GUI才能识别和使用 材质路径 这里填充textureResName 请看核心配置中的 PathNormal 与 PathCrit
  link1:
    #攻击文字的名称 槽位识别识别这个，papi变量也显示这个 手持模式关键字也是这个
    name: "蓝普黄暴伤害"
    #暴击后文字尺寸增加值
    CritSizeAdd: 0.5
    #Gui界面显示的伤害皮肤简介
    description: "端午限定，先到先得，高中毕业生及时登录领取"
    #打出伤害时需要播放的动画组设置
    UseanimationGroup: "action1"
    #此处为Gui中展示得贴图图片 槽位模式可以忽略
    Texture: "attack/link1/TextUre.png"
    # 此处要未命中填写的Miss图片
    MissTexture: "attack/link1/TextUre.png"
  link2:
    name: "粉爆炸黑伤"
    CritSizeAdd: 0.5
    description: "端午限定，先到先得，高中毕业生及时登录领取"
    UseanimationGroup: "action1"
    Texture: "attack/link2/TextUre.png"
    MissTexture: "attack/link1/TextUre.png"
  link3:
    name: "花姑娘伤害"
    CritSizeAdd: 0.5
    description: "端午限定，先到先得，高中毕业生及时登录领取"
    UseanimationGroup: "action1"
    Texture: "attack/link3/TextUre.png"
    MissTexture: "attack/link1/TextUre.png"
  link4:
    name: "黑眼熊伤害"
    CritSizeAdd: 0.5
    description: "端午限定，先到先得，高中毕业生及时登录领取"
    UseanimationGroup: "action2"
    Texture: "attack/link4/TextUre.png"
    MissTexture: "attack/link1/TextUre.png"
  link5:
    name: "绿普黄爆"
    CritSizeAdd: 0.5
    description: "端午限定，先到先得，高中毕业生及时登录领取"
    UseanimationGroup: "action2"
    Texture: "attack/link5/TextUre.png"
    MissTexture: "attack/link1/TextUre.png"
###################################
##########攻击动画组配置#############
###################################
animationList:
  action1:
    # 上下动画设置
    TranslateAnimation:
      delay: 0
      distance: 2.1
      duration: 1000
      cycleCount: 1
      fixed: true
    # 缩放动画设置
    ScaleAnimation:
      delay: 0
      cycleCount: 1
      fixed: false
      fromScale: 1.0
      toScale: 3.0
      duration: 1000
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

