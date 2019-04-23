---
title: IHostSyncManager::CreateSemaphore 方法
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateSemaphore
helpviewer_keywords:
- CreateSemaphore method [.NET Framework hosting]
- IHostSyncManager::CreateSemaphore method [.NET Framework hosting]
ms.assetid: 37679e94-5ff9-4173-8fa5-457febeb89bf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ef9a5896c2ecc54b7fd48670f751d193ac74554
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59138615"
---
# <a name="ihostsyncmanagercreatesemaphore-method"></a><span data-ttu-id="b3bdb-102">IHostSyncManager::CreateSemaphore 方法</span><span class="sxs-lookup"><span data-stu-id="b3bdb-102">IHostSyncManager::CreateSemaphore Method</span></span>
<span data-ttu-id="b3bdb-103">會建立[IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)以作為等候事件的號誌的 common language runtime (CLR) 物件。</span><span class="sxs-lookup"><span data-stu-id="b3bdb-103">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the common language runtime (CLR) to use as a semaphore for wait events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3bdb-104">語法</span><span class="sxs-lookup"><span data-stu-id="b3bdb-104">Syntax</span></span>  
  
```  
HRESULT CreateSemaphore (  
    [in]  DWORD dwInitial,  
    [in]  DWORD dwMax,  
    [out] IHostSemaphore **ppSemaphore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3bdb-105">參數</span><span class="sxs-lookup"><span data-stu-id="b3bdb-105">Parameters</span></span>  
 `dwInitial`  
 <span data-ttu-id="b3bdb-106">[in]初始計數`ppSemaphore`。</span><span class="sxs-lookup"><span data-stu-id="b3bdb-106">[in] The initial count for `ppSemaphore`.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="b3bdb-107">[in]最大計數`ppSemaphore`。</span><span class="sxs-lookup"><span data-stu-id="b3bdb-107">[in] The maximum count for `ppSemaphore`.</span></span>  
  
 `ppSemaphore`  
 <span data-ttu-id="b3bdb-108">[out]位址指標`IHostSemaphore`執行個體，或如果無法建立號誌，則為 null。</span><span class="sxs-lookup"><span data-stu-id="b3bdb-108">[out] A pointer to the address of an `IHostSemaphore` instance, or null if the semaphore could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3bdb-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="b3bdb-109">Return Value</span></span>  
  
|<span data-ttu-id="b3bdb-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b3bdb-110">HRESULT</span></span>|<span data-ttu-id="b3bdb-111">描述</span><span class="sxs-lookup"><span data-stu-id="b3bdb-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b3bdb-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b3bdb-112">S_OK</span></span>|<span data-ttu-id="b3bdb-113">`CreateSemaphore` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="b3bdb-113">`CreateSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="b3bdb-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b3bdb-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b3bdb-115">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="b3bdb-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b3bdb-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b3bdb-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b3bdb-117">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="b3bdb-117">The call timed out.</span></span>|  
|<span data-ttu-id="b3bdb-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b3bdb-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b3bdb-119">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="b3bdb-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b3bdb-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b3bdb-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b3bdb-121">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="b3bdb-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b3bdb-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b3bdb-122">E_FAIL</span></span>|<span data-ttu-id="b3bdb-123">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="b3bdb-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b3bdb-124">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="b3bdb-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b3bdb-125">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b3bdb-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b3bdb-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b3bdb-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="b3bdb-127">記憶體不足，無法建立要求的事件物件。</span><span class="sxs-lookup"><span data-stu-id="b3bdb-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3bdb-128">備註</span><span class="sxs-lookup"><span data-stu-id="b3bdb-128">Remarks</span></span>  
 <span data-ttu-id="b3bdb-129">`CreateSemaphore` 鏡像 Win32 函式具有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="b3bdb-129">`CreateSemaphore` mirrors the Win32 function that has the same name.</span></span> <span data-ttu-id="b3bdb-130">`dwInitial`並`dwMax`參數使用相同的語意號誌計數做為 Win32`lInitialCount`和`lMaximumCount`參數，分別。</span><span class="sxs-lookup"><span data-stu-id="b3bdb-130">The `dwInitial` and `dwMax` parameters use the same semantics for the semaphore count as the Win32 `lInitialCount` and `lMaximumCount` parameters, respectively.</span></span> <span data-ttu-id="b3bdb-131">`dwInitial` 必須是介於 0 和`dwMax`（包含頭尾)。</span><span class="sxs-lookup"><span data-stu-id="b3bdb-131">`dwInitial` must be between zero and `dwMax`, inclusive.</span></span> <span data-ttu-id="b3bdb-132">`dwMax` 必須是小於或等於零。</span><span class="sxs-lookup"><span data-stu-id="b3bdb-132">`dwMax` must be greater than zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3bdb-133">需求</span><span class="sxs-lookup"><span data-stu-id="b3bdb-133">Requirements</span></span>  
 <span data-ttu-id="b3bdb-134">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b3bdb-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3bdb-135">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b3bdb-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b3bdb-136">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b3bdb-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b3bdb-137">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3bdb-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3bdb-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3bdb-138">See also</span></span>

- [<span data-ttu-id="b3bdb-139">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="b3bdb-139">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="b3bdb-140">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="b3bdb-140">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="b3bdb-141">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="b3bdb-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
