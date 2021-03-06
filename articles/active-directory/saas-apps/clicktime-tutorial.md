---
title: 教程：Azure Active Directory 与 ClickTime 集成 | Microsoft Docs
description: 了解如何在 Azure Active Directory 和 ClickTime 之间配置单一登录。
services: active-directory
documentationCenter: na
author: jeevansd
manager: mtillman
ms.reviewer: barbkess
ms.assetid: d437b5ab-4d71-4c13-96d0-79018cebbbd4
ms.service: Azure-Active-Directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: tutorial
ms.date: 01/21/2019
ms.author: jeedes
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2728ce2c375519646d0781005fc10a4174cf2483
ms.sourcegitcommit: 50ea09d19e4ae95049e27209bd74c1393ed8327e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/26/2019
ms.locfileid: "56881356"
---
# <a name="tutorial-azure-active-directory-integration-with-clicktime"></a>教程：Azure Active Directory 与 ClickTime 集成

本教程介绍了如何将 ClickTime 与 Azure Active Directory (Azure AD) 进行集成。
将 ClickTime 与 Azure AD 集成可提供以下优势：

* 可以在 Azure AD 中控制谁有权访问 ClickTime。
* 可以让用户使用其 Azure AD 帐户自动登录到 ClickTime（单一登录）。
* 可在中心位置（即 Azure 门户）管理帐户。

