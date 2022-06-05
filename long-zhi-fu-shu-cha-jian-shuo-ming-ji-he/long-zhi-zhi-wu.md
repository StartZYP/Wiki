---
description: 适用于多种RPG服务器，适合设置区域采矿或者区域种植等操作。
cover: >-
  ../.gitbook/assets/src=http___i0.hdslb.com_bfs_article_643cb3f8d166763b7f2ea894adeffe7b93301acb.jpg&refer=http___i0.hdslb.jpg
coverY: 0
---

# 龙之采种

|         |                                                            |
| :-----: | :--------------------------------------------------------: |
| 适用服务端核心 |                          1.12.2全核心                         |
|   前置插件  | PlaceholderAPI,DragonCore,ProtocolLib,WorldGuard,Adyeshach |
|   可选前置  |                              无                             |

## 1.插件介绍 <a href="#1.-cha-jian-jie-shao" id="1.-cha-jian-jie-shao"></a>

1.支持多文件夹分类自定义采种实体属性.

2.支持多种采种实体多种状态，(未成熟，成熟，解锁).并有采种强度。

3.支持采种实体设置js脚本种植前与采集两种js脚本，支持多种参数.

4.支持定时wg区域生成自定义采种实体(矿物，植物，宝箱均可).

5.掉落物支持MM库物品，无需再繁杂配置，直接调用MM物品。

6.支持玩家在wg区域内自由种植，种植的植物有归属权。

7.右键植物自定义Gui显示采种实体信息界面。

8.采种工具设置 (工具耐久,工具采种强度)

9.采种强化药剂 (增产量,加快成熟时间，减缓成熟时间)

10.支持地皮区域化种植，每个玩家可以种植在自己地皮内，根据权限有数量限制。

## 2.插件展示 <a href="#2.-cha-jian-zhan-shi" id="2.-cha-jian-zhan-shi"></a>

![](../.gitbook/assets/7\_@BEB3R]W8NBX%YOQFRT3Y.jpg)

![](<../.gitbook/assets/image (26).png>)

![](<../.gitbook/assets/image (14).png>)

![](<../.gitbook/assets/image (25).png>)

![](<../.gitbook/assets/image (16).png>)

![](<../.gitbook/assets/image (15).png>)

## 3.插件命令 <a href="#2.-cha-jian-zhan-shi" id="2.-cha-jian-zhan-shi"></a>

```
/DragonCollectPlant|dcp list &7- &c查看物品库(鼠标点击获取 ,按住Shift获取一组)
/DragonCollectPlant|dcp AddItem &7- &c手持物品添加进物品库（删除请再ItemData中删除）
/DragonCollectPlant|dcp SetHandUtils [工具节点名] &7- &c设置手中物品为采集工具
/DragonCollectPlant|dcp SetGrowthItem [增长剂节点名] &7- &c设置手中物品为增长剂工具
/DragonCollectPlant|dcp area list &7- &c展示区域产量列表
/DragonCollectPlant|dcp reload &7- &c重载插件数据。
```



## 4.使用说明 <a href="#4.-shi-yong-shuo-ming" id="4.-shi-yong-shuo-ming"></a>

#### 1.拿到插件丢进Plugin中 启动服务端等他生成文件夹 DragonCollectPlant.

#### 2.进入DragonCollectPlant文件夹中Config.yml填写激活码.

#### 3.了解文件结构

![](<../.gitbook/assets/image (3).png>)

CollectPlantEntity \[文件夹 里面是所有的采种矿物或植物，可以无限制创建文件夹都可以识别到。]

Script \[是你采种的时候执行的脚本 ScriptLib是你要加载的其他插件的类文件(不懂就别动)]

config.yml \[里面包含催化道具 采摘道具 区域设定 等一些配置组]

EntityModel.yml \[模型配置，会动态合并到龙核配置项中]

ItemData.yml \[物品库数据 如果启用MM物品库则无视这个]

Lang.yml \[语言配置文件]

#### 4.随机生成矿物或植物方法

1.首先进入服务器 使用斧头圈一个地 （切记从地板开始圈）随机生成是地板+1方块的位置，没设置好会载入土里。

2.圈好地后使用wg插件 名字设置为plant1 (按照这种方法圈4个) 名字从plant1-4

3.圈好地后进config.yml配置项 设置想在wg区域内生成的植物。

```
# Area区域生成 【注意】: 必须装worldguard 才有此效果
# 例
#  a1: （a1是区域名称）
#    PlantName: "暴热花" （这个是植物中DisPlayName名称）
#    RandomNum: 5  （这个是随机固定生成植物或矿物数量）
# 这些区域一定要选择平地
RandomGrowthGroundArea:
  plant1:
    WorldName: "flatroom"
    PlantName: "爆裂花"
    RandomNum: 6
  plant2:
    WorldName: "flatroom"
    PlantName: "爆裂花"
    RandomNum: 7
  plant3:
    WorldName: "flatroom"
    PlantName: "塔合曼"
    RandomNum: 8
  plant4:
    WorldName: "flatroom"
    PlantName: "天山雪莲"
    RandomNum: 7
```

4.切记设置好世界植物名称和数量。这样就大功告成了，等待生成就行了。

#### 5.如何创建一个植物或者矿物

在CollectPlantEntity 文件夹中创建一个任意名字的yml。

然后将老配置中的yml复制进新配置，根据指示进行修改

#### 6.编写脚本与使用脚本

在Script目录中打开CollectScripts.yml

例:&#x20;

```
范围等级脚本_参数2: |-
  function execute(player){
    var result = player.getLevel() <= <1> && player.getLevel() >= <2>;
    if(!result){
  	player.sendMessage("§c你等级不在范围<1>-<2>内");
    };
    return result;
  }
```

脚本中有占位符 <1> 这个代表填充位 对应采种实体目录下的

```
# 脚本类 支持papi 参数变量等
# 采集条件脚本需要返回 true或者false 满足所有才会返回成功
# 此处<->符号右侧 为参数，会填充到脚本中 <1>和<2>得位置进行计算
CollectConditionScript:
  - "权限限制脚本_参数1<->DragonPlant.Collect.3"
  - "等级大于等于脚本_参数1<->10"
```

你可以写参数也可以不写参数

不写参数:  - "脚本名称" （Scirpt目录一定要有这个 权限限制脚本\_无参）

写1个参数: - "脚本名称<->参数1"

写2个参数: -"脚本名称<->参数1<分割>参数2"

#### 7.制作一个种子或者矿物孢

1.手持一个你想设置为种子的物品上面写上关键字。

```
# 所有可以种下的物品中Lore必须要有此关键字
GlobalLoreKey:
  - "种子"
  - "矿石"
```

2\. 手持物品输入 /lore add 爆裂花种子

3.手持这个种子对wg区域内右键就可以种植了。切记 爆裂花一定要存在于 采种实体文件夹中yml

## 5.配置项

