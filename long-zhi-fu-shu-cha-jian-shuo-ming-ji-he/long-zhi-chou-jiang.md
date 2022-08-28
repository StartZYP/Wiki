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

5\. 支持自定义gif动画，抽奖动画，结束动画。

## 2.插件展示

![](<../.gitbook/assets/image (25) (1).png>)

![](<../.gitbook/assets/image (26) (1).png>)

#### ![](<../.gitbook/assets/image (10).png>)

#### ![](<../.gitbook/assets/image (4) (2).png>)

#### ![](<../.gitbook/assets/image (28) (1).png>)

## 3.插件指令

```
dl reload [重载]
dl lottery 奖池名 [抽奖]
dl list [当前加载奖池]
dl cmd [领取保存中的指令]
dl item [领取保存中的物品]
dl gif ur链接 自定义图片名 [获取gif图片tick]
dl冲突请使用mlottery
```

```
Papi变量

%moolottery_amount_奖池名% # 玩家某奖池抽奖次数
%moolottery_cmd% # 玩家待领取的指令奖励数量
%moolottery_items% # 玩家待领取的物品奖励数量

```

## 4.使用说明

### 4.1 CSGO模式配置（模式配置）

```
Functions:
  # 首先界面打开时，会自动触发open方法，然后读取yml的值并保存为界面变量
  # 然后开始异步执行方法，为什么要异步？是因为只有在异步方法里才可以用延时方法
  open: |-
    界面变量.计数 = 0;
    界面变量.循环 = 0;
    界面变量.文本=方法.合并文本('reward',方法.到整数(界面变量.计数),'_texture');
    loop(43,{        
        方法.设置组件值(界面变量.组件1,'texture',方法.取yaml值(方法.到整数(界面变量.计数)));
        方法.添加组件(界面变量.组件1,'');
        界面变量.计数=界面变量.计数+1;
     });
     方法.异步执行方法('move');
  move: |-
    界面变量.计数=0;
    loop(43,{
        界面变量.文本=方法.合并文本('reward',方法.到整数(界面变量.计数),'_texture');
        方法.设置组件值(界面变量.文本,'x', 方法.取组件值(界面变量.文本,'x')-30);
        界面变量.计数=界面变量.计数+1;
    });
    方法.延时(方法.取yaml值(方法.合并文本('timeset',方法.到整数(界面变量.循环))));
    界面变量.循环 = 界面变量.循环+1; 
    (界面变量.循环<=42) ? {方法.异步执行方法('move');}:-1;
    
# 模式 csgo需要amount为1
model: csgo
# amount 在model为free时读取
amount: 2 # 1就是抽一次
# 选取的奖池
lottery: 1
# 此抽奖奖励是否储存在抽奖的背包中
save: false
# time 毫秒单位 1s = 1000ms
# 几个奖励就配置几个
# 0-42为43个奖励
time:
  enable: true
  set:
    0: 100
    1: 100
    2: 100
    3: 100
    4: 100
    5: 100
    6: 100
    7: 100
    8: 100
    9: 100
    10: 100
    11: 100
    12: 100
    13: 100
    14: 100
    15: 100
    16: 100
    17: 150
    18: 150
    19: 150
    20: 150
    21: 150
    22: 150
    23: 150
    24: 150
    25: 150
    26: 150
    27: 150
    28: 150
    29: 150
    30: 150
    31: 200
    32: 200
    33: 200
    34: 200
    35: 200
    36: 200
    37: 200
    38: 200
    39: 200
    40: 250
    41: 300
    42: 350
# 头顶是否弹出奖励图片
emoji:
  enable: false
  x: 0
  y: 1
  z: 0
  w: 1
  h: 1
  time: 10 # 多久后消失 20 = 1s
# 延迟出现 原神不是有个先播放一段gif然后抽奖的 这个就是
delay:
  enable: false
  gif: "" # 必须填写gif图的url链接
  name: "测试" # name是下载gif时的命名同时也是需要在DragonCore/Gui中新建的测试.yml文件的名
# base设置 删除也行 enable写false不启用也行
base:
  enable: false
  # 开启take时 当设置了50抽和100抽保底时 如果50抽前抽到了50抽的保底物品
  # 那么第100抽就会 (100-50)/100的概率
  # 保底机制备注 无论保底前是否抽到保底物品，保底次数到达时都会抽到保底物品
  take: false
  set:
    # 此奖池抽取50次时 会从1.yml中获取指定奖品设置给玩家
    # 需要保证在lottery指定的奖池中有所指定的奖励
    12: "2"
    100: "奖品2"
condition:
  # - vault:100 # 会扣除
  # - point:1 # 会扣除
  # - material:name:10 # 会扣除
  # - papi:%papi%:>=:10 # 不会扣除 仅作为判断条件
# csgo模式下的必须拥有的配置
# csgo.amount为总共抽取多少个奖励 这个时候上面的amount为无效配置
# csgo.rewar为抽取的奖励的序号 我安排1-43中的第41个
csgo:
  amount: 43
  reward: 41
# 龙核界面
背包背景_texture:
  x: "界面变量.x"
  y: "界面变量.y"
  alpha: "方法.取界面存活时间/700"
  width: "518"
  height: "248"
  texture: "UI/背景层最新36.png"
# 奖励
reward0_texture:
  x: "界面变量.x+58.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: "/UI/覆盖.png"
reward1_texture:
  x: "界面变量.x+28.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: ""
reward2_texture:
  x: "界面变量.x+108.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: "/UI/覆盖.png"
reward3_texture:
  x: "界面变量.x+158.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: ""
reward4_texture:
  x: "界面变量.x+208.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: "/UI/覆盖.png"
reward5_texture:
  x: "界面变量.x+258.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: ""
reward6_texture:
  x: "界面变量.x+308.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: "/UI/覆盖.png"
reward7_texture:
  x: "界面变量.x+358.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: ""
reward8_texture:
  x: "界面变量.x+408.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: "/UI/覆盖.png"
reward9_texture:
  x: "界面变量.x+458.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: ""
reward10_texture:
  x: "界面变量.x+508.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: "/UI/覆盖.png"
reward11_texture:
  x: "界面变量.x+558.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: ""
reward12_texture:
  x: "界面变量.x+608.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: "/UI/覆盖.png"
reward13_texture:
  x: "界面变量.x+658.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: ""
reward14_texture:
  x: "界面变量.x+708.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: "/UI/覆盖.png"
reward15_texture:
  x: "界面变量.x+758.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: ""
reward16_texture:
  x: "界面变量.x+808.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: "/UI/覆盖.png"
reward17_texture:
  x: "界面变量.x+858.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: ""
reward18_texture:
  x: "界面变量.x+908.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: "/UI/覆盖.png"
reward19_texture:
  x: "界面变量.x+958.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: ""
reward20_texture:
  x: "界面变量.x+1008.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: "/UI/覆盖.png"
reward21_texture:
  x: "界面变量.x+1058.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: ""
reward22_texture:
  x: "界面变量.x+1108.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: "/UI/覆盖.png"
reward23_texture:
  x: "界面变量.x+1158.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: ""
reward24_texture:
  x: "界面变量.x+1208.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: "/UI/覆盖.png"
reward25_texture:
  x: "界面变量.x+1258.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: ""
reward26_texture:
  x: "界面变量.x+1308.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: "/UI/覆盖.png"
reward27_texture:
  x: "界面变量.x+1358.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: ""
reward28_texture:
  x: "界面变量.x+1408.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: "/UI/覆盖.png"
reward29_texture:
  x: "界面变量.x+1458.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: ""
reward30_texture:
  x: "界面变量.x+1508.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: "/UI/覆盖.png"
reward31_texture:
  x: "界面变量.x+1558.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: ""
reward32_texture:
  x: "界面变量.x+1608.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: "/UI/覆盖.png"
reward33_texture:
  x: "界面变量.x+1658.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: ""
reward34_texture:
  x: "界面变量.x+1708.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: "/UI/覆盖.png"
reward35_texture:
  x: "界面变量.x+1758.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: ""
reward36_texture:
  x: "界面变量.x+1808.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: "/UI/覆盖.png"
reward37_texture:
  x: "界面变量.x+1858.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: ""
reward38_texture:
  x: "界面变量.x+1908.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: "/UI/覆盖.png"
reward39_texture:
  x: "界面变量.x+1958.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: ""
reward40_texture:
  x: "界面变量.x+2008.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: "/UI/覆盖.png"
reward41_texture:
  x: "界面变量.x+2058.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: ""
reward42_texture:
  x: "界面变量.x+2108.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "50"
  height: "50"
  texture: "/UI/覆盖.png"
```

