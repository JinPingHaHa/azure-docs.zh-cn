---
title: include 文件
description: include 文件
services: vpn-gateway
author: cherylmc
ms.service: vpn-gateway
ms.topic: include
ms.date: 02/01/2019
ms.author: cherylmc
ms.custom: include file
ms.openlocfilehash: deabef0c2c3540e515fe72a161710c95a20fa86f
ms.sourcegitcommit: 79038221c1d2172c0677e25a1e479e04f470c567
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2019
ms.locfileid: "56418054"
---
使用提升的权限打开 PowerShell 控制台。



如果要在本地运行 Azure PowerShell，请连接到 Azure 帐户。 Connect-AzureRmAccount cmdlet 会提示输入凭据。 进行身份验证后，它会下载帐户设置，以便 Azure PowerShell 可以使用这些设置。 如果未在本地运行 PowerShell，而是在浏览器中使用 Azure Cloud Shell“试用”，请跳过此第一步。 你将自动连接到 Azure 帐户。

```azurepowershell
Connect-AzAccount
```

如果有多个订阅，请获取 Azure 订阅的列表。

```azurepowershell-interactive
Get-AzSubscription
```

指定要使用的订阅。

```azurepowershell-interactive
Select-AzSubscription -SubscriptionName "Name of subscription"
```