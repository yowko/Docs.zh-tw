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
ms.openlocfilehash: 02066d3923714e66bf287f1435b7854280c97cb7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195823"
---
# <a name="ihostsyncmanagercreatesemaphore-method"></a><span data-ttu-id="6c70b-102">IHostSyncManager::CreateSemaphore 方法</span><span class="sxs-lookup"><span data-stu-id="6c70b-102">IHostSyncManager::CreateSemaphore Method</span></span>
<span data-ttu-id="6c70b-103">建立[IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)物件，以供 common language RUNTIME （CLR）用來做為等候事件的信號。</span><span class="sxs-lookup"><span data-stu-id="6c70b-103">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the common language runtime (CLR) to use as a semaphore for wait events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c70b-104">語法</span><span class="sxs-lookup"><span data-stu-id="6c70b-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateSemaphore (  
    [in]  DWORD dwInitial,  
    [in]  DWORD dwMax,  
    [out] IHostSemaphore **ppSemaphore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c70b-105">參數</span><span class="sxs-lookup"><span data-stu-id="6c70b-105">Parameters</span></span>  
 `dwInitial`  
 <span data-ttu-id="6c70b-106">在`ppSemaphore`的初始計數。</span><span class="sxs-lookup"><span data-stu-id="6c70b-106">[in] The initial count for `ppSemaphore`.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="6c70b-107">在`ppSemaphore`的最大計數。</span><span class="sxs-lookup"><span data-stu-id="6c70b-107">[in] The maximum count for `ppSemaphore`.</span></span>  
  
 `ppSemaphore`  
 <span data-ttu-id="6c70b-108">脫銷`IHostSemaphore` 實例之位址的指標，如果無法建立信號，則為 null。</span><span class="sxs-lookup"><span data-stu-id="6c70b-108">[out] A pointer to the address of an `IHostSemaphore` instance, or null if the semaphore could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c70b-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="6c70b-109">Return Value</span></span>  
  
|<span data-ttu-id="6c70b-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6c70b-110">HRESULT</span></span>|<span data-ttu-id="6c70b-111">描述</span><span class="sxs-lookup"><span data-stu-id="6c70b-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6c70b-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="6c70b-112">S_OK</span></span>|<span data-ttu-id="6c70b-113">已成功傳回 `CreateSemaphore`。</span><span class="sxs-lookup"><span data-stu-id="6c70b-113">`CreateSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="6c70b-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6c70b-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6c70b-115">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="6c70b-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6c70b-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6c70b-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6c70b-117">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="6c70b-117">The call timed out.</span></span>|  
|<span data-ttu-id="6c70b-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6c70b-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6c70b-119">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="6c70b-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6c70b-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6c70b-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6c70b-121">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="6c70b-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6c70b-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6c70b-122">E_FAIL</span></span>|<span data-ttu-id="6c70b-123">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="6c70b-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6c70b-124">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="6c70b-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6c70b-125">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="6c70b-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6c70b-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="6c70b-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="6c70b-127">沒有足夠的記憶體可用來建立要求的事件物件。</span><span class="sxs-lookup"><span data-stu-id="6c70b-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c70b-128">備註</span><span class="sxs-lookup"><span data-stu-id="6c70b-128">Remarks</span></span>  
 <span data-ttu-id="6c70b-129">`CreateSemaphore` 會反映具有相同名稱的 Win32 函數。</span><span class="sxs-lookup"><span data-stu-id="6c70b-129">`CreateSemaphore` mirrors the Win32 function that has the same name.</span></span> <span data-ttu-id="6c70b-130">`dwInitial` 和 `dwMax` 參數會分別針對信號計數使用相同的語義，做為 Win32 `lInitialCount` 和 `lMaximumCount` 參數。</span><span class="sxs-lookup"><span data-stu-id="6c70b-130">The `dwInitial` and `dwMax` parameters use the same semantics for the semaphore count as the Win32 `lInitialCount` and `lMaximumCount` parameters, respectively.</span></span> <span data-ttu-id="6c70b-131">`dwInitial` 必須介於零和 `dwMax`（含）之間。</span><span class="sxs-lookup"><span data-stu-id="6c70b-131">`dwInitial` must be between zero and `dwMax`, inclusive.</span></span> <span data-ttu-id="6c70b-132">`dwMax` 必須大於零。</span><span class="sxs-lookup"><span data-stu-id="6c70b-132">`dwMax` must be greater than zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c70b-133">需求</span><span class="sxs-lookup"><span data-stu-id="6c70b-133">Requirements</span></span>  
 <span data-ttu-id="6c70b-134">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6c70b-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c70b-135">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="6c70b-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6c70b-136">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6c70b-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c70b-137">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c70b-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c70b-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="6c70b-138">See also</span></span>

- [<span data-ttu-id="6c70b-139">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="6c70b-139">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="6c70b-140">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="6c70b-140">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="6c70b-141">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="6c70b-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
