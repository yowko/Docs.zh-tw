---
title: ICLRTask::Reset 方法
ms.date: 03/30/2017
api_name:
- ICLRTask.Reset
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Reset
helpviewer_keywords:
- ICLRTask::Reset method [.NET Framework hosting]
- Reset method, ICLRTask interface [.NET Framework hosting]
ms.assetid: 1bfb5d3a-0ffd-4bb4-9bf6-aec00cb675b7
topic_type:
- apiref
ms.openlocfilehash: 17fca3e5a2d763277d3a5f9f72e2d35be6fc350c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124647"
---
# <a name="iclrtaskreset-method"></a><span data-ttu-id="22bb6-102">ICLRTask::Reset 方法</span><span class="sxs-lookup"><span data-stu-id="22bb6-102">ICLRTask::Reset Method</span></span>
<span data-ttu-id="22bb6-103">通知 common language runtime （CLR），表示主機已完成工作，並讓 CLR 重複使用目前的[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)實例來表示另一個工作。</span><span class="sxs-lookup"><span data-stu-id="22bb6-103">Informs the common language runtime (CLR) that the host has completed a task, and enables the CLR to reuse the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance to represent another task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22bb6-104">語法</span><span class="sxs-lookup"><span data-stu-id="22bb6-104">Syntax</span></span>  
  
