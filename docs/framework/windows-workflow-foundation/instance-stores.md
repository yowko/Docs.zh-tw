---
title: "執行個體存放區 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f2629668-0923-4987-b943-67477131c1e0
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# 執行個體存放區
執行個體存放區是執行個體的邏輯容器者。這是儲存執行個體資料和中繼資料的位置。執行個體存放區並不是指專用的實際儲存區。執行個體存放區可包含 SQL Server 資料庫中的耐久資訊，或記憶體中的非耐久狀態資訊。[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 隨附於 SQL 工作流程執行個體存放區，是執行個體存放區的具體實作，可讓工作流程將執行個體資料與中繼資料保存在 SQL Server 2005 或 SQL Server 2008 資料庫中。此外 Windows Server App Fabric 還提供執行個體存放區的具體實作。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Windows Server App Fabric 執行個體存放區、查詢和控制項提供者](http://go.microsoft.com/fwlink/?LinkID=201201&clcid=0x409)。  
  
 持續性應用程式開發介面是介於主機和執行個體存放區間的介面，可讓主機傳送命令要求 \(例如：<xref:System.Activities.DurableInstancing.LoadWorkflowCommand> 和 <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>\) 至執行個體存放區。此 API 的具體實作稱為持續性提供者。持續性提供者會收到來自主機的要求，並修改執行個體存放區。  
  
 主機和執行個體存放區都是可插拔的，因此主機可用於許多執行個體存放區，執行個體存放區也可用於許多主機。雖然執行個體存放區通常已針對特定主機的使用模式進行最佳化，但是執行個體存放區和主機可能要以獨立的生命週期來運作。例如，**WorkflowServiceHost** 和 **SqlWorkflowInstanceStore** 是設計為適合共同運作。您可以建立專屬的執行個體存放區，來保留工作流程服務執行個體的資料和中繼資料，並與 **WorkflowServiceHost** 共同使用該執行個體存放區。例如，您可以建立 OracleWorkflowInstanceStore，讓工作流程將資訊保存在 Oracle 資料庫中，而非儲存至 SQL Server 資料庫。  
  
 使用修改已保留物件的其他功能來擴充主機是很常見的。例如，執行個體持續性系統可能有一個支援「暫停」作業的工作流程主機擴充功能，以及一個 SQL 執行個體存放區。工作流程主機可傳送標準命令，例如「儲存」\(Save\) 工作流程、將工作流程從執行個體存放區「載入」\(Load\)，或將工作流程儲存至執行個體存放區。暫停的擴充可將其他語意加入至命令中以儲存或載入工作流程執行個體，這樣暫停的工作流程就無法載入。SQL 執行個體存放區的持續性提供者會了解儲存與載入工作流程執行個體的命令，並呼叫可變更 SQL Server 伺服器中持續性物件資料表的適當儲存程序來實作命令。  
  
 做為執行個體存放區中執行個體擁有者的主機。主機可做為一個以上的執行個體擁有者，這些擁有者同時擁有一個以上的執行個體存放區。主機提供與執行個體相關聯的執行個體索引鍵 GUID。執行個體索引鍵是識別執行個體的唯一別名。持續性系統在執行主機要求的命令時，會建立、更新與刪除執行個體擁有者資訊。  
  
 下列清單包含主機與執行個體存放區互動時的相關重要步驟。  
  
1.  從持續性提供者取得 **InstanceStore**。  
  
2.  呼叫 **InstanceStore** 上的 <xref:System.Runtime.Persistence.InstanceStore.CreateInstanceHandle%2A> 方法來取得執行個體的控制代碼。  
  
3.  呼叫 **InstanceStore** 上的 <xref:System.Runtime.Persistence.InstanceStore.Execute%2A> 方法來叫用對執行個體控制代碼進行的命令。  
  
4.  檢查 **InstanceStore.Execute** 傳回的 <xref:System.Runtime.Persistence.InstanceView> 以判斷命令的結果。