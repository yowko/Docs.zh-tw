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
ms.openlocfilehash: df20e98a9e88c10bac748a5acfc91adcb133da79
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762984"
---
# <a name="iclrtaskneedspriorityscheduling-method"></a><span data-ttu-id="f11b2-102">ICLRTask::NeedsPriorityScheduling 方法</span><span class="sxs-lookup"><span data-stu-id="f11b2-102">ICLRTask::NeedsPriorityScheduling Method</span></span>
<span data-ttu-id="f11b2-103">取得值，指出目前正在切換的工作是否需要標示為高優先順序以進行重新排定。</span><span class="sxs-lookup"><span data-stu-id="f11b2-103">Gets a value that indicates whether the current task, which is being switched out, needs to be marked as a high priority for rescheduling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f11b2-104">語法</span><span class="sxs-lookup"><span data-stu-id="f11b2-104">Syntax</span></span>  
  
```cpp  
HRESULT NeedsPriorityScheduling (  
    [out] BOOL *pbNeedsPriorityScheduling  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f11b2-105">參數</span><span class="sxs-lookup"><span data-stu-id="f11b2-105">Parameters</span></span>  
 `pbNeedsPriorityRescheduling`  
 <span data-ttu-id="f11b2-106">[out] `true` ，如果主機應該儘快嘗試重新排定目前的工作實例，則為，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="f11b2-106">[out] `true`, if the host should attempt to reschedule the current task instance as soon as possible; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f11b2-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="f11b2-107">Return Value</span></span>  
  
|<span data-ttu-id="f11b2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f11b2-108">HRESULT</span></span>|<span data-ttu-id="f11b2-109">Description</span><span class="sxs-lookup"><span data-stu-id="f11b2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f11b2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f11b2-110">S_OK</span></span>|<span data-ttu-id="f11b2-111">`NeedsPriorityRescheduling`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="f11b2-111">`NeedsPriorityRescheduling` returned successfully.</span></span>|  
|<span data-ttu-id="f11b2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f11b2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f11b2-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="f11b2-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f11b2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f11b2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f11b2-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="f11b2-115">The call timed out.</span></span>|  
|<span data-ttu-id="f11b2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f11b2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f11b2-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="f11b2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f11b2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f11b2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f11b2-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="f11b2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f11b2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f11b2-120">E_FAIL</span></span>|<span data-ttu-id="f11b2-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="f11b2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f11b2-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="f11b2-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f11b2-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="f11b2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f11b2-124">備註</span><span class="sxs-lookup"><span data-stu-id="f11b2-124">Remarks</span></span>  
 <span data-ttu-id="f11b2-125">在工作接近垃圾收集行程收集的情況下，CLR 會將的值設定 `pbNeedsPriorityScheduling` 為 `true` ，表示高優先順序的重新排程。</span><span class="sxs-lookup"><span data-stu-id="f11b2-125">In situations where the task is close to being collected by the garbage collector, the CLR sets the value of `pbNeedsPriorityScheduling` to `true`, indicating high-priority rescheduling.</span></span> <span data-ttu-id="f11b2-126">這可讓主機快速重新排程工作，藉此將垃圾收集延遲的可能性降到最低，並讓主機和執行時間能夠共同作業以節省記憶體資源。</span><span class="sxs-lookup"><span data-stu-id="f11b2-126">This allows the host to reschedule the task quickly, thereby minimizing the potential for delays in garbage collection, and enabling the host and the runtime to cooperate in conserving memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f11b2-127">規格需求</span><span class="sxs-lookup"><span data-stu-id="f11b2-127">Requirements</span></span>  
 <span data-ttu-id="f11b2-128">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f11b2-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f11b2-129">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="f11b2-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f11b2-130">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f11b2-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f11b2-131">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f11b2-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f11b2-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f11b2-132">See also</span></span>

- [<span data-ttu-id="f11b2-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="f11b2-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="f11b2-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="f11b2-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="f11b2-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="f11b2-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="f11b2-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="f11b2-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
