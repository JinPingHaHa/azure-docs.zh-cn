---
title: 购买 SUSE Linux 计划 - Azure 预留 | Microsoft Docs
description: 了解如何为使用的 SUSE 预付费，并节省即用即付成本。
services: virtual-machines-linux
documentationcenter: ''
author: yashesvi
manager: yashesvi
editor: ''
ms.service: virtual-machines-linux
ms.devlang: na
ms.topic: conceptual
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 01/18/2019
ms.author: yashar
ms.openlocfilehash: 4f70a34febcf0b39d051053a6ddd9abe5c9a6726
ms.sourcegitcommit: 947b331c4d03f79adcb45f74d275ac160c4a2e83
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/05/2019
ms.locfileid: "55745973"
---
# <a name="prepay-for-suse-software-plans-from-azure-reservations"></a>通过 Azure 预留为 SUSE 软件计划预付费

为使用的 SUSE 预付费，并节省即用即付成本。 折扣仅适用于 SUSE 计量，而不适用于虚拟机使用情况。 可以单独购买虚拟机预留，以节省更多成本。

可以在 Azure 门户中购买 SUSE 软件计划。 若要购买计划：

- 你必须至少具有一个企业或即用即付订阅的所有者角色。
- 对于企业订阅，必须在 [EA 门户](https://ea.azure.com)中启用“添加预留实例”。 或者，如果禁用了该设置，则你必须是订阅的 EA 管理员。
- 对于云解决方案提供商 (CSP) 计划，管理代理或销售代理可以购买 SUSE 计划。

## <a name="buy-a-suse-software-plan"></a>购买 SUSE 软件计划

1. 在 Azure 门户中转到[预留](https://portal.azure.com/#blade/Microsoft_Azure_Reservations/ReservationsBrowseBlade)。
1. 选择“添加”并选择 SUSE Linux。
1. 填写必填字段。 与所购买计划的属性匹配的任何 SUSE Linux VM 都可以获得折扣。 实际获得折扣的部署数取决于所选范围和数量。

    | 字段      | 说明|
    |:------------|:--------------|
    |Name        |此购买的名称。|
    |订阅|用于支付此计划的订阅。 将向订阅的付款方式收取预订的预付费用。 订阅类型必须为企业协议（套餐编号：MS-AZR-0017P 或 MS-AZR-0148P）或即用即付（套餐编号：MS-AZR-0003P 或 MS-AZR-0023P）。 对于企业订阅，从注册的货币承诺余额中扣除费用或作为超额收取费用。 对于即用即付订阅，将向订阅的信用卡或发票付款方式收取费用。|
    |范围       |范围可以包含一个订阅或多个订阅（共享范围）。 如果选择： <ul><li>单个订阅 - 计划折扣将应用到此订阅中的 SUSE Linux 使用情况。 </li><li>共享 - 计划折扣将应用到计费上下文中任何订阅中的 SUSE Linux 使用情况。 对于企业客户，共享范围是注册范围，包括注册中的所有订阅。 对于即用即付客户，共享范围是由帐户管理员创建的所有即用即付订阅。</li></ul>|
    |软件计划     |选择 SUSE Linux 计划。 有关确定要购买计划的帮助，请参阅[了解如何应用 SUSE Linux Enterprise 软件预留折扣](../../billing/billing-understand-suse-reservation-charges.md)。|
    |VM 大小     |SUSE Linux 定价取决于 VM 上的 vCPU 数量。 选择可表示 SUSE Linux VM 上的 vCPU 数量的选项。|
    |术语        |一年或三年。|
    |数量    |购买此 SUSE Linux 计划的目标 VM 数量。 数量是可以获得计费折扣的正在运行的 SUSE Linux 实例数。|
1. 选择“购买”。
1. 选择“查看此预订”以查看购买的状态。

预留折扣自动应用于匹配预留的任何正在运行的 SUSE 虚拟机。 折扣仅适用于 SUSE 计量。 此计划不涵盖 VM 计算费用。

## <a name="discount-applies-to-different-vm-sizes-with-instance-size-flexibility"></a>折扣适用于具有实例大小灵活性的不同大小的 VM

与预留的 VM 实例一样，SUSE Linux 计划提供了实例大小的灵活性。 这意味着，即使你部署的 VM 与你购买的 SUSE 计划的大小不同，折扣也同样适用。 有关详细信息，请参阅[了解如何应用 SUSE Linux Enterprise 软件预留折扣](../../billing/billing-understand-suse-reservation-charges.md)。

## <a name="cancellation-and-exchanges-not-allowed"></a>不允许取消和交换

无法取消和交换已购买的 SUSE 计划。 请检查你的使用情况，确保购买的是正确的计划。 有关确定要购买计划的帮助，请参阅[了解如何应用 SUSE Linux Enterprise 软件预留折扣](../../billing/billing-understand-suse-reservation-charges.md)。

## <a name="next-steps"></a>后续步骤

若要了解如何管理预留，请参阅[管理 Azure 预留](../../billing/billing-manage-reserved-vm-instance.md)。

若要了解更多信息，请参阅下列文章：

- [什么是 Azure 预订？](../../billing/billing-save-compute-costs-reservations.md)
- [管理 Azure 中的预留](../../billing/billing-manage-reserved-vm-instance.md)
- [了解如何应用 SUSE 预留折扣](../../billing/billing-understand-suse-reservation-charges.md)
- [了解即用即付订阅的预留使用情况](../../billing/billing-understand-reserved-instance-usage.md)
- [了解企业合约的预留使用情况](../../billing/billing-understand-reserved-instance-usage-ea.md)

## <a name="need-help-contact-us"></a>需要帮助？ 请联系我们。

如有任何疑问或需要帮助，请[创建支持请求](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest)。