---
title: ICLRSyncManager::CreateRWLockOwnerIterator 方法
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.CreateRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator method [.NET Framework hosting]
- CreateRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: b5535b87-9439-424e-b9b3-7d6fafb9819e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eda20543c28a7b97979463928ce307df9b830103
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436016"
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a><span data-ttu-id="38b9c-102">ICLRSyncManager::CreateRWLockOwnerIterator 方法</span><span class="sxs-lookup"><span data-stu-id="38b9c-102">ICLRSyncManager::CreateRWLockOwnerIterator Method</span></span>
<span data-ttu-id="38b9c-103">Common language runtime (CLR) 建立的主機可用來判斷一組工作正在等候讀取器-寫入器鎖定之迭代器的要求。</span><span class="sxs-lookup"><span data-stu-id="38b9c-103">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38b9c-104">語法</span><span class="sxs-lookup"><span data-stu-id="38b9c-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="38b9c-105">參數</span><span class="sxs-lookup"><span data-stu-id="38b9c-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="38b9c-106">[in]與所需的讀取器-寫入器鎖定相關聯的 cookie。</span><span class="sxs-lookup"><span data-stu-id="38b9c-106">[in] The cookie associated with the desired reader-writer lock.</span></span>  
  
 `pIterator`  
 <span data-ttu-id="38b9c-107">[out]指標迭代器可以傳遞至[GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md)和[DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="38b9c-107">[out] A pointer to an iterator that can be passed to the [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) and [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38b9c-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="38b9c-108">Return Value</span></span>  
  
|<span data-ttu-id="38b9c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="38b9c-109">HRESULT</span></span>|<span data-ttu-id="38b9c-110">描述</span><span class="sxs-lookup"><span data-stu-id="38b9c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="38b9c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="38b9c-111">S_OK</span></span>|<span data-ttu-id="38b9c-112">`CreateRWLockOwnerIterator` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="38b9c-112">`CreateRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="38b9c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="38b9c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="38b9c-114">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="38b9c-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="38b9c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="38b9c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="38b9c-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="38b9c-116">The call timed out.</span></span>|  
|<span data-ttu-id="38b9c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="38b9c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="38b9c-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="38b9c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="38b9c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="38b9c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="38b9c-120">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="38b9c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="38b9c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="38b9c-121">E_FAIL</span></span>|<span data-ttu-id="38b9c-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="38b9c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="38b9c-123">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="38b9c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="38b9c-124">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="38b9c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="38b9c-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="38b9c-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="38b9c-126">`CreateRWLockOwnerIterator` 目前正在執行 managed 程式碼的執行緒上呼叫。</span><span class="sxs-lookup"><span data-stu-id="38b9c-126">`CreateRWLockOwnerIterator` was called on a thread that is currently running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38b9c-127">備註</span><span class="sxs-lookup"><span data-stu-id="38b9c-127">Remarks</span></span>  
 <span data-ttu-id="38b9c-128">主機通常會呼叫`CreateRWLockOwnerIterator`， `DeleteRWLockOwnerIterator`，和`GetRWLockOwnerNext`期間死結偵測的方法。</span><span class="sxs-lookup"><span data-stu-id="38b9c-128">Hosts typically call the `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, and `GetRWLockOwnerNext` methods during deadlock detection.</span></span> <span data-ttu-id="38b9c-129">主機負責確保，讀取器-寫入器鎖定仍然有效，因為 CLR 不會嘗試讓讀取器-寫入器的鎖定保持運作。</span><span class="sxs-lookup"><span data-stu-id="38b9c-129">The host is responsible for ensuring that the reader-writer lock is still valid, because the CLR makes no attempt to keep the reader-writer lock alive.</span></span> <span data-ttu-id="38b9c-130">數個策略就可供主機用來確定有效性的鎖定：</span><span class="sxs-lookup"><span data-stu-id="38b9c-130">Several strategies are available for the host to ensure the validity of the lock:</span></span>  
  
-   <span data-ttu-id="38b9c-131">主機可能會封鎖讀取器-寫入器鎖定上的釋出呼叫 (例如， [ihostsemaphore:: Releasesemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) 同時確保此區塊不會造成死結。</span><span class="sxs-lookup"><span data-stu-id="38b9c-131">The host can block release calls on the reader-writer lock (for example, [IHostSemaphore::ReleaseSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) while ensuring that this block does not cause deadlock.</span></span>  
  
-   <span data-ttu-id="38b9c-132">主機可以封鎖從讀取器-寫入器鎖定相關聯的事件物件上等候結束，確定此區塊不會造成死結。</span><span class="sxs-lookup"><span data-stu-id="38b9c-132">The host can block the exit from waiting on the event object associated with the reader-writer lock, again ensuring that this block does not cause deadlock.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38b9c-133">`CreateRWLockOwnerIterator` 必須只在目前正在執行 unmanaged 程式碼的執行緒上呼叫。</span><span class="sxs-lookup"><span data-stu-id="38b9c-133">`CreateRWLockOwnerIterator` must be called only on threads that are currently executing unmanaged code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38b9c-134">需求</span><span class="sxs-lookup"><span data-stu-id="38b9c-134">Requirements</span></span>  
 <span data-ttu-id="38b9c-135">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="38b9c-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38b9c-136">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="38b9c-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="38b9c-137">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="38b9c-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="38b9c-138">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38b9c-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38b9c-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38b9c-139">See Also</span></span>  
 [<span data-ttu-id="38b9c-140">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="38b9c-140">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="38b9c-141">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="38b9c-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
