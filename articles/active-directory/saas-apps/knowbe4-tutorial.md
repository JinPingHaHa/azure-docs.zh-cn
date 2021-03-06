---
title: 教程：Azure Active Directory 与 KnowBe4 Security Awareness Training 集成 | Microsoft Docs
description: 了解如何在 Azure Active Directory 和 KnowBe4 安全意识培训之间配置单一登录。
services: active-directory
documentationCenter: na
author: jeevansd
manager: daveba
ms.reviewer: barbkess
ms.assetid: b80d2212-cc5f-4adb-836c-570640810c39
ms.service: Azure-Active-Directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: tutorial
ms.date: 01/02/2019
ms.author: jeedes
ms.collection: M365-identity-device-management
ms.openlocfilehash: 23ba6e46d5f92e8b07077aaf82ad03f49dc2df7a
ms.sourcegitcommit: 50ea09d19e4ae95049e27209bd74c1393ed8327e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/26/2019
ms.locfileid: "56865206"
---
# <a name="tutorial-azure-active-directory-integration-with-knowbe4-security-awareness-training"></a>教程：Azure Active Directory 与 KnowBe4 Security Awareness Training 集成

本教程介绍如何将 KnowBe4 安全意识培训与 Azure Active Directory (Azure AD) 集成。
将 KnowBe4 安全意识培训与 Azure AD 集成具有以下优势：

* 可在 Azure AD 中控制谁有权访问 KnowBe4 安全意识培训。
* 可使用户使用其 Azure AD 帐户自动登录到 KnowBe4 Security Awareness Training（单一登录）。
* 可在中心位置（即 Azure 门户）管理帐户。

