---
title: "IHostSyncManager::CreateCrst 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateCrst
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateCrst
helpviewer_keywords:
- CreateCrst method [.NET Framework hosting]
- IHostSyncManager::CreateCrst method [.NET Framework hosting]
ms.assetid: ac278cc8-2540-4a6c-b5c6-b90c3970b4f4
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b54abb60b00d071900d3bfdd01c2e5f1807998a5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanagercreatecrst-method"></a><span data-ttu-id="a597e-102">IHostSyncManager::CreateCrst 方法</span><span class="sxs-lookup"><span data-stu-id="a597e-102">IHostSyncManager::CreateCrst Method</span></span>
<span data-ttu-id="a597e-103">建立關鍵區段進行同步處理物件。</span><span class="sxs-lookup"><span data-stu-id="a597e-103">Creates a critical section object for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a597e-104">語法</span><span class="sxs-lookup"><span data-stu-id="a597e-104">Syntax</span></span>  
  
```  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a597e-105">參數</span><span class="sxs-lookup"><span data-stu-id="a597e-105">Parameters</span></span>  
 `ppCrst`  
 <span data-ttu-id="a597e-106">[out]位址指標[IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)實作由主應用程式，則為 null，如果無法建立關鍵區段的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a597e-106">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance implemented by the host, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a597e-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="a597e-107">Return Value</span></span>  
  
|<span data-ttu-id="a597e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a597e-108">HRESULT</span></span>|<span data-ttu-id="a597e-109">描述</span><span class="sxs-lookup"><span data-stu-id="a597e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a597e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a597e-110">S_OK</span></span>|<span data-ttu-id="a597e-111">`CreateCrst`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="a597e-111">`CreateCrst` returned successfully.</span></span>|  
|<span data-ttu-id="a597e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a597e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a597e-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="a597e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a597e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a597e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a597e-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="a597e-115">The call timed out.</span></span>|  
|<span data-ttu-id="a597e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a597e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a597e-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="a597e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a597e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a597e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a597e-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="a597e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a597e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a597e-120">E_FAIL</span></span>|<span data-ttu-id="a597e-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="a597e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a597e-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="a597e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a597e-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a597e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a597e-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="a597e-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="a597e-125">沒有足夠的記憶體可用來建立要求的重要區段。</span><span class="sxs-lookup"><span data-stu-id="a597e-125">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a597e-126">備註</span><span class="sxs-lookup"><span data-stu-id="a597e-126">Remarks</span></span>  
 <span data-ttu-id="a597e-127">關鍵區段物件會提供同步處理所提供的 mutex 物件，類似，不同之處在於關鍵區段僅供在單一處理序執行緒。</span><span class="sxs-lookup"><span data-stu-id="a597e-127">Critical section objects provide synchronization similar to that provided by a mutex object, except that critical sections can be used only by the threads of a single process.</span></span> <span data-ttu-id="a597e-128">`CreateCrst`鏡像處理 Win32`InitializeCriticalSection`函式。</span><span class="sxs-lookup"><span data-stu-id="a597e-128">`CreateCrst` mirrors the Win32 `InitializeCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a597e-129">需求</span><span class="sxs-lookup"><span data-stu-id="a597e-129">Requirements</span></span>  
 <span data-ttu-id="a597e-130">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a597e-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a597e-131">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a597e-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a597e-132">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a597e-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a597e-133">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a597e-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a597e-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a597e-134">See Also</span></span>  
 [<span data-ttu-id="a597e-135">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="a597e-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="a597e-136">IHostCrst 介面</span><span class="sxs-lookup"><span data-stu-id="a597e-136">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="a597e-137">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="a597e-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="a597e-138">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="a597e-138">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="a597e-139">Mutex</span><span class="sxs-lookup"><span data-stu-id="a597e-139">Mutexes</span></span>](../../../../docs/standard/threading/mutexes.md)  
 [<span data-ttu-id="a597e-140">Semaphore 和 SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="a597e-140">Semaphore and SemaphoreSlim</span></span>](../../../../docs/standard/threading/semaphore-and-semaphoreslim.md)
