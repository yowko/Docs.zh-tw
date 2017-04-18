---
title: "非持續性的工作流程執行個體 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5e01af77-6b14-4964-91a5-7dfd143449c0
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 非持續性的工作流程執行個體
當建立工作流程的新執行個體，將其狀態保存在 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 中時，服務主機會在執行個體存放區中為該服務建立項目。接下來，當第一次保存工作流程執行個體時，<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 會儲存目前的執行個體狀態。如果此工作流程裝載於 Windows 處理序啟用服務中，當初次保存執行個體時，服務部署資料也會寫入執行個體存放區。  
  
 只要未保存工作流程執行個體，它就會處於**非保存**狀態。當工作流程執行個體處於這個狀態時，便無法在應用程式定義域回收、主機故障或電腦故障之後復原。  
  
## 非保存狀態  
 在下列案例中，尚未保存的永久性工作流程執行個體會持續處於非保存狀態：  
  
-   服務主機在工作流程執行個體初次保存之前當機。工作流程執行個體依然保存在執行個體存放區中，而且不會復原。如果相互關聯的訊息抵達，則工作流程執行個體會再次變成作用中。  
  
-   工作流程執行個體在初次保存之前遇到例外狀況。根據傳回的 <xref:System.Activities.UnhandledExceptionAction> 發生以下狀況：  
  
    -   <xref:System.Activities.UnhandledExceptionAction> 設定為 <xref:System.Activities.UnhandledExceptionAction>：當發生例外狀況時，服務部署資訊會寫入執行個體存放區，而工作流程執行個體則會從記憶體中卸載。工作流程執行個體持續處於非保存狀態，而且無法重新載入。  
  
    -   <xref:System.Activities.UnhandledExceptionAction> 設定為 <xref:System.Activities.UnhandledExceptionAction> 或 <xref:System.Activities.UnhandledExceptionAction>：當發生例外狀況時，服務部署資訊會寫入執行個體存放區，而活動執行個體狀態則會設定為 <xref:System.Activities.ActivityInstanceState>。  
  
 為了讓遇到卸載的非保存工作流程執行個體的風險降到最低，我們建議您在其生命週期的早期保存工作流程。  
  
## 偵測及移除非保存的執行個體  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 不會從執行個體存放區移除任何非保存的工作流程執行個體。也不會移除擁有關聯之非保存工作流程執行個體的任何過期的鎖定擁有者。  
  
 我們建議系統管理員最好定期檢查非保存之執行個體的執行個體存放區。只要系統管理員知道這個工作流程不會接收關聯的訊息，就可以從執行個體存放區中移除這些執行個體。例如，如果執行個體已在資料庫中停留數個月之久，而您知道工作流程通常只有數天的存留期，則可放心將該執行個體視為已損毀的初始化執行個體。  
  
 若要在 SQL 工作流程執行個體存放區中尋找非保存的執行個體，您可以使用下列 SQL 查詢：  
  
-   這個查詢會尋找尚未保存的所有執行個體，而且會針對這些執行個體傳回 ID 和建立時間 \(以 UTC 時間儲存\)。  
  
    ```sql  
    select InstanceId, CreationTime   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0  
    ```  
  
-   這個查詢會尋找尚未保存且尚未載入的所有執行個體，而且會針對這些執行個體傳回 ID 和建立時間 \(以 UTC 時間儲存\)。  
  
    ```sql  
    select InstanceId, CreationTime   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0   
            and CurrentMachine is NULL  
    ```  
  
-   這個查詢會尋找尚未保存且已暫止的所有執行個體，而且會針對這些執行個體傳回 ID、建立時間 \(以 UTC 時間儲存\)、暫停原因和例外狀況名稱。  
  
    ```sql  
    select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0   
            and IsSuspended = 1  
    ```  
  
 當您刪除非保存的執行個體時，請務必小心謹慎。一般而言，您可以放心移除 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 所建立且已暫止或未載入的非保存執行個體。這些特定的執行個體可以從存放區中刪除，其方式是從 `[System.Activities.DurableInstancing].[Instances]` 檢視中加以刪除，或是使用下列 SQL 命令來替代正確的執行個體 ID。  
  
```sql  
delete [System.Activities.DurableInstancing].[Instances]   
    where InstanceId=’078a9bc4-ada5-4f9e-8cce-b0eb0009995f’  
  
```  
  
> [!WARNING]
>  我們不建議您移除所有非保存執行個體，因為這樣會包含剛剛建立且尚未保存的執行個體。