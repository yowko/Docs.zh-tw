---
title: 非持續性的工作流程執行個體
ms.date: 03/30/2017
ms.assetid: 5e01af77-6b14-4964-91a5-7dfd143449c0
ms.openlocfilehash: 410451f0dfeb91111e77634245aa786c4afc5b04
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516746"
---
# <a name="non-persisted-workflow-instances"></a><span data-ttu-id="d34f3-102">非持續性的工作流程執行個體</span><span class="sxs-lookup"><span data-stu-id="d34f3-102">Non-Persisted Workflow Instances</span></span>
<span data-ttu-id="d34f3-103">當建立工作流程的新執行個體，將其狀態保存在 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 中時，服務主機會在執行個體存放區中為該服務建立項目。</span><span class="sxs-lookup"><span data-stu-id="d34f3-103">When a new instance of a workflow is created that persists its state in the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, the service host creates an entry for that service in the instance store.</span></span> <span data-ttu-id="d34f3-104">接下來，當第一次保存工作流程執行個體時，<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 會儲存目前的執行個體狀態。</span><span class="sxs-lookup"><span data-stu-id="d34f3-104">Subsequently, when the workflow instance is persisted for the first time, the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> stores the current instance state.</span></span> <span data-ttu-id="d34f3-105">如果此工作流程裝載於 Windows 處理序啟用服務中，當初次保存執行個體時，服務部署資料也會寫入執行個體存放區。</span><span class="sxs-lookup"><span data-stu-id="d34f3-105">If the workflow is hosted in the Windows Process Activation Service, the service deployment data is also written to the instance store when the instance is persisted for the first time.</span></span>  
  
 <span data-ttu-id="d34f3-106">只要未保存工作流程執行個體，它處於**非保存**狀態。</span><span class="sxs-lookup"><span data-stu-id="d34f3-106">As long as the workflow instance has not been persisted, it is in a **non-persisted** state.</span></span> <span data-ttu-id="d34f3-107">當工作流程執行個體處於這個狀態時，便無法在應用程式定義域回收、主機故障或電腦故障之後復原。</span><span class="sxs-lookup"><span data-stu-id="d34f3-107">While in this state, the workflow instance cannot be recovered after an application domain recycle, host failure, or computer failure.</span></span>  
  
## <a name="the-non-persisted-state"></a><span data-ttu-id="d34f3-108">非保存狀態</span><span class="sxs-lookup"><span data-stu-id="d34f3-108">The Non-Persisted State</span></span>  
 <span data-ttu-id="d34f3-109">在下列案例中，尚未保存的永久性工作流程執行個體會持續處於非保存狀態：</span><span class="sxs-lookup"><span data-stu-id="d34f3-109">Durable workflow instances that have not been persisted remain in a non-persisted state in the following cases:</span></span>  
  
-   <span data-ttu-id="d34f3-110">服務主機在工作流程執行個體初次保存之前當機。</span><span class="sxs-lookup"><span data-stu-id="d34f3-110">The service host crashes before the workflow instance is persisted for the first time.</span></span> <span data-ttu-id="d34f3-111">工作流程執行個體依然保存在執行個體存放區中，而且不會復原。</span><span class="sxs-lookup"><span data-stu-id="d34f3-111">The workflow instance remains in the instance store and is not recovered.</span></span> <span data-ttu-id="d34f3-112">如果相互關聯的訊息抵達，則工作流程執行個體會再次變成作用中。</span><span class="sxs-lookup"><span data-stu-id="d34f3-112">If a correlated message arrives, the workflow instance becomes active again.</span></span>  
  
-   <span data-ttu-id="d34f3-113">工作流程執行個體在初次保存之前遇到例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d34f3-113">The workflow instance experiences an exception before it is persisted for the first time.</span></span> <span data-ttu-id="d34f3-114">根據傳回的 <xref:System.Activities.UnhandledExceptionAction> 發生以下狀況：</span><span class="sxs-lookup"><span data-stu-id="d34f3-114">Depending on the <xref:System.Activities.UnhandledExceptionAction> returned, the following scenarios occur:</span></span>  
  
    -   <span data-ttu-id="d34f3-115"><xref:System.Activities.UnhandledExceptionAction> 設定為 <xref:System.Activities.UnhandledExceptionAction.Abort>：當發生例外狀況時，服務部署資訊會寫入執行個體存放區，而工作流程執行個體則會從記憶體中卸載。</span><span class="sxs-lookup"><span data-stu-id="d34f3-115"><xref:System.Activities.UnhandledExceptionAction> is set to <xref:System.Activities.UnhandledExceptionAction.Abort>: When an exception occurs, service deployment information is written to the instance store, and the workflow instance is unloaded from memory.</span></span> <span data-ttu-id="d34f3-116">工作流程執行個體持續處於非保存狀態，而且無法重新載入。</span><span class="sxs-lookup"><span data-stu-id="d34f3-116">The workflow instance remains in a non-persisted state and cannot be reloaded.</span></span>  
  
    -   <span data-ttu-id="d34f3-117"><xref:System.Activities.UnhandledExceptionAction> 設定為 <xref:System.Activities.UnhandledExceptionAction.Cancel> 或 <xref:System.Activities.UnhandledExceptionAction.Terminate>：當發生例外狀況時，服務部署資訊會寫入執行個體存放區，而活動執行個體狀態則會設定為 <xref:System.Activities.ActivityInstanceState.Closed>。</span><span class="sxs-lookup"><span data-stu-id="d34f3-117"><xref:System.Activities.UnhandledExceptionAction> is set to <xref:System.Activities.UnhandledExceptionAction.Cancel> or <xref:System.Activities.UnhandledExceptionAction.Terminate>: When an exception occurs, service deployment information is written to the instance store, and the activity instance state is set to <xref:System.Activities.ActivityInstanceState.Closed>.</span></span>  
  
 <span data-ttu-id="d34f3-118">為了讓遇到卸載的非保存工作流程執行個體的風險降到最低，我們建議您在其生命週期的早期保存工作流程。</span><span class="sxs-lookup"><span data-stu-id="d34f3-118">To minimize the risk of encountering unloaded non-persisted workflow instances, we recommend persisting the workflow early in its life cycle.</span></span>  
  
