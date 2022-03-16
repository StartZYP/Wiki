---
description: 适合类型服务器根据等级奖励来吸引玩家的战令系统。
---

# 龙之战令

|         |                                              |
| :-----: | :------------------------------------------: |
| 适用服务端核心 |                   1.12.2全核心                  |
|   前置插件  | DragonCore,PlaceholderAPI,PlayerPoints,Vault |
|   可选前置  |                       无                      |

## 1.插件简介

1.支持完成日期。

2.支持所需点券开启 金币开启 物品开启再次付费开启高级战令。

3.支持bc跨服数据库全服同步。

4.插件可以自定义界面 可以设置冷却时间的任务。

5.甚至可以配合其他任务插件完成一些特殊操作。

## 2.插件展示

![](<../.gitbook/assets/image (12) (1).png>)

## 3.插件命令

```
/dwo reload [重载]
/dwo receive 战令名 [接受战令]
/dwo open 战令名 [打开战令]
/dwo change 战令名 [更换进行中的战令]
/dwo fix 玩家 战令名 积分数 [增加积分-支持负数]
/dwo orders [玩家战令列表]
/dwo setPay 战令名 [设置某个战令开启付费内容]
/dwo clear [设置玩家没有正在进行的战令]
/dwo ordersServer [服务器战令列表]
/dwo getAll [领取全部可以领取的奖励]
/dwo last [上一页]
/dwo next [下一页]
```

## 4.使用说明

1.贴图丢进客户端，插件丢进plugin，插件配置生成于 plugins / DragonWarOrder 中

2.界面文件Gui 战令文件夹:order 玩家数据:playerData

3.其他yaml config.yml: 填写cdk\[验证码] 以及 测试模式 \[仅管理员可见的输出息]

4.message.yml：插件中大部分与玩家相关的提示信息

5.贴图存放位置 贴图应放在客户端中 .minrcraft / resourcepacks / DragonCore / 自定义名字 也可以使用 url 图床



## 5.配置展示

战令总体Yml配置

```
# 击杀名为 §a怪物名字 的怪物1只可以得到5 point冷却0天
task:
  - "kill:§a怪物名字:1:5:0"
condition:
  date: "2021-12-30"
  # 领取战令条件
  playerpoints: 50 # 点券需求
  vault: 50 # 金币需求
  # 领取战令之后的战令pay内容
  pay: vault:50
  # 需要 §6需要的物品名 的名字的物品 5个
  material: "§6需要的物品名:5"
  # 积分上限 到达积分上限后玩家战令设置为true表示完成 并不再被玩家进行
  maxPoints: 100000
# 如果战令采用翻页模式 每页一排显示几个奖励
rewardCount: 8
# 此部分为变量 用于小框中显示战令任务
# 配置的部分会自动替换
info:
  tasks:
    kill: "击<event><amount>给<points>冷却<day>"
# 变量 显示玩家战令状态
state:
  none: "你还没开通战令"
  free: "初阶战令"
  pay: "高阶战令"
  none_pic: "xxx/xxx.png"
  free_pic: "xxx/xxx.png"
  pay_pic: "xxx/xxx.png"
# 当玩家未接受战令时打开战令界面在等级图片位置处显示的图片
level_null: "xxx/xxx.png"
# 战令等级配置 表示为此战令在100积分时 等级为1 对应图片为xxx/xxx.png
# 此功能为变量 用于龙核显示等级文字以及对应图片
level:
  0: "0:xxx/xxx.png"
  100: "1:xxx/xxx.png"
# free与pay的任务名可以重复
# 
order:
# 当玩家接受战令 玩家会拥有free内容的领取权限
  free:
    任务1:
      # 玩家领取该任务需要什么
      condition:
        point: 100 # 需要的积分
        playerpoints: 0 # 需要的点券
        vault: 0 # 需要的金币
        # 这里和task有关 你的task有kill §a怪物这个任务才行
        # 不然不会记录数据
        kill: "§a怪物:5" 
      # 这里配置的是 小的背景图 以及 小的背景图上的icon
      # icon你可以设置为这个奖励的一个主要物品贴图
      # tips则是这个奖励的描述 如果你不想写..
      # 那就 tips:  即可，嗯 我用#注释了下
      pic:
        background: "" # 玩家战令条件足够时会显示这个(颜色较亮)
        unFinish: "" # 玩家战令条件不足时会显示这个(颜色较暗)
        icon: ""
        tips:
          # - §a 我是描述
      # 不会吧 这是命令 和龙核按键的配置方式一样
      # 带[op]是以OP权限执行 不带就是玩家 带[consle]是控制台
      cmd:
        - "[op] say 1"
  pay:
    任务1:
        #玩家领取该任务需要什么
        condition:
          point: 100 # 需要的积分
          playerpoints: 0
          vault: 0
          kill: "§a怪物:5"
        cmd:
          - "[op] say 1"

```

