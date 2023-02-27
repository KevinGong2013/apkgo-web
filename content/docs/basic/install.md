---
title: "安装"
weight: 1
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

## 安装

apkgo使用Go语言开发，几乎支持所有的常见平台。

- ### 包管理器安装

[Homebrew](https://brew.sh) is a free and open source package manager for macOS and Linux. This will install apkgo:

``` shell
brew tap kevingong2013/tap
brew install apkgo
```

- ### 预编译版

常见系统均可以前往[Github Release](https://github.com/KevinGong2013/apkgo/releases),下载安装包进行安装。

- ### Docker

From scratch only 4mb

``` shell
docker pull kevingong2013/apkgo
```

- ### Build from source

To build apkgo from source you must:

1. install[Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
2. Install[Go](https://go.dev/doc/install) version 1.21 or later

> The install directory is controlled by the GOPATH and GOBIN environment variables. If GOBIN is set, binaries are installed to that directory. If GOPATH is set, binaries are installed to the bin subdirectory of the first directory in the GOPATH list. Otherwise, binaries are installed to the bin subdirectory of the default GOPATH ($HOME/go or %USERPROFILE%\go).

Then build and test:

``` shell
go install github.com/KevinGong2013/apkgo@latest
apkgo --help

```
