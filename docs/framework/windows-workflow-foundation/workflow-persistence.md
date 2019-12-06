---
title: 工作流程持續性
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], persistence
ms.assetid: 39e69d1f-b771-4c16-9e18-696fa43b65b2
ms.openlocfilehash: c49e287c6132103d4bb85a8ae892a76f9b582274
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837528"
---
# <a name="workflow-persistence"></a>工作流程持續性
工作流程持續性是永久擷取工作流程執行個體的狀態，與處理序或電腦資訊無關。 這麼做是為了在發生系統故障時提供已知的工作流程執行個體復原點，或者藉由卸載非正在進行工作的工作流程執行個體來保留記憶體，或者將工作流程執行個體的狀態從某個節點移到伺服器陣列中的另一個節點。  
  
 持續性可讓處理序擁有靈活度、擴充性、發生錯誤時的復原能力，以及以更高的效率管理記憶體的能力。 持續性處理序包括識別保存點、收集要儲存的資料，最後將資料的實際儲存委派給持續性提供者。  
  
 若要啟用工作流程的持續性，您必須將實例存放區與**WorkflowApplication**或**WorkflowServiceHost**建立關聯，如[如何：啟用工作流程和工作流程服務的持續](how-to-enable-persistence-for-workflows-and-workflow-services.md)性中所述。 **WorkflowApplication**和**WorkflowServiceHost**會使用與其相關聯的實例存放區，以便將工作流程實例保存至持續性存放區，並根據儲存在持續性存放區中的工作流程實例資料，將工作流程實例載入記憶體中。  
  
 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 隨附于**SqlWorkflowInstanceStore**類別，可讓您將有關工作流程實例的資料和中繼資料保存到 SQL Server 2005 或 SQL Server 2008 資料庫。 如需詳細資訊，請參閱[SQL 工作流程實例存放區](sql-workflow-instance-store.md)。  
  
 若要儲存及載入應用程式特定資料與工作流程執行個體相關資訊，您可以建立擴充 <xref:System.Activities.Persistence.PersistenceParticipant> 類別的持續性參與者。 持續性參與者會參與保存程序，將自訂可序列化資料儲存至持續性存放區中，以便將執行個體存放區中的資料載入記憶體中，以及在持續性異動下執行任何其他邏輯。 如需詳細資訊，請參閱[持續性參與者](persistence-participants.md)。  
  
 Windows Server App Fabric 會簡化設定持續性的程序。 如需詳細資訊，請參閱[Windows Server App Fabric 的持續性概念](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10))  
  
## <a name="implicit-persistence-points"></a>隱含的保存點  
 下列清單包含當執行個體存放區與工作流程相關時，保存工作流程的條件範例。  
  
- 當**TransactionScope**活動完成或**TransactedReceiveScope**活動完成時。  
  
- 當工作流程實例變成閒置，且已在工作流程主機上設定**WorkflowIdleBehavior**時。 例如，當您使用訊息活動或**延遲**活動時，就會發生這種情況。  
  
- 當 WorkflowApplication 變成閒置，且應用程式的**PersistableIdle**屬性設定為 PersistableIdleAction 時，就會**保存**。  
  
- 當指示主應用程式保存或卸載工作流程執行個體時。  
  
- 當工作流程執行個體終止或完成時。  
  
- 當**保存**活動執行時。  
  
- 當使用舊版 Windows Workflow Foundation 開發的工作流程執行個體在互通的執行期間遇到保存點時。  
  
## <a name="in-this-section"></a>本章節內容  
  
- [SQL 工作流程執行個體存放區](sql-workflow-instance-store.md)  
  
- [執行個體存放區](instance-stores.md)  
  
- [持續性參與者](persistence-participants.md)  
  
- [持續性最佳做法](persistence-best-practices.md)  
  
- [非持續性工作流程執行個體](non-persisted-workflow-instances.md)  
  
- [暫停及繼續工作流程](pausing-and-resuming-a-workflow.md)
