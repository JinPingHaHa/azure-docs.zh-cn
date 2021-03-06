---
title: include 文件
description: include 文件
services: networking
author: jimdial
ms.service: networking
ms.topic: include
ms.date: 02/07/2019
ms.author: jdial
ms.custom: include file
ms.openlocfilehash: fe1993a914ea4d3bd8ab9116748198cbb0c1c43c
ms.sourcegitcommit: e51e940e1a0d4f6c3439ebe6674a7d0e92cdc152
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2019
ms.locfileid: "55904948"
---
<a name="virtual-networking-limits-classic"></a>以下限制仅适用于每个订阅通过经典部署模型托管的网络资源。 了解如何[针对订阅限制查看当前资源使用情况](../articles/networking/check-usage-against-limits.md)。

| 资源 | 默认限制 | 最大限制 |
| --- | --- | --- |
| 虚拟网络 |50 |100 |
| 本地网络站点 |20 |联系支持人员 |
| 每个虚拟网络的 DNS 服务器数 |20 |20 |
| 每个虚拟网络的专用 IP 地址数 |4096 |4096 |
| 虚拟机或角色实例的单 NIC 并发 TCP 或 UDP 流数 |500K |500K |
| 网络安全组 (NSG) |100 |200 |
| 每个 NSG 的 NSG 规则数 |200 |1000 |
| 用户定义路由表数 |100 |200 |
| 每个路由表的用户定义的路由数 |100 |400 |
| 公共 IP 地址 (动态) |5 |联系支持人员 |
| 保留的公共 IP 地址 |20 |联系支持人员 |
| 每个部署的公共 VIP |5 |联系支持人员 |
| 每个部署的私有 VIP (ILB) |1 |1 |
| 终结点访问控制列表 (ACL) |50 |50 |

#### <a name="azure-resource-manager-virtual-networking-limits"></a>网络限制 - Azure 资源管理器
以下限制仅适用于每个订阅按区域通过 Azure 资源管理器管理的网络资源。 了解如何[针对订阅限制查看当前资源使用情况](../articles/networking/check-usage-against-limits.md)。

> [!NOTE]
> 我们最近将所有默认限制提高到了最大限制。 如果没有**最大限制**列，则资源没有可调整的限制。 如果过去已通过客户支持提高了这些上限，因此看不到下述更新的限制，可[免费提交联机客户支持请求](../articles/azure-resource-manager/resource-manager-quota-errors.md)

| 资源 | 默认限制 | 
| --- | --- |
| 虚拟网络 |1000 |
| 每个虚拟网络的子网数 |3000 |
| 每个虚拟网络的虚拟网络对等互连数 |100 |
| 每个虚拟网络的 DNS 服务器数 |20 |
| 每个虚拟网络的专用 IP 地址数 |65536 |
| 每个网络接口的专用 IP 地址数 |256 |
| 每个虚拟机的专用 IP 地址数 |256 |
| 虚拟机或角色实例的单 NIC 并发 TCP 或 UDP 流数 |500K |
| 网络接口 (NIC) |65536 |
| 网络安全组 (NSG) |5000 |
| 每个 NSG 的 NSG 规则数 |1000 |
| 为安全组中的源或目标指定的 IP 地址和范围数 |4000 |
| 应用程序安全组 |3000 |
| 每个 IP 配置和每个 NIC 的应用程序安全组数 |20 |
| 每个应用程序安全组的 IP 配置数 |4000 |
| 可在网络安全组的所有安全规则中指定的应用程序安全组数 |100 |
| 用户定义路由表数 |200 |
| 每个路由表的用户定义的路由数 |400 |
| 每个 VPN 网关的点到站点根证书 |20 |
| 虚拟网络 TAP |100 |
| 每个虚拟网络 TAP 的网络接口 TAP 配置 |100 |

#### <a name="publicip-address"></a>公共 IP 地址限制
| 资源 | 默认限制 | 最大限制 |
| --- | --- | --- |
| 公共 IP 地址数 - 动态 |（基本）1000 |联系支持人员 |
| 公共 IP 地址数 - 静态 |（基本）200 |联系支持人员 |
| 公共 IP 地址数 - 静态 |（标准）200 |联系支持人员 |
| 公共 IP 前缀大小（预览版） | /28 | /28 |

#### <a name="load-balancer"></a>负载均衡器限制
以下限制仅适用于每个订阅按区域通过 Azure 资源管理器管理的网络资源。 了解如何[针对订阅限制查看当前资源使用情况](../articles/networking/check-usage-against-limits.md)

| 资源 | 默认限制 |
| --- | --- |
| 负载均衡器 | 1000 | 
| 每个资源的规则数，基本 | 250 |
| 每个资源的规则数，标准 | 1500 | 
| 每个 IP 配置的规则数 | 299 |
| 每个 NIC 的规则数 | 500 |
| 前端 IP 配置数，基本 | 200 |
| 前端 IP 配置数，标准 | 600 |
| 后端池数，基本 | 100，单个可用性集 |
| 后端池数，标准 | 1000，单个 VNet |
| 每个负载均衡器的后端资源数，标准* | 150 |
| HA 端口数，标准 | 每个内部前端 1 个 |

** 多达 150 种资源，独立虚拟机资源、可用性集资源和虚拟机规模集资源可任意组合。

