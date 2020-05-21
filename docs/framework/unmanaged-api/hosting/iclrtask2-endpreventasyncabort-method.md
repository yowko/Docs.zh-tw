---
title: ICLRTask2::EndPreventAsyncAbort 方法
ms.date: 03/30/2017
api_name:
- ICLRTask2.EndPreventAsyncAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2::EndPreventAsyncAbort
helpviewer_keywords:
- EndPreventAsyncAbort method [.NET Framework hosting]
- ICLRTask2::EndPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: d8013659-e3df-44b3-814f-a6b534ce62f8
topic_type:
- apiref
ms.openlocfilehash: 3ea36c56ef9ccf5886ba96191627e5283da186f7
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762848"
---
# <a name="iclrtask2endpreventasyncabort-method"></a><span data-ttu-id="a5b7c-102">ICLRTask2::EndPreventAsyncAbort 方法</span><span class="sxs-lookup"><span data-stu-id="a5b7c-102">ICLRTask2::EndPreventAsyncAbort Method</span></span>
<span data-ttu-id="a5b7c-103">允許新的或暫止的執行緒中止要求，導致目前線程上的執行緒中止。</span><span class="sxs-lookup"><span data-stu-id="a5b7c-103">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5b7c-104">語法</span><span class="sxs-lookup"><span data-stu-id="a5b7c-104">Syntax</span></span>  
  
```cpp  
HRESULT EndPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a5b7c-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="a5b7c-105">Return Value</span></span>  
 <span data-ttu-id="a5b7c-106">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="a5b7c-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a5b7c-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a5b7c-107">HRESULT</span></span>|<span data-ttu-id="a5b7c-108">Description</span><span class="sxs-lookup"><span data-stu-id="a5b7c-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a5b7c-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="a5b7c-109">S_OK</span></span>|<span data-ttu-id="a5b7c-110">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="a5b7c-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="a5b7c-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="a5b7c-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="a5b7c-112">在不是目前線程的執行緒上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="a5b7c-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5b7c-113">備註</span><span class="sxs-lookup"><span data-stu-id="a5b7c-113">Remarks</span></span>  
 <span data-ttu-id="a5b7c-114">呼叫這個方法會將目前線程的延遲線程中止計數器減一。</span><span class="sxs-lookup"><span data-stu-id="a5b7c-114">Calling this method decrements the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="a5b7c-115">呼叫[ICLRTask2：： BeginPreventAsyncAbort](iclrtask2-beginpreventasyncabort-method.md)和 `EndPreventAsyncAbort` 可以嵌套。</span><span class="sxs-lookup"><span data-stu-id="a5b7c-115">Calls to [ICLRTask2::BeginPreventAsyncAbort](iclrtask2-beginpreventasyncabort-method.md) and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="a5b7c-116">只要計數器大於零，就會延遲目前線程的執行緒中止。</span><span class="sxs-lookup"><span data-stu-id="a5b7c-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="a5b7c-117">這項功能所公開的功能會在虛擬機器（VM）內部使用。</span><span class="sxs-lookup"><span data-stu-id="a5b7c-117">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="a5b7c-118">誤用這些方法可能會導致 VM 中未指定的行為。</span><span class="sxs-lookup"><span data-stu-id="a5b7c-118">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="a5b7c-119">例如，在 `EndPreventAsyncAbort` 沒有第一次呼叫的情況下呼叫， `BeginPreventAsyncAbort` 可能會在 VM 先前已遞增時，將計數器設定為零。</span><span class="sxs-lookup"><span data-stu-id="a5b7c-119">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="a5b7c-120">同樣地，內部計數器也不會檢查溢位。</span><span class="sxs-lookup"><span data-stu-id="a5b7c-120">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="a5b7c-121">如果它超過其整數限制，因為它是由主機和 VM 增加，則會未指定所產生的行為。</span><span class="sxs-lookup"><span data-stu-id="a5b7c-121">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5b7c-122">規格需求</span><span class="sxs-lookup"><span data-stu-id="a5b7c-122">Requirements</span></span>  
 <span data-ttu-id="a5b7c-123">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a5b7c-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5b7c-124">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="a5b7c-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a5b7c-125">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a5b7c-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a5b7c-126">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5b7c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5b7c-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5b7c-127">See also</span></span>

- [<span data-ttu-id="a5b7c-128">BeginPreventAsyncAbort 方法</span><span class="sxs-lookup"><span data-stu-id="a5b7c-128">BeginPreventAsyncAbort Method</span></span>](iclrtask2-beginpreventasyncabort-method.md)
- [<span data-ttu-id="a5b7c-129">ICLRTask2 介面</span><span class="sxs-lookup"><span data-stu-id="a5b7c-129">ICLRTask2 Interface</span></span>](iclrtask2-interface.md)
- [<span data-ttu-id="a5b7c-130">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="a5b7c-130">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="a5b7c-131">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="a5b7c-131">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="a5b7c-132">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="a5b7c-132">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="a5b7c-133">裝載介面</span><span class="sxs-lookup"><span data-stu-id="a5b7c-133">Hosting Interfaces</span></span>](hosting-interfaces.md)