战令界面配置 战令界面在gui文件夹中 如你配置了一个 示例战令.yml 那么在如果想打开这个战令界面 在gui文件夹则需要一个示例战令.yml 值得一说的是 玩家没接受战令也可以打开界面 不过没法领东西和完成战令 下面是龙核配置（很长很长）

```
Functions:
  open: |-
    方法.更新变量值('dwo_order_page1','dwo_order_page2','dwo_tasks_0','dwo_order_level','dwo_order_points','dwo_order_maxPoints','dwo_order_day','dwo_order_level','dwo_order_levelPic');
    方法.更新变量值('dwo_order_state','dwo_order_state_pic');
############继承区域############
任务显示:
  width: 23
  height: 23
  maxDistanceY: "100"
  minDistanceX: "100"
  limitHeight: "背景_texture.y+130"
  limitWidth: "背景_texture.x+500"
############继承区域############
背景_texture:
  x: "(w-背景_texture.width)/2"
  y: "(h-背景_texture.height)/2"
  width: "389.8"
  height: "290"
  texture: "order/战令-HUD(带LOGO).png"
  actions:
    wheel: "滚动条_texture.distanceY=滚动条_texture.distanceY-滚动条_texture.maxDistanceY*0.05*方法.取滚轮值"
任务背景:
  type: texture
  x: "(w-背景_texture.width)/2+250"
  y: "(h-背景_texture.height)/2+60"
  width: "130"
  height: "70"
  texture: "order/战令-任务视图.png"
滚动条_texture:
  x: "背景_texture.x+374.3"
  y: "背景_texture.y+60.5"
  width: "背景_texture.x*0.02"
  height: "背景_texture.y*0.25"
  extends: '任务显示'
  texture: "order/战令-滑轮.png"
# 滑轮界面中的任务显示配置示例
任务1:
  type: "label"
  x: "背景_texture.x+312.3"
  y: "背景_texture.y+72.5-滚动条_texture.distanceY"
  center: true
  extends: '任务显示'
  texts: "方法.取变量('dwo_tasks_0')"
任务2:
  type: "label"
  x: "背景_texture.x+312.3"
  y: "任务1.y+任务1.height"
  center: true
  extends: '任务显示'
  texts: "方法.取变量('dwo_tasks_1')"
  #dwo_order_levelPic
等级和积分等信息:
  type: label
  x: "(w-背景_texture.width)/2+136"
  y: "(h-背景_texture.height)/2+75.5"
  texts: "方法.合并文本('等级:',方法.取变量('dwo_order_level'),'\n经验：',方法.取变量('dwo_order_points'),'/',方法.取变量('dwo_order_maxPoints'),'\n','剩余:',方法.取变量('dwo_order_day'),'天\n','你的战令等级为:',方法.取变量('dwo_order_level'),'\n','你现在:',方法.取变量('dwo_order_state'))"
等级图片_texture:
  x: "(w-背景_texture.width)/2+8"
  y: "(h-背景_texture.height)/2+50.5"
  width: "32"
  height: "16"
  texture: "方法.取变量('dwo_order_levelPic')"
战令状态图片_texture:
  x: "(w-背景_texture.width)/2+40"
  y: "(h-背景_texture.height)/2+68.5"
  width: "64"
  height: "64"
  texture: "方法.取变量('dwo_order_state_pic')"
初级:
  type: "texture"
  x: "(w-背景_texture.width)/2+6" # 横排间隔42
  y: "(h-背景_texture.height)/2+150"
  width: "40"
  height: "58"
  texture: "order/战令-初级冒险者.png"
高级:
  type: "texture"
  x: "(w-背景_texture.width)/2+6" # 横排间隔42
  y: "(h-背景_texture.height)/2+210"
  width: "40"
  height: "58"
  texture: "order/战令-高级冒险者.png"
上一页:
  type: "texture"
  x: "(w-背景_texture.width)/2+170"
  y: "(h-背景_texture.height)/2+272"
  width: "10"
  height: "15"
  texture: "order/战令-按钮-上一页.png"
  actions:
    click: "方法.聊天('/dwo last')"
下一页:
  type: "texture"
  x: "(w-背景_texture.width)/2+211"
  y: "(h-背景_texture.height)/2+272"
  width: "10"
  height: "15"
  texture: "order/战令-按钮-下一页.png"
  actions:
    click: "方法.聊天('/dwo next')"
当前页数:
  type: label
  x: "(w-背景_texture.width)/2+186"
  y: "(h-背景_texture.height)/2+275.5"
  texts: "方法.合并文本(方法.取变量('dwo_order_page1'),' / ',方法.取变量('dwo_order_page2'))"
任务框:
# 以下三个代表 free部分的第一个奖励的背景图 奖励物品(仅支持一个)小图 领取图
# 带***的部分在玩家打开界面时会自动内置
free0_texture:
  type: "**"
  x: "(w-背景_texture.width)/2+47"
  y: "(h-背景_texture.height)/2+150"
  width: "42.5"
  height: "58"
  texture: "***"
free0_icon:
  type: "**"
  x: "(w-背景_texture.width)/2+52"
  y: "(h-背景_texture.height)/2+160"
  width: "32"
  height: "32"
  texture: "***"
free0_label:
  type: "**"
  x: "(w-背景_texture.width)/2+67"
  y: "(h-背景_texture.height)/2+138"
  texts: "§5§l<code>"
free0_get:
  x: "(w-背景_texture.width)/2+57"
  y: "(h-背景_texture.height)/2+192"
  width: "22"
  height: "11"
  texture: "order/战令-按钮-1.png"
  text: "领取"
  tip:
    - 点我领取奖励
  actions:
    click: "方法.聊天('say /dwo get index_free_0')"
free1_texture:
  type: "**"
  x: "(w-背景_texture.width)/2+89"
  y: "(h-背景_texture.height)/2+150"
  width: "42.5"
  height: "58"
  texture: "***"
free1_icon:
  type: "**"
  x: "(w-背景_texture.width)/2+94"
  y: "(h-背景_texture.height)/2+160"
  width: "32"
  height: "32"
  texture: "***"
free1_label:
  type: "**"
  x: "(w-背景_texture.width)/2+109"
  y: "(h-背景_texture.height)/2+138"
  texts: "§5§l<code>"
free1_get:
  x: "(w-背景_texture.width)/2+99"
  y: "(h-背景_texture.height)/2+192"
  width: "22"
  height: "11"
  texture: "order/战令-按钮-1.png"
  text: "领取"
  tip:
    - 点我领取奖励
  actions:
    click: "方法.聊天('say /dwo get index_free_1')"
free2_texture:
  type: "**"
  x: "(w-背景_texture.width)/2+131"
  y: "(h-背景_texture.height)/2+150"
  width: "42.5"
  height: "58"
  texture: "***"
free2_icon:
  type: "**"
  x: "(w-背景_texture.width)/2+136"
  y: "(h-背景_texture.height)/2+160"
  width: "32"
  height: "32"
  texture: "***"
free2_label:
  type: "**"
  x: "(w-背景_texture.width)/2+151"
  y: "(h-背景_texture.height)/2+138"
  texts: "§5§l<code>"
free2_get:
  x: "(w-背景_texture.width)/2+141"
  y: "(h-背景_texture.height)/2+192"
  width: "22"
  height: "11"
  texture: "order/战令-按钮-1.png"
  text: "领取"
  tip:
    - 点我领取奖励
  actions:
    click: "方法.聊天('/dwo get index_free_2')"
free3_texture:
  type: "**"
  x: "(w-背景_texture.width)/2+173"
  y: "(h-背景_texture.height)/2+150"
  width: "42.5"
  height: "58"
  texture: "***"
free3_icon:
  type: "**"
  x: "(w-背景_texture.width)/2+178"
  y: "(h-背景_texture.height)/2+160"
  width: "32"
  height: "32"
  texture: "***"
free3_label:
  type: "**"
  x: "(w-背景_texture.width)/2+193"
  y: "(h-背景_texture.height)/2+138"
  texts: "§5§l<code>"
free3_get:
  x: "(w-背景_texture.width)/2+183"
  y: "(h-背景_texture.height)/2+192"
  width: "22"
  height: "11"
  texture: "order/战令-按钮-1.png"
  text: "领取"
  tip:
    - 点我领取奖励
  actions:
    click: "方法.聊天('say /dwo get index_free_3')"
free4_texture:
  type: "**"
  x: "(w-背景_texture.width)/2+215"
  y: "(h-背景_texture.height)/2+150"
  width: "42.5"
  height: "58"
  texture: "***"
free4_icon:
  type: "**"
  x: "(w-背景_texture.width)/2+220"
  y: "(h-背景_texture.height)/2+160"
  width: "32"
  height: "32"
  texture: "***"
free4_label:
  type: "**"
  x: "(w-背景_texture.width)/2+235"
  y: "(h-背景_texture.height)/2+138"
  texts: "§5§l<code>"
free4_get:
  x: "(w-背景_texture.width)/2+225"
  y: "(h-背景_texture.height)/2+192"
  width: "22"
  height: "11"
  texture: "order/战令-按钮-1.png"
  text: "领取"
  tip:
    - 点我领取奖励
  actions:
    click: "方法.聊天('say /dwo get index_free_4')"
free5_texture:
  type: "**"
  x: "(w-背景_texture.width)/2+257"
  y: "(h-背景_texture.height)/2+150"
  width: "42.5"
  height: "58"
  texture: "***"
free5_icon:
  type: "**"
  x: "(w-背景_texture.width)/2+262"
  y: "(h-背景_texture.height)/2+160"
  width: "32"
  height: "32"
  texture: "***"
free5_label:
  type: "**"
  x: "(w-背景_texture.width)/2+277"
  y: "(h-背景_texture.height)/2+138"
  texts: "§5§l<code>"
free5_get:
  x: "(w-背景_texture.width)/2+267"
  y: "(h-背景_texture.height)/2+192"
  width: "22"
  height: "11"
  texture: "order/战令-按钮-1.png"
  text: "领取"
  tip:
    - 点我领取奖励
  actions:
    click: "方法.聊天('say /dwo get index_free_5')"
free6_texture:
  type: "**"
  x: "(w-背景_texture.width)/2+299"
  y: "(h-背景_texture.height)/2+150"
  width: "42.5"
  height: "58"
  texture: "***"
free6_icon:
  type: "**"
  x: "(w-背景_texture.width)/2+304"
  y: "(h-背景_texture.height)/2+160"
  width: "32"
  height: "32"
  texture: "***"
free6_label:
  type: "**"
  x: "(w-背景_texture.width)/2+319"
  y: "(h-背景_texture.height)/2+138"
  texts: "§5§l<code>"
free6_get:
  x: "(w-背景_texture.width)/2+309"
  y: "(h-背景_texture.height)/2+192"
  width: "22"
  height: "11"
  texture: "order/战令-按钮-1.png"
  text: "领取"
  tip:
    - 点我领取奖励
  actions:
    click: "方法.聊天('say /dwo get index_free_6')"
free7_texture:
  type: "**"
  x: "(w-背景_texture.width)/2+341"
  y: "(h-背景_texture.height)/2+150"
  width: "42.5"
  height: "58"
  texture: "***"
free7_icon:
  type: "**"
  x: "(w-背景_texture.width)/2+346"
  y: "(h-背景_texture.height)/2+160"
  width: "32"
  height: "32"
  texture: "***"
free7_label:
  type: "**"
  x: "(w-背景_texture.width)/2+361"
  y: "(h-背景_texture.height)/2+138"
  texts: "§5§l<code>"
free7_get:
  x: "(w-背景_texture.width)/2+351"
  y: "(h-背景_texture.height)/2+192"
  width: "22"
  height: "11"
  texture: "order/战令-按钮-1.png"
  text: "领取"
  tip:
    - 点我领取奖励
  actions:
    click: "方法.聊天('say /dwo get index_free_7')"
pay0_texture:
  type: "**"
  x: "(w-背景_texture.width)/2+47"
  y: "(h-背景_texture.height)/2+210"
  width: "42.5"
  height: "58"
  texture: "***"
pay0_icon:
  type: "**"
  x: "(w-背景_texture.width)/2+52"
  y: "(h-背景_texture.height)/2+220"
  width: "32"
  height: "32"
  texture: "***"
pay0_get:
  x: "(w-背景_texture.width)/2+57"
  y: "(h-背景_texture.height)/2+252"
  width: "22"
  height: "11"
  texture: "order/战令-按钮-1.png"
  text: "领取"
  tip:
    - 点我领取奖励
  actions:
    click: "方法.聊天('say /dwo get index_pay_0')"

```

