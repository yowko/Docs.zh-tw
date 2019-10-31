---
title: IHostSyncManager 介面
ms.date: 03/30/2017
api_name:
- IHostSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager
helpviewer_keywords:
- IHostSyncManager interface [.NET Framework hosting]
ms.assetid: 2e081a37-6a28-4c93-b7ab-1c96a464637c
topic_type:
- apiref
ms.openlocfilehash: 02a59b8ef63f7e866e419db4e3232da7eec19558
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132634"
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="82631-102">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="82631-102">IHostSyncManager Interface</span></span>
<span data-ttu-id="82631-103">提供的方法可讓 common language runtime （CLR）藉由呼叫主機來建立同步處理原始物件，而不是使用 Win32 同步處理函式。</span><span class="sxs-lookup"><span data-stu-id="82631-103">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="82631-104">方法</span><span class="sxs-lookup"><span data-stu-id="82631-104">Methods</span></span>  
  
|<span data-ttu-id="82631-105">方法</span><span class="sxs-lookup"><span data-stu-id="82631-105">Method</span></span>|<span data-ttu-id="82631-106">描述</span><span class="sxs-lookup"><span data-stu-id="82631-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="82631-107">CreateAutoEvent 方法</span><span class="sxs-lookup"><span data-stu-id="82631-107">CreateAutoEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="82631-108">建立自動重設事件物件。</span><span class="sxs-lookup"><span data-stu-id="82631-108">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="82631-109">CreateCrst 方法</span><span class="sxs-lookup"><span data-stu-id="82631-109">CreateCrst Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="82631-110">建立同步處理的重要區段物件。</span><span class="sxs-lookup"><span data-stu-id="82631-110">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="82631-111">CreateCrstWithSpinCount 方法</span><span class="sxs-lookup"><span data-stu-id="82631-111">CreateCrstWithSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="82631-112">使用微調計數來建立重要區段物件，以進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="82631-112">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="82631-113">CreateManualEvent 方法</span><span class="sxs-lookup"><span data-stu-id="82631-113">CreateManualEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="82631-114">建立手動重設事件物件。</span><span class="sxs-lookup"><span data-stu-id="82631-114">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="82631-115">CreateMonitorEvent 方法</span><span class="sxs-lookup"><span data-stu-id="82631-115">CreateMonitorEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="82631-116">建立受監視的自動重設事件物件。</span><span class="sxs-lookup"><span data-stu-id="82631-116">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="82631-117">CreateRWLockReaderEvent 方法</span><span class="sxs-lookup"><span data-stu-id="82631-117">CreateRWLockReaderEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="82631-118">建立手動重設的事件物件，以執行讀取器鎖定。</span><span class="sxs-lookup"><span data-stu-id="82631-118">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="82631-119">CreateRWLockWriterEvent 方法</span><span class="sxs-lookup"><span data-stu-id="82631-119">CreateRWLockWriterEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="82631-120">建立自動重設事件物件，以執行寫入器鎖定。</span><span class="sxs-lookup"><span data-stu-id="82631-120">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="82631-121">CreateSemaphore 方法</span><span class="sxs-lookup"><span data-stu-id="82631-121">CreateSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="82631-122">建立[IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)物件，以供 CLR 用來做為等候事件的信號。</span><span class="sxs-lookup"><span data-stu-id="82631-122">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="82631-123">SetCLRSyncManager 方法</span><span class="sxs-lookup"><span data-stu-id="82631-123">SetCLRSyncManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="82631-124">設定要與目前 `IHostSyncManager` 實例相關聯的[ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)實例。</span><span class="sxs-lookup"><span data-stu-id="82631-124">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82631-125">備註</span><span class="sxs-lookup"><span data-stu-id="82631-125">Remarks</span></span>  
 <span data-ttu-id="82631-126">CLR 會藉由呼叫[IHostControl：： GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)方法與 IID_IHostSyncManager 的 `IID`，來探索主機的 `IHostSyncManager` 的執行。</span><span class="sxs-lookup"><span data-stu-id="82631-126">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82631-127">需求</span><span class="sxs-lookup"><span data-stu-id="82631-127">Requirements</span></span>  
 <span data-ttu-id="82631-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="82631-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82631-129">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="82631-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="82631-130">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="82631-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="82631-131">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82631-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82631-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="82631-132">See also</span></span>

- [<span data-ttu-id="82631-133">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="82631-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="82631-134">裝載介面</span><span class="sxs-lookup"><span data-stu-id="82631-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
