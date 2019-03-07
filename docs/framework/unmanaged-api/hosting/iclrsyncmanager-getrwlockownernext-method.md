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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb91a49086eae4d9e8d43a2d38b51d9dd0a6814e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473720"
---
# <a name="iclrsyncmanagergetrwlockownernext-method"></a><span data-ttu-id="dbc6b-102">ICLRSyncManager::GetRWLockOwnerNext 方法</span><span class="sxs-lookup"><span data-stu-id="dbc6b-102">ICLRSyncManager::GetRWLockOwnerNext Method</span></span>
<span data-ttu-id="dbc6b-103">取得下一步[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)目前讀取器-寫入器鎖定遭到封鎖的執行個體。</span><span class="sxs-lookup"><span data-stu-id="dbc6b-103">Gets the next [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that is blocked on the current reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbc6b-104">語法</span><span class="sxs-lookup"><span data-stu-id="dbc6b-104">Syntax</span></span>  
  
```  
HRESULT GetRWLockOwnerNext (  
    [in] SIZE_T       Iterator,  
    [out] IHostTask  *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbc6b-105">參數</span><span class="sxs-lookup"><span data-stu-id="dbc6b-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="dbc6b-106">[in]使用呼叫所建立的迭代器[CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md)。</span><span class="sxs-lookup"><span data-stu-id="dbc6b-106">[in] The iterator that was created by using a call to [CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="dbc6b-107">[out]下一個指標`IHostTask`，正在等候鎖定，則為 null 如果沒有工作正在等候。</span><span class="sxs-lookup"><span data-stu-id="dbc6b-107">[out] A pointer to the next `IHostTask` that is waiting on the lock, or null if no task is waiting.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dbc6b-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="dbc6b-108">Return Value</span></span>  
  
|<span data-ttu-id="dbc6b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dbc6b-109">HRESULT</span></span>|<span data-ttu-id="dbc6b-110">描述</span><span class="sxs-lookup"><span data-stu-id="dbc6b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dbc6b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="dbc6b-111">S_OK</span></span>|<span data-ttu-id="dbc6b-112">`GetRWLockOwnerNext` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="dbc6b-112">`GetRWLockOwnerNext` returned successfully.</span></span>|  
|<span data-ttu-id="dbc6b-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dbc6b-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dbc6b-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="dbc6b-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dbc6b-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dbc6b-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dbc6b-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="dbc6b-116">The call timed out.</span></span>|  
|<span data-ttu-id="dbc6b-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dbc6b-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dbc6b-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="dbc6b-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dbc6b-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dbc6b-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dbc6b-120">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="dbc6b-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dbc6b-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dbc6b-121">E_FAIL</span></span>|<span data-ttu-id="dbc6b-122">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="dbc6b-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dbc6b-123">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="dbc6b-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dbc6b-124">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="dbc6b-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbc6b-125">備註</span><span class="sxs-lookup"><span data-stu-id="dbc6b-125">Remarks</span></span>  
 <span data-ttu-id="dbc6b-126">如果`ppOwnerHostTask`設為 null，將已終止反覆項目，而主應用程式應該呼叫[DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="dbc6b-126">If `ppOwnerHostTask` is set to null, the iteration has terminated, and the host should call the [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dbc6b-127">CLR 會呼叫`AddRef`上`IHostTask`要`ppOwnerHostTask`點，以防止這項工作結束時的主機保留的指標。</span><span class="sxs-lookup"><span data-stu-id="dbc6b-127">The CLR calls `AddRef` on the `IHostTask` to which `ppOwnerHostTask` points to prevent this task from exiting while the host holds the pointer.</span></span> <span data-ttu-id="dbc6b-128">主機必須呼叫`Release`完成後遞減參考計數。</span><span class="sxs-lookup"><span data-stu-id="dbc6b-128">The host must call `Release` to decrement the reference count when it is finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbc6b-129">需求</span><span class="sxs-lookup"><span data-stu-id="dbc6b-129">Requirements</span></span>  
 <span data-ttu-id="dbc6b-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dbc6b-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbc6b-131">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dbc6b-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dbc6b-132">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="dbc6b-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dbc6b-133">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbc6b-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbc6b-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbc6b-134">See also</span></span>
- [<span data-ttu-id="dbc6b-135">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="dbc6b-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="dbc6b-136">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="dbc6b-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
