---
title: "IHostCrst::SetSpinCount 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostCrst.SetSpinCount
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostCrst::SetSpinCount
helpviewer_keywords:
- IHostCrst::SetSpinCount method [.NET Framework hosting]
- SetSpinCount method [.NET Framework hosting]
ms.assetid: 863fc8ce-9b8a-477e-8dd8-75c8544bb43a
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 19172c6d498e5066c102c642105d78d10b26212c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ihostcrstsetspincount-method"></a><span data-ttu-id="d75be-102">IHostCrst::SetSpinCount 方法</span><span class="sxs-lookup"><span data-stu-id="d75be-102">IHostCrst::SetSpinCount Method</span></span>
<span data-ttu-id="d75be-103">設定目前的微調計數[IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)執行個體。</span><span class="sxs-lookup"><span data-stu-id="d75be-103">Sets the spin count for the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d75be-104">語法</span><span class="sxs-lookup"><span data-stu-id="d75be-104">Syntax</span></span>  
  
```  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d75be-105">參數</span><span class="sxs-lookup"><span data-stu-id="d75be-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="d75be-106">[in]新的微調計數，目前`IHostCrst`執行個體。</span><span class="sxs-lookup"><span data-stu-id="d75be-106">[in] The new spin count for the current `IHostCrst` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d75be-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="d75be-107">Return Value</span></span>  
  
|<span data-ttu-id="d75be-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d75be-108">HRESULT</span></span>|<span data-ttu-id="d75be-109">描述</span><span class="sxs-lookup"><span data-stu-id="d75be-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d75be-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d75be-110">S_OK</span></span>|<span data-ttu-id="d75be-111">`SetSpinCount`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="d75be-111">`SetSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="d75be-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d75be-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d75be-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="d75be-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d75be-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d75be-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d75be-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="d75be-115">The call timed out.</span></span>|  
|<span data-ttu-id="d75be-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d75be-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d75be-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="d75be-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d75be-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d75be-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d75be-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="d75be-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d75be-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d75be-120">E_FAIL</span></span>|<span data-ttu-id="d75be-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="d75be-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d75be-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="d75be-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d75be-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d75be-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d75be-124">備註</span><span class="sxs-lookup"><span data-stu-id="d75be-124">Remarks</span></span>  
 <span data-ttu-id="d75be-125">在多處理器系統中，如果關鍵區段以表示由目前`IHostCrst`執行個體無法使用，請呼叫執行緒旋轉`dwSpinCount`之前呼叫的時間點[ihostsemaphore:: Wait](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md)相關聯的號誌上與關鍵區段。</span><span class="sxs-lookup"><span data-stu-id="d75be-125">On multi-processor systems, if the critical section represented by the current `IHostCrst` instance is unavailable, a calling thread spins `dwSpinCount` times before calling [IHostSemaphore::Wait](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md) on a semaphore associated with the critical section.</span></span> <span data-ttu-id="d75be-126">關鍵區段會變成可用微調作業期間，如果呼叫的執行緒可避免等候作業。</span><span class="sxs-lookup"><span data-stu-id="d75be-126">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span>  
  
 <span data-ttu-id="d75be-127">使用`dwSpinCount`等同於在 Win32 中相同名稱的參數的使用方式`InitializeCriticalSectionAndSpinCount`函式。</span><span class="sxs-lookup"><span data-stu-id="d75be-127">The usage of `dwSpinCount` is identical to the usage of the parameter of the same name in the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d75be-128">需求</span><span class="sxs-lookup"><span data-stu-id="d75be-128">Requirements</span></span>  
 <span data-ttu-id="d75be-129">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d75be-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d75be-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d75be-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d75be-131">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d75be-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d75be-132">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d75be-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d75be-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d75be-133">See Also</span></span>  
 [<span data-ttu-id="d75be-134">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="d75be-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="d75be-135">IHostCrst 介面</span><span class="sxs-lookup"><span data-stu-id="d75be-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="d75be-136">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="d75be-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
