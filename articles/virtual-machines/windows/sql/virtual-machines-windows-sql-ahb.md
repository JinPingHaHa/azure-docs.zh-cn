---
title: 如何在 Azure 中更改 SQL Server VM 的许可模型 | Microsoft Docs
description: 了解如何在 Azure 中切换 SQL 虚拟机的许可。
services: virtual-machines-windows
documentationcenter: na
author: MashaMSFT
manager: craigg
tags: azure-resource-manager
ms.assetid: aa5bf144-37a3-4781-892d-e0e300913d03
ms.service: virtual-machines-sql
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: vm-windows-sql-server
ms.workload: iaas-sql-server
ms.date: 02/13/2019
ms.author: mathoma
ms.reviewer: jroth
ms.openlocfilehash: 66e94ed4f68ed43891ad3e81bd66cdc57799d204
ms.sourcegitcommit: 2d0fb4f3fc8086d61e2d8e506d5c2b930ba525a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/18/2019
ms.locfileid: "58117891"
---
# <a name="how-to-change-the-licensing-model-for-a-sql-server-virtual-machine-in-azure"></a>如何在 Azure 中更改 SQL Server 虚拟机的许可模型
本文介绍如何在 Azure 中使用新的 SQL VM 资源提供程序 **Microsoft.SqlVirtualMachine** 来更改 SQL Server 虚拟机的许可模型。 有两个许可模型为虚拟机 (VM) 托管 SQL Server 的即用即付，并自带许可 (BYOL)。 现在可以通过 PowerShell 或 Azure CLI 对 SQL Server VM 使用哪个许可模型进行修改。 

**即用即付**(PAYG) 模型的推出意味着 Azure VM 运行的每秒费用包括 SQL Server 许可证的费用。

