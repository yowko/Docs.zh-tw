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
ms.openlocfilehash: 2b6a2082d27fca4c78dcb15a13cfd87e8066e388
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687212"
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a><span data-ttu-id="7471c-102">ICLRSyncManager::CreateRWLockOwnerIterator 方法</span><span class="sxs-lookup"><span data-stu-id="7471c-102">ICLRSyncManager::CreateRWLockOwnerIterator Method</span></span>

<span data-ttu-id="7471c-103">要求 common language runtime (CLR) 為主機建立反覆運算器，以用來判斷等候讀取器寫入器鎖定的工作集。</span><span class="sxs-lookup"><span data-stu-id="7471c-103">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7471c-104">語法</span><span class="sxs-lookup"><span data-stu-id="7471c-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7471c-105">參數</span><span class="sxs-lookup"><span data-stu-id="7471c-105">Parameters</span></span>  

 `cookie`  
 <span data-ttu-id="7471c-106">在與所需讀取器寫入器鎖定相關聯的 cookie。</span><span class="sxs-lookup"><span data-stu-id="7471c-106">[in] The cookie associated with the desired reader-writer lock.</span></span>  
  
 `pIterator`  
 <span data-ttu-id="7471c-107">擴展反覆運算器的指標，可傳遞至 [GetRWLockOwnerNext](iclrsyncmanager-getrwlockownernext-method.md) 和 [DeleteRWLockOwnerIterator](iclrsyncmanager-deleterwlockowneriterator-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="7471c-107">[out] A pointer to an iterator that can be passed to the [GetRWLockOwnerNext](iclrsyncmanager-getrwlockownernext-method.md) and [DeleteRWLockOwnerIterator](iclrsyncmanager-deleterwlockowneriterator-method.md) methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7471c-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="7471c-108">Return Value</span></span>  
  
|<span data-ttu-id="7471c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7471c-109">HRESULT</span></span>|<span data-ttu-id="7471c-110">描述</span><span class="sxs-lookup"><span data-stu-id="7471c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7471c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7471c-111">S_OK</span></span>|<span data-ttu-id="7471c-112">`CreateRWLockOwnerIterator` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="7471c-112">`CreateRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="7471c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7471c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7471c-114">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="7471c-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7471c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7471c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7471c-116">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="7471c-116">The call timed out.</span></span>|  
|<span data-ttu-id="7471c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7471c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7471c-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="7471c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7471c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7471c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7471c-120">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="7471c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7471c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7471c-121">E_FAIL</span></span>|<span data-ttu-id="7471c-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="7471c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7471c-123">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="7471c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7471c-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="7471c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7471c-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="7471c-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="7471c-126">`CreateRWLockOwnerIterator` 在目前正在執行 managed 程式碼的執行緒上呼叫。</span><span class="sxs-lookup"><span data-stu-id="7471c-126">`CreateRWLockOwnerIterator` was called on a thread that is currently running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7471c-127">備註</span><span class="sxs-lookup"><span data-stu-id="7471c-127">Remarks</span></span>  

 <span data-ttu-id="7471c-128">主機通常會 `CreateRWLockOwnerIterator` `DeleteRWLockOwnerIterator` `GetRWLockOwnerNext` 在進行鎖死偵測期間呼叫、和方法。</span><span class="sxs-lookup"><span data-stu-id="7471c-128">Hosts typically call the `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, and `GetRWLockOwnerNext` methods during deadlock detection.</span></span> <span data-ttu-id="7471c-129">主機會負責確保讀取器寫入器鎖定仍有效，因為 CLR 不會嘗試讓讀取器寫入器鎖定保持運作。</span><span class="sxs-lookup"><span data-stu-id="7471c-129">The host is responsible for ensuring that the reader-writer lock is still valid, because the CLR makes no attempt to keep the reader-writer lock alive.</span></span> <span data-ttu-id="7471c-130">主機提供數種策略，以確保鎖定的有效性：</span><span class="sxs-lookup"><span data-stu-id="7471c-130">Several strategies are available for the host to ensure the validity of the lock:</span></span>  
  
- <span data-ttu-id="7471c-131">主機可以封鎖讀取器-寫入器鎖定上的發行呼叫 (例如， [IHostSemaphore：： ReleaseSemaphore](ihostsemaphore-releasesemaphore-method.md)) ，同時確保此區塊不會造成鎖死。</span><span class="sxs-lookup"><span data-stu-id="7471c-131">The host can block release calls on the reader-writer lock (for example, [IHostSemaphore::ReleaseSemaphore](ihostsemaphore-releasesemaphore-method.md)) while ensuring that this block does not cause deadlock.</span></span>  
  
- <span data-ttu-id="7471c-132">主機可以封鎖離開與讀取器寫入器鎖定相關聯之事件物件的結束，再次確定這個區塊不會造成鎖死。</span><span class="sxs-lookup"><span data-stu-id="7471c-132">The host can block the exit from waiting on the event object associated with the reader-writer lock, again ensuring that this block does not cause deadlock.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7471c-133">`CreateRWLockOwnerIterator` 必須只在目前執行非受控碼的執行緒上呼叫。</span><span class="sxs-lookup"><span data-stu-id="7471c-133">`CreateRWLockOwnerIterator` must be called only on threads that are currently executing unmanaged code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7471c-134">需求</span><span class="sxs-lookup"><span data-stu-id="7471c-134">Requirements</span></span>  

 <span data-ttu-id="7471c-135">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7471c-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7471c-136">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="7471c-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7471c-137">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="7471c-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7471c-138">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7471c-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7471c-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7471c-139">See also</span></span>

- [<span data-ttu-id="7471c-140">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="7471c-140">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="7471c-141">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="7471c-141">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
