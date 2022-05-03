---
description: Rpg服务器必备技能神器，此插件为skillapi附属可视化插件。
cover: >-
  ../.gitbook/assets/src=http___i0.hdslb.com_bfs_article_643cb3f8d166763b7f2ea894adeffe7b93301acb.jpg&refer=http___i0.hdslb.jpg
coverY: 0
---

# 龙之技能栏

|         |                                    |
| :-----: | :--------------------------------: |
| 适用服务端核心 |              1.12.2全核心             |
|   前置插件  | DragonCore，PlaceholderAPI，SkillApi |
|   可选前置  |         Vault,PlayerPoints         |

## 1.插件简介

1. 该插件能全面可视化您的SkillView系统 不再为不知道如何指导玩家操作Skills而烦恼。
2. 全DragonCore界面化的操作 玩家全程无指令操作
3. 主界面+子窗口 无需切换一堆界面导致玩家玩不懂
4. 配合Papi的Hud显示 更直观的体现技能绑定内容和技能冷却动画
5. 增加洗点和降级道具 让玩家可以自己选择重开
6. 如果您装了点券或者金币插件 可设置技能升级所需的金币与点券
7. 所有技能单独配置 限制等级 权限 所需货币 不再为普通技能vip技能无法限制而烦恼
8. 界面基于龙核写法完全自定义，只要您想得到的，在您有耐心学习下来后都可做到
9. 拥有自己的ModHooker，可以让玩家自定义按键
10. 以下展示图中 所见即所得 贴图以及配置自带 上手即用

## 2.插件展示

![](<../.gitbook/assets/image (3) (1) (1) (1).png>)

![](<../.gitbook/assets/image (8) (1) (1) (1) (1) (1).png>)

![](<../.gitbook/assets/image (7) (1) (1) (1) (1) (1) (1).png>)

![](<../.gitbook/assets/image (12) (1) (1) (1) (1).png>)

## 3.插件指令

```
/dragonSkillview | dsv <界面名> 打开龙技界面 需要权限：dragonskillview.open.<界面名>
/dragonSkillview | dsv reload 重载界面
```

## 4.使用说明

#### 4.1 正确运行插件的方式

![](<../.gitbook/assets/image (12) (1).png>)

{% hint style="info" %}
1.在售后群内下载最新版龙技能视图包+Skill基础技能\[必须]+MCCore技能依赖\[必须]

2\. 技能包同时包含一个\[SkillViewHUD]文件，将此文件放入龙之核心配置文件GUi文件内，载入选用技能展示框.

3\. 解压DragonCore【客服端贴图】压缩包，得到插件主体材质包，放入客服端内的DragonCore\[龙核材质包]内

4.插件运行前检查服务器内是否加入了PlaceholderAPI\[必须前置]

5\. 如果你是群组服请将\[BC]BungeereSkillViewSyn放入到你的BC插件栏

6.运行一次服务器插件生成\[DragonSkillView-Rel]文件，打开该文件内的文件输入你的激活码。之后重启服务器，插件就已经开始运行了！
{% endhint %}

#### 4.2  **如何正确配置数据库和跨服文件**

```
SQL:
  enable: false[改为ture打开数据库连接]
  database: "skills"[数据库名称，此项可以随意起名]
  username: "root"
  password: "你的数据库密码"
```

{% hint style="info" %}
Ps:数据库不会配置的请看 首页教程
{% endhint %}

{% hint style="info" %}
1\. \[数据库配置]首先我们打开插件配置文件内\[PluginConfig]文件

更改完成后重启服务器，在后台界面本插件加载时会出现两条信息

\[\[com.zaxxer.hikari.HikariDataSource] DragonSkill-Connection-Pool - Starting...]

\[\[com.zaxxer.hikari.HikariDataSource] DragonSkill-Connection-Pool - Start completed.]
{% endhint %}

![](<../.gitbook/assets/image (13) (1) (1).png>)

{% hint style="info" %}
出现本信息说明数据库连接成功，若是失败请检查你的数据库密码，ID是否和插件配置内信息是否一致。

