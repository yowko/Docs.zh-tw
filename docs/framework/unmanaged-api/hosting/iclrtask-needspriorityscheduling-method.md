---
title: ICLRTask::NeedsPriorityScheduling 方法
ms.date: 03/30/2017
api_name:
- ICLRTask.NeedsPriorityScheduling
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::NeedsPriorityScheduling
helpviewer_keywords:
- ICLRTask::NeedsPriorityScheduling method [.NET Framework hosting]
- NeedsPriorityScheduling method [.NET Framework hosting]
ms.assetid: 9c9db3f3-26bf-4317-88de-5eb926a22a1d
topic_type:
- apiref
ms.openlocfilehash: 86e0899b883f09f2e7b27c0f957e943deb73bb66
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690794"
---
# <a name="iclrtaskneedspriorityscheduling-method"></a><span data-ttu-id="5d108-102">ICLRTask::NeedsPriorityScheduling 方法</span><span class="sxs-lookup"><span data-stu-id="5d108-102">ICLRTask::NeedsPriorityScheduling Method</span></span>

<span data-ttu-id="5d108-103">取得值，這個值會指出目前正在切換的工作是否需要標示為高優先順序的重新排程。</span><span class="sxs-lookup"><span data-stu-id="5d108-103">Gets a value that indicates whether the current task, which is being switched out, needs to be marked as a high priority for rescheduling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d108-104">語法</span><span class="sxs-lookup"><span data-stu-id="5d108-104">Syntax</span></span>  
  
```cpp  
HRESULT NeedsPriorityScheduling (  
    [out] BOOL *pbNeedsPriorityScheduling  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d108-105">參數</span><span class="sxs-lookup"><span data-stu-id="5d108-105">Parameters</span></span>  

 `pbNeedsPriorityRescheduling`  
 <span data-ttu-id="5d108-106">[out] `true` ，如果主機應該儘快嘗試重新排定目前的工作實例，則為，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="5d108-106">[out] `true`, if the host should attempt to reschedule the current task instance as soon as possible; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d108-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="5d108-107">Return Value</span></span>  
  
|<span data-ttu-id="5d108-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5d108-108">HRESULT</span></span>|<span data-ttu-id="5d108-109">描述</span><span class="sxs-lookup"><span data-stu-id="5d108-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5d108-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5d108-110">S_OK</span></span>|<span data-ttu-id="5d108-111">`NeedsPriorityRescheduling` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="5d108-111">`NeedsPriorityRescheduling` returned successfully.</span></span>|  
|<span data-ttu-id="5d108-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5d108-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5d108-113">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="5d108-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5d108-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5d108-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5d108-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="5d108-115">The call timed out.</span></span>|  
|<span data-ttu-id="5d108-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5d108-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5d108-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="5d108-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5d108-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5d108-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5d108-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="5d108-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5d108-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5d108-120">E_FAIL</span></span>|<span data-ttu-id="5d108-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="5d108-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5d108-122">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="5d108-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5d108-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="5d108-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d108-124">備註</span><span class="sxs-lookup"><span data-stu-id="5d108-124">Remarks</span></span>  

 <span data-ttu-id="5d108-125">在垃圾收集行程即將收集工作的情況下，CLR 會將的值設定 `pbNeedsPriorityScheduling` 為 `true` ，指出高優先順序的重新排程。</span><span class="sxs-lookup"><span data-stu-id="5d108-125">In situations where the task is close to being collected by the garbage collector, the CLR sets the value of `pbNeedsPriorityScheduling` to `true`, indicating high-priority rescheduling.</span></span> <span data-ttu-id="5d108-126">如此一來，主機就可以快速地重新排程工作，藉此將垃圾收集延遲的可能性降至最低，並讓主控制項和執行時間共同工作以節省記憶體資源。</span><span class="sxs-lookup"><span data-stu-id="5d108-126">This allows the host to reschedule the task quickly, thereby minimizing the potential for delays in garbage collection, and enabling the host and the runtime to cooperate in conserving memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d108-127">需求</span><span class="sxs-lookup"><span data-stu-id="5d108-127">Requirements</span></span>  

 <span data-ttu-id="5d108-128">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5d108-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d108-129">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="5d108-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5d108-130">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="5d108-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5d108-131">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d108-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d108-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d108-132">See also</span></span>

- [<span data-ttu-id="5d108-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="5d108-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="5d108-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="5d108-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="5d108-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="5d108-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="5d108-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="5d108-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
