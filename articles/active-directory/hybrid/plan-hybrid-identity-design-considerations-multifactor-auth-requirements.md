---
title: 混合标识设计 - 多重身份验证要求 Azure | Microsoft Docs
description: 借助条件性访问控制，Azure Active Directory 会在验证用户身份时先检查选取的特定条件，然后才允许访问应用程序。 一旦符合这些条件，用户就会通过身份验证并获权访问应用程序。
documentationcenter: ''
services: active-directory
author: billmath
manager: billmath
editor: ''
ms.assetid: 9c59fda9-47d0-4c7e-b3e7-3575c29beabe
ms.service: active-directory
ms.devlang: na
ms.topic: conceptual
ms.tgt_pltfrm: na
ms.workload: identity
ms.date: 07/18/2017
ms.subservice: hybrid
ms.author: billmath
ms.custom: seohack1
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3dabb381c16aa107e41c1d556e61e020b8c6a6c3
ms.sourcegitcommit: 301128ea7d883d432720c64238b0d28ebe9aed59
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/13/2019
ms.locfileid: "56170213"
---
# <a name="determine-multi-factor-authentication-requirements-for-your-hybrid-identity-solution"></a>确定混合标识解决方案的多重身份验证要求
在充斥移动性的当下，用户访问云中和任何设备中的数据和应用程序，确保该信息安全变得尤为重要。  每天都会有关于安全漏洞的新闻头条。  尽管并不能保证避免此类漏洞，但多重身份验证提供了额外的安全层，可帮助防止利用这些漏洞。
首先评估多重身份验证的组织要求。 即，组织要尝试保护的内容。  在针对设置和启用组织用户的多重身份验证确定技术要求时，此评估非常重要。

务必回答以下问题：

* 贵公司是否会尝试保护 Microsoft 应用安全？ 
* 如何发布这些应用？
* 贵公司是否会提供允许员工访问本地应用的远程访问？

如果是，是何种类型的远程访问？还需要评估要访问这些应用程序的用户将位于何处。 对定义正确的多重身份验证策略而言，此评估是另一个重要步骤。 务必回答以下问题：

* 用户将位于何处？
* 用户是否可以位于任何位置？
* 贵公司是否想要根据用户的位置建立限制？

在了解了这些要求后，还必须评估多重身份验证的用户的要求。 此评估非常重要，因为将针对推出多重身份验证定义要求。 务必回答以下问题：

* 用户是否熟悉多重身份验证？
* 某些使用是否需要提供额外的身份验证？  
  * 如果是，始终、从外部网络访问时、访问特定应用程序时，还是在其他情况下？
* 用户是否需要培训如何设置和实施多重身份验证？
* 什么是贵公司想要为其用户启用多重身份验证的关键方案？

在回答完上述问题后，能够了解本地是否存在已实施的多重身份验证。 在针对设置和启用组织用户的多重身份验证确定技术要求时，此评估非常重要。 务必回答以下问题：

* 贵公司是否需要使用 MFA 保护特权帐户？
* 贵公司出于合规性原因，是否需要为某些应用程序启用 MFA？
* 贵公司是否需要为这些应用程序的所有合格用户或仅管理员启用 MFA？
* 需要始终启用 MFA，还是仅当用户在公司网络之外登录时启用 MFA？

## <a name="next-steps"></a>后续步骤
[定义混合标识采用策略](plan-hybrid-identity-design-considerations-identity-adoption-strategy.md)

## <a name="see-also"></a>另请参阅
[设计注意事项概述](plan-hybrid-identity-design-considerations-overview.md)

