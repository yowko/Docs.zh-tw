---
title: SQL 工作流程執行個體存放區
ms.date: 03/30/2017
ms.assetid: 8cd2f8a5-4bf8-46ea-8909-c7fdb314fabc
ms.openlocfilehash: 8314781f46d9cd4eddd06f6be95f8e952feef1b9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086568"
---
# <a name="sql-workflow-instance-store"></a>SQL 工作流程執行個體存放區
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 隨附於 SQL 工作流程執行個體存放區，可讓工作流程將有關工作流程執行個體的狀態資訊保存在 SQL Server 2005 或 SQL Server 2008 資料庫中。 這項功能主要是以 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 類別的形式實作，該類別衍生自持續性架構的抽象 <xref:System.Runtime.DurableInstancing.InstanceStore> 類別。 SQL 工作流程執行個體存放區功能會構成 SQL 持續性提供者，該提供者是持續性 API 的具象實作，主機會運用此 API 將持續性命令傳送至存放區。  
  
 SQL 工作流程執行個體存放區支援使用 <xref:System.Activities.WorkflowApplication> 或 <xref:System.ServiceModel.WorkflowServiceHost> 的自我裝載工作流程或工作流程服務，以及使用 <xref:System.ServiceModel.WorkflowServiceHost> 裝載於 WAS 中的服務。 您可以使用這項功能所公開的物件模型，以程式設計方式設定自我裝載服務的 SQL 工作流程執行個體存放區功能。 您可以使用物件模型及 XML 組態檔，以程式設計方式，針對由 <xref:System.ServiceModel.WorkflowServiceHost> 裝載的服務，設定這項功能。  
  
 SQL 工作流程執行個體存放區功能 (**SqlWorkflowInstanceStore**類別) 不會實作<xref:System.ServiceModel.Persistence.PersistenceProviderFactory>，因此不會提供持久的非工作流程 WCF 服務的持續性支援。 此外，該功能也不會實作 <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService>，因此不針對 3.x 工作流程提供持續性支援。 這項功能僅支援 WF 4.0 (和更新版本) 工作流程及工作流程服務的持續性。 除了 SQL Server 2005 和 SQL Server 2008 以外，此功能亦不支援其他資料庫。  
  
 本節中的主題描述 SQL 工作流程執行個體存放區的屬性和功能，同時說明關於設定存放區的詳細資訊。  
  
 Windows Server App Fabric 提供其本身的執行個體存放區和工具，可簡化執行個體存放區的設定和使用。 如需詳細資訊，請參閱 < [Windows Server App Fabric 執行個體存放區](https://go.microsoft.com/fwlink/?LinkId=201201)。 如需有關 App Fabric SQL Server 持續性資料庫，請參閱[App Fabric SQL Server 持續性資料庫](https://go.microsoft.com/fwlink/?LinkId=201202)  
  
## <a name="in-this-section"></a>本節內容  
  
-   [SQL 工作流程執行個體存放區的屬性](properties-of-sql-workflow-instance-store.md)  
  
-   [HOW TO：啟用工作流程與工作流程服務的 SQL 持續性](how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)  
  
-   [執行個體啟動](instance-activation.md)  
  
-   [支援查詢](support-for-queries.md)  
  
-   [存放區擴充性](store-extensibility.md)  
  
-   [安全性](security.md)  
  
-   [SQL Server 持續性資料庫](sql-server-persistence-database.md)  
  
## <a name="see-also"></a>另請參閱

- [持續性範例](https://go.microsoft.com/fwlink/?LinkID=177735)
