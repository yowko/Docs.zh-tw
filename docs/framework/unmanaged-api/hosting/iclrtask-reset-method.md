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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae0a2a3af532b81d7b346cdd17da1712dfa3cba8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499923"
---
# <a name="iclrtaskreset-method"></a><span data-ttu-id="d1f0d-102">ICLRTask::Reset 方法</span><span class="sxs-lookup"><span data-stu-id="d1f0d-102">ICLRTask::Reset Method</span></span>
<span data-ttu-id="d1f0d-103">通知 common language runtime (CLR) 主機已完成一項工作，並可讓重複使用目前的 CLR [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)來代表另一項工作的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d1f0d-103">Informs the common language runtime (CLR) that the host has completed a task, and enables the CLR to reuse the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance to represent another task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1f0d-104">語法</span><span class="sxs-lookup"><span data-stu-id="d1f0d-104">Syntax</span></span>  
  
```  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1f0d-105">參數</span><span class="sxs-lookup"><span data-stu-id="d1f0d-105">Parameters</span></span>  
 `fFull`  
 <span data-ttu-id="d1f0d-106">[in]`true`，如果執行階段應該重設所有執行緒相關靜態值除了與目前的安全性和地區設定資訊`ICLRTask`執行個體; 否則`false`。</span><span class="sxs-lookup"><span data-stu-id="d1f0d-106">[in] `true`, if the runtime should reset all thread-related static values in addition to the security and locale information related to the current `ICLRTask` instance; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="d1f0d-107">如果值為`true`，執行階段會使用儲存的資料重設<xref:System.Threading.Thread.AllocateDataSlot%2A>或<xref:System.Threading.Thread.AllocateNamedDataSlot%2A>。</span><span class="sxs-lookup"><span data-stu-id="d1f0d-107">If the value is `true`, the runtime resets data that was stored using <xref:System.Threading.Thread.AllocateDataSlot%2A> or <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1f0d-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="d1f0d-108">Return Value</span></span>  
  
|<span data-ttu-id="d1f0d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d1f0d-109">HRESULT</span></span>|<span data-ttu-id="d1f0d-110">描述</span><span class="sxs-lookup"><span data-stu-id="d1f0d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d1f0d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d1f0d-111">S_OK</span></span>|<span data-ttu-id="d1f0d-112">`Reset` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="d1f0d-112">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="d1f0d-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d1f0d-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d1f0d-114">不到程序中，載入 CLR 或 CLR 中不能在其中執行 managed 程式碼，或處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="d1f0d-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="d1f0d-115">已成功</span><span class="sxs-lookup"><span data-stu-id="d1f0d-115">successfully</span></span>|  
|<span data-ttu-id="d1f0d-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d1f0d-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d1f0d-117">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="d1f0d-117">The call timed out.</span></span>|  
|<span data-ttu-id="d1f0d-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d1f0d-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d1f0d-119">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="d1f0d-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d1f0d-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d1f0d-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d1f0d-121">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="d1f0d-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d1f0d-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d1f0d-122">E_FAIL</span></span>|<span data-ttu-id="d1f0d-123">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="d1f0d-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d1f0d-124">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="d1f0d-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d1f0d-125">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d1f0d-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1f0d-126">備註</span><span class="sxs-lookup"><span data-stu-id="d1f0d-126">Remarks</span></span>  
 <span data-ttu-id="d1f0d-127">CLR 可以回收之前建立`ICLRTask`避免重複建立新的執行個體，每次需要新的工作負載的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d1f0d-127">The CLR can recycle previously created `ICLRTask` instances to avoid the overhead of repeatedly creating new instances every time it needs a fresh task.</span></span> <span data-ttu-id="d1f0d-128">主應用程式啟用這項功能，藉由呼叫`ICLRTask::Reset`而非[iclrtask:: Exittask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md)何時已完成工作。</span><span class="sxs-lookup"><span data-stu-id="d1f0d-128">The host enables this feature by calling `ICLRTask::Reset` instead of [ICLRTask::ExitTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) when it has completed a task.</span></span> <span data-ttu-id="d1f0d-129">下列清單摘要說明一般生命週期的`ICLRTask`執行個體：</span><span class="sxs-lookup"><span data-stu-id="d1f0d-129">The following list summarizes the normal life cycle of an `ICLRTask` instance:</span></span>  
  
1.  <span data-ttu-id="d1f0d-130">執行階段建立新`ICLRTask`執行個體。</span><span class="sxs-lookup"><span data-stu-id="d1f0d-130">The runtime creates a new `ICLRTask` instance.</span></span>  
  
2.  <span data-ttu-id="d1f0d-131">執行階段會呼叫[ihosttaskmanager:: Getcurrenttask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md)來取得目前的主控件工作的參考。</span><span class="sxs-lookup"><span data-stu-id="d1f0d-131">The runtime calls [IHostTaskManager::GetCurrentTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) to get a reference to the current host task.</span></span>  
  
3.  <span data-ttu-id="d1f0d-132">執行階段會呼叫[ihosttask:: Setclrtask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)主應用程式工作相關聯的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="d1f0d-132">The runtime calls [IHostTask::SetCLRTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) to associate the new instance with the host task.</span></span>  
  
4.  <span data-ttu-id="d1f0d-133">工作執行，並完成。</span><span class="sxs-lookup"><span data-stu-id="d1f0d-133">The task executes and completes.</span></span>  
  
5.  <span data-ttu-id="d1f0d-134">主機會終結工作，藉由呼叫`ICLRTask::ExitTask`。</span><span class="sxs-lookup"><span data-stu-id="d1f0d-134">The host destroys the task by calling `ICLRTask::ExitTask`.</span></span>  
  
 <span data-ttu-id="d1f0d-135">`Reset` 改變此案例中的有兩種。</span><span class="sxs-lookup"><span data-stu-id="d1f0d-135">`Reset` alters this scenario in two ways.</span></span> <span data-ttu-id="d1f0d-136">在步驟 5，主機會呼叫上述`Reset`重設為初始狀態的工作，然後以減少`ICLRTask`與其關聯的執行個體[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)執行個體。</span><span class="sxs-lookup"><span data-stu-id="d1f0d-136">In step 5 above, the host calls `Reset` to reset the task to a clean state, and then decouples the `ICLRTask` instance from its associated [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span> <span data-ttu-id="d1f0d-137">如有需要，主應用程式也可以快取`IHostTask`供重複使用的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d1f0d-137">If desired, the host can also cache the `IHostTask` instance for reuse.</span></span> <span data-ttu-id="d1f0d-138">在步驟 1 所述，執行階段提取回收`ICLRTask`從快取，而不是建立新的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d1f0d-138">In step 1 above, the runtime pulls a recycled `ICLRTask` from the cache instead of creating a new instance.</span></span>  
  
 <span data-ttu-id="d1f0d-139">也在主應用程式也有可重複使用的背景工作的工作集區時，適用於這種方法。</span><span class="sxs-lookup"><span data-stu-id="d1f0d-139">This approach works well when the host also has a pool of reusable worker tasks.</span></span> <span data-ttu-id="d1f0d-140">當主應用程式會終結的其中一個其`IHostTask`執行個體，它會終結對應`ICLRTask`藉由呼叫`ExitTask`。</span><span class="sxs-lookup"><span data-stu-id="d1f0d-140">When the host destroys one of its `IHostTask` instances, it destroys the corresponding `ICLRTask` by calling `ExitTask`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1f0d-141">需求</span><span class="sxs-lookup"><span data-stu-id="d1f0d-141">Requirements</span></span>  
 <span data-ttu-id="d1f0d-142">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d1f0d-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1f0d-143">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d1f0d-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d1f0d-144">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d1f0d-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d1f0d-145">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1f0d-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1f0d-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1f0d-146">See also</span></span>
- [<span data-ttu-id="d1f0d-147">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="d1f0d-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="d1f0d-148">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="d1f0d-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="d1f0d-149">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="d1f0d-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="d1f0d-150">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="d1f0d-150">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
