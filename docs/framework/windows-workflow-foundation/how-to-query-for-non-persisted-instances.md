---
title: HOW TO：非保存執行個體的查詢
ms.date: 03/30/2017
ms.assetid: 294019b1-c1a7-4b81-a14f-b47c106cd723
ms.openlocfilehash: 87b29ce6a5858872929cea4408d0d7bcc1b378d1
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425324"
---
# <a name="how-to-query-for-non-persisted-instances"></a><span data-ttu-id="2e154-102">HOW TO：非保存執行個體的查詢</span><span class="sxs-lookup"><span data-stu-id="2e154-102">How to: Query for Non-persisted Instances</span></span>

<span data-ttu-id="2e154-103">當建立服務的新執行個體且服務已定義 SQL 工作流程執行個體存放區行為時，服務主機會在執行個體存放區中為該服務執行個體建立初始項目。</span><span class="sxs-lookup"><span data-stu-id="2e154-103">When a new instance of a service is created and the service has the SQL Workflow Instance Store behavior defined, the service host creates a initial entry for that service instance in the instance store.</span></span> <span data-ttu-id="2e154-104">接著在初次保存服務執行個體時，SQL 工作流程執行個體存放區行為會保存目前的執行個體狀態，連同啟動、復原和控制所需的其他資料。</span><span class="sxs-lookup"><span data-stu-id="2e154-104">Subsequently when the service instance persists for the first time, the SQL Workflow Instance Store behavior stores the current instance state together with additional data that is required for activation, recovery, and control.</span></span>

<span data-ttu-id="2e154-105">如果執行個體未在執行個體的初始項目建立時保存，則會將服務執行個體視為處於非保存狀態。</span><span class="sxs-lookup"><span data-stu-id="2e154-105">If an instance is not persisted after the initial entry for the instance is created, the service instance is said to be in the non-persisted state.</span></span> <span data-ttu-id="2e154-106">所有保存的服務執行個體都可以進行查詢並加以控制。</span><span class="sxs-lookup"><span data-stu-id="2e154-106">All the persisted service instances can be queried and controlled.</span></span> <span data-ttu-id="2e154-107">非保存的服務執行個體則無法進行查詢，也無法加以控制。</span><span class="sxs-lookup"><span data-stu-id="2e154-107">Non-persisted service instances can neither be queried nor controlled.</span></span> <span data-ttu-id="2e154-108">如果非保存的執行個體因為未處理的例外狀況而暫止，則可以進行查詢，但無法加以控制。</span><span class="sxs-lookup"><span data-stu-id="2e154-108">If a non-persisted instance is suspended due to an unhandled exception it can be queried but not controlled.</span></span>

<span data-ttu-id="2e154-109">在下列案例中，尚未保存的永久性服務執行個體會持續處於非保存狀態：</span><span class="sxs-lookup"><span data-stu-id="2e154-109">Durable service instances that are not yet persisted remain in a non-persisted state in the following scenarios:</span></span>

- <span data-ttu-id="2e154-110">服務主機在執行個體初次保存之前當機。</span><span class="sxs-lookup"><span data-stu-id="2e154-110">The service host crashes before the instance persisted for the first time.</span></span> <span data-ttu-id="2e154-111">執行個體的初始項目保留在執行個體存放區中。</span><span class="sxs-lookup"><span data-stu-id="2e154-111">The initial entry for the instance remains in the instance store.</span></span> <span data-ttu-id="2e154-112">執行個體無法復原。</span><span class="sxs-lookup"><span data-stu-id="2e154-112">The instance is not recoverable.</span></span> <span data-ttu-id="2e154-113">如果相互關聯的訊息抵達，則執行個體會再次變成作用中。</span><span class="sxs-lookup"><span data-stu-id="2e154-113">If a correlated message arrives, the instance becomes active again.</span></span>

- <span data-ttu-id="2e154-114">執行個體在初次保存之前發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2e154-114">The instance experiences an unhandled exception before it persisted for the first time.</span></span> <span data-ttu-id="2e154-115">發生下列情況</span><span class="sxs-lookup"><span data-stu-id="2e154-115">The following scenarios arise</span></span>

  - <span data-ttu-id="2e154-116">如果值**UnhandledExceptionAction**屬性設定為**放棄**、 服務部署資訊會寫入執行個體存放區，而從記憶體卸載執行個體時。</span><span class="sxs-lookup"><span data-stu-id="2e154-116">If the value of the **UnhandledExceptionAction** property is set to **Abandon**, the service deployment information is written to the instance store and the instance is unloaded from memory.</span></span> <span data-ttu-id="2e154-117">執行個體在持續性資料庫中保持非保存狀態。</span><span class="sxs-lookup"><span data-stu-id="2e154-117">The instance remains in non-persisted state in the persistence database.</span></span>

  - <span data-ttu-id="2e154-118">如果值**UnhandledExceptionAction**屬性設定為**AbandonAndSuspend**，則服務部署資訊會寫入持續性資料庫，而執行個體的狀態設為**暫止**。</span><span class="sxs-lookup"><span data-stu-id="2e154-118">If the value of the **UnhandledExceptionAction** property is set to **AbandonAndSuspend**, the service deployment information is written to the persistence database and the instance state is set to **Suspended**.</span></span> <span data-ttu-id="2e154-119">執行個體無法繼續、取消或終止。</span><span class="sxs-lookup"><span data-stu-id="2e154-119">The instance cannot be resumed, canceled, or terminated.</span></span> <span data-ttu-id="2e154-120">服務主機無法載入執行個體，因為執行個體尚未保存，所以執行個體的資料庫項目並不完整。</span><span class="sxs-lookup"><span data-stu-id="2e154-120">The service host cannot load the instance because the instance hasn't persisted yet and, hence the database entry for the instance is not complete.</span></span>

  - <span data-ttu-id="2e154-121">如果的值**UnhandledExceptionAction**屬性設定為**取消**或是**終止**，服務部署資訊會寫入執行個體存放區，執行個體狀態會設為**已完成**。</span><span class="sxs-lookup"><span data-stu-id="2e154-121">If the value of the **UnhandledExceptionAction** property is set to **Cancel** or **Terminate**, the service deployment information is written to the instance store and the instance state is set to **Completed**.</span></span>

