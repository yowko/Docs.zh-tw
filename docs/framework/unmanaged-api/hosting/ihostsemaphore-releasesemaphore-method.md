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
ms.openlocfilehash: aa67aabbe8a7a47a9b3036f508e2f8bb6082c3e0
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803549"
---
# <a name="ihostsemaphorereleasesemaphore-method"></a><span data-ttu-id="0123c-102">IHostSemaphore::ReleaseSemaphore 方法</span><span class="sxs-lookup"><span data-stu-id="0123c-102">IHostSemaphore::ReleaseSemaphore Method</span></span>
<span data-ttu-id="0123c-103">依指定的數量增加目前[IHostSemaphore](ihostsemaphore-interface.md)實例的計數。</span><span class="sxs-lookup"><span data-stu-id="0123c-103">Increases the count of the current [IHostSemaphore](ihostsemaphore-interface.md) instance by the specified amount.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0123c-104">語法</span><span class="sxs-lookup"><span data-stu-id="0123c-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseSemaphore (  
    [in]  LONG  lReleaseCount,  
    [out] LONG  *lpPreviousCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0123c-105">參數</span><span class="sxs-lookup"><span data-stu-id="0123c-105">Parameters</span></span>  
 `lReleaseCount`  
 <span data-ttu-id="0123c-106">在要增加目前實例計數的數量 `IHostSemaphore` 。</span><span class="sxs-lookup"><span data-stu-id="0123c-106">[in] The amount by which to increase the count of the current `IHostSemaphore` instance.</span></span> <span data-ttu-id="0123c-107">此數量必須大於零。</span><span class="sxs-lookup"><span data-stu-id="0123c-107">This amount must be greater than zero.</span></span>  
  
 `lpPreviousCount`  
 <span data-ttu-id="0123c-108">脫銷先前計數的指標，如果呼叫端不需要先前的計數，則為 null。</span><span class="sxs-lookup"><span data-stu-id="0123c-108">[out] A pointer to the previous count, or null if the caller does not require the previous count.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0123c-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="0123c-109">Return Value</span></span>  
  
|<span data-ttu-id="0123c-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0123c-110">HRESULT</span></span>|<span data-ttu-id="0123c-111">描述</span><span class="sxs-lookup"><span data-stu-id="0123c-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0123c-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="0123c-112">S_OK</span></span>|<span data-ttu-id="0123c-113">`ReleaseSemaphore`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="0123c-113">`ReleaseSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="0123c-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0123c-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0123c-115">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="0123c-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0123c-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0123c-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0123c-117">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="0123c-117">The call timed out.</span></span>|  
|<span data-ttu-id="0123c-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0123c-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0123c-119">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="0123c-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0123c-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0123c-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0123c-121">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="0123c-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0123c-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0123c-122">E_FAIL</span></span>|<span data-ttu-id="0123c-123">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="0123c-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0123c-124">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="0123c-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0123c-125">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="0123c-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0123c-126">備註</span><span class="sxs-lookup"><span data-stu-id="0123c-126">Remarks</span></span>  
 <span data-ttu-id="0123c-127">CLR 通常會呼叫， `ReleaseSemaphore` 以通知主機其已使用資源完成，並為參數傳遞1的值 `lReleaseCount` 。</span><span class="sxs-lookup"><span data-stu-id="0123c-127">The CLR typically calls `ReleaseSemaphore` to notify the host that it has finished using a resource, passing a value of 1 for the `lReleaseCount` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0123c-128">規格需求</span><span class="sxs-lookup"><span data-stu-id="0123c-128">Requirements</span></span>  
 <span data-ttu-id="0123c-129">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0123c-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0123c-130">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="0123c-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0123c-131">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0123c-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0123c-132">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0123c-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0123c-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0123c-133">See also</span></span>

- [<span data-ttu-id="0123c-134">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="0123c-134">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="0123c-135">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="0123c-135">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="0123c-136">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="0123c-136">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="0123c-137">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="0123c-137">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="0123c-138">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="0123c-138">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
