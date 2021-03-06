---
title: 为 Azure Stack 集成系统部署生成 Azure Stack 公钥基础结构证书 | Microsoft Docs
description: 介绍 Azure Stack 集成系统的 Azure Stack PKI 证书部署过程。
services: azure-stack
documentationcenter: ''
author: mattbriggs
manager: femila
ms.service: azure-stack
ms.workload: na
pms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 01/25/2019
ms.author: mabrigg
ms.reviewer: ppacent
ms.lastreviewed: 01/25/2019
ms.openlocfilehash: 9d358c021f795172e7ced0ba2a2f309a0a0dab6e
ms.sourcegitcommit: a4efc1d7fc4793bbff43b30ebb4275cd5c8fec77
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/21/2019
ms.locfileid: "56649721"
---
# <a name="azure-stack-certificates-signing-request-generation"></a>Azure Stack 证书签名请求生成

Azure Stack 就绪性检查器工具可用于创建证书签名请求 (Csr) 适用于 Azure Stack 部署。 应该花费足够的时间来请求、生成并验证证书，以便在部署之前进行测试。 您可以获得工具[从 PowerShell 库](https://aka.ms/AzsReadinessChecker)。

Azure Stack 就绪性检查器工具 (AzsReadinessChecker) 可用于请求的以下证书：

- **标准证书申请**根据[为 Azure Stack 部署生成 PKI 证书](azure-stack-get-pki-certs.md)。
- **平台即服务**:可以请求 [Azure Stack 公钥基础结构证书要求 - 可选的 PaaS 证书](azure-stack-pki-certs.md#optional-paas-certificates)中指定的证书的平台即服务 (PaaS) 名称。

## <a name="prerequisites"></a>必备组件

在为 Azure Stack 部署生成 PKI 证书的 CSR 之前，系统应符合以下先决条件：

- Microsoft Azure Stack Readiness Checker
- 证书属性：
  - 区域名称
  - 外部完全限定的域名 (FQDN)
  - 主题
- Windows 10 或 Windows Server 2016

  > [!NOTE]  
  > 从证书颁发机构收回证书时，需要在同一个系统上完成[准备 Azure Stack PKI 证书](azure-stack-prepare-pki-certs.md)中的步骤！

## <a name="generate-certificate-signing-requests"></a>生成证书签名请求

使用以下步骤来准备和验证 Azure Stack PKI 证书：

1. 在 PowerShell 提示符（5.1 或更高版本）下，运行以下 cmdlet 安装 AzsReadinessChecker：

    ```PowerShell  
        Install-Module Microsoft.AzureStack.ReadinessChecker
    ```

2. 将**使用者**声明为有序字典。 例如：

    ```PowerShell  
    $subjectHash = [ordered]@{"OU"="AzureStack";"O"="Microsoft";"L"="Redmond";"ST"="Washington";"C"="US"}
    ```

    > [!note]  
    > 如果提供公用名 (CN)，此值将被证书请求的第一个 DNS 名称覆盖。

3. 声明已存在的输出目录。 例如：

    ```PowerShell  
    $outputDirectory = "$ENV:USERPROFILE\Documents\AzureStackCSR"
    ```

4. 声明标识系统

    Azure Active Directory

    ```PowerShell
    $IdentitySystem = "AAD"
    ```

    Active Directory 联合身份验证服务

    ```PowerShell
    $IdentitySystem = "ADFS"
    ```

5. 声明用于 Azure Stack 部署的**区域名称**和**外部 FQDN**。

    ```PowerShell
    $regionName = 'east'
    $externalFQDN = 'azurestack.contoso.com'
    ```

    > [!note]  
    > `<regionName>.<externalFQDN>` 构成了 Azure Stack 中所有外部 DNS 名称创建位置的基础，在此示例中，门户是 `portal.east.azurestack.contoso.com`。  

6. 若要为每个 DNS 名称生成证书签名请求，请执行以下命令：

    ```PowerShell  
    New-AzsCertificateSigningRequest -RegionName $regionName -FQDN $externalFQDN -subject $subjectHash -OutputRequestPath $OutputDirectory -IdentitySystem $IdentitySystem
    ```

    若要包括 PaaS 服务，请指定开关 ```-IncludePaaS```

7. 另外，对于开发/测试环境，若要生成具有多个使用者可选名称的单个证书请求，请添加 **-RequestType SingleCSR** 参数和值（**不**建议用于生产环境）：

    ```PowerShell  
    New-AzsCertificateSigningRequest -RegionName $regionName -FQDN $externalFQDN -subject $subjectHash -RequestType SingleCSR -OutputRequestPath $OutputDirectory -IdentitySystem $IdentitySystem
    ```

    若要包括 PaaS 服务，请指定开关 ```-IncludePaaS```

8. 查看输出：

    ```PowerShell  
    New-AzsCertificateSigningRequest v1.1809.1005.1 started.

    CSR generating for following SAN(s): dns=*.east.azurestack.contoso.com&dns=*.blob.east.azurestack.contoso.com&dns=*.queue.east.azurestack.contoso.com&dns=*.table.east.azurestack.cont
    oso.com&dns=*.vault.east.azurestack.contoso.com&dns=*.adminvault.east.azurestack.contoso.com&dns=portal.east.azurestack.contoso.com&dns=adminportal.east.azurestack.contoso.com&dns=ma
    nagement.east.azurestack.contoso.com&dns=adminmanagement.east.azurestack.contoso.com*dn2=*.adminhosting.east.azurestack.contoso.com@dns=*.hosting.east.azurestack.contoso.com
    Present this CSR to your Certificate Authority for Certificate Generation: C:\Users\username\Documents\AzureStackCSR\wildcard_east_azurestack_contoso_com_CertRequest_20180405233530.req
    Certreq.exe output: CertReq: Request Created

    Log location (contains PII): C:\Users\username\AppData\Local\Temp\AzsReadinessChecker\AzsReadinessChecker.log
    New-AzsCertificateSigningRequest Completed
    ```

9. 将生成的 **.REQ** 文件提交到 CA（内部或公共 CA）。  **New-AzsCertificateSigningRequest** 的输出目录包含提交到证书颁发机构时所需的 CSR。  此目录还包含一个子目录，其中包含生成证书请求期间使用的 INF 文件，供你参考。 请确保 CA 使用符合 [Azure Stack PKI 要求](azure-stack-pki-certs.md)的生成请求来生成证书。

## <a name="next-steps"></a>后续步骤

[准备 Azure Stack PKI 证书](azure-stack-prepare-pki-certs.md)
