---
description: 一款可以让头顶有气泡的聊天框
cover: >-
  ../.gitbook/assets/src=http___i0.hdslb.com_bfs_article_643cb3f8d166763b7f2ea894adeffe7b93301acb.jpg&refer=http___i0.hdslb.jpg
coverY: 0
---

# 聊天与表情包

## 1.插件介绍 <a href="#1.-cha-jian-jie-shao" id="1.-cha-jian-jie-shao"></a>

作者：沐老师 QQ：1134802072

## 2.插件展示

<figure><img src="../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>

## 3.插件命令 <a href="#3.-cha-jian-ming-ling" id="3.-cha-jian-ming-ling"></a>

```
指令全部为OP权限执行
emojis reload
emojis player 表情
emojis use 气泡 玩家设置当前使用的气泡类型
emojis emojis/chat 玩家名称 表情/气泡 [增加表情/气泡 不限时]
emojis emojis/chat 玩家名称 表情/气泡 天数
[增加表情/气泡 到期日期=当天日期+天数]
emojis prolong/plc 玩家名称 表情/气泡 天数
[延迟表情/气泡 到期日期=旧到期日期+天数]
```

## 4.使用说明 <a href="#4.-shi-yong-shuo-ming" id="4.-shi-yong-shuo-ming"></a>

表情包配置在emojis文件夹中

可以随意创建yml文件 其中的表情配置均会加载

```
表情1:
  width: 50
  height: 50
  # 表情以玩家为坐标的位置
  x: 0
  y: 1
  z: 0
  # 多久后消失 单位:秒
  time: 2
  # 是否在播放表情时播放声音 不播放删除或者填none即可
  sound: "none"
  # 必填 播放范围 附近多少格的玩家可以看到
  range: ""
  # 图片地址 支持gif url
  texture: "xx/xx.png"

```

```
PAPI
emojis_size 玩家表情总数
emojis_namee_1 玩家第一个表情名称
emojis_timee_1 玩家第一个表情到期时间 此变量返回值格式在config.yml中配置
emojis_namec_1 玩家第一个气泡名称
emojis_timec_1 玩家第一个气泡到期时间 此变量返回值格式在config.yml中配置
emojis_total 服务器表情总数
emojis_sname_1 服务器第一个表情名称
emojis_srange_1 服务器第一个表情显示范围
emojis_stime_1 服务器第一个表情显示时间(秒)

```

