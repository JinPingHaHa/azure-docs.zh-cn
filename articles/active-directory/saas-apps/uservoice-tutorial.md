---
title: 教程：Azure Active Directory 与 UserVoice 集成 | Microsoft Docs
description: 了解如何在 Azure Active Directory 与 UserVoice 之间配置单一登录。
services: active-directory
documentationCenter: na
author: jeevansd
manager: daveba
ms.reviewer: joflore
ms.assetid: 684a405b-8932-46f6-b43a-4d97a42b6b87
ms.service: active-directory
ms.subservice: saas-app-tutorial
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 07/21/2017
ms.author: jeedes
ms.collection: M365-identity-device-management
ms.openlocfilehash: 94e077e07796fc111c35b6571459a5e316096ebc
ms.sourcegitcommit: 301128ea7d883d432720c64238b0d28ebe9aed59
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/13/2019
ms.locfileid: "56206627"
---
# <a name="tutorial-azure-active-directory-integration-with-uservoice"></a>教程：Azure Active Directory 与 UserVoice 集成

本教程介绍如何将 UserVoice 与 Azure Active Directory (Azure AD) 集成。

将 UserVoice 与 Azure AD 集成提供以下优势：

- 可以在 Azure AD 中控制谁有权访问 UserVoice
- 可让用户通过其 Azure AD 帐户自动登录 UserVoice（单一登录）
- 可在中心位置（即 Azure 门户）管理帐户。

如需了解有关 SaaS 应用与 Azure AD 集成的详细信息，请参阅 [Azure Active Directory 的应用程序访问与单一登录是什么](../manage-apps/what-is-single-sign-on.md)。

## <a name="prerequisites"></a>先决条件

若要配置 Azure AD 与 UserVoice 的集成，需备齐以下项目：

- Azure AD 订阅
- 已启用 UserVoice 单一登录的订阅

> [!NOTE]
> 为了测试本教程中的步骤，我们不建议使用生产环境。

测试本教程中的步骤应遵循以下建议：