### 4.2 自由模式（模式配置）

```
Functions:
  # 首先界面打开时，会自动触发open方法，然后读取yml的值并保存为界面变量
  # 然后开始异步执行方法，为什么要异步？是因为只有在异步方法里才可以用延时方法
  open: |-
    界面变量.amount=方法.取yaml值('amount')-1;
    界面变量.计数 = 0;
    方法.异步执行方法('xxx') 
  xxx: |-
    界面变量.文本=方法.合并文本('reward',方法.到整数(界面变量.计数),'_texture');
    界面变量.开始时间 = 方法.取当前时间;
    方法.设置组件值(界面变量.文本,'texture',方法.取yaml值(方法.到整数(界面变量.计数)));
    方法.延时(方法.取yaml值(方法.合并文本('timeset',方法.到整数(界面变量.计数))));   
    界面变量.计数=界面变量.计数+1;
    (界面变量.amount>=界面变量.公告数) ? {方法.异步执行方法('xxx');}:-1;
    
    
    
# 模式
model: free
# amount 在model为free时读取
amount: 10 # 1就是抽一次
# 选取的奖池
lottery: 1
# 此抽奖奖励是否储存在抽奖的背包中
save: false
# time 毫秒单位
# 几个奖励就配置几个
time:
  enable: true
  set:
    0: 1000
    1: 1000
    2: 1000
    3: 1000
    4: 1000
    5: 1000
    6: 1000
    7: 1000
    8: 1000
    9: 1000
# base设置 删除也行 enable写false不启用也行
base:
  enable: false
  # 开启take时 当设置了50抽和100抽保底时 如果50抽前抽到了50抽的保底物品
  # 那么第100抽就会 (100-50)/100的概率
  # 保底机制备注 无论保底前是否抽到保底物品，保底次数到达时都会抽到保底物品
  take: false
  set:
    # 此奖池抽取50次时 会从1.yml中获取指定奖品设置给玩家
    # 需要保证在lottery指定的奖池中有所指定的奖励
    12: "2"
    100: "奖品2"
condition:
  # - vault:0 # 会扣除
  # - point:0 # 会扣除
  # - material:name:10 # 会扣除
  # - papi:%papi%:>=:10 # 不会扣除 仅作为判断条件
# 龙核界面
背包背景_texture:
  x: "界面变量.x"
  y: "界面变量.y"
  alpha: "方法.取界面存活时间/700"
  width: "518"
  height: "248"
  texture: "UI/背景层最新36.png"
# 奖励
reward0_texture:
  x: "界面变量.x+28.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "80"
  height: "80"
  texture: "/UI/覆盖.png"
reward1_texture:
  x: "界面变量.x+88.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "80"
  height: "80"
  texture: ""
reward2_texture:
  x: "界面变量.x+118.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "80"
  height: "80"
  texture: ""
reward3_texture:
  x: "界面变量.x+148.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "80"
  height: "80"
  texture: ""
reward4_texture:
  x: "界面变量.x+178.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "80"
  height: "80"
  texture: ""
reward5_texture:
  x: "界面变量.x+208.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "80"
  height: "80"
  texture: ""
reward6_texture:
  x: "界面变量.x+238.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "80"
  height: "80"
  texture: ""
reward7_texture:
  x: "界面变量.x+268.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "80"
  height: "80"
  texture: ""
reward8_texture:
  x: "界面变量.x+298.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "80"
  height: "80"
  texture: ""
reward9_texture:
  x: "界面变量.x+328.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "80"
  height: "80"
  texture: ""
```

