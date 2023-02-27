---
title: "配置"
weight: 2
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

## 配置

### 1. 环境变量

apkgo使用`APKGO_HOME`环境变量来确认缓存文件位置，如不设置默认为`$HOME/.apkgo`，开始之前请确认`APKGO_HOME`

``` shell
#若输出为空则默认为 $HOME/.apkgo
echo $APKGO_HOME
```

> 本文档关于路径，如不特殊说明则全部是`$APKGO_HOME`的相对路径

### 2. 初始化

apkgo支持两种模式

- 单机（即只在初始化的机器上使用）
- 团队（一人维护认证信息，其他成员皆可发布，也可与CI/CD及其他工具配合使用）
{{< hint danger >}}
**提示**

团队模式下使用`git repo`同步各商店认证信息，注意一定要创建私有的git仓库并合理的配置仓库读写权限。

同一团队一定要使用同一个repo。

{{< /hint >}}

``` shell
# 根据提示提供对应信息即可
apkgo init
```

### 3. 认证信息

打开初始配置文件`$APKGO_HOME/secrets/store_config.json`，可以看到`stores`节点下包含了所有支持的商店。

所有商店的认证信息分为两类：

- 支持API调用，直接去相应管理后台拿到认证信息即可

{{< tabs "stores" >}}
{{< tab "huawei" >}}

#### 华为AppGalleryConnect

前往[华为AppGalleryConnect](https://developer.huawei.com/consumer/cn/doc/development/AppGallery-connect-Guides/agcapi-getstarted-0000001111845114)获取到`client_id`、`client_secret`。大概类似于下面这样：

``` json
{
    "huawei": {
        "client_id": "1093143911913426",
        "client_secret": "D4F2F8A234232F59FD232CF5DEE03A29E"
    }
}
```

{{< /tab >}}
{{< tab "xiaomi" >}}

#### 小米开放平台

在[小米开放平台管理中心](https://dev.mi.com/distribute/doc/details?pId=1134)获取到`private_key`。大概类似于下面这样：

```json
{
    "xiaomi": {
        "username": "example@icloud.com",
        "private_key": "e4p2302p2302p2302p2302pgessd1mrumvo3pzw"
    }
}
```

> username 用户名，在小米开发者站登陆的邮箱
{{< /tab >}}
{{< tab "vivo" >}}

#### vivo应用商店

前往[vivo](https://dev.vivo.com.cn/documentCenter/doc/326)申请开通api传包服务，然后获取`access_key`、`access_secret`。大概类似于下面这样：

``` json
{
    "vivo": {
        "access_key": "20223420y0b",
        "access_secret": "01bss6dfsdfewfewf6aa4fb"
    }
}
```

{{< /tab >}}
{{< tab "fir.im" >}}

#### betaqr.com

前往[文档](https://www.betaqr.com/docs)获取`api_token`。大概类似于下面这样：

```json
{
    "fir": {
        "api_token": "a090dsd59sdfsdfdsfc7e5"
    }
}
```

{{< /tab >}}
{{< tab "pgyer" >}}

### 蒲公英

前往[文档](https://www.pgyer.com/doc/view/api#fastUploadApp)获取`api_key`。大概类似于下面这样：

```json
{
    "pgyer": {
        "api_key": "5222323f90e0sdfewf5434sdsdssd"
    }
}
```

{{< /tab >}}
{{< /tabs >}}

若不需要某个商店，直接删除掉对应的节点即可。配置完成自己需要的商店以后执行

``` shell
# 会检查所有配置的认证信息是否有效
# 如果全部有效且是团队使用则会将配置信息同步至git repo
apkgo check
```

- 需要通过浏览器登录拿到认证信息

`oppo`,`tencent`,`baidu`,`qh360`均使用这种认证方式

``` shell
# 执行以下命令如果，oppo市场认证信息无效则会打开oppo管理后台
# 在管理后台登录成功以后会自动关闭浏览器同步认证信息
apkgo check oppo
```

- 私有服务配置及认证

私有服务的使用需要apkgo插件系统的支持，请前往[高级使用-插件](advance/plugin.md)
