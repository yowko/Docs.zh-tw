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
ms.openlocfilehash: 450530baed850a66327c4b1326c399529b3de67d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64630605"
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a><span data-ttu-id="e42e7-102">ICLRSyncManager::CreateRWLockOwnerIterator 方法</span><span class="sxs-lookup"><span data-stu-id="e42e7-102">ICLRSyncManager::CreateRWLockOwnerIterator Method</span></span>
<span data-ttu-id="e42e7-103">Common language runtime (CLR) 建立迭代器，用來判斷一組工作正在等候讀取器-寫入器鎖定主機的要求。</span><span class="sxs-lookup"><span data-stu-id="e42e7-103">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e42e7-104">語法</span><span class="sxs-lookup"><span data-stu-id="e42e7-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e42e7-105">參數</span><span class="sxs-lookup"><span data-stu-id="e42e7-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="e42e7-106">[in]使用所需的讀取器-寫入器鎖定相關聯的 cookie。</span><span class="sxs-lookup"><span data-stu-id="e42e7-106">[in] The cookie associated with the desired reader-writer lock.</span></span>  
  
 `pIterator`  
 <span data-ttu-id="e42e7-107">[out]指標迭代器可以傳遞給[GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md)並[DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="e42e7-107">[out] A pointer to an iterator that can be passed to the [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) and [DeleteRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e42e7-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="e42e7-108">Return Value</span></span>  
  
|<span data-ttu-id="e42e7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e42e7-109">HRESULT</span></span>|<span data-ttu-id="e42e7-110">描述</span><span class="sxs-lookup"><span data-stu-id="e42e7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e42e7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e42e7-111">S_OK</span></span>|<span data-ttu-id="e42e7-112">`CreateRWLockOwnerIterator` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="e42e7-112">`CreateRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="e42e7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e42e7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e42e7-114">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="e42e7-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e42e7-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e42e7-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e42e7-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="e42e7-116">The call timed out.</span></span>|  
|<span data-ttu-id="e42e7-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e42e7-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e42e7-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="e42e7-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e42e7-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e42e7-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e42e7-120">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="e42e7-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e42e7-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e42e7-121">E_FAIL</span></span>|<span data-ttu-id="e42e7-122">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="e42e7-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e42e7-123">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="e42e7-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e42e7-124">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="e42e7-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e42e7-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="e42e7-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="e42e7-126">`CreateRWLockOwnerIterator` 目前正在執行的 managed 程式碼的執行緒上呼叫。</span><span class="sxs-lookup"><span data-stu-id="e42e7-126">`CreateRWLockOwnerIterator` was called on a thread that is currently running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e42e7-127">備註</span><span class="sxs-lookup"><span data-stu-id="e42e7-127">Remarks</span></span>  
 <span data-ttu-id="e42e7-128">主機通常會呼叫`CreateRWLockOwnerIterator`， `DeleteRWLockOwnerIterator`，和`GetRWLockOwnerNext`死結偵測期間的方法。</span><span class="sxs-lookup"><span data-stu-id="e42e7-128">Hosts typically call the `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, and `GetRWLockOwnerNext` methods during deadlock detection.</span></span> <span data-ttu-id="e42e7-129">主應用程式會負責確保 reader-writer 鎖定仍然有效，因為 CLR 並不會嘗試維持 reader-writer 鎖定。</span><span class="sxs-lookup"><span data-stu-id="e42e7-129">The host is responsible for ensuring that the reader-writer lock is still valid, because the CLR makes no attempt to keep the reader-writer lock alive.</span></span> <span data-ttu-id="e42e7-130">數種策略可供主應用程式，以確保有效性的鎖定：</span><span class="sxs-lookup"><span data-stu-id="e42e7-130">Several strategies are available for the host to ensure the validity of the lock:</span></span>  
  
- <span data-ttu-id="e42e7-131">主應用程式可能會封鎖讀取器-寫入器鎖定上發行的呼叫 (例如[ihostsemaphore:: Releasesemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) 同時確保此區塊不會造成死結。</span><span class="sxs-lookup"><span data-stu-id="e42e7-131">The host can block release calls on the reader-writer lock (for example, [IHostSemaphore::ReleaseSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) while ensuring that this block does not cause deadlock.</span></span>  
  
- <span data-ttu-id="e42e7-132">主機可以封鎖等候讀取器-寫入器鎖定相關聯的事件物件上的結束，確定此區塊不會造成死結。</span><span class="sxs-lookup"><span data-stu-id="e42e7-132">The host can block the exit from waiting on the event object associated with the reader-writer lock, again ensuring that this block does not cause deadlock.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e42e7-133">`CreateRWLockOwnerIterator` 必須只能在目前正在執行 unmanaged 程式碼的執行緒上呼叫。</span><span class="sxs-lookup"><span data-stu-id="e42e7-133">`CreateRWLockOwnerIterator` must be called only on threads that are currently executing unmanaged code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e42e7-134">需求</span><span class="sxs-lookup"><span data-stu-id="e42e7-134">Requirements</span></span>  
 <span data-ttu-id="e42e7-135">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e42e7-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e42e7-136">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e42e7-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e42e7-137">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e42e7-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e42e7-138">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e42e7-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e42e7-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e42e7-139">See also</span></span>

- [<span data-ttu-id="e42e7-140">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="e42e7-140">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="e42e7-141">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="e42e7-141">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
