---
title: 教程：Azure Active Directory 与 TargetProcess 的集成 | Microsoft Docs
description: 了解如何在 Azure Active Directory 和 TargetProcess 之间配置单一登录。
services: active-directory
documentationCenter: na
author: jeevansd
manager: daveba
ms.reviewer: barbkess
ms.assetid: 7cb91628-e758-480d-a233-7a3caaaff50d
ms.service: Azure-Active-Directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: tutorial
ms.date: 12/7/2018
ms.author: jeedes
ms.collection: M365-identity-device-management
ms.openlocfilehash: a6f5a20dc911faa9d6d8948543b6391d4a8ec2c9
ms.sourcegitcommit: 50ea09d19e4ae95049e27209bd74c1393ed8327e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/26/2019
ms.locfileid: "56883743"
---
# <a name="tutorial-azure-active-directory-integration-with-targetprocess"></a>教程：Azure Active Directory 与 TargetProcess 的集成

本教程介绍如何将 TargetProcess 与 Azure Active Directory (Azure AD) 集成。
将 TargetProcess 与 Azure AD 集成具有以下优势：

* 可以在 Azure AD 中控制谁有权访问 TargetProcess。
* 可以让用户使用其 Azure AD 帐户自动登录到 TargetProcess（单一登录）。
* 可在中心位置（即 Azure 门户）管理帐户。