2\. \[跨服文件]同样是在\[PluginConfig]文件内找到

YmlDataPath: ""\[文件路径]

此项配置是配置一个文件夹，来存放玩家yaml数据

本地服务器均可读取本配置文件
{% endhint %}

#### 4.3 **如何配置一个技能并释放**

{% hint style="info" %}
1\. 首先在\[SkillApi]文件内找到\[dynamic]文件

在Skill文件内放入你写好的技能
{% endhint %}

![](<../.gitbook/assets/image (16) (1) (1).png>)

![](<../.gitbook/assets/image (18) (1) (1).png>)

{% hint style="info" %}
**2.**接着打开class文件

在此文件放入你的职业
{% endhint %}

![](<../.gitbook/assets/image (20) (1).png>)

![](<../.gitbook/assets/image (11).png>)

记得检查skills是否写入了本职业的持有技能，然后，class reload重载skillapi

3\. 然后我们进入服务器加入该职业\[/class profess \[职业名]]

&#x20;

4.回到本插件配置文件找到\[SkillConfig]文件

![](<../.gitbook/assets/image (21) (1) (1).png>)

5.接着我们打开插件的Guis文件内

![](<../.gitbook/assets/image (19) (1).png>)

如果未出现本文件请先输入\[/dsv open defaultgui]加载出来

打开本文件

![](<../.gitbook/assets/image (10) (1).png>)

Type: "爆发"

此项对应skillapi技能的Type

![](<../.gitbook/assets/image (14) (1) (1).png>)

一定要保持一致，不然将会加载不出技能

6.重载插件就可以载入技能了

7.接着打开我们的插件GUI界面\[/dsv open defaultgui]

![](<../.gitbook/assets/image (7) (1) (1).png>)

现在就已经载入技能到了我们的GUI界面

8.点击技能进行拖拽，放入到下方技能空列

![](<../.gitbook/assets/image (22) (1) (1).png>)

这样技能就可以出现在对应的快捷键内

9\. 到这里就可以正常使用你的skillapi技能了

![](<../.gitbook/assets/image (17) (1).png>)

#### 4.3 **如何配置学习技能消耗**

示例:

我想要让技能需要技能书才能学习该如何做

1\. 首先我们打开插件配置文件\[SkillConfig]

2\. 找到你要配置的技能

![](<../.gitbook/assets/image (15) (1) (1).png>)

needItemName: "\&c\&l利刃环绕技能书" \[需要的物品name]

&#x20; needItemCount: 1 \[学习技能需要多少本技能书]

&#x20; levelAddItem: 1 \[升级技能需要多少本技能书]

1\. 修改完成后重载插件\[/dsv reload]

同时给出了更多配置已经详细写在了插件配置

## 5.配置项

{% hint style="info" %}
Ps:给看不懂教程的蠢蛋使用，实在不行您就替换下面这个默认配置，照葫芦画瓢吧
{% endhint %}

{% file src="../.gitbook/assets/插件配置需求.zip" %}

![](<../.gitbook/assets/image (4) (1) (1).png>)

{% hint style="info" %}
Guis文件:

本文件放入插件的GUI配置表

可自由配置本插件的技能视图界面

\[食用前请学习龙之核心界面制作]
{% endhint %}

&#x20;

{% hint style="info" %}
PlayerDate文件:

本文件储存玩家数据
{% endhint %}

&#x20;

{% hint style="info" %}
CodeConfig文件:

授权码放在这里激活
{% endhint %}

&#x20;

{% hint style="info" %}
KeyConfig文件:

此文件可以自定义插件技能释放快捷键

\[同样使用的龙核键位监听]
{% endhint %}

&#x20;

{% hint style="info" %}
lang文件:

插件的语言文件

可更改插件提示信息
{% endhint %}



{% hint style="info" %}
PluginConfig文件:

本文件可更改插件数据储存方式

\[MySQL]\[本地数据储存]

可更改洗点道具，降级道具

是否启用配套MOD

SkillConfig文件:

此文件配置你的skillapi技能项
{% endhint %}
