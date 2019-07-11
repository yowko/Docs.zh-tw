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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16fcc631e7e734e1bce4566f31d209a8433fbfdf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753450"
---
# <a name="ihostsyncmanagercreatecrstwithspincount-method"></a><span data-ttu-id="bc39f-102">IHostSyncManager::CreateCrstWithSpinCount 方法</span><span class="sxs-lookup"><span data-stu-id="bc39f-102">IHostSyncManager::CreateCrstWithSpinCount Method</span></span>
<span data-ttu-id="bc39f-103">建立具有同步處理的微調計數的重要區段物件。</span><span class="sxs-lookup"><span data-stu-id="bc39f-103">Creates a critical section object with spin count for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc39f-104">語法</span><span class="sxs-lookup"><span data-stu-id="bc39f-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCrstWithSpinCount (  
    [in]  DWORD dwSpinCount,  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc39f-105">參數</span><span class="sxs-lookup"><span data-stu-id="bc39f-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="bc39f-106">[in]指定旋轉計數重要區段物件。</span><span class="sxs-lookup"><span data-stu-id="bc39f-106">[in] Specifies the spin count for the critical section object.</span></span>  
  
 `ppCrst`  
 <span data-ttu-id="bc39f-107">[out]位址指標[IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)執行個體，或如果無法建立重要區段，則為 null。</span><span class="sxs-lookup"><span data-stu-id="bc39f-107">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc39f-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="bc39f-108">Return Value</span></span>  
  
|<span data-ttu-id="bc39f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bc39f-109">HRESULT</span></span>|<span data-ttu-id="bc39f-110">描述</span><span class="sxs-lookup"><span data-stu-id="bc39f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bc39f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="bc39f-111">S_OK</span></span>|<span data-ttu-id="bc39f-112">`CreateCrstWithSpinCount` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="bc39f-112">`CreateCrstWithSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="bc39f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bc39f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bc39f-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="bc39f-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bc39f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bc39f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bc39f-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="bc39f-116">The call timed out.</span></span>|  
|<span data-ttu-id="bc39f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bc39f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bc39f-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="bc39f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bc39f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bc39f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bc39f-120">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="bc39f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bc39f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bc39f-121">E_FAIL</span></span>|<span data-ttu-id="bc39f-122">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="bc39f-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bc39f-123">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="bc39f-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bc39f-124">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="bc39f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="bc39f-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="bc39f-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="bc39f-126">沒有足夠的記憶體可用來建立要求的重要區段。</span><span class="sxs-lookup"><span data-stu-id="bc39f-126">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc39f-127">備註</span><span class="sxs-lookup"><span data-stu-id="bc39f-127">Remarks</span></span>  
 <span data-ttu-id="bc39f-128">旋轉計數只適用於在多處理器系統。</span><span class="sxs-lookup"><span data-stu-id="bc39f-128">A spin count is used only on a multi-processor system.</span></span> <span data-ttu-id="bc39f-129">旋轉計數指定的執行與無法使用的重要區段相關聯的號誌的等候作業之前，呼叫的執行緒必須啟動的次數。</span><span class="sxs-lookup"><span data-stu-id="bc39f-129">The spin count specifies the number of times a calling thread must spin before it performs a wait operation on a semaphore that is associated with an unavailable critical section.</span></span> <span data-ttu-id="bc39f-130">重要區段中變成可用時微調作業，如果呼叫執行緒會避免等候作業。</span><span class="sxs-lookup"><span data-stu-id="bc39f-130">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span> <span data-ttu-id="bc39f-131">`CreateCrstWithSpinCount` 鏡像處理 Win32`InitializeCriticalSectionAndSpinCount`函式。</span><span class="sxs-lookup"><span data-stu-id="bc39f-131">`CreateCrstWithSpinCount` mirrors the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc39f-132">需求</span><span class="sxs-lookup"><span data-stu-id="bc39f-132">Requirements</span></span>  
 <span data-ttu-id="bc39f-133">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bc39f-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc39f-134">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bc39f-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bc39f-135">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="bc39f-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bc39f-136">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc39f-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc39f-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc39f-137">See also</span></span>

- [<span data-ttu-id="bc39f-138">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="bc39f-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="bc39f-139">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="bc39f-139">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="bc39f-140">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="bc39f-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
