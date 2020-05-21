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
ms.openlocfilehash: 0da18c6850f393808d05dff8b1f19ac12b05bb86
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762886"
---
# <a name="iclrtask2beginpreventasyncabort-method"></a><span data-ttu-id="fc00c-102">ICLRTask2::BeginPreventAsyncAbort 方法</span><span class="sxs-lookup"><span data-stu-id="fc00c-102">ICLRTask2::BeginPreventAsyncAbort Method</span></span>
<span data-ttu-id="fc00c-103">延遲在目前線程上導致執行緒中止的新執行緒中止要求。</span><span class="sxs-lookup"><span data-stu-id="fc00c-103">Delays new thread abort requests from resulting in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc00c-104">語法</span><span class="sxs-lookup"><span data-stu-id="fc00c-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="fc00c-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="fc00c-105">Return Value</span></span>  
 <span data-ttu-id="fc00c-106">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="fc00c-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="fc00c-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fc00c-107">HRESULT</span></span>|<span data-ttu-id="fc00c-108">Description</span><span class="sxs-lookup"><span data-stu-id="fc00c-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fc00c-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="fc00c-109">S_OK</span></span>|<span data-ttu-id="fc00c-110">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="fc00c-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="fc00c-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="fc00c-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="fc00c-112">在不是目前線程的執行緒上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="fc00c-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc00c-113">備註</span><span class="sxs-lookup"><span data-stu-id="fc00c-113">Remarks</span></span>  
 <span data-ttu-id="fc00c-114">呼叫這個方法會將目前線程的延遲線程中止計數器遞增一。</span><span class="sxs-lookup"><span data-stu-id="fc00c-114">Calling this method increments the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="fc00c-115">`BeginPreventAsyncAbort`可以嵌套呼叫和[ICLRTask2：： EndPreventAsyncAbort](iclrtask2-endpreventasyncabort-method.md) 。</span><span class="sxs-lookup"><span data-stu-id="fc00c-115">Calls to `BeginPreventAsyncAbort` and [ICLRTask2::EndPreventAsyncAbort](iclrtask2-endpreventasyncabort-method.md) can be nested.</span></span> <span data-ttu-id="fc00c-116">只要計數器大於零，就會延遲目前線程的執行緒中止。</span><span class="sxs-lookup"><span data-stu-id="fc00c-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span> <span data-ttu-id="fc00c-117">如果此呼叫未與方法的呼叫配對 `EndPreventAsyncAbort` ，則可能會到達無法將執行緒中止傳遞至目前線程的狀態。</span><span class="sxs-lookup"><span data-stu-id="fc00c-117">If this call is not paired with a call to the `EndPreventAsyncAbort` method, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="fc00c-118">中斷本身的執行緒不會接受延遲。</span><span class="sxs-lookup"><span data-stu-id="fc00c-118">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="fc00c-119">這項功能所公開的功能會在虛擬機器（VM）內部使用。</span><span class="sxs-lookup"><span data-stu-id="fc00c-119">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="fc00c-120">誤用這些方法可能會導致 VM 中未指定的行為。</span><span class="sxs-lookup"><span data-stu-id="fc00c-120">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="fc00c-121">例如，在 `EndPreventAsyncAbort` 沒有第一次呼叫的情況下呼叫， `BeginPreventAsyncAbort` 可能會在 VM 先前已遞增時，將計數器設定為零。</span><span class="sxs-lookup"><span data-stu-id="fc00c-121">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="fc00c-122">同樣地，內部計數器也不會檢查溢位。</span><span class="sxs-lookup"><span data-stu-id="fc00c-122">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="fc00c-123">如果它超過其整數限制，因為它是由主機和 VM 增加，則會未指定所產生的行為。</span><span class="sxs-lookup"><span data-stu-id="fc00c-123">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc00c-124">規格需求</span><span class="sxs-lookup"><span data-stu-id="fc00c-124">Requirements</span></span>  
 <span data-ttu-id="fc00c-125">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fc00c-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc00c-126">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="fc00c-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fc00c-127">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fc00c-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc00c-128">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc00c-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc00c-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc00c-129">See also</span></span>

- [<span data-ttu-id="fc00c-130">EndPreventAsyncAbort 方法</span><span class="sxs-lookup"><span data-stu-id="fc00c-130">EndPreventAsyncAbort Method</span></span>](iclrtask2-endpreventasyncabort-method.md)
- [<span data-ttu-id="fc00c-131">ICLRTask2 介面</span><span class="sxs-lookup"><span data-stu-id="fc00c-131">ICLRTask2 Interface</span></span>](iclrtask2-interface.md)
- [<span data-ttu-id="fc00c-132">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="fc00c-132">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="fc00c-133">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="fc00c-133">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="fc00c-134">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="fc00c-134">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="fc00c-135">裝載介面</span><span class="sxs-lookup"><span data-stu-id="fc00c-135">Hosting Interfaces</span></span>](hosting-interfaces.md)
