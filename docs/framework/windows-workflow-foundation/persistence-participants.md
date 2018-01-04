---
title: "持續性參與者"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f84d2d5d-1c1b-4f19-be45-65b552d3e9e3
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5b85acf2e3c4d885988e92948481182b7cf8c32c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="persistence-participants"></a><span data-ttu-id="5eb4b-102">持續性參與者</span><span class="sxs-lookup"><span data-stu-id="5eb4b-102">Persistence Participants</span></span>
<span data-ttu-id="5eb4b-103">持續性參與者可參與由應用程式主機所觸發的持續性作業 (「儲存」或「載入」)。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-103">A persistence participant can participate in a persistence operation (Save or Load) triggered by an application host.</span></span> <span data-ttu-id="5eb4b-104">[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]隨附兩個抽象類別， **PersistenceParticipant**和**PersistenceIOParticipant**，讓您可以用來建立持續性參與者。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-104">The [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] ships with two abstract classes, **PersistenceParticipant** and **PersistenceIOParticipant**, which you can use to create a persistence participant.</span></span> <span data-ttu-id="5eb4b-105">持續性參與者會衍生自這些類別的其中一個、實作感興趣的方法，然後將類別的執行個體加入至 <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> 上的 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 集合。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-105">A persistence participant derives from one of these classes, implements the methods of interest, and then adds an instance of the class to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> collection on the <xref:System.ServiceModel.Activities.WorkflowServiceHost> .</span></span> <span data-ttu-id="5eb4b-106">應用程式主機保存工作流程執行個體時，可能會尋找此類工作流程擴充功能，並且在適當的時間於持續性參與者上叫用適當的方法。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-106">The application host may look for such workflow extensions when persisting a workflow instance and invoke appropriate methods on the persistence participants at appropriate times.</span></span>  
  
 <span data-ttu-id="5eb4b-107">以下清單描述持續性子系統在不同階段的「保存」(儲存) 作業時所執行的工作。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-107">The following list describes the tasks performed by the persistence subsystem in different stages of the Persist (Save) operation.</span></span> <span data-ttu-id="5eb4b-108">持續性參與者會用於第三與第四階段。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-108">The persistence participants are used in the third and fourth stages.</span></span> <span data-ttu-id="5eb4b-109">如果參與者是 IO 參與者 (同樣參與 IO 作業的持續性參與者)，則此參與者會用於第六階段。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-109">If the participant is an IO participant (a persistence participant that also participates in IO operations), the participant is also used in the sixth stage.</span></span>  
  
1.  <span data-ttu-id="5eb4b-110">收集內建值，包含工作流程狀態、書籤、對應的變數以及時間戳記。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-110">Gathers built-in values, including workflow state, bookmarks, mapped variables, and timestamp.</span></span>  
  
2.  <span data-ttu-id="5eb4b-111">收集加入至與工作流程執行個體相關之擴充集合的所有持續性參與者。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-111">Gathers all persistence participants that were added to the extension collection associated with the workflow instance.</span></span>  
  
3.  <span data-ttu-id="5eb4b-112">叫用由所有持續性參與者實作的 <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-112">Invokes the <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> method implemented by all persistence participants.</span></span>  
  
4.  <span data-ttu-id="5eb4b-113">叫用由所有持續性參與者實作的 <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-113">Invokes the <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> method implemented by all persistence participants.</span></span>  
  
5.  <span data-ttu-id="5eb4b-114">保存工作流程，或將工作流程儲存至持續性存放區中。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-114">Persist or save the workflow into the persistence store.</span></span>  
  
6.  <span data-ttu-id="5eb4b-115">在所有持續性 IO 參與者上叫用 <xref:System.Activities.Persistence.PersistenceIOParticipant.BeginOnSave%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-115">Invokes the <xref:System.Activities.Persistence.PersistenceIOParticipant.BeginOnSave%2A> method on all of the persistence IO participants.</span></span> <span data-ttu-id="5eb4b-116">如果參與者並非 IO 參與者，則會略過此工作。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-116">If the participant is not an IO participant, this task is skipped.</span></span> <span data-ttu-id="5eb4b-117">如果持續性的時段屬於交易性質，則交易會在 Transaction.Current 屬性中提供。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-117">If the persistence episode is transactional, the transaction is provided in Transaction.Current property.</span></span>  
  