## <a name="detection-and-removal-of-non-persisted-instances"></a><span data-ttu-id="d34f3-119">偵測及移除非保存的執行個體</span><span class="sxs-lookup"><span data-stu-id="d34f3-119">Detection and Removal of Non-Persisted Instances</span></span>  
 <span data-ttu-id="d34f3-120"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 不會從執行個體存放區移除任何非保存的工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="d34f3-120">The <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> does not remove any non-persisted workflow instances from the instance store.</span></span> <span data-ttu-id="d34f3-121">也不會移除擁有關聯之非保存工作流程執行個體的任何過期的鎖定擁有者。</span><span class="sxs-lookup"><span data-stu-id="d34f3-121">It also does not remove any expired lock owners that have non-persisted workflow instances associated with them.</span></span>  
  
 <span data-ttu-id="d34f3-122">我們建議系統管理員最好定期檢查非保存之執行個體的執行個體存放區。</span><span class="sxs-lookup"><span data-stu-id="d34f3-122">We recommend that the administrator periodically checks the instance store for non-persisted instances.</span></span> <span data-ttu-id="d34f3-123">只要系統管理員知道這個工作流程不會接收關聯的訊息，就可以從執行個體存放區中移除這些執行個體。</span><span class="sxs-lookup"><span data-stu-id="d34f3-123">Administrators can remove those instances from the instance store as long as they know that this workflow will not receive correlated messages.</span></span> <span data-ttu-id="d34f3-124">例如，如果執行個體已在資料庫中停留數個月之久，而您知道工作流程通常只有數天的存留期，則可放心將該執行個體視為已損毀的初始化執行個體。</span><span class="sxs-lookup"><span data-stu-id="d34f3-124">For example, if the instance has been in the database for several months and it is known that the workflow typically has a lifetime of several days, it would be safe to assume that this was an initialized instance that had crashed.</span></span>  
  
 <span data-ttu-id="d34f3-125">若要在 SQL 工作流程執行個體存放區中尋找非保存的執行個體，您可以使用下列 SQL 查詢：</span><span class="sxs-lookup"><span data-stu-id="d34f3-125">To find non-persisted instances in the SQL Workflow Instance Store you can use the following SQL queries:</span></span>  
  
-   <span data-ttu-id="d34f3-126">這個查詢會尋找尚未保存的所有執行個體，而且會針對這些執行個體傳回 ID 和建立時間 (以 UTC 時間儲存)。</span><span class="sxs-lookup"><span data-stu-id="d34f3-126">This query finds all instances that have not been persisted, and returns the ID and creation time (stored in UTC time) for them.</span></span>  
  
    ```sql  
    select InstanceId, CreationTime   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0  
    ```  
  
-   <span data-ttu-id="d34f3-127">這個查詢會尋找尚未保存且尚未載入的所有執行個體，而且會針對這些執行個體傳回 ID 和建立時間 (以 UTC 時間儲存)。</span><span class="sxs-lookup"><span data-stu-id="d34f3-127">This query finds all instances that have not been persisted, and that are not loaded, and returns the ID and creation time (stored in UTC time) for them.</span></span>  
  
    ```sql  
    select InstanceId, CreationTime   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0   
            and CurrentMachine is NULL  
    ```  
  
-   <span data-ttu-id="d34f3-128">這個查詢會尋找尚未保存且已暫止的所有執行個體，而且會針對這些執行個體傳回 ID、建立時間 (以 UTC 時間儲存)、暫停原因和例外狀況名稱。</span><span class="sxs-lookup"><span data-stu-id="d34f3-128">This query finds all suspended instances that have not been persisted, and returns the ID, creation time (stored in UTC time), suspension reason, and exception name for them.</span></span>  
  
    ```sql  
    select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0   
            and IsSuspended = 1  
    ```  
  
 <span data-ttu-id="d34f3-129">當您刪除非保存的執行個體時，請務必小心謹慎。</span><span class="sxs-lookup"><span data-stu-id="d34f3-129">Use care when you are deleting non-persisted instances.</span></span> <span data-ttu-id="d34f3-130">一般而言，您可以放心移除 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 所建立且已暫止或未載入的非保存執行個體。</span><span class="sxs-lookup"><span data-stu-id="d34f3-130">In general, it is safe to remove non-persisted instances created by <xref:System.ServiceModel.Activities.WorkflowServiceHost> that are suspended or are not loaded.</span></span> <span data-ttu-id="d34f3-131">這些特定的執行個體可以從存放區中刪除，其方式是從 `[System.Activities.DurableInstancing].[Instances]` 檢視中加以刪除，或是使用下列 SQL 命令來替代正確的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="d34f3-131">Those specific instances can be deleted from the store by deleting them from the `[System.Activities.DurableInstancing].[Instances]` view by using the following SQL command, substituting the correct instance ID.</span></span>  
  
```sql  
delete [System.Activities.DurableInstancing].[Instances]   
    where InstanceId=’078a9bc4-ada5-4f9e-8cce-b0eb0009995f’  
```  
  
> [!WARNING]
>  <span data-ttu-id="d34f3-132">我們不建議您移除所有非保存執行個體，因為這樣會包含剛剛建立且尚未保存的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d34f3-132">We do not recommend removing all non-persisted instances because this includes instances that have just been created and have not yet been persisted.</span></span>
