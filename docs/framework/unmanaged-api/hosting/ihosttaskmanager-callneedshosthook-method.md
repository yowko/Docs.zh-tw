---
title: IHostTaskManager::CallNeedsHostHook 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CallNeedsHostHook
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CallNeedsHostHook
helpviewer_keywords:
- CallNeedsHostHook method [.NET Framework hosting]
- IHostTaskManager::CallNeedsHostHook method [.NET Framework hosting]
ms.assetid: b60f1f59-9825-4b57-961f-d2979518e6a7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb91c5dfbe5c83e08d786043d7e4732fa19e53db
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566778"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a><span data-ttu-id="201d4-102">IHostTaskManager::CallNeedsHostHook 方法</span><span class="sxs-lookup"><span data-stu-id="201d4-102">IHostTaskManager::CallNeedsHostHook Method</span></span>
<span data-ttu-id="201d4-103">可讓主應用程式指定 common language runtime (CLR) 是否可內嵌指定呼叫 unmanaged 函式。</span><span class="sxs-lookup"><span data-stu-id="201d4-103">Enables the host to specify whether the common language runtime (CLR) can inline the specified call to an unmanaged function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="201d4-104">語法</span><span class="sxs-lookup"><span data-stu-id="201d4-104">Syntax</span></span>  
  
```  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,   
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="201d4-105">參數</span><span class="sxs-lookup"><span data-stu-id="201d4-105">Parameters</span></span>  
 `target`  
 <span data-ttu-id="201d4-106">[in]要呼叫 unmanaged 函式的對應的可攜式執行檔 (PE) 檔案中的位址。</span><span class="sxs-lookup"><span data-stu-id="201d4-106">[in] The address within the mapped portable executable (PE) file of the unmanaged function that is to be called.</span></span>  
  
 `pbCallNeedsHostHook`  
 <span data-ttu-id="201d4-107">[out]布林值，指出主應用程式是否需要呼叫連結指標。</span><span class="sxs-lookup"><span data-stu-id="201d4-107">[out] A pointer to a Boolean value that indicates whether the host requires the call to be hooked.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="201d4-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="201d4-108">Return Value</span></span>  
  
|<span data-ttu-id="201d4-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="201d4-109">HRESULT</span></span>|<span data-ttu-id="201d4-110">描述</span><span class="sxs-lookup"><span data-stu-id="201d4-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="201d4-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="201d4-111">S_OK</span></span>|<span data-ttu-id="201d4-112">`CallNeedsHostHook` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="201d4-112">`CallNeedsHostHook` returned successfully.</span></span>|  
|<span data-ttu-id="201d4-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="201d4-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="201d4-114">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="201d4-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="201d4-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="201d4-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="201d4-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="201d4-116">The call timed out.</span></span>|  
|<span data-ttu-id="201d4-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="201d4-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="201d4-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="201d4-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="201d4-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="201d4-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="201d4-120">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="201d4-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="201d4-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="201d4-121">E_FAIL</span></span>|<span data-ttu-id="201d4-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="201d4-122">An unknown catastrophic failure has occurred.</span></span> <span data-ttu-id="201d4-123">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="201d4-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="201d4-124">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="201d4-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="201d4-125">備註</span><span class="sxs-lookup"><span data-stu-id="201d4-125">Remarks</span></span>  
 <span data-ttu-id="201d4-126">為了協助最佳化程式碼執行，CLR 會分析每個平台叫用來判斷呼叫是否可以內嵌在編譯期間的呼叫。</span><span class="sxs-lookup"><span data-stu-id="201d4-126">To help optimize code execution, the CLR performs an analysis of each platform invoke call during compilation to determine whether the call can be inlined.</span></span> <span data-ttu-id="201d4-127">`CallNeedsHostHook` 可讓主應用程式需要連接至 unmanaged 函式的呼叫，以覆寫這項決定。</span><span class="sxs-lookup"><span data-stu-id="201d4-127">`CallNeedsHostHook` enables the host to override that decision by requiring that a call to an unmanaged function be hooked.</span></span> <span data-ttu-id="201d4-128">如果主機需要攔截程序，執行階段會不會內嵌呼叫。</span><span class="sxs-lookup"><span data-stu-id="201d4-128">If the host requires a hook, the runtime does not inline the call.</span></span>  
  
 <span data-ttu-id="201d4-129">主機通常需要攔截程序必須調整為浮點數的狀態，或在收到呼叫進入其中主應用程式無法追蹤記憶體或任何鎖定的執行階段的要求狀態的通知。</span><span class="sxs-lookup"><span data-stu-id="201d4-129">The host typically would require a hook where it must adjust a floating-point state, or upon receiving notification that a call is entering a state where the host cannot track the runtime's requests for memory or any locks taken.</span></span> <span data-ttu-id="201d4-130">當主應用程式需要呼叫被攔截時，執行階段主應用程式的轉換與 managed 程式碼藉由呼叫[EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)， [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)， [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)，並[ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)。</span><span class="sxs-lookup"><span data-stu-id="201d4-130">When the host requires that the call be hooked, the runtime notifies the host of transitions to and from managed code by using calls to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), and [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="201d4-131">需求</span><span class="sxs-lookup"><span data-stu-id="201d4-131">Requirements</span></span>  
 <span data-ttu-id="201d4-132">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="201d4-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="201d4-133">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="201d4-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="201d4-134">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="201d4-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="201d4-135">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="201d4-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="201d4-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="201d4-136">See also</span></span>
- [<span data-ttu-id="201d4-137">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="201d4-137">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="201d4-138">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="201d4-138">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="201d4-139">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="201d4-139">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="201d4-140">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="201d4-140">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
