---
title: 教程：Azure Active Directory 与 TalentLMS 集成 | Microsoft Docs
description: 了解如何在 Azure Active Directory 和 TalentLMS 之间配置单一登录。
services: active-directory
documentationCenter: na
author: jeevansd
manager: mtillman
ms.assetid: c903d20d-18e3-42b0-b997-6349c5412dde
ms.service: active-directory
ms.component: saas-app-tutorial
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 07/13/2017
ms.author: jeedes
ms.openlocfilehash: 5d7f77b1c2b7677310246afd4dd512a3dcaff442
ms.sourcegitcommit: 16ddc345abd6e10a7a3714f12780958f60d339b6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2018
ms.locfileid: "36223325"
---
# <a name="tutorial-azure-active-directory-integration-with-talentlms"></a>教程：Azure Active Directory 与 TalentLMS 集成

本教程介绍如何将 TalentLMS 与 Azure Active Directory (Azure AD) 集成。

将 TalentLMS 与 Azure AD 集成可提供以下优势：

- 可在 Azure AD 中控制谁有权访问 TalentLMS
- 可以让用户使用其 Azure AD 帐户自动登录到 TalentLMS（单一登录）
- 可以在一个中心位置（即 Azure 门户）管理帐户

如需了解有关 SaaS 应用与 Azure AD 集成的详细信息，请参阅 [Azure Active Directory 的应用程序访问与单一登录是什么](../manage-apps/what-is-single-sign-on.md)。

## <a name="prerequisites"></a>先决条件

若要配置 Azure AD 与 TalentLMS 的集成，需要以下项：

- Azure AD 订阅
- 已启用 TalentLMS 单一登录的订阅

> [!NOTE]
> 为了测试本教程中的步骤，我们不建议使用生产环境。

测试本教程中的步骤应遵循以下建议：