如果要了解有关 SaaS 应用与 Azure AD 集成的更多详细信息，请参阅 [Azure Active Directory 的应用程序访问与单一登录是什么](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis)。
如果还没有 Azure 订阅，可以在开始前[创建一个免费帐户](https://azure.microsoft.com/free/)。

## <a name="prerequisites"></a>先决条件

若要配置 Azure AD 与 KnowBe4 安全意识培训的集成，需要以下项：

* 一个 Azure AD 订阅。 如果你没有 Azure AD 环境，可以在[此处](https://azure.microsoft.com/pricing/free-trial/)获取一个月的试用版。
* 已启用 KnowBe4 Security Awareness Training 单一登录的订阅

## <a name="scenario-description"></a>方案描述

本教程会在测试环境中配置和测试 Azure AD 单一登录。

* KnowBe4 Security Awareness Training 支持 **SP** 发起的 SSO

* KnowBe4 Security Awareness Training 支持**恰时**用户预配

## <a name="adding-knowbe4-security-awareness-training-from-the-gallery"></a>从库中添加 KnowBe4 安全意识培训

若要配置 KnowBe4 安全意识培训与 Azure AD 的集成，需从库中将 KnowBe4 安全意识培训添加到托管 SaaS 应用列表。

**若要从库中添加 KnowBe4 安全意识培训，请执行以下步骤：**

1. 在 **[Azure 门户](https://portal.azure.com)** 的左侧导航面板中，单击“Azure Active Directory”图标。

    ![“Azure Active Directory”按钮](common/select-azuread.png)

2. 转到“企业应用”，并选择“所有应用”选项。

    ![“企业应用程序”边栏选项卡](common/enterprise-applications.png)

3. 若要添加新应用程序，请单击对话框顶部的“新建应用程序”按钮。

    ![“新增应用程序”按钮](common/add-new-app.png)

4. 在搜索框中，键入“KnowBe4 安全意识培训”，选择结果面板中的“KnowBe4 安全意识培训”，然后单击“添加”按钮，添加应用程序。

     ![结果列表中的“KnowBe4 安全意识培训”](common/search-new-app.png)

## <a name="configure-and-test-azure-ad-single-sign-on"></a>配置和测试 Azure AD 单一登录

在本部分中，基于名为“Britta Simon”的测试用户配置和测试 KnowBe4 Security Awareness Training 的 Azure AD 单一登录。
若要运行单一登录，需要在 Azure AD 用户与 KnowBe4 Security Awareness Training 相关用户之间建立链接关系。

若要配置和测试 KnowBe4 安全意识培训的 Azure AD 单一登录，需要完成以下构建基块：

1. **[配置 Azure AD 单一登录](#configure-azure-ad-single-sign-on)** - 使用户能够使用此功能。
2. **[配置 KnowBe4 Security Awareness Training 单一登录](#configure-knowbe4-security-awareness-training-single-sign-on)** - 在应用程序端配置单一登录设置。
3. **[创建 Azure AD 测试用户](#create-an-azure-ad-test-user)** - 使用 Britta Simon 测试 Azure AD 单一登录。
4. **[分配 Azure AD 测试用户](#assign-the-azure-ad-test-user)** - 使 Britta Simon 能够使用 Azure AD 单一登录。
5. **[创建 KnowBe4 Security Awareness Training 测试用户](#create-knowbe4-security-awareness-training-test-user)** - 在 KnowBe4 Security Awareness Training 中创建 Britta Simon 的对应用户，并将其链接到该用户的 Azure AD 表示形式。
6. **[测试单一登录](#test-single-sign-on)** - 验证配置是否正常工作。

### <a name="configure-azure-ad-single-sign-on"></a>配置 Azure AD 单一登录

在本部分中，将在 Azure 门户中启用 Azure AD 单一登录。

若要配置 KnowBe4 Security Awareness Training 的 Azure AD 单一登录，请执行以下步骤：

1. 在 [Azure 门户](https://portal.azure.com/)中的 KnowBe4 Security Awareness Training 应用程序集成页上，选择“单一登录”。

    ![配置单一登录链接](common/select-sso.png)

2. 在**选择单一登录方法**对话框中，选择 **SAML/WS-Fed**模式以启用单一登录。

    ![单一登录选择模式](common/select-saml-option.png)

3. 在“使用 SAML 设置单一登录”页上，单击“编辑”图标以打开“基本 SAML 配置”对话框。

    ![编辑基本 SAML 配置](common/edit-urls.png)

4. 在“基本 SAML 配置”部分中，按照以下步骤操作：

    ![KnowBe4 安全意识培训域和 URl 单一登录信息](common/sp-identifier.png)

    a. 在“登录 URL”文本框中，使用以下模式键入 URL：`https://<companyname>.KnowBe4.com/auth/saml/<instancename>`

    > [!NOTE]
    > 登录 URL 值不是实际值。 请使用实际登录 URL 更新此值。 请联系 [KnowBe4 安全意识培训客户端支持团队](mailto:support@KnowBe4.com)获取此值。 还可以参考 Azure 门户中的“基本 SAML 配置”部分中显示的模式。

    b. 在“标识符(实体 ID)”文本框中，键入字符串值：`KnowBe4`

    > [!NOTE]
    > 此参数区分大小写。

5. 在“使用 SAML 设置单一登录”页上，在“SAML 签名证书”部分中，单击“下载”以根据要求通过从给定的选项下载**证书(原始)** 并将其保存在计算机上。

    ![证书下载链接](common/certificateraw.png)

6. 在“设置 KnowBe4 Security Awareness Training”部分，根据要求复制相应 URL。

    ![复制配置 URL](common/copy-configuration-urls.png)

    a. 登录 URL

    b. Azure AD 标识符

    c. 注销 URL

### <a name="configure-knowbe4-security-awareness-training-single-sign-on"></a>配置 KnowBe4 Security Awareness Training 单一登录

若要在 **KnowBe4 Security Awareness Training** 端配置单一登录，需要将下载的**证书(原始)** 以及从 Azure 门户复制的相应 URL 发送给 [KnowBe4 Security Awareness Training 支持团队](mailto:support@KnowBe4.com)。 他们会对此进行设置，使两端的 SAML SSO 连接均正确设置。

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

在本部分中，通过授予 Britta Simon 对 KnowBe4 安全意识培训的访问权限，使其能够使用 Azure 单一登录。

1. 在 Azure 门户中，依次选择“企业应用程序”、“所有应用程序”、“KnowBe4 Security Awareness Training”。

    ![“企业应用程序”边栏选项卡](common/enterprise-applications.png)

2. 在应用程序列表中，选择“KnowBe4 安全意识培训”。

    ![应用程序列表中的“KnowBe4 安全意识培训”链接](common/all-applications.png)

3. 在左侧菜单中，选择“用户和组”。

    ![“用户和组”链接](common/users-groups-blade.png)

4. 单击“添加用户”按钮，然后在“添加分配”对话框中选择“用户和组”。

    ![“添加分配”窗格](common/add-assign-user.png)

5. 在“用户和组”对话框中，选择“用户”列表中的 Britta Simon，然后单击屏幕底部的“选择”按钮。

6. 如果你在 SAML 断言中需要任何角色值，请在“选择角色”对话框中从列表中为用户选择合适的角色，然后单击屏幕底部的“选择”按钮。

7. 在“添加分配”对话框中，单击“分配”按钮。

### <a name="create-knowbe4-security-awareness-training-test-user"></a>创建 KnowBe4 Security Awareness Training 测试用户

本部分的目的是在 KnowBe4 安全意识培训中创建名为“Britta Simon”的用户。 KnowBe4 安全意识培训支持实时预配，该功能会默认启用。

此部分不存在任何操作项。 如果用户尚不存在，则会在尝试访问 KnowBe4 安全意识培训期间创建一个新用户。

> [!NOTE]
> 如果需要手动创建用户，则需联系 [KnowBe4 安全意识培训支持团队](mailto:support@KnowBe4.com)。

### <a name="test-single-sign-on"></a>测试单一登录

在本部分中，使用访问面板测试 Azure AD 单一登录配置。

单击访问面板中的 KnowBe4 Security Awareness Training 磁贴时，应当会自动登录到为其设置了 SSO 的 KnowBe4 Security Awareness Training。 有关访问面板的详细信息，请参阅 [Introduction to the Access Panel](https://docs.microsoft.com/azure/active-directory/active-directory-saas-access-panel-introduction)（访问面板简介）。

## <a name="additional-resources"></a>其他资源

- [有关如何将 SaaS 应用与 Azure Active Directory 集成的教程列表](https://docs.microsoft.com/azure/active-directory/active-directory-saas-tutorial-list)

- [Azure Active Directory 的应用程序访问与单一登录是什么？](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis)

- [什么是 Azure Active Directory 中的条件访问？](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)
