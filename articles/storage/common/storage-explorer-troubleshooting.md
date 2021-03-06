---
title: Azure 存储资源管理器疑难解答指南 | Microsoft Docs
description: Azure 存储资源管理器的调试技术的概述
services: virtual-machines
author: Deland-Han
ms.service: virtual-machines
ms.topic: troubleshooting
ms.date: 06/15/2018
ms.author: delhan
ms.openlocfilehash: bff1e8c111a8a50e15b6d316e422a641a778c73c
ms.sourcegitcommit: 5fbca3354f47d936e46582e76ff49b77a989f299
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2019
ms.locfileid: "57775163"
---
# <a name="azure-storage-explorer-troubleshooting-guide"></a>Azure 存储资源管理器故障排除指南

Microsoft Azure 存储资源管理器是一款独立应用，可用于在 Windows、macOS 和 Linux 上轻松处理 Azure 存储数据。 应用可连接到托管在 Azure、National Clouds 和 Azure Stack 上的存储帐户。

本指南汇总了存储资源管理器中常见问题的解决方案。

## <a name="role-based-access-control-permission-issues"></a>基于角色的访问控制权限问题

[基于角色的访问控制 (RBAC)](https://docs.microsoft.com/azure/role-based-access-control/overview)通过合并到的权限集提供的 Azure 资源的精细访问管理_角色_。 以下是一些可以按照若要获取在存储资源管理器中工作的 RBAC 的建议。

### <a name="what-do-i-need-to-see-my-resources-in-storage-explorer"></a>若要查看我在存储资源管理器中的资源，我需要什么？

如果遇到访问使用 RBAC 的存储资源出现问题，则可能是因为你尚未分配相应的角色。 以下部分介绍存储资源管理器当前需要访问你的存储资源的权限。

如果不确定你具有相应的角色或权限，请与你的 Azure 帐户管理员联系。

#### <a name="read-listget-storage-accounts"></a>读取：列出/获取存储帐户

必须有权列出存储帐户。 可以通过分配"读者"角色来获取此权限。

#### <a name="list-storage-account-keys"></a>列出存储帐户密钥

存储资源管理器还可以使用帐户密钥进行身份验证请求。 可以获取访问密钥与更强大的角色，如"参与者"角色的权限。

> [!NOTE]
> 访问密钥向其保存的任何人授予不受限制的权限。 因此，通常不建议它们分发给用户帐户。 如果需要撤消访问密钥，你可以生成从[Azure 门户](https://portal.azure.com/)。

#### <a name="data-roles"></a>数据角色

您必须分配至少一个角色授予访问从资源读取数据。 例如，如果需要以列表或下载 blob，将至少需要"存储 Blob 数据读取者"角色。

### <a name="why-do-i-need-a-management-layer-role-to-see-my-resources-in-storage-explorer"></a>为何需要管理层角色，可以查看我在存储资源管理器中的资源？

Azure 存储包含两个层的访问权限：_管理_并_数据_。 通过管理层来访问订阅和存储帐户。 数据层可以通过访问容器、 blob 和其他数据资源。 例如，如果你想要从 Azure 获取存储帐户的列表，则管理终结点发送请求。 如果你想在帐户中的 blob 容器的列表，您向适当的服务终结点发送请求。

RBAC 角色可能包含用于管理或数据层访问权限。 "读者"角色，例如，向你授予只读访问权限管理层资源。

严格地说，"读者"角色不提供任何数据层权限，且不需要用于访问数据层。

存储资源管理器轻松访问你的资源收集有关您连接到 Azure 资源的必要信息。 例如，若要显示你的 blob 容器，存储资源管理器列表容器将请求发送到 blob 服务终结点。 若要获取该终结点，存储资源管理器搜索的订阅列表，并可以访问存储帐户。 但是，若要查找你的订阅和存储帐户，存储资源管理器，还需要对管理层的访问。

如果您没有授予任何管理层的权限的角色，存储资源管理器无法获取它需要连接到数据层的信息。

### <a name="what-if-i-cant-get-the-management-layer-permissions-i-need-from-my-administrator"></a>如果我无法获得管理层权限需要从我的管理员？

此时，我们还没有获得 RBAC 相关的解决方案。 解决此问题，可以请求一个 SAS URI[将附加到所需的资源](https://docs.microsoft.com/azure/vs-azure-tools-storage-manage-with-storage-explorer?tabs=linux#attach-a-service-by-using-a-shared-access-signature-sas)。

## <a name="error-self-signed-certificate-in-certificate-chain-and-similar-errors"></a>错误：证书链中的自签名证书（和类似错误）

证书错误是由以下两种情况之一导致的：

1. 应用通过“透明代理”连接，这意味着服务器（如公司服务器）在拦截 HTTPS 流量、对其解密，然后使用自签名证书对其加密。
2. 正在运行的应用程序正在向收到的 HTTPS 消息注入自签名 SSL 证书。 注入证书的应用程序示例包括防病毒软件和网络流量检查软件。

当存储资源管理器看到自签名或不受信任的证书时，无法再判断收到的 HTTPS 消息是否被更改。 如果拥有自签名证书的副本，可通过执行以下步骤，让存储资源管理器信任它：

1. 获取证书的 Base-64 编码 X.509 (.cer) 副本
2. 单击“编辑” > “SSL 证书” > “导入证书”，然后使用文件选取器查找、选择和打开 .cer 文件

此问题还有可能是由于存在多个证书（根证书和中间证书）造成的。 必须添加这两个证书才能解决错误。

如果你不确定该证书来源于何处，可以尝试执行以下步骤来找到它：

1. 安装 Open SSL
    * [Windows](https://slproweb.com/products/Win32OpenSSL.html)（任意轻量版本应该都满足要求）
    * Mac 和 Linux：应包含在操作系统中
2. 运行 Open SSL
    * Windows：打开安装目录，单击“/bin/”，然后双击“openssl.exe”。
    * Mac 和 Linux：从终端运行“openssl”。
3. 执行 `s_client -showcerts -connect microsoft.com:443`
4. 查找自签名证书。 如果您不确定哪个证书是自签名，请查找任何位置使用者`("s:")`和颁发者`("i:")`是相同的。
5. 找到任何自签名证书后，将每个证书中从“-----BEGIN CERTIFICATE-----”（含）到“-----END CERTIFICATE-----”（含）的部分复制和粘贴到新的 .cer 文件。
6. 打开存储资源管理器，单击“编辑” > “SSL 证书” > “导入证书”，然后使用文件选取器查找、选择和打开创建的 .cer 文件。

如果通过上述步骤无法找到任何自签名证书，请通过反馈工具联系我们以获取更多帮助。 或者，可以选择通过命令行使用 `--ignore-certificate-errors` 标志启动存储资源管理器。 使用此标志启动后，存储资源管理器将忽略证书错误。

## <a name="sign-in-issues"></a>登录问题

### <a name="blank-sign-in-dialog"></a>空白登录对话框

空白登录对话框通常导致由 ADFS 要求存储资源管理器来执行重定向，不支持将 Electron。 若要解决此问题，可以尝试使用设备代码流进行登录。 为此，请执行以下步骤：

1. "转到预览"->"使用设备代码登录"。
2. 打开“连接”对话框（通过左侧垂直栏上的插头图标或“帐户”面板上的“添加帐户”）。
3. 选择你想要登录到哪种的环境。
4. 单击“登录”按钮。
5. 按照下一个面板上的说明进行操作。

如果您发现自己想要使用，因为在默认浏览器已登录到不同的帐户的帐户登录遇到问题，您可以：

1. 手动将链接和代码复制到浏览器的私有会话中。
2. 手动将链接和代码复制到其他浏览器中。

### <a name="reauthentication-loop-or-upn-change"></a>重新验证循环或 UPN 更改

如果你处于重新验证循环中，或者已更改其中一个帐户的 UPN，请尝试以下操作：

1. 删除所有帐户，然后关闭存储资源管理器
2. 从计算机中删除 .IdentityService 文件夹。 在 Windows 中，该文件夹位于 `C:\users\<username>\AppData\Local`。 对于 Mac 和 Linux，可以在用户目录的根目录中找到该文件夹。
3. 如果使用的是 Mac 或 Linux，则还需要从 OS 的密钥存储中删除 Microsoft.Developer.IdentityService 条目。 在 Mac 上，密钥存储是“Gnome Keychain”应用程序。 对于 Linux，该应用程序通常称为“Keyring”，但名称可能会有所不同，具体取决于分发版。

### <a name="conditional-access"></a>条件性访问

在 Windows 10、Linux 或 macOS 上使用存储资源管理器时，不支持条件性访问。 这是由于存储资源管理器使用的 AAD 库中的某个限制导致的。

## <a name="mac-keychain-errors"></a>Mac 密钥链错误

有时，macOS 密钥链可能会进入导致存储资源管理器的身份验证库出现问题的状态。 若要此状态中获取密钥链，请尝试以下步骤：

1. 关闭存储资源管理器。
2. 打开密钥链（**cmd+space**、键入密钥链、按 Enter）。
3. 选择“登录”密钥链。
4. 单击挂锁图标以锁定密钥链（挂锁在完成后将对锁定位置进行动画处理，这可能需要几秒钟的时间，具体要取决于你打开的应用）。

    ![图像](./media/storage-explorer-troubleshooting/unlockingkeychain.png)

5. 启动存储资源管理器。
6. 应出现一个弹出窗口，其中显示“服务中心想要访问密钥链”。 如果是这样，请输入 Mac 管理员帐户密码，然后单击“始终允许”（如果“始终允许”不可用，则单击“允许”）。
7. 请尝试登录。

### <a name="general-sign-in-troubleshooting-steps"></a>常规登录故障排除步骤

* 如果您是在 macOS 上，并且在登录窗口永远不会将出现在"等待进行身份验证..."对话框中，然后重试[这些步骤](#mac-keychain-errors)
* 重启存储资源管理器
* 如果身份验证窗口为空，请等待至少一分钟，然后关闭身份验证对话框。
* 确保为计算机和存储资源管理器正确配置了代理和证书设置。
* 如果您是在 Windows 上并有权访问同一台计算机上的 Visual Studio 2017 并登录，请尝试登录到 Visual Studio 2017。 成功登录 Visual Studio 2017 后，应该可以打开存储资源管理器并在帐户面板中查看帐户。

如果这些方法均不起作用，请[在 GitHub 上提出问题](https://github.com/Microsoft/AzureStorageExplorer/issues)。

### <a name="missing-subscriptions-and-broken-tenants"></a>缺少订阅和中断的租户

如果成功登录后无法检索订阅，请尝试以下故障排除方法：

* 验证你的帐户是否有权访问所需的订阅。 可以通过登录到门户，想要使用的 Azure 环境中验证你的访问权限。
* 请确保使用正确的 Azure 环境登录（Azure、Azure 中国 21Vianet、Azure 德国、Azure 美国政府或自定义环境）。
* 如果使用代理，请确保已正确配置存储资源管理器代理。
* 尝试移除并重新添加帐户。
* 如果有“更多信息”链接，请查看针对失败的租户报告的错误消息。 如果不确定如何处理看到的错误消息，请随时[在 GitHub 上提出问题](https://github.com/Microsoft/AzureStorageExplorer/issues)。

## <a name="cannot-remove-attached-account-or-storage-resource"></a>无法删除附加的帐户或存储资源

如果无法通过 UI 删除附加的帐户或存储资源，可以通过删除以下文件夹来手动删除所有附加的资源：

* Windows：`%AppData%/StorageExplorer`
* macOS：`/Users/<your_name>/Library/Application Support/StorageExplorer`
* Linux：`~/.config/StorageExplorer`

> [!NOTE]
> 在删除上述文件夹之前关闭存储资源管理器。

> [!NOTE]
> 如果曾经导入了任何 SSL 证书，请备份 `certs` 目录的内容。 以后，可以使用备份来重新导入 SSL 证书。

## <a name="proxy-issues"></a>代理问题

首先，请确保输入的以下信息全部正确：

* 代理 URL 和端口号
* 用户名和密码（若代理需要）

> [!NOTE]
> 存储资源管理器不支持代理自动配置文件配置代理设置。

### <a name="common-solutions"></a>常见解决方法

如果仍遇到问题，请尝试以下故障排除方法：

* 若能不使用代理连接到 Internet，请验证存储资源管理器在不启用代理设置的情况下是否工作。 若是，则可能是代理设置出错。 请与代理管理员一起确定问题。
* 验证其他使用该代理服务器的应用程序是否按预期运行。
* 验证是否能够连接到尝试使用的 Azure 环境的门户
* 验证能否从服务终结点接收响应。 在浏览器中输入一个终结点 URL。 若能连接，会收到 InvalidQueryParameterValue 或类似的 XML响应。
* 如果其他人也通过你的代理服务器使用存储资源管理器，请验证他们能否连接。 若能，则你可能需要联系代理服务器管理员。

### <a name="tools-for-diagnosing-issues"></a>诊断问题的工具

若有网络服务工具（如 Fiddler for Windows），或许能够按以下操作诊断问题：

* 如果必须通过代理工作，则须将网络工具配置为通过代理连接。
* 检查网络工具使用的端口号。
* 在存储资源管理器中，输入本地主机 URL和网络工具的端口号作为代理设置。 如果操作无误，网络工具将开始记录存储资源管理器向管理和服务终结点发出的网络请求。 例如，如果在浏览器中输入 https://cawablobgrs.blob.core.windows.net/ 作为 Blob 终结点，将收到类似以下的响应，表示资源存在，尽管无法访问。

![代码示例](./media/storage-explorer-troubleshooting/4022502_en_2.png)

### <a name="contact-proxy-server-admin"></a>联系代理服务器管理员

如果代理设置正确，则可能需要联系代理服务器管理员，并

* 确保代理不会阻止流向 Azure 管理或资源终结点的流量。
* 验证代理服务器使用的身份验证协议。 目前存储资源管理器不支持 NTLM 代理。

## <a name="unable-to-retrieve-children-error-message"></a>“无法检索子级”错误消息

如果通过代理连接到 Azure，请验证代理设置是否正确。 如果您授予访问资源的订阅或帐户所有者，验证您具有读取或列出该资源的权限。

## <a name="connection-string-does-not-have-complete-configuration-settings"></a>连接字符串没有完整的配置设置

如果收到此错误消息，则表示你可能没有所需的权限来获取你的存储帐户的密钥。 若要确认是否如此，请转到门户并找到你的存储帐户。 快速，可以执行此操作通过你的存储帐户的节点，右键单击并单击"打开在门户中"。 执行此操作后，转到“访问密钥”边栏选项卡。 如果您没有权限查看密钥，您将看到消息"不能访问"页。 若要解决此问题，可以从其他人获取帐户密钥，并附加名称和密钥，或可以询问到存储帐户 sas，并使用它来附加存储帐户。

如果您看到的帐户密钥，以便我们可以帮助你解决此问题提出在 GitHub 上问题。

## <a name="issues-with-sas-url"></a>SAS URL 的问题

如果使用 SAS URL 连接到服务并遇到以下错误：

* 验证该 URL 是否提供读取和列出资源的必需权限。
* 验证该 URL 是否未过期。
* 如果 SAS URL建立在访问策略基础上，请验证该访问策略是否被撤销。

如果意外附加了无效的 SAS URL，并且无法分离，请执行以下步骤：

1. 运行存储资源管理器时，按 F12 打开开发人员工具窗口。
2. 单击“应用程序”选项卡，然后单击左侧树中的“本地存储”> file://。
3. 查找与有问题的 SAS URI 服务类型关联的键。 例如，如果用于 blob 容器的 SAS URI 错误，请查找名为 `StorageExplorer_AddStorageServiceSAS_v1_blob` 的键。
4. 键的值应为 JSON 数组。 查找与错误 URI 关联的对象，并将其删除。
5. 按 Ctrl+R 重新加载存储资源管理器。

## <a name="linux-dependencies"></a>Linux 依赖项

对于 Ubuntu 16.04 以外的 Linux 分发版，你可能需要手动安装某些依赖项。 一般情况下，以下包是必需的：

* [.NET Core 2.x](https://docs.microsoft.com/dotnet/core/linux-prerequisites?tabs=netcore2x)
* `libsecret`
* `libgconf-2-4`
* Up-to-date GCC

根据你的分发，可能需要安装其他包。 存储资源管理器[发行说明](https://go.microsoft.com/fwlink/?LinkId=838275&clcid=0x409)包含用于某些发行版的特定步骤。

## <a name="open-in-explorer-from-azure-portal-doesnt-work"></a>打开在资源管理器从 Azure 门户不起作用

如果在 Azure 门户上的"打开在资源管理器"按钮不起作用，，请确保使用兼容的浏览器。 已在以下浏览器测试的兼容性。
* Microsoft Edge
* Mozilla Firefox
* Google Chrome
* Microsoft Internet Explorer

## <a name="next-steps"></a>后续步骤

如果上述解决方法均不起作用，请[在 GitHub 上提出问题](https://github.com/Microsoft/AzureStorageExplorer/issues)。 也可以使用左下角的“向 GitHub 报告问题”按钮快速转到 GitHub。

![反馈](./media/storage-explorer-troubleshooting/feedback-button.PNG)
