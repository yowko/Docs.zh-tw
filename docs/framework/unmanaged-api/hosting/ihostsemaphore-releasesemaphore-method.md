---
title: IHostSemaphore::ReleaseSemaphore 方法
ms.date: 03/30/2017
api_name:
- IHostSemaphore.ReleaseSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore::ReleaseSemaphore
helpviewer_keywords:
- ReleaseSemaphore method [.NET Framework hosting]
- IHostSemaphore::ReleaseSemaphore method [.NET Framework hosting]
ms.assetid: a343d197-979a-4ac6-ab8c-cb8a05f3120e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24ec56345a5b48540d2451769f739a236a85e47b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100609"
---
# <a name="ihostsemaphorereleasesemaphore-method"></a><span data-ttu-id="3f851-102">IHostSemaphore::ReleaseSemaphore 方法</span><span class="sxs-lookup"><span data-stu-id="3f851-102">IHostSemaphore::ReleaseSemaphore Method</span></span>
<span data-ttu-id="3f851-103">增加的目前計數[IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)指定數量的執行個體。</span><span class="sxs-lookup"><span data-stu-id="3f851-103">Increases the count of the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance by the specified amount.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f851-104">語法</span><span class="sxs-lookup"><span data-stu-id="3f851-104">Syntax</span></span>  
  
```  
HRESULT ReleaseSemaphore (  
    [in]  LONG  lReleaseCount,  
    [out] LONG  *lpPreviousCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f851-105">參數</span><span class="sxs-lookup"><span data-stu-id="3f851-105">Parameters</span></span>  
 `lReleaseCount`  
 <span data-ttu-id="3f851-106">[in]用來在目前的計數增加數量`IHostSemaphore`執行個體。</span><span class="sxs-lookup"><span data-stu-id="3f851-106">[in] The amount by which to increase the count of the current `IHostSemaphore` instance.</span></span> <span data-ttu-id="3f851-107">這個數量必須小於或等於零。</span><span class="sxs-lookup"><span data-stu-id="3f851-107">This amount must be greater than zero.</span></span>  
  
 `lpPreviousCount`  
 <span data-ttu-id="3f851-108">[out]前次計數或如果呼叫端不需要上一個計數則為 null 指標。</span><span class="sxs-lookup"><span data-stu-id="3f851-108">[out] A pointer to the previous count, or null if the caller does not require the previous count.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f851-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="3f851-109">Return Value</span></span>  
  
|<span data-ttu-id="3f851-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3f851-110">HRESULT</span></span>|<span data-ttu-id="3f851-111">描述</span><span class="sxs-lookup"><span data-stu-id="3f851-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3f851-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="3f851-112">S_OK</span></span>|`ReleaseSemaphore` <span data-ttu-id="3f851-113">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="3f851-113">returned successfully.</span></span>|  
|<span data-ttu-id="3f851-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3f851-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3f851-115">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="3f851-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3f851-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3f851-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3f851-117">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="3f851-117">The call timed out.</span></span>|  
|<span data-ttu-id="3f851-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3f851-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3f851-119">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="3f851-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3f851-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3f851-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3f851-121">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="3f851-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3f851-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3f851-122">E_FAIL</span></span>|<span data-ttu-id="3f851-123">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="3f851-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3f851-124">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="3f851-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3f851-125">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="3f851-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f851-126">備註</span><span class="sxs-lookup"><span data-stu-id="3f851-126">Remarks</span></span>  
 <span data-ttu-id="3f851-127">CLR 通常會呼叫`ReleaseSemaphore`以通知主機發出它已完成使用資源時，傳遞的值為 1`lReleaseCount`參數。</span><span class="sxs-lookup"><span data-stu-id="3f851-127">The CLR typically calls `ReleaseSemaphore` to notify the host that it has finished using a resource, passing a value of 1 for the `lReleaseCount` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f851-128">需求</span><span class="sxs-lookup"><span data-stu-id="3f851-128">Requirements</span></span>  
 <span data-ttu-id="3f851-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3f851-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f851-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3f851-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3f851-131">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3f851-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="3f851-132">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="3f851-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3f851-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f851-133">See also</span></span>

- [<span data-ttu-id="3f851-134">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="3f851-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="3f851-135">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="3f851-135">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="3f851-136">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="3f851-136">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="3f851-137">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="3f851-137">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="3f851-138">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="3f851-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
