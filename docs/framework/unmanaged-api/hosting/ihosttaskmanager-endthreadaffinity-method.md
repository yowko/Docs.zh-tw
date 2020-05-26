---
title: IHostTaskManager::EndThreadAffinity 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndThreadAffinity
helpviewer_keywords:
- EndThreadAffinity method [.NET Framework hosting]
- IHostTaskManager::EndThreadAffinity method [.NET Framework hosting]
ms.assetid: 7738a904-0cd7-4fde-a3eb-2323a5533157
topic_type:
- apiref
ms.openlocfilehash: 2e857f951a837e1385d02dfc810fc12cfefd0d2b
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841954"
---
# <a name="ihosttaskmanagerendthreadaffinity-method"></a><span data-ttu-id="6dea4-102">IHostTaskManager::EndThreadAffinity 方法</span><span class="sxs-lookup"><span data-stu-id="6dea4-102">IHostTaskManager::EndThreadAffinity Method</span></span>
<span data-ttu-id="6dea4-103">遵循先前對[IHostTaskManager：： BeginThreadAffinity](ihosttaskmanager-beginthreadaffinity-method.md)的呼叫，通知主機 managed 程式碼即將結束，但目前的工作不得移至另一個作業系統執行緒。</span><span class="sxs-lookup"><span data-stu-id="6dea4-103">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to [IHostTaskManager::BeginThreadAffinity](ihosttaskmanager-beginthreadaffinity-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dea4-104">語法</span><span class="sxs-lookup"><span data-stu-id="6dea4-104">Syntax</span></span>  
  
```cpp  
HRESULT EndThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="6dea4-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="6dea4-105">Return Value</span></span>  
  
|<span data-ttu-id="6dea4-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6dea4-106">HRESULT</span></span>|<span data-ttu-id="6dea4-107">描述</span><span class="sxs-lookup"><span data-stu-id="6dea4-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6dea4-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="6dea4-108">S_OK</span></span>|<span data-ttu-id="6dea4-109">`EndThreadAffinity`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="6dea4-109">`EndThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="6dea4-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6dea4-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6dea4-111">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="6dea4-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6dea4-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6dea4-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6dea4-113">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="6dea4-113">The call timed out.</span></span>|  
|<span data-ttu-id="6dea4-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6dea4-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6dea4-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="6dea4-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6dea4-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6dea4-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6dea4-117">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="6dea4-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6dea4-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6dea4-118">E_FAIL</span></span>|<span data-ttu-id="6dea4-119">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="6dea4-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6dea4-120">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="6dea4-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6dea4-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="6dea4-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6dea4-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="6dea4-122">E_UNEXPECTED</span></span>|<span data-ttu-id="6dea4-123">`EndThreadAffinity`已呼叫，但沒有稍早對應的呼叫 `BeginThreadAffinity` 。</span><span class="sxs-lookup"><span data-stu-id="6dea4-123">`EndThreadAffinity` was called without an earlier corresponding call to `BeginThreadAffinity`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6dea4-124">備註</span><span class="sxs-lookup"><span data-stu-id="6dea4-124">Remarks</span></span>  
 <span data-ttu-id="6dea4-125">在呼叫之前，CLR 會對目前的工作進行相對應的呼叫 `BeginThreadAffinity` `EndThreadAffinity` 。</span><span class="sxs-lookup"><span data-stu-id="6dea4-125">The CLR makes a corresponding call to `BeginThreadAffinity` on the current task before calling `EndThreadAffinity`.</span></span> <span data-ttu-id="6dea4-126">如果沒有這類對應的呼叫，主機的[IHostTaskManager](ihosttaskmanager-interface.md)應該會傳回 E_UNEXPECTED，而且不採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="6dea4-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](ihosttaskmanager-interface.md) should return E_UNEXPECTED, and take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dea4-127">規格需求</span><span class="sxs-lookup"><span data-stu-id="6dea4-127">Requirements</span></span>  
 <span data-ttu-id="6dea4-128">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6dea4-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6dea4-129">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="6dea4-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6dea4-130">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6dea4-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6dea4-131">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6dea4-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dea4-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6dea4-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="6dea4-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="6dea4-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="6dea4-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="6dea4-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="6dea4-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="6dea4-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="6dea4-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="6dea4-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
