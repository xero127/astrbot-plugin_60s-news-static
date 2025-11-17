# 📰 AstrBot Daily News



每日 60 秒新闻推送插件
<br>
开发基于：https://github.com/anka-afk/astrbot_plugin_daily_news
（version: v2.1.0）  
<br>
此分支针对国内服务器访问60s相关域名出错问题进行优化测试



## 🛠️ 配置说明

在插件配置中设置以下参数:

```json
{
  "target_groups": {
    "description": "需要推送60s新闻的群组唯一标识符列表",
    "type": "list",
    "hint": "填写需要接收60s新闻推送的群组唯一标识符，如: 你的平台名称(自己起的):GroupMessage:1350989414, napcat:FriendMessage:123456, telegram:FriendMessage:123456",
    "default": ["这里填你的平台名字:GroupMessage:这里填写你的群号"]
  },
  "push_time": {
    "description": "推送时间(以服务器时区为准)",
    "type": "string",
    "hint": "填写推送的时间，如: 08:00, 12:30, 18:00",
    "default": "08:00"
  },
  "show_text_news": {
    "description": "是否显示文字新闻",
    "type": "bool",
    "hint": "是否显示文字新闻，默认隐藏",
    "default": false
  },
  "use_local_image_draw": {
    "description": "是否使用本地图片绘制",
    "type": "bool",
    "hint": "是否使用本地图片绘制，为否则使用api获取图片",
    "default": false
  }
}
```

### 🛠️ 参数说明

下面是一份参数对照表:
| 参数名称 | 类型 | 默认值 | 描述 |
|----------------------|--------|----------------------------|--------------------------------------------------------------|
| target_groups | list | ["aiocqhttp:GroupMessage:这里填写你的群号"] | 需要推送 60s 新闻的群组唯一标识符列表 |
| push_time | string | "08:00" | 推送时间(以服务器时区为准) |
| show_text_news | bool | false | 是否显示文字新闻，默认隐藏 |
| use_local_image_draw | bool | true | 是否使用本地图片绘制，为否则使用 api 获取图片 |

群聊唯一标识符分为: 前缀:中缀:后缀

# AstrBot 4.0 及以后群聊前缀直接填你自己起的名字, 例如我连接了 napcat 平台, 起名字叫"困困猫", 那么前缀就是"困困猫"!

AstrBot 4.0 及以前:

**下面是所有可选的群组唯一标识符前缀:**

| 平台 | 群组唯一标识符前缀 |
|------------------|-------------------------------------|
| qq, napcat, Lagrange 之类的 | aiocqhttp |
| qq 官方 bot | qq_official |
| telegram | telegram |
| 钉钉 | dingtalk |
| gewechat 微信(虽然已经停止维护) | gewechat |
| lark | lark |
| qq webhook 方法 | qq_official_webhook |
| astrbot 网页聊天界面 | webchat |

**下面是所有可选的群组唯一标识符中缀:**

| 群组唯一标识符中缀 | 描述 |
|----------------------|--------|
| GroupMessage | 群组消息 |
| FriendMessage | 私聊消息 |
| OtherMessage | 其他消息 |

**群组唯一标识符后缀为群号, qq 号等**

下面提供部分示例:

1. napcat 平台向私聊用户 1350989414 推送消息, 我将平台命名为困困猫

   - `困困猫:FriendMessage:1350989414`

2. napcat 平台向群组 1350989414 推送消息

   - `aiocqhttp:GroupMessage:1350989414`

3. telegram 平台向私聊用户 1350989414 推送消息

   - `telegram:FriendMessage:1350989414`

4. telegram 平台向群组 1350989414 推送消息
   - `telegram:GroupMessage:1350989414`

## 📝 使用命令

### 查看插件状态

```
/news_status
```

显示当前配置的目标群组、推送时间、是否显示文字新闻，以及距离下次推送的剩余时间。

### 手动推送新闻

```
/push_news [模式]
```

支持的模式:

- `image` - 仅推送图片新闻
- `text` - 仅推送文字新闻
- `all` - 同时推送图片和文字新闻（默认）

此命令会将新闻推送到配置的所有目标群组。

### 用户手动获取新闻

```
/get_news [模式]
```

支持的模式:

- `image` - 仅推送图片新闻
- `text` - 仅推送文字新闻
- `all` - 同时推送图片和文字新闻（默认）

此命令会将新闻发送至请求获取新闻的用户会话。
