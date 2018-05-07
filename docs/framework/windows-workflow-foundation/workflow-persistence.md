---
title: 工作流程持續性
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], persistence
ms.assetid: 39e69d1f-b771-4c16-9e18-696fa43b65b2
ms.openlocfilehash: 8baae818db114567804d3796192249d6738fbb17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="workflow-persistence"></a>工作流程持續性
工作流程持續性是永久擷取工作流程執行個體的狀態，與處理序或電腦資訊無關。 這麼做是為了在發生系統故障時提供已知的工作流程執行個體復原點，或者藉由卸載非正在進行工作的工作流程執行個體來保留記憶體，或者將工作流程執行個體的狀態從某個節點移到伺服器陣列中的另一個節點。  
  
 持續性可讓處理序擁有靈活度、擴充性、發生錯誤時的復原能力，以及以更高的效率管理記憶體的能力。 持續性處理序包括識別保存點、收集要儲存的資料，最後將資料的實際儲存委派給持續性提供者。  
  
 若要啟用持續性工作流程，您必須建立關聯的執行個體存放區**WorkflowApplication**或**WorkflowServiceHost**中所述[How to： 啟用持續性工作流程與工作流程服務](../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md)。 **WorkflowApplication**和**WorkflowServiceHost**使用與其相關聯的執行個體存放區啟用保存工作流程執行個體持續性存放區及載入工作流程執行個體根據儲存在持續性存放區的工作流程執行個體資料的記憶體。  
  
 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]隨附**SqlWorkflowInstanceStore**類別，可讓持續性的資料和工作流程執行個體至 SQL Server 2005 或 SQL Server 2008 資料庫的相關中繼資料。 請參閱[SQL 工作流程執行個體存放區](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)如需詳細資訊。  
  
 若要儲存及載入應用程式特定資料與工作流程執行個體相關資訊，您可以建立擴充 <xref:System.Activities.Persistence.PersistenceParticipant> 類別的持續性參與者。 持續性參與者會參與保存程序，將自訂可序列化資料儲存至持續性存放區中，以便將執行個體存放區中的資料載入記憶體中，以及在持續性異動下執行任何其他邏輯。 如需詳細資訊，請參閱[持續性參與者](../../../docs/framework/windows-workflow-foundation/persistence-participants.md)。  
  
 Windows Server App Fabric 會簡化設定持續性的程序。 如需詳細資訊，請參閱[與 Windows Server App Fabric 持續性概念](http://go.microsoft.com/fwlink/?LinkId=201200)  
  
## <a name="implicit-persistence-points"></a>隱含的保存點  
 下列清單包含當執行個體存放區與工作流程相關時，保存工作流程的條件範例。  
  
-   當**TransactionScope**活動完成或**TransactedReceiveScope**活動完成。  
  
-   當工作流程執行個體變成閒置， **WorkflowIdleBehavior**集合工作流程主機上。 發生這種情況，例如，當您使用訊息活動或**延遲**活動。  
  
-   當 WorkflowApplication 變成閒置， **PersistableIdle**應用程式的屬性設定為**PersistableIdleAction.Persist**。  
  
-   當指示主應用程式保存或卸載工作流程執行個體時。  
  
-   當工作流程執行個體終止或完成時。  
  
-   當**保存**活動執行。  
  
-   當使用舊版 Windows Workflow Foundation 開發的工作流程執行個體在互通的執行期間遇到保存點時。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [SQL 工作流程執行個體存放區](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)  
  
-   [執行個體存放區](../../../docs/framework/windows-workflow-foundation/instance-stores.md)  
  
-   [持續性參與者](../../../docs/framework/windows-workflow-foundation/persistence-participants.md)  
  
-   [持續性最佳做法](../../../docs/framework/windows-workflow-foundation/persistence-best-practices.md)  
  
-   [非持續性工作流程執行個體](../../../docs/framework/windows-workflow-foundation/non-persisted-workflow-instances.md)  
  
-   [暫停及繼續工作流程](../../../docs/framework/windows-workflow-foundation/pausing-and-resuming-a-workflow.md)
