---
title: IHostSyncManager::CreateCrstWithSpinCount 方法
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateCrstWithSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateCrstWithSpinCount
helpviewer_keywords:
- CreateCrstWithSpinCount method [.NET Framework hosting]
- IHostSyncManager::CreateCrstWithSpinCount method [.NET Framework hosting]
ms.assetid: 7280fa8c-3639-4abf-91cb-bc343da742d1
topic_type:
- apiref
ms.openlocfilehash: 632b8d43ed459d489825dc796d39864e2ed15ec3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139420"
---
# <a name="ihostsyncmanagercreatecrstwithspincount-method"></a><span data-ttu-id="b3b0a-102">IHostSyncManager::CreateCrstWithSpinCount 方法</span><span class="sxs-lookup"><span data-stu-id="b3b0a-102">IHostSyncManager::CreateCrstWithSpinCount Method</span></span>
<span data-ttu-id="b3b0a-103">使用微調計數來建立重要區段物件，以進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="b3b0a-103">Creates a critical section object with spin count for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3b0a-104">語法</span><span class="sxs-lookup"><span data-stu-id="b3b0a-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCrstWithSpinCount (  
    [in]  DWORD dwSpinCount,  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3b0a-105">參數</span><span class="sxs-lookup"><span data-stu-id="b3b0a-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="b3b0a-106">在指定重要區段物件的微調計數。</span><span class="sxs-lookup"><span data-stu-id="b3b0a-106">[in] Specifies the spin count for the critical section object.</span></span>  
  
 `ppCrst`  
 <span data-ttu-id="b3b0a-107">脫銷[IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)實例位址的指標，如果無法建立重要區段，則為 null。</span><span class="sxs-lookup"><span data-stu-id="b3b0a-107">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3b0a-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="b3b0a-108">Return Value</span></span>  
  
|<span data-ttu-id="b3b0a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b3b0a-109">HRESULT</span></span>|<span data-ttu-id="b3b0a-110">描述</span><span class="sxs-lookup"><span data-stu-id="b3b0a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b3b0a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b3b0a-111">S_OK</span></span>|<span data-ttu-id="b3b0a-112">已成功傳回 `CreateCrstWithSpinCount`。</span><span class="sxs-lookup"><span data-stu-id="b3b0a-112">`CreateCrstWithSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="b3b0a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b3b0a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b3b0a-114">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="b3b0a-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b3b0a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b3b0a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b3b0a-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="b3b0a-116">The call timed out.</span></span>|  
|<span data-ttu-id="b3b0a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b3b0a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b3b0a-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="b3b0a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b3b0a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b3b0a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b3b0a-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="b3b0a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b3b0a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b3b0a-121">E_FAIL</span></span>|<span data-ttu-id="b3b0a-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="b3b0a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b3b0a-123">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="b3b0a-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b3b0a-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b3b0a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b3b0a-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b3b0a-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="b3b0a-126">沒有足夠的記憶體可用來建立要求的重要區段。</span><span class="sxs-lookup"><span data-stu-id="b3b0a-126">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3b0a-127">備註</span><span class="sxs-lookup"><span data-stu-id="b3b0a-127">Remarks</span></span>  
 <span data-ttu-id="b3b0a-128">微調計數只會在多處理器系統上使用。</span><span class="sxs-lookup"><span data-stu-id="b3b0a-128">A spin count is used only on a multi-processor system.</span></span> <span data-ttu-id="b3b0a-129">[微調計數] 會指定呼叫執行緒在與無法使用的重要區段相關聯的信號上執行等候作業之前，必須旋轉的次數。</span><span class="sxs-lookup"><span data-stu-id="b3b0a-129">The spin count specifies the number of times a calling thread must spin before it performs a wait operation on a semaphore that is associated with an unavailable critical section.</span></span> <span data-ttu-id="b3b0a-130">如果關鍵區段在微調作業期間變得免費，呼叫的執行緒會避免等候作業。</span><span class="sxs-lookup"><span data-stu-id="b3b0a-130">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span> <span data-ttu-id="b3b0a-131">`CreateCrstWithSpinCount` 鏡像 Win32 `InitializeCriticalSectionAndSpinCount` 函數。</span><span class="sxs-lookup"><span data-stu-id="b3b0a-131">`CreateCrstWithSpinCount` mirrors the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3b0a-132">需求</span><span class="sxs-lookup"><span data-stu-id="b3b0a-132">Requirements</span></span>  
 <span data-ttu-id="b3b0a-133">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b3b0a-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3b0a-134">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="b3b0a-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b3b0a-135">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b3b0a-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b3b0a-136">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3b0a-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3b0a-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="b3b0a-137">See also</span></span>

- [<span data-ttu-id="b3b0a-138">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="b3b0a-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="b3b0a-139">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="b3b0a-139">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="b3b0a-140">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="b3b0a-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