### Task任务配置

这次准备多更新点....和之前一样

```
首先！config.yml下有个test 默认是true的
当你除非我所支持的任务类型时，会发送只有OP可见的信息
这些信息是帮助你获取事件对象的信息 如 杀了 §a牛 
在你配置task的任务时 要填写 - "kill:§a牛:5:10:1"
=================================================
任务类型 识别名字 需求数量 积分 时间限制(0为不设置 单位天)
# 请严格按照如上格式 不然出问题我不管嗷 没法写一堆判断来照顾不读教程的
如 kill:Cow:5:10:1   解读为 击杀牛5只获得积分10冷却1天
当你改为 kill:Cow:5:10:0时 玩家每击杀5只牛都可以得到10积分
==================================================
```

### 战令奖励领取条件配置

为了更加好的去帮助(折磨)玩家

我这次拓展了下玩家在领取战令奖励时需要更多的东西（比如task中的任务积累总数）

```
free:
    任务1:
      condition:
        point: 100 # 需要的积分
        playerpoints: 0 # 需要的点券
        vault: 0 # 需要的金币
        kill: "§a怪物:5" 
```

拿出来一块当例子 前三个有注释

从 kill: "§a怪物:5" 开始

这个表示需要曾经击杀过5个名字为 §a怪物 的怪物

