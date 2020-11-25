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
ms.openlocfilehash: 8a5fc42191634a2e5a441baecc4b78212ffad687
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720486"
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="23649-102">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="23649-102">IHostSyncManager Interface</span></span>

<span data-ttu-id="23649-103">提供方法，讓 common language runtime (CLR) 透過呼叫主機而非使用 Win32 同步處理函式來建立同步處理原始物件。</span><span class="sxs-lookup"><span data-stu-id="23649-103">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="23649-104">方法</span><span class="sxs-lookup"><span data-stu-id="23649-104">Methods</span></span>  
  
|<span data-ttu-id="23649-105">方法</span><span class="sxs-lookup"><span data-stu-id="23649-105">Method</span></span>|<span data-ttu-id="23649-106">描述</span><span class="sxs-lookup"><span data-stu-id="23649-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="23649-107">CreateAutoEvent 方法</span><span class="sxs-lookup"><span data-stu-id="23649-107">CreateAutoEvent Method</span></span>](ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="23649-108">建立自動重設事件物件。</span><span class="sxs-lookup"><span data-stu-id="23649-108">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="23649-109">CreateCrst 方法</span><span class="sxs-lookup"><span data-stu-id="23649-109">CreateCrst Method</span></span>](ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="23649-110">建立同步處理的重要區段物件。</span><span class="sxs-lookup"><span data-stu-id="23649-110">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="23649-111">CreateCrstWithSpinCount 方法</span><span class="sxs-lookup"><span data-stu-id="23649-111">CreateCrstWithSpinCount Method</span></span>](ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="23649-112">使用微調計數來建立重要區段物件以進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="23649-112">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="23649-113">CreateManualEvent 方法</span><span class="sxs-lookup"><span data-stu-id="23649-113">CreateManualEvent Method</span></span>](ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="23649-114">建立手動重設事件物件。</span><span class="sxs-lookup"><span data-stu-id="23649-114">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="23649-115">CreateMonitorEvent 方法</span><span class="sxs-lookup"><span data-stu-id="23649-115">CreateMonitorEvent Method</span></span>](ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="23649-116">建立受監視的自動重設事件物件。</span><span class="sxs-lookup"><span data-stu-id="23649-116">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="23649-117">CreateRWLockReaderEvent 方法</span><span class="sxs-lookup"><span data-stu-id="23649-117">CreateRWLockReaderEvent Method</span></span>](ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="23649-118">建立手動重設的事件物件，以執行讀取器鎖定。</span><span class="sxs-lookup"><span data-stu-id="23649-118">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="23649-119">CreateRWLockWriterEvent 方法</span><span class="sxs-lookup"><span data-stu-id="23649-119">CreateRWLockWriterEvent Method</span></span>](ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="23649-120">建立自動重設事件物件，以執行寫入器鎖定。</span><span class="sxs-lookup"><span data-stu-id="23649-120">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="23649-121">CreateSemaphore 方法</span><span class="sxs-lookup"><span data-stu-id="23649-121">CreateSemaphore Method</span></span>](ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="23649-122">建立 [IHostSemaphore](ihostsemaphore-interface.md) 物件，讓 CLR 用來作為等候事件的信號。</span><span class="sxs-lookup"><span data-stu-id="23649-122">Creates an [IHostSemaphore](ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="23649-123">SetCLRSyncManager 方法</span><span class="sxs-lookup"><span data-stu-id="23649-123">SetCLRSyncManager Method</span></span>](ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="23649-124">設定要與目前實例相關聯的 [ICLRSyncManager](iclrsyncmanager-interface.md) 實例 `IHostSyncManager` 。</span><span class="sxs-lookup"><span data-stu-id="23649-124">Sets the [ICLRSyncManager](iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23649-125">備註</span><span class="sxs-lookup"><span data-stu-id="23649-125">Remarks</span></span>  

 <span data-ttu-id="23649-126">CLR 會藉 `IHostSyncManager` 由呼叫 [IHostControl：： GetHostManager](ihostcontrol-gethostmanager-method.md) 方法和 IID_IHostSyncManager 來探索主機的實 `IID` 。</span><span class="sxs-lookup"><span data-stu-id="23649-126">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23649-127">需求</span><span class="sxs-lookup"><span data-stu-id="23649-127">Requirements</span></span>  

 <span data-ttu-id="23649-128">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="23649-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23649-129">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="23649-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="23649-130">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="23649-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="23649-131">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23649-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23649-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23649-132">See also</span></span>

- [<span data-ttu-id="23649-133">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="23649-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="23649-134">裝載介面</span><span class="sxs-lookup"><span data-stu-id="23649-134">Hosting Interfaces</span></span>](hosting-interfaces.md)
