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
ms.openlocfilehash: 91c1ea51969447861ff6d0956c5714baa0054450
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124661"
---
# <a name="iclrtaskneedspriorityscheduling-method"></a><span data-ttu-id="0e673-102">ICLRTask::NeedsPriorityScheduling 方法</span><span class="sxs-lookup"><span data-stu-id="0e673-102">ICLRTask::NeedsPriorityScheduling Method</span></span>
<span data-ttu-id="0e673-103">取得值，指出目前正在切換的工作是否需要標示為高優先順序以進行重新排定。</span><span class="sxs-lookup"><span data-stu-id="0e673-103">Gets a value that indicates whether the current task, which is being switched out, needs to be marked as a high priority for rescheduling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e673-104">語法</span><span class="sxs-lookup"><span data-stu-id="0e673-104">Syntax</span></span>  
  
```cpp  
HRESULT NeedsPriorityScheduling (  
    [out] BOOL *pbNeedsPriorityScheduling  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e673-105">參數</span><span class="sxs-lookup"><span data-stu-id="0e673-105">Parameters</span></span>  
 `pbNeedsPriorityRescheduling`  
 <span data-ttu-id="0e673-106">[out] `true`，如果主機應該儘快嘗試重新排定目前的工作實例;否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="0e673-106">[out] `true`, if the host should attempt to reschedule the current task instance as soon as possible; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0e673-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="0e673-107">Return Value</span></span>  
  
|<span data-ttu-id="0e673-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0e673-108">HRESULT</span></span>|<span data-ttu-id="0e673-109">描述</span><span class="sxs-lookup"><span data-stu-id="0e673-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0e673-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0e673-110">S_OK</span></span>|<span data-ttu-id="0e673-111">已成功傳回 `NeedsPriorityRescheduling`。</span><span class="sxs-lookup"><span data-stu-id="0e673-111">`NeedsPriorityRescheduling` returned successfully.</span></span>|  
|<span data-ttu-id="0e673-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0e673-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0e673-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="0e673-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0e673-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0e673-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0e673-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="0e673-115">The call timed out.</span></span>|  
|<span data-ttu-id="0e673-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0e673-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0e673-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="0e673-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0e673-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0e673-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0e673-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="0e673-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0e673-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0e673-120">E_FAIL</span></span>|<span data-ttu-id="0e673-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="0e673-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0e673-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="0e673-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0e673-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="0e673-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e673-124">備註</span><span class="sxs-lookup"><span data-stu-id="0e673-124">Remarks</span></span>  
 <span data-ttu-id="0e673-125">在工作接近垃圾收集行程收集的情況下，CLR 會將 `pbNeedsPriorityScheduling` 的值設定為 `true`，表示高優先順序的重新排定。</span><span class="sxs-lookup"><span data-stu-id="0e673-125">In situations where the task is close to being collected by the garbage collector, the CLR sets the value of `pbNeedsPriorityScheduling` to `true`, indicating high-priority rescheduling.</span></span> <span data-ttu-id="0e673-126">這可讓主機快速重新排程工作，藉此將垃圾收集延遲的可能性降到最低，並讓主機和執行時間能夠共同作業以節省記憶體資源。</span><span class="sxs-lookup"><span data-stu-id="0e673-126">This allows the host to reschedule the task quickly, thereby minimizing the potential for delays in garbage collection, and enabling the host and the runtime to cooperate in conserving memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e673-127">需求</span><span class="sxs-lookup"><span data-stu-id="0e673-127">Requirements</span></span>  
 <span data-ttu-id="0e673-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0e673-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e673-129">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="0e673-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0e673-130">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0e673-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0e673-131">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e673-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e673-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="0e673-132">See also</span></span>

- [<span data-ttu-id="0e673-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="0e673-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="0e673-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="0e673-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="0e673-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="0e673-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="0e673-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="0e673-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
