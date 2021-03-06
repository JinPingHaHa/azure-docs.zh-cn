---
title: 使用 Azure 中的 Cloudyn 仪表板查看关键指标 | Microsoft Docs
description: 本文介绍如何使用 Cloudyn 中的仪表板查看关键指标。
services: cost-management
keywords: ''
author: bandersmsft
ms.author: banders
ms.date: 12/07/2018
ms.topic: conceptual
ms.service: cost-management
manager: vitavor
ms.custom: seodec18
ms.openlocfilehash: f232ee89993998eb25ecce73e9c2ac8e08f3198b
ms.sourcegitcommit: 9fb6f44dbdaf9002ac4f411781bf1bd25c191e26
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/08/2018
ms.locfileid: "53094095"
---
# <a name="view-key-cost-metrics-with-dashboards"></a>使用仪表板查看关键成本指标

Cloudyn 中的仪表板提供报表的高级别视图。 通过仪表板，可在单个视图中查看关键成本指标。 此外，仪表板还着重体现业务趋势，帮助做出重要的业务决策。

还可使用仪表板为组织中具有不同职责的人员创建视图，这些人员可能包括：

- 财务总监
- 应用程序或项目所有者
- DevOps 工程师
- 高管人员

仪表板由小组件组成，每个小组件实质上为报表缩略图。 单击小组件打开其报表。 自定义报表时，将它们保存至“我的报表”，即可将其添加到仪表板中。