如果要了解有关 SaaS 应用与 Azure AD 集成的更多详细信息，请参阅 [Azure Active Directory 的应用程序访问与单一登录是什么](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis)。
如果还没有 Azure 订阅，可以在开始前[创建一个免费帐户](https://azure.microsoft.com/free/)。

## <a name="prerequisites"></a>先决条件

若要配置 Azure AD 与 ClickTime 的集成，需要具有以下项：

* 一个 Azure AD 订阅。 如果你没有 Azure AD 环境，可以在[此处](https://azure.microsoft.com/pricing/free-trial/)获取一个月的试用版。
* 启用了单一登录的 ClickTime 订阅

## <a name="scenario-description"></a>方案描述

本教程会在测试环境中配置和测试 Azure AD 单一登录。

* ClickTime 支持 **IDP** 发起的 SSO

## <a name="adding-clicktime-from-the-gallery"></a>从库中添加 ClickTime

要配置 ClickTime 与 Azure AD 的集成，需要从库中将 ClickTime 添加到托管 SaaS 应用列表。

**要从库中添加 ClickTime，请执行以下步骤：**

1. 在 **[Azure 门户](https://portal.azure.com)** 的左侧导航面板中，单击“Azure Active Directory”图标。

    ![“Azure Active Directory”按钮](common/select-azuread.png)

2. 转到“企业应用”，并选择“所有应用”选项。

    ![“企业应用程序”边栏选项卡](common/enterprise-applications.png)

3. 若要添加新应用程序，请单击对话框顶部的“新建应用程序”按钮。

    ![“新增应用程序”按钮](common/add-new-app.png)

4. 在搜索框中，键入“ClickTime”，在结果面板中选择“ClickTime”，然后单击“添加”按钮添加该应用程序。

     ![结果列表中的 ClickTime](common/search-new-app.png)

## <a name="configure-and-test-azure-ad-single-sign-on"></a>配置和测试 Azure AD 单一登录

在本部分中，将基于名为 **Britta Simon** 的测试用户配置和测试 ClickTime 的 Azure AD 单一登录。
若要运行单一登录，需要在 Azure AD 用户与 ClickTime 中相关用户之间建立链接关系。

若要配置并测试 ClickTime 的 Azure AD 单一登录，需要完成以下构建基块：

1. **[配置 Azure AD 单一登录](#configure-azure-ad-single-sign-on)** - 使用户能够使用此功能。
2. **[配置 ClickTime 单一登录](#configure-clicktime-single-sign-on)** - 在应用程序端配置单一登录设置。
3. **[创建 Azure AD 测试用户](#create-an-azure-ad-test-user)** - 使用 Britta Simon 测试 Azure AD 单一登录。
4. **[分配 Azure AD 测试用户](#assign-the-azure-ad-test-user)** - 使 Britta Simon 能够使用 Azure AD 单一登录。
5. **[创建 ClickTime 测试用户](#create-clicktime-test-user)** - 在 ClickTime 中创建 Britta Simon 的对应用户，并将其链接到用户的 Azure AD 表示形式。
6. **[测试单一登录](#test-single-sign-on)** - 验证配置是否正常工作。

### <a name="configure-azure-ad-single-sign-on"></a>配置 Azure AD 单一登录

在本部分中，将在 Azure 门户中启用 Azure AD 单一登录。

若要配置 ClickTime 的 Azure AD 单一登录，请执行以下步骤：

1. 在 [Azure 门户](https://portal.azure.com/)中，在 **ClickTime** 应用程序集成页上，选择“单一登录”。

    ![配置单一登录链接](common/select-sso.png)

2. 在**选择单一登录方法**对话框中，选择 **SAML/WS-Fed**模式以启用单一登录。

    ![单一登录选择模式](common/select-saml-option.png)

3. 在“使用 SAML 设置单一登录”页上，单击“编辑”图标以打开“基本 SAML 配置”对话框。

    ![编辑基本 SAML 配置](common/edit-urls.png)

4. 在“设置 SAML 单一登录”页上，执行以下步骤：

    ![ClickTime 域和 URL 单一登录信息](common/idp-intiated.png)

    a. 在“标识符”文本框中键入 URL：`https://app.clicktime.com/sp/`

    b. 在“回复 URL”文本框中，使用以下模式键入 URL：
    | |
    |--|
    | `https://app.clicktime.com/Login/` |
    | `https://app.clicktime.com/App/Login/Consume.aspx` |

4. 在“使用 SAML 设置单一登录”页上，在“SAML 签名证书”部分中，单击“下载”以根据要求从给定的选项下载**证书(Base64)** 并将其保存在计算机上。

    ![证书下载链接](common/certificatebase64.png)

6. 在“设置 ClickTime”部分中，根据要求复制相应的 URL。

    ![复制配置 URL](common/copy-configuration-urls.png)

    a. 登录 URL

    b. Azure AD 标识符

    c. 注销 URL

### <a name="configure-clicktime-single-sign-on"></a>配置 ClickTime 单一登录

1. 在另一个 Web 浏览器窗口中，以管理员身份登录到 ClickTime 公司站点。

1. 在顶部工具栏中，单击“首选项”，并单击“安全设置”。

1. 在“单一登录首选项”配置部分中，执行以下步骤：
   
    ![安全设置](./media/clicktime-tutorial/tic777280.png "安全设置")
   
    a.  选择“允许”通过“Azure AD”使用单一登录 (SSO) 进行登录。
   
    b. 在“标识提供者终结点”文本框中，粘贴从 Azure 门户复制的**登录 URL**。
   
    c.  在记事本中打开从 Azure 门户下载的 base-64 编码证书，复制内容，然后将其粘贴到“X.509 证书”文本框中。
   
    d.  单击“ **保存**”。

### <a name="create-an-azure-ad-test-user"></a>创建 Azure AD 测试用户 

本部分的目的是在 Azure 门户中创建名为 Britta Simon 的测试用户。

1. 在 Azure 门户的左侧窗格中，依次选择“Azure Active Directory”、“用户”和“所有用户”。

    ![“用户和组”以及“所有用户”链接](common/users.png)

2. 选择屏幕顶部的“新建用户”。

    ![“新建用户”按钮](common/new-user.png)

3. 在“用户属性”中，按照以下步骤操作。

    ![“用户”对话框](common/user-properties.png)

    a. 在“名称”字段中，输入 BrittaSimon。
  
    b. 在“用户名”字段中键入 brittasimon@yourcompanydomain.extension  
    例如： BrittaSimon@contoso.com

    c. 选中“显示密码”复选框，然后记下“密码”框中显示的值。

    d. 单击“创建”。

### <a name="assign-the-azure-ad-test-user"></a>分配 Azure AD 测试用户

在本部分中，将通过向 Britta Simon 授予 ClickTime 的访问权限使之能够使用 Azure 单一登录。

1. 在 Azure 门户中，依次选择“企业应用程序”、“所有应用程序”和“ClickTime”。

    ![“企业应用程序”边栏选项卡](common/enterprise-applications.png)

2. 在应用程序列表中，选择“ClickTime”。

    ![应用程序列表中的 ClickTime 链接](common/all-applications.png)

3. 在左侧菜单中，选择“用户和组”。

    ![“用户和组”链接](common/users-groups-blade.png)

4. 单击“添加用户”按钮，然后在“添加分配”对话框中选择“用户和组”。

    ![“添加分配”窗格](common/add-assign-user.png)

5. 在“用户和组”对话框中，选择“用户”列表中的 Britta Simon，然后单击屏幕底部的“选择”按钮。

6. 如果你在 SAML 断言中需要任何角色值，请在“选择角色”对话框中从列表中为用户选择合适的角色，然后单击屏幕底部的“选择”按钮。

7. 在“添加分配”对话框中，单击“分配”按钮。

### <a name="create-clicktime-test-user"></a>创建 ClickTime 测试用户

为了使 Azure AD 用户能够登录到 ClickTime，必须将其预配到 ClickTime 中。  
对于 ClickTime，需要手动执行预配。

> [!NOTE]
> 可以使用 ClickTime 提供的任何其他 ClickTime 用户帐户创建工具或 API 来预配 Azure AD 用户帐户。

**若要预配用户帐户，请执行以下步骤：**

1. 登录到 **ClickTime** 租户。

1. 在顶部工具栏中，单击“公司”，并单击“人员”。
   
    ![人员](./media/clicktime-tutorial/tic777282.png "人员")

1. 单击“添加用户”。
   
    ![添加人员](./media/clicktime-tutorial/tic777283.png "添加人员")

1. 在“新建人员”部分中，执行以下步骤：
   
    ![人员](./media/clicktime-tutorial/tic777284.png "人员")
   
    a.  在“全名”文本框中，键入用户的全名，例如 Britta Simon。 
  
    b.  在“电子邮件地址”文本框中，键入用户的电子邮件，例如 brittasimon@contoso.com。
       
    > [!NOTE]
    > 如果需要，可以设置新人员对象的其他属性。
   
    c.  单击“ **保存**”。

### <a name="test-single-sign-on"></a>测试单一登录 

在本部分中，使用访问面板测试 Azure AD 单一登录配置。

单击访问面板中的 ClickTime 磁贴时，应当会自动登录到为其设置了 SSO 的 ClickTime。 有关访问面板的详细信息，请参阅 [Introduction to the Access Panel](https://docs.microsoft.com/azure/active-directory/active-directory-saas-access-panel-introduction)（访问面板简介）。

## <a name="additional-resources"></a>其他资源

- [有关如何将 SaaS 应用与 Azure Active Directory 集成的教程列表](https://docs.microsoft.com/azure/active-directory/active-directory-saas-tutorial-list)

- [Azure Active Directory 的应用程序访问与单一登录是什么？](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis)

- [什么是 Azure Active Directory 中的条件访问？](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)