如果要了解有关 SaaS 应用与 Azure AD 集成的更多详细信息，请参阅 [Azure Active Directory 的应用程序访问与单一登录是什么](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis)。
如果还没有 Azure 订阅，可以在开始前[创建一个免费帐户](https://azure.microsoft.com/free/)。

## <a name="prerequisites"></a>先决条件

若要配置 Azure AD 与 TargetProcess 的集成，需要以下项：

* 一个 Azure AD 订阅。 如果你没有 Azure AD 环境，可以在[此处](https://azure.microsoft.com/pricing/free-trial/)获取一个月的试用版。
* 启用了单一登录的 TargetProcess 订阅

## <a name="scenario-description"></a>方案描述

本教程会在测试环境中配置和测试 Azure AD 单一登录。

* TargetProcess 支持 **SP** 启动的 SSO
* TargetProcess 支持实时预配

## <a name="adding-targetprocess-from-the-gallery"></a>从库中添加 TargetProcess

要配置 TargetProcess 与 Azure AD 的集成，需要从库中将 TargetProcess 添加到托管 SaaS 应用列表。

**若要从库中添加 TargetProcess，请执行以下步骤：**

1. 在 **[Azure 门户](https://portal.azure.com)** 的左侧导航面板中，单击“Azure Active Directory”图标。

    ![“Azure Active Directory”按钮](common/select-azuread.png)

2. 转到“企业应用”，并选择“所有应用”选项。

    ![“企业应用程序”边栏选项卡](common/enterprise-applications.png)

3. 若要添加新应用程序，请单击对话框顶部的“新建应用程序”按钮。

    ![“新增应用程序”按钮](common/add-new-app.png)

4. 在搜索框中，键入“TargetProcess”，在结果面板中选择“TargetProcess”，然后单击“添加”按钮以添加该应用程序。

     ![结果列表中的 TargetProcess](common/search-new-app.png)

## <a name="configure-and-test-azure-ad-single-sign-on"></a>配置和测试 Azure AD 单一登录

在本部分中，将基于名为 **Britta Simon** 的测试用户配置和测试 TargetProcess 的 Azure AD 单一登录。
若要运行单一登录，需要在 Azure AD 用户与 TargetProcess 中相关用户之间建立链接关系。

若要配置和测试 TargetProcess 的 Azure AD 单一登录，需要完成以下构建基块：

1. **[配置 Azure AD 单一登录](#configure-azure-ad-single-sign-on)** - 使用户能够使用此功能。
2. **[创建 Azure AD 测试用户](#create-an-azure-ad-test-user)** - 使用 Britta Simon 测试 Azure AD 单一登录。
3. **[创建 TargetProcess 测试用户](#create-targetprocess-test-user)** - 在 TargetProcess 中创建 Britta Simon 的对应用户，将其链接到用户的 Azure AD 表示形式。
4. **[分配 Azure AD 测试用户](#assign-the-azure-ad-test-user)** - 使 Britta Simon 能够使用 Azure AD 单一登录。
5. **[测试单一登录](#test-single-sign-on)** - 验证配置是否正常工作。

### <a name="configure-azure-ad-single-sign-on"></a>配置 Azure AD 单一登录

在本部分中，将在 Azure 门户中启用 Azure AD 单一登录。

若要配置 TargetProcess 的 Azure AD 单一登录，请执行以下步骤：

1. 在 [Azure 门户](https://portal.azure.com/)中，在 **TargetProcess** 应用程序集成页上，单击“单一登录”。

    ![配置单一登录链接](common/select-sso.png)

2. 在**选择单一登录方法**对话框中，选择 **SAML/WS-Fed**模式以启用单一登录。

    ![单一登录选择模式](common/select-saml-option.png)

3. 在“使用 SAML 设置单一登录”页上，单击“编辑”图标以打开“基本 SAML 配置”对话框。

    ![编辑基本 SAML 配置](common/edit-urls.png)

4. 在“基本 SAML 配置”部分中，按照以下步骤操作：

    ![TargetProcess 域和 URL 单一登录信息](common/sp-identifier.png)

    a. 在“登录 URL”文本框中，使用以下模式键入 URL： `https://<subdomain>.tpondemand.com/`

    b. 在“标识符”文本框中，使用以下模式键入 URL：`https://<subdomain>.tpondemand.com/`

    > [!NOTE]
    > 这些不是实际值。 必须使用实际登录 URL 和标识符更新这些值。  请联系 [TargetProcess 客户端支持团队](mailto:support@targetprocess.com)获取这些值。

5. 在“使用 SAML 设置单一登录”页上，在“SAML 签名证书”部分中，单击“下载”以根据要求从给定的选项下载**证书(Base64)** 并将其保存在计算机上。

    ![证书下载链接](common/certificatebase64.png)

6. 在“设置 TargetProcess”部分中，根据要求复制相应的 URL。

    ![复制配置 URL](common/copy-configuration-urls.png)

    a. 登录 URL

    b. Azure AD 标识符

    c. 注销 URL

7. 必须通过单击“安装扩展”来安装“我的应用安全登录浏览器扩展”，才能在 **TargetProcess** 中自动执行配置。

    ![图像](./media/target-process-tutorial/install_extension.png)

8. 将扩展添加到浏览器后，单击“安装 TargetProcess”会定向到 TargetProcess 应用程序。 随后，提供管理员凭据，以登录到 TargetProcess。 浏览器扩展将自动为你配置应用程序并自动执行步骤 9-13。

    **如果要手动配置应用程序，请执行以下步骤：**

9. 以管理员身份登录 TargetProcess 应用程序。

10. 在顶部菜单中，单击“设置”。

    ![设置](./media/target-process-tutorial/tutorial_target_process_05.png)

11. 单击“设置”。

    ![设置](./media/target-process-tutorial/tutorial_target_process_06.png)

12. 单击“单一登录”。

    ![单击“单一登录”](./media/target-process-tutorial/tutorial_target_process_07.png)

13. 在“单一登录设置”对话框上，执行以下步骤：

    ![配置单一登录](./media/target-process-tutorial/tutorial_target_process_08.png)

    a. 单击“启用单一登录”。

    b. 在“登录 URL”文本框中，粘贴从 Azure 门户复制的“SAML 单一登录服务 URL”值。

    c. 在记事本中打开下载的证书，复制其内容，并将其粘贴到“证书”文本框中。

    d. 单击“启用 JIT 预配”。

    e. 单击“ **保存**”。

> [!TIP]
> 之后在设置应用时，就可以在 [Azure 门户](https://portal.azure.com)中阅读这些说明的简明版本了！  从“Active Directory”>“企业应用程序”部分添加此应用后，只需单击“单一登录”选项卡，即可通过底部的“配置”部分访问嵌入式文档。 可在此处阅读有关嵌入式文档功能的详细信息：[Azure AD 嵌入式文档]( https://go.microsoft.com/fwlink/?linkid=845985)

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

在本部分中，通过授予 Britta Simon 访问 TargetProcess 的权限，允许她使用 Azure 单一登录。

1. 在 Azure 门户中，依次选择“企业应用程序”、“所有应用程序”和“TargetProcess”。

    ![“企业应用程序”边栏选项卡](common/enterprise-applications.png)

2. 在应用程序列表中，键入并选择“TargetProcess”。

    ![应用程序列表中的 TargetProcess 链接](common/all-applications.png)

3. 在左侧菜单中，选择“用户和组”。

    ![“用户和组”链接](common/users-groups-blade.png)

4. 单击“添加用户”按钮，然后在“添加分配”对话框中选择“用户和组”。

    ![“添加分配”窗格](common/add-assign-user.png)

5. 在“用户和组”对话框中，选择“用户”列表中的 Britta Simon，然后单击屏幕底部的“选择”按钮。

6. 如果你在 SAML 断言中需要任何角色值，请在“选择角色”对话框中从列表中为用户选择合适的角色，然后单击屏幕底部的“选择”按钮。

7. 在“添加分配”对话框中，单击“分配”按钮。

### <a name="create-targetprocess-test-user"></a>创建 TargetProcess 测试用户

本部分的目的是在 TargetProcess 中创建名为“Britta Simon”的用户。 TargetProcess 支持在默认情况下启用的实时预配。 此部分不存在任何操作项。 如果新用户尚不存在，可在尝试访问 TargetProcess 期间创建该用户。

> [!Note]
> 如果需要手动创建用户，请联系  [TargetProcess 支持团队](mailto:support@targetprocess.com)。

### <a name="test-single-sign-on"></a>测试单一登录

在本部分中，使用访问面板测试 Azure AD 单一登录配置。

单击访问面板中的 TargetProcess 磁贴时，应当会自动登录到你为其设置了 SSO 的 TargetProcess。 有关访问面板的详细信息，请参阅 [Introduction to the Access Panel](https://docs.microsoft.com/azure/active-directory/active-directory-saas-access-panel-introduction)（访问面板简介）。

## <a name="additional-resources"></a>其他资源

- [有关如何将 SaaS 应用与 Azure Active Directory 集成的教程列表](https://docs.microsoft.com/azure/active-directory/active-directory-saas-tutorial-list)

- [Azure Active Directory 的应用程序访问与单一登录是什么？](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis)

- [什么是 Azure Active Directory 中的条件访问？](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)
