---
description: RPG服务器必备神器，此插件为BQ提供玩家可视化界面
---

# 龙之任务



|         |                       |
| :-----: | :-------------------: |
| 适用服务端核心 |       1.12.2全核心       |
|   前置插件  | BetonQuest，DragonCore |
|   可选前置  |          萨德发          |

## 1.插件介绍

1\. 该插件能全面可视化您的BQ任务系统，方便玩家进行任务操作

2\. 界面基于龙核写法完全自定义，随心所欲制作属于你的服务器风格界面

3\. 超级简单的操作方法轻轻松松上手编辑

4\. 可自由编辑NPC对话框，实现高品质任务体系

5.可自由配置主线任务/支线任务/日常任务....等等

## 2.插件展示

![](<../.gitbook/assets/image (12).png>)

![](<../.gitbook/assets/image (23) (1).png>)

![](<../.gitbook/assets/image (19).png>)

## 3.插件命令

```
 /qv open defaultgui 打开GUI界面|需要权限: dqv.open.界面名
 /qv open [界面名] [玩家名]|需要权限：OP权限
 /qv reload 重载插件
```

## 4.使用说明

**\[重要事项]**

在插件第一次运行时会刷新BQ任务配置项，目录

所以在加载插件之前请先备份一份BQ配置文件

使用初始配置连接插件

之后在把配置移回去

**1.正确运行插件方式**

![](<../.gitbook/assets/image (18) (1).png>)

{% hint style="info" %}
1.在售后群内下载最新版龙之任务视图安装包,BetonQuest1.10基础依赖

2.安装包内包含了龙核材质包文件，插件本体

3\. 把QuestView放入客服端的龙核材质包，插件放入服务端的plugins文件内

4\. 重启服务器加载插件

5\. 生成\[DragonQuestView]文件夹后放入激活码，重启服务器。插件加载完毕
{% endhint %}

2\. **如何配置对话框并运行**

{% hint style="info" %}
1\. 本插件为NPC对话添加了自定义对话选项

首先需要打开\[BetonQuest>config.yml]

找到default\_conversation\_IO: 这一条节点

替换成

default\_conversation\_IO: DragonCore

此节点一定要加上！不然无法适应对话框

2\. 接下来为NPC添加一段对话

打开\[BetonQuest>default>main.yml]

添加一条

npcs:

&#x20; '1': 新手任务
{% endhint %}

![](<../.gitbook/assets/image (17).png>)

{% hint style="info" %}
然后打开\[BetonQuest>default>conversations]文件夹

新建一个yml文件

内容写上

quester:

&#x20; cn: "新手任务"

first: 'a1'

NPC\_options:

&#x20; a1:

&#x20;   text: 你好，旅行者!

&#x20;   pointers: q1, end

player\_options:

&#x20; q1:

&#x20;   text: 你也好...

&#x20; end:

text: 啊对对对

然后创建一个NPC \[/NPC create 新手任务]

右键即可开启对话框
{% endhint %}

![](<../.gitbook/assets/image (15) (1) (1).png>)

{% hint style="info" %}
1\. 对话框的配置文件在\[DragonQuestView>Cornv>default.yml]

此文件可自由配置对话图片背景，格式。

注:需要有足够的龙核界面制作基础。食用前请先学习龙核制作
{% endhint %}

![](<../.gitbook/assets/image (22) (1).png>)



### 4.1 搭配BQ任务的一些设置

**本插件可以给任务做出分类**

配置文件\[QuestConfig.yml]

![](<../.gitbook/assets/image (13) (1).png>)

{% hint style="info" %}
questType: "主线" #此节点用来给任务做出分类

列如: 测试任务

对应BQ的击杀僵尸任务，我想给他分到支线任务

只需要把questType: "主线"改为questType: "支线"

即可自动适应
{% endhint %}

**这里的\[主线]需要对应\[Guis>defaultgui.yml]配置文件的Type"主线"**

![](<../.gitbook/assets/image (24) (1).png>)

![](<../.gitbook/assets/image (5) (1) (1) (1).png>)

**如果想要创建一个新的任务分类**

我们需要打开插件的配置文件\[Guis>defaultgui.yml]文件

![](<../.gitbook/assets/image (7) (1).png>)

{% hint style="info" %}
复制一份文件

更改文件的Type节点

我这里是改为了Type: "示例分类"
{% endhint %}

**接着把\[QuestConfig.yml]文件内的配置和此界面对接**

![](<../.gitbook/assets/image (25) (1) (1) (1).png>)

这样新的分类就已经添加完毕了

### 4.2 如何配置任务视图与日志绑定

{% hint style="info" %}
插件激活后文件内会生成一个\[QuestConfig.yml]文件

此文件用来连接BQ任务事件

首先创建一个击杀僵尸的任务
{% endhint %}

​

![](<../.gitbook/assets/image (3) (1).png>)

{% hint style="info" %}
接着更改配置文件的节点

identifier: ""\[任务名称]

在此节点内写入接到的任务名称

接到击杀僵尸任务后就会在GUI内显示任务信息
{% endhint %}

![](<../.gitbook/assets/image (21) (1).png>)

