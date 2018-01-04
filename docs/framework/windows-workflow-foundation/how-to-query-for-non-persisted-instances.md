---
title: "HOW TO：非保存執行個體的查詢"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 294019b1-c1a7-4b81-a14f-b47c106cd723
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bde3ab1049edf6cb52a221225321f1e505a2491b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-query-for-non-persisted-instances"></a>HOW TO：非保存執行個體的查詢
當建立服務的新執行個體且服務已定義 SQL 工作流程執行個體存放區行為時，服務主機會在執行個體存放區中為該服務執行個體建立初始項目。 接著在初次保存服務執行個體時，SQL 工作流程執行個體存放區行為會保存目前的執行個體狀態，連同啟動、復原和控制所需的其他資料。  
  
 如果執行個體未在執行個體的初始項目建立時保存，則會將服務執行個體視為處於非保存狀態。 所有保存的服務執行個體都可以進行查詢並加以控制。 非保存的服務執行個體則無法進行查詢，也無法加以控制。 如果非保存的執行個體因為未處理的例外狀況而暫止，則可以進行查詢，但無法加以控制。  
  
 在下列案例中，尚未保存的永久性服務執行個體會持續處於非保存狀態：  
  
-   服務主機在執行個體初次保存之前當機。 執行個體的初始項目保留在執行個體存放區中。 執行個體無法復原。 如果相互關聯的訊息抵達，則執行個體會再次變成作用中。  
  
-   執行個體在初次保存之前發生未處理的例外狀況。 發生下列情況  
  
    -   如果值**UnhandledExceptionAction**屬性設定為**放棄**、 服務部署資訊會寫入執行個體存放區和執行個體已從記憶體中卸載。 執行個體在持續性資料庫中保持非保存狀態。  
  
    -   如果值**UnhandledExceptionAction**屬性設定為**AbandonAndSuspsend**、 服務部署資訊會寫入持續性資料庫和執行個體狀態會設為**暫止**。 執行個體無法繼續、取消或終止。 服務主機無法載入執行個體，因為執行個體尚未保存，所以執行個體的資料庫項目並不完整。  
  
    -   如果值**UnhandledExceptionAction**屬性設定為**取消**或**終止**，則服務部署資訊會寫入執行個體存放區，執行個體狀態會設為**已完成**。  
  
 以下各節提供範例查詢，用來尋找 SQL 持續性資料庫中的非保存執行個體，以及從資料庫中刪除這些執行個體。  
  
## <a name="to-find-all-instances-not-persisted-yet"></a>尋找所有尚未保存的執行個體  
 下面的 SQL 查詢會傳回所有尚未保存至持續性資料庫內之執行個體的識別碼和建立時間。  
  
```  
select InstanceId, CreationTime from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0;  
```  
  
## <a name="to-find-all-instances-not-persisted-yet-and-also-not-loaded"></a>尋找所有尚未保存且尚未載入的執行個體  
 下面的 SQL 查詢會傳回所有尚未保留且尚未載入之執行個體的識別碼和建立時間。  
  
```  
select InstanceId, CreationTime from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0 and CurrentMachine is NULL;  
```  
  
## <a name="to-find-all-suspended-instances-not-persisted-yet"></a>尋找所有尚未保存的已暫止執行個體  
 下面的 SQL 查詢會傳回所有尚未保存且處於暫止狀態之執行個體的識別碼、建立時間、暫止原因和暫止例外狀況名稱。  
  
```  
select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0 and IsSuspended = 1;  
```  
  
## <a name="to-delete-non-persisted-instances-from-the-persistence-database"></a>從持續性資料庫刪除非保存執行個體  
 您應該定期檢查執行個體存放區中是否有非保存執行個體，並且從執行個體存放區移除確定將不會接收相互關聯訊息的執行個體。 例如，如果執行個體已在資料庫中停留數個月之久，而您知道工作流程通常只有數天的存留期，則可放心將該執行個體視為已損毀的未初始化執行個體。  
  
 一般而言，您可以放心刪除未暫止或未載入的非保存執行個體。 您不應該刪除**所有**非保存執行個體，因為這個執行個體集包含剛建立但尚未保存。 您只應刪除因載入執行個體的工作流程服務主機造成例外狀況，或因執行個體本身造成例外狀況而留下的非保存執行個體。  
  
> [!WARNING]
>  從執行個體存放區刪除非保存執行個體會減少存放區的大小，並且可提升存放區作業的效能。