### 4.3 原神翻卡模式（模式配置）

```
# 模式
model: card
# amount 在model为free时读取
amount: 2 # 1就是抽一次
# 选取的奖池
lottery: 1
# 此抽奖奖励是否储存在抽奖的背包中
save: false
# time 毫秒单位
# 几个奖励就配置几个
time:
  enable: false
  set:
    0: 1000
    1: 1000
# base设置 删除也行 enable写false不启用也行
base:
  enable: false
  # 开启take时 当设置了50抽和100抽保底时 如果50抽前抽到了50抽的保底物品
  # 那么第100抽就会 (100-50)/100的概率
  # 保底机制备注 无论保底前是否抽到保底物品，保底次数到达时都会抽到保底物品
  take: false
  set:
    # 此奖池抽取50次时 会从1.yml中获取指定奖品设置给玩家
    # 需要保证在lottery指定的奖池中有所指定的奖励
    12: "2"
    100: "奖品2"
condition:
  # - vault:0 # 会扣除
  # - point:0 # 会扣除
  # - material:name:10 # 会扣除
  # - papi:%papi%:>=:10 # 不会扣除 仅作为判断条件
# 龙核界面
背包背景_texture:
  x: "界面变量.x"
  y: "界面变量.y"
  alpha: "方法.取界面存活时间/700"
  width: "518"
  height: "248"
  texture: "UI/背景层最新36.png"
  actions:
    click: 方法.发包('标识名','测试','任意文本',5,'随便多少参数')
# 奖励
reward0_texture:
  x: "界面变量.x+28.5"
  y: "界面变量.y+110"
  alpha: "方法.取界面存活时间/700"
  width: "80"
  height: "80"
  texture: "/UI/覆盖.png"
reward1_texture:
  x: "界面变量.x+28.5"
  y: "界面变量.y+180"
  alpha: "方法.取界面存活时间/700"
  width: "80"
  height: "80"
  texture: ""

 
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
