---
title: IHostSyncManager::CreateRWLockWriterEvent 方法
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateRWLockWriterEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateRWLockWriterEvent
helpviewer_keywords:
- CreateRWLockWriterEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockWriterEvent method [.NET Framework hosting]
ms.assetid: 70e488c2-cf53-4dc0-ba52-74372d215c41
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1deff93744d1dec0ff7d6cab5bb6580f3a8fbad
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490043"
---
# <a name="ihostsyncmanagercreaterwlockwriterevent-method"></a><span data-ttu-id="e0a3c-102">IHostSyncManager::CreateRWLockWriterEvent 方法</span><span class="sxs-lookup"><span data-stu-id="e0a3c-102">IHostSyncManager::CreateRWLockWriterEvent Method</span></span>
<span data-ttu-id="e0a3c-103">建立自動重設事件物件的寫入器鎖定的實作。</span><span class="sxs-lookup"><span data-stu-id="e0a3c-103">Creates an auto-reset event object for the implementation of a writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0a3c-104">語法</span><span class="sxs-lookup"><span data-stu-id="e0a3c-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockWriterEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0a3c-105">參數</span><span class="sxs-lookup"><span data-stu-id="e0a3c-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="e0a3c-106">[in]自動重設事件相關聯的 cookie。</span><span class="sxs-lookup"><span data-stu-id="e0a3c-106">[in] A cookie to associate with the auto-reset event.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="e0a3c-107">[out]位址指標[IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)執行個體，或如果無法建立事件物件，則為 null。</span><span class="sxs-lookup"><span data-stu-id="e0a3c-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0a3c-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="e0a3c-108">Return Value</span></span>  
  
|<span data-ttu-id="e0a3c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e0a3c-109">HRESULT</span></span>|<span data-ttu-id="e0a3c-110">描述</span><span class="sxs-lookup"><span data-stu-id="e0a3c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e0a3c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e0a3c-111">S_OK</span></span>|<span data-ttu-id="e0a3c-112">`CreateRWLockWriterEvent` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="e0a3c-112">`CreateRWLockWriterEvent` returned successfully.</span></span>|  
|<span data-ttu-id="e0a3c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e0a3c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e0a3c-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="e0a3c-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e0a3c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e0a3c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e0a3c-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="e0a3c-116">The call timed out.</span></span>|  
|<span data-ttu-id="e0a3c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e0a3c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e0a3c-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="e0a3c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e0a3c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e0a3c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e0a3c-120">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="e0a3c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e0a3c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e0a3c-121">E_FAIL</span></span>|<span data-ttu-id="e0a3c-122">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="e0a3c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e0a3c-123">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="e0a3c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e0a3c-124">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="e0a3c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e0a3c-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="e0a3c-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="e0a3c-126">記憶體不足，無法建立要求的事件物件。</span><span class="sxs-lookup"><span data-stu-id="e0a3c-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0a3c-127">備註</span><span class="sxs-lookup"><span data-stu-id="e0a3c-127">Remarks</span></span>  
 <span data-ttu-id="e0a3c-128">CLR 會呼叫`CreateRWLockWriterEvent`方法來取得參考`IHostAutoEvent`寫入器鎖定的實作中使用的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e0a3c-128">The CLR calls the `CreateRWLockWriterEvent` method to get a reference to an `IHostAutoEvent` instance to use in its implementation of a writer lock.</span></span> <span data-ttu-id="e0a3c-129">主機可以使用指定的 cookie，以判斷哪些工作正在等候鎖定上藉由呼叫的反覆項目方法[ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="e0a3c-129">The host can use the specified cookie to determine which tasks are waiting on the lock by calling the iteration methods of the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0a3c-130">需求</span><span class="sxs-lookup"><span data-stu-id="e0a3c-130">Requirements</span></span>  
 <span data-ttu-id="e0a3c-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e0a3c-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0a3c-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e0a3c-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e0a3c-133">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e0a3c-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e0a3c-134">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0a3c-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0a3c-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0a3c-135">See also</span></span>
- [<span data-ttu-id="e0a3c-136">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="e0a3c-136">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="e0a3c-137">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="e0a3c-137">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="e0a3c-138">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="e0a3c-138">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="e0a3c-139">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="e0a3c-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
