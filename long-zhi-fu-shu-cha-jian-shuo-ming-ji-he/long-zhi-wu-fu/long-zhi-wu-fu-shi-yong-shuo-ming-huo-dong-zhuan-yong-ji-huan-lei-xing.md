# \[龙之五福]-使用说明(活动专用-集换类型)

| 插件名称 | 龙之五福                   |
| ---- | ---------------------- |
| 适用核心 | 1.12.2全端               |
| 必要前置 | DragonCore，ProtocolLib |
| 可选前置 | PlaceholderAPI         |

### 1.插件介绍

1.支持任意五种方块合成。

2.合成总量有计数。

3.实时刷新排行榜系统。

4.支持Bc跨服数据共享

5.支持合成后任意命令执行

6.支持瓜分点券 金币

### 1.展示图片

{% embed url="https://player.bilibili.com/player.html?aid=56850347&cid=99299213&page=1" %}

### 3.使用说明

输入 /fivefu set xxx 设置五个

/fivefu set 福1

/fivefu set 福2

/fivefu set 福3

/fivefu set 福4

/fivefu set 福5

![](http://p.ipedg.com/wp-content/uploads/2022/01/image-16.png)

/fivefu gui 打开五福界面

![](http://p.ipedg.com/wp-content/uploads/2022/01/image-17.png)

如何渲染icon图标成福？？

龙核itemicon.yml文件下写入给他们渲染上

![](http://p.ipedg.com/wp-content/uploads/2022/01/image-18.png)

### 3.配置项

```
# 激活码
Code: ""

#跨服请将此文件夹填写到同一个路径，我会把玩家数据写进此路径
SavePath: ""
# 根据合成次数执行命令
CmdDo:
  5:
    - "bc <Player> 成功合成了<Num>次,送他五百块"
    - "eco give <Player> 500"
  10:
    - "bc <Player> 成功合成了<Num>次,送他一千块"
    - "eco give <Player> 1000"

Msg:
  ComposeNum: "你成功集齐了五福合成了,这是第几<Num>合成"
```