**自带的自己的许可证**(BYOL) 模型是也称为[Azure 混合权益 (AHB)](https://azure.microsoft.com/pricing/hybrid-benefit/)，并且可以将 SQL Server 许可证用于运行 SQL Server 的虚拟机。 有关价格的详细信息，请参阅 [SQL Server VM 定价指南](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-pricing-guidance)。

在两个许可证模型之间进行切换不会导致停机，不会重启 VM，不会增加费用（事实上，激活 AHB 会降低费用），并且会立即生效。 

  >[!NOTE]
  > - 当前，仅当从即用即付 SQL Server VM 映像开始时，才能使用转换许可模型的功能。 如果从门户首先使用自带许可映像，则无法将该映像转换为即用即付。
  > - CSP 客户可通过首先部署即用即付 VM，然后将它转换为自带许可，来利用 AHB 权益。 
  > - 当前仅对公有云安装启用此功能。


## <a name="prerequisites"></a>必备组件
使用 SQL VM 资源提供程序需要安装 SQL IaaS 扩展。 因此，若要继续利用 SQL VM 提供程序，需要：
- 一个 [Azure 订阅](https://azure.microsoft.com/free/)。
- [软件保障](https://www.microsoft.com/licensing/licensing-programs/software-assurance-default)。 
- 一个*即用即付* [SQL Server 虚拟机](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-server-provision)与[SQL IaaS 扩展](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-agent-extension)安装。 


## <a name="register-sql-resource-provider-with-your-subscription"></a>将 SQL 资源提供程序注册到订阅 

在许可模型之间进行切换是新的 SQL VM 资源提供程序 (Microsoft.SqlVirtualMachine) 提供的一项功能。 在 2018 年 12 月之后部署的 SQL Server VM 会自动注册到新的资源提供程序。 但是，在此日期之前部署的现有 VM 需要手动注册到资源提供程序，然后它们才能切换许可模型。 

  > [!NOTE] 
  > 如果删除了 SQL Server VM 资源，则会回退到映像的硬编码许可证设置。 

若要向 SQL 资源提供程序注册 SQL Server VM，必须将资源提供程序注册到订阅。 您可以这样做，使用 Azure CLI、 PowerShell、 或使用 Azure 门户。 

### <a name="with-the-azure-portal"></a>使用 Azure 门户
以下步骤使用 Azure 门户将 SQL 资源提供程序注册到 Azure 订阅。 

1. 打开 Azure 门户，导航到“所有服务”。 
1. 导航到“订阅”，选择感兴趣的订阅。  
1. 在“订阅”边栏选项卡中，导航到“资源提供程序”。 
1. 在筛选器中键入 `sql`，以便显示与 SQL 相关的资源提供程序。 
1. 根据所需操作为 **Microsoft.SqlVirtualMachine** 提供程序选择“注册”、“重新注册”或“取消注册”。 

   ![修改提供程序](media/virtual-machines-windows-sql-ahb/select-resource-provider-sql.png)

### <a name="with-azure-cli"></a>使用 Azure CLI
下面的代码片段将 SQL 资源提供程序注册到 Azure 订阅。 

```cli
# Register the new SQL resource provider for your subscription 
az provider register --namespace Microsoft.SqlVirtualMachine 
```

### <a name="with-powershell"></a>使用 PowerShell
下面的代码片段将 SQL 资源提供程序注册到 Azure 订阅。 

```powershell
# Register the new SQL resource provider for your subscription
Register-AzResourceProvider -ProviderNamespace Microsoft.SqlVirtualMachine
```


## <a name="register-sql-server-vm-with-sql-resource-provider"></a>将 SQL Server VM 注册到 SQL 资源提供程序
SQL 资源提供程序已注册后与你的订阅，您可以向资源提供程序中注册 SQL Server VM。 您可以使用 Azure CLI 和 PowerShell 来完成。 

### <a name="with-azure-cli"></a>使用 Azure CLI

注册 SQL Server 虚拟机使用以下代码片段中使用 Azure CLI: 

```cli
# Register your existing SQL Server VM with the new resource provider
az sql vm create -n <VMName> -g <ResourceGroupName> -l <VMLocation>
```

### <a name="with-powershell"></a>使用 PowerShell

注册 SQL Server 虚拟机使用以下代码片段使用 PowerShell: 
```powershell
# Register your existing SQL Server VM with the new resource provider
# example: $vm=Get-AzureRmVm -ResourceGroupName AHBTest -Name AHBTest
$vm=Get-AzureRmVm -ResourceGroupName <ResourceGroupName> -Name <VMName>
New-AzureRmResource -ResourceName $vm.Name -ResourceGroupName $vm.ResourceGroupName -Location $vm.Location -ResourceType Microsoft.SqlVirtualMachine/sqlVirtualMachines -Properties @{virtualMachineResourceId=$vm.Id}
```


## <a name="change-licensing-model"></a>更改授权模型
使用资源提供程序注册到 SQL Server VM 后, 可以更改使用 Azure 门户、 Azure CLI 或 PowerShell 的许可模式。 


  >[!NOTE]
  >  当前，仅当从即用即付 SQL Server VM 映像开始时，才能使用转换许可模型的功能。 如果从门户首先使用自带许可映像，则无法将该映像转换为即用即付。 

### <a name="with-the-azure-portal"></a>使用 Azure 门户
您可以修改直接从门户的授权模型。 

1. 导航到 SQL Server VM 内[Azure 门户](https://portal.azure.com)。 
1. 选择**SQL Server 配置**中**设置**窗格。 
1. 选择**编辑**中**SQL Server 许可证**窗格，可以修改该许可证。 

![在门户中的 AHB](media/virtual-machines-windows-sql-ahb/ahb-in-portal.png)

  >[!NOTE]
  > 此选项不可用的自带的自己的许可证映像。 

### <a name="with-azure-cli"></a>使用 Azure CLI
可以通过 Azure CLI 更改许可模型。  

下面的代码段将切换到 BYOL （或使用 Azure 混合权益） 即用即付许可证模型：
```azurecli
# Switch  your SQL Server VM license from pay-as-you-go to bring-your-own
# example: az sql vm update -n AHBTest -g AHBTest --license-type AHUB

az sql vm update -n <VMName> -g <ResourceGroupName> --license-type AHUB
```

下面的代码段将切换到即用即付 BYOL 模型： 
```azurecli
# Switch  your SQL Server VM license from bring-your-own to pay-as-you-go
# example: az sql vm update -n AHBTest -g AHBTest --license-type PAYG

az sql vm update -n <VMName> -g <ResourceGroupName> --license-type PAYG
```

### <a name="with-powershell"></a>使用 PowerShell 
可以使用 PowerShell 更改许可模型。 

下面的代码段将切换到 BYOL （或使用 Azure 混合权益） 即用即付许可证模型： 
```PowerShell
# Switch  your SQL Server VM license from pay-as-you-go to bring-your-own
#example: $SqlVm = Get-AzResource -ResourceType Microsoft.SqlVirtualMachine/SqlVirtualMachines -ResourceGroupName AHBTest -ResourceName AHBTest

$SqlVm = Get-AzResource -ResourceType Microsoft.SqlVirtualMachine/SqlVirtualMachines -ResourceGroupName <resource_group_name> -ResourceName <VM_name>
$SqlVm.Properties.sqlServerLicenseType="AHUB"
<# the following code snippet is only necessary if using Azure Powershell version > 4
$SqlVm.Kind= "LicenseChange"
$SqlVm.Plan= [Microsoft.Azure.Management.ResourceManager.Models.Plan]::new()
$SqlVm.Sku= [Microsoft.Azure.Management.ResourceManager.Models.Sku]::new() #>
$SqlVm | Set-AzResource -Force 
```

下面的代码段将切换到即用即付 BYOL 模型：
```PowerShell
# Switch  your SQL Server VM license from bring-your-own to pay-as-you-go
#example: $SqlVm = Get-AzResource -ResourceType Microsoft.SqlVirtualMachine/SqlVirtualMachines -ResourceGroupName AHBTest -ResourceName AHBTest

$SqlVm = Get-AzResource -ResourceType Microsoft.SqlVirtualMachine/SqlVirtualMachines -ResourceGroupName <resource_group_name> -ResourceName <VM_name>
$SqlVm.Properties.sqlServerLicenseType="PAYG"
<# the following code snippet is only necessary if using Azure Powershell version > 4
$SqlVm.Kind= "LicenseChange"
$SqlVm.Plan= [Microsoft.Azure.Management.ResourceManager.Models.Plan]::new()
$SqlVm.Sku= [Microsoft.Azure.Management.ResourceManager.Models.Sku]::new() #>
$SqlVm | Set-AzResource -Force 
``` 


## <a name="view-current-licensing"></a>查看当前许可 

可以使用以下代码片段查看 SQL Server VM 的当前许可模型。 

```PowerShell
# View current licensing model for your SQL Server VM
#example: $SqlVm = Get-AzResource -ResourceType Microsoft.SqlVirtualMachine/SqlVirtualMachines -ResourceGroupName <resource_group_name> -ResourceName <VM_name>

$SqlVm = Get-AzResource -ResourceType Microsoft.SqlVirtualMachine/SqlVirtualMachines -ResourceGroupName <resource_group_name> -ResourceName <VM_name>
$SqlVm.Properties.sqlServerLicenseType
```

## <a name="known-errors"></a>已知错误

### <a name="sql-iaas-extension-is-not-installed-on-virtual-machine"></a>虚拟机上未安装 SQL IaaS 扩展
必须安装 SQL IaaS 扩展才能将 SQL Server VM 注册到 SQL VM 资源提供程序。 如果尝试在安装 SQL IaaS 扩展之前注册 SQL Server VM，将遇到以下错误：

`Sql IaaS Extension is not installed on Virtual Machine: '{0}'. Please make sure it is installed and in running state and try again later.`

若要解决此问题，请在尝试注册 SQL Server VM 之前先安装 SQL IaaS 扩展。 

  > [!NOTE]
  > 安装 SQL IaaS 扩展会重启 SQL Server 服务，请只在维护时段进行安装。 有关详细信息，请参阅 [SQL IaaS 扩展安装](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-agent-extension#installation)。 

### <a name="cannot-validate-argument-on-parameter-sku"></a>无法验证参数“Sku”中的自变量
尝试使用 4.0 以上版本的 Azure PowerShell 更改 SQL Server VM 许可模型时，可能会遇到以下错误：

`Set-AzResource : Cannot validate argument on parameter 'Sku'. The argument is null or empty. Provide an argument that is not null or empty, and then try the command again.`

若要解决此错误，请在切换许可模型时，取消注释上述 PowerShell 代码片段中的以下行： 
```PowerShell
# the following code snippet is necessary if using Azure Powershell version > 4
$SqlVm.Kind= "LicenseChange"
$SqlVm.Plan= [Microsoft.Azure.Management.ResourceManager.Models.Plan]::new()
$SqlVm.Sku= [Microsoft.Azure.Management.ResourceManager.Models.Sku]::new()
```

使用以下代码验证 Azure PowerShell 版本：

```PowerShell
Get-Module -ListAvailable -Name Azure -Refresh
```

### <a name="the-resource-microsoftsqlvirtualmachinesqlvirtualmachinesresource-group-under-resource-group-resource-group-was-not-found-the-property-sqlserverlicensetype-cannot-be-found-on-this-object-verify-that-the-property-exists-and-can-be-set"></a>找不到资源 Microsoft.SqlVirtualMachine/SqlVirtualMachines/ < 资源组 > 资源组 < 资源组 > 下。 此对象上找不到 sqlServerLicenseType 的属性。 验证属性存在并且可以设置。
不向 SQL 资源提供程序注册 SQL Server VM 时，将发生此错误。 将需要注册资源提供程序与你[订阅](#register-sql-resource-provider-with-your-subscription)，然后使用 SQL 注册 SQL Server 虚拟机[资源提供程序](#register-sql-server-vm-with-sql-resource-provider)。 

## <a name="next-steps"></a>后续步骤

有关详细信息，请参阅以下文章： 

* [Windows VM 上的 SQL Server 概述](virtual-machines-windows-sql-server-iaas-overview.md)
* [Windows VM 上的 SQL Server 常见问题解答](virtual-machines-windows-sql-server-iaas-faq.md)
* [Windows VM 上的 SQL Server 定价指南](virtual-machines-windows-sql-server-pricing-guidance.md)
* [Windows VM 上的 SQL Server 发行说明](virtual-machines-windows-sql-server-iaas-release-notes.md)


