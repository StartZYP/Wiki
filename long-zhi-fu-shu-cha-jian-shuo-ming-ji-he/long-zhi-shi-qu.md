---
description: 此插件是一款个性化拾取提示插件。
cover: >-
  ../.gitbook/assets/src=http___i0.hdslb.com_bfs_article_643cb3f8d166763b7f2ea894adeffe7b93301acb.jpg&refer=http___i0.hdslb.jpg
coverY: 0
---

# 龙之拾取

|         |            |
| :-----: | :--------: |
| 适用服务端核心 |  1.12.2全核心 |
|   前置插件  | DragonCore |
|   可选前置  |      无     |

## 1.插件简介

1.支持自定义配置拾取样式&#x20;

2.支持自定义拾取音效&#x20;

3.动态修改&#x20;

4.支持多种配置混合

5.支持聊天栏回放拾取信息【配合聊天栏插件】

## 2.插件展示

![](<../.gitbook/assets/image (6) (1) (1) (1) (1) (1).png>)

![](<../.gitbook/assets/image (5) (1) (1) (1) (1).png>)

## 3.插件命令

```
/DragonPickMsg | dpm reload 重载插件
```

## 4.使用说明

![](<../.gitbook/assets/image (3) (1) (1) (1) (1).png>)

1.插件丢进服务端plugin目录

2.PickMsg丢进客户端龙核材质目录

3.启动服务端填激活码，完成！



## 5.配置展示

```
Code: "" #验证
# 是否开启聊天栏提示
ChatIsOpen: true
ChatMsg: "§e[拾取提示]§b恭喜您捡到{DropItem} * {Num}个物品"
#如果匹配不到默认用这个配置文件
defaultyml: "pickhud/PickMsg1.yml"
# 是否开启多种PickMsg 支持多种Hud false就只启用默认的
OpenMulit: true
# true开启lore识别 false开启name识别
IsLore: true
# Hud提示配置
PickMsgConfig:
  type1:
    name: "普通"
    Useyml: "pickhud/PickMsg1.yml"
  type2:
    name: "高级"
    Useyml: "pickhud/PickMsg2.yml"
  type3:
    name: "史诗级"
    Useyml: "pickhud/PickMsg3.yml"
```