7.  <span data-ttu-id="5eb4b-118">等候所有持續性參與者完成。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-118">Waits for all persistence participants to complete.</span></span> <span data-ttu-id="5eb4b-119">如果所有參與者成功保存執行個體資料，則認可交易。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-119">If all the participants succeed in persisting instance data, commits the transaction.</span></span>  
  
 <span data-ttu-id="5eb4b-120">持續性參與者衍生自**PersistenceParticipant**類別，並可能實作**CollectValues**和**MapValues**方法。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-120">A persistence participant derives from the **PersistenceParticipant** class and may implement the **CollectValues** and **MapValues** methods.</span></span> <span data-ttu-id="5eb4b-121">持續性 IO 參與者衍生自**PersistenceIOParticipant**類別，並可能實作**BeginOnSave**方法，除了實作**CollectValues**和**MapValues**方法。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-121">A persistence IO participant derives from the **PersistenceIOParticipant** class and may implement the **BeginOnSave** method in addition to implementing the **CollectValues** and **MapValues** methods.</span></span>  
  
 <span data-ttu-id="5eb4b-122">每個階段都會先完成，再開始進行下一個階段。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-122">Each stage is completed before the next stage begins.</span></span> <span data-ttu-id="5eb4b-123">例如，值從收集**所有**第一階段的持續性參與者。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-123">For example, values are collected from **all** persistence participants in the first stage.</span></span> <span data-ttu-id="5eb4b-124">然後，會將在第一階段中收集到的所有值提供給第二階段中的所有持續性參與者，以進行對應。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-124">Then all the values collected in the first stage are provided to all persistence participants in the second stage for mapping.</span></span> <span data-ttu-id="5eb4b-125">接著，會將在第一和第二階段中收集到的所有值提供給第三階段中的所有持續性參與者，以進行對應，依此類推。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-125">Then all the values collected and mapped in the first and second stages are provided to the persistence provider in the third stage, and so on.</span></span>  
  
 <span data-ttu-id="5eb4b-126">以下清單描述持續性子系統在不同階段的「載入」作業時所執行的工作。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-126">The following list describes the tasks performed by the persistence subsystem in different stages of the Load operation.</span></span> <span data-ttu-id="5eb4b-127">持續性參與者會用於第四階段。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-127">The persistence participants are used in the fourth stage.</span></span> <span data-ttu-id="5eb4b-128">持續性 IO 參與者 (同樣參與 IO 作業的持續性參與者) 也會用於第三階段。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-128">The persistence IO participants (persistence participants that also participate in IO operations) are also used in the third stage.</span></span>  
  
1.  <span data-ttu-id="5eb4b-129">收集加入至與工作流程執行個體相關之擴充集合的所有持續性參與者。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-129">Gathers all persistence participants that were added to the extension collection associated with the workflow instance.</span></span>  
  
2.  <span data-ttu-id="5eb4b-130">自持續性存放區載入工作流程。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-130">Loads the workflow from the persistence store.</span></span>  
  
3.  <span data-ttu-id="5eb4b-131">在所有持續性 IO 參與者上叫用 <xref:System.Activities.Persistence.PersistenceIOParticipant.BeginOnLoad%2A> 方法，並等候所有持續性參與者完成。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-131">Invokes the <xref:System.Activities.Persistence.PersistenceIOParticipant.BeginOnLoad%2A> on all persistence IO participants and waits for all the persistence participants to complete.</span></span> <span data-ttu-id="5eb4b-132">如果持續性的時段屬於交易性質，則交易會在 Transaction.Current 中提供。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-132">If the persistence episode is transactional, the transaction is provided in Transaction.Current.</span></span>  
  
4.  <span data-ttu-id="5eb4b-133">根據從持續性存放區所擷取的資料，載入記憶體中的工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-133">Loads the workflow instance in memory based on the data retrieved from the persistence store.</span></span>  
  
