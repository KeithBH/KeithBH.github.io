---
layout: post
title:  "工业机器人通信与信息传递"
date:   2024-03-07 00:00:00 +0800
published:  False
---

# comet_rpc

[github项目链接](https://github.com/gavanderhoorn/comet_rpc)

简介（机翻）：这是一个围绕 JSON-RPC 接口的低级 Python 包装器，该接口由 FANUC 的 web 服务器的 COMET 扩展在 R-30iB 和 R-30iB+ 控制器上提供(即:V8及以上版本，尽管比V9早的版本有一个(非常)有限的接口)。COMET 被 iRProgrammer 和 FANUC 在其最新的控制器系列中提供的其他几个基于 web 的 ui 所使用。

我的理解：是个库，适用于 FANUC 机器人，可以获取、修改机器人的参数值。

使用前提与注意事项
* 机器人版本：最低 V8
* http://robot_ip 能 ping 通
* 作者多次强调：不要在实际的生产环境中使用
* 仅支持部分 RPC（85 个中的 32 个），详见项目介绍中的表格

## 安装

```Py
pip install -U pip
pip install -U wheel setuptools
pip install https://github.com/gavanderhoorn/comet_rpc/archive/0.2.4.tar.gz
```

## 使用

```Py
from comet_rpc import (
    exec_kcl,
    IoType,
    iogetpn,
    iovalrd,
    vmip_writeva,
)

# 机器人 IP
server = "..."

# 执行KCL（KAREL命令语言）命令以重置控制器
exec_kcl(server, "reset")
# 将 100 写入系统命名空间（"SYSTEM"）中的指定变量，即将 override 设为 100% （由于风险较大未实际运行）
vmip_writeva(server, "*SYSTEM*", "$MCR.$GENOVERRIDE", value=100)
# 获取数字输出 DI[1] 的值
dout1_val = iovalrd(server, IoType.DigitalOut, index=1).value
# 获取数字输出 DI[1] 的注释
dout1_cmt = iogetpn(server, IoType.DigitalOut, index=1).value

print(dout1_val) # 实测得到输出 0
print(dout1_cmt) # 实测得到输出 命令允许
```

## 延伸 & 进一步了解

### iRProgrammer

一种编辑机器人程序的工具，可以在 PC 和移动端等设备上运行，主要有三个方面的功能：
* 创建和编辑机器人程序
* 执行机器人程序
* 调整基础设置


### SON-RPC 接口

### COMET