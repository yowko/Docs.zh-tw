---
title: "工作流程持續性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "程式設計 [WF], 持續性"
ms.assetid: 39e69d1f-b771-4c16-9e18-696fa43b65b2
caps.latest.revision: 26
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 26
---
# 工作流程持續性
工作流程持續性是永久擷取工作流程執行個體的狀態，與處理序或電腦資訊無關。這麼做是為了在發生系統故障時提供已知的工作流程執行個體復原點，或者藉由卸載非正在進行工作的工作流程執行個體來保留記憶體，或者將工作流程執行個體的狀態從某個節點移到伺服器陣列中的另一個節點。  
  
 持續性可讓處理序擁有靈活度、擴充性、發生錯誤時的復原能力，以及以更高的效率管理記憶體的能力。持續性處理序包括識別保存點、收集要儲存的資料，最後將資料的實際儲存委派給持續性提供者。  
  
 若要啟用工作流程的持續性，您需要將執行個體存放區與 **WorkflowApplication** 或 **WorkflowServiceHost** 關聯，如 [HOW TO：啟用工作流程與工作流程服務的持續性](../../../docs/framework/windows-workflow-foundation//how-to-enable-persistence-for-workflows-and-workflow-services.md)中所述。**WorkflowApplication** 和 **WorkflowServiceHost** 會使用與其相關的執行個體存放區，將工作流程執行個體保存在持續性存放區中，並且根據儲存在持續性存放區中的工作流程執行個體資料，將工作流程執行個體載入到記憶體中。  
  
 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 隨附於 **SqlWorkflowInstanceStore** 類別，可將有關工作流程執行個體的資料和中繼資料保存在 SQL Server 2005 或 SQL Server 2008 資料庫中。如需詳細資訊，請參閱 [SQL 工作流程執行個體存放區](../../../docs/framework/windows-workflow-foundation//sql-workflow-instance-store.md)。  
  
 若要儲存及載入應用程式特定資料與工作流程執行個體相關資訊，您可以建立擴充 <xref:System.Activities.Persistence.PersistenceParticipant> 類別的持續性參與者。持續性參與者會參與保存程序，將自訂可序列化資料儲存至持續性存放區中，以便將執行個體存放區中的資料載入記憶體中，以及在持續性交易下執行任何其他邏輯。如需詳細資訊，請參閱[持續性參與者](../../../docs/framework/windows-workflow-foundation//persistence-participants.md)。  
  
 Windows Server App Fabric 會簡化設定持續性的程序。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Windows Server App Fabric 持續性概念](http://go.microsoft.com/fwlink/?LinkId=201200)  
  
## 隱含的保存點  
 下列清單包含當執行個體存放區與工作流程相關時，保存工作流程的條件範例。  
  
-   當 **TransactionScope** 活動或 **TransactedReceiveScope** 活動完成時。  
  
-   當工作流程執行個體變成閒置，且在工作流程主機上設定了 **WorkflowIdleBehavior** 時。例如，當您使用訊息活動或 **Delay** 時，就會發生這個狀況。  
  
-   當 WorkflowApplication 變成閒置，而且應用程式的 **PersistableIdle** 屬性設為 **PersistableIdleAction.Persist** 時。  
  
-   當指示主應用程式保存或卸載工作流程執行個體時。  
  
-   當工作流程執行個體終止或完成時。  
  
-   當 **Persist** 活動執行時。  
  
-   當使用舊版 Windows Workflow Foundation 開發的工作流程執行個體在互通的執行期間遇到保存點時。  
  
## 本章節內容  
  
-   [SQL 工作流程執行個體存放區](../../../docs/framework/windows-workflow-foundation//sql-workflow-instance-store.md)  
  
-   [執行個體存放區](../../../docs/framework/windows-workflow-foundation//instance-stores.md)  
  
-   [持續性參與者](../../../docs/framework/windows-workflow-foundation//persistence-participants.md)  
  
-   [持續性的最佳作法](../../../docs/framework/windows-workflow-foundation//persistence-best-practices.md)  
  
-   [非持續性的工作流程執行個體](../../../docs/framework/windows-workflow-foundation//non-persisted-workflow-instances.md)  
  
-   [暫止和繼續流程](../../../docs/framework/windows-workflow-foundation//pausing-and-resuming-a-workflow.md)