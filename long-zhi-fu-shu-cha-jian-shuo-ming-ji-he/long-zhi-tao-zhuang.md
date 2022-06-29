---
description: RPG服务器必备套装神器之一，可图形化渲染特效
cover: >-
  ../.gitbook/assets/src=http___i0.hdslb.com_bfs_article_643cb3f8d166763b7f2ea894adeffe7b93301acb.jpg&refer=http___i0.hdslb.jpg
coverY: 0
---

# 龙之套装

|         |                                           |
| :-----: | :---------------------------------------: |
| 适用服务端核心 |                 1.12.2全核心                 |
|   前置插件  |                 DragonCore                |
|   可选前置  | SX-Attribute,AttributePlus,ItemLoreOrigin |

## 1.插件介绍 <a href="#1.-cha-jian-jie-shao" id="1.-cha-jian-jie-shao"></a>

1.无需实时刷新Lore极度耗能，只需要附加ItemTips即可

2.支持自定义Lore，无需将属性写入到副ItemTips中。

3.套装支持自定义药水效果。

4.套装支持多种属性插件 ap2 ap3 sx2 sx3 ilo 几乎涵盖所有。

5.套装特效，支持每种套装自定义图片特效加持,动画加持

B站视频教程: [https://www.bilibili.com/video/BV1er4y1M7oG/](https://www.bilibili.com/video/BV1er4y1M7oG/)

## 2.插件展示 <a href="#2.-cha-jian-zhan-shi" id="2.-cha-jian-zhan-shi"></a>

![](<../.gitbook/assets/image (18).png>)

![](../.gitbook/assets/9TW\({\[NFE5YTVE9FM\[AN1\[K.png)

![](../.gitbook/assets/P@VLJ\~A2XZCU%K5H\(@YEBRW.png)

![](../.gitbook/assets/$\(OR\_X5O2X5BO0UW5}64$HC.jpg)

![](<../.gitbook/assets/image (28).png>)

## 3.插件命令 <a href="#3.-cha-jian-ming-ling" id="3.-cha-jian-ming-ling"></a>

```
/DragonSuit |drs reload 重载插件
```

## 4.使用说明 <a href="#4.-shi-yong-shuo-ming" id="4.-shi-yong-shuo-ming"></a>

1.首先将插件丢进Plugin 装好前置，将前置插件安装好，等待生成配置项

2.找到DragonSuit/DragonSuit/副本1套装/xxxx.yml 这个就是套装 你可以创建无数个文件夹都会读取到

3.其中每个套装有SuitGlobalKey 关键字，此关键字主要用于识别那一套套装。

4.SuitShowItemTips 是右侧额外展示的内容，可以随便写，不受属性药水限制。

5.ConvertSuit 配置项是转换 三元运算方式 是否满足?满足执行:不满足执行，此处戊土头盔为 ItemLoreKey 使用<> 进行包裹， 此处运算完成后会替换到 SuitShowItemTips

6\. ItemLoreKey 为套装中装备的关键字 比如头盔 鞋子等一系列。

7.SuitEffect 是每套套装效果 其中包含 属性 药水 特效，数字是标注当你穿戴第几套会触发的效果。

8.药水和属性都很简单，唯一要说的是特效，特效需要搭配动画+图片定位，其中图片定位蕴含公式，支持papi变量和数学运算符计算。如下

```
雷霆法阵:
    width: "2.65+<Num>*2.65"
    height: "2.65+<Num>*2.65"
    BindAnimation: "action1"
    x: "0"  # 时间文字显示 为了保证摆放在你想要的位置
    y: "-2.8+<Num>*3" #这个会加上实体自身身高
    z: "0"
```

\<Num>是特效总数 比如你在套装写了3个雷霆法阵 \<Num> 会依次从1 -3 创建三个此处Num就为变量

带引号的都可以触发公式效果，你可以携带Papi进行运算，给每个人不同的效果和体验。

BindAnimation 为绑定的动画特效，动画特效跟魂环一致，具体请看魂环篇章。

9.ItemTips部分跟龙核原来的一致你可以放在龙核目录，如果不放他会默认加载一个本地目录的，根据你的需求进行设置

设置的时候需要注意 match: ""  这里写套装所包含的Lore 也可以把这些复制到Tips里重写 反正就是龙核界面 比如你所有的套装都有 套装两个Lore关键字 那么在上面就写套装 match: "套装"

## 5.配置项

#### 基础核心配置项

```
########################################
############激活码填写位################
########################################
Code: ""
# 龙核槽位识别  填以下槽位会被识别为套装之一
DragonSlot:
  - "额外槽位1"
  - "额外槽位2"
########################################
############模式设置################
########################################
# 填写 1.启用SX 2.启用AP 3.启用ap2.0
Use: 2

########################################
############功能启用设置################
########################################
# 是否启用特效功能
UseSuitEffect: false
# 是否启用药水
UsePotion: true

########################################
###########特效详情设置################
########################################
# 套装特效支持Papi变量 能让每个人特权分明
# 支持公式运算简单加减乘除
# 支持多方位定位 通过<Num>变量 <Num> 为你套装.yml的Effect总数量
# 角度无法支持
# 这个特效做的是根据套装数量越来越大
SuitEffect:
  雷霆法阵:
    TexturePath: "DragonSuit/2.png"
    width: "2.65+<Num>*2.65"
    height: "2.65+<Num>*2.65"
    BindAnimation: "action1"
    x: "0"  # 时间文字显示 为了保证摆放在你想要的位置
    y: "-2.8+<Num>*3" #这个会加上实体自身身高
    z: "0"
    rotatex: 90 # 偏转度数
    rotatey: 0
    rotatez: 0
  头顶紫环:
    TexturePath: "DragonSuit/1.png"
    width: "2.65+<Num>*2.65"
    height: "2.65+<Num>*2.65"
    BindAnimation: "action1"
    x: "0"  # 时间文字显示 为了保证摆放在你想要的位置
    y: "4.5" #这个会加上实体自身身高
    z: "0"
    rotatex: 180 # 偏转度数
    rotatey: 0
    rotatez: 0

###################################
##########套装贴图动画组配置#########
###################################
animationList:
  action1:
    # 旋转动画设置
    RotateAnimation:
      delay: 0
      angle: 0
      duration: 5000
      cycleCount: 1
      fixed: true
      resetTime: 5
  action2:
    # 旋转动画设置
    RotateAnimation:
      delay: 0
      angle: 0
      duration: 5000
      cycleCount: 1
      fixed: true
      resetTime: 1
    # 上下动画设置
    TranslateAnimation:
      delay: 0
      distance: 2
      duration: 5000
      cycleCount: 1
      fixed: true
    # 缩放动画设置
    ScaleAnimation:
      delay: 0
      cycleCount: 1
      fixed: false
      fromScale: 2.5
      toScale: 1.0
      duration: 2000
```

#### 龙核Tips配置项

```


# 这里写套装所包含的Lore 也可以把这些复制到Tips里重写 反正就是龙核界面
match: "套装"

Functions:
  open: |-
    方法.执行方法('缓存物品数据');
    方法.异步执行方法('DragonSuit');

  缓存物品数据: |-
    方法.设置组件值('lore','texts',界面变量.lines);
    方法.发包('DragonSuit','Update',方法.序列化物品(方法.取物品('mouse')));

  DragonSuit: |-
    方法.延时(400);
    方法.更新变量值('DragonSuit_ItemTips');
    界面变量.套装 = 方法.取变量('DragonSuit_ItemTips');
    (方法.取文本长度(界面变量.套装)==0)?{方法.设置组件值('DragonSuit背景','visible','false');方法.设置组件值('DragonSuitlore','visible','false');}:方法.设置组件值('DragonSuitlore','texts',方法.取变量('DragonSuit_ItemTips'));

背景:
  type: "texture"
  x: "(方法.取鼠标x-10+界面变量.w > 方法.取屏幕宽度) ? 方法.取屏幕宽度-界面变量.w : 方法.取鼠标x+10;"
  y: "(方法.取鼠标y-8+界面变量.h > 方法.取屏幕高度) ? 方法.取屏幕高度-154 : 方法.取鼠标y-8;"
  width: "界面变量.w+8"
  height: "界面变量.h+8"
  texture: "https://download.bbs.miaomc.cn/o_1g1r42okn1k801apu1pq31jkhh1sa.png"

lore:
  type: "label"
  x: "背景.x+4"
  y: "背景.y+4"
  texts: "界面变量.lines"

DragonSuit背景:
  type: "texture"
  x: "背景.x+界面变量.w+10"
  y: "背景.y"
  width: "方法.取组件值('DragonSuitlore','width')+8"
  height: "方法.取组件值('DragonSuitlore','height')+8-10"
  visible: true
  texture: "https://download.bbs.miaomc.cn/o_1g1r42okn1k801apu1pq31jkhh1sa.png"
DragonSuitlore:
  type: "label"
  x: "背景.x+界面变量.w+10+4"
  y: "背景.y+4-10"
  visible: true
```

#### 套装展示配置项

```
# 此为Lore关键字
# Lore中必须含有戊土两个字才会触发 套装效果
SuitGlobalKey: "戊土"
# 物品ItemTips会显示此处的信息
# 此处戊土头盔为 ItemLoreKey 使用<> 进行包裹
SuitShowItemTips:
  - "----大地之盾套装(<当前>/<总数>)----"
  - "<戊土头盔>"
  - "<戊土胸甲>"
  - "<戊土裤子>"
  - "<戊土鞋履>"
  - "----大地之盾套装(描述)----"
  - "二套:"
  - "属性: +1000防御"
  - "特效: 大地之盾"
  - "三套:"
  - "药水: 明亮效果"
  - "属性: +10086防御"
  - "介绍:"
  - "来自大地之龙的低语-戊土之龙掉落几率(0.5%)"

# 三元运算方式   是否满足?满足执行:不满足执行
# 此处戊土头盔为 ItemLoreKey 使用<> 进行包裹
# 此处运算完成后会替换到 SuitShowItemTips
ConvertSuit:
  - "<戊土头盔>?§b§l戊土头盔 (1/1):§c§l戊土头盔 (0/1)"
  - "<戊土胸甲>?§b§l戊土胸甲 (1/1):§c§l戊土胸甲 (0/1)"
  - "<戊土裤子>?§b§l戊土裤子 (1/1):§c§l戊土裤子 (0/1)"
  - "<戊土鞋履>?§b§l戊土鞋履 (1/1):§c§l戊土鞋履 (0/1)"

# 当Lore中含有此关键字 则触发套装效果 此触发条件必须通过SuitGlobalKey的规则筛选
ItemLoreKey:
  - "戊土头盔"
  - "戊土胸甲"
  - "戊土裤子"
  - "戊土鞋履"
# 套装效果
SuitEffectSuitEffectSuitEf:
  1:
    #1则代表一件套
    Lore:
      - "防御力+100"
    Effect: []
    Potion:
      - "1<->1"
    #药水id<->药水等级
  2:
    #2则代表两件套
    Lore:
      #属性lore
      - "防御力+1000"
    Effect:
      - "头顶紫环"
    Potion:
      - "1<->2"
      #药水id|药水等级
```
