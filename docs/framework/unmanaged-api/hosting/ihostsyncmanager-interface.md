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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 200da8b87b52a29c2b075d1e06929031d3f588b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769625"
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="09654-102">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="09654-102">IHostSyncManager Interface</span></span>
<span data-ttu-id="09654-103">提供方法，可讓 common language runtime (CLR) 呼叫主應用程式，而不是使用 Win32 同步處理函式來建立同步處理原始物件。</span><span class="sxs-lookup"><span data-stu-id="09654-103">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="09654-104">方法</span><span class="sxs-lookup"><span data-stu-id="09654-104">Methods</span></span>  
  
|<span data-ttu-id="09654-105">方法</span><span class="sxs-lookup"><span data-stu-id="09654-105">Method</span></span>|<span data-ttu-id="09654-106">描述</span><span class="sxs-lookup"><span data-stu-id="09654-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="09654-107">CreateAutoEvent 方法</span><span class="sxs-lookup"><span data-stu-id="09654-107">CreateAutoEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="09654-108">建立自動重設事件物件。</span><span class="sxs-lookup"><span data-stu-id="09654-108">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="09654-109">CreateCrst 方法</span><span class="sxs-lookup"><span data-stu-id="09654-109">CreateCrst Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="09654-110">建立同步處理的重要區段物件。</span><span class="sxs-lookup"><span data-stu-id="09654-110">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="09654-111">CreateCrstWithSpinCount 方法</span><span class="sxs-lookup"><span data-stu-id="09654-111">CreateCrstWithSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="09654-112">建立具有同步處理的微調計數的重要區段物件。</span><span class="sxs-lookup"><span data-stu-id="09654-112">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="09654-113">CreateManualEvent 方法</span><span class="sxs-lookup"><span data-stu-id="09654-113">CreateManualEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="09654-114">建立手動重設事件物件。</span><span class="sxs-lookup"><span data-stu-id="09654-114">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="09654-115">CreateMonitorEvent 方法</span><span class="sxs-lookup"><span data-stu-id="09654-115">CreateMonitorEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="09654-116">建立受監視的自動重設事件物件。</span><span class="sxs-lookup"><span data-stu-id="09654-116">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="09654-117">CreateRWLockReaderEvent 方法</span><span class="sxs-lookup"><span data-stu-id="09654-117">CreateRWLockReaderEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="09654-118">建立手動重設事件物件實作的讀取器的鎖定。</span><span class="sxs-lookup"><span data-stu-id="09654-118">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="09654-119">CreateRWLockWriterEvent 方法</span><span class="sxs-lookup"><span data-stu-id="09654-119">CreateRWLockWriterEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="09654-120">建立自動重設事件物件的寫入器鎖定的實作。</span><span class="sxs-lookup"><span data-stu-id="09654-120">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="09654-121">CreateSemaphore 方法</span><span class="sxs-lookup"><span data-stu-id="09654-121">CreateSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="09654-122">會建立[IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) CLR 作為等候事件的號誌的物件。</span><span class="sxs-lookup"><span data-stu-id="09654-122">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="09654-123">SetCLRSyncManager 方法</span><span class="sxs-lookup"><span data-stu-id="09654-123">SetCLRSyncManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="09654-124">設定組[ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)目前相關聯的執行個體`IHostSyncManager`執行個體。</span><span class="sxs-lookup"><span data-stu-id="09654-124">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09654-125">備註</span><span class="sxs-lookup"><span data-stu-id="09654-125">Remarks</span></span>  
 <span data-ttu-id="09654-126">CLR 會探索主應用程式的實作`IHostSyncManager`藉由呼叫[ihostcontrol:: Gethostmanager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)方法`IID`IID_IHostSyncManager。</span><span class="sxs-lookup"><span data-stu-id="09654-126">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09654-127">需求</span><span class="sxs-lookup"><span data-stu-id="09654-127">Requirements</span></span>  
 <span data-ttu-id="09654-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="09654-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09654-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="09654-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="09654-130">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="09654-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="09654-131">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09654-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09654-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09654-132">See also</span></span>

- [<span data-ttu-id="09654-133">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="09654-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="09654-134">裝載介面</span><span class="sxs-lookup"><span data-stu-id="09654-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
