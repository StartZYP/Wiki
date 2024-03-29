---
description: 类似于王者荣耀的抽奖机制，支持保底，支持连抽与单抽，氪金服必备。
---

# 龙之抽奖百宝箱

|      |                |
| :--: | :------------: |
| 适用核心 |    1.12.2全核心   |
| 前置插件 |   DragonCore   |
| 可选前置 | PlaceholderAPI |

## 1.插件简介 <a href="#2.-cha-jian-zhan-shi" id="2.-cha-jian-zhan-shi"></a>

1.支持插件自带物品库，支持MM物品导入，支持命令模式

2.支持单抽与十连抽，支持抽奖几率分配与界面显示。

3.支持本地存储与数据库存储两种模式，单服与跨服均可。

4.抽奖支持抽中物品与命令两种样式抽奖。

5.支持设置多种抽奖界面，纯箱子渲染，简单方便。

6.支持设置保底与百宝箱兑换。

## 2.插件展示

<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (2) (2).png" alt=""><figcaption></figcaption></figure>

## 3.插件命令

```
管理员命令
/DragonTreasureBox|dtb list &7- &c查看物品库(鼠标点击获取 ,按住Shift获取一组)
/DragonTreasureBox|dtb AddItem [物品别名] &7- &c手持物品添加进物品库（删除请再ItemData中删除）
/DragonTreasureBox|dtb clear [玩家名] [宝箱名] &7- &c清理某一玩家宝箱数据
/DragonTreasureBox|dtb look [玩家名] [宝箱名] &7- &c查看玩家某一宝箱数据
/DragonTreasureBox|dtb give [玩家名] [宝箱名] [钥匙数量] &7- &c给予玩家某一宝箱钥匙
/DragonTreasureBox|dtb open [玩家名] [宝箱名] &7- &c让某一玩家打开某一宝箱
/DragonTreasureBox|dtb reload &7- &c重载插件数据。
玩家命令
/DragonTreasureBox|dtb open &7- &c打开百宝箱抽奖界面
```

## 4.使用说明

1.拿到插件贴图丢进客户端

2.将插件丢进plugin后在config.yaml填激活码。

3.激活成功后进服。输入/dtb help 查看帮助

4.再输入/dtb open 打开抽奖界面

5.config.yml中可选mysql与文件存储默认文件存储

6.在游戏中输入/dtb list 可以查看并且拿去物品

7.手持物品输入/dtb add xxx 可以加入物品库配置到宝箱的配置界面

8\. 不用物品库可以用mm物品 将config.yaml 中OnlyMMItemModel 改成true就为mm物品了

9.抽奖支持 命令形式 可以查看宝箱中的介绍



## 5.插件配置

### 1.全局Config.yml配置说明

```
# 验证填写
Code: ""
# 存储模式 1 Mysql模式 2文件存储模式
StorageModel: 2

# 仅用MM物品模式 true为启用 false 为不启用用自带龙之物品库
OnlyMMItemModel: false

# 数据库模式不必多谈
MySQL:
  host: 'localhost'
  port: 3306
  username: 'root'
  password: 'root'
  database: 'level'

CmdGroups:
  克鲁斯魔王宝箱抽中命令A组:
    - "say %player_name% 已通过命令调用某插件命令"
    - "say %player_name% 成功给你发放了ap成长属性点"
    - "say %player_name% 你抽中了这个命令组克鲁斯魔王宝箱抽中命令A组"
  克鲁斯魔王宝箱命令B组:
    - "say %player_name% 已通过命令调用某插件命令"
    - "say %player_name% 成功给你发放了ap成长属性点"
    - "say %player_name% 你抽中了这个命令组克鲁斯魔王宝箱抽中命令B组"
  开心快乐宝箱A组:
    - "say %player_name% 抽中给你送回家"
    - "say %player_name% 这个命令上支持papi变量多多少少"
  事例抽奖组B组:
    - "say %player_name% 多多少少抽中B组了"
    - "say %player_name% 抽中了之后也没啥这是命令组"
```

### 2.宝箱配置说明

