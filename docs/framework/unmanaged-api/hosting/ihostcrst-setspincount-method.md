---
title: IHostCrst::SetSpinCount 方法
ms.date: 03/30/2017
api_name:
- IHostCrst.SetSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::SetSpinCount
helpviewer_keywords:
- IHostCrst::SetSpinCount method [.NET Framework hosting]
- SetSpinCount method [.NET Framework hosting]
ms.assetid: 863fc8ce-9b8a-477e-8dd8-75c8544bb43a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ca17a6814b56c0fe781cfb28a35a576f02f1943
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090572"
---
# <a name="ihostcrstsetspincount-method"></a><span data-ttu-id="5416d-102">IHostCrst::SetSpinCount 方法</span><span class="sxs-lookup"><span data-stu-id="5416d-102">IHostCrst::SetSpinCount Method</span></span>
<span data-ttu-id="5416d-103">設定目前的微調計數[IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)執行個體。</span><span class="sxs-lookup"><span data-stu-id="5416d-103">Sets the spin count for the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5416d-104">語法</span><span class="sxs-lookup"><span data-stu-id="5416d-104">Syntax</span></span>  
  
```  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5416d-105">參數</span><span class="sxs-lookup"><span data-stu-id="5416d-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="5416d-106">[in]新的微調計數，目前`IHostCrst`執行個體。</span><span class="sxs-lookup"><span data-stu-id="5416d-106">[in] The new spin count for the current `IHostCrst` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5416d-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="5416d-107">Return Value</span></span>  
  
|<span data-ttu-id="5416d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5416d-108">HRESULT</span></span>|<span data-ttu-id="5416d-109">描述</span><span class="sxs-lookup"><span data-stu-id="5416d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5416d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5416d-110">S_OK</span></span>|`SetSpinCount` <span data-ttu-id="5416d-111">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="5416d-111">returned successfully.</span></span>|  
|<span data-ttu-id="5416d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5416d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5416d-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="5416d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5416d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5416d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5416d-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="5416d-115">The call timed out.</span></span>|  
|<span data-ttu-id="5416d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5416d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5416d-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="5416d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5416d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5416d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5416d-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="5416d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5416d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5416d-120">E_FAIL</span></span>|<span data-ttu-id="5416d-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="5416d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5416d-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="5416d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5416d-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="5416d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5416d-124">備註</span><span class="sxs-lookup"><span data-stu-id="5416d-124">Remarks</span></span>  
 <span data-ttu-id="5416d-125">在多處理器系統上，如果重要區段表示由目前`IHostCrst`執行個體無法使用，呼叫執行緒會旋轉`dwSpinCount`時間，然後再呼叫[ihostsemaphore:: Wait](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md)相關聯的號誌上使用重要區段。</span><span class="sxs-lookup"><span data-stu-id="5416d-125">On multi-processor systems, if the critical section represented by the current `IHostCrst` instance is unavailable, a calling thread spins `dwSpinCount` times before calling [IHostSemaphore::Wait](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md) on a semaphore associated with the critical section.</span></span> <span data-ttu-id="5416d-126">重要區段中變成可用時微調作業，如果呼叫執行緒會避免等候作業。</span><span class="sxs-lookup"><span data-stu-id="5416d-126">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span>  
  
 <span data-ttu-id="5416d-127">使用方式`dwSpinCount`等同於在 Win32 中相同名稱的參數的使用方式`InitializeCriticalSectionAndSpinCount`函式。</span><span class="sxs-lookup"><span data-stu-id="5416d-127">The usage of `dwSpinCount` is identical to the usage of the parameter of the same name in the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5416d-128">需求</span><span class="sxs-lookup"><span data-stu-id="5416d-128">Requirements</span></span>  
 <span data-ttu-id="5416d-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5416d-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5416d-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5416d-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5416d-131">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5416d-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="5416d-132">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="5416d-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5416d-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5416d-133">See also</span></span>

- [<span data-ttu-id="5416d-134">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="5416d-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="5416d-135">IHostCrst 介面</span><span class="sxs-lookup"><span data-stu-id="5416d-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="5416d-136">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="5416d-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
