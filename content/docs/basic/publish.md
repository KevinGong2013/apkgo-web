---
title: "开始使用"
weight: 3
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

## 开始使用

最新版本 ![v](https://img.shields.io/docker/v/kevingong2013/apkgo?arch=amd64&sort=date)

在更新应用之前请确认已经升级apkgo到最新版本,然后执行`check`命令，确认本地认证信息有效

``` shell
apkgo check
```

### 使用举例

#### Example 1

``` shell
apkgo upload -f /path/to/release_flat_apk.go --store all
```

- `-f`: 将要上传的apk文件路径
- `-store all`: `all`指配置文件中的所有商店， 当然也可以指定某几个商店例如这样：`--store cams,xiaomi,huawei`

#### Example 2

``` shell
apkgo upload --file32 /path/to/release_apk_32.apk --file64 /path/to/release_apk_64.apk -s huawei,xiaomi --release-notes "1. 禁止了用户的微信登陆\n2. 禁止用户QQ登陆"
```

- `--file32`、`--file64`: 分包上传。 注意不是所有的商店都支持分包上传建议可以配合`--store`使用
- `--release-notes`: 更新日志

#### Example 3

``` shell
apkgo upload -f /path/to/apk.apk -s all --release-notes $CHANGELOG --disable-double-confirmation
```

- `--disable-double-confirmation`: 不二次确认直接开始发布

更多使用方式可以执行 `apkgo upload --help` 查看