```cpp  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22bb6-105">參數</span><span class="sxs-lookup"><span data-stu-id="22bb6-105">Parameters</span></span>  
 `fFull`  
 <span data-ttu-id="22bb6-106">[in] `true`，如果執行時間除了與目前 `ICLRTask` 實例相關的安全性和地區設定資訊之外，應重設所有線程相關的靜態值;否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="22bb6-106">[in] `true`, if the runtime should reset all thread-related static values in addition to the security and locale information related to the current `ICLRTask` instance; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="22bb6-107">如果 `true`值，則執行時間會重設使用 <xref:System.Threading.Thread.AllocateDataSlot%2A> 或 <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>儲存的資料。</span><span class="sxs-lookup"><span data-stu-id="22bb6-107">If the value is `true`, the runtime resets data that was stored using <xref:System.Threading.Thread.AllocateDataSlot%2A> or <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22bb6-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="22bb6-108">Return Value</span></span>  
  
|<span data-ttu-id="22bb6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="22bb6-109">HRESULT</span></span>|<span data-ttu-id="22bb6-110">描述</span><span class="sxs-lookup"><span data-stu-id="22bb6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="22bb6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="22bb6-111">S_OK</span></span>|<span data-ttu-id="22bb6-112">已成功傳回 `Reset`。</span><span class="sxs-lookup"><span data-stu-id="22bb6-112">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="22bb6-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="22bb6-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="22bb6-114">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="22bb6-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="22bb6-115">能夠</span><span class="sxs-lookup"><span data-stu-id="22bb6-115">successfully</span></span>|  
|<span data-ttu-id="22bb6-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="22bb6-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="22bb6-117">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="22bb6-117">The call timed out.</span></span>|  
|<span data-ttu-id="22bb6-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="22bb6-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="22bb6-119">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="22bb6-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="22bb6-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="22bb6-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="22bb6-121">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="22bb6-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="22bb6-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="22bb6-122">E_FAIL</span></span>|<span data-ttu-id="22bb6-123">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="22bb6-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="22bb6-124">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="22bb6-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="22bb6-125">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="22bb6-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22bb6-126">備註</span><span class="sxs-lookup"><span data-stu-id="22bb6-126">Remarks</span></span>  
 <span data-ttu-id="22bb6-127">CLR 可以回收先前建立的 `ICLRTask` 實例，以避免每次需要全新的工作時重複建立新實例的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="22bb6-127">The CLR can recycle previously created `ICLRTask` instances to avoid the overhead of repeatedly creating new instances every time it needs a fresh task.</span></span> <span data-ttu-id="22bb6-128">主機會在完成工作時呼叫 `ICLRTask::Reset`，而不是[ICLRTask：： ExitTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) ，藉以啟用這項功能。</span><span class="sxs-lookup"><span data-stu-id="22bb6-128">The host enables this feature by calling `ICLRTask::Reset` instead of [ICLRTask::ExitTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) when it has completed a task.</span></span> <span data-ttu-id="22bb6-129">下列清單摘要說明 `ICLRTask` 實例的一般生命週期：</span><span class="sxs-lookup"><span data-stu-id="22bb6-129">The following list summarizes the normal life cycle of an `ICLRTask` instance:</span></span>  
  
1. <span data-ttu-id="22bb6-130">執行時間會建立新的 `ICLRTask` 實例。</span><span class="sxs-lookup"><span data-stu-id="22bb6-130">The runtime creates a new `ICLRTask` instance.</span></span>  
  
2. <span data-ttu-id="22bb6-131">執行時間會呼叫[IHostTaskManager：： GetCurrentTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md)以取得目前主機工作的參考。</span><span class="sxs-lookup"><span data-stu-id="22bb6-131">The runtime calls [IHostTaskManager::GetCurrentTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) to get a reference to the current host task.</span></span>  
  
3. <span data-ttu-id="22bb6-132">執行時間會呼叫[IHostTask：： SetCLRTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) ，將新的實例與主機工作產生關聯。</span><span class="sxs-lookup"><span data-stu-id="22bb6-132">The runtime calls [IHostTask::SetCLRTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) to associate the new instance with the host task.</span></span>  
  
4. <span data-ttu-id="22bb6-133">此工作會執行並完成。</span><span class="sxs-lookup"><span data-stu-id="22bb6-133">The task executes and completes.</span></span>  
  
5. <span data-ttu-id="22bb6-134">主機會藉由呼叫 `ICLRTask::ExitTask`來終結工作。</span><span class="sxs-lookup"><span data-stu-id="22bb6-134">The host destroys the task by calling `ICLRTask::ExitTask`.</span></span>  
  
 <span data-ttu-id="22bb6-135">`Reset` 以兩種方式改變此案例。</span><span class="sxs-lookup"><span data-stu-id="22bb6-135">`Reset` alters this scenario in two ways.</span></span> <span data-ttu-id="22bb6-136">在上述步驟5中，主機會呼叫 `Reset`，將工作重設為「清除」狀態，然後將 `ICLRTask` 實例與相關聯的[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)實例分離。</span><span class="sxs-lookup"><span data-stu-id="22bb6-136">In step 5 above, the host calls `Reset` to reset the task to a clean state, and then decouples the `ICLRTask` instance from its associated [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span> <span data-ttu-id="22bb6-137">如有需要，主機也可以快取 `IHostTask` 實例以供重複使用。</span><span class="sxs-lookup"><span data-stu-id="22bb6-137">If desired, the host can also cache the `IHostTask` instance for reuse.</span></span> <span data-ttu-id="22bb6-138">在上述步驟1中，執行時間會從快取中提取回收的 `ICLRTask`，而不是建立新的實例。</span><span class="sxs-lookup"><span data-stu-id="22bb6-138">In step 1 above, the runtime pulls a recycled `ICLRTask` from the cache instead of creating a new instance.</span></span>  
  
 <span data-ttu-id="22bb6-139">當主機也有可重複使用之背景工作角色的集區時，這個方法會很有作用。</span><span class="sxs-lookup"><span data-stu-id="22bb6-139">This approach works well when the host also has a pool of reusable worker tasks.</span></span> <span data-ttu-id="22bb6-140">當主機終結其中一個 `IHostTask` 實例時，它會藉由呼叫 `ExitTask`來終結對應的 `ICLRTask`。</span><span class="sxs-lookup"><span data-stu-id="22bb6-140">When the host destroys one of its `IHostTask` instances, it destroys the corresponding `ICLRTask` by calling `ExitTask`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22bb6-141">需求</span><span class="sxs-lookup"><span data-stu-id="22bb6-141">Requirements</span></span>  
 <span data-ttu-id="22bb6-142">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="22bb6-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22bb6-143">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="22bb6-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="22bb6-144">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="22bb6-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="22bb6-145">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22bb6-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22bb6-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="22bb6-146">See also</span></span>

- [<span data-ttu-id="22bb6-147">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="22bb6-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="22bb6-148">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="22bb6-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="22bb6-149">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="22bb6-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="22bb6-150">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="22bb6-150">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
