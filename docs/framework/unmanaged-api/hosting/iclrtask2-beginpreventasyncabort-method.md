---
title: ICLRTask2::BeginPreventAsyncAbort 方法
ms.date: 03/30/2017
api_name:
- ICLRTask2.BeginPreventAsyncAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2::BeginPreventAsyncAbort
helpviewer_keywords:
- ICLRTask2::BeginPreventAsyncAbort method [.NET Framework hosting]
- BeginPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: 75754c2f-38c7-4707-85fe-559db4542729
topic_type:
- apiref
ms.openlocfilehash: daf211fcc496f63ef71575abf6a28655004db264
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720239"
---
# <a name="iclrtask2beginpreventasyncabort-method"></a><span data-ttu-id="c363f-102">ICLRTask2::BeginPreventAsyncAbort 方法</span><span class="sxs-lookup"><span data-stu-id="c363f-102">ICLRTask2::BeginPreventAsyncAbort Method</span></span>

<span data-ttu-id="c363f-103">延遲新的執行緒中止要求，導致執行緒在目前線程上中止。</span><span class="sxs-lookup"><span data-stu-id="c363f-103">Delays new thread abort requests from resulting in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c363f-104">語法</span><span class="sxs-lookup"><span data-stu-id="c363f-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c363f-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="c363f-105">Return Value</span></span>  

 <span data-ttu-id="c363f-106">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="c363f-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c363f-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c363f-107">HRESULT</span></span>|<span data-ttu-id="c363f-108">描述</span><span class="sxs-lookup"><span data-stu-id="c363f-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c363f-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="c363f-109">S_OK</span></span>|<span data-ttu-id="c363f-110">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="c363f-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="c363f-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="c363f-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="c363f-112">方法是在不是目前線程的執行緒上呼叫。</span><span class="sxs-lookup"><span data-stu-id="c363f-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c363f-113">備註</span><span class="sxs-lookup"><span data-stu-id="c363f-113">Remarks</span></span>  

 <span data-ttu-id="c363f-114">呼叫這個方法會將目前線程的延遲線程中止計數器遞增一。</span><span class="sxs-lookup"><span data-stu-id="c363f-114">Calling this method increments the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="c363f-115">`BeginPreventAsyncAbort`和[ICLRTask2：： EndPreventAsyncAbort](iclrtask2-endpreventasyncabort-method.md)的呼叫可以嵌套。</span><span class="sxs-lookup"><span data-stu-id="c363f-115">Calls to `BeginPreventAsyncAbort` and [ICLRTask2::EndPreventAsyncAbort](iclrtask2-endpreventasyncabort-method.md) can be nested.</span></span> <span data-ttu-id="c363f-116">只要計數器大於零，目前線程的執行緒中止就會延遲。</span><span class="sxs-lookup"><span data-stu-id="c363f-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span> <span data-ttu-id="c363f-117">如果此呼叫未與方法的呼叫配對 `EndPreventAsyncAbort` ，則可能會達到無法將執行緒中止傳遞給目前線程的狀態。</span><span class="sxs-lookup"><span data-stu-id="c363f-117">If this call is not paired with a call to the `EndPreventAsyncAbort` method, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="c363f-118">中止本身的執行緒不會接受延遲。</span><span class="sxs-lookup"><span data-stu-id="c363f-118">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="c363f-119">虛擬機器 (VM) 會在內部使用這項功能所公開的功能。</span><span class="sxs-lookup"><span data-stu-id="c363f-119">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="c363f-120">誤用這些方法可能會導致 VM 未指定的行為。</span><span class="sxs-lookup"><span data-stu-id="c363f-120">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="c363f-121">例如，呼叫 `EndPreventAsyncAbort` 時若未先呼叫， `BeginPreventAsyncAbort` 就可以在 VM 先前遞增計數器時，將計數器設定為零。</span><span class="sxs-lookup"><span data-stu-id="c363f-121">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="c363f-122">同樣地，不會檢查內部計數器是否有溢位。</span><span class="sxs-lookup"><span data-stu-id="c363f-122">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="c363f-123">如果它超過整數限制，因為它會同時由主機和 VM 遞增，則會未指定產生的行為。</span><span class="sxs-lookup"><span data-stu-id="c363f-123">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c363f-124">需求</span><span class="sxs-lookup"><span data-stu-id="c363f-124">Requirements</span></span>  

 <span data-ttu-id="c363f-125">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c363f-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c363f-126">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="c363f-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c363f-127">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="c363f-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c363f-128">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c363f-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c363f-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c363f-129">See also</span></span>

- [<span data-ttu-id="c363f-130">EndPreventAsyncAbort 方法</span><span class="sxs-lookup"><span data-stu-id="c363f-130">EndPreventAsyncAbort Method</span></span>](iclrtask2-endpreventasyncabort-method.md)
- [<span data-ttu-id="c363f-131">ICLRTask2 介面</span><span class="sxs-lookup"><span data-stu-id="c363f-131">ICLRTask2 Interface</span></span>](iclrtask2-interface.md)
- [<span data-ttu-id="c363f-132">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="c363f-132">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="c363f-133">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="c363f-133">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="c363f-134">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="c363f-134">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="c363f-135">裝載介面</span><span class="sxs-lookup"><span data-stu-id="c363f-135">Hosting Interfaces</span></span>](hosting-interfaces.md)
