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
ms.openlocfilehash: 680280e959d523356b95a5a4d9390c80720c0330
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803131"
---
# <a name="ihostsyncmanagercreatesemaphore-method"></a><span data-ttu-id="30dd0-102">IHostSyncManager::CreateSemaphore 方法</span><span class="sxs-lookup"><span data-stu-id="30dd0-102">IHostSyncManager::CreateSemaphore Method</span></span>
<span data-ttu-id="30dd0-103">建立[IHostSemaphore](ihostsemaphore-interface.md)物件，以供 common language RUNTIME （CLR）用來做為等候事件的信號。</span><span class="sxs-lookup"><span data-stu-id="30dd0-103">Creates an [IHostSemaphore](ihostsemaphore-interface.md) object for the common language runtime (CLR) to use as a semaphore for wait events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30dd0-104">語法</span><span class="sxs-lookup"><span data-stu-id="30dd0-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateSemaphore (  
    [in]  DWORD dwInitial,  
    [in]  DWORD dwMax,  
    [out] IHostSemaphore **ppSemaphore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30dd0-105">參數</span><span class="sxs-lookup"><span data-stu-id="30dd0-105">Parameters</span></span>  
 `dwInitial`  
 <span data-ttu-id="30dd0-106">在的初始計數 `ppSemaphore` 。</span><span class="sxs-lookup"><span data-stu-id="30dd0-106">[in] The initial count for `ppSemaphore`.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="30dd0-107">在的最大計數 `ppSemaphore` 。</span><span class="sxs-lookup"><span data-stu-id="30dd0-107">[in] The maximum count for `ppSemaphore`.</span></span>  
  
 `ppSemaphore`  
 <span data-ttu-id="30dd0-108">脫銷實例位址的指標 `IHostSemaphore` ，如果無法建立信號，則為 null。</span><span class="sxs-lookup"><span data-stu-id="30dd0-108">[out] A pointer to the address of an `IHostSemaphore` instance, or null if the semaphore could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30dd0-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="30dd0-109">Return Value</span></span>  
  
|<span data-ttu-id="30dd0-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="30dd0-110">HRESULT</span></span>|<span data-ttu-id="30dd0-111">描述</span><span class="sxs-lookup"><span data-stu-id="30dd0-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="30dd0-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="30dd0-112">S_OK</span></span>|<span data-ttu-id="30dd0-113">`CreateSemaphore`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="30dd0-113">`CreateSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="30dd0-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="30dd0-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="30dd0-115">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="30dd0-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="30dd0-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="30dd0-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="30dd0-117">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="30dd0-117">The call timed out.</span></span>|  
|<span data-ttu-id="30dd0-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="30dd0-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="30dd0-119">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="30dd0-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="30dd0-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="30dd0-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="30dd0-121">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="30dd0-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="30dd0-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="30dd0-122">E_FAIL</span></span>|<span data-ttu-id="30dd0-123">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="30dd0-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="30dd0-124">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="30dd0-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="30dd0-125">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="30dd0-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="30dd0-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="30dd0-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="30dd0-127">沒有足夠的記憶體可用來建立要求的事件物件。</span><span class="sxs-lookup"><span data-stu-id="30dd0-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30dd0-128">備註</span><span class="sxs-lookup"><span data-stu-id="30dd0-128">Remarks</span></span>  
 <span data-ttu-id="30dd0-129">`CreateSemaphore`鏡像具有相同名稱的 Win32 函數。</span><span class="sxs-lookup"><span data-stu-id="30dd0-129">`CreateSemaphore` mirrors the Win32 function that has the same name.</span></span> <span data-ttu-id="30dd0-130">`dwInitial`和 `dwMax` 參數會分別針對信號計數使用相同的語義，做為 Win32 `lInitialCount` 和 `lMaximumCount` 參數。</span><span class="sxs-lookup"><span data-stu-id="30dd0-130">The `dwInitial` and `dwMax` parameters use the same semantics for the semaphore count as the Win32 `lInitialCount` and `lMaximumCount` parameters, respectively.</span></span> <span data-ttu-id="30dd0-131">`dwInitial`必須介於零和 `dwMax` （含）之間。</span><span class="sxs-lookup"><span data-stu-id="30dd0-131">`dwInitial` must be between zero and `dwMax`, inclusive.</span></span> <span data-ttu-id="30dd0-132">`dwMax`必須大於零。</span><span class="sxs-lookup"><span data-stu-id="30dd0-132">`dwMax` must be greater than zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30dd0-133">規格需求</span><span class="sxs-lookup"><span data-stu-id="30dd0-133">Requirements</span></span>  
 <span data-ttu-id="30dd0-134">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="30dd0-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30dd0-135">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="30dd0-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="30dd0-136">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="30dd0-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="30dd0-137">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30dd0-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30dd0-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30dd0-138">See also</span></span>

- [<span data-ttu-id="30dd0-139">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="30dd0-139">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="30dd0-140">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="30dd0-140">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="30dd0-141">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="30dd0-141">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
