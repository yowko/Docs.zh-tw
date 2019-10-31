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
ms.openlocfilehash: 64cf6c80ab1cf4b3ca52c60d6e72b54c438f9f4a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195843"
---
# <a name="ihostsyncmanagercreaterwlockreaderevent-method"></a><span data-ttu-id="3cc45-102">IHostSyncManager::CreateRWLockReaderEvent 方法</span><span class="sxs-lookup"><span data-stu-id="3cc45-102">IHostSyncManager::CreateRWLockReaderEvent Method</span></span>
<span data-ttu-id="3cc45-103">建立手動重設的事件物件，以執行讀取器鎖定。</span><span class="sxs-lookup"><span data-stu-id="3cc45-103">Creates a manual-reset event object for the implementation of a reader lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cc45-104">語法</span><span class="sxs-lookup"><span data-stu-id="3cc45-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockReaderEvent (  
    [in]  BOOL bInitialState,  
    [in]  SIZE_T cookie,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3cc45-105">參數</span><span class="sxs-lookup"><span data-stu-id="3cc45-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="3cc45-106">[in] `true`，如果 `ppEvent` 應該收到信號，則為，否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="3cc45-106">[in] `true`, if `ppEvent` should be signaled; otherwise, `false`.</span></span>  
  
 `cookie`  
 <span data-ttu-id="3cc45-107">在與讀取器鎖定相關聯的 cookie。</span><span class="sxs-lookup"><span data-stu-id="3cc45-107">[in] A cookie to associate with the reader lock.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="3cc45-108">脫銷[IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)實例位址的指標，如果無法建立事件物件則為 null。</span><span class="sxs-lookup"><span data-stu-id="3cc45-108">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3cc45-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="3cc45-109">Return Value</span></span>  
  
|<span data-ttu-id="3cc45-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3cc45-110">HRESULT</span></span>|<span data-ttu-id="3cc45-111">描述</span><span class="sxs-lookup"><span data-stu-id="3cc45-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3cc45-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="3cc45-112">S_OK</span></span>|<span data-ttu-id="3cc45-113">已成功傳回 `CreateRWLockReaderEvent`。</span><span class="sxs-lookup"><span data-stu-id="3cc45-113">`CreateRWLockReaderEvent` returned successfully.</span></span>|  
|<span data-ttu-id="3cc45-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3cc45-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3cc45-115">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="3cc45-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3cc45-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3cc45-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3cc45-117">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="3cc45-117">The call timed out.</span></span>|  
|<span data-ttu-id="3cc45-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3cc45-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3cc45-119">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="3cc45-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3cc45-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3cc45-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3cc45-121">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="3cc45-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3cc45-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3cc45-122">E_FAIL</span></span>|<span data-ttu-id="3cc45-123">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="3cc45-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3cc45-124">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="3cc45-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3cc45-125">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="3cc45-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3cc45-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="3cc45-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="3cc45-127">沒有足夠的記憶體可用來建立要求的事件物件。</span><span class="sxs-lookup"><span data-stu-id="3cc45-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3cc45-128">備註</span><span class="sxs-lookup"><span data-stu-id="3cc45-128">Remarks</span></span>  
 <span data-ttu-id="3cc45-129">CLR 會呼叫 `CreateRWLockReaderEvent` 來取得 `IHostManualEvent` 實例的參考，以在其讀取器鎖定的執行中使用。</span><span class="sxs-lookup"><span data-stu-id="3cc45-129">The CLR calls `CreateRWLockReaderEvent` to get a reference to an `IHostManualEvent` instance to use in its implementation of a reader lock.</span></span> <span data-ttu-id="3cc45-130">主機可以使用 cookie，藉由查詢[ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)介面來判斷哪些工作正在等候讀取器鎖定。</span><span class="sxs-lookup"><span data-stu-id="3cc45-130">The host can use the cookie to determine which tasks are waiting on the reader lock by querying the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cc45-131">需求</span><span class="sxs-lookup"><span data-stu-id="3cc45-131">Requirements</span></span>  
 <span data-ttu-id="3cc45-132">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3cc45-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cc45-133">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="3cc45-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3cc45-134">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3cc45-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3cc45-135">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cc45-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cc45-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="3cc45-136">See also</span></span>

- [<span data-ttu-id="3cc45-137">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="3cc45-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="3cc45-138">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="3cc45-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="3cc45-139">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="3cc45-139">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="3cc45-140">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="3cc45-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
