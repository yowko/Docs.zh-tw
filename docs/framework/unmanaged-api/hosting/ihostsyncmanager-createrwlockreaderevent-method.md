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
ms.openlocfilehash: bb2a7a6650da03796628b647bc0b06174c576538
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="ihostsyncmanagercreaterwlockreaderevent-method"></a><span data-ttu-id="686c7-102">IHostSyncManager::CreateRWLockReaderEvent 方法</span><span class="sxs-lookup"><span data-stu-id="686c7-102">IHostSyncManager::CreateRWLockReaderEvent Method</span></span>
<span data-ttu-id="686c7-103">建立手動重設事件物件的讀取器鎖定的實作。</span><span class="sxs-lookup"><span data-stu-id="686c7-103">Creates a manual-reset event object for the implementation of a reader lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="686c7-104">語法</span><span class="sxs-lookup"><span data-stu-id="686c7-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockReaderEvent (  
    [in]  BOOL bInitialState,  
    [in]  SIZE_T cookie,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="686c7-105">參數</span><span class="sxs-lookup"><span data-stu-id="686c7-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="686c7-106">[in]`true`，如果`ppEvent`應該會收到信號，否則`false`。</span><span class="sxs-lookup"><span data-stu-id="686c7-106">[in] `true`, if `ppEvent` should be signaled; otherwise, `false`.</span></span>  
  
 `cookie`  
 <span data-ttu-id="686c7-107">[in]此 cookie 會與 讀取器鎖定。</span><span class="sxs-lookup"><span data-stu-id="686c7-107">[in] A cookie to associate with the reader lock.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="686c7-108">[out]位址指標[IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)執行個體，或如果無法建立事件物件則為 null。</span><span class="sxs-lookup"><span data-stu-id="686c7-108">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="686c7-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="686c7-109">Return Value</span></span>  
  
|<span data-ttu-id="686c7-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="686c7-110">HRESULT</span></span>|<span data-ttu-id="686c7-111">描述</span><span class="sxs-lookup"><span data-stu-id="686c7-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="686c7-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="686c7-112">S_OK</span></span>|<span data-ttu-id="686c7-113">`CreateRWLockReaderEvent` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="686c7-113">`CreateRWLockReaderEvent` returned successfully.</span></span>|  
|<span data-ttu-id="686c7-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="686c7-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="686c7-115">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="686c7-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="686c7-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="686c7-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="686c7-117">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="686c7-117">The call timed out.</span></span>|  
|<span data-ttu-id="686c7-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="686c7-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="686c7-119">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="686c7-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="686c7-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="686c7-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="686c7-121">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="686c7-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="686c7-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="686c7-122">E_FAIL</span></span>|<span data-ttu-id="686c7-123">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="686c7-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="686c7-124">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="686c7-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="686c7-125">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="686c7-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="686c7-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="686c7-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="686c7-127">沒有足夠的記憶體可用來建立要求的事件物件。</span><span class="sxs-lookup"><span data-stu-id="686c7-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="686c7-128">備註</span><span class="sxs-lookup"><span data-stu-id="686c7-128">Remarks</span></span>  
 <span data-ttu-id="686c7-129">CLR 會呼叫`CreateRWLockReaderEvent`取得參考`IHostManualEvent`執行個體將其實作的讀取器的鎖定。</span><span class="sxs-lookup"><span data-stu-id="686c7-129">The CLR calls `CreateRWLockReaderEvent` to get a reference to an `IHostManualEvent` instance to use in its implementation of a reader lock.</span></span> <span data-ttu-id="686c7-130">主機可以使用 cookie 來判斷哪些工作，藉由查詢正在等候讀取器鎖定[ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="686c7-130">The host can use the cookie to determine which tasks are waiting on the reader lock by querying the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="686c7-131">需求</span><span class="sxs-lookup"><span data-stu-id="686c7-131">Requirements</span></span>  
 <span data-ttu-id="686c7-132">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="686c7-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="686c7-133">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="686c7-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="686c7-134">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="686c7-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="686c7-135">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="686c7-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="686c7-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="686c7-136">See Also</span></span>  
 [<span data-ttu-id="686c7-137">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="686c7-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="686c7-138">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="686c7-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="686c7-139">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="686c7-139">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="686c7-140">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="686c7-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
