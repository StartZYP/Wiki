---
cover: >-
  ../.gitbook/assets/src=http___i0.hdslb.com_bfs_article_643cb3f8d166763b7f2ea894adeffe7b93301acb.jpg&refer=http___i0.hdslb.jpg
coverY: 0
description: 过年发红包的趣味必不可少的趣味组件，支持物品，点券，金币，口令，问答，拼手气红包
---

# 龙之红包

|         |                                          |
| :-----: | :--------------------------------------: |
| 适用服务端核心 |                 1.12.2全核心                |
|   前置插件  | DragonCore,ProtocolLib,PlayerPoint,Valut |
|   可选前置  |                     无                    |

## 1.插件简介

1.支持红包类型模式有【问答红包】【口令红包】【拼手气红包】。

2.支持发送红包类型【物品红包】【点券红包】【金币红包】。

3.支持玩家自选红包皮肤，红包皮肤取决于权限。

4.支持聊天栏Gui显示红包样式，交互点击方式领取。

5.红包支持显示历史领取记录，一览小伙伴瓜分多少。

6.支持跨服红包，红包队列。

## 2.插件展示



## 3.插件命令

```
/dragonredpacket | drp use pt [skin] &7- &c发普通拼手气红包 &6权限:dragonredpacket.pt
/dragonredpacket | drp use kl [skin] &7- &c发送口令拼手气红包 &6权限:dragonredpacket.kl
/dragonredpacket | drp use wd [skin] &7- &c发送口令拼手气红包 &6权限:dragonredpacket.wd
/dragonredpacket | drp reload [skin] &7- &c重载配置项。默认op使用

```

## 4.使用说明

权限列表

```
//玩家红包皮肤权限
dragonredpacket.skin.皮肤节点 (此处配置项有讲)
//玩家领取红包权限
dragonredpacket.get
```

1.拿到插件后丢进plugin中，启动生成配置项，填写激活码。

2.检查配置项配置。配置文件中baseredpacket 是所有红包存储的地方，需要改红包的一些样式或者逻辑，请在此处修改。（Ps:龙核配置）

3.进游戏发红包 输入，/drp use pt skin1 就会按照skin1的皮肤进行发红包。

4.最后适配需要自己调整图片之类的。

5.可以自己创建一个总界面去调用红包这些皮肤界面，比如点击图片触发命令/drp use pt \[皮肤编号]

## 5.配置项

```
# 此处填写你的验证码
Code: ""
# 是否聊天栏显示红包图标
IsShowRedPacketImg: true
# 红包未领取后回收时间 默认60秒
Timeout: 60

# 发送红包时触发的指令
SendRedPacketCmd:
  - "bc 玩家{Player} 在一服发送了{Num}个 {type}红包，总额{Value}"
  - "say 哈哈哈这是指令"
# 领取红包时触发的指令
GetRedPacketCmd:
  - "bc 玩家{Player} 在一服领取到价值{Money}的{type}红包,还有{Value}个红包"
  - "say 哈哈哈领取红包时触发的指令"

# 三种类型红包模板 此处位于 本插件 baseredpacket 目录下
oderredpacket:
  Get: "领取口令.yml"
  Send: "口令红包.yml"
questionredpacket:
  Get: "领取问答.yml"
  Send: "问答红包.yml"
normalredpacket:
  Get: "领取普通.yml"
  Send: "普通红包.yml"

# 红包皮肤 支持Url 可以自己额外做一个红包选皮肤的ui 点击搭配执行 /drp use pt [skin] 召唤出对应皮肤的红包界面
redpacketskin:
  skin1: "https://tabclass.coding.net/p/minecraftproject/d/ResouceImg/git/raw/master/RedPackagePng/1.png"
  skin2: "https://tabclass.coding.net/p/minecraftproject/d/ResouceImg/git/raw/master/RedPackagePng/2.png"
  skin3: "https://tabclass.coding.net/p/minecraftproject/d/ResouceImg/git/raw/master/RedPackagePng/3.png"
  skin4: "https://tabclass.coding.net/p/minecraftproject/d/ResouceImg/git/raw/master/RedPackagePng/4.png"
  skin5: "https://tabclass.coding.net/p/minecraftproject/d/ResouceImg/git/raw/master/RedPackagePng/5.png"

# 红包语言文件
Lang:
  Lang1: "没得领红包的权限"
  Lang2: "没得这个红包了"
  Lang3: "没发普通红包权限"
  Lang4: "没发口令红包权限"
  Lang5: "没有问答红包权限"
  Lang6: "请检查你准备发送红包参数是否正确"
  Lang7: "红包已经抢完"
  Lang8: "领过了还想领？"
  Lang9: "口令或答案错误"
  Lang10: "§e§l↓↓↓>>§c§l鼠标点击§e§l<<↓↓↓"
  Lang11: "§b§l------>>§a§l抢抢抢抢§b§l<<------"
  Lang12: "§e§l↑↑↑>>§c§l鼠标点击§e§l<<↑↑↑"
  Lang13: "红包金额应该是正数！"
  Lang14: "至少需要一个人来抢吧！"
  Lang15: "手持的物品总数要大于瓜分人数，老铁！"
  Lang16: "金额要大于瓜分人数啊，老铁！"
  Lang17: "你兜兜里点券貌似不够啊！"
  Lang18: "已将你的点券包入红包中！"
  Lang19: "你兜兜里钱好像不太够！"
  Lang20: "已将你的金币放入红包中！"
```