```
# 虚拟钥匙索取 1个
KeyValue: 1

# 宝库名称
BoxName: "克鲁斯魔王宝箱"

# 宝箱简介
BoxInfo: "克鲁斯魔王的巢穴 副本: 克鲁斯全身上下 掉落BOSS: 克鲁斯魔王  掉落钥匙物品: 克鲁斯钥匙X10"

# 单抽免费刷新时间 换算单位秒 -1为不开启
refresh: 86400

# 进度条阀值，满了必出一个 ProgressFullItem 物品
ThresholdNum: 100

# 以下支持两种 1.抽奖获取物品  2.抽奖获取命令
# 物品则配置项为 - "[MM或者物品仓库物品名称]-个数-[堆叠数量]-占比-[占据整个抽奖的几率比例]"
# 命令则配置项为 - "[展示在GUI中的物品写MM或者物品仓库物品名称]-命令-[这里写config.yml中CmdGroups的分组名称]-占比-[占据整个抽奖的几率比例]"

TenLottyItems:
  - "孤竹种子-个数-3-占比-0.5"
  - "蝎紫红藤树种子-个数-3-占比-0.03"
  - "白悬莲种子-个数-3-占比-0.3"
  - "岣嵝树种子-个数-3-占比-0.1"

# 进度条满后赠送礼物
ProgressFullItem:
  - "孤竹种子-个数-3-占比-0.5"
  - "蝎紫红藤树种子-个数-3-占比-0.03"
  - "白悬莲种子-个数-3-占比-0.3"
  - "岣嵝树种子-个数-3-占比-0.1"

# 奖品预览列表 可以多写支持分页
LottyItems:
  - "克鲁斯魔王之剑-个数-3-占比-0.5"
  - "克鲁斯魔王之铲-个数-3-占比-0.03"
  - "克鲁斯魔王之稿-个数-3-占比-0.3"
  - "克鲁斯魔王之斧-个数-3-占比-0.1"
  - "克鲁斯魔王之头盔-个数-3-占比-0.5"
  - "克鲁斯魔王之衣-个数-3-占比-0.03"
  - "克鲁斯魔王之裤-个数-3-占比-0.3"
  - "克鲁斯魔王之鞋-个数-3-占比-0.1"
  - "克鲁斯魔王之手部血液-个数-3-占比-0.1"
  - "克鲁斯魔王之胸部血液-个数-3-占比-0.5"
  - "克鲁斯魔王之头部血液-个数-3-占比-0.03"
  - "克鲁斯魔王之脚部血液-个数-3-占比-0.3"
  - "克鲁斯魔王之肉-个数-3-占比-0.5"
  - "克鲁斯魔王之血肉-个数-3-占比-0.03"
  - "克鲁斯魔王遗书-个数-3-占比-0.3"
  - "克鲁斯魔王泪水-个数-3-占比-0.1"
  - "克鲁斯魔王骨头-个数-3-占比-0.1"
  - "克鲁斯魔王之皮肤-个数-3-占比-0.1"
  - "克鲁斯魔王头发-个数-3-占比-0.1"
  - "克鲁斯魔王墓碑-个数-3-占比-0.1"


# 抽奖次数兑换列表 物品对应物品库或者MM 在config.yml启用
ExchangeList:
  3:
    Info:
      - "初级植物"
      - "累计抽奖达到3次可兑换"
      - "只云逊兑换一次"
      - "礼包有一个屁"
    Items:
      - "克鲁斯魔王墓碑|5"
    Cmds:
      - "say %player_name% 送出一个大狗是"
      - "say %player_name% 送出一个大狗是"
      - "say %player_name% 送出一个大狗是"
  5:
    Info:
      - "初级植物"
      - "累计抽奖达到5次可兑换"
      - "只云逊兑换一次"
      - "礼包有一个屁"
    Items:
      - "克鲁斯魔王泪水|1"
      - "克鲁斯魔王之衣|1"
    Cmds:
      - "say %player_name% 送出一个大狗是"
      - "say %player_name% 送出一个大狗是"
      - "say %player_name% 送出一个大狗是"
  7:
    Info:
      - "初级植物"
      - "累计抽奖达到7次可兑换"
      - "只云逊兑换一次"
      - "礼包有一个屁"
    Items:
      - "克鲁斯魔王泪水|1"
      - "克鲁斯魔王之衣|3"
      - "克鲁斯魔王之剑|3"
    Cmds:
      - "say %player_name% 送出一个大狗是"
      - "say %player_name% 送出一个大狗是"
      - "say %player_name% 送出一个大狗是"
  10:
    Info:
      - "初级植物"
      - "累计抽奖达到10次可兑换"
      - "只云逊兑换一次"
      - "礼包有一个屁"
    Items:
      - "克鲁斯魔王之头盔|1"
      - "克鲁斯魔王之剑|3"
    Cmds:
      - "say %player_name% 送出一个大狗是"
      - "say %player_name% 送出一个大狗是"
      - "say %player_name% 送出一个大狗是"

  20:
    Info:
      - "初级植物"
      - "累计抽奖达到20次可兑换"
      - "只云逊兑换一次"
      - "礼包有一个屁"
    Items:
      - "克鲁斯魔王之铲|1"
      - "克鲁斯魔王之剑|3"
    Cmds:
      - "say %player_name% 送出一个大狗是"
      - "say %player_name% 送出一个大狗是"
      - "say %player_name% 送出一个大狗是"
  40:
    Info:
      - "初级植物"
      - "累计抽奖达到40次可兑换"
      - "只云逊兑换一次"
      - "礼包有一个屁"
    Items:
      - "克鲁斯魔王之铲|1"
      - "克鲁斯魔王之铲|3"
    Cmds:
      - "say %player_name% 送出一个大狗是"
      - "say %player_name% 送出一个大狗是"
      - "say %player_name% 送出一个大狗是"

```

