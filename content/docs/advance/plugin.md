---
title: "插件"
weight: 1
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

## 插件

apkgo集成了插件系统，可以很方便的开发自己的更新发布流程

### 1. 开始

使用此<https://github.com/KevinGong2013/apkgo-plugin>模版，新建仓库

查看`publisher.go`文件

``` go
type CustomPublisher struct{}

func (cp *CustomPublisher) Name() string {
 return "custom_publisher"
}

func (p *CustomPublisher) Do(req shared.PublishRequest) error {

 r := rand.Intn(10)
 time.Sleep(time.Second * time.Duration(10+r))

 if r%2 == 0 {
  return fmt.Errorf("upload %s failed", req.AppName)
 }

 return nil
}
```

只需要根据自己的业务逻辑及需求实现接口`shared.Publisher`即可

### 2. 打包

```shell
go build . -o ./apkgo-plugin-name
```

> 可以参考apkgo项目使用 `goreleaser` 打包及发布

### 3. 握手信息配置

打开`$APKGO_HOME/secrets/stores_config.json`文件添加如下配置

```jsonc
{
    "stores"{
        ...
        "oppo": {},
        // key 为插件名称
        "apkgo-demo": {
            // 以下三项的至依赖于 main.go 中的配置信息
            "version": "23",
            "magic_cookie_key": "",
            "magic_cookie_value": "",

            // 团队其他成员可见用于提示安装插件
            "home_page": "kevin",
            "author": "kevin"
        }
    }
}
```

### 2. 配置插件路径

打开`APKGO_HOME/config.yaml`文件，添加如下配置

``` yaml
# 示例忽略掉
storage:
    location: local
# 主要是以下节点的配置
plugins:
      # apkgo 插件名称
    - name: apkgo-plugin
      # 插件在本地的路径
      path: path/to/your/apk-plugin
```

### 3. 验证

```shell
apkgo check apkgo-plugin
```
