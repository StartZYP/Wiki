---
description: 龙之商店适用于任何服务器商店，支持修改任意界面翻页，支持点券,金币,物品,出售与收购为一体。
cover: >-
  ../.gitbook/assets/src=http___i0.hdslb.com_bfs_article_643cb3f8d166763b7f2ea894adeffe7b93301acb.jpg&refer=http___i0.hdslb.jpg
coverY: 0
---

# 龙之商店

|         |                               |
| :-----: | :---------------------------: |
| 适用服务端核心 |           1.12.2全核心           |
|   前置插件  | PlayerPoints,Vault,DragonCore |
|   可选插件  |               无               |

## 1.插件介绍 <a href="#1.-cha-jian-jie-shao" id="1.-cha-jian-jie-shao"></a>

1.支持点券，金币，以物换物，售出，收购为一体。

2.支持定时优惠和vip优惠功能。

3.支持模糊搜索，分页，商品分类。

4.玩家的每日限购、每月限购、永久限购。

5.支持数据库查询购买日志，绝不放过任何一个卡bug玩家,回溯任何一条交互商店记录。

6支持自定义购买前与购买后两种自定义js脚本。

## 2.插件展示

![](<../.gitbook/assets/image (4) (1) (1) (1).png>)

![](<../.gitbook/assets/image (7) (1) (1) (1) (1).png>)

## 3.插件命令

```
1./systemshop | ss create <id> 创建新的商品
2./systemshop | ss reload 重载所有商品
3./systemshop | ss save 保存所有商品(重载之前记得保存)
4./systemshop | ss open <界面名称> 打开某个商店界面(不需要加.yml)
5./systemshop | ss open gui 自动生成一份商店界面配置
```

## 4.使用说明

### 4.1 正确运行插件方式

![](<../.gitbook/assets/image (14) (1).png>)

**1.在售后群内下载最新版龙之商店压缩包**

**2.解压DSystemShop.zip，得到插件主体材质包(可自行定制)，放入客户端 .minecraft\resourcepacks\DragonCore 路径内(也就是龙核材质包内)**

**3.运行一次服务器，插件生成DragonSystemShop文件夹，打开该文件内的CodeConfig.yml文件输入你的激活码。之后重启服务器，插件就已经开始运行了！**

### **4.2 如何配置一个商品**

**1.首先在DragonSystemShop文件夹中，找到Guis里面自动生成的商店界面（也就是gui.yml），查看Type(Type后面的可以自定义)**

****![](<../.gitbook/assets/image (21).png>)****

**flow后面加Goods文件夹中商品的文件名也可以显示，这里先说Type，所以我们暂时把他删掉**

**Type: "1"**

**此项对应该商城的Type**

**商品一定要和对应商城里的Type保持一致，不然商店不会显示商品**

**添加商品到商店里**

**我们回到游戏里，手持想要出售|收购的物品，然后输入/ss create 1(“1”为商品创建好后的文件名)，就会弹出**

****![](<../.gitbook/assets/image (13) (2).png>)****

**我们直接输入添加物品的商店的Type即可**

**然后填入所需的金币(0为不消耗)**

****![](<../.gitbook/assets/image (8) (1).png>)****

**填入所需点券(0为不消耗)**

![](<../.gitbook/assets/image (9) (1).png>)

**输入消耗物品的名称及其数量(none为不消耗)**

**例:单个物品:火药(消耗物品的名称)##1(消耗物品的个数)**

&#x20;  **多个物品:火药##1\<and>南瓜##1(多个物品之间用\<and>连接)**

****![](<../.gitbook/assets/image (15) (1).png>)****

**输入写在Limit.yml文件内的脚本(注:脚本不存在或填none都不会进行限制)**

**输入脚本名或输入none**

****![](<../.gitbook/assets/image (26) (1) (1).png>)****

**buy为出售，即玩家花钱购买**

**sell为收购，即玩家用物品换钱**

**输入商品性质后**

**物品创建完成**

### 4.3 修改商品配置项

**改变商品出售|收购**

**找到DragonSystemShop\Goods里对应的yml文件，双击打开**

****![](<../.gitbook/assets/image (25) (1) (1).png>)****

**找到isbuy这行，当他为true时，商品为出售，当他为false时，商品即为收购**

**改变商品消费金额**

**找到DragonSystemShop\Goods里对应的yml文件，双击打开**

****![](<../.gitbook/assets/image (27).png>)****

**eco为消耗|获得的金币数(不消耗|获得即为0)**

![](<../.gitbook/assets/image (22) (2).png>)

**points为消耗|获得的点券数(不消耗|获得即为0)**

![](<../.gitbook/assets/image (24).png>)

**needItem为购买所需要的物品，#前面为物品名，#后面为消耗的数量，两个以上的物品中间请用\<and>连接**

****![](<../.gitbook/assets/image (23).png>)****

**js为共买所需要的权限|变量**

****![](<../.gitbook/assets/image (7).png>)****

**js后面加Limit.yml内的配置(即为红框框住的内容)，无则为none**

****![](<../.gitbook/assets/image (6) (2).png>)****

**需要的权限即为玩家名=十七哥哥**

****![](<../.gitbook/assets/image (5) (1) (1).png>)****

**若玩家名≠十七哥哥，就不能购买商品ss**

### 4.4 脚本教学

```
打开Limit.yml文件
1.识别玩家名字
例:
自定:
  limit: |-
    function execute(player){
      var result = player.getName() == '识别的玩家名';
      if(!result){
    	player.sendMessage("如果条件不符，错误提示在这里，颜色符号用§");
      };
      return result;
    }
2.识别某条权限
例:
自定:
  limit: |-
    function execute(player){
      var result = player.hasPermission("识别权限");
      if(!result){
    	player.sendMessage("如果条件不符，错误提示在这里，颜色符号用§");
      };
      return result;
    }
3.指定变量
例:
自定:
  limit: |-
    function execute(player){
      var result = '识别的变量，要带%%' == '符合变量的条件';
      if(!result){
    	player.sendMessage("如果条件不符，错误提示在这里，颜色符号用§");
      };
      return result;
    }
4.等级限制
例:
自定:
  limit: |-
    function execute(player){
      var result = player.getLevel() >= 限定的等级;
      if(!result){
    	player.sendMessage("如果条件不符，错误提示在这里，颜色符号用§");
      };
      return result;
    }
```

## 5.配置项



**Guis文件:**

**本文件放入插件的GUI配置表**

**可自由配置本插件的技能视图界面**

**\[食用前请学习龙之核心界面制作]**

&#x20;****&#x20;

**PlayerDate文件:**

**本文件储存玩家数据**

&#x20;****&#x20;

**CodeConfig文件:**

**授权码放在这里激活**

&#x20;****&#x20;

**lang文件:**

**插件的语言文件**

**可更改插件提示信息**

&#x20;****&#x20;

**Limit文件:**

**插件的脚本文件**

**可自定义购买权限**

