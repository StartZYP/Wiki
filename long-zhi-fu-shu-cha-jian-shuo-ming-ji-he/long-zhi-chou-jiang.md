---
description: 七种抽奖模式，大大增加游戏中氪金成分，RPG服务器必备神器之一。
---

# 龙之抽奖

|       |                                           |
| :---: | :---------------------------------------: |
| 服务端核心 |                 1.12.2全核心                 |
|  前置插件 | DragonCore，PlayerPoints Vault PlaceholAPI |
|  可选插件 |                     无                     |

## 1.插件简介

1.支持经济消耗点券 金币 物品消耗。

2.支持物品触发右键即可打开出抽奖界面。（可自定义宝箱类似）

3.仿王者荣耀智能化保底系统，让你的玩家不再担心抽不到。

4.支持本地存储与mysql存储，跨服利器。

## 2.插件展示

![](<../.gitbook/assets/image (25).png>)

![](<../.gitbook/assets/image (26).png>)

#### ![](<../.gitbook/assets/image (10).png>)

#### ![](<../.gitbook/assets/image (4).png>)

#### ![](<../.gitbook/assets/image (28) (1).png>)

## 3.插件指令

```
抽奖[玩家]：/dl open 奖池名
关闭界面[玩家]：/dl close
奖池列表[OP]：/dl lotterylist
重载插件[OP]：/dl reload
```

## 4.使用说明

### 4.1 CSGO模式配置（模式配置）

```
# count为奖励数量显示在屏幕上
# move为移动距离
# move_count为移动次数
# time为移动速度
# reward为奖品 如当设置了三十个奖品 你设置的为5，那么玩家的奖励就是5号奖励
# 设置的奖励和最终的图片显示没有关系，请适当把握距离
# 默认配置下 第10个奖励为中心
public:
  ogg: ""
  ttf: ""
  count: 30
  move: 10
  move_count: 40
  time: 1
  reward: 10
  x: 50
  y: 50
  w: 50
  h: 50
  dis: 50
  icon:
    enable: true
    time: 20
    x: 0
    y: 2.5
    z: 0
    w: 1
    h: 1
```

### 4.2 原神翻卡模式（模式配置）

```
# x y为排列的起始位置 xAdd yAdd为生成奖励时的间隔位置
# row col 为横竖格子 随机生成的奖品总数为 row * col
# image下的w h为按钮大小
public:
  ogg: ""
  ttf: ""
  x: 50
  y: 50
  xAdd: 60
  yAdd: 60
  row: 3
  col: 3
  image:
    w: 35
    h: 35
  icon:
    enable: true
    time: 20
    x: 0
    y: 2.5
    z: 0
    w: 1
    h: 1

```

### 4.3 单抽DNF开罐模式（模式配置）

```
# 非龙核方法配置
public:
  ttf: ""
  ogg: ""
  x: 50
  y: 50
  w: 50
  h: 50
  icon:
    enable: true
    time: 20
    x: 0
    y: 2.5
    z: 0
    w: 1
    h: 1

```

龙核内搭配

```
Functions:
  close: 方法.发包('EasyScreenCloseEvent','component1');
background:
  type: texture
  x: (w-100)/2
  y: (h-100)/2
  height: 100
  width: 100
  texture: lottery/main.png
component1:
  type: reward # 将类型设置为reward texture设为rewardPic为奖励图片
  tip:
  - 奖励3
  x: 25
  y: 30
  width: 50
  height: 50
  texture: rewardPic
  text: ''
  actions: {}
  position: 1_background
reward:
  奖励1:
    code: 1
    pic: "lottery/reward1.png"
    chance: 1
    cmd:
      - "say §d一号奖励"
  奖励2:
    code: 2
    pic: "lottery/reward2.png"
    chance: 10
    cmd:
      - "say §d二号奖励"
  奖励3:
    code: 3
    pic: "lottery/reward3.png"
    chance: 20
    cmd:
      - "say §d三号奖励"

```

### 4.4 无界面模式（模式配置）

```
public:
  icon:
    enable: true
    time: 20
    x: 0
    y: 2.5
    z: 0
    w: 1
    h: 1

```

### 4.5 自由无限轮盘模式（模式配置）

```
# location中为每个奖励的位置
# 如果设置total为10，你需要配置10个位置
location:
  x1: 50
  y1: 100
  x2: 50
  y2: 150
  x3: 50
  y3: 200
  x4: 100
  y4: 100
  x5: 100
  y5: 150
# delay为奖励显示时间间隔
public:
  ogg: ""
  ttf: ""
  delay: 5 # 20 = 1秒
  total: 5
  w: 50
  h: 50

```

### 4.6 量子随机模式（模式配置）

