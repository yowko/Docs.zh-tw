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
ms.openlocfilehash: 3566907544c72da2735e155d9088fe09fea4a728
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803470"
---
# <a name="ihostsyncmanagercreatecrst-method"></a><span data-ttu-id="deafd-102">IHostSyncManager::CreateCrst 方法</span><span class="sxs-lookup"><span data-stu-id="deafd-102">IHostSyncManager::CreateCrst Method</span></span>
<span data-ttu-id="deafd-103">建立同步處理的重要區段物件。</span><span class="sxs-lookup"><span data-stu-id="deafd-103">Creates a critical section object for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="deafd-104">語法</span><span class="sxs-lookup"><span data-stu-id="deafd-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="deafd-105">參數</span><span class="sxs-lookup"><span data-stu-id="deafd-105">Parameters</span></span>  
 `ppCrst`  
 <span data-ttu-id="deafd-106">脫銷主機所實[IHostCrst](ihostcrst-interface.md)實例的位址指標，如果無法建立重要區段，則為 null。</span><span class="sxs-lookup"><span data-stu-id="deafd-106">[out] A pointer to the address of an [IHostCrst](ihostcrst-interface.md) instance implemented by the host, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="deafd-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="deafd-107">Return Value</span></span>  
  
|<span data-ttu-id="deafd-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="deafd-108">HRESULT</span></span>|<span data-ttu-id="deafd-109">描述</span><span class="sxs-lookup"><span data-stu-id="deafd-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="deafd-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="deafd-110">S_OK</span></span>|<span data-ttu-id="deafd-111">`CreateCrst`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="deafd-111">`CreateCrst` returned successfully.</span></span>|  
|<span data-ttu-id="deafd-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="deafd-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="deafd-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="deafd-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="deafd-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="deafd-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="deafd-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="deafd-115">The call timed out.</span></span>|  
|<span data-ttu-id="deafd-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="deafd-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="deafd-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="deafd-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="deafd-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="deafd-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="deafd-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="deafd-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="deafd-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="deafd-120">E_FAIL</span></span>|<span data-ttu-id="deafd-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="deafd-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="deafd-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="deafd-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="deafd-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="deafd-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="deafd-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="deafd-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="deafd-125">沒有足夠的記憶體可用來建立要求的重要區段。</span><span class="sxs-lookup"><span data-stu-id="deafd-125">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="deafd-126">備註</span><span class="sxs-lookup"><span data-stu-id="deafd-126">Remarks</span></span>  
 <span data-ttu-id="deafd-127">重要區段物件提供的同步處理與 mutex 物件所提供的類似，不同之處在于，重要區段只能由單一進程的執行緒使用。</span><span class="sxs-lookup"><span data-stu-id="deafd-127">Critical section objects provide synchronization similar to that provided by a mutex object, except that critical sections can be used only by the threads of a single process.</span></span> <span data-ttu-id="deafd-128">`CreateCrst`鏡像 Win32 `InitializeCriticalSection` 函數。</span><span class="sxs-lookup"><span data-stu-id="deafd-128">`CreateCrst` mirrors the Win32 `InitializeCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="deafd-129">規格需求</span><span class="sxs-lookup"><span data-stu-id="deafd-129">Requirements</span></span>  
 <span data-ttu-id="deafd-130">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="deafd-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="deafd-131">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="deafd-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="deafd-132">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="deafd-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="deafd-133">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="deafd-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deafd-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="deafd-134">See also</span></span>

- [<span data-ttu-id="deafd-135">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="deafd-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="deafd-136">IHostCrst 介面</span><span class="sxs-lookup"><span data-stu-id="deafd-136">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="deafd-137">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="deafd-137">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="deafd-138">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="deafd-138">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="deafd-139">Mutex</span><span class="sxs-lookup"><span data-stu-id="deafd-139">Mutexes</span></span>](../../../standard/threading/mutexes.md)
- [<span data-ttu-id="deafd-140">Semaphore 和 SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="deafd-140">Semaphore and SemaphoreSlim</span></span>](../../../standard/threading/semaphore-and-semaphoreslim.md)
