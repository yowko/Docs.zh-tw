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
ms.openlocfilehash: aa9f039cb7eaa7ccd22bad36098c00a697d818d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443969"
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="6fe87-102">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="6fe87-102">IHostSyncManager Interface</span></span>
<span data-ttu-id="6fe87-103">提供方法讓 common language runtime (CLR) 呼叫主應用程式，而不是使用 Win32 同步處理函式來建立同步處理原始物件。</span><span class="sxs-lookup"><span data-stu-id="6fe87-103">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6fe87-104">方法</span><span class="sxs-lookup"><span data-stu-id="6fe87-104">Methods</span></span>  
  
|<span data-ttu-id="6fe87-105">方法</span><span class="sxs-lookup"><span data-stu-id="6fe87-105">Method</span></span>|<span data-ttu-id="6fe87-106">描述</span><span class="sxs-lookup"><span data-stu-id="6fe87-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6fe87-107">CreateAutoEvent 方法</span><span class="sxs-lookup"><span data-stu-id="6fe87-107">CreateAutoEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="6fe87-108">建立的自動重設事件物件。</span><span class="sxs-lookup"><span data-stu-id="6fe87-108">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="6fe87-109">CreateCrst 方法</span><span class="sxs-lookup"><span data-stu-id="6fe87-109">CreateCrst Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="6fe87-110">建立關鍵區段進行同步處理物件。</span><span class="sxs-lookup"><span data-stu-id="6fe87-110">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="6fe87-111">CreateCrstWithSpinCount 方法</span><span class="sxs-lookup"><span data-stu-id="6fe87-111">CreateCrstWithSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="6fe87-112">建立關鍵區段物件具有微調計數進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="6fe87-112">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="6fe87-113">CreateManualEvent 方法</span><span class="sxs-lookup"><span data-stu-id="6fe87-113">CreateManualEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="6fe87-114">建立手動重設事件物件。</span><span class="sxs-lookup"><span data-stu-id="6fe87-114">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="6fe87-115">CreateMonitorEvent 方法</span><span class="sxs-lookup"><span data-stu-id="6fe87-115">CreateMonitorEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="6fe87-116">建立受監視的自動重設事件物件。</span><span class="sxs-lookup"><span data-stu-id="6fe87-116">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="6fe87-117">CreateRWLockReaderEvent 方法</span><span class="sxs-lookup"><span data-stu-id="6fe87-117">CreateRWLockReaderEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="6fe87-118">建立手動重設事件物件的讀取器鎖定的實作。</span><span class="sxs-lookup"><span data-stu-id="6fe87-118">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="6fe87-119">CreateRWLockWriterEvent 方法</span><span class="sxs-lookup"><span data-stu-id="6fe87-119">CreateRWLockWriterEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="6fe87-120">建立自動重設事件物件的寫入器鎖定的實作。</span><span class="sxs-lookup"><span data-stu-id="6fe87-120">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="6fe87-121">CreateSemaphore 方法</span><span class="sxs-lookup"><span data-stu-id="6fe87-121">CreateSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="6fe87-122">建立[IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)作為等候事件信號的 CLR 物件。</span><span class="sxs-lookup"><span data-stu-id="6fe87-122">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="6fe87-123">SetCLRSyncManager 方法</span><span class="sxs-lookup"><span data-stu-id="6fe87-123">SetCLRSyncManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="6fe87-124">設定[ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)與目前的執行個體`IHostSyncManager`執行個體。</span><span class="sxs-lookup"><span data-stu-id="6fe87-124">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6fe87-125">備註</span><span class="sxs-lookup"><span data-stu-id="6fe87-125">Remarks</span></span>  
 <span data-ttu-id="6fe87-126">CLR 會探索主應用程式的實作`IHostSyncManager`藉由呼叫[ihostcontrol:: Gethostmanager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)方法`IID`IID_IHostSyncManager。</span><span class="sxs-lookup"><span data-stu-id="6fe87-126">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fe87-127">需求</span><span class="sxs-lookup"><span data-stu-id="6fe87-127">Requirements</span></span>  
 <span data-ttu-id="6fe87-128">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6fe87-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fe87-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6fe87-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6fe87-130">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6fe87-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6fe87-131">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fe87-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fe87-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6fe87-132">See Also</span></span>  
 [<span data-ttu-id="6fe87-133">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="6fe87-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="6fe87-134">裝載介面</span><span class="sxs-lookup"><span data-stu-id="6fe87-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