```
# 强烈建议不要把time设置的小于5，因为代码运行还是要时间的，太短的话点击没反应
# 效果为就中间的奖励一直变，点击停止之后停止了而已
public:
  time: 7
  ogg: ""
  ttf: ""
  begin:
    x: 50
    y: 100
    w: 50
    h: 20
    pic: "lottery/抽一次.png"
    pic2: "lottery/抽一次_按下.png"
  stop:
    x: 150
    y: 100
    w: 50
    h: 20
    pic: "lottery/抽一次.png"
    pic2: "lottery/抽一次_按下.png"
  image:
    x: 80
    y: 50
    w: 50
    h: 50
  icon:
    enable: false
    time: 4
    x: 0
    y: 2.5
    z: 0
    w: 1
    h: 1

```

### 4.7 简易红包模式（模式配置）

红包模式建议用以下插件

{% content-ref url="long-zhi-hong-bao.md" %}
[long-zhi-hong-bao.md](long-zhi-hong-bao.md)
{% endcontent-ref %}

```
# 完整配置 只配置这些就行
model: packet 
format: "[点我抽奖]"
# \n为换行符号 %lottery%为红包的名字
# lottery 后的为发送的奖池 抽奖费用由发送者承担
text: 
  - "§d发送者：%player%\n"
  - "§c红包：%lottery%\n"
  - "§e希望你有个好运气\n"
lottery: "Single"

```

### 4.8 奖励配置说明

```
reward为第一层级，其下为奖励的配置
code为序号，从1开始
chance为奖励几率，抽奖算法为  奖励的chance / 所有奖励的chance之和
如 奖励1 chance = 1
     奖励2 chance = 2
     奖励3 chance = 10
则抽到奖励3的概率为 10 / (1 + 2 + 10) = 10 / 13

```

```
reward:
  奖励1:
    code: 1
    pic: "lottery/reward1.png"
    pic2: "lottery/reward1.png"
    chance: 1
    cmd:
      - "say §d一号奖励"
  奖励2:
    code: 2
    pic: "lottery/reward2.png"
    pic2: "lottery/reward2.png"
    chance: 10
    cmd:
      - "say §d二号奖励"
  奖励3:
    code: 3
    pic: "lottery/reward3.png"
    pic2: "lottery/reward3.png"
    chance: 20
    cmd:
      - "say §d三号奖励"

```

### 4.9 保底设置

保底在公共配置中的 base

可以配置保底在第几次时触发

如，base: 5 则当玩家抽取第五次时，触发保底

保底是一直存在的，如玩家抽取了这个奖池99次，第100次会触发保底

### 4.10 变量设置

玩家该奖池的抽奖总次数 %dwo\_奖池名%

### 4.11 右键打开抽奖配置

给任意物品添加lore

如 类型：Single

Single为奖池名，当右键物品时，则会打开奖池进行抽奖

消耗的物品数为奖池配置下 material 的 amount

同时如果点券和金币配置不为0，则会扣除点券和点券

如果material.enable为true，那么会再次扣除一遍物品

### 4.12 动态gif延迟播放配置

插件支持使用gif延迟打开抽奖界面 意为先放一张gif，gif播放结束后抽奖

配置介绍在 配置部分的公共配置的gif下 这里只讲用法

name为 gif 图片名字

pic中必须填为网络url链接，因为需要获取gif图片的播放时间

gif 图片如果未在DragonLottery/image中 则会在通过配置的url下载到服务端



如，某张gif的播放时间为5秒，图片名为 测试.gif

那么在抽奖配置中应有 public下的gif下的name: "测试.gif" 等配置

以及在服务端的DragonLottery/image中应该存在名为测试的 gif 图片

### 4.13 公共配置大全

当前共7种模式

他们有着 3 - 4个部分组成 这里给出所有部分 不是每个模式都有这些东西

```
model: csgo/card/single/none/free/random # 识别模式
# 奖池tip与lotteryList.yml有关
tip:
  - §d我是奖励
  - §d我用于界面集中化部分
  - §d自定义这个显示奖池内容
points: 0 # 需求点券
price: 0 # 需求金币
base: 5 # 保底次数 不用删除此项或者设置为0
material: # 物品消耗
  enable: false # 是否开启
  lore: "测试" # 识别lore
  amount: 1 # 需求数量
main: # 界面背景
  w: 200
  h: 350
  pic: "lottery/main.png"
location: [这个location是自由模式专属的，用于奖励定位]
public: # 公共配置 各模式public部分不同，下面已经给出
  text: # 抽取到的奖励的名称 csgo以及card无此配置
    x: 5
    y: 10
    scale: 1.0
  gif: # 播放一段gif后再打开抽奖界面 pic必须为网络链接
    name: "测试.gif"
    pic: "https://****//.gif"
    w: 100
    h: 100
  ogg: ""
  ttf: ""

```
