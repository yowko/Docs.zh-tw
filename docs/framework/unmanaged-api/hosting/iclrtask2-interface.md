---
title: ICLRTask2 介面
ms.date: 03/30/2017
api_name:
- ICLRTask2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2
helpviewer_keywords:
- ICLRTask2 interface [.NET Framework hosting]
ms.assetid: b5a22ebc-0582-49de-91f9-97a3d9789290
topic_type:
- apiref
ms.openlocfilehash: 47c6dd9045636bcfbe07c909fec3fda515d28ee8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124530"
---
# <a name="iclrtask2-interface"></a><span data-ttu-id="50c87-102">ICLRTask2 介面</span><span class="sxs-lookup"><span data-stu-id="50c87-102">ICLRTask2 Interface</span></span>
<span data-ttu-id="50c87-103">提供[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)介面的所有功能;此外，也提供可讓執行緒中止在目前線程上延遲的方法。</span><span class="sxs-lookup"><span data-stu-id="50c87-103">Provides all the functionality of the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface; in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="50c87-104">方法</span><span class="sxs-lookup"><span data-stu-id="50c87-104">Methods</span></span>  
  
|<span data-ttu-id="50c87-105">方法</span><span class="sxs-lookup"><span data-stu-id="50c87-105">Method</span></span>|<span data-ttu-id="50c87-106">描述</span><span class="sxs-lookup"><span data-stu-id="50c87-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="50c87-107">BeginPreventAsyncAbort 方法</span><span class="sxs-lookup"><span data-stu-id="50c87-107">BeginPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|<span data-ttu-id="50c87-108">延遲目前線程上的新執行緒中止要求。</span><span class="sxs-lookup"><span data-stu-id="50c87-108">Delays new thread abort requests on the current thread.</span></span>|  
|[<span data-ttu-id="50c87-109">EndPreventAsyncAbort 方法</span><span class="sxs-lookup"><span data-stu-id="50c87-109">EndPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|<span data-ttu-id="50c87-110">允許新的或暫止的執行緒中止要求，導致目前線程上的執行緒中止。</span><span class="sxs-lookup"><span data-stu-id="50c87-110">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50c87-111">備註</span><span class="sxs-lookup"><span data-stu-id="50c87-111">Remarks</span></span>  
 <span data-ttu-id="50c87-112">`ICLRTask2` 介面會繼承 `ICLRTask` 介面，並新增可讓主機延遲線程中止的方法，以保護不能失敗的程式碼區域。</span><span class="sxs-lookup"><span data-stu-id="50c87-112">The `ICLRTask2` interface inherits the `ICLRTask` interface and adds methods that allow the host to delay thread aborts, to protect a region of code that must not fail.</span></span> <span data-ttu-id="50c87-113">呼叫 `BeginPreventAsyncAbort` 會遞增目前線程的延遲線程中止計數器，而呼叫 `EndPreventAsyncAbort` 會將其遞減。</span><span class="sxs-lookup"><span data-stu-id="50c87-113">Calling `BeginPreventAsyncAbort` increments the delay-thread-abort counter for the current thread, and calling `EndPreventAsyncAbort` decrements it.</span></span> <span data-ttu-id="50c87-114">`BeginPreventAsyncAbort` 和 `EndPreventAsyncAbort` 的呼叫可以進行嵌套。</span><span class="sxs-lookup"><span data-stu-id="50c87-114">Calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="50c87-115">只要計數器大於零，就會延遲目前線程的執行緒中止。</span><span class="sxs-lookup"><span data-stu-id="50c87-115">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="50c87-116">如果 `BeginPreventAsyncAbort` 和 `EndPreventAsyncAbort` 的呼叫未配對，則可能會到達無法將執行緒中止傳遞至目前線程的狀態。</span><span class="sxs-lookup"><span data-stu-id="50c87-116">If calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` are not paired, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="50c87-117">中斷本身的執行緒不會接受延遲。</span><span class="sxs-lookup"><span data-stu-id="50c87-117">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="50c87-118">這項功能所公開的功能會在虛擬機器（VM）內部使用。</span><span class="sxs-lookup"><span data-stu-id="50c87-118">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="50c87-119">誤用這些方法可能會導致 VM 中未指定的行為。</span><span class="sxs-lookup"><span data-stu-id="50c87-119">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="50c87-120">例如，在沒有第一次呼叫 `BeginPreventAsyncAbort` 的情況下呼叫 `EndPreventAsyncAbort`，會在 VM 先前已遞增時，將計數器設定為零。</span><span class="sxs-lookup"><span data-stu-id="50c87-120">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="50c87-121">同樣地，內部計數器也不會檢查溢位。</span><span class="sxs-lookup"><span data-stu-id="50c87-121">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="50c87-122">如果它超過其整數限制，因為它是由主機和 VM 增加，則會未指定所產生的行為。</span><span class="sxs-lookup"><span data-stu-id="50c87-122">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
 <span data-ttu-id="50c87-123">如需繼承自 `ICLRTask` 的成員以及此介面的其他用法的詳細資訊，請參閱[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="50c87-123">For information about members inherited from `ICLRTask` and about the other uses of this interface, see the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50c87-124">需求</span><span class="sxs-lookup"><span data-stu-id="50c87-124">Requirements</span></span>  
 <span data-ttu-id="50c87-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="50c87-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50c87-126">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="50c87-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="50c87-127">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="50c87-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50c87-128">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50c87-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50c87-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="50c87-129">See also</span></span>

- [<span data-ttu-id="50c87-130">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="50c87-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="50c87-131">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="50c87-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="50c87-132">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="50c87-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="50c87-133">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="50c87-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="50c87-134">裝載介面</span><span class="sxs-lookup"><span data-stu-id="50c87-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
