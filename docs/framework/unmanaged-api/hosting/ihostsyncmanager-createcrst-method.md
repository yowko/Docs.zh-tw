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
ms.openlocfilehash: 27861a9258916f4c188d981c44833e5be4c507f2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682871"
---
# <a name="ihostsyncmanagercreatecrst-method"></a><span data-ttu-id="d5734-102">IHostSyncManager::CreateCrst 方法</span><span class="sxs-lookup"><span data-stu-id="d5734-102">IHostSyncManager::CreateCrst Method</span></span>

<span data-ttu-id="d5734-103">建立同步處理的重要區段物件。</span><span class="sxs-lookup"><span data-stu-id="d5734-103">Creates a critical section object for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5734-104">語法</span><span class="sxs-lookup"><span data-stu-id="d5734-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5734-105">參數</span><span class="sxs-lookup"><span data-stu-id="d5734-105">Parameters</span></span>  

 `ppCrst`  
 <span data-ttu-id="d5734-106">擴展主機所執行之 [IHostCrst](ihostcrst-interface.md) 實例位址的指標，如果無法建立重要區段，則為 null。</span><span class="sxs-lookup"><span data-stu-id="d5734-106">[out] A pointer to the address of an [IHostCrst](ihostcrst-interface.md) instance implemented by the host, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5734-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="d5734-107">Return Value</span></span>  
  
|<span data-ttu-id="d5734-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d5734-108">HRESULT</span></span>|<span data-ttu-id="d5734-109">描述</span><span class="sxs-lookup"><span data-stu-id="d5734-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d5734-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d5734-110">S_OK</span></span>|<span data-ttu-id="d5734-111">`CreateCrst` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="d5734-111">`CreateCrst` returned successfully.</span></span>|  
|<span data-ttu-id="d5734-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d5734-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d5734-113">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="d5734-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d5734-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d5734-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d5734-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="d5734-115">The call timed out.</span></span>|  
|<span data-ttu-id="d5734-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d5734-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d5734-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="d5734-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d5734-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d5734-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d5734-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="d5734-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d5734-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d5734-120">E_FAIL</span></span>|<span data-ttu-id="d5734-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="d5734-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d5734-122">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="d5734-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d5734-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d5734-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d5734-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d5734-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="d5734-125">沒有足夠的記憶體可用來建立要求的重要區段。</span><span class="sxs-lookup"><span data-stu-id="d5734-125">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5734-126">備註</span><span class="sxs-lookup"><span data-stu-id="d5734-126">Remarks</span></span>  

 <span data-ttu-id="d5734-127">重要區段物件提供的同步處理與 mutex 物件所提供的類似，不同之處在于，只有單一進程的執行緒可以使用重要區段。</span><span class="sxs-lookup"><span data-stu-id="d5734-127">Critical section objects provide synchronization similar to that provided by a mutex object, except that critical sections can be used only by the threads of a single process.</span></span> <span data-ttu-id="d5734-128">`CreateCrst` 鏡像 Win32 `InitializeCriticalSection` 函數。</span><span class="sxs-lookup"><span data-stu-id="d5734-128">`CreateCrst` mirrors the Win32 `InitializeCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5734-129">需求</span><span class="sxs-lookup"><span data-stu-id="d5734-129">Requirements</span></span>  

 <span data-ttu-id="d5734-130">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d5734-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5734-131">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d5734-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d5734-132">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="d5734-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d5734-133">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5734-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5734-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5734-134">See also</span></span>

- [<span data-ttu-id="d5734-135">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="d5734-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="d5734-136">IHostCrst 介面</span><span class="sxs-lookup"><span data-stu-id="d5734-136">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="d5734-137">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="d5734-137">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="d5734-138">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="d5734-138">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="d5734-139">Mutex</span><span class="sxs-lookup"><span data-stu-id="d5734-139">Mutexes</span></span>](../../../standard/threading/mutexes.md)
- [<span data-ttu-id="d5734-140">Semaphore 和 SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="d5734-140">Semaphore and SemaphoreSlim</span></span>](../../../standard/threading/semaphore-and-semaphoreslim.md)
