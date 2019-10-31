---
title: ICLRSyncManager::GetRWLockOwnerNext 方法
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.GetRWLockOwnerNext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::GetRWLockOwnerNext
helpviewer_keywords:
- ICLRSyncManager::GetRWLockOwnerNext method [.NET Framework hosting]
- GetRWLockOwnerNext method [.NET Framework hosting]
ms.assetid: 0e025b6a-280e-40a2-a2d0-b15f58777b81
topic_type:
- apiref
ms.openlocfilehash: 860a818b08cb88b0fa17adccdfac5c81c0ec502c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130566"
---
# <a name="iclrsyncmanagergetrwlockownernext-method"></a><span data-ttu-id="86c29-102">ICLRSyncManager::GetRWLockOwnerNext 方法</span><span class="sxs-lookup"><span data-stu-id="86c29-102">ICLRSyncManager::GetRWLockOwnerNext Method</span></span>
<span data-ttu-id="86c29-103">取得目前讀取器寫入器鎖定上封鎖的下一個[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)實例。</span><span class="sxs-lookup"><span data-stu-id="86c29-103">Gets the next [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that is blocked on the current reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86c29-104">語法</span><span class="sxs-lookup"><span data-stu-id="86c29-104">Syntax</span></span>  
  
```cpp
HRESULT GetRWLockOwnerNext (  
    [in] SIZE_T       Iterator,  
    [out] IHostTask  *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86c29-105">參數</span><span class="sxs-lookup"><span data-stu-id="86c29-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="86c29-106">在使用[CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md)的呼叫所建立的反覆運算器。</span><span class="sxs-lookup"><span data-stu-id="86c29-106">[in] The iterator that was created by using a call to [CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="86c29-107">脫銷正在等候鎖定的下一個 `IHostTask` 的指標，如果沒有任何工作正在等候，則為 null。</span><span class="sxs-lookup"><span data-stu-id="86c29-107">[out] A pointer to the next `IHostTask` that is waiting on the lock, or null if no task is waiting.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86c29-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="86c29-108">Return Value</span></span>  
  
|<span data-ttu-id="86c29-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="86c29-109">HRESULT</span></span>|<span data-ttu-id="86c29-110">描述</span><span class="sxs-lookup"><span data-stu-id="86c29-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="86c29-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="86c29-111">S_OK</span></span>|<span data-ttu-id="86c29-112">已成功傳回 `GetRWLockOwnerNext`。</span><span class="sxs-lookup"><span data-stu-id="86c29-112">`GetRWLockOwnerNext` returned successfully.</span></span>|  
|<span data-ttu-id="86c29-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="86c29-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="86c29-114">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="86c29-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="86c29-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="86c29-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="86c29-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="86c29-116">The call timed out.</span></span>|  
|<span data-ttu-id="86c29-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="86c29-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="86c29-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="86c29-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="86c29-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="86c29-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="86c29-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="86c29-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="86c29-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="86c29-121">E_FAIL</span></span>|<span data-ttu-id="86c29-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="86c29-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="86c29-123">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="86c29-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="86c29-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="86c29-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86c29-125">備註</span><span class="sxs-lookup"><span data-stu-id="86c29-125">Remarks</span></span>  
 <span data-ttu-id="86c29-126">如果 `ppOwnerHostTask` 設定為 null，則反復專案會終止，而且主機應該呼叫[DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="86c29-126">If `ppOwnerHostTask` is set to null, the iteration has terminated, and the host should call the [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="86c29-127">CLR 會呼叫 `ppOwnerHostTask` 指向的 `IHostTask` `AddRef`，以便在主機保留指標時，防止此工作結束。</span><span class="sxs-lookup"><span data-stu-id="86c29-127">The CLR calls `AddRef` on the `IHostTask` to which `ppOwnerHostTask` points to prevent this task from exiting while the host holds the pointer.</span></span> <span data-ttu-id="86c29-128">主機必須呼叫 `Release`，以在完成時遞減參考計數。</span><span class="sxs-lookup"><span data-stu-id="86c29-128">The host must call `Release` to decrement the reference count when it is finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86c29-129">需求</span><span class="sxs-lookup"><span data-stu-id="86c29-129">Requirements</span></span>  
 <span data-ttu-id="86c29-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="86c29-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86c29-131">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="86c29-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="86c29-132">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="86c29-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="86c29-133">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86c29-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86c29-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="86c29-134">See also</span></span>

- [<span data-ttu-id="86c29-135">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="86c29-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="86c29-136">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="86c29-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
