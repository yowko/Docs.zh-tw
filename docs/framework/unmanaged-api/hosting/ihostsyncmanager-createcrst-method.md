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
ms.openlocfilehash: 03c0f94d10629b677cca4c4c456cdaab344cfcdd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139426"
---
# <a name="ihostsyncmanagercreatecrst-method"></a><span data-ttu-id="cbe88-102">IHostSyncManager::CreateCrst 方法</span><span class="sxs-lookup"><span data-stu-id="cbe88-102">IHostSyncManager::CreateCrst Method</span></span>
<span data-ttu-id="cbe88-103">建立同步處理的重要區段物件。</span><span class="sxs-lookup"><span data-stu-id="cbe88-103">Creates a critical section object for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbe88-104">語法</span><span class="sxs-lookup"><span data-stu-id="cbe88-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbe88-105">參數</span><span class="sxs-lookup"><span data-stu-id="cbe88-105">Parameters</span></span>  
 `ppCrst`  
 <span data-ttu-id="cbe88-106">脫銷主機所實[IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)實例的位址指標，如果無法建立重要區段，則為 null。</span><span class="sxs-lookup"><span data-stu-id="cbe88-106">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance implemented by the host, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cbe88-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="cbe88-107">Return Value</span></span>  
  
|<span data-ttu-id="cbe88-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cbe88-108">HRESULT</span></span>|<span data-ttu-id="cbe88-109">描述</span><span class="sxs-lookup"><span data-stu-id="cbe88-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cbe88-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="cbe88-110">S_OK</span></span>|<span data-ttu-id="cbe88-111">已成功傳回 `CreateCrst`。</span><span class="sxs-lookup"><span data-stu-id="cbe88-111">`CreateCrst` returned successfully.</span></span>|  
|<span data-ttu-id="cbe88-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cbe88-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cbe88-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="cbe88-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cbe88-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cbe88-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cbe88-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="cbe88-115">The call timed out.</span></span>|  
|<span data-ttu-id="cbe88-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cbe88-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cbe88-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="cbe88-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cbe88-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cbe88-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cbe88-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="cbe88-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cbe88-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cbe88-120">E_FAIL</span></span>|<span data-ttu-id="cbe88-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="cbe88-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cbe88-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="cbe88-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cbe88-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="cbe88-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="cbe88-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="cbe88-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="cbe88-125">沒有足夠的記憶體可用來建立要求的重要區段。</span><span class="sxs-lookup"><span data-stu-id="cbe88-125">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbe88-126">備註</span><span class="sxs-lookup"><span data-stu-id="cbe88-126">Remarks</span></span>  
 <span data-ttu-id="cbe88-127">重要區段物件提供的同步處理與 mutex 物件所提供的類似，不同之處在于，重要區段只能由單一進程的執行緒使用。</span><span class="sxs-lookup"><span data-stu-id="cbe88-127">Critical section objects provide synchronization similar to that provided by a mutex object, except that critical sections can be used only by the threads of a single process.</span></span> <span data-ttu-id="cbe88-128">`CreateCrst` 鏡像 Win32 `InitializeCriticalSection` 函數。</span><span class="sxs-lookup"><span data-stu-id="cbe88-128">`CreateCrst` mirrors the Win32 `InitializeCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbe88-129">需求</span><span class="sxs-lookup"><span data-stu-id="cbe88-129">Requirements</span></span>  
 <span data-ttu-id="cbe88-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cbe88-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbe88-131">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="cbe88-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cbe88-132">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="cbe88-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cbe88-133">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbe88-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbe88-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="cbe88-134">See also</span></span>

- [<span data-ttu-id="cbe88-135">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="cbe88-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="cbe88-136">IHostCrst 介面</span><span class="sxs-lookup"><span data-stu-id="cbe88-136">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="cbe88-137">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="cbe88-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="cbe88-138">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="cbe88-138">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="cbe88-139">Mutex</span><span class="sxs-lookup"><span data-stu-id="cbe88-139">Mutexes</span></span>](../../../standard/threading/mutexes.md)
- [<span data-ttu-id="cbe88-140">Semaphore 和 SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="cbe88-140">Semaphore and SemaphoreSlim</span></span>](../../../standard/threading/semaphore-and-semaphoreslim.md)
