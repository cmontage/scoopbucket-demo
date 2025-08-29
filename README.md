<h1 align="center">Scoop Bucket All In One</h1>

<p align="center"><img src="https://gcore.jsdelivr.net/gh/cmontage/scoopbucket@main/bin/scoop-ico.png" width="100" alt="Scoop Logo"></p>

将 Scoop 官方的 Bucket 库整合成一个 Bucket，每日同步，便于自用。

Consolidate Scoop's official Bucket library into one Bucket that is synchronized daily for easy self-use.

## 介绍

同时包含了 Scoop 官方的十个应用库：main、extras、versions、nirsoft、sysinternals、php、nerd-fonts、nonportable、java、games（可使用命令 `scoop bucket known` 查看）。

本应用库每天自动更新一次。

## 如何使用
### 第一次使用 Scoop（已安装请忽略）

1. [PowerShell](https://learn.microsoft.com/zh-cn/powershell/) 版本在 5.1 或以上这条不用看了，如果没有 PowerShell 大于 5.1 版本，可以下载安装 [PowerShell Core](https://github.com/PowerShell/PowerShell)。运行以下命令查看：

```powershell
$PSVersionTable.PSVersion.Major # should be >= 5.1
```

2. 之后请根据 [官方教程](https://github.com/ScoopInstaller/Install#readme) 安装 Scoop，建议自定义安装目录，以下为我建议的安装操作 **（该安装使用我自建的 Scoop 源，自动代理无法访问资源以及默认内置本仓库的 official bucket。详情可以看[这里](https://github.com/cmontage/scoop)）**

```powershell
# 设置 PowerShell 执行策略（非管理员启动）
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

# 下载安装脚本到本地
irm https://gitee.com/cmontage/scoop/raw/master/install.ps1 -outfile 'install.ps1'

# 自定义 Scoop 安装目录，以下是我的路径例子，你可以自己根据情况修改
# 可以不设全局文件夹ScoopGlobalDir，全局文件夹里的应用需要管理员权限
.\install.ps1 -ScoopDir 'D:\Apps\Scoop\ScoopApps' -ScoopGlobalDir 'D:\Apps\Scoop\ScoopApps-G' -NoProxy

# 下载 7zip git，因为我们之后如果要添加别的 Bucket，必须有 git、7zip
scoop install 7zip git
```
### 已安装 Scoop

> [!CAUTION]
> 确保你已经安装了 Scoop ！
>
> 输入 scoop -V 命令查看 Scoop 版本

1. 添加本仓库 bucket，运行命令

    ```powershell
    scoop bucket add official https://gitee.com/cmontage/scoopbucket

    # 如果需要移除本仓库
    scoop bucket rm official
    ```

3. 下载几个基本的应用，**注意使用代理最好不要用aria2**

    ```powershell
    # 下载 7zip git sudo dark innounp ...
    scoop install official/7zip official/git official/aria2 official/sudo official/dark official/innounp 
    ```

4. 替换自带的 scoop search，因为自带的比较慢

    ```powershell
    scoop install official/scoop-search

    # 使用 scoop-search ，例如
    scoop-search 7zip
    ```

> [!TIP]
>
> 如果你之前添加过其他 bucket 并下载过应用，你希望他们全部或者部分使用本仓库来进行更新。那么你需要在 app 安装后的 apps\current 路径下的 install.json 的 bucket 项的值改为 official。然后运行 scoop list 来检查是否替换成功。
>
> 如果要批量修改，直接 vscode 搜索替换大法。



## 安装应用

搜索应用：

```powershell
scoop-search APPNAME
```

安装应用：

```powershell
scoop install official/APPNAME
```

## 查看帮助

要了解 Scoop 的更多用法，请查看 [Scoop Wiki](https://github.com/ScoopInstaller/Scoop/wiki)。或运行命令查看简要的帮助：

```powershell
scoop help
```
