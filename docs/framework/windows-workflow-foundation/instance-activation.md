---
title: 執行個體啟動
ms.date: 03/30/2017
ms.assetid: 134c3f70-5d4e-46d0-9d49-469a6643edd8
ms.openlocfilehash: 088722ba19a1f38e8a341e34a8344963021f1113
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64584928"
---
# <a name="instance-activation"></a>執行個體啟動
SQL 工作流程執行個體存放區會執行內部工作，定期喚醒及偵測持續性資料庫中可執行或可啟動的工作流程執行個體。 如果找到可執行的工作流程執行個體，就會通知工作流程主機，表示主機可以啟動該執行個體。 如果執行個體存放區找到可啟動的工作流程執行個體，則會通知啟動工作流程主機的泛型主機，再由該主機執行工作流程執行個體。 本主題中的下列章節詳細說明執行個體啟動處理序。  
  
## <a name="RunnableSection"></a> 偵測與啟動可執行工作流程執行個體  
 SQL 工作流程執行個體存放區會考慮工作流程執行個體*可執行*如果執行個體不是處於暫停的狀態或已完成的狀態，而且滿足以下條件：  
  
- 執行個體已解除鎖定，並具有已過期的暫止計時器。  
  
- 執行個體上有過期的鎖定。  
  
- 執行個體已解除鎖定，且其狀態為**Executing**。  
  
 當 SQL 工作流程執行個體存放區找到可執行的執行個體時，會引發 <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent>。 之後，SqlWorkflowInstanceStore 就會停止監視，直到在存放區呼叫 <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> 一次為止。  
  
 訂閱 <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> 且可載入執行個體的工作流程主機會針對執行個體存放區執行 <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand>，將執行個體載入到記憶體中。 工作流程主機會被視為可載入工作流程執行個體，如果主應用程式和執行個體中繼資料屬性**WorkflowServiceType**設為相同的值。  
  
## <a name="detecting-and-activating-activatable-workflow-instances"></a>偵測與啟動可啟動的工作流程執行個體  
 工作流程執行個體將會被視為*可啟動*如果執行個體是可執行，而且沒有任何工作流程主機能夠載入執行個體在電腦上執行。 如需可執行工作流程執行個體的定義，請參閱上面的＜偵測及啟動可執行工作流程執行個體＞。  
  
 當 SQL 工作流程執行個體存放區在資料庫中找到可啟動的工作流程執行個體時，會引發 <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent>。 之後，SqlWorkflowInstanceStore 就會停止監視，直到在存放區呼叫 <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> 一次為止。  
  
 當訂閱 <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> 的泛型主機收到這個事件時，會針對執行個體存放區執行 <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand>，以取得建立工作流程主機所需的啟動參數。 泛型主機會使用這些啟動參數建立工作流程主機，而後者則會載入和執行可執行的服務執行個體。  
  
## <a name="generic-hosts"></a>泛型主機  
 泛型主機是主機的中繼資料屬性的值與**WorkflowServiceType**泛型主機會設為**WorkflowServiceType.Any**表示它可以處理任何工作流程類型。 泛型主機含有名為的 XName 參數**ActivationType**。  
  
 目前，SQL 工作流程執行個體存放區支援將 ActivationType 參數設定為值的泛型主機**WAS**。 如果 ActivationType 未設定為 WAS，SQL 工作流程執行個體存放區會擲回 <xref:System.Runtime.DurableInstancing.InstancePersistenceException>。 Workflow Management Service 隨附[!INCLUDE[dublin](../../../includes/dublin-md.md)]是泛型主機，已將啟動類型設定為**WAS**。  
  
 針對 WAS 啟動，泛型主機需要一組啟動參數，才能衍生能夠用於啟動新主機的端點位址。 WAS 啟動的啟動參數是網站的名稱、應用程式的路徑 (相對於網站)，以及服務的路徑 (相對於應用程式)。 SQL 工作流程執行個體存放區會在執行 <xref:System.Activities.DurableInstancing.SaveWorkflowCommand> 的期間存放這些啟動參數。  
  
## <a name="runnable-instances-detection-period"></a>可執行的執行個體偵測週期  
 **可執行的執行個體偵測週期**SQL 工作流程執行個體存放區的屬性會指定時間週期之後，SQL 工作流程執行個體存放區會執行偵測工作，以偵測任何可執行或可啟動的工作流程在上一個偵測循環之後持續性資料庫中的執行個體。 請參閱[可執行的執行個體偵測週期](runnable-instances-detection-period.md)如需有關這個屬性的詳細資訊。
