---
description: 头顶称号系统，支持槽位与Gui双模式配置，ap与sx支持 高度解耦满足你的所有要求。
cover: >-
  ../.gitbook/assets/src=http___i0.hdslb.com_bfs_article_643cb3f8d166763b7f2ea894adeffe7b93301acb.jpg&refer=http___i0.hdslb.jpg
coverY: 0
---

# 龙之称号

|         |                           |
| :-----: | :-----------------------: |
| 适用服务端核心 |         1.12.2全核心         |
|   前置插件  | DragonCore，PlaceholderAPI |
|   可选前置  |    sx2.0属性，sx3.0属性，Ap属性   |

## 1.插件简介

1.支持GUI模式以权限作为存储单位，超轻量级.支持群组跨服数据同步。

2.支持龙核槽位和原版槽位支持默认称号，同时支持权限识别与槽位模式。

3.支持ap所有版本和sx2.0和sx3.0。

4.支持papi变量显示当前配戴称号。

5.支持lore与name识别切换，同时支持称号跟随视野与不跟随两种。

6.支持每个称号高度与大小自由切换。

## 2.插件展示

![](<../.gitbook/assets/image (2) (1) (1) (1).png>)

![](<../.gitbook/assets/image (8) (1) (1) (1) (1) (1).png>)

![](<../.gitbook/assets/image (7) (1) (1) (1) (1) (1).png>)

![](<../.gitbook/assets/image (9) (1) (1).png>)

## 3.插件命令

```
/DragonChengHao | dch show &7- &c打开称号界面(必须界面模式才行)
/DragonChengHao | dch reload &7- &c重载插件
```

## 4.使用说明

#### 称号papi变量 当前配戴称号:%chenghao\_title%

![](<../.gitbook/assets/image (6) (1) (1).png>)

1.拿到插件后选择你的属性版本和类型丢进服务端plugin，等待生成填写激活码 目录DragonChengHao

2.将贴图放进本地客户端目录对应文件，也可以放远程图床

3.查看配置选择你需要的模式

4.默认槽位模式 并不启用属性 无缓存，需要修改请在如下配置项进行修改。

## 5.配置展示