管理 (MSP)、企业和高级 Cloudyn 用户的仪表板版本有所不同。 其差异取决于实体访问级别。 有关访问级别的详细信息，请参阅[实体访问级别](tutorial-user-access.md#entity-access-levels)。

仪表板可用性取决于查看仪表板时使用的云服务提供商帐户的类型。 由 Cloudyn 收集的可用信息类型会影响仪表板中的报表。 例如，如果没有 AWS 帐户，则无法看到 S3 跟踪器仪表板。 同样，如果未启用 Azure 资源管理器对 Cloudyn 的访问权限，将无法查看优化器仪表板小组件中的任何特定于 Azure 的信息。

可以使用任何预制仪表板，或者可以使用自定义报表创建自己的仪表板。 如果不熟悉 Cloudyn 报表，请参阅[使用 Cloudyn 报表](use-reports.md)。

## <a name="create-a-custom-dashboard"></a>创建自定义仪表板

若要快速开始使用自定义仪表板，可以复制现有仪表板以使用其属性。 然后可以修改该仪表板，以满足你的需要。 在想要复制的仪表板上，单击“另存为”。 只能复制自定义仪表板，无法复制 Cloudyn 中包含的仪表板。

若要创建自定义仪表板：

1. 在主页上，单击“新增 +”。 将显示“我的仪表板”页。  
    ![供添加新报表的“我的仪表板”页面](./media/dashboards/my-dashboard.png)
2. 单击“添加新报表”。 将显示“添加报表”框。
3. 选择想要添加到仪表板小组件的报表。 小组件被添加到仪表板。
4. 在仪表板完成前，重复以上步骤。
5. 若要更改仪表板的名称，单击仪表板主页上的仪表板名称并键入新名称。

## <a name="modify-a-custom-dashboard"></a>修改自定义仪表板

与创建自定义仪表板的情况类似，Cloudyn 中包含的仪表板同样无法修改。 若要修改自定义仪表板报表：

1. 在仪表板中，找到想要修改的报表并单击“编辑”。 将显示该报表。
2. 对报表进行任何想要的更改并单击“保存”。 将更新报表并显示更改内容。

## <a name="share-a-custom-dashboard"></a>共享自定义仪表板

可将自定义仪表板放至“公共”或“我的实体”，与其他人员共享。 当共享至“公共”时，所有用户都可以查看仪表板。 当共享至“我的实体”时，只有具有当前实体访问权限的用户才可以查看仪表板。 与“公共”共享自定义仪表板的步骤和与“我的实体”共享自定义仪表板的步骤类似。

若要将自定义仪表板共享至“公共”：

1. 在仪表板中，单击“仪表板设置”。 将显示“仪表板设置”框。  
    ![自定义仪表板的仪表板设置](./media/dashboards/dashboard-options.png)
2. 在“仪表板设置”框中，单击箭头符号，然后单击“公共”。 将显示公共仪表板确认对话框。
3. 单击“是”。 仪表板现在可供其他人员使用。

## <a name="delete-a-custom-dashboard-report"></a>删除自定义仪表板报表

可以从仪表板中删除自定义报表组件。 从仪表板中删除报表时，并不会将其从报表列表中删除。 相反，删除报表只会将其从仪表板中删除。

若要删除仪表板组件，在仪表板组件上，单击“删除”。 单击“删除”将立即删除仪表板组件。

## <a name="share-a-dashboard-enterprise"></a>共享仪表板（企业版）

可以将自定义仪表板共享给组织中的所有用户或与当前实体的用户共享。 可以通过共享仪表板，让其他人员即刻看到自己的 KPI 高级别视图。 共享仪表板时，会自动将仪表板复制给所有 Cloudyn 实体/客户。 将自动更新对共享仪表板的更改。

若要与包括子实体的所有用户共享仪表板，请执行以下操作：

1. 在仪表板主页上，单击“编辑”。
2. 单击“共享”，然后选择“公共”。
3. 将显示全局公共仪表板确认框。
4. 单击“是”，将仪表板设置为全局公共仪表板。

若要与当前实体的所有用户共享仪表板，请执行以下操作：

1. 从仪表板主页上，单击“编辑”。
2. 单击“共享”，然后选择“我的实体”。
3. 单击“是”，将仪表板设置为公共仪表板。

## <a name="duplicate-a-custom-dashboard"></a>复制自定义仪表板

创建新仪表板时，你可能想要使用现有仪表板中的类似属性。 可以复制仪表板以创建新仪表板。

只可复制自定义仪表板。 不能复制标准仪表板。

若要复制（克隆）自定义仪表板，请执行以下操作：

1. 在想要复制的仪表板上，单击“另存为”。 将打开一个具有相同名称和一个编号的新仪表板。
2. 根据需要重命名复制的仪表板并对其进行修改。

-或-

1. 在“仪表板设置”中，在想要复制的仪表板行上单击“另存为”。
2. 将打开复制的仪表板。
3. 根据需要重命名仪表板并对其进行修改。

## <a name="set-a-default-dashboard"></a>设置默认仪表板

可将任意仪表板设置为默认仪表板。 将仪表板设置为默认仪表板，该仪表板将显示为仪表板选项卡列表中最左侧的选项卡。 打开 Cloudyn 门户时，将显示默认仪表板。

- 单击想要设置为默认仪表板的仪表板选项卡，然后在右侧单击“默认”。

-或-

1. 单击“仪表板设置”，查看可用的仪表板列表并选择想要设置为默认仪表板的仪表板。  
    ![自定义仪表板的仪表板选项](./media/dashboards/dashboard-options.png)
2. 在仪表板行中，单击“默认”。 将显示默认仪表板确认框。
3. 单击 **“是”**。 该仪表板被设置为默认仪表板。

## <a name="management-dashboard"></a>“管理”仪表板
“管理”（或 MSP 用户的 MSP 仪表板）仪表板包括主报表类型的突出显示。  
![显示各种报表的管理仪表板](./media/dashboards/management-dash.png)

### <a name="cost-entity-summary-enterprise-only"></a>成本实体摘要（仅适用于企业）
此小组件总结托管的成本实体，包括实体数和帐户数。
- 单击此小组件可打开企业详情报表。

### <a name="cost-over-time"></a>时段成本
此小组件可帮助发现成本趋势。 它根据过去 30 天的趋势，突出显示最后一天的成本。
- 单击此小组件可打开实际时段成本报表，以查看并筛选其他详细信息。

### <a name="asset-controller"></a>资产控制器
此小组件突出显示前一天的运行实例数，高于过去 30 天的使用趋势。
- 单击此小组件可打开资产控制器仪表板。

### <a name="unused-ri-detector"></a>未使用的 RI 检测程序
此小组件突出显示 Amazon EC2 未使用的预留数。
- 单击此小组件可打开当前未使用的预留报表，在该报表中，可查看可修改的未使用预留。

### <a name="cost-by-service"></a>按服务划分的费用
此小组件突出显示过去 30 天按服务划分的摊余成本。 将鼠标悬停在饼图上可查看每项服务的成本。
- 单击此小组件可打开实际成本分析报表。

### <a name="potential-savings"></a>可能的节省额
此小组件显示 Amazon EC2 和 Amazon RDS 的实例类型定价建议。
- 单击此小组件打开节省额分析报表。 该报表列出了按实例类型划分的包含可能的节省额的成本。

### <a name="compute-instances---daily-trend"></a>计算实例 - 每日趋势
此小组件显示按类型划分的过去 30 天的活动实例。
- 单击此小组件可打开时段实例报表，在该报表中，可查看过去 30 天运行的所有实例的细目。

### <a name="storage-by-department"></a>按部门划分的存储
此小组件显示由部门使用的存储服务。 将鼠标悬停在饼图上可查看按部门划分的存储消耗。
- 单击此小组件可打开 S3 跟踪器仪表板。

## <a name="cost-controller-dashboard"></a>成本控制器仪表板
成本控制器仪表板显示预设成本分配突出显示。  
![显示各种报表的成本控制器仪表板](./media/dashboards/cost-controller-dashboard.png)

### <a name="cost-over-time"></a>时段成本
此小组件帮助发现成本趋势。 它根据过去 30 天的趋势，突出显示最后一天的成本。
- 单击此小组件可打开实际时段成本报表，以查看并筛选其他详细信息。

### <a name="monthly-cost-trends"></a>月度成本趋势
此小组件突出显示本月初以来的预计摊销支出和实际支出。
- 单击此小组件可打开本月预计成本报表，其中提供本月至今累计的成本摘要。

此报表显示从月初开始的成本、上个月的成本和本月预计的成本。 最新的每月成本与预计成本相加即可计算出本月预计成本。 预计成本根据过去 30 天监测的成本得出。

### <a name="12-month-planner"></a>12 个月规划表
此小组件突出显示接下来 12 个月的预计成本和可能的节省额。
- 单击此小组件可打开年度预计成本报表。

### <a name="cost-by-service"></a>按服务划分的费用
此小组件突出显示过去 30 天按服务划分的摊余成本。
- 将鼠标悬停在饼图上可查看每项服务的成本。
- 单击此小组件可打开实际成本分析报表。

### <a name="cost-by-account"></a>按帐户划分的成本
此小组件突出显示过去 30 天按帐户划分的摊余成本。
- 将鼠标悬停在饼图上可查看每个帐户的成本。
- 单击此小组件可打开实际成本分析报表。

### <a name="cost-trend-by-day"></a>按天划分的成本趋势
此小组件突出显示过去 30 天的支出。
- 将鼠标悬停在条形图上可查看每日成本。
- 单击此小组件可打开实际时段成本报表。

### <a name="cost-trend-by-month---last-6-months"></a>按月划分的成本趋势 - 过去 6 个月

此小组件突出显示过去六个月的支出。
- 将鼠标悬停在条形图上可查看每月成本。
- 单击此小组件可打开实际时段成本报表。

## <a name="asset-controller-dashboard"></a>资产控制器仪表板

该仪表板显示运行实例数、可用和正在使用的磁盘、实例类型分发和存储信息。  
![显示各种报表的资产控制器仪表板](./media/dashboards/asset-controller-dashboard.png)

### <a name="compute-instances"></a>计算实例
此小组件根据过去 30 天的使用趋势显示运行实例数。
- 单击此小组件可打开时段实例报表。

### <a name="disks"></a>磁盘
此小组件突出显示正在使用和可用的磁盘的总数和卷数。
- 单击此小组件可打开活动磁盘报表。

### <a name="instance-type-distribution"></a>实例类型分发
此小组件突出显示饼图中的实例类型。
- 单击此小组件可打开实例分发报表，其中提供按所选聚合划分的活动实例的细目。

### <a name="compute-instances---daily-trend"></a>计算实例 - 每日趋势
此小组件突出显示过去 30 天的每日计算实例（发现、预留和按需）。
- 将鼠标悬停在该图上可查看每日每种类型的计算实例数。
- 单击此小组件可打开时段实例报表。

### <a name="all-buckets-s3"></a>所有存储桶 (S3)
此小组件突出显示总 S3 存储和存储的对象数。
- 单击此小组件可打开 S3 跟踪器仪表板。 该仪表板可帮助查找、分析和显示当前存储使用情况和趋势。

### <a name="sql-db-instances-rds"></a>SQL 数据库实例 (RDS)
此小组件根据过去 30 天的趋势，突出显示运行 Amazon RDS 实例数。
- 单击此小组件可打开时段 RDS 实例报表。

## <a name="optimizer-dashboard"></a>优化器仪表板
此仪表板显示精简建议、未使用的资源和可能的节省额。  
![显示各种报表的优化器仪表板](./media/dashboards/optimizer-dashboard.png)

### <a name="ri-calculator"></a>RI 计算器
此小组件显示 RI 购买建议数，并突出显示可能的年度节省额。
- 单击此小组件可打开预留实例计算器，在该计算器中，可确定使用按需和预留定价计划的时间。

### <a name="sizing"></a>调整大小
此小组件突出显示建议调整的可能的节省额（若实现）。
- 单击此小组件可打开 EC2 成本效益调整建议报表。

### <a name="unused-ri-detector"></a>未使用的 RI 检测程序
此小组件突出显示 Amazon EC2 未使用的预留数。
- 单击此小组件可打开当前未使用的预留报表，在该报表中，可查看可修改的未使用预留。

###  <a name="available-disks"></a>可用磁盘
此小组件突出显示部署中未附加的磁盘数。
- 单击此小组件可打开未附加的磁盘报表。

### <a name="rds-ri-calculator"></a>RDS RI 计算器
此小组件突出显示 Amazon RDS 实例和可能的节省额的预留建议数。
- 单击此小组件可打开 RDS RI 购买建议报表，在该报表中，可查看 Cloudyn 建议以使用预留实例而不是按需实例。

### <a name="rds-sizing"></a>RDS 大小调整
此小组件显示大小调整建议数和可能的节省额。
- 单击此小组件可打开 RDS 大小调整建议报表，该报表显示了详细的 Amazon RDS 大小调整建议。

优化建议基于上个月监控的使用情况和性能数据。

## <a name="s3-tracker-dashboard"></a>S3 跟踪器仪表板
S3 跟踪器仪表板可帮助查找、分析和显示当前存储使用情况和趋势。  
![显示各种报表的 S3 跟踪器仪表板](./media/dashboards/s3-tracker-dashboard.png)

### <a name="all-buckets"></a>所有存储桶
此小组件突出显示所有存储桶的总小大 (GB) 和存储桶中的总对象数。
- 单击此小组件可打开 S3 大小的分发报表。 该报表可帮助按存储桶、顶层文件夹、存储类和版本状态来分析 S3 大小。

### <a name="bucket-properties"></a>存储桶属性
此小组件突出显示存储存储桶的总数。
- 单击此小组件可查看 S3 存储桶属性报表。

### <a name="scan-status"></a>扫描状态
此小组件突出显示上一次 S3 扫描完成的时间和下一次将开始扫描的时间。
- 单击此小组件可打开 S3 扫描状态报表。

### <a name="storage-by-bucket"></a>按存储桶划分的存储
此小组件突出显示每个存储桶存储类正在使用的百分比。
- 单击此小组件可打开 S3 大小的分发报表。 该报表可帮助按存储桶、顶层文件夹、存储类和版本状态来分析 S3 大小。

### <a name="number-of-objects-by-bucket"></a>按存储桶划分的对象数
此小组件以实际数量和百分比突出显示每个存储桶的对象数。 将鼠标悬停在存储桶上可查看总对象数。
- 单击此小组件可打开 S3 大小的分发报表（基于扫描）。

## <a name="cloud-comparison-dashboard"></a>云比较仪表板
云比较仪表板可帮助根据定价、CPU 类型和 RAM 大小来比较不同云提供商的成本。  
![显示各种报表的云比较仪表板](./media/dashboards/cloud-comparison-dashboard.png)

### <a name="ec2-cost-in-azure-by-instance-type"></a>按实例类型划分的 Azure 中的 EC2 成本
此小组件以按需费率突出显示过去 30 天的使用情况。 它比较当前的 Amazon EC2 成本与 Azure 中可能的成本。
- 将鼠标悬停在条形图上可比较每个实例类型的成本。
- 单击此小组件可打开“移植你的部署” - 成本分析报表。

### <a name="ec2-cost-in-azure"></a>Azure 中的 EC2 成本
此小组件显示当前的 Amazon EC2 成本，并将其与 Azure 进行比较。 此比较基于过去 30 天按需费率的使用情况进行。
- 单击此小组件可打开“移植你的部署” - 成本分析报表。

### <a name="ec2azure-instance-type-mapping"></a>EC2/Azure 实例类型映射
此小组件突出显示 Amazon EC2 与 Azure 之间弹性计算单位的最佳映射。
- 单击此小组件可打开实例类型映射报表。

## <a name="next-steps"></a>后续步骤
- 阅读[使用 Cloudyn 报表](use-reports.md)一文，了解有关报表的详细信息。
