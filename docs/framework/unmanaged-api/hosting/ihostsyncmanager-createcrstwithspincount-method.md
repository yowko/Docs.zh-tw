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
ms.openlocfilehash: 6b2f57c7147cc8ff2abff848bd1e4661c2f5e728
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682874"
---
# <a name="ihostsyncmanagercreatecrstwithspincount-method"></a><span data-ttu-id="be960-102">IHostSyncManager::CreateCrstWithSpinCount 方法</span><span class="sxs-lookup"><span data-stu-id="be960-102">IHostSyncManager::CreateCrstWithSpinCount Method</span></span>

<span data-ttu-id="be960-103">使用微調計數來建立重要區段物件以進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="be960-103">Creates a critical section object with spin count for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be960-104">語法</span><span class="sxs-lookup"><span data-stu-id="be960-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCrstWithSpinCount (  
    [in]  DWORD dwSpinCount,  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be960-105">參數</span><span class="sxs-lookup"><span data-stu-id="be960-105">Parameters</span></span>  

 `dwSpinCount`  
 <span data-ttu-id="be960-106">在指定重要區段物件的微調計數。</span><span class="sxs-lookup"><span data-stu-id="be960-106">[in] Specifies the spin count for the critical section object.</span></span>  
  
 `ppCrst`  
 <span data-ttu-id="be960-107">擴展 [IHostCrst](ihostcrst-interface.md) 實例位址的指標，如果無法建立重要區段，則為 null。</span><span class="sxs-lookup"><span data-stu-id="be960-107">[out] A pointer to the address of an [IHostCrst](ihostcrst-interface.md) instance, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be960-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="be960-108">Return Value</span></span>  
  
|<span data-ttu-id="be960-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="be960-109">HRESULT</span></span>|<span data-ttu-id="be960-110">描述</span><span class="sxs-lookup"><span data-stu-id="be960-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="be960-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="be960-111">S_OK</span></span>|<span data-ttu-id="be960-112">`CreateCrstWithSpinCount` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="be960-112">`CreateCrstWithSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="be960-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="be960-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="be960-114">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="be960-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="be960-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="be960-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="be960-116">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="be960-116">The call timed out.</span></span>|  
|<span data-ttu-id="be960-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="be960-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="be960-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="be960-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="be960-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="be960-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="be960-120">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="be960-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="be960-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="be960-121">E_FAIL</span></span>|<span data-ttu-id="be960-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="be960-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="be960-123">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="be960-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="be960-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="be960-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="be960-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="be960-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="be960-126">沒有足夠的記憶體可用來建立要求的重要區段。</span><span class="sxs-lookup"><span data-stu-id="be960-126">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be960-127">備註</span><span class="sxs-lookup"><span data-stu-id="be960-127">Remarks</span></span>  

 <span data-ttu-id="be960-128">微調計數只會在多處理器系統上使用。</span><span class="sxs-lookup"><span data-stu-id="be960-128">A spin count is used only on a multi-processor system.</span></span> <span data-ttu-id="be960-129">微調計數會指定呼叫執行緒在與無法使用的重要區段相關聯的信號上執行等候作業之前，必須旋轉的次數。</span><span class="sxs-lookup"><span data-stu-id="be960-129">The spin count specifies the number of times a calling thread must spin before it performs a wait operation on a semaphore that is associated with an unavailable critical section.</span></span> <span data-ttu-id="be960-130">如果重要區段在微調作業期間變成可用，則呼叫執行緒會避免等候作業。</span><span class="sxs-lookup"><span data-stu-id="be960-130">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span> <span data-ttu-id="be960-131">`CreateCrstWithSpinCount` 鏡像 Win32 `InitializeCriticalSectionAndSpinCount` 函數。</span><span class="sxs-lookup"><span data-stu-id="be960-131">`CreateCrstWithSpinCount` mirrors the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be960-132">需求</span><span class="sxs-lookup"><span data-stu-id="be960-132">Requirements</span></span>  

 <span data-ttu-id="be960-133">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="be960-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be960-134">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="be960-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="be960-135">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="be960-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="be960-136">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be960-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be960-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be960-137">See also</span></span>

- [<span data-ttu-id="be960-138">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="be960-138">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="be960-139">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="be960-139">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="be960-140">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="be960-140">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
