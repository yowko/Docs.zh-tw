---
title: "ICLRTask::Reset 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.Reset
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::Reset
helpviewer_keywords:
- ICLRTask::Reset method [.NET Framework hosting]
- Reset method, ICLRTask interface [.NET Framework hosting]
ms.assetid: 1bfb5d3a-0ffd-4bb4-9bf6-aec00cb675b7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7c50dc4770665e2b049f41a105b58231221b8e9c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskreset-method"></a><span data-ttu-id="6b73b-102">ICLRTask::Reset 方法</span><span class="sxs-lookup"><span data-stu-id="6b73b-102">ICLRTask::Reset Method</span></span>
<span data-ttu-id="6b73b-103">通知主機已完成工作，並啟用 CLR，若要重複使用目前的 common language runtime (CLR) [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)來代表另一項工作的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6b73b-103">Informs the common language runtime (CLR) that the host has completed a task, and enables the CLR to reuse the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance to represent another task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b73b-104">語法</span><span class="sxs-lookup"><span data-stu-id="6b73b-104">Syntax</span></span>  
  
```  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b73b-105">參數</span><span class="sxs-lookup"><span data-stu-id="6b73b-105">Parameters</span></span>  
 `fFull`  
 <span data-ttu-id="6b73b-106">[in]`true`，如果執行階段應該重設所有與執行緒相關靜態值除了與目前的安全性和地區設定資訊`ICLRTask`執行個體; 否則`false`。</span><span class="sxs-lookup"><span data-stu-id="6b73b-106">[in] `true`, if the runtime should reset all thread-related static values in addition to the security and locale information related to the current `ICLRTask` instance; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="6b73b-107">如果值為`true`，執行階段會重設使用儲存的資料<xref:System.Threading.Thread.AllocateDataSlot%2A>或<xref:System.Threading.Thread.AllocateNamedDataSlot%2A>。</span><span class="sxs-lookup"><span data-stu-id="6b73b-107">If the value is `true`, the runtime resets data that was stored using <xref:System.Threading.Thread.AllocateDataSlot%2A> or <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b73b-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="6b73b-108">Return Value</span></span>  
  
|<span data-ttu-id="6b73b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6b73b-109">HRESULT</span></span>|<span data-ttu-id="6b73b-110">描述</span><span class="sxs-lookup"><span data-stu-id="6b73b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6b73b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6b73b-111">S_OK</span></span>|<span data-ttu-id="6b73b-112">`Reset`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="6b73b-112">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="6b73b-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6b73b-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6b73b-114">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="6b73b-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="6b73b-115">已成功</span><span class="sxs-lookup"><span data-stu-id="6b73b-115">successfully</span></span>|  
|<span data-ttu-id="6b73b-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6b73b-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6b73b-117">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="6b73b-117">The call timed out.</span></span>|  
|<span data-ttu-id="6b73b-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6b73b-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6b73b-119">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="6b73b-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6b73b-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6b73b-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6b73b-121">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="6b73b-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6b73b-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6b73b-122">E_FAIL</span></span>|<span data-ttu-id="6b73b-123">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="6b73b-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6b73b-124">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="6b73b-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6b73b-125">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="6b73b-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b73b-126">備註</span><span class="sxs-lookup"><span data-stu-id="6b73b-126">Remarks</span></span>  
 <span data-ttu-id="6b73b-127">CLR 可以回收之前建立`ICLRTask`執行個體，以避免重複建立新的執行個體，每次需要新的工作的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="6b73b-127">The CLR can recycle previously created `ICLRTask` instances to avoid the overhead of repeatedly creating new instances every time it needs a fresh task.</span></span> <span data-ttu-id="6b73b-128">主應用程式啟用這項功能，藉由呼叫`ICLRTask::Reset`而不是[iclrtask:: Exittask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md)何時完成工作。</span><span class="sxs-lookup"><span data-stu-id="6b73b-128">The host enables this feature by calling `ICLRTask::Reset` instead of [ICLRTask::ExitTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) when it has completed a task.</span></span> <span data-ttu-id="6b73b-129">下列清單摘要說明一般生命週期的`ICLRTask`執行個體：</span><span class="sxs-lookup"><span data-stu-id="6b73b-129">The following list summarizes the normal life cycle of an `ICLRTask` instance:</span></span>  
  
1.  <span data-ttu-id="6b73b-130">執行階段建立新`ICLRTask`執行個體。</span><span class="sxs-lookup"><span data-stu-id="6b73b-130">The runtime creates a new `ICLRTask` instance.</span></span>  
  
2.  <span data-ttu-id="6b73b-131">執行階段呼叫[ihosttaskmanager:: Getcurrenttask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md)取得目前的主控件工作的參考。</span><span class="sxs-lookup"><span data-stu-id="6b73b-131">The runtime calls [IHostTaskManager::GetCurrentTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) to get a reference to the current host task.</span></span>  
  
3.  <span data-ttu-id="6b73b-132">執行階段呼叫[ihosttask:: Setclrtask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)與 「 主機 」 工作的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="6b73b-132">The runtime calls [IHostTask::SetCLRTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) to associate the new instance with the host task.</span></span>  
  
4.  <span data-ttu-id="6b73b-133">工作會執行並完成。</span><span class="sxs-lookup"><span data-stu-id="6b73b-133">The task executes and completes.</span></span>  
  
5.  <span data-ttu-id="6b73b-134">藉由呼叫主機會終結的工作`ICLRTask::ExitTask`。</span><span class="sxs-lookup"><span data-stu-id="6b73b-134">The host destroys the task by calling `ICLRTask::ExitTask`.</span></span>  
  
 <span data-ttu-id="6b73b-135">`Reset`改變此案例有兩種。</span><span class="sxs-lookup"><span data-stu-id="6b73b-135">`Reset` alters this scenario in two ways.</span></span> <span data-ttu-id="6b73b-136">在步驟 5，主機會呼叫上述`Reset`重設為初始狀態的工作，然後以減少`ICLRTask`從及其相關聯的執行個體[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)執行個體。</span><span class="sxs-lookup"><span data-stu-id="6b73b-136">In step 5 above, the host calls `Reset` to reset the task to a clean state, and then decouples the `ICLRTask` instance from its associated [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span> <span data-ttu-id="6b73b-137">如有需要，主應用程式也可以快取`IHostTask`供重複使用的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6b73b-137">If desired, the host can also cache the `IHostTask` instance for reuse.</span></span> <span data-ttu-id="6b73b-138">步驟 1 上述，以執行階段會提取回收`ICLRTask`從快取，而不是建立的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="6b73b-138">In step 1 above, the runtime pulls a recycled `ICLRTask` from the cache instead of creating a new instance.</span></span>  
  
 <span data-ttu-id="6b73b-139">這個方法適用於主機也有可重複使用的工作者工作的集區時。</span><span class="sxs-lookup"><span data-stu-id="6b73b-139">This approach works well when the host also has a pool of reusable worker tasks.</span></span> <span data-ttu-id="6b73b-140">當主機的其中一個終結其`IHostTask`執行個體，它會終結對應`ICLRTask`藉由呼叫`ExitTask`。</span><span class="sxs-lookup"><span data-stu-id="6b73b-140">When the host destroys one of its `IHostTask` instances, it destroys the corresponding `ICLRTask` by calling `ExitTask`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b73b-141">需求</span><span class="sxs-lookup"><span data-stu-id="6b73b-141">Requirements</span></span>  
 <span data-ttu-id="6b73b-142">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6b73b-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b73b-143">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6b73b-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6b73b-144">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6b73b-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b73b-145">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b73b-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b73b-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b73b-146">See Also</span></span>  
 [<span data-ttu-id="6b73b-147">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="6b73b-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="6b73b-148">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="6b73b-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="6b73b-149">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="6b73b-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="6b73b-150">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="6b73b-150">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
