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
ms.openlocfilehash: 9eace3e7330d3f8c0c9762e0b1b456ad1bf8a3ac
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763185"
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a><span data-ttu-id="a65aa-102">ICLRSyncManager::CreateRWLockOwnerIterator 方法</span><span class="sxs-lookup"><span data-stu-id="a65aa-102">ICLRSyncManager::CreateRWLockOwnerIterator Method</span></span>
<span data-ttu-id="a65aa-103">要求 common language runtime （CLR）為主機建立反覆運算器，以用來判斷等候讀取器寫入器鎖定的一組工作。</span><span class="sxs-lookup"><span data-stu-id="a65aa-103">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a65aa-104">語法</span><span class="sxs-lookup"><span data-stu-id="a65aa-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a65aa-105">參數</span><span class="sxs-lookup"><span data-stu-id="a65aa-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="a65aa-106">在與所需讀取器寫入器鎖定相關聯的 cookie。</span><span class="sxs-lookup"><span data-stu-id="a65aa-106">[in] The cookie associated with the desired reader-writer lock.</span></span>  
  
 `pIterator`  
 <span data-ttu-id="a65aa-107">脫銷可傳遞至[GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md)和[DeleteRWLockOwnerIterator](iclrsyncmanager-deleterwlockowneriterator-method.md)方法之反覆運算器的指標。</span><span class="sxs-lookup"><span data-stu-id="a65aa-107">[out] A pointer to an iterator that can be passed to the [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) and [DeleteRWLockOwnerIterator](iclrsyncmanager-deleterwlockowneriterator-method.md) methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a65aa-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="a65aa-108">Return Value</span></span>  
  
|<span data-ttu-id="a65aa-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a65aa-109">HRESULT</span></span>|<span data-ttu-id="a65aa-110">Description</span><span class="sxs-lookup"><span data-stu-id="a65aa-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a65aa-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a65aa-111">S_OK</span></span>|<span data-ttu-id="a65aa-112">`CreateRWLockOwnerIterator`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="a65aa-112">`CreateRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="a65aa-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a65aa-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a65aa-114">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="a65aa-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a65aa-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a65aa-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a65aa-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="a65aa-116">The call timed out.</span></span>|  
|<span data-ttu-id="a65aa-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a65aa-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a65aa-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="a65aa-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a65aa-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a65aa-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a65aa-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="a65aa-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a65aa-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a65aa-121">E_FAIL</span></span>|<span data-ttu-id="a65aa-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="a65aa-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a65aa-123">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="a65aa-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a65aa-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a65aa-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a65aa-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="a65aa-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="a65aa-126">`CreateRWLockOwnerIterator`在目前正在執行 managed 程式碼的執行緒上呼叫。</span><span class="sxs-lookup"><span data-stu-id="a65aa-126">`CreateRWLockOwnerIterator` was called on a thread that is currently running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a65aa-127">備註</span><span class="sxs-lookup"><span data-stu-id="a65aa-127">Remarks</span></span>  
 <span data-ttu-id="a65aa-128">主機通常會 `CreateRWLockOwnerIterator` `DeleteRWLockOwnerIterator` `GetRWLockOwnerNext` 在偵測到鎖死時呼叫、和方法。</span><span class="sxs-lookup"><span data-stu-id="a65aa-128">Hosts typically call the `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, and `GetRWLockOwnerNext` methods during deadlock detection.</span></span> <span data-ttu-id="a65aa-129">主機負責確保讀取器寫入器的鎖定仍然有效，因為 CLR 不會嘗試讓讀取器寫入器鎖定保持運作。</span><span class="sxs-lookup"><span data-stu-id="a65aa-129">The host is responsible for ensuring that the reader-writer lock is still valid, because the CLR makes no attempt to keep the reader-writer lock alive.</span></span> <span data-ttu-id="a65aa-130">有數個策略可供主機使用，以確保鎖定的有效性：</span><span class="sxs-lookup"><span data-stu-id="a65aa-130">Several strategies are available for the host to ensure the validity of the lock:</span></span>  
  
- <span data-ttu-id="a65aa-131">主機可以封鎖讀取器寫入器鎖定（例如， [IHostSemaphore：： ReleaseSemaphore](ihostsemaphore-releasesemaphore-method.md)）的發行呼叫，同時確保此區塊不會造成鎖死。</span><span class="sxs-lookup"><span data-stu-id="a65aa-131">The host can block release calls on the reader-writer lock (for example, [IHostSemaphore::ReleaseSemaphore](ihostsemaphore-releasesemaphore-method.md)) while ensuring that this block does not cause deadlock.</span></span>  
  
- <span data-ttu-id="a65aa-132">主機可以封鎖在與讀取器寫入器鎖定相關聯的事件物件上等待結束，再次確保此區塊不會造成鎖死。</span><span class="sxs-lookup"><span data-stu-id="a65aa-132">The host can block the exit from waiting on the event object associated with the reader-writer lock, again ensuring that this block does not cause deadlock.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a65aa-133">`CreateRWLockOwnerIterator`必須只在目前執行非受控碼的執行緒上呼叫。</span><span class="sxs-lookup"><span data-stu-id="a65aa-133">`CreateRWLockOwnerIterator` must be called only on threads that are currently executing unmanaged code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a65aa-134">規格需求</span><span class="sxs-lookup"><span data-stu-id="a65aa-134">Requirements</span></span>  
 <span data-ttu-id="a65aa-135">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a65aa-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a65aa-136">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="a65aa-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a65aa-137">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a65aa-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a65aa-138">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a65aa-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a65aa-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a65aa-139">See also</span></span>

- [<span data-ttu-id="a65aa-140">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="a65aa-140">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="a65aa-141">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="a65aa-141">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
