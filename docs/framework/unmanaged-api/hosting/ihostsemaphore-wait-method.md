---
title: IHostSemaphore::Wait 方法
ms.date: 03/30/2017
api_name:
- IHostSemaphore.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore::Wait
helpviewer_keywords:
- IHostSemaphore::Wait method [.NET Framework hosting]
- Wait method, IHostSemaphore interface [.NET Framework hosting]
ms.assetid: 0da962a3-ce55-44dd-ab7a-14ad7105af4a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d9fcbca92b1615679be57fb4c9b872339fef8a3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59118210"
---
# <a name="ihostsemaphorewait-method"></a><span data-ttu-id="c40ad-102">IHostSemaphore::Wait 方法</span><span class="sxs-lookup"><span data-stu-id="c40ad-102">IHostSemaphore::Wait Method</span></span>
<span data-ttu-id="c40ad-103">造成目前[IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)等候，直到它擁有的執行個體或指定的時間量。</span><span class="sxs-lookup"><span data-stu-id="c40ad-103">Causes the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance to wait until it is owned or the specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c40ad-104">語法</span><span class="sxs-lookup"><span data-stu-id="c40ad-104">Syntax</span></span>  
  
```  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c40ad-105">參數</span><span class="sxs-lookup"><span data-stu-id="c40ad-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="c40ad-106">[in]如果在傳回之前，等待的毫秒數目前`IHostSemaphore`不屬於執行個體。</span><span class="sxs-lookup"><span data-stu-id="c40ad-106">[in] The number of milliseconds to wait before returning, if the current `IHostSemaphore` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="c40ad-107">[in]其中一個[WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)值，指定如果這個，主應用程式應執行的動作作業封鎖。</span><span class="sxs-lookup"><span data-stu-id="c40ad-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, specifying what action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c40ad-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="c40ad-108">Return Value</span></span>  
  
|<span data-ttu-id="c40ad-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c40ad-109">HRESULT</span></span>|<span data-ttu-id="c40ad-110">描述</span><span class="sxs-lookup"><span data-stu-id="c40ad-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c40ad-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c40ad-111">S_OK</span></span>|<span data-ttu-id="c40ad-112">`Wait` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="c40ad-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="c40ad-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c40ad-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c40ad-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="c40ad-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c40ad-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c40ad-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c40ad-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="c40ad-116">The call timed out.</span></span>|  
|<span data-ttu-id="c40ad-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c40ad-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c40ad-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="c40ad-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c40ad-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c40ad-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c40ad-120">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="c40ad-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c40ad-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c40ad-121">E_FAIL</span></span>|<span data-ttu-id="c40ad-122">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="c40ad-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c40ad-123">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="c40ad-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c40ad-124">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="c40ad-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c40ad-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="c40ad-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="c40ad-126">主機會等候時間間隔內偵測到死結，然後選擇 目前`IHostSemaphore`作為死結的犧牲者的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c40ad-126">The host detected a deadlock during the wait interval, and chose the current `IHostSemaphore` instance as a deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c40ad-127">需求</span><span class="sxs-lookup"><span data-stu-id="c40ad-127">Requirements</span></span>  
 <span data-ttu-id="c40ad-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c40ad-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c40ad-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c40ad-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c40ad-130">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c40ad-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c40ad-131">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c40ad-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c40ad-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c40ad-132">See also</span></span>

- [<span data-ttu-id="c40ad-133">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="c40ad-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="c40ad-134">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="c40ad-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="c40ad-135">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="c40ad-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="c40ad-136">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="c40ad-136">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="c40ad-137">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="c40ad-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