<span data-ttu-id="2e154-122">以下各節提供範例查詢，用來尋找 SQL 持續性資料庫中的非保存執行個體，以及從資料庫中刪除這些執行個體。</span><span class="sxs-lookup"><span data-stu-id="2e154-122">The following sections provide sample queries to find non-persisted instances in the SQL persistence database and to delete these instances from the database.</span></span>

## <a name="to-find-all-instances-not-persisted-yet"></a><span data-ttu-id="2e154-123">尋找所有尚未保存的執行個體</span><span class="sxs-lookup"><span data-stu-id="2e154-123">To find all instances not persisted yet</span></span>

<span data-ttu-id="2e154-124">下面的 SQL 查詢會傳回所有尚未保存至持續性資料庫內之執行個體的識別碼和建立時間。</span><span class="sxs-lookup"><span data-stu-id="2e154-124">The following SQL query returns the ID and creation time for all instances that are not persisted in to the persistence database yet.</span></span>

```sql
select InstanceId, CreationTime from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0;
```

## <a name="to-find-all-instances-not-persisted-yet-and-also-not-loaded"></a><span data-ttu-id="2e154-125">尋找所有尚未保存且尚未載入的執行個體</span><span class="sxs-lookup"><span data-stu-id="2e154-125">To find all instances not persisted yet and also not loaded</span></span>
 <span data-ttu-id="2e154-126">下面的 SQL 查詢會傳回所有尚未保留且尚未載入之執行個體的識別碼和建立時間。</span><span class="sxs-lookup"><span data-stu-id="2e154-126">The following SQL query returns ID and creation time for all instances that are not persisted and also are not loaded.</span></span>

```sql
select InstanceId, CreationTime from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0 and CurrentMachine is NULL;
```

## <a name="to-find-all-suspended-instances-not-persisted-yet"></a><span data-ttu-id="2e154-127">尋找所有尚未保存的已暫止執行個體</span><span class="sxs-lookup"><span data-stu-id="2e154-127">To find all suspended instances not persisted yet</span></span>

<span data-ttu-id="2e154-128">下面的 SQL 查詢會傳回所有尚未保存且處於暫止狀態之執行個體的識別碼、建立時間、暫止原因和暫止例外狀況名稱。</span><span class="sxs-lookup"><span data-stu-id="2e154-128">The following SQL query returns ID, creation time, suspension reason, and suspension exception name for all instances that are not persisted and also in a suspended state.</span></span>

```sql
select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0 and IsSuspended = 1;
```

## <a name="to-delete-non-persisted-instances-from-the-persistence-database"></a><span data-ttu-id="2e154-129">從持續性資料庫刪除非保存執行個體</span><span class="sxs-lookup"><span data-stu-id="2e154-129">To delete non-persisted instances from the persistence database</span></span>

<span data-ttu-id="2e154-130">您應該定期檢查執行個體存放區中是否有非保存執行個體，並且從執行個體存放區移除確定將不會接收相互關聯訊息的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2e154-130">You should periodically check the instance store for non-persisted instances and remove instances from the instance store if you are sure that the instance will not receive a correlated message.</span></span> <span data-ttu-id="2e154-131">例如，如果執行個體已在資料庫中停留數個月之久，而您知道工作流程通常只有數天的存留期，則可放心將該執行個體視為已損毀的未初始化執行個體。</span><span class="sxs-lookup"><span data-stu-id="2e154-131">For example, if the instance has been in the database for several months and you know that the workflow typically has a lifetime of a few days, it would be safe to assume that this is an uninitialized instance that had crashed.</span></span>

<span data-ttu-id="2e154-132">一般而言，您可以放心刪除未暫止或未載入的非保存執行個體。</span><span class="sxs-lookup"><span data-stu-id="2e154-132">In general, it is safe to delete non-persisted instances that are not suspended or not loaded.</span></span> <span data-ttu-id="2e154-133">您不應該刪除**所有**非保存執行個體因為這個執行個體集包含剛建立但不執行個體尚未保存的。</span><span class="sxs-lookup"><span data-stu-id="2e154-133">You should not delete **all** the non-persisted instances because this instance set includes instances that are just created but are not persisted yet.</span></span> <span data-ttu-id="2e154-134">您只應刪除因載入執行個體的工作流程服務主機造成例外狀況，或因執行個體本身造成例外狀況而留下的非保存執行個體。</span><span class="sxs-lookup"><span data-stu-id="2e154-134">You should only delete non-persisted instances that are left over because the workflow service host that had the instance loaded caused an exception or the instance itself caused an exception.</span></span>

> [!WARNING]
> <span data-ttu-id="2e154-135">從執行個體存放區刪除非保存執行個體會減少存放區的大小，並且可提升存放區作業的效能。</span><span class="sxs-lookup"><span data-stu-id="2e154-135">Deleting non-persisted instances from the instance store decreases the size of the store and may improve the performance of store operations.</span></span>
