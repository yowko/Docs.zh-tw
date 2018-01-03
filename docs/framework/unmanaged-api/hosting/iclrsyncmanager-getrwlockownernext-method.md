---
title: "ICLRSyncManager::GetRWLockOwnerNext 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRSyncManager.GetRWLockOwnerNext
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRSyncManager::GetRWLockOwnerNext
helpviewer_keywords:
- ICLRSyncManager::GetRWLockOwnerNext method [.NET Framework hosting]
- GetRWLockOwnerNext method [.NET Framework hosting]
ms.assetid: 0e025b6a-280e-40a2-a2d0-b15f58777b81
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1181cbb71aa30281fbff634354162e1f245d05fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrsyncmanagergetrwlockownernext-method"></a><span data-ttu-id="f0d34-102">ICLRSyncManager::GetRWLockOwnerNext 方法</span><span class="sxs-lookup"><span data-stu-id="f0d34-102">ICLRSyncManager::GetRWLockOwnerNext Method</span></span>
<span data-ttu-id="f0d34-103">取得下一個[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)便被封鎖於目前的讀取器-寫入器鎖定的執行個體。</span><span class="sxs-lookup"><span data-stu-id="f0d34-103">Gets the next [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that is blocked on the current reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0d34-104">語法</span><span class="sxs-lookup"><span data-stu-id="f0d34-104">Syntax</span></span>  
  
```  
HRESULT GetRWLockOwnerNext (  
    [in] SIZE_T       Iterator,  
    [out] IHostTask  *ppOwnerHostTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f0d34-105">參數</span><span class="sxs-lookup"><span data-stu-id="f0d34-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="f0d34-106">[in]使用呼叫所建立的迭代器[CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md)。</span><span class="sxs-lookup"><span data-stu-id="f0d34-106">[in] The iterator that was created by using a call to [CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="f0d34-107">[out]下一個指標`IHostTask`，正在等候的鎖定或為 null 如果沒有工作正在等候。</span><span class="sxs-lookup"><span data-stu-id="f0d34-107">[out] A pointer to the next `IHostTask` that is waiting on the lock, or null if no task is waiting.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f0d34-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="f0d34-108">Return Value</span></span>  
  
|<span data-ttu-id="f0d34-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f0d34-109">HRESULT</span></span>|<span data-ttu-id="f0d34-110">描述</span><span class="sxs-lookup"><span data-stu-id="f0d34-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f0d34-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f0d34-111">S_OK</span></span>|<span data-ttu-id="f0d34-112">`GetRWLockOwnerNext`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="f0d34-112">`GetRWLockOwnerNext` returned successfully.</span></span>|  
|<span data-ttu-id="f0d34-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f0d34-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f0d34-114">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="f0d34-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f0d34-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f0d34-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f0d34-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="f0d34-116">The call timed out.</span></span>|  
|<span data-ttu-id="f0d34-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f0d34-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f0d34-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="f0d34-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f0d34-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f0d34-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f0d34-120">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="f0d34-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f0d34-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f0d34-121">E_FAIL</span></span>|<span data-ttu-id="f0d34-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="f0d34-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f0d34-123">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="f0d34-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f0d34-124">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="f0d34-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0d34-125">備註</span><span class="sxs-lookup"><span data-stu-id="f0d34-125">Remarks</span></span>  
 <span data-ttu-id="f0d34-126">如果`ppOwnerHostTask`設為 null，將已終止反覆項目，且主應用程式應該呼叫[DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="f0d34-126">If `ppOwnerHostTask` is set to null, the iteration has terminated, and the host should call the [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f0d34-127">CLR 會呼叫`AddRef`上`IHostTask`的`ppOwnerHostTask`點，以防止這項工作結束時的主機保留的指標。</span><span class="sxs-lookup"><span data-stu-id="f0d34-127">The CLR calls `AddRef` on the `IHostTask` to which `ppOwnerHostTask` points to prevent this task from exiting while the host holds the pointer.</span></span> <span data-ttu-id="f0d34-128">主機必須呼叫`Release`遞減參考計數，在完成時。</span><span class="sxs-lookup"><span data-stu-id="f0d34-128">The host must call `Release` to decrement the reference count when it is finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0d34-129">需求</span><span class="sxs-lookup"><span data-stu-id="f0d34-129">Requirements</span></span>  
 <span data-ttu-id="f0d34-130">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f0d34-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0d34-131">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f0d34-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f0d34-132">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f0d34-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0d34-133">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0d34-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0d34-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="f0d34-134">See Also</span></span>  
 [<span data-ttu-id="f0d34-135">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="f0d34-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="f0d34-136">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="f0d34-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
