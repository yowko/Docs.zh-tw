---
title: "執行個體啟用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 134c3f70-5d4e-46d0-9d49-469a6643edd8
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 執行個體啟用
SQL 工作流程執行個體存放區會執行內部工作，定期喚醒及偵測持續性資料庫中可執行或可啟動的工作流程執行個體。如果找到可執行的工作流程執行個體，就會通知工作流程主機，表示主機可以啟動該執行個體。如果執行個體存放區找到可啟動的工作流程執行個體，則會通知啟動工作流程主機的泛型主機，再由該主機執行工作流程執行個體。本主題中的下列章節詳細說明執行個體啟動處理序。  
  
##  <a name="RunnableSection"></a> 偵測與啟動可執行的工作流程執行個體  
 如果工作流程執行個體不是處於已暫停或已完成狀態，而且符合下列條件，SQL 工作流程執行個體存放區會將該執行個體視為「*可執行項目*」\(runnable\)：  
  
-   執行個體已解除鎖定，並具有已過期的暫止計時器。  
  
-   執行個體上有過期的鎖定。  
  
-   執行個體已解除鎖定，其狀態為**執行中**。  
  
 當 SQL 工作流程執行個體存放區找到可執行的執行個體時，會引發 <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent>。之後，SqlWorkflowInstanceStore 就會停止監視，直到在存放區呼叫 <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> 一次為止。  
  
 訂閱 <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> 且可載入執行個體的工作流程主機會針對執行個體存放區執行 <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand>，將執行個體載入到記憶體中。如果工作流程主機和執行個體將中繼資料屬性 **WorkflowServiceType** 的值設定為相同的值，則表示該主機可以載入工作流程執行個體。  
  
## 偵測與啟動可啟動的工作流程執行個體  
 如果工作流程執行個體可以執行，而且沒有任何工作流程主機能夠載入電腦中執行的執行個體，表示該工作流程執行個體為「*可啟動項目*」\(activatable\)。如需可執行工作流程執行個體的定義，請參閱上面的＜偵測及啟動可執行工作流程執行個體＞。  
  
 當 SQL 工作流程執行個體存放區在資料庫中找到可啟動的工作流程執行個體時，會引發 <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent>。之後，SqlWorkflowInstanceStore 就會停止監視，直到在存放區呼叫 <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> 一次為止。  
  
 當訂閱 <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> 的泛型主機收到這個事件時，會針對執行個體存放區執行 <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand>，以取得建立工作流程主機所需的啟動參數。泛型主機會使用這些啟動參數建立工作流程主機，而後者則會載入和執行可執行的服務執行個體。  
  
## 泛型主機  
 泛型主機是指主機的中繼資料屬性值 **WorkflowServiceType** \(屬於泛型主機\) 設定為 **WorkflowServiceType.Any**，以表示此主機能夠處理任何工作流程型別。泛型主機含有名為 **ActivationType** 的 XName 參數。  
  
 目前，SQL 工作流程執行個體存放區支援將 ActivationType 參數值設定為 **WAS** 的泛型主機。如果 ActivationType 未設定為 WAS，SQL 工作流程執行個體存放區會擲回 <xref:System.Runtime.DurableInstancing.InstancePersistenceException>。隨附於 [!INCLUDE[dublin](../../../includes/dublin-md.md)] 的工作流程管理服務是泛型主機，其啟動型別設定為 **WAS**。  
  
 針對 WAS 啟動，泛型主機需要一組啟動參數，才能衍生能夠用於啟動新主機的端點位址。WAS 啟動的啟動參數是網站的名稱、應用程式的路徑 \(相對於網站\)，以及服務的路徑 \(相對於應用程式\)。SQL 工作流程執行個體存放區會在執行 <xref:System.Activities.DurableInstancing.SaveWorkflowCommand> 的期間存放這些啟動參數。  
  
## 可執行的執行個體偵測週期  
 SQL 工作流程執行個體存放區的**可執行的執行個體偵測週期**屬性會指定一段時間，在這段時間之後，SQL 工作流程執行個體存放區會執行偵測工作，以偵測在上一次偵測週期之後，持續性資料庫中任何可執行或可啟動的工作流程執行個體。如需這個屬性的詳細資訊，請參閱[可執行的執行個體偵測週期](../../../docs/framework/windows-workflow-foundation//runnable-instances-detection-period.md)。