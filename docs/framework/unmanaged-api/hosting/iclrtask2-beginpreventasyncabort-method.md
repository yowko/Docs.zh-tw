---
title: "ICLRTask2::BeginPreventAsyncAbort 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7bbbf609963f06e6c0204e8d44db30bb392886e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtask2beginpreventasyncabort-method"></a><span data-ttu-id="b2231-102">ICLRTask2::BeginPreventAsyncAbort 方法</span><span class="sxs-lookup"><span data-stu-id="b2231-102">ICLRTask2::BeginPreventAsyncAbort Method</span></span>
<span data-ttu-id="b2231-103">延遲新執行緒中止的要求結果的執行緒中止目前的執行緒上。</span><span class="sxs-lookup"><span data-stu-id="b2231-103">Delays new thread abort requests from resulting in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2231-104">語法</span><span class="sxs-lookup"><span data-stu-id="b2231-104">Syntax</span></span>  
  
```  
HRESULT BeginPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b2231-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="b2231-105">Return Value</span></span>  
 <span data-ttu-id="b2231-106">這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="b2231-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b2231-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b2231-107">HRESULT</span></span>|<span data-ttu-id="b2231-108">描述</span><span class="sxs-lookup"><span data-stu-id="b2231-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b2231-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="b2231-109">S_OK</span></span>|<span data-ttu-id="b2231-110">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="b2231-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="b2231-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="b2231-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="b2231-112">這不是目前執行緒的執行緒上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="b2231-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2231-113">備註</span><span class="sxs-lookup"><span data-stu-id="b2231-113">Remarks</span></span>  
 <span data-ttu-id="b2231-114">呼叫這個方法會延遲執行緒中止計數器目前的執行緒加一。</span><span class="sxs-lookup"><span data-stu-id="b2231-114">Calling this method increments the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="b2231-115">呼叫`BeginPreventAsyncAbort`和[iclrtask2:: Endpreventasyncabort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)可以巢狀。</span><span class="sxs-lookup"><span data-stu-id="b2231-115">Calls to `BeginPreventAsyncAbort` and [ICLRTask2::EndPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md) can be nested.</span></span> <span data-ttu-id="b2231-116">只要計數器是小於或等於零，執行緒中止目前的執行緒會延遲。</span><span class="sxs-lookup"><span data-stu-id="b2231-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span> <span data-ttu-id="b2231-117">如果此呼叫未成對的呼叫`EndPreventAsyncAbort`方法，您就能夠達到在哪一個執行緒中止無法傳遞至目前執行緒的狀態。</span><span class="sxs-lookup"><span data-stu-id="b2231-117">If this call is not paired with a call to the `EndPreventAsyncAbort` method, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="b2231-118">中止本身的執行緒不是接受的延遲。</span><span class="sxs-lookup"><span data-stu-id="b2231-118">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="b2231-119">這項功能所公開的功能是由虛擬機器 (VM) 內部使用。</span><span class="sxs-lookup"><span data-stu-id="b2231-119">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="b2231-120">不當使用這些方法可能導致 VM 未指定的行為。</span><span class="sxs-lookup"><span data-stu-id="b2231-120">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="b2231-121">例如，呼叫`EndPreventAsyncAbort`情況下先呼叫`BeginPreventAsyncAbort`VM 之前會遞增它時，無法設定計數器為零。</span><span class="sxs-lookup"><span data-stu-id="b2231-121">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="b2231-122">同樣地，內部計數器不會檢查溢位。</span><span class="sxs-lookup"><span data-stu-id="b2231-122">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="b2231-123">如果它超過其整數類資料的限制，因為主機和 VM，就會遞增，結果行為是未指定。</span><span class="sxs-lookup"><span data-stu-id="b2231-123">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2231-124">需求</span><span class="sxs-lookup"><span data-stu-id="b2231-124">Requirements</span></span>  
 <span data-ttu-id="b2231-125">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b2231-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2231-126">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b2231-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b2231-127">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b2231-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b2231-128">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2231-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2231-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="b2231-129">See Also</span></span>  
 [<span data-ttu-id="b2231-130">EndPreventAsyncAbort 方法</span><span class="sxs-lookup"><span data-stu-id="b2231-130">EndPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)  
 [<span data-ttu-id="b2231-131">ICLRTask2 介面</span><span class="sxs-lookup"><span data-stu-id="b2231-131">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 [<span data-ttu-id="b2231-132">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="b2231-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="b2231-133">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="b2231-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="b2231-134">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="b2231-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="b2231-135">裝載介面</span><span class="sxs-lookup"><span data-stu-id="b2231-135">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