- 除非必要，请勿使用生产环境。
- 如果没有 Azure AD 试用环境，可以[获取一个月的试用版](https://azure.microsoft.com/pricing/free-trial/)。

## <a name="scenario-description"></a>方案描述
在本教程中，将在测试环境中测试 Azure AD 单一登录。 本教程中概述的方案包括两个主要构建基块：

1. 从库添加 UserVoice
1. 配置和测试 Azure AD 单一登录

## <a name="adding-uservoice-from-the-gallery"></a>从库添加 UserVoice
要配置 UserVoice 与 Azure AD 的集成，需要从库中将 UserVoice 添加到托管 SaaS 应用列表。

**若要从库中添加 UserVoice，请执行以下步骤：**

1. 在 **[Azure 门户](https://portal.azure.com)** 的左侧导航面板中，单击“Azure Active Directory”图标。 

    ![“Azure Active Directory”按钮][1]

1. 导航到“企业应用程序”。 然后转到“所有应用程序”。

    ![“企业应用程序”边栏选项卡][2]
    
1. 若要添加新应用程序，请单击对话框顶部的“新建应用程序”按钮。

    ![“新增应用程序”按钮][3]

1. 在搜索框中键入 **UserVoice**，在结果面板中选择“UserVoice”，并单击“添加”按钮添加该应用程序。

    ![结果列表中的 UserVoice](./media/uservoice-tutorial/tutorial_uservoice_addfromgallery.png)

## <a name="configure-and-test-azure-ad-single-sign-on"></a>配置和测试 Azure AD 单一登录

在本部分中，基于一个名为“Britta Simon”的测试用户使用 UserVoice 配置和测试 Azure AD 单一登录。

若要运行单一登录，Azure AD 需要知道与 Azure AD 用户相对应的 UserVoice 用户。 换句话说，需要建立 Azure AD 用户与 UserVoice 中相关用户之间的链接关系。

可通过将 Azure AD 中“用户名”的值指定为 UserVoice 中“用户名”的值来建立关联关系。

若要配置和测试 UserVoice 的 Azure AD 单一登录，需要完成以下构建基块：

1. **[配置 Azure AD 单一登录](#configure-azure-ad-single-sign-on)** - 使用户能够使用此功能。
1. **[创建 Azure AD 测试用户](#create-an-azure-ad-test-user)** - 使用 Britta Simon 测试 Azure AD 单一登录。
1. **[创建 UserVoice 测试用户](#create-a-uservoice-test-user)** - 在 UserVoice 中创建 Britta Simon 的对应用户，并将其链接到该用户的 Azure AD 表示形式。
1. **[分配 Azure AD 测试用户](#assign-the-azure-ad-test-user)** - 使 Britta Simon 能够使用 Azure AD 单一登录。
1. **[测试单一登录](#test-single-sign-on)** - 验证配置是否正常工作。

### <a name="configure-azure-ad-single-sign-on"></a>配置 Azure AD 单一登录

在本部分中，将介绍如何在 Azure 门户中启用 Azure AD 单一登录并在 UserVoice 应用程序中配置单一登录。

**若要配置 UserVoice 的 Azure AD 单一登录，请执行以下步骤：**

1. 在 Azure 门户中，在 **UserVoice** 应用程序集成页上，单击“单一登录”。

    ![配置单一登录链接][4]

1. 在“单一登录”对话框中，选择“基于 SAML 的单一登录”作为“模式”以启用单一登录。
 
    ![“单一登录”对话框](./media/uservoice-tutorial/tutorial_uservoice_samlbase.png)

1. 在“UserVoice 域和 URL”部分中，执行以下步骤：

    ![UserVoice 域和 URL 单一登录信息](./media/uservoice-tutorial/tutorial_uservoice_url.png)

    a. 在“登录 URL”文本框中，使用以下模式键入 URL： `https://<tenantname>.UserVoice.com`

    b. 在“标识符”文本框中，使用以下模式键入 URL：`https://<tenantname>.UserVoice.com`

    > [!NOTE] 
    > 这些不是实际值。 必须使用实际登录 URL 和标识符更新这些值。 请联系 [UserVoice 客户端支持团队](https://www.uservoice.com/)获取这些值。

1. 在“SAML 签名证书”部分中，复制证书的“指纹”值。

    ![证书下载链接](./media/uservoice-tutorial/tutorial_uservoice_certificate.png) 

1. 单击“保存”按钮。

    ![配置单一登录“保存”按钮](./media/uservoice-tutorial/tutorial_general_400.png)

1. 在“UserVoice 配置”部分，单击“配置 UserVoice”打开“配置登录”窗口。 从“快速参考”部分中复制“注销 URL 和 SAML 单一登录服务 URL”。

    ![UserVoice 配置](./media/uservoice-tutorial/tutorial_uservoice_configure.png) 

1. 在其他 Web 浏览器窗口中，以管理员身份登录到 UserVoice 公司站点。

1. 在顶部工具栏中，单击“设置”，并从菜单中选择“Web 门户”。
   
    ![应用端上的“设置”部分](./media/uservoice-tutorial/ic777519.png "设置")

1. 在“Web 门户”选项卡的“用户身份验证”部分中，单击“编辑”以打开“编辑用户身份验证”对话框页
   
    ![Web 门户选项卡](./media/uservoice-tutorial/ic777520.png "Web 门户")

1. 在“编辑用户身份验证”对话框页上，执行以下步骤：
   
    ![编辑用户身份验证](./media/uservoice-tutorial/ic777521.png "编辑用户身份验证")
   
    a. 单击“单一登录(SSO)”。
 
    b. 在“SSO 远程登录”文本框中，粘贴从 Azure 门户复制的“SAML 单一登录服务 URL”值。

    c. 在“SSO 远程注销”文本框中，粘贴从 Azure 门户复制的“注销 URL”值。
 
    d. 在“当前证书 SHA1 指纹”文本框中，粘贴从 Azure 门户复制的“指纹”值  **** 。
    
    e. 单击“保存身份验证设置”。

> [!TIP]
> 之后在设置应用时，就可以在 [Azure 门户](https://portal.azure.com)中阅读这些说明的简明版本了！  从“Active Directory”>“企业应用程序”部分添加此应用后，只需单击“单一登录”选项卡，即可通过底部的“配置”部分访问嵌入式文档。 可在此处阅读有关嵌入式文档功能的详细信息：[Azure AD 嵌入式文档]( https://go.microsoft.com/fwlink/?linkid=845985)
> 

### <a name="create-an-azure-ad-test-user"></a>创建 Azure AD 测试用户

本部分的目的是在 Azure 门户中创建名为 Britta Simon 的测试用户。

   ![创建 Azure AD 测试用户][100]

**若要在 Azure AD 中创建测试用户，请执行以下步骤：**

1. 在 Azure 门户的左窗格中，单击“Azure Active Directory”按钮。

    ![“Azure Active Directory”按钮](./media/uservoice-tutorial/create_aaduser_01.png)

1. 若要显示用户列表，请转到“用户和组”，然后单击“所有用户”。

    ![“用户和组”以及“所有用户”链接](./media/uservoice-tutorial/create_aaduser_02.png)

1. 若要打开“用户”对话框，在“所有用户”对话框顶部单击“添加”。

    ![“添加”按钮](./media/uservoice-tutorial/create_aaduser_03.png)

1. 在“用户”对话框中，执行以下步骤：

    ![“用户”对话框](./media/uservoice-tutorial/create_aaduser_04.png)

    a. 在“姓名”框中，键入“BrittaSimon”。

    b. 在“用户名”框中，键入用户 Britta Simon 的电子邮件地址。

    c. 选中“显示密码”复选框，然后记下“密码”框中显示的值。

    d. 单击“创建”。
 
### <a name="create-a-uservoice-test-user"></a>创建 UserVoice 测试用户

为了使 Azure AD 用户能够登录到 UserVoice，必须将其预配到 UserVoice 中。 对于 UserVoice，需要手动执行预配。

### <a name="to-provision-a-user-account-perform-the-following-steps"></a>若要预配用户帐户，请执行以下步骤：
1. 登录到 **UserVoice** 租户。

1. 转到“设置”。
   
    ![设置](./media/uservoice-tutorial/ic777811.png "设置")

1. 单击“常规”。

1. 单击“代理和权限”。
   
    ![代理和权限](./media/uservoice-tutorial/ic777812.png "代理和权限")

1. 单击“添加管理员”。
   
    ![添加管理员](./media/uservoice-tutorial/ic777813.png "添加管理员")

1. 在“邀请管理员”对话框中，执行以下步骤：
   
    ![邀请管理员](./media/uservoice-tutorial/ic777814.png "邀请管理员")
   
    a. 在“电子邮件”文本框中，键入要预配帐户的电子邮件地址，并单击“添加”。
   
    b. 单击“邀请”。

> [!NOTE]
> 可以使用 UserVoice 提供的任何其他 UserVoice 用户帐户创建工具或 API 来预配 AAD 用户帐户。

### <a name="assign-the-azure-ad-test-user"></a>分配 Azure AD 测试用户

在本部分中，通过授予 Britta Simon 访问 UserVoice 的权限，允许她使用 Azure 单一登录。

![分配用户角色][200] 

**若要将 Britta Simon 分配到 UserVoice，请执行以下步骤：**

1. 在 Azure 门户中打开应用程序视图，导航到目录视图，接着转到“企业应用程序”，并单击“所有应用程序”。

    ![分配用户][201] 

1. 在应用程序列表中，选择“UserVoice”。

    ![应用程序列表中的 UserVoice 链接](./media/uservoice-tutorial/tutorial_uservoice_app.png)  

1. 在左侧菜单中，单击“用户和组”。

    ![“用户和组”链接][202]

1. 单击“添加”按钮。 然后在“添加分配”对话框中选择“用户和组”。

    ![“添加分配”窗格][203]

1. 在“用户和组”对话框的“用户”列表中，选择“Britta Simon”。

1. 在“用户和组”对话框中单击“选择”按钮。

1. 在“添加分配”对话框中单击“分配”按钮。
    
### <a name="test-single-sign-on"></a>测试单一登录

在本部分中，使用访问面板测试 Azure AD 单一登录配置。

单击“访问面板”中的 UserVoice 磁贴时，应会自动登录到 UserVoice 应用程序。
有关访问面板的详细信息，请参阅 [Introduction to the Access Panel](../user-help/active-directory-saas-access-panel-introduction.md)（访问面板简介）。 

## <a name="additional-resources"></a>其他资源

* [有关如何将 SaaS 应用与 Azure Active Directory 集成的教程列表](tutorial-list.md)
* [Azure Active Directory 的应用程序访问与单一登录是什么？](../manage-apps/what-is-single-sign-on.md)



<!--Image references-->

[1]: ./media/uservoice-tutorial/tutorial_general_01.png
[2]: ./media/uservoice-tutorial/tutorial_general_02.png
[3]: ./media/uservoice-tutorial/tutorial_general_03.png
[4]: ./media/uservoice-tutorial/tutorial_general_04.png

[100]: ./media/uservoice-tutorial/tutorial_general_100.png

[200]: ./media/uservoice-tutorial/tutorial_general_200.png
[201]: ./media/uservoice-tutorial/tutorial_general_201.png
[202]: ./media/uservoice-tutorial/tutorial_general_202.png
[203]: ./media/uservoice-tutorial/tutorial_general_203.png

