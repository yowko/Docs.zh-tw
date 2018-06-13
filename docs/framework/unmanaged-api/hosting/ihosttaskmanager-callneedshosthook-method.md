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
ms.openlocfilehash: 983cad5ed87d0666ed71a805a3b3f7a3c7e7c091
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444300"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a><span data-ttu-id="d608e-102">IHostTaskManager::CallNeedsHostHook 方法</span><span class="sxs-lookup"><span data-stu-id="d608e-102">IHostTaskManager::CallNeedsHostHook Method</span></span>
<span data-ttu-id="d608e-103">可讓主應用程式指定 common language runtime (CLR) 是否可內嵌指定呼叫 unmanaged 函式。</span><span class="sxs-lookup"><span data-stu-id="d608e-103">Enables the host to specify whether the common language runtime (CLR) can inline the specified call to an unmanaged function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d608e-104">語法</span><span class="sxs-lookup"><span data-stu-id="d608e-104">Syntax</span></span>  
  
```  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,   
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d608e-105">參數</span><span class="sxs-lookup"><span data-stu-id="d608e-105">Parameters</span></span>  
 `target`  
 <span data-ttu-id="d608e-106">[in]要呼叫 unmanaged 函式的對應的可攜式執行檔 (PE) 檔案中的位址。</span><span class="sxs-lookup"><span data-stu-id="d608e-106">[in] The address within the mapped portable executable (PE) file of the unmanaged function that is to be called.</span></span>  
  
 `pbCallNeedsHostHook`  
 <span data-ttu-id="d608e-107">[out]布林值，表示主機是否需要呼叫連結指標。</span><span class="sxs-lookup"><span data-stu-id="d608e-107">[out] A pointer to a Boolean value that indicates whether the host requires the call to be hooked.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d608e-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="d608e-108">Return Value</span></span>  
  
|<span data-ttu-id="d608e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d608e-109">HRESULT</span></span>|<span data-ttu-id="d608e-110">描述</span><span class="sxs-lookup"><span data-stu-id="d608e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d608e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d608e-111">S_OK</span></span>|<span data-ttu-id="d608e-112">`CallNeedsHostHook` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="d608e-112">`CallNeedsHostHook` returned successfully.</span></span>|  
|<span data-ttu-id="d608e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d608e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d608e-114">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="d608e-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d608e-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d608e-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d608e-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="d608e-116">The call timed out.</span></span>|  
|<span data-ttu-id="d608e-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d608e-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d608e-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="d608e-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d608e-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d608e-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d608e-120">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="d608e-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d608e-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d608e-121">E_FAIL</span></span>|<span data-ttu-id="d608e-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="d608e-122">An unknown catastrophic failure has occurred.</span></span> <span data-ttu-id="d608e-123">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="d608e-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d608e-124">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d608e-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d608e-125">備註</span><span class="sxs-lookup"><span data-stu-id="d608e-125">Remarks</span></span>  
 <span data-ttu-id="d608e-126">若要協助最佳化程式碼執行，CLR 就會執行分析的每個平台叫用呼叫期間編譯，以判斷是否可以內嵌呼叫。</span><span class="sxs-lookup"><span data-stu-id="d608e-126">To help optimize code execution, the CLR performs an analysis of each platform invoke call during compilation to determine whether the call can be inlined.</span></span> <span data-ttu-id="d608e-127">`CallNeedsHostHook` 可讓主應用程式需要被攔截的 unmanaged 函式呼叫，以覆寫該決策。</span><span class="sxs-lookup"><span data-stu-id="d608e-127">`CallNeedsHostHook` enables the host to override that decision by requiring that a call to an unmanaged function be hooked.</span></span> <span data-ttu-id="d608e-128">如果主機需要攔截程序，執行階段並不會內嵌呼叫。</span><span class="sxs-lookup"><span data-stu-id="d608e-128">If the host requires a hook, the runtime does not inline the call.</span></span>  
  
 <span data-ttu-id="d608e-129">主機通常需要攔截程序必須調整浮點狀態，或在收到呼叫會進入主應用程式無法追蹤記憶體或任何採用的鎖定的執行階段的要求，其中某一狀態的通知。</span><span class="sxs-lookup"><span data-stu-id="d608e-129">The host typically would require a hook where it must adjust a floating-point state, or upon receiving notification that a call is entering a state where the host cannot track the runtime's requests for memory or any locks taken.</span></span> <span data-ttu-id="d608e-130">當主應用程式需要呼叫被攔截時，執行階段會使用呼叫通知 managed 程式碼往來的轉換主機[EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)， [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)， [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)，和[ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)。</span><span class="sxs-lookup"><span data-stu-id="d608e-130">When the host requires that the call be hooked, the runtime notifies the host of transitions to and from managed code by using calls to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), and [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d608e-131">需求</span><span class="sxs-lookup"><span data-stu-id="d608e-131">Requirements</span></span>  
 <span data-ttu-id="d608e-132">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d608e-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d608e-133">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d608e-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d608e-134">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d608e-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d608e-135">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d608e-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d608e-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d608e-136">See Also</span></span>  
 [<span data-ttu-id="d608e-137">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="d608e-137">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="d608e-138">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="d608e-138">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="d608e-139">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="d608e-139">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="d608e-140">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="d608e-140">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