我拿出来讲的原因是

你需要在task下配置 - "kill:§a怪物:多少只:多少积分:冷却几天"

如上这种的累计杀多少给积分的任务，不然玩家的§a怪物击杀数永远是0

\# 另外 需要注意的是，当一个task任务处于冷却时，并不会被计入数据中

## 插件PAPI变量

```
dwo_index # 当前页一排最多有几个战令奖励(用于生成序号)
dwo_index_free # 当前页free有几个
dwo_index_pay # 当前页pay有几个
dwo_order_sum # 玩家战令总数(包括已经完成的和过期的)
dwo_order_points # 玩家当前打开/进行的战令积分
dwo_order_maxPoints # 战令最大积分
dwo_order_level # 打开的战令等级
dwo_order_levelPic # 打开的战令等级对应的图片
dwo_order_page1 # 当前查看的页数是战令的第几页
dwo_order_page2 # 当前查看的战令的最大页数
dwo_order_state # 玩家当前战令状态
dwo_order_stata_pic # 玩家当前战令状态对应图片
dwo_order_day # 当前战令截止天数
dwo_order_date # 当前战令截止日期 得到的格式 "2021-012-31"
dwo_tasks_0 # 从0开始 当前玩家打开战令的task配置下的第一个任务 1 2 3
```

## Task任务类型

```
kill # 击杀 数值击杀+1
damage # 伤害 数值为伤害数值
destroy # 破坏方块 数值破坏+1
place # 放置方块 数值放置+1
craft # 合成物品 数值为合成出的数量 如两个木板合成的木棍为4 则+4
collect # 捡起物品 数值为捡起的物品数量 （itemstack好像有个堆?)
```

## 奖励条件类型

```
task 支持的这里全部支持
# 下面是另外的
freeAmount # 完成的免费任务数量
payAmount # 完成的付费任务数量
allAmount # 完成的总共的任务数量
# 如果你同时配置了 freeAmount: 5和allAmount: 10 但玩家free没5个 会失败
```
