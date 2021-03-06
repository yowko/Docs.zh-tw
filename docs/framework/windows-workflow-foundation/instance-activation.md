---
title: 執行個體啟動
ms.date: 03/30/2017
ms.assetid: 134c3f70-5d4e-46d0-9d49-469a6643edd8
ms.openlocfilehash: 1fd30d9d440c06c03e726ed1f1ddbebb0d5f7e8c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279931"
---
# <a name="instance-activation"></a>執行個體啟動

SQL 工作流程執行個體存放區會執行內部工作，定期喚醒及偵測持續性資料庫中可執行或可啟動的工作流程執行個體。 如果找到可執行的工作流程執行個體，就會通知工作流程主機，表示主機可以啟動該執行個體。 如果執行個體存放區找到可啟動的工作流程執行個體，則會通知啟動工作流程主機的泛型主機，再由該主機執行工作流程執行個體。 本主題中的下列章節詳細說明執行個體啟動處理序。  
  
## <a name="detecting-and-activating-runnable-workflow-instances"></a><a name="RunnableSection"></a> 偵測和啟用可執行檔工作流程實例  

 如果實例不是處於暫停狀態或已完成狀態，而且符合下列條件，SQL 工作 *流程實例存放* 區會將工作流程實例視為可執行：  
  
- 執行個體已解除鎖定，並具有已過期的暫止計時器。  
  
- 執行個體上有過期的鎖定。  
  
- 實例已解除鎖定，且其狀態為 **執行** 中。  
  
 當 SQL 工作流程執行個體存放區找到可執行的執行個體時，會引發 <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent>。 之後，SqlWorkflowInstanceStore 就會停止監視，直到在存放區呼叫 <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> 一次為止。  
  
 訂閱 <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> 且可載入執行個體的工作流程主機會針對執行個體存放區執行 <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand>，將執行個體載入到記憶體中。 如果主控制項和實例的中繼資料屬性 **WorkflowServiceType** 設定為相同的值，則工作流程主機會被視為能夠載入工作流程實例。  
  
## <a name="detecting-and-activating-activatable-workflow-instances"></a>偵測與啟動可啟動的工作流程執行個體  

 *如果實例* 可執行，而且沒有能夠載入實例的工作流程主機正在電腦上執行，則會將工作流程實例視為可啟動。 如需可執行工作流程執行個體的定義，請參閱上面的＜偵測及啟動可執行工作流程執行個體＞。  
  
 當 SQL 工作流程執行個體存放區在資料庫中找到可啟動的工作流程執行個體時，會引發 <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent>。 之後，SqlWorkflowInstanceStore 就會停止監視，直到在存放區呼叫 <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> 一次為止。  
  
 當訂閱 <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> 的泛型主機收到這個事件時，會針對執行個體存放區執行 <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand>，以取得建立工作流程主機所需的啟動參數。 泛型主機會使用這些啟動參數建立工作流程主機，而後者則會載入和執行可執行的服務執行個體。  
  
## <a name="generic-hosts"></a>泛型主機  

 泛型主機是具有泛型主控制項的中繼資料屬性 **WorkflowServiceType** 值的主控制項，會設定為 **WorkflowServiceType。 any** 表示它可以處理任何工作流程類型。 泛型主機具有名為 **ActivationType** 的 XName 參數。  
  
 目前，SQL 工作流程實例存放區支援將 ActivationType 參數值設定為 **WAS** 的一般主機。 如果 ActivationType 未設定為 WAS，SQL 工作流程執行個體存放區會擲回 <xref:System.Runtime.DurableInstancing.InstancePersistenceException>。 隨附于 Windows Server AppFabric 裝載功能的工作流程管理服務是泛型主機，其啟用類型設定為 **WAS**。  
  
 針對 WAS 啟動，泛型主機需要一組啟動參數，才能衍生能夠用於啟動新主機的端點位址。 WAS 啟動的啟動參數是網站的名稱、應用程式的路徑 (相對於網站)，以及服務的路徑 (相對於應用程式)。 SQL 工作流程執行個體存放區會在執行 <xref:System.Activities.DurableInstancing.SaveWorkflowCommand> 的期間存放這些啟動參數。  
  
## <a name="runnable-instances-detection-period"></a>可執行的執行個體偵測週期  

 SQL 工作流程實例存放區的可執行檔 **實例偵測週期** 屬性會指定一段時間，之後 Sql 工作流程實例存放區就會執行偵測工作，以偵測在上一次偵測週期之後，持續性資料庫中任何可執行或可啟動的工作流程實例。 如需此屬性的詳細資訊，請參閱可執行檔 [實例偵測期間](runnable-instances-detection-period.md) 。