- 除非必要，请勿使用生产环境。
- 如果没有 Azure AD 试用环境，可在此处获取一个月的试用版：[试用产品/服务](https://azure.microsoft.com/pricing/free-trial/)。

## <a name="scenario-description"></a>方案描述
在本教程中，将在测试环境中测试 Azure AD 单一登录。 本教程中概述的方案包括两个主要构建基块：

1. 从库中添加 TalentLMS
2. 配置和测试 Azure AD 单一登录

## <a name="adding-talentlms-from-the-gallery"></a>从库中添加 TalentLMS
若要配置 TalentLMS 与 Azure AD 的集成，需要从库中将 TalentLMS 添加到托管 SaaS 应用列表。

若要从库中添加 TalentLMS，请执行以下步骤：

1. 在 **[Azure 门户](https://portal.azure.com)** 的左侧导航面板中，单击“Azure Active Directory”图标。 

    ![Active Directory][1]

2. 导航到“企业应用程序”。 然后转到“所有应用程序”。

    ![应用程序][2]
    
3. 若要添加新应用程序，请单击对话框顶部的“新建应用程序”按钮。

    ![应用程序][3]

4. 在搜索框中，键入“TalentLMS”。

    ![创建 Azure AD 测试用户](./media/talentlms-tutorial/tutorial_talentlms_search.png)

5. 在结果面板中，选择“TalentLMS”，并单击“添加”按钮添加该应用程序。

    ![创建 Azure AD 测试用户](./media/talentlms-tutorial/tutorial_talentlms_addfromgallery.png)

##  <a name="configuring-and-testing-azure-ad-single-sign-on"></a>配置和测试 Azure AD 单一登录
在本部分中，将基于一个名为“Britta Simon”的测试用户使用 TalentLMS 配置和测试 Azure AD 单一登录。

为使单一登录能正常工作，Azure AD 需要知道与 Azure AD 用户相对应的 TalentLMS 用户。 换句话说，需要建立 Azure AD 用户与 TalentLMS 中相关用户之间的链接关系。

可通过将 Azure AD 中“用户名”的值指定为 TalentLMS 中“用户名”的值来建立此链接关系。

若要配置并测试 TalentLMS 的 Azure AD 单一登录，需要完成以下构建基块：

1. **[配置 Azure AD 单一登录](#configuring-azure-ad-single-sign-on)** - 让用户使用此功能。
2. **[创建 Azure AD 测试用户](#creating-an-azure-ad-test-user)** - 使用 Britta Simon 测试 Azure AD 单一登录。
3. [创建 TalentLMS 测试用户](#creating-a-talentlms-test-user) - 在 TalentLMS 中创建 Britta Simon 的对应用户，链接到用户的 Azure AD 表示形式。
4. **[分配 Azure AD 测试用户](#assigning-the-azure-ad-test-user)** - 让 Britta Simon 使用 Azure AD 单一登录。
5. **[测试单一登录](#testing-single-sign-on)** - 验证配置是否正常工作。

### <a name="configuring-azure-ad-single-sign-on"></a>配置 Azure AD 单一登录

在本部分中，将介绍如何在 Azure 门户中启用 Azure AD 单一登录并在 TalentLMS 应用程序中配置单一登录。

若要配置 TalentLMS 的 Azure AD 单一登录，请执行以下步骤：

1. 在 Azure 门户中的 TalentLMS 应用程序集成页上，单击“单一登录”。

    ![配置单一登录][4]

2. 在“单一登录”对话框中，选择“基于 SAML 的单一登录”作为“模式”以启用单一登录。
 
    ![配置单一登录](./media/talentlms-tutorial/tutorial_talentlms_samlbase.png)

3. 在“TalentLMS 域和 URL”部分中，执行以下步骤：

    ![配置单一登录](./media/talentlms-tutorial/tutorial_talentlms_url.png)

    a. 在“登录 URL”文本框中，使用以下模式键入 URL：`https://<tenant-name>.TalentLMSapp.com`

    b. 在“标识符”文本框中，使用以下模式键入 URL：`http://<tenant-name>.talentlms.com`

    > [!NOTE] 
    > 这些不是实际值。 必须使用实际登录 URL 和标识符更新这些值。 请联系 [TalentLMS 客户端支持团队](https://www.talentlms.com/contact)获取这些值。 
 
4. 在“SAML 签名证书”部分中，复制证书的指纹值。

    ![配置单一登录](./media/talentlms-tutorial/tutorial_talentlms_certificate.png) 

5. 单击“保存”按钮。

    ![配置单一登录](./media/talentlms-tutorial/tutorial_general_400.png)

6. 在“TalentLMS 配置”部分中，单击“配置 TalentLMS”打开“配置登录”窗口。 从“快速参考”部分中复制“注销 URL”、“SAML 实体 ID”和“SAML 单一登录服务 URL”。

    ![配置单一登录](./media/talentlms-tutorial/tutorial_talentlms_configure.png)  

7. 在另一个 Web 浏览器窗口中，以管理员身份登录 TalentLMS 公司站点。

8. 在“帐户与设置” 部分中，单击“用户”选项卡。
   
    ![帐户与设置](./media/talentlms-tutorial/IC777296.png "帐户与设置")

9. 单击“单一登录(SSO)”。

10. 在“单一登录”部分中，执行以下步骤：
   
    ![单一登录](./media/talentlms-tutorial/IC777297.png "单一登录")   

    a. 从“SSO 集成类型”列表中，选择“SAML 2.0”。

    b. 在“标识提供程序 (IDP)”文本框中，粘贴从 Azure 门户复制的“SAML 实体 ID”值。
 
    c. 将 Azure 门户中的指纹值粘贴到“证书指纹”文本框。    

    d.  在“远程登录 URL”文本框中，粘贴从 Azure 门户复制的“SAML 单一登录服务 URL”值。
 
    e. 在“远程注销 URL”文本框中，粘贴从 Azure 门户复制的“注销 URL”值。

    f. 填写以下信息： 

    * 在“TargetedID”文本框中，键入 `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name`
     
    * 在“名字”文本框中，键入 `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname`
    
    * 在“姓氏”文本框中，键入 `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname`
    
    * 在“电子邮件”文本框中，键入 `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress`
    
11. 单击“ **保存**”。
 
> [!TIP]
> 之后在设置应用时，就可以在 [Azure 门户](https://portal.azure.com)中阅读这些说明的简明版本了！  从“Active Directory”>“企业应用程序”部分添加此应用后，只需单击“单一登录”选项卡，即可通过底部的“配置”部分访问嵌入式文档。 可在此处阅读有关嵌入式文档功能的详细信息：[ Azure AD 嵌入式文档]( https://go.microsoft.com/fwlink/?linkid=845985)
> 

### <a name="creating-an-azure-ad-test-user"></a>创建 Azure AD 测试用户
本部分的目的是在 Azure 门户中创建名为 Britta Simon 的测试用户。

![创建 Azure AD 用户][100]

**若要在 Azure AD 中创建测试用户，请执行以下步骤：**

1. 在 **Azure 门户**的左侧导航窗格中，单击“Azure Active Directory”图标。

    ![创建 Azure AD 测试用户](./media/talentlms-tutorial/create_aaduser_01.png) 

2. 若要显示用户列表，请转到“用户和组”，单击“所有用户”。
    
    ![创建 Azure AD 测试用户](./media/talentlms-tutorial/create_aaduser_02.png) 

3. 若要打开“用户”对话框，请在对话框顶部单击“添加”。
 
    ![创建 Azure AD 测试用户](./media/talentlms-tutorial/create_aaduser_03.png) 

4. 在“用户”对话框页上，执行以下步骤：
 
    ![创建 Azure AD 测试用户](./media/talentlms-tutorial/create_aaduser_04.png) 

    a. 在“名称”文本框中，键入 **BrittaSimon**。

    b. 在“用户名”文本框中，键入 BrittaSimon 的“电子邮件地址”。

    c. 选择“显示密码”并记下“密码”的值。

    d. 单击“创建”。
 
### <a name="creating-a-talentlms-test-user"></a>创建 TalentLMS 测试用户

若要使 Azure AD 用户能够登录 TalentLMS，必须将这些用户预配到 TalentLMS 中。 对于 TalentLMS，预配是一项手动任务。

**若要预配用户帐户，请执行以下步骤：**

1. 登录到 **TalentLMS** 租户。

2. 单击“用户”，并单击“添加用户”。

3. 在“添加用户”对话框页上，执行以下步骤：
   
    ![添加用户](./media/talentlms-tutorial/IC777299.png "添加用户")  

    a. 在“名字”文本框中，输入用户的名字（如“Britta”）。

    b. 在“姓氏”文本框中，输入用户的姓氏（如“Simon”）。
 
    c. 在“电子邮件地址”文本框中，输入用户的电子邮件地址（例如 brittasimon@contoso.com）。

    d. 单击“添加用户”。

>[!NOTE]
>可以使用任何其他 TalentLMS 用户帐户创建工具或 TalentLMS 提供的 API 来预配 AAD 用户帐户。
 

### <a name="assigning-the-azure-ad-test-user"></a>分配 Azure AD 测试用户

在本节中，将通过授予 Britta Simon 访问 TalentLMS 的权限，允许她使用 Azure 单一登录。

![分配用户][200] 

若要将 Britta Simon 分配到 TalentLMS，请执行以下步骤：

1. 在 Azure 门户中打开应用程序视图，导航到目录视图，接着转到“企业应用程序”，并单击“所有应用程序”。

    ![分配用户][201] 

2. 在应用程序列表中，选择“TalentLMS”。

    ![配置单一登录](./media/talentlms-tutorial/tutorial_talentlms_app.png) 

3. 在左侧菜单中，单击“用户和组”。

    ![分配用户][202] 

4. 单击“添加”按钮。 然后在“添加分配”对话框中选择“用户和组”。

    ![分配用户][203]

5. 在“用户和组”对话框的“用户”列表中，选择“Britta Simon”。

6. 在“用户和组”对话框中单击“选择”按钮。

7. 在“添加分配”对话框中单击“分配”按钮。
    
### <a name="testing-single-sign-on"></a>测试单一登录

本部分旨在使用“访问面板”测试 Azure AD 单一登录配置。

单击访问面板中的 TalentLMS 磁贴时，应自动登录到 TalentLMS 应用程序

## <a name="additional-resources"></a>其他资源

* [有关如何将 SaaS 应用与 Azure Active Directory 集成的教程列表](tutorial-list.md)
* [什么是使用 Azure Active Directory 的应用程序访问和单一登录？](../manage-apps/what-is-single-sign-on.md)



<!--Image references-->

[1]: ./media/talentlms-tutorial/tutorial_general_01.png
[2]: ./media/talentlms-tutorial/tutorial_general_02.png
[3]: ./media/talentlms-tutorial/tutorial_general_03.png
[4]: ./media/talentlms-tutorial/tutorial_general_04.png

[100]: ./media/talentlms-tutorial/tutorial_general_100.png

[200]: ./media/talentlms-tutorial/tutorial_general_200.png
[201]: ./media/talentlms-tutorial/tutorial_general_201.png
[202]: ./media/talentlms-tutorial/tutorial_general_202.png
[203]: ./media/talentlms-tutorial/tutorial_general_203.png