5.  <span data-ttu-id="5eb4b-134">叫用每個持續性參與者上的 <xref:System.Activities.Persistence.PersistenceParticipant.PublishValues%2A>。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-134">Invokes <xref:System.Activities.Persistence.PersistenceParticipant.PublishValues%2A> on each persistence participant.</span></span>  
  
 <span data-ttu-id="5eb4b-135">持續性參與者衍生自**PersistenceParticipant**類別，並可能實作**PublishValues**方法。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-135">A persistence participant derives from the **PersistenceParticipant** class and may implement the **PublishValues** method.</span></span> <span data-ttu-id="5eb4b-136">持續性 IO 參與者衍生自**PersistenceIOParticipant**類別，並可能實作**BeginOnLoad**方法，除了實作**PublishValues**方法。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-136">A persistence IO participant derives from the **PersistenceIOParticipant** class and may implement the **BeginOnLoad** method in addition to implementing the **PublishValues** method.</span></span>  
  
 <span data-ttu-id="5eb4b-137">載入工作流程執行個體時，持續性提供者會建立該執行個體的鎖定。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-137">When loading a workflow instance the persistence provider creates a lock on that instance.</span></span> <span data-ttu-id="5eb4b-138">這可防止在多節點的案例中，多個主機載入執行個體。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-138">This prevents the instance from being loaded by more than one host in a multi-node scenario.</span></span> <span data-ttu-id="5eb4b-139">如果您嘗試載入已鎖定的工作流程執行個體您會看到類似下列的例外狀況： 例外狀況"System.ServiceModel.Persistence.InstanceLockException： 要求的作業無法完成，因為鎖定執行個體 '00000000-0000-0000-0000-000000000000' 無法取得"。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-139">If you attempt to load a workflow instance that has been locked you will see an exception like the following: The exception " System.ServiceModel.Persistence.InstanceLockException: The requested operation could not complete because the lock for instance '00000000-0000-0000-0000-000000000000' could not be acquired".</span></span> <span data-ttu-id="5eb4b-140">當下列任一情形發生時，就會發生這個錯誤：</span><span class="sxs-lookup"><span data-stu-id="5eb4b-140">This error is caused when one of the following occurs:</span></span>  
  
-   <span data-ttu-id="5eb4b-141">在多節點的案例中，執行個體是由另一個主機載入。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-141">In a multi-node scenario the instance is loaded by another host.</span></span>  <span data-ttu-id="5eb4b-142">有幾個不同的方法來解決這些類型的衝突：將處理轉送到擁有鎖定的節點然後重試，或是強制載入，這會導致其他主機無法儲存它們的工作。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-142">There are a few different ways to resolve these types of conflicts: forward the processing to the node which owns the lock and retry, or force the load which will cause the other host to be unable to save their work.</span></span>  
  
-   <span data-ttu-id="5eb4b-143">在單一節點的案例中且主機毀損。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-143">In a single-node scenario and the host crashed.</span></span>  <span data-ttu-id="5eb4b-144">當主機再次啟動時 (處理序回收或建立新的持續性提供者處理站)，新主機嘗試載入執行個體，但此執行個體仍被舊主機鎖定，因為鎖定尚未到期。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-144">When the host starts up again (a process recycle or creating a new persistence provider factory) the new host attempts to load an instance which is still locked by the old host because the lock hasn't expired yet.</span></span>  
  
-   <span data-ttu-id="5eb4b-145">在單一節點的案例中，出現問題的執行個體已在某個時間點中止，新的持續性提供者執行個體已建立，其具有不同的主機 ID。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-145">In a single-node scenario and the instance in question was aborted at some point and a new persistence provider instance is created which has a different host ID.</span></span>  
  
 <span data-ttu-id="5eb4b-146">鎖定逾時值預設為 5 分鐘，您可以在呼叫 <xref:System.ServiceModel.Persistence.PersistenceProvider.Load%2A> 時指定不同的逾時值。</span><span class="sxs-lookup"><span data-stu-id="5eb4b-146">The lock timeout value has a default value of 5 minutes, you can specify a different timeout value when calling <xref:System.ServiceModel.Persistence.PersistenceProvider.Load%2A>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5eb4b-147">本節內容</span><span class="sxs-lookup"><span data-stu-id="5eb4b-147">In This Section</span></span>  
  
-   [<span data-ttu-id="5eb4b-148">如何：建立自訂持續性參與者</span><span class="sxs-lookup"><span data-stu-id="5eb4b-148">How to: Create a Custom Persistence Participant</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-persistence-participant.md)  
  
## <a name="see-also"></a><span data-ttu-id="5eb4b-149">請參閱</span><span class="sxs-lookup"><span data-stu-id="5eb4b-149">See Also</span></span>  
 [<span data-ttu-id="5eb4b-150">存放區擴充性</span><span class="sxs-lookup"><span data-stu-id="5eb4b-150">Store Extensibility</span></span>](../../../docs/framework/windows-workflow-foundation/store-extensibility.md)
