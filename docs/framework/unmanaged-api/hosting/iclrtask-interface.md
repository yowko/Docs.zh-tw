---
title: ICLRTask 介面
ms.date: 03/30/2017
api_name:
- ICLRTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask
helpviewer_keywords:
- ICLRTask interface [.NET Framework hosting]
ms.assetid: b3a44df3-578a-4451-b55e-70c8e7695f5e
topic_type:
- apiref
ms.openlocfilehash: b1327e13006ca4b3f9074c1348b1817c9a1b3728
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503948"
---
# <a name="iclrtask-interface"></a><span data-ttu-id="35081-102">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="35081-102">ICLRTask Interface</span></span>
<span data-ttu-id="35081-103">提供的方法可讓主機提出 common language runtime （CLR）的要求，或提供相關聯工作的通知給 CLR。</span><span class="sxs-lookup"><span data-stu-id="35081-103">Provides methods that allow the host to make requests of the common language runtime (CLR), or to provide notification to the CLR about the associated task.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="35081-104">方法</span><span class="sxs-lookup"><span data-stu-id="35081-104">Methods</span></span>  
  
|<span data-ttu-id="35081-105">方法</span><span class="sxs-lookup"><span data-stu-id="35081-105">Method</span></span>|<span data-ttu-id="35081-106">描述</span><span class="sxs-lookup"><span data-stu-id="35081-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="35081-107">Abort 方法</span><span class="sxs-lookup"><span data-stu-id="35081-107">Abort Method</span></span>](iclrtask-abort-method.md)|<span data-ttu-id="35081-108">要求 CLR 中止目前實例所代表的工作 `ICLRTask` 。</span><span class="sxs-lookup"><span data-stu-id="35081-108">Requests that the CLR abort the task that the current `ICLRTask` instance represents.</span></span>|  
|[<span data-ttu-id="35081-109">ExitTask 方法</span><span class="sxs-lookup"><span data-stu-id="35081-109">ExitTask Method</span></span>](iclrtask-exittask-method.md)|<span data-ttu-id="35081-110">通知 CLR，與目前實例相關聯的工作 `ICLRTask` 正在結束，並嘗試正常關閉工作。</span><span class="sxs-lookup"><span data-stu-id="35081-110">Notifies the CLR that the task associated with the current `ICLRTask` instance is ending, and attempts to shut the task down gracefully.</span></span>|  
|[<span data-ttu-id="35081-111">GetMemStats 方法</span><span class="sxs-lookup"><span data-stu-id="35081-111">GetMemStats Method</span></span>](iclrtask-getmemstats-method.md)|<span data-ttu-id="35081-112">取得目前實例所代表之工作使用記憶體資源的統計資訊 `ICLRTask` 。</span><span class="sxs-lookup"><span data-stu-id="35081-112">Gets statistical information on the use of memory resources by the task represented by the current `ICLRTask` instance.</span></span>|  
|[<span data-ttu-id="35081-113">LocksHeld 方法</span><span class="sxs-lookup"><span data-stu-id="35081-113">LocksHeld Method</span></span>](iclrtask-locksheld-method.md)|<span data-ttu-id="35081-114">取得目前保留在工作上的鎖定數目。</span><span class="sxs-lookup"><span data-stu-id="35081-114">Gets the number of locks currently held on the task.</span></span>|  
|[<span data-ttu-id="35081-115">NeedsPriorityScheduling 方法</span><span class="sxs-lookup"><span data-stu-id="35081-115">NeedsPriorityScheduling Method</span></span>](iclrtask-needspriorityscheduling-method.md)|<span data-ttu-id="35081-116">取得值，指出主機是否應指派高優先順序來重新排定目前實例所代表的工作 `ICLRTask` 。</span><span class="sxs-lookup"><span data-stu-id="35081-116">Gets a value indicating whether the host should assign a high priority to rescheduling the task represented by the current `ICLRTask` instance.</span></span>|  
|[<span data-ttu-id="35081-117">Reset 方法</span><span class="sxs-lookup"><span data-stu-id="35081-117">Reset Method</span></span>](iclrtask-reset-method.md)|<span data-ttu-id="35081-118">通知 CLR 主機已完成工作，並可讓 CLR 重複使用目前的 `ICLRTask` 實例來表示另一個工作。</span><span class="sxs-lookup"><span data-stu-id="35081-118">Informs the CLR that the host has completed a task, and enables the CLR to reuse the current `ICLRTask` instance to represent another task.</span></span>|  
|[<span data-ttu-id="35081-119">RudeAbort 方法</span><span class="sxs-lookup"><span data-stu-id="35081-119">RudeAbort Method</span></span>](iclrtask-rudeabort-method.md)|<span data-ttu-id="35081-120">導致 CLR 立即中止目前實例所代表的工作 `ICLRTask` ，而不保證會執行完成項。</span><span class="sxs-lookup"><span data-stu-id="35081-120">Causes the CLR to abort the task represented by the current `ICLRTask` instance immediately, without a guarantee that finalizers will be executed.</span></span>|  
|[<span data-ttu-id="35081-121">SetTaskIdentifier 方法</span><span class="sxs-lookup"><span data-stu-id="35081-121">SetTaskIdentifier Method</span></span>](iclrtask-settaskidentifier-method.md)|<span data-ttu-id="35081-122">設定目前實例所代表之工作的唯一識別碼 `ICLRTask` ，以用於偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="35081-122">Sets a unique identifier for the task represented by the current `ICLRTask` instance, for use in debugging.</span></span>|  
|[<span data-ttu-id="35081-123">SwitchIn 方法</span><span class="sxs-lookup"><span data-stu-id="35081-123">SwitchIn Method</span></span>](iclrtask-switchin-method.md)|<span data-ttu-id="35081-124">通知 CLR，目前實例所代表的工作處於 `ICLRTask` 可運作狀態。</span><span class="sxs-lookup"><span data-stu-id="35081-124">Notifies the CLR that the task represented by the current `ICLRTask` instance is in an operable state.</span></span>|  
|[<span data-ttu-id="35081-125">SwitchOut 方法</span><span class="sxs-lookup"><span data-stu-id="35081-125">SwitchOut Method</span></span>](iclrtask-switchout-method.md)|<span data-ttu-id="35081-126">通知 CLR，目前實例所代表的工作 `ICLRTask` 已不再處於可運作狀態。</span><span class="sxs-lookup"><span data-stu-id="35081-126">Notifies the CLR that the task represented by the current `ICLRTask` instance is no longer in an operable state.</span></span>|  
|[<span data-ttu-id="35081-127">YieldTask 方法</span><span class="sxs-lookup"><span data-stu-id="35081-127">YieldTask Method</span></span>](iclrtask-yieldtask-method.md)|<span data-ttu-id="35081-128">要求 CLR 將處理器時間提供給其他工作使用。</span><span class="sxs-lookup"><span data-stu-id="35081-128">Requests that the CLR make processor time available to other tasks.</span></span> <span data-ttu-id="35081-129">CLR 不保證工作會進入可能會產生處理時間的狀態。</span><span class="sxs-lookup"><span data-stu-id="35081-129">The CLR makes no guarantee that the task will be put in a state where it can yield processing time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35081-130">備註</span><span class="sxs-lookup"><span data-stu-id="35081-130">Remarks</span></span>  
 <span data-ttu-id="35081-131">`ICLRTask`是 CLR 工作的標記法。</span><span class="sxs-lookup"><span data-stu-id="35081-131">An `ICLRTask` is the representation of a task for the CLR.</span></span> <span data-ttu-id="35081-132">在程式碼執行期間的任何時間點，可以將工作描述為正在執行或等待執行。</span><span class="sxs-lookup"><span data-stu-id="35081-132">At any point during code execution, a task can be described either as running or waiting to run.</span></span> <span data-ttu-id="35081-133">主機 `ICLRTask::SwitchIn` 會呼叫方法，以通知 CLR 目前實例所代表的工作 `ICLRTask` 現在處於可運作狀態。</span><span class="sxs-lookup"><span data-stu-id="35081-133">The host calls the `ICLRTask::SwitchIn` method to notify the CLR that the task that the current `ICLRTask` instance represents is now in an operable state.</span></span> <span data-ttu-id="35081-134">呼叫之後， `ICLRTask::SwitchIn` 主機可以在任何作業系統執行緒上排程工作，但執行時間需要執行緒親和性（如呼叫[IHostTaskManager：： BeginThreadAffinity](ihosttaskmanager-beginthreadaffinity-method.md)和[IHostTaskManager：： EndThreadAffinity](ihosttaskmanager-endthreadaffinity-method.md)方法所指定）的情況除外。</span><span class="sxs-lookup"><span data-stu-id="35081-134">After a call to `ICLRTask::SwitchIn`, the host can schedule the task on any operating system thread, except in cases where the runtime requires thread-affinity, as specified by calls to the [IHostTaskManager::BeginThreadAffinity](ihosttaskmanager-beginthreadaffinity-method.md) and [IHostTaskManager::EndThreadAffinity](ihosttaskmanager-endthreadaffinity-method.md) methods.</span></span> <span data-ttu-id="35081-135">一些時間之後，作業系統可能會決定從執行緒中移除工作，並將它置於非執行中的狀態。</span><span class="sxs-lookup"><span data-stu-id="35081-135">Some time later, the operating system might decide to remove the task from the thread and place it in a non-running state.</span></span> <span data-ttu-id="35081-136">例如，當工作在同步處理原始物件上封鎖，或等候 i/o 作業完成時，就可能發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="35081-136">For example, this might happen whenever the task blocks on synchronization primitives, or waits for I/O operations to complete.</span></span> <span data-ttu-id="35081-137">主機會呼叫[SwitchOut](iclrtask-switchout-method.md)來通知 CLR，目前實例所代表的工作 `ICLRTask` 已不再處於可運作狀態。</span><span class="sxs-lookup"><span data-stu-id="35081-137">The host calls [SwitchOut](iclrtask-switchout-method.md) to notify the CLR that the task represented by the current `ICLRTask` instance is no longer in an operable state.</span></span>  
  
 <span data-ttu-id="35081-138">工作通常會在程式碼執行結束時終止。</span><span class="sxs-lookup"><span data-stu-id="35081-138">A task typically terminates at the end of code execution.</span></span> <span data-ttu-id="35081-139">此時，主機會呼叫來終結 `ICLRTask::ExitTask` 相關聯的 `ICLRTask` 。</span><span class="sxs-lookup"><span data-stu-id="35081-139">At that time, the host calls `ICLRTask::ExitTask` to destroy the associated `ICLRTask`.</span></span> <span data-ttu-id="35081-140">不過，也可以使用對的呼叫來回收 `ICLRTask::Reset` 工作，讓 `ICLRTask` 實例再次使用。</span><span class="sxs-lookup"><span data-stu-id="35081-140">However, tasks can also be recycled by using a call to `ICLRTask::Reset`, which allows the `ICLRTask` instance to be used again.</span></span> <span data-ttu-id="35081-141">這種方法可防止重複建立和終結實例的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="35081-141">This approach prevents the overhead of repeatedly creating and destroying instances.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35081-142">規格需求</span><span class="sxs-lookup"><span data-stu-id="35081-142">Requirements</span></span>  
 <span data-ttu-id="35081-143">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="35081-143">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35081-144">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="35081-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="35081-145">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="35081-145">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="35081-146">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35081-146">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35081-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35081-147">See also</span></span>

- [<span data-ttu-id="35081-148">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="35081-148">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="35081-149">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="35081-149">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="35081-150">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="35081-150">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="35081-151">裝載介面</span><span class="sxs-lookup"><span data-stu-id="35081-151">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="35081-152">ICLRTask2 介面</span><span class="sxs-lookup"><span data-stu-id="35081-152">ICLRTask2 Interface</span></span>](iclrtask2-interface.md)