```
###################################
##############请填写激活码###########
###################################
Code: ""
###################################
###########称号系统核心设置###########
###################################
defalutpapi: "§e§l无称号"
Use: 0 # 填写 1启用Sx 2启用AP 0不启用 注意 槽位模式不要启用这个，否则双倍叠加属性
#  1为槽位模式 2为GUI模式会打开GUI 如果选槽位模式 Use则失效
Model: 1
# IsCache Gui模式才开启次选项，意思就是你上下线都会保存你的配戴称号
OpenCache: false
# 是否是用文字 不使用图片 切记如果设置此处那么将无法展示图片 使用的是name字段作为称号显示在头上
IsText: false
#是否跟随观看玩家视角而旋转
IsFollow: true
# 是否发光
IsGlow: true
# 语言lang 配置
Msg:
  UpTitle: "§4§l成功配戴上称号~"
  DownTitle: "§b§l成功卸下称号~"
  NoPermission: "§e§l你没有权限配戴这个称号"
###################################
###########槽位模式单独配置###########
###################################
# 槽位注意事项，如果你是槽位模式的话
# 称号图片属性配置这块 不需要关注属性,描述,
#
## true识别lore false识别name
IsLore: true
#自定义槽位名称
DragonSlotName: "额外槽位1"
###################################
###########称号图片属性配置###########
###################################
Designation:
  Name_1: # 自定义
    texture: "chenghao/chenghao_1.png"    #支持URL贴图
    width: 1.5    #配戴称号宽高
    height: 0.5
    # 称号显示高度
    showheight: 2.3
    name: "名望大夫"
    permission: "hyy.name1"
    description: "端午限定，先到先得，高中毕业生及时登录领取"
    attribute:
      - "a+1"
      - "s+1"
      - "d+1"
      - "f+1"
  Name_2:
    texture: "chenghao/chenghao_2.png"
    width: 1.5    #配戴称号宽高
    height: 0.5
    # 称号显示高度
    showheight: 2.3
    name: "权倾大夫"
    permission: "hyy.name2"
    attribute:
      - "血量+2"
    description: "限定哦_2"

  Name_3:
    texture: "chenghao/chenghao_3.png"
    width: 1.5    #配戴称号宽高
    height: 0.5
    # 称号显示高度
    showheight: 2.3
    name: "怀才之卿"
    permission: "hyy.name3"
    attribute:
      - "血量+3"
    description: "限定哦_3"

  Name_4:
    texture: "chenghao/chenghao_4.png"
    width: 1.5    #配戴称号宽高
    height: 0.5
    # 称号显示高度
    showheight: 2.3
    name: "理政之卿"
    permission: "hyy.name4"
    attribute:
      - "血量+4"
    description: "限定哦_4"

  Name_5:
    texture: "chenghao/chenghao_5.png"
    width: 1.5    #配戴称号宽高
    height: 0.5
    # 称号显示高度
    showheight: 2.3
    name: "立德之卿"
    permission: "hyy.name5"
    attribute:
      - "血量+5"
    description: "限定哦_5"

  Name_6:
    texture: "chenghao/chenghao_6.png"
    width: 1.5    #配戴称号宽高
    height: 0.5
    # 称号显示高度
    showheight: 2.3
    name: "富豪贵势"
    permission: "hyy.name6"
    attribute:
      - "血量+6"
    description: "限定哦_6"

  Name_7:
    texture: "chenghao/chenghao_7.png"
    width: 1.5    #配戴称号宽高
    height: 0.5
    # 称号显示高度
    showheight: 2.3
    name: "威望贵势"
    permission: "hyy.name7"
    attribute:
      - "血量+7"
    description: "限定哦_7"

  Name_8:
    texture: "chenghao/chenghao_8.png"
    width: 1.5    #配戴称号宽高
    height: 0.5
    # 称号显示高度
    showheight: 2.3
    name: "金强世族"
    permission: "hyy.name8"
    attribute:
      - "血量+8"
    description: "限定哦_8"

  Name_9:
    texture: "chenghao/chenghao_9.png"
    width: 1.5    #配戴称号宽高
    height: 0.5
    # 称号显示高度
    showheight: 2.3
    name: "鼎贵世族"
    permission: "hyy.name9"
    attribute:
      - "血量+9"
    description: "限定哦_9"

  Name_10:
    texture: "chenghao/chenghao_10.png"
    width: 1.5    #配戴称号宽高
    height: 0.5
    # 称号显示高度
    showheight: 2.3
    name: "光耀华族"
    permission: "hyy.name10"
    attribute:
      - "血量+10"
    description: "限定哦_10"

  Name_11:
    texture: "chenghao/chenghao_11.png"
    width: 1.5    #配戴称号宽高
    height: 0.5
    # 称号显示高度
    showheight: 2.3
    name: "光兴华勋"
    permission: "hyy.name11"
    attribute:
      - "血量+11"
    description: "限定哦_11"

  Name_12:
    texture: "chenghao/chenghao_12.png"
    width: 1.5    #配戴称号宽高
    height: 0.5
    # 称号显示高度
    showheight: 2.3
    name: "光禄华勋"
    permission: "hyy.name12"
    attribute:
      - "血量+12"
    description: "限定哦_12"

  Name_13:
    texture: "chenghao/chenghao_13.png"
    width: 1.5    #配戴称号宽高
    height: 0.5
    # 称号显示高度
    showheight: 2.3
    name: "天勤华勋"
    permission: "hyy.name13"
    attribute:
      - "血量+13"
    description: "限定哦_13"

  Name_14:
    texture: "chenghao/chenghao_14.png"
    width: 1.5    #配戴称号宽高
    height: 0.5
    # 称号显示高度
    showheight: 2.3
    name: "天骄华勋"
    permission: "hyy.name14"
    attribute:
      - "血量+14"
    description: "限定哦_14"

```
