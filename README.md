# OpenWrt Plus 23.05

### 固件为主路由：mosdns sing-box fakeip 集成使用

#### 食用方法：

正常连网联网之后：

mosdns：请选择自定义规则，默认端口`53`，请将 网络-dhcp/dns里的 端口修改为`任意` 并将`hosts和解析文件`里的`忽略解析文件`勾选
请将自定义规则里的`forward_remote`的地址修改为你的 `sing-box`入站地址 默认应该`主路由:6666`
添加`白名单`即是直连
添加`黑名单`即是发送远程sing-box代理

``` shell
wget https://file.herozmy.com/File/router/openwrt/op.sh && bash op.sh
```
根据提示执行脚本

脚本正常执行无报错，手动将命令写入：系统-启动项-本地启动脚本   exit 0 上方
```
nohup  /usr/bin/sing-box run -c /etc/sing-box/config.json > /tmp/sbstart.log 2>&1

```

### NanoPi R4S/R5S/R5C & X86_64 固件下载:

https://github.com/pmkol/openwrt-plus/releases

```
【首次登陆】
地址：10.0.0.1（默认）
用户：root
密码：空

【分区挂载】
系统/磁盘管理 将系统盘剩余空间创建新分区
系统/挂载点   启用新分区并挂载至/opt目录
```

---------------

#### 固件编译脚本存档来自：https://init2.cooluc.com

- 优化系统内核
  - [x] Full cone NAT
  - [x] TCP BBRv3
  - [x] TCP Brutal
  - [x] LLVM-BPF
  - [x] Shortcut-FE
- 使用 OpenWrt+ImmortalWrt 软件源，支持更多插件的在线安装与升级
- 最小化集成常用插件，修复多处上游插件BUG

自定义预装插件建议fork上游原项目，以免因本项目未及时同步导致编译失败

---------------

### 更改 LAN IP 地址
##### 自定义默认 LAN IP 地址
##### 只需在构建固件前执行以下命令即可覆盖默认 LAN 地址（默认：10.0.0.1）

```
export LAN=10.0.0.1
```

# 使用 Github Actions 构建

### 一、Fork 本仓库到自己 GitHub 存储库

### 二、构建固件
- 在存储库名称下，单击（<img src="https://camo.githubusercontent.com/392391d290482f9c4881912eec0700ec2acef8e0d5d2e24b3f8b23d9354fa73e/68747470733a2f2f66696c652e636f6f6c75632e636f6d2f323232322e737667" alt="Actions"> Actions）。
  
- 在左侧边栏中，单击要运行的工作流的名称：**Build releases**。
  
- 在工作流运行的列表上方，单击“**Run workflow**”按钮，选择要构建的设备固件并运行工作流。
  
  ![image](https://github.com/sbwml/r4s_build_script/assets/16485166/136abcd1-ecf3-4e6d-aa1a-5393a75a25cc)
