---
title: "IHostSemaphore::ReleaseSemaphore 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSemaphore.ReleaseSemaphore
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSemaphore::ReleaseSemaphore
helpviewer_keywords:
- ReleaseSemaphore method [.NET Framework hosting]
- IHostSemaphore::ReleaseSemaphore method [.NET Framework hosting]
ms.assetid: a343d197-979a-4ac6-ab8c-cb8a05f3120e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 06765d019d5443730656e7f4d6745bd8ad39ee00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsemaphorereleasesemaphore-method"></a><span data-ttu-id="9c668-102">IHostSemaphore::ReleaseSemaphore 方法</span><span class="sxs-lookup"><span data-stu-id="9c668-102">IHostSemaphore::ReleaseSemaphore Method</span></span>
<span data-ttu-id="9c668-103">會在目前的計數增加[IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)執行個體，以指定的數量。</span><span class="sxs-lookup"><span data-stu-id="9c668-103">Increases the count of the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance by the specified amount.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c668-104">語法</span><span class="sxs-lookup"><span data-stu-id="9c668-104">Syntax</span></span>  
  
```  
HRESULT ReleaseSemaphore (  
    [in]  LONG  lReleaseCount,  
    [out] LONG  *lpPreviousCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9c668-105">參數</span><span class="sxs-lookup"><span data-stu-id="9c668-105">Parameters</span></span>  
 `lReleaseCount`  
 <span data-ttu-id="9c668-106">[in]目前的計數增加的量`IHostSemaphore`執行個體。</span><span class="sxs-lookup"><span data-stu-id="9c668-106">[in] The amount by which to increase the count of the current `IHostSemaphore` instance.</span></span> <span data-ttu-id="9c668-107">這個數量必須大於零。</span><span class="sxs-lookup"><span data-stu-id="9c668-107">This amount must be greater than zero.</span></span>  
  
 `lpPreviousCount`  
 <span data-ttu-id="9c668-108">[out]前次計數或如果呼叫端不需要的先前計數為 null 指標。</span><span class="sxs-lookup"><span data-stu-id="9c668-108">[out] A pointer to the previous count, or null if the caller does not require the previous count.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c668-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="9c668-109">Return Value</span></span>  
  
|<span data-ttu-id="9c668-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9c668-110">HRESULT</span></span>|<span data-ttu-id="9c668-111">描述</span><span class="sxs-lookup"><span data-stu-id="9c668-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9c668-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="9c668-112">S_OK</span></span>|<span data-ttu-id="9c668-113">`ReleaseSemaphore`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="9c668-113">`ReleaseSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="9c668-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9c668-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9c668-115">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="9c668-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9c668-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9c668-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9c668-117">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="9c668-117">The call timed out.</span></span>|  
|<span data-ttu-id="9c668-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9c668-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9c668-119">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="9c668-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9c668-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9c668-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9c668-121">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="9c668-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9c668-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9c668-122">E_FAIL</span></span>|<span data-ttu-id="9c668-123">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="9c668-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9c668-124">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="9c668-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9c668-125">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="9c668-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c668-126">備註</span><span class="sxs-lookup"><span data-stu-id="9c668-126">Remarks</span></span>  
 <span data-ttu-id="9c668-127">CLR 通常會呼叫`ReleaseSemaphore`以通知主機發出它已完成使用資源，傳遞的值為 1 的`lReleaseCount`參數。</span><span class="sxs-lookup"><span data-stu-id="9c668-127">The CLR typically calls `ReleaseSemaphore` to notify the host that it has finished using a resource, passing a value of 1 for the `lReleaseCount` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c668-128">需求</span><span class="sxs-lookup"><span data-stu-id="9c668-128">Requirements</span></span>  
 <span data-ttu-id="9c668-129">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9c668-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c668-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9c668-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9c668-131">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9c668-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9c668-132">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c668-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c668-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c668-133">See Also</span></span>  
 [<span data-ttu-id="9c668-134">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="9c668-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="9c668-135">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="9c668-135">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="9c668-136">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="9c668-136">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="9c668-137">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="9c668-137">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="9c668-138">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="9c668-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
