---
title: IHostSyncManager::CreateCrst 方法
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateCrst
helpviewer_keywords:
- CreateCrst method [.NET Framework hosting]
- IHostSyncManager::CreateCrst method [.NET Framework hosting]
ms.assetid: ac278cc8-2540-4a6c-b5c6-b90c3970b4f4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b63b283a28ed27a70698c45bdc87d63fef0daf8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61696934"
---
# <a name="ihostsyncmanagercreatecrst-method"></a><span data-ttu-id="95100-102">IHostSyncManager::CreateCrst 方法</span><span class="sxs-lookup"><span data-stu-id="95100-102">IHostSyncManager::CreateCrst Method</span></span>
<span data-ttu-id="95100-103">建立同步處理的重要區段物件。</span><span class="sxs-lookup"><span data-stu-id="95100-103">Creates a critical section object for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95100-104">語法</span><span class="sxs-lookup"><span data-stu-id="95100-104">Syntax</span></span>  
  
```  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95100-105">參數</span><span class="sxs-lookup"><span data-stu-id="95100-105">Parameters</span></span>  
 `ppCrst`  
 <span data-ttu-id="95100-106">[out]位址指標[IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)實作由主應用程式，或如果無法建立重要區段則為 null 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="95100-106">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance implemented by the host, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="95100-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="95100-107">Return Value</span></span>  
  
|<span data-ttu-id="95100-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="95100-108">HRESULT</span></span>|<span data-ttu-id="95100-109">描述</span><span class="sxs-lookup"><span data-stu-id="95100-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="95100-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="95100-110">S_OK</span></span>|<span data-ttu-id="95100-111">`CreateCrst` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="95100-111">`CreateCrst` returned successfully.</span></span>|  
|<span data-ttu-id="95100-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="95100-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="95100-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="95100-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="95100-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="95100-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="95100-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="95100-115">The call timed out.</span></span>|  
|<span data-ttu-id="95100-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="95100-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="95100-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="95100-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="95100-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="95100-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="95100-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="95100-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="95100-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="95100-120">E_FAIL</span></span>|<span data-ttu-id="95100-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="95100-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="95100-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="95100-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="95100-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="95100-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="95100-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="95100-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="95100-125">沒有足夠的記憶體可用來建立要求的重要區段。</span><span class="sxs-lookup"><span data-stu-id="95100-125">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95100-126">備註</span><span class="sxs-lookup"><span data-stu-id="95100-126">Remarks</span></span>  
 <span data-ttu-id="95100-127">重要區段物件會提供同步處理所提供的 mutex 物件，類似，不同之處在於關鍵區段僅供單一處理序的執行緒。</span><span class="sxs-lookup"><span data-stu-id="95100-127">Critical section objects provide synchronization similar to that provided by a mutex object, except that critical sections can be used only by the threads of a single process.</span></span> <span data-ttu-id="95100-128">`CreateCrst` 鏡像處理 Win32`InitializeCriticalSection`函式。</span><span class="sxs-lookup"><span data-stu-id="95100-128">`CreateCrst` mirrors the Win32 `InitializeCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95100-129">需求</span><span class="sxs-lookup"><span data-stu-id="95100-129">Requirements</span></span>  
 <span data-ttu-id="95100-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="95100-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95100-131">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="95100-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="95100-132">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="95100-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="95100-133">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95100-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95100-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95100-134">See also</span></span>

- [<span data-ttu-id="95100-135">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="95100-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="95100-136">IHostCrst 介面</span><span class="sxs-lookup"><span data-stu-id="95100-136">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="95100-137">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="95100-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="95100-138">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="95100-138">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="95100-139">Mutex</span><span class="sxs-lookup"><span data-stu-id="95100-139">Mutexes</span></span>](../../../../docs/standard/threading/mutexes.md)
- [<span data-ttu-id="95100-140">Semaphore 和 SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="95100-140">Semaphore and SemaphoreSlim</span></span>](../../../../docs/standard/threading/semaphore-and-semaphoreslim.md)
