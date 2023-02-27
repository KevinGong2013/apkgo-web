---
title: "消息通知"
weight: 5
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

## 配置消息通知

执行应用更新操作以后可以将操作结果同步到办公软件，目前支持飞书、企业微信、钉钉以及自定义webhook通知

### 配置

打开`$APKGO_HOME/secrets/store_config.json`文件，查看`notifiers`节点

``` json
{
   "notifiers": {
        "lark": {
            "key": "[替换为你的值]",
            "secret_token": "[替换为你的值]"
         },
        "dingtalk": {
            "access_token": "[替换为你的值]",
            "secret_token": "[替换为你的值]"
        },
        "wecom": {
            "key": "[替换为你的值]"
        },
        "webhook": {
            "url": [
                "[替换为你的值]"
            ]
        }
   }
}
```

删掉不需要的节点，然后填写你想要支持的平台。

### 测试&同步

```shell
apkgo check notifiers
```

来测试及同步配置信息
