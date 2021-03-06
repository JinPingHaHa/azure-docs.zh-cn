---
title: 在 Microsoft 应用中启用领英集成 - Azure Active Directory | Microsoft Docs
description: 介绍如何为 Azure Active Directory 中的 Microsoft 应用启用或禁用 LinkedIn 集成
services: active-directory
author: curtand
manager: mtillman
ms.service: active-directory
ms.workload: identity
ms.subservice: users-groups-roles
ms.topic: article
ms.date: 01/31/2019
ms.author: curtand
ms.reviewer: beengen
ms.custom: it-pro
ms.collection: M365-identity-device-management
ms.openlocfilehash: d86b8dc271eead1196d946895ec7676935135cef
ms.sourcegitcommit: 301128ea7d883d432720c64238b0d28ebe9aed59
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/13/2019
ms.locfileid: "56202479"
---
# <a name="linkedin-integration"></a>领英集成

在本文中，你将了解如何在 Azure Active Directory (Azure AD) 管理中心内为租户启用或禁用领英集成。

> [!IMPORTANT]
> 我们目前正在推出适用于 Azure AD 租户的领英集成设置。 针对你的租户推出此功能后，默认会启用此功能。
> 
> 异常：
> * 此设置不适用于使用以下软件的客户：美国政府版 Microsoft 云、德国 Microsoft 云或者在中国通过 21Vianet 运营的 Azure 和 Office 365。
> * 对于在德国预配的租户，此设置默认为关闭。 请注意，此设置不适用于使用德国 Microsoft 云的客户。
> * 对于在法国预配的租户，此设置默认为关闭。

> 使用集成的前提是将其启用并让用户同意应用代表用户访问公司数据。 有关许可设置的信息，请参阅[如何删除用户对应用程序的访问权限](https://docs.microsoft.com/azure/active-directory/application-access-assignment-how-to-remove-assignment)。

## <a name="enable-or-disable-linkedin-integration-for-your-users-in-the-azure-portal"></a>在 Azure 门户中为用户启用或禁用领英集成

可以针对整个租户或者仅针对租户中的选定用户启用或禁用领英集成。

1. 使用 Azure AD 租户的全局管理员帐户登录到 [Azure Active Directory 管理中心](https://aad.portal.azure.com/)。
2. 选择“用户”。
3. 在“用户”边栏选项卡中，选择“用户设置”。
4. 在“领英集成”下：
  * 选择“是”可以为租户中的所有用户启用领英集成
  * 选择“选定”可以仅为选定的租户用户启用领英集成
  * 选择“否”可以为所有用户禁用领英集成 **** ![](./media/linkedin-integration/linkedin-integration.png)
5. 设置完成后，选择“保存”来保存设置。

## <a name="enable-or-disable-linkedin-integration-for-your-users-in-group-policy"></a>在组策略中为用户启用或禁用领英集成

1. 下载 [Office 2016 管理模板文件 (ADMX/ADML)](https://www.microsoft.com/download/details.aspx?id=49030)
2. 提取 ADMX 文件然后将其复制到中央存储。
3. 打开组策略管理。
4. 使用以下设置创建一个组策略对象：“用户配置” > “管理模板” > “Microsoft Office 2016” > “杂项” > “在 Office 应用程序中显示 LinkedIn 的功能”。
5. 选择“已启用”或“已禁用”。
  
 状态 | 效果
------ | ------
**已启用** | Office 2016“选项”中的“在 Office 应用程序中显示领英功能”设置已启用。 组织中的用户可以在其 Office 应用程序中使用领英功能。
 **已禁用** | Office 2016“选项”中的“在 Office 应用程序中显示领英功能”设置已禁用，最终用户不能更改此设置。 组织中的用户无法在其 Office 2016 应用程序中使用 LinkedIn 功能。

此组策略只会影响本地计算机上的 Office 2016 应用。 即使用户在其 Office 2016 应用中禁用了 LinkedIn，也能在整个 Office 365 的个人资料卡片中看到 LinkedIn 功能。

## <a name="learn-more"></a>了解详细信息

* [在组织中集成领英](linkedin-user-consent.md)

* [Microsoft 应用中的 LinkedIn 信息和功能](https://go.microsoft.com/fwlink/?linkid=850740)

* [LinkedIn 帮助中心](https://www.linkedin.com/help/linkedin)

## <a name="next-steps"></a>后续步骤

使用以下链接查看 Azure 门户中的当前 LinkedIn 集成设置：

[在 Azure 门户中查看当前的领英集成设置](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/UserManagementMenuBlade/UserSettings)
