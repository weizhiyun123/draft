# webhook 中的 json

* 你会从云巴收到的 json 

你会收到的 json 有三种：`connect/disconnect`, `subscribe/unsubscribe` 和 `publish`，接下来我们来具体看看它们的内容是什么，代表什么意思。

* connect/disconnect

这类 json 会有以下结构：

```json
{
    "action":`{String}`,
    "from":`{String}`,
    "timestamp":`{YYYY-MM-DDThh:mm:ss.sTZD}`,
    "appkey":`{String}`,
    "uid":`{String}`
}
```

- `action` 表示现在用户在进行什么操作，可能为 `connect` `disconnect`
- `from` 表示这是一个 `prewebhook` 还是 `postwebhook`，`prewebhook` 需要用户的回应，`postwebhook` 不需要
- `timestamp` 表示这个请求产生的时间，timestamp 格式遵循 ISO 8601 标准
- `appkey` 用户的 appkey
- `uid` 云巴的唯一用户标识，详细的说明参考这里[uid 是什么](#hook)

* subscribe/unsubscribe

这类 json 会有以下结构：

```json
{
    "action":`{String}`,
    "from":`{String}`,
    "timestamp":`{YYYY-MM-DDThh:mm:ss.sTZD}`,
    "appkey":`{String}`,
    "uid":`{String}`,
    "topic":`{String}`,
    "message_id":`{String}`
}
```

- `action` 表示现在用户在进行什么操作，可能为 `subscribe` `unsubscribe`
- `from` 表示这是一个 `prewebhook` 还是 `postwebhook`，`prewebhook` 需要用户的回应，`postwebhook` 不需要
- `timestamp` 表示这个请求产生的时间，timestamp 格式遵循 ISO 8601 标准
- `appkey` 用户的 appkey
- `uid` 云巴的唯一用户标识，详细的说明参考这里[uid 是什么](#hook)
- `topic` 正在进行操作的 topic，关于 topic 的介绍可以参考这里[topic](#hook)
- `message_id` 云巴的唯一消息标识

* publish

这类 json 会有以下结构：

```json
{
    "action":`{String}`,
    "from":`{String}`,
    "timestamp":`{YYYY-MM-DDThh:mm:ss.sTZD}`,
    "appkey":`{String}`,
    "uid":`{String}`,
    "topic":`{String}`,
    "payload":`{String}`,
    "message_id":`{String}`
}
```

- `action` 表示现在用户在进行什么操作，可能为 `subscribe` `unsubscribe`
- `from` 表示这是一个 `prewebhook` 还是 `postwebhook`，`prewebhook` 需要用户的回应，`postwebhook` 不需要
- `timestamp` 表示这个请求产生的时间，timestamp 格式遵循 ISO 8601 标准
- `appkey` 用户的 appkey
- `uid` 云巴的唯一用户标识，详细的说明参考这里[uid 是什么](#hook)
- `topic` 正在进行操作的 topic，关于 topic 的介绍可以参考这里[topic](#hook)
- `payload` 用户想要 publish 的消息内容
- `message_id` 云巴的唯一消息标识