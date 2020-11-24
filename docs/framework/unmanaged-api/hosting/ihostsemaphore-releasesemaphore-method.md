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
ms.openlocfilehash: 660062fb69bb8fe0a06bbca9046d65175fb72f9a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683026"
---
# <a name="ihostsemaphorereleasesemaphore-method"></a><span data-ttu-id="b53b1-102">IHostSemaphore::ReleaseSemaphore 方法</span><span class="sxs-lookup"><span data-stu-id="b53b1-102">IHostSemaphore::ReleaseSemaphore Method</span></span>

<span data-ttu-id="b53b1-103">依指定的數量增加目前 [IHostSemaphore](ihostsemaphore-interface.md) 實例的計數。</span><span class="sxs-lookup"><span data-stu-id="b53b1-103">Increases the count of the current [IHostSemaphore](ihostsemaphore-interface.md) instance by the specified amount.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b53b1-104">語法</span><span class="sxs-lookup"><span data-stu-id="b53b1-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseSemaphore (  
    [in]  LONG  lReleaseCount,  
    [out] LONG  *lpPreviousCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b53b1-105">參數</span><span class="sxs-lookup"><span data-stu-id="b53b1-105">Parameters</span></span>  

 `lReleaseCount`  
 <span data-ttu-id="b53b1-106">在要增加目前實例之計數的量 `IHostSemaphore` 。</span><span class="sxs-lookup"><span data-stu-id="b53b1-106">[in] The amount by which to increase the count of the current `IHostSemaphore` instance.</span></span> <span data-ttu-id="b53b1-107">此數量必須大於零。</span><span class="sxs-lookup"><span data-stu-id="b53b1-107">This amount must be greater than zero.</span></span>  
  
 `lpPreviousCount`  
 <span data-ttu-id="b53b1-108">擴展先前計數的指標，如果呼叫端不需要先前的計數，則為 null。</span><span class="sxs-lookup"><span data-stu-id="b53b1-108">[out] A pointer to the previous count, or null if the caller does not require the previous count.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b53b1-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="b53b1-109">Return Value</span></span>  
  
|<span data-ttu-id="b53b1-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b53b1-110">HRESULT</span></span>|<span data-ttu-id="b53b1-111">描述</span><span class="sxs-lookup"><span data-stu-id="b53b1-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b53b1-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b53b1-112">S_OK</span></span>|<span data-ttu-id="b53b1-113">`ReleaseSemaphore` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="b53b1-113">`ReleaseSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="b53b1-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b53b1-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b53b1-115">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="b53b1-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b53b1-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b53b1-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b53b1-117">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="b53b1-117">The call timed out.</span></span>|  
|<span data-ttu-id="b53b1-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b53b1-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b53b1-119">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="b53b1-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b53b1-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b53b1-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b53b1-121">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="b53b1-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b53b1-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b53b1-122">E_FAIL</span></span>|<span data-ttu-id="b53b1-123">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="b53b1-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b53b1-124">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="b53b1-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b53b1-125">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b53b1-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b53b1-126">備註</span><span class="sxs-lookup"><span data-stu-id="b53b1-126">Remarks</span></span>  

 <span data-ttu-id="b53b1-127">CLR 通常會呼叫， `ReleaseSemaphore` 以通知主機它已完成使用資源，並傳遞值1給 `lReleaseCount` 參數。</span><span class="sxs-lookup"><span data-stu-id="b53b1-127">The CLR typically calls `ReleaseSemaphore` to notify the host that it has finished using a resource, passing a value of 1 for the `lReleaseCount` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b53b1-128">需求</span><span class="sxs-lookup"><span data-stu-id="b53b1-128">Requirements</span></span>  

 <span data-ttu-id="b53b1-129">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b53b1-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b53b1-130">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b53b1-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b53b1-131">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="b53b1-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b53b1-132">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b53b1-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b53b1-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b53b1-133">See also</span></span>

- [<span data-ttu-id="b53b1-134">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="b53b1-134">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="b53b1-135">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="b53b1-135">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="b53b1-136">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="b53b1-136">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="b53b1-137">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="b53b1-137">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="b53b1-138">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="b53b1-138">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
