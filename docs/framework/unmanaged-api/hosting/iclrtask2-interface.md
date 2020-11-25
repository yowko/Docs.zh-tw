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
ms.openlocfilehash: 9332b3462ba389783a113d173e32850d40427ce2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720226"
---
# <a name="iclrtask2-interface"></a><span data-ttu-id="971a5-102">ICLRTask2 介面</span><span class="sxs-lookup"><span data-stu-id="971a5-102">ICLRTask2 Interface</span></span>

<span data-ttu-id="971a5-103">提供 [ICLRTask](iclrtask-interface.md) 介面的所有功能;此外，還提供可讓執行緒中止在目前線程上延遲的方法。</span><span class="sxs-lookup"><span data-stu-id="971a5-103">Provides all the functionality of the [ICLRTask](iclrtask-interface.md) interface; in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="971a5-104">方法</span><span class="sxs-lookup"><span data-stu-id="971a5-104">Methods</span></span>  
  
|<span data-ttu-id="971a5-105">方法</span><span class="sxs-lookup"><span data-stu-id="971a5-105">Method</span></span>|<span data-ttu-id="971a5-106">描述</span><span class="sxs-lookup"><span data-stu-id="971a5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="971a5-107">BeginPreventAsyncAbort 方法</span><span class="sxs-lookup"><span data-stu-id="971a5-107">BeginPreventAsyncAbort Method</span></span>](iclrtask2-beginpreventasyncabort-method.md)|<span data-ttu-id="971a5-108">延遲目前線程上的新執行緒中止要求。</span><span class="sxs-lookup"><span data-stu-id="971a5-108">Delays new thread abort requests on the current thread.</span></span>|  
|[<span data-ttu-id="971a5-109">EndPreventAsyncAbort 方法</span><span class="sxs-lookup"><span data-stu-id="971a5-109">EndPreventAsyncAbort Method</span></span>](iclrtask2-endpreventasyncabort-method.md)|<span data-ttu-id="971a5-110">允許新的或擱置中的執行緒中止要求，導致執行緒在目前線程上中止。</span><span class="sxs-lookup"><span data-stu-id="971a5-110">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="971a5-111">備註</span><span class="sxs-lookup"><span data-stu-id="971a5-111">Remarks</span></span>  

 <span data-ttu-id="971a5-112">`ICLRTask2`介面會繼承 `ICLRTask` 介面，並加入可讓主機延遲線程中止的方法，以保護不能失敗的程式碼區域。</span><span class="sxs-lookup"><span data-stu-id="971a5-112">The `ICLRTask2` interface inherits the `ICLRTask` interface and adds methods that allow the host to delay thread aborts, to protect a region of code that must not fail.</span></span> <span data-ttu-id="971a5-113">呼叫 `BeginPreventAsyncAbort` 會遞增目前線程的延遲線程中止計數器，並呼叫 `EndPreventAsyncAbort` 遞減。</span><span class="sxs-lookup"><span data-stu-id="971a5-113">Calling `BeginPreventAsyncAbort` increments the delay-thread-abort counter for the current thread, and calling `EndPreventAsyncAbort` decrements it.</span></span> <span data-ttu-id="971a5-114">對和的呼叫 `BeginPreventAsyncAbort` `EndPreventAsyncAbort` 可以嵌套。</span><span class="sxs-lookup"><span data-stu-id="971a5-114">Calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="971a5-115">只要計數器大於零，目前線程的執行緒中止就會延遲。</span><span class="sxs-lookup"><span data-stu-id="971a5-115">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="971a5-116">如果對 `BeginPreventAsyncAbort` 和 `EndPreventAsyncAbort` 的呼叫未配對，則可能會達到無法將執行緒中止傳遞給目前線程的狀態。</span><span class="sxs-lookup"><span data-stu-id="971a5-116">If calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` are not paired, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="971a5-117">中止本身的執行緒不會接受延遲。</span><span class="sxs-lookup"><span data-stu-id="971a5-117">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="971a5-118">虛擬機器 (VM) 會在內部使用這項功能所公開的功能。</span><span class="sxs-lookup"><span data-stu-id="971a5-118">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="971a5-119">誤用這些方法可能會導致 VM 未指定的行為。</span><span class="sxs-lookup"><span data-stu-id="971a5-119">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="971a5-120">例如，呼叫 `EndPreventAsyncAbort` 時若未先呼叫， `BeginPreventAsyncAbort` 就可以在 VM 先前遞增計數器時，將計數器設定為零。</span><span class="sxs-lookup"><span data-stu-id="971a5-120">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="971a5-121">同樣地，不會檢查內部計數器是否有溢位。</span><span class="sxs-lookup"><span data-stu-id="971a5-121">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="971a5-122">如果它超過整數限制，因為它會同時由主機和 VM 遞增，則會未指定產生的行為。</span><span class="sxs-lookup"><span data-stu-id="971a5-122">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
 <span data-ttu-id="971a5-123">如需有關繼承自此介面之其他用法的成員和的詳細資訊 `ICLRTask` ，請參閱 [ICLRTask](iclrtask-interface.md) 介面。</span><span class="sxs-lookup"><span data-stu-id="971a5-123">For information about members inherited from `ICLRTask` and about the other uses of this interface, see the [ICLRTask](iclrtask-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="971a5-124">需求</span><span class="sxs-lookup"><span data-stu-id="971a5-124">Requirements</span></span>  

 <span data-ttu-id="971a5-125">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="971a5-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="971a5-126">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="971a5-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="971a5-127">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="971a5-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="971a5-128">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="971a5-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="971a5-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="971a5-129">See also</span></span>

- [<span data-ttu-id="971a5-130">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="971a5-130">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="971a5-131">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="971a5-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="971a5-132">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="971a5-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="971a5-133">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="971a5-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="971a5-134">裝載介面</span><span class="sxs-lookup"><span data-stu-id="971a5-134">Hosting Interfaces</span></span>](hosting-interfaces.md)
