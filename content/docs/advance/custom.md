---
title: "内部服务"
weight: 2
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

## 内部服务

内部分发服务的支持是通过[apkgo插件](/docs/advance/plugin/)实现。

### 1. 下载插件

联系插件开发者获取插件，将插件放在任意位置
> 推荐放在`APKGO_HOME`根目录下

``` shell
# 直接执行你下载的插件
./apkgo_plugin

# 确保输出以下日志，证明插件安装成功
This binary is a plugin. These are not meant to be executed directly.
Please execute the program that consumes these plugins, which will
load any plugins automatically

```

### 2. 配置插件

打开`APKGO_HOME/config.yaml`文件，添加如下配置

``` yaml
# 示例忽略掉
storage:
    location: local
# 主要是以下节点的配置
plugins:
      # apkgo 插件名称 联系插件开发者
    - name: apkgo-plugin
      # 插件在本地的路径
      path: path/to/your/apk-plugin
```

### 3. 验证

```shell
apkgo check apkgo-plugin
```
