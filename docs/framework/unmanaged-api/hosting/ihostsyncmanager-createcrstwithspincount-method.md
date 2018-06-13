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
ms.openlocfilehash: 50f292ab39bcf77d49d8a363b43b9233f350974c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446762"
---
# <a name="ihostsyncmanagercreatecrstwithspincount-method"></a><span data-ttu-id="f5348-102">IHostSyncManager::CreateCrstWithSpinCount 方法</span><span class="sxs-lookup"><span data-stu-id="f5348-102">IHostSyncManager::CreateCrstWithSpinCount Method</span></span>
<span data-ttu-id="f5348-103">建立關鍵區段物件具有微調計數進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="f5348-103">Creates a critical section object with spin count for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5348-104">語法</span><span class="sxs-lookup"><span data-stu-id="f5348-104">Syntax</span></span>  
  
```  
HRESULT CreateCrstWithSpinCount (  
    [in]  DWORD dwSpinCount,  
    [out] IHostCrst** ppCrst  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f5348-105">參數</span><span class="sxs-lookup"><span data-stu-id="f5348-105">Parameters</span></span>  
 `dwSpinCount`  
 <span data-ttu-id="f5348-106">[in]指定微調計數關鍵區段物件。</span><span class="sxs-lookup"><span data-stu-id="f5348-106">[in] Specifies the spin count for the critical section object.</span></span>  
  
 `ppCrst`  
 <span data-ttu-id="f5348-107">[out]位址指標[IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)執行個體，或如果無法建立關鍵區段，則為 null。</span><span class="sxs-lookup"><span data-stu-id="f5348-107">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5348-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="f5348-108">Return Value</span></span>  
  
|<span data-ttu-id="f5348-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f5348-109">HRESULT</span></span>|<span data-ttu-id="f5348-110">描述</span><span class="sxs-lookup"><span data-stu-id="f5348-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f5348-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f5348-111">S_OK</span></span>|<span data-ttu-id="f5348-112">`CreateCrstWithSpinCount` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="f5348-112">`CreateCrstWithSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="f5348-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f5348-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f5348-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="f5348-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f5348-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f5348-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f5348-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="f5348-116">The call timed out.</span></span>|  
|<span data-ttu-id="f5348-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f5348-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f5348-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="f5348-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f5348-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f5348-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f5348-120">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="f5348-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f5348-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f5348-121">E_FAIL</span></span>|<span data-ttu-id="f5348-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="f5348-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f5348-123">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="f5348-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f5348-124">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="f5348-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f5348-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="f5348-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="f5348-126">沒有足夠的記憶體可用來建立要求的重要區段。</span><span class="sxs-lookup"><span data-stu-id="f5348-126">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5348-127">備註</span><span class="sxs-lookup"><span data-stu-id="f5348-127">Remarks</span></span>  
 <span data-ttu-id="f5348-128">微調計數只適用於多處理器系統。</span><span class="sxs-lookup"><span data-stu-id="f5348-128">A spin count is used only on a multi-processor system.</span></span> <span data-ttu-id="f5348-129">微調計數指定的執行與無法使用的重要區段相關聯的號誌上的等候作業之前，必須備呼叫執行緒的次數。</span><span class="sxs-lookup"><span data-stu-id="f5348-129">The spin count specifies the number of times a calling thread must spin before it performs a wait operation on a semaphore that is associated with an unavailable critical section.</span></span> <span data-ttu-id="f5348-130">關鍵區段會變成可用微調作業期間，如果呼叫的執行緒可避免等候作業。</span><span class="sxs-lookup"><span data-stu-id="f5348-130">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span> <span data-ttu-id="f5348-131">`CreateCrstWithSpinCount` 鏡像處理 Win32`InitializeCriticalSectionAndSpinCount`函式。</span><span class="sxs-lookup"><span data-stu-id="f5348-131">`CreateCrstWithSpinCount` mirrors the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5348-132">需求</span><span class="sxs-lookup"><span data-stu-id="f5348-132">Requirements</span></span>  
 <span data-ttu-id="f5348-133">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f5348-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5348-134">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f5348-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5348-135">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f5348-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5348-136">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5348-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5348-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5348-137">See Also</span></span>  
 [<span data-ttu-id="f5348-138">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="f5348-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="f5348-139">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="f5348-139">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="f5348-140">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="f5348-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
