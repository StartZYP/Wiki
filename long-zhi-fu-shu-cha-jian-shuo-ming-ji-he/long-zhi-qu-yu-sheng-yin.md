---
description: 通过龙之核心让插件可以在某一个区域的进出事件来播放和关闭不同的BGM，从而达到进BOSS对战时音乐和进副本时不同。
cover: >-
  ../.gitbook/assets/src=http___i0.hdslb.com_bfs_article_643cb3f8d166763b7f2ea894adeffe7b93301acb.jpg&refer=http___i0.hdslb.jpg
coverY: 0
---

# 龙之区域声音

|         |                       |
| :-----: | :-------------------: |
| 适用服务端核心 |       1.12.2全核心       |
|   前置插件  | DragonCore，WorldGuard |
|   可选插件  |     PlaceholderAPI    |

## 1.插件介绍 <a href="#1.-cha-jian-jie-shao" id="1.-cha-jian-jie-shao"></a>

1.支持wg进出区域事件,触发相关音乐。

2.支持音乐叠加逻辑判断,如大区域进小区域,区域交集区域并集等。

3.支持wg事件触发cmd指令,进区域触发与出区域触发,支持papi变量

## 2.插件展示 <a href="#2.-cha-jian-zhan-shi" id="2.-cha-jian-zhan-shi"></a>

<figure><img src="../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>

## 3.插件命令 <a href="#3.-cha-jian-ming-ling" id="3.-cha-jian-ming-ling"></a>

```
仅有重载指令
/das reload
```

## 4.使用说明 <a href="#4.-shi-yong-shuo-ming" id="4.-shi-yong-shuo-ming"></a>

1.检查前置,安装插件,进config填写激活码。

2.找到DragonAreaSound目录中的AreaConfig进行新建一个yml

3.打开老yml复制到新建的yml配置对应的wg区域,和相关音乐文件目录

4.音乐放DragonCore目录下为根目录

