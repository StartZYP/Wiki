---
description: 适用于服务器拉新专用的福利模块，让你的玩家想着你第二天的礼物~
cover: >-
  ../.gitbook/assets/src=http___i0.hdslb.com_bfs_article_643cb3f8d166763b7f2ea894adeffe7b93301acb.jpg&refer=http___i0.hdslb.jpg
coverY: 0
---

# 龙之七日福利

## 1.插件介绍 <a href="#1.-cha-jian-jie-shao" id="1.-cha-jian-jie-shao"></a>

1.支持检查玩家当前天数。

2.支持跨服配置数据库同步。

3.可自定义每天礼物的奖励，命令形式发放。

4.支持自定义贴图自由化制作，简洁方便。

5.支持补签卡，售卖补签系统

## 2.插件展示 <a href="#2.-cha-jian-zhan-shi" id="2.-cha-jian-zhan-shi"></a>

![](<../.gitbook/assets/image (10) (1) (1).png>)

## 3.插件命令 <a href="#3.-cha-jian-ming-ling" id="3.-cha-jian-ming-ling"></a>

```
/sign open 打开界面
/sign check [玩家id] 检查玩家签到情况
/sign reload 重载插件
```

## 4.使用说明 <a href="#4.-shi-yong-shuo-ming" id="4.-shi-yong-shuo-ming"></a>



1.将插件安装到服务端，将贴图放到客户端服务端重启，

2.插件将自动生成config.yml

3.然后在cdk填入你的激活码 再次重启服务器。

4.此插件需要安装数据库,并链接数据库才可以使用.

5.查看日志无报错后，进服输入/sign open 进行签到

6.设置补签卡 在游戏中手持要设置的补签卡 /lore name §f§l补签卡 即可 （切记颜色符号用§ 精准匹配）

## 5.配置项 <a href="#5.-pei-zhi-xiang" id="5.-pei-zhi-xiang"></a>

```
#请填写激活码
Code: ""
mysql:
  host: "localhost"
  port: 3306
  base: "sign"
  user: "root"
  password: ""
message:
  message1: "§a您的在线时间已达到1小时,现可领取签到奖励!"
  message2: "§a成功领取奖励!"
  message3: "§c时间还没到,无法领取!"
  message4: "§a补签成功!"
  message5: "§c你没有补签卡,无法补签!"
  message6: "§c已领取!"
crad: "§f§l补签卡"
commands:
  day1:
    - say 1
  day2:
    - say 2
  day3:
    - say 3
  day4:
    - say 4
  day5:
    - say 5
  day6:
    - say 6
  day7:
    - say 7
  all:
    - say 集齐7天
setting:
  #背景
  Main:
    url: "背景.png"
    h: 348
    w: 697
  #补签奖励
  Component_1:
    url: "补签奖励1.png"
    urlHoverd: "补签奖励2.png"
    h: 178
    w: 29
    x: 202
    y: 210
  #领取奖励
  Component_2:
    url: "领取1.png"
    urlHoverd: "领取2.png"
    h: 178
    w: 29
    x: 262
    y: 210
  #时间未到
  Component_3:
    url: "时间未到1.png"
    urlHoverd: "时间未到2.png"
    h: 178
    w: 29
    x: 324
    y: 210
  #已领取
  Component_4:
    url: "已领取1.png"
    urlHoverd: "已领取2.png"
    h: 178
    w: 29
    x: 202
    y: 210
```

