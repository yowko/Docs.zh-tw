---
title: "ICLRTask2 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask2
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask2
helpviewer_keywords: ICLRTask2 interface [.NET Framework hosting]
ms.assetid: b5a22ebc-0582-49de-91f9-97a3d9789290
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5f2312d193031eae556f55b061a36259531d013b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtask2-interface"></a><span data-ttu-id="90814-102">ICLRTask2 介面</span><span class="sxs-lookup"><span data-stu-id="90814-102">ICLRTask2 Interface</span></span>
<span data-ttu-id="90814-103">提供的所有功能[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)介面; 此外，都提供方法，讓執行緒中止目前的執行緒上延遲。</span><span class="sxs-lookup"><span data-stu-id="90814-103">Provides all the functionality of the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface; in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="90814-104">方法</span><span class="sxs-lookup"><span data-stu-id="90814-104">Methods</span></span>  
  
|<span data-ttu-id="90814-105">方法</span><span class="sxs-lookup"><span data-stu-id="90814-105">Method</span></span>|<span data-ttu-id="90814-106">說明</span><span class="sxs-lookup"><span data-stu-id="90814-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="90814-107">BeginPreventAsyncAbort 方法</span><span class="sxs-lookup"><span data-stu-id="90814-107">BeginPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|<span data-ttu-id="90814-108">延遲新執行緒中止目前的執行緒上的要求。</span><span class="sxs-lookup"><span data-stu-id="90814-108">Delays new thread abort requests on the current thread.</span></span>|  
|[<span data-ttu-id="90814-109">EndPreventAsyncAbort 方法</span><span class="sxs-lookup"><span data-stu-id="90814-109">EndPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|<span data-ttu-id="90814-110">可讓新的或暫止的執行緒中止要求，以產生的執行緒會中止目前的執行緒上。</span><span class="sxs-lookup"><span data-stu-id="90814-110">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90814-111">備註</span><span class="sxs-lookup"><span data-stu-id="90814-111">Remarks</span></span>  
 <span data-ttu-id="90814-112">`ICLRTask2`介面繼承`ICLRTask`介面，並加入方法，可讓主應用程式延遲執行緒中止，若要保護的程式碼必須通過的區域。</span><span class="sxs-lookup"><span data-stu-id="90814-112">The `ICLRTask2` interface inherits the `ICLRTask` interface and adds methods that allow the host to delay thread aborts, to protect a region of code that must not fail.</span></span> <span data-ttu-id="90814-113">呼叫`BeginPreventAsyncAbort`遞增延遲執行緒中止計數器目前的執行緒和呼叫`EndPreventAsyncAbort`遞減它。</span><span class="sxs-lookup"><span data-stu-id="90814-113">Calling `BeginPreventAsyncAbort` increments the delay-thread-abort counter for the current thread, and calling `EndPreventAsyncAbort` decrements it.</span></span> <span data-ttu-id="90814-114">呼叫`BeginPreventAsyncAbort`和`EndPreventAsyncAbort`可以巢狀。</span><span class="sxs-lookup"><span data-stu-id="90814-114">Calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="90814-115">只要計數器是小於或等於零，執行緒中止目前的執行緒會延遲。</span><span class="sxs-lookup"><span data-stu-id="90814-115">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="90814-116">如果呼叫`BeginPreventAsyncAbort`和`EndPreventAsyncAbort`會不成對的便可達到在哪一個執行緒中止無法傳遞至目前執行緒的狀態。</span><span class="sxs-lookup"><span data-stu-id="90814-116">If calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` are not paired, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="90814-117">中止本身的執行緒不是接受的延遲。</span><span class="sxs-lookup"><span data-stu-id="90814-117">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="90814-118">這項功能所公開的功能是由虛擬機器 (VM) 內部使用。</span><span class="sxs-lookup"><span data-stu-id="90814-118">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="90814-119">不當使用這些方法可能導致 VM 未指定的行為。</span><span class="sxs-lookup"><span data-stu-id="90814-119">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="90814-120">例如，呼叫`EndPreventAsyncAbort`情況下先呼叫`BeginPreventAsyncAbort`VM 之前會遞增它時，無法設定計數器為零。</span><span class="sxs-lookup"><span data-stu-id="90814-120">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="90814-121">同樣地，內部計數器不會檢查溢位。</span><span class="sxs-lookup"><span data-stu-id="90814-121">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="90814-122">如果它超過其整數類資料的限制，因為主機和 VM，就會遞增，結果行為是未指定。</span><span class="sxs-lookup"><span data-stu-id="90814-122">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
 <span data-ttu-id="90814-123">從繼承成員的相關資訊`ICLRTask`和此介面的其他用途，請參閱[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="90814-123">For information about members inherited from `ICLRTask` and about the other uses of this interface, see the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90814-124">需求</span><span class="sxs-lookup"><span data-stu-id="90814-124">Requirements</span></span>  
 <span data-ttu-id="90814-125">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="90814-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90814-126">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="90814-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="90814-127">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="90814-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="90814-128">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90814-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90814-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90814-129">See Also</span></span>  
 [<span data-ttu-id="90814-130">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="90814-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="90814-131">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="90814-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="90814-132">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="90814-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="90814-133">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="90814-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="90814-134">裝載介面</span><span class="sxs-lookup"><span data-stu-id="90814-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
