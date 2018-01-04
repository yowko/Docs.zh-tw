---
title: "IHostSyncManager 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager
helpviewer_keywords: IHostSyncManager interface [.NET Framework hosting]
ms.assetid: 2e081a37-6a28-4c93-b7ab-1c96a464637c
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b51e1dd9219c30eb4918bf1e331c96585f7c03ac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="dbde2-102">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="dbde2-102">IHostSyncManager Interface</span></span>
<span data-ttu-id="dbde2-103">提供方法讓 common language runtime (CLR) 呼叫主應用程式，而不是使用 Win32 同步處理函式來建立同步處理原始物件。</span><span class="sxs-lookup"><span data-stu-id="dbde2-103">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dbde2-104">方法</span><span class="sxs-lookup"><span data-stu-id="dbde2-104">Methods</span></span>  
  
|<span data-ttu-id="dbde2-105">方法</span><span class="sxs-lookup"><span data-stu-id="dbde2-105">Method</span></span>|<span data-ttu-id="dbde2-106">描述</span><span class="sxs-lookup"><span data-stu-id="dbde2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dbde2-107">CreateAutoEvent 方法</span><span class="sxs-lookup"><span data-stu-id="dbde2-107">CreateAutoEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="dbde2-108">建立的自動重設事件物件。</span><span class="sxs-lookup"><span data-stu-id="dbde2-108">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="dbde2-109">CreateCrst 方法</span><span class="sxs-lookup"><span data-stu-id="dbde2-109">CreateCrst Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="dbde2-110">建立關鍵區段進行同步處理物件。</span><span class="sxs-lookup"><span data-stu-id="dbde2-110">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="dbde2-111">CreateCrstWithSpinCount 方法</span><span class="sxs-lookup"><span data-stu-id="dbde2-111">CreateCrstWithSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="dbde2-112">建立關鍵區段物件具有微調計數進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="dbde2-112">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="dbde2-113">CreateManualEvent 方法</span><span class="sxs-lookup"><span data-stu-id="dbde2-113">CreateManualEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="dbde2-114">建立手動重設事件物件。</span><span class="sxs-lookup"><span data-stu-id="dbde2-114">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="dbde2-115">CreateMonitorEvent 方法</span><span class="sxs-lookup"><span data-stu-id="dbde2-115">CreateMonitorEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="dbde2-116">建立受監視的自動重設事件物件。</span><span class="sxs-lookup"><span data-stu-id="dbde2-116">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="dbde2-117">CreateRWLockReaderEvent 方法</span><span class="sxs-lookup"><span data-stu-id="dbde2-117">CreateRWLockReaderEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="dbde2-118">建立手動重設事件物件的讀取器鎖定的實作。</span><span class="sxs-lookup"><span data-stu-id="dbde2-118">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="dbde2-119">CreateRWLockWriterEvent 方法</span><span class="sxs-lookup"><span data-stu-id="dbde2-119">CreateRWLockWriterEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="dbde2-120">建立自動重設事件物件的寫入器鎖定的實作。</span><span class="sxs-lookup"><span data-stu-id="dbde2-120">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="dbde2-121">CreateSemaphore 方法</span><span class="sxs-lookup"><span data-stu-id="dbde2-121">CreateSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="dbde2-122">建立[IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)作為等候事件信號的 CLR 物件。</span><span class="sxs-lookup"><span data-stu-id="dbde2-122">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="dbde2-123">SetCLRSyncManager 方法</span><span class="sxs-lookup"><span data-stu-id="dbde2-123">SetCLRSyncManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="dbde2-124">設定[ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)與目前的執行個體`IHostSyncManager`執行個體。</span><span class="sxs-lookup"><span data-stu-id="dbde2-124">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbde2-125">備註</span><span class="sxs-lookup"><span data-stu-id="dbde2-125">Remarks</span></span>  
 <span data-ttu-id="dbde2-126">CLR 會探索主應用程式的實作`IHostSyncManager`藉由呼叫[ihostcontrol:: Gethostmanager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)方法`IID`IID_IHostSyncManager。</span><span class="sxs-lookup"><span data-stu-id="dbde2-126">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbde2-127">需求</span><span class="sxs-lookup"><span data-stu-id="dbde2-127">Requirements</span></span>  
 <span data-ttu-id="dbde2-128">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dbde2-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbde2-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dbde2-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dbde2-130">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="dbde2-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dbde2-131">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbde2-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbde2-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="dbde2-132">See Also</span></span>  
 [<span data-ttu-id="dbde2-133">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="dbde2-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="dbde2-134">裝載介面</span><span class="sxs-lookup"><span data-stu-id="dbde2-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
