---
title: "鉴权检查"
weight: 4
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

## 检查商店鉴权信息

由于各种原因商店的鉴权信息可能会失效，失效以后需要及时更新。

- 对于支持api更新的商店鉴权信息理论上永久有效

> 如果再商店后台重置了对应的key，则需要手动更新

- 对于通过浏览器登陆的商店，鉴权信息有效期一般为一天

```shell
# 检查 单个商店鉴权信息
apkgo check oppo
```

{{< hint info >}}

### 提示

如果资源允许可以写个定时任务每10个小时调用一次

```shell
apkgo check --quite
```

来自动刷新商店鉴权信息
{{< /hint >}}
