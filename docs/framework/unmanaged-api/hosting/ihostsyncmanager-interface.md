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
ms.openlocfilehash: 951f7808e238f514ffcf19a8dda0033b7b07172c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="b6cf7-102">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="b6cf7-102">IHostSyncManager Interface</span></span>
<span data-ttu-id="b6cf7-103">提供方法讓 common language runtime (CLR) 呼叫主應用程式，而不是使用 Win32 同步處理函式來建立同步處理原始物件。</span><span class="sxs-lookup"><span data-stu-id="b6cf7-103">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b6cf7-104">方法</span><span class="sxs-lookup"><span data-stu-id="b6cf7-104">Methods</span></span>  
  
|<span data-ttu-id="b6cf7-105">方法</span><span class="sxs-lookup"><span data-stu-id="b6cf7-105">Method</span></span>|<span data-ttu-id="b6cf7-106">說明</span><span class="sxs-lookup"><span data-stu-id="b6cf7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b6cf7-107">CreateAutoEvent 方法</span><span class="sxs-lookup"><span data-stu-id="b6cf7-107">CreateAutoEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="b6cf7-108">建立的自動重設事件物件。</span><span class="sxs-lookup"><span data-stu-id="b6cf7-108">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="b6cf7-109">CreateCrst 方法</span><span class="sxs-lookup"><span data-stu-id="b6cf7-109">CreateCrst Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="b6cf7-110">建立關鍵區段進行同步處理物件。</span><span class="sxs-lookup"><span data-stu-id="b6cf7-110">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="b6cf7-111">CreateCrstWithSpinCount 方法</span><span class="sxs-lookup"><span data-stu-id="b6cf7-111">CreateCrstWithSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="b6cf7-112">建立關鍵區段物件具有微調計數進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="b6cf7-112">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="b6cf7-113">CreateManualEvent 方法</span><span class="sxs-lookup"><span data-stu-id="b6cf7-113">CreateManualEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="b6cf7-114">建立手動重設事件物件。</span><span class="sxs-lookup"><span data-stu-id="b6cf7-114">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="b6cf7-115">CreateMonitorEvent 方法</span><span class="sxs-lookup"><span data-stu-id="b6cf7-115">CreateMonitorEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="b6cf7-116">建立受監視的自動重設事件物件。</span><span class="sxs-lookup"><span data-stu-id="b6cf7-116">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="b6cf7-117">CreateRWLockReaderEvent 方法</span><span class="sxs-lookup"><span data-stu-id="b6cf7-117">CreateRWLockReaderEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="b6cf7-118">建立手動重設事件物件的讀取器鎖定的實作。</span><span class="sxs-lookup"><span data-stu-id="b6cf7-118">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="b6cf7-119">CreateRWLockWriterEvent 方法</span><span class="sxs-lookup"><span data-stu-id="b6cf7-119">CreateRWLockWriterEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="b6cf7-120">建立自動重設事件物件的寫入器鎖定的實作。</span><span class="sxs-lookup"><span data-stu-id="b6cf7-120">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="b6cf7-121">CreateSemaphore 方法</span><span class="sxs-lookup"><span data-stu-id="b6cf7-121">CreateSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="b6cf7-122">建立[IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)作為等候事件信號的 CLR 物件。</span><span class="sxs-lookup"><span data-stu-id="b6cf7-122">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="b6cf7-123">SetCLRSyncManager 方法</span><span class="sxs-lookup"><span data-stu-id="b6cf7-123">SetCLRSyncManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="b6cf7-124">設定[ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)與目前的執行個體`IHostSyncManager`執行個體。</span><span class="sxs-lookup"><span data-stu-id="b6cf7-124">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6cf7-125">備註</span><span class="sxs-lookup"><span data-stu-id="b6cf7-125">Remarks</span></span>  
 <span data-ttu-id="b6cf7-126">CLR 會探索主應用程式的實作`IHostSyncManager`藉由呼叫[ihostcontrol:: Gethostmanager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)方法`IID`IID_IHostSyncManager。</span><span class="sxs-lookup"><span data-stu-id="b6cf7-126">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6cf7-127">需求</span><span class="sxs-lookup"><span data-stu-id="b6cf7-127">Requirements</span></span>  
 <span data-ttu-id="b6cf7-128">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b6cf7-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6cf7-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b6cf7-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b6cf7-130">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b6cf7-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6cf7-131">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6cf7-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6cf7-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6cf7-132">See Also</span></span>  
 [<span data-ttu-id="b6cf7-133">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="b6cf7-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="b6cf7-134">裝載介面</span><span class="sxs-lookup"><span data-stu-id="b6cf7-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