![](<../.gitbook/assets/image (6) (1).png>)



### 4.3 制作一个简单的打怪流程

{% hint style="info" %}
**打开 BetonQuest>default文件**

1\. \[main.yml]文件

我们要先绑定NPC

variables:

&#x20; block: LOG

npcs:

&#x20; '0': 新手任务&#x20;

2.\[conversations]文件夹

这个文件夹存放NPC对话流程

先简单写一份对话流程

&#x20;

quester:

&#x20; cn: "新手任务"&#x20;

first: 'a6,a1,a3'&#x20;

NPC\_options:&#x20;

&#x20; a1: #节点

&#x20;   text: 你好，旅行者! #对话文本

&#x20;   pointers: q1, end&#x20;

conditions: '!击杀僵尸1'&#x20;

&#x20; a2:

&#x20;   text: 你能帮我击杀5只僵尸吗？

&#x20;   pointers: q2, end

&#x20; a3:

&#x20;   text: 你已经凯旋归来了吗!

&#x20;   pointers: q3, q4

&#x20; a4:

&#x20;   text: 贡献你！完成了任务！这是你的奖励

&#x20;   conditions: '击杀僵尸2,!击杀僵尸3'

&#x20;   events: '击杀僵尸3,击杀僵尸文本3,击杀僵尸奖励' #执行的任务事件

&#x20;   pointers:

&#x20; a5:

&#x20;   text: 不！你并没有完成这项任务！

&#x20;   pointers:

&#x20; a6:

&#x20;   text: 有新的任务我会告诉你的\~

&#x20;   conditions: '击杀僵尸3'

&#x20;   pointers:

player\_options: #玩家讲的话

&#x20; q1:

&#x20;   text: 我能够做什么？

&#x20;   pointers: a2

&#x20; q2:

&#x20;   text: 好的！没问题！

&#x20;   pointers:

&#x20;   events: '击杀僵尸1,击杀僵尸文本1,击杀僵尸'

&#x20; q3:

&#x20;   text: 是的！我已经击杀了他们！

&#x20;   pointers: a4, a5

&#x20; q4:

&#x20;   text: 不！我还没有！

&#x20;   pointers:

&#x20; end:

text: 抱歉我得先走了。

3.\[conditions.yml]文件

此文件是任务条件

&#x20;

击杀僵尸1: 'tag 击杀僵尸1'

击杀僵尸2: 'tag 击杀僵尸2'

击杀僵尸3: 'tag 击杀僵尸3'

4.\[events.yml]文件

此文件是任务事件

&#x20;

击杀僵尸1: 'tag add 击杀僵尸1'

击杀僵尸2: 'tag add 击杀僵尸2'

击杀僵尸3: 'tag add 击杀僵尸3'

击杀僵尸文本1: 'journal add 击杀僵尸1'

击杀僵尸文本2: 'journal add 击杀僵尸2'

击杀僵尸文本3: 'journal add 击杀僵尸3'

击杀僵尸: 'objective start 击杀僵尸'

击杀僵尸奖励: 'command eco give %player% 500'

2\. \[journal.yml]文件

此文件是任务文本

&#x20;

击杀僵尸1: '&6主线任务 \&a击杀5只僵尸'

击杀僵尸2: '&6主线任务 \&a您已经完成击杀'

击杀僵尸3: '&6主线任务 \&a任务完成！'

3\. \[objectives.yml]文件

此文件是编辑任务目标

&#x20;

击杀僵尸: mmobkill 低级僵尸 amount:5 events:击杀僵尸2,击杀僵尸文本2 label:mythicmobs notify
{% endhint %}

好了，这是一份简单的BQ任务过程

首先和 新手任务NPC对话接取任务

![](<../.gitbook/assets/image (4) (1).png>)

点击我能够做什么？

任务就会更新进GUI界面

![](<../.gitbook/assets/image (20).png>)

此任务是要击杀5个MM怪，在MM文件mobs文件怪物ID是低级僵尸

![](<../.gitbook/assets/image (16) (1) (1).png>)

击杀完毕后返回NPC所在地，对话完成任务即可

![](<../.gitbook/assets/image (8) (1) (1).png>)

### 4.4 示例配置项下载

实在不会请下载这一份配置项，照葫芦画瓢

{% file src="../.gitbook/assets/龙之任务配置示例.zip" %}

## 6.配置项

{% hint style="info" %}
&#x20;\[Conv]文件夹

此文件夹是对话框界面，可自由配置每一个NPC的对话框
{% endhint %}

{% hint style="info" %}
&#x20;\[guis]文件夹

此文件夹是插件的GUI界面文件，可自由配置
{% endhint %}

{% hint style="info" %}
&#x20;\[CodeConfig.yml]文件

此文件是激活码文件
{% endhint %}

{% hint style="info" %}
\[ItemConfig.yml]文件

此文件是在任务栏显示的奖励物品设置
{% endhint %}

{% hint style="info" %}
&#x20;\[LangConfig.yml]文件

此文件是语言文件
{% endhint %}

{% hint style="info" %}
\[QuestConfig.yml]文件

此文件是任务GUI显示设置文件

可以配置任务详细信息
{% endhint %}
