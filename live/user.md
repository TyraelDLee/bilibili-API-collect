# 直播间用户实用API

- [直播间用户实用API](#直播间用户实用api)
- [获取用户持有的粉丝勋章信息](#获取用户持有的粉丝勋章信息)
- [佩戴勋章](#佩戴勋章)
- [进入直播间/当前用户信息](#进入直播间)
- [直播签到](#直播签到)


---

## 获取用户持有的粉丝勋章信息

> https://api.live.bilibili.com/fans_medal/v5/live_fans_medal/iApiMedal

*请求方式：GET*

认证方式：Cookie（SESSDATA）或APP

**url参数：**

| 参数名 | 类型 | 内容        | 必要性 | 备注 |
| ------ | ---- | ----------- | ------ | ---- |
| page    | num  | 返回结果页数 | 非必要   | 返回结果单页最大为10 |

**json回复：**

根对象：

| 字段    | 类型 | 内容     | 备注                        |
| ------- | ---- | -------- | --------------------------- |
| code    | num  | 返回值   | 0：成功<br>-400：请求错误 |
| message | str  | 错误信息 | 默认为空("")                     |
| msg     | str  | 错误信息  | 默认为空("")                  |
| data    | obj  | 信息本体 |                             |

`data`对象：

| 字段           | 类型 | 内容             | 备注                     |
| -------------- | ---- | ---------------- | ------------------------ |
| medalCount     | num  | 勋章数量  |                  |
| count    | num  | 勋章数量         |                       |
| fansMedalList     | array  | 粉丝勋章信息本体    |           |
| name    | str  | 用户名 |                             |
| pageinfo    | obj  | 页码信息 |                             |

`fansMedalList 数组内`对象：

| 字段           | 类型 | 内容             | 备注                     |
| -------------- | ---- | ---------------- | ------------------------ |
| uid     | num  | 发起请求的用户mid  |                  |
| target_id    | num  | up主mid   |                       |
| medal_id     | num  | 粉丝勋章id    |           |
| score    | num  |        |                             |
| level    | num  | 勋章等级 |                             |
| intimacy     | num  | 当前已得亲密度  |                  |
| status    | num  |         |                       |
| source     | num  |        |           |
| receive_channel    | num  | 获得方式 | 2：投币获得<br>3000：b坷拉             |
| is_receive     | num  | 勋章数量  |                  |
| master_status    | num  |             |                       |
| receive_time     | str  | 勋章获取时间  |           |
| today_intimacy    | num  | 本日亲密度 |                             |
| last_wear_time    | num  | 上次佩戴时间 |                             |
| is_lighted     | num  | 是否点亮 | 0：未点亮<br>1：点亮                 |
| medal_level    | num  | 勋章等级         |                       |
| next_intimacy     | num  | 升级所需经验  |           |
| day_limit    | num  | 日经验上限（原力值）|                             |
| medal_name    | str  | 勋章名 |                             |
| master_available     | num  |          |                  |
| guard_type    | num  | 加成状态   |                       |
| lpl_status     | num  |           |           |
| can_delete    | bool  | 可否删除 |                             |
| target_name    | str  | up主用户名 |                             |
| target_face     | str  | up主头像 |                  |
| live_stream_status    | num  | 当前直播间放松状态  |                       |
| icon_code     | num  |         |           |
| icon_text    | str  |     |                             |
| rank    | str  |      |                             |
| medal_color    | num  | 勋章颜色信息 |  颜色数值为10进制的16进制值（下同）  |
| medal_color_start     | num  | 勋章起始颜色    | 从右往左渐变（20级+勋章） |
| medal_color_end    | num  | 勋章结束颜色 |  从右往左渐变（20级+勋章）   |
| guard_level    | num  |           |                             |
| medal_color_border     | num  | 勋章颜色信息  |                  |
| today_feed    | num  | 本日亲密度  |                       |
| todayFeed     | num  | 同上    |           |
| dayLimit    | num  | 日经验上限（原力值） |                             |
| uname    | str  | up主用户名 |                             |
| color     | num  | 勋章颜色  |                  |
| medalName    | str  | 勋章内容     |                       |
| guard_medal_title     | str  | 加成状态  |           |
| anchorInfo    | obj  | up信息 |                             |
| roomid    | num  | 直播间房间号 |                             |

`pageinfo`对象：

| 字段           | 类型 | 内容             | 备注                     |
| -------------- | ---- | ---------------- | ------------------------ |
| totalpages     | num  | 页码总长度       |                       |
| curPage        | num  | 当前返回的页码   | 0：未轮播<br>1：轮播   |

`anchorInfo`对象：

| 字段           | 类型 | 内容             | 备注                     |
| -------------- | ---- | ---------------- | ------------------------ |
| uid     | num  | up主mid   |                       |
| uname        | str  | up主用户名   |                   |
| gender        | num  | 性别 | 0：女<br>1：男<br/>-1：保密   |
| face        | str  | up主头像  |                       |
| silence        | num  | up主禁言状态  |                          |
| masterVip        | num  | 会员类型 |                          |
| masterRank        | num  | 10000 |                          |
| masterLevel        | num  | up主主站等级 |                          |
| masterHeadpic        | str  | up主头像框 |                          |
| masterVerify        | num  |  |                          |
| mobileVerified        | num  | 当前返回的页码   |                          |
| identification        | num  | 当前返回的页码   |                          |
| official        | obj  | 认证信息   |                          |
| rank        | num  | 当前返回的页码   |                          |
| platform_user_level        | num  | up主主站等级   |                          |
| vip_type        | num  | 会员类型 |                          |
| mobile_verify        | num  |            |                          |
| official_verify        | obj  | 认证信息   |                          |

**示例：**

```shell
curl https://api.live.bilibili.com/fans_medal/v5/live_fans_medal/iApiMedal \
-b "SESSDATA=xxx"
```

<details>
<summary>查看响应示例：</summary>

```json
{
    "code": 0,
    "msg": "",
    "message": "",
    "data": {
        "medalCount": 20,
        "count": 19,
        "fansMedalList": [
            {
                "uid": 1,
                "target_id": 3821157,
                "medal_id": 283582,
                "score": 16031,
                "level": 11,
                "intimacy": 1130,
                "status": 0,
                "source": 1,
                "receive_channel": 3000,
                "is_receive": 1,
                "master_status": 1,
                "receive_time": "2021-07-24 23:06:03",
                "today_intimacy": 252,
                "last_wear_time": 1630386090,
                "is_lighted": 1,
                "medal_level": 11,
                "next_intimacy": 10000,
                "day_limit": 1500,
                "medal_name": "秧歌星",
                "master_available": 1,
                "guard_type": 0,
                "lpl_status": 0,
                "can_delete": true,
                "target_name": "东爱璃Lovely",
                "target_face": "https://i0.hdslb.com/bfs/face/fecabd8cb7cc129fd3bdbc4b71cffec91d342bdd.jpg",
                "live_stream_status": 0,
                "icon_code": 0,
                "icon_text": "",
                "rank": "",
                "medal_color": 9272486,
                "medal_color_start": 9272486,
                "medal_color_end": 9272486,
                "guard_level": 0,
                "medal_color_border": 9272486,
                "today_feed": 252,
                "todayFeed": 252,
                "dayLimit": 1500,
                "uname": "东爱璃Lovely",
                "color": 9272486,
                "medalName": "秧歌星",
                "guard_medal_title": "未开启加成",
                "anchorInfo": {
                    "uid": 3821157,
                    "uname": "东爱璃Lovely",
                    "gender": -1,
                    "face": "https://i0.hdslb.com/bfs/face/fecabd8cb7cc129fd3bdbc4b71cffec91d342bdd.jpg",
                    "silence": 0,
                    "masterVip": 2,
                    "masterRank": 10000,
                    "masterLevel": 6,
                    "masterHeadpic": "https://i0.hdslb.com/bfs/garb/ebe4ac76f95ccb9146fdba2db2723f182ec3276b.png",
                    "masterVerify": 0,
                    "mobileVerified": 1,
                    "identification": 1,
                    "official": {
                        "role": 7,
                        "title": "bilibili 直播高能主播",
                        "desc": ""
                    },
                    "rank": 10000,
                    "platform_user_level": 6,
                    "vip_type": 2,
                    "mobile_verify": 0,
                    "official_verify": {
                        "role": 7,
                        "title": "bilibili 直播高能主播",
                        "desc": "",
                        "type": -1
                    }
                },
                "roomid": 21692711
            }
        ],
        "name": "xxx",
        "pageinfo": {
            "totalpages": 2,
            "curPage": 2
        }
    }
}
```

</details>

## 佩戴勋章

> https://api.live.bilibili.com/xlive/web-room/v1/fansMedal/wear

*请求方式：POST*

**表单参数：**

|    参数名   | 类型 |          内容        | 必要性 | 备注 |
| ---------- | ---- | -------------------- | ---- | ---- |
| medal_id   | num  |         勋章id       | 必要 |      |
| csrf       | num  | cookie中bili_jct字段 | 必要 |      |
| csrf_token | num  |          同上        | 必要 |      |

**json回复：**

根对象：

| 字段    | 类型 | 内容     | 备注                        |
| ------- | ---- | -------- | --------------------------- |
| code    | num  | 返回值   | 0：成功                      |
| ttl     | str  |   1     |                              |
| message | str  | 错误信息 | 默认为佩戴成功                |
| data    | obj  | 信息本体 | 默认为无                     |

**示例：**

佩戴勋章id为1的勋章

```JavaScript
var madelForm = new FormData();
madelForm.append("medal_id", 1);
madelForm.append("csrf", bili_jct);
madelForm.append("csrf_token", bili_jct);
$.ajax({
    url: "https://api.live.bilibili.com/xlive/web-room/v1/fansMedal/wear",
    type: "POST",
    data: madelForm,
    dataType: "JSON",
    processData: false,
    contentType: false,
    cache: false,
    xhrFields: {
        withCredentials: true
    },
    success: function (){

    }
})
```

<details>
<summary>查看响应示例：</summary>

```json
{
    "code": 0,
    "message": "佩戴成功",
    "ttl": 1,
    "data": {}
}
```

</details>

## 直播签到

> https://api.live.bilibili.com/xlive/web-ucenter/v1/sign/DoSign

*请求方式：GET*

认证方式：Cookie（SESSDATA）或APP

**json回复：**

根对象：

| 字段    | 类型 | 内容     | 备注                    |
| ------- | ---- | -------- | ---------------------- |
| code    | num  | 返回值   |   0：成功<br>1：参数错误 |
| ttl     | str  |    1    |                         |
| message | str  | 错误信息 | 默认为当日签到奖励内容    |
| data    | obj  | 信息本体 | 默认为空                 |


## 进入直播间

> https://api.live.bilibili.com/xlive/web-room/v1/index/getInfoByUser

*请求方式：GET*

认证方式：Cookie（SESSDATA）或APP
当拦截或修改room_id参数即可阻止显示进入直播间。但会导致直播间关注/粉丝团显示异常以及房管权限异常。

**url参数：**

|    参数名   | 类型 |          内容        | 必要性 | 备注 |
| ---------- | ---- | -------------------- | ---- | ---- |
| room_id   | num  |         房间id       | 必要 |  可以为短号    |


**json回复：**

根对象：

| 字段    | 类型 | 内容     | 备注                        |
| ------- | ---- | -------- | --------------------------- |
| code    | num  | 返回值   | 0：成功                      |
| ttl     | str  |   1     |                              |
| message | str  | 错误信息 | 默认为佩戴成功                |
| data    | obj  | 信息本体 |                              |

**示例：**

查询账户在直播间545的信息

```shell
curl 'https://api.live.bilibili.com/xlive/web-room/v1/index/getInfoByUser?room_id=545' \
```

<details>
<summary>查看响应示例：</summary>

```json
{
  "code": 0,
  "message": "0",
  "ttl": 1,
  "data": {
    "user_level": {
      "level": 26,
      "next_level": 27,
      "color": 5805790,
      "level_rank": "\u003e50000"
    },
    "vip": {
      "vip": 0,
      "vip_time": "0000-00-00 00:00:00",
      "svip": 0,
      "svip_time": "0000-00-00 00:00:00"
    },
    "title": {
      "title": ""
    },
    "badge": {
      "is_room_admin": false
    },
    "privilege": {
      "target_id": 0,
      "privilege_type": 0,
      "privilege_uname_color": "",
      "buy_guard_notice": null,
      "sub_level": 0,
      "notice_status": 1,
      "expired_time": "",
      "auto_renew": 0,
      "renew_remind": null
    },
    "info": {
      "uid": 0,
      "uname": "xxx",
      "uface": "xxx",
      "main_rank": 10000,
      "bili_vip": 2,
      "mobile_verify": 1,
      "identification": 0
    },
    "property": {
      "uname_color": "",
      "bubble": 0,
      "danmu": {
        "mode": 1,
        "color": 5566168,
        "length": 30,
        "room_id": 573893
      },
      "bubble_color": ""
    },
    "recharge": {
      "status": 0,
      "type": 1,
      "value": "",
      "color": "fb7299",
      "config_id": 0
    },
    "relation": {
      "is_followed": true,
      "is_fans": false,
      "is_in_fansclub": true
    },
    "wallet": {
      "gold": 0,
      "silver": 0
    },
    "medal": {
      "cnt": 1,
      "is_weared": true,
      "curr_weared": {
        "target_id": ,
        "target_name": "xxx",
        "medal_name": "xxx",
        "target_roomid": ,
        "level": 1,
        "intimacy": 1,
        "next_intimacy": 200,
        "day_limit": 1500,
        "today_feed": 0,
        "is_union": 0,
        "medal_color_start": ,
        "medal_color_end": ,
        "medal_color_border": ,
        "is_lighted": 1,
        "guard_level": 0,
        "icon_id": 0,
        "score": 
      },
      "up_medal": {
        "uid": 15641218,
        "medal_name": "boba",
        "medal_color": 6067854,
        "level": 1
      }
    },
    "extra_config": {
      "show_bag": true,
      "show_vip_broadcast": true
    },
    "mailbox": {
      "switch_status": 0,
      "red_notice": 0
    },
    "user_reward": {
      "entry_effect": {
        "id": 0,
        "privilege_type": 0,
        "priority": 0,
        "web_basemap_url": "",
        "web_effective_time": 0,
        "web_effect_close": 0,
        "web_close_time": 0,
        "copy_writing": "",
        "copy_color": "",
        "highlight_color": "",
        "mock_effect": 0,
        "business": 0,
        "face": "",
        "basemap_url": "",
        "show_avatar": 0,
        "effective_time": 0
      },
      "welcome": {
        "allow_mock": 1
      }
    },
    "shield_info": {
      "shield_user_list": [
        {
          "uid": 000,
          "uname": "xxx"
        },
        {
          "uid": 000,
          "uname": "xxx"
        },
        {
          "uid": 000,
          "uname": "xxx"
        },
        {
          "uid": 000,
          "uname": "xxx"
        },
        {
          "uid": 000,
          "uname": "xxx"
        }
      ],
      "keyword_list": [],
      "shield_rules": {
        "rank": 1,
        "verify": 0,
        "level": 1
      }
    },
    "super_chat_message": {
      "list": []
    },
    "lpl_info": {
      "lpl": 0
    },
    "cd": {
      "guide_free_medal_cost": 0,
      "guide_light_medal": 0,
      "guide_follow": 0,
      "guard_compensate": 0,
      "interact_toasts": []
    }
  }
}
```

</details>

## 直播签到

> https://api.live.bilibili.com/xlive/web-ucenter/v1/sign/DoSign

*请求方式：GET*

认证方式：Cookie（SESSDATA）或APP

**json回复：**

根对象：

| 字段    | 类型 | 内容     | 备注                    |
| ------- | ---- | -------- | ---------------------- |
| code    | num  | 返回值   |   0：成功<br>1：参数错误 |
| ttl     | str  |    1    |                         |
| message | str  | 错误信息 | 默认为当日签到奖励内容    |
| data    | obj  | 信息本体 | 默认为空                 |
