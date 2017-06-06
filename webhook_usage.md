# webhook 基本介绍

* webhook 是用来干什么的？

webhook 主要在用户进行 `connect`, `disconnect`, `subscribe`, `unsubscribe` 和 `publish` 的时候添加了可由服务器控制的机制，从而提供控制用户行为以及统计功能。

* 我需要什么来使用 webhook？

要使用 webhook，你需要要有一个接收由我们发起的 post 请求并返回特定数据的服务器。

# webhook 是怎么用的？

* 首先要在 portal 上设置`此处省略`

* 设置完成后你会通过 `这里是地址` 收到一个 json 数据包，这个 json 数据包阐述了现在你账户下用户正在进行（`connect`, `disconnect`, `subscribe`, `unsubscribe` 和 `publish` 之中的）哪一个操作，这个 json 数据包看起来会和下面的数据包类似。这里面的内容具体表示什么意思我们会在[下一个章节](#hook)进一步说明。

```json
{
    "action":"connect/disconnect",
    "from":"prewebhook/postwebhook",
    "timestamp":"2017-02-17T15:42:28+08:00",
    "appkey":"58579af0b09557a45c14301322",
    "uid":"2839915490570825472"
}
```

* 这时候你可以给`这里也是地址` 回应一个 json（如果你只设置了 post-webhook 则不需要向云巴回应 json），云巴会根据你回应的 json 来决定接下来需要做什么。你需要回复的 json 大概是下面的样子。同样，这个 json 的具体含义我们会在[下一个章节](#hook)进一步说明。

```json
{
    "enable_original_action":"true",
    "extra_action":
    [
        {
            "action":"subscribe",
            "topic":"subscribe_topic_example"
        },
        {
            "action":"unsubscribe",
            "topic":"unsubscribe_topic_example"
        },
        {
            "action":"publish",
            "topic":"publish_topic_example",
            "payload":"payload_example"
        }
    ]
}
```