---
title: IHostSyncManager::CreateRWLockReaderEvent 方法
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateRWLockReaderEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateRWLockReaderEvent
helpviewer_keywords:
- CreateRWLockReaderEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockReaderEvent method [.NET Framework hosting]
ms.assetid: 68c4ea19-c47c-45c6-b420-d3a2ba1c2d50
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 89e6a6e1d2aa90d4f113364693fb5f1e0399c21d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745450"
---
# <a name="ihostsyncmanagercreaterwlockreaderevent-method"></a><span data-ttu-id="e8a84-102">IHostSyncManager::CreateRWLockReaderEvent 方法</span><span class="sxs-lookup"><span data-stu-id="e8a84-102">IHostSyncManager::CreateRWLockReaderEvent Method</span></span>
<span data-ttu-id="e8a84-103">建立手動重設事件物件實作的讀取器的鎖定。</span><span class="sxs-lookup"><span data-stu-id="e8a84-103">Creates a manual-reset event object for the implementation of a reader lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8a84-104">語法</span><span class="sxs-lookup"><span data-stu-id="e8a84-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockReaderEvent (  
    [in]  BOOL bInitialState,  
    [in]  SIZE_T cookie,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e8a84-105">參數</span><span class="sxs-lookup"><span data-stu-id="e8a84-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="e8a84-106">[in]`true`的話`ppEvent`應該收到信號; 否則即為`false`。</span><span class="sxs-lookup"><span data-stu-id="e8a84-106">[in] `true`, if `ppEvent` should be signaled; otherwise, `false`.</span></span>  
  
 `cookie`  
 <span data-ttu-id="e8a84-107">[in]此 cookie 會與 讀取器鎖定。</span><span class="sxs-lookup"><span data-stu-id="e8a84-107">[in] A cookie to associate with the reader lock.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="e8a84-108">[out]位址指標[IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)執行個體，或如果無法建立事件物件，則為 null。</span><span class="sxs-lookup"><span data-stu-id="e8a84-108">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8a84-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="e8a84-109">Return Value</span></span>  
  
|<span data-ttu-id="e8a84-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e8a84-110">HRESULT</span></span>|<span data-ttu-id="e8a84-111">描述</span><span class="sxs-lookup"><span data-stu-id="e8a84-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e8a84-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="e8a84-112">S_OK</span></span>|<span data-ttu-id="e8a84-113">`CreateRWLockReaderEvent` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="e8a84-113">`CreateRWLockReaderEvent` returned successfully.</span></span>|  
|<span data-ttu-id="e8a84-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e8a84-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e8a84-115">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="e8a84-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e8a84-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e8a84-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e8a84-117">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="e8a84-117">The call timed out.</span></span>|  
|<span data-ttu-id="e8a84-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e8a84-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e8a84-119">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="e8a84-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e8a84-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e8a84-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e8a84-121">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="e8a84-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e8a84-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e8a84-122">E_FAIL</span></span>|<span data-ttu-id="e8a84-123">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="e8a84-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e8a84-124">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="e8a84-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e8a84-125">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="e8a84-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e8a84-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="e8a84-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="e8a84-127">記憶體不足，無法建立要求的事件物件。</span><span class="sxs-lookup"><span data-stu-id="e8a84-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8a84-128">備註</span><span class="sxs-lookup"><span data-stu-id="e8a84-128">Remarks</span></span>  
 <span data-ttu-id="e8a84-129">CLR 會呼叫`CreateRWLockReaderEvent`以取得參考`IHostManualEvent`在它的讀取器鎖定的實作中使用的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e8a84-129">The CLR calls `CreateRWLockReaderEvent` to get a reference to an `IHostManualEvent` instance to use in its implementation of a reader lock.</span></span> <span data-ttu-id="e8a84-130">主機可以使用 cookie，以判斷哪些工作正在等候讀取器鎖定上藉由查詢[ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="e8a84-130">The host can use the cookie to determine which tasks are waiting on the reader lock by querying the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8a84-131">需求</span><span class="sxs-lookup"><span data-stu-id="e8a84-131">Requirements</span></span>  
 <span data-ttu-id="e8a84-132">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e8a84-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8a84-133">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e8a84-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e8a84-134">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e8a84-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e8a84-135">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8a84-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8a84-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8a84-136">See also</span></span>
- [<span data-ttu-id="e8a84-137">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="e8a84-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="e8a84-138">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="e8a84-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="e8a84-139">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="e8a84-139">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="e8a84-140">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="e8a84-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
