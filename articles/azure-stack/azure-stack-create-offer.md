---
title: 在 Azure Stack 中创建套餐 | Microsoft Docs
description: 作为云管理员，了解如何在 Azure Stack 中为用户创建套餐。
services: azure-stack
documentationcenter: ''
author: sethmanheim
manager: femila
editor: ''
ms.service: azure-stack
ms.workload: na
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: conceptual
ms.date: 03/07/2019
ms.author: sethm
ms.reviewer: efemmano
ms.lastreviewed: 03/07/2019
ms.openlocfilehash: 59c69477e120facec1fbf132ce7017ca21aa8748
ms.sourcegitcommit: 2d0fb4f3fc8086d61e2d8e506d5c2b930ba525a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/18/2019
ms.locfileid: "58092610"
---
# <a name="create-an-offer-in-azure-stack"></a>在 Azure Stack 中创建套餐

[套餐](azure-stack-key-features.md)是提供者提供给用户购买或订阅的一个或多个计划的组合。 本文介绍如何创建包含[创建的计划](azure-stack-create-plan.md)的套餐。 订阅方可以使用此套餐设置虚拟机 (VM)。

## <a name="create-an-offer-1902-and-later"></a>创建产品/服务 （1902年和更高版本）

1. 登录到[Azure Stack 管理员门户](https://adminportal.local.azurestack.external)，然后选择 **+ 创建资源**，然后**产品/服务 + 计划**，然后**提供**。

   ![创建产品](media/azure-stack-create-offer/offers.png)

2. 将显示选项卡式的用户界面，可用于定义产品/服务名称，并添加现有项或创建新的基本计划和外接程序计划。 最重要的是，你可以查看创建之前你决定创建它的产品/服务的详细信息。

   在中**基础知识**选项卡上，在**新建产品/服务**，输入**显示名称**和一个**资源名称**，然后在**资源组**，选择**新建**或**使用现有**。 显示名称是套餐的易记名称。 此友好名称，是关于用户在他们所订阅产品/服务在用户门户时看到的产品/服务的唯一信息。 请使用直观名称，以帮助用户了解该套餐附带了什么功能。 只有管理员可以看到资源名称。 管理员使用此名称将该产品/服务作为 Azure 资源管理器资源处理。 在此选项卡上，您还可以公开此产品/服务或将它专用的保留默认值。 你可以[更改产品/服务的公共或私有状态](#change-the-state-of-an-offer)更高版本，因此也。

   ![新建产品/服务](media/azure-stack-create-offer/new-offer.png)
  
3. 选择**基本计划**选项卡。选择想要包括在产品/服务的计划。

   ![选择计划](media/azure-stack-create-offer/select-plan.png)

4. 此时可以创建附加计划来修改基本计划，但这是可选的。 我们将在下一篇文章中，创建附加计划[Azure Stack 的附加计划](create-add-on-plan.md)。

5. 选择**查看 + 创建**选项卡。查看产品/服务摘要以确保所有值都都正确。 接口使你可以在所选计划中，一次，可在计划中，查看每个配额的详细信息，并返回一个地进行任何必要的编辑扩展配额。

6. 选择**创建**创建产品/服务。

   ![查看并创建](media/azure-stack-create-offer/review-offer.png)

### <a name="change-the-state-of-an-offer"></a>更改产品/服务的状态

创建套餐后，可以更改其状态。 必须将套餐设为“公共”，用户才能在订阅时获得完整视图。 产品/服务可以是：

- **公共**：对用户可见。
- **专用**：仅对云管理员可见。 起草计划或套餐时，或者当云管理员想要[为用户创建每个订阅](azure-stack-subscribe-plan-provision-vm.md#create-a-subscription-as-a-cloud-operator)时，此设置非常有用。
- **已解除授权**：已对新订阅方关闭。 云管理员可以解除套餐的授权来防止将来订阅，但不影响当前订阅方。

  > [!TIP]  
  > 产品/服务的更改不会对用户立即可见。 若要查看所做的更改，用户可能需要先注销，然后重新登录到用户门户，这样才能看到新的套餐。

有两种方法，若要更改产品/服务的状态：

1. 在中**的所有资源**，选择产品/服务的名称。 上**概述**屏幕上的产品/服务，选择**更改状态**。 选择你想要使用的状态 (例如，**公共**)。

   ![选择状态](media/azure-stack-create-offer/change-state.png)

2. 在中**的所有资源**，选择产品/服务的名称。 然后选择**产品/服务设置**。 选择你想要使用的状态 (例如，**公共**)，然后选择**保存**。

   ![选择辅助功能状态](media/azure-stack-create-offer/offer-settings.png)

## <a name="create-an-offer-1901-and-earlier"></a>创建产品/服务 （1901年及更早版本）

1. 登录到 [Azure Stack 管理员门户](https://adminportal.local.azurestack.external)，依次选择“+ 创建资源”、“租户套餐 + 计划”、“套餐”。

   ![创建产品](media/azure-stack-create-offer/image01.png)
  
2. 在“新建套餐”下，输入“显示名称”和“资源名称”，然后在“资源组”下选择“新建”或“使用现有项”。 显示名称是套餐的易记名称。 此易记名称是用户在订阅套餐时可看到的有关该套餐的唯一信息。 请使用直观名称，以帮助用户了解该套餐附带了什么功能。 只有管理员可以看到资源名称。 管理员使用此名称将该产品/服务作为 Azure 资源管理器资源处理。

   ![新建产品/服务](media/azure-stack-create-offer/image01a.png)
  
3. 选择“基本计划”打开“计划”。 选择要包含在套餐中的计划，然后选择“选择”。 若要创建套餐，请选择“创建”。

   ![选择计划](media/azure-stack-create-offer/image02.png)
  
4. 创建套餐后，可以更改其状态。 必须将套餐设为“公共”，用户才能在订阅时获得完整视图。 产品/服务可以是：

   - **公共**：对用户可见。
   - **专用**：仅对云管理员可见。 起草计划或套餐时，或者当云管理员想要[为用户创建每个订阅](azure-stack-subscribe-plan-provision-vm.md#create-a-subscription-as-a-cloud-operator)时，此设置非常有用。
   - **已解除授权**：已对新订阅方关闭。 云管理员可以解除套餐的授权来防止将来订阅，但不影响当前订阅方。

   > [!TIP]  
   > 产品/服务的更改不会对用户立即可见。 若要查看所做的更改，用户可能需要先注销，然后重新登录到用户门户，这样才能看到新的套餐。

   在套餐的概览屏幕上，选择“辅助功能状态”。 选择要使用的状态（例如“公共”），然后选择“保存”。

     ![选择状态](media/azure-stack-create-offer/change-stage-1807.png)

     或者，选择“更改状态”，然后选择状态。

    ![选择辅助功能状态](media/azure-stack-create-offer/change-stage-select-1807.png)

> [!NOTE]
> 还可以使用 PowerShell 来创建默认套餐、计划和配额。 有关详细信息，请参阅 [Azure Stack PowerShell 模块 1.4.0](/powershell/azure/azure-stack/overview?view=azurestackps-1.4.0)。

## <a name="next-steps"></a>后续步骤

- [创建订阅](azure-stack-subscribe-plan-provision-vm.md)
- [预配虚拟机](azure-stack-provision-vm.md)
