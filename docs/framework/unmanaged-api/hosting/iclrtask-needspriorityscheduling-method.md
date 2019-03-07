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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c5d061227e4094c96f14bd8f4f3e80e869b838a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487148"
---
# <a name="iclrtaskneedspriorityscheduling-method"></a><span data-ttu-id="337e3-102">ICLRTask::NeedsPriorityScheduling 方法</span><span class="sxs-lookup"><span data-stu-id="337e3-102">ICLRTask::NeedsPriorityScheduling Method</span></span>
<span data-ttu-id="337e3-103">取得值，指出目前的工作中，正在切換移出，是否需要標示為高優先順序的重新排程。</span><span class="sxs-lookup"><span data-stu-id="337e3-103">Gets a value that indicates whether the current task, which is being switched out, needs to be marked as a high priority for rescheduling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="337e3-104">語法</span><span class="sxs-lookup"><span data-stu-id="337e3-104">Syntax</span></span>  
  
```  
HRESULT NeedsPriorityScheduling (  
    [out] BOOL *pbNeedsPriorityScheduling  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="337e3-105">參數</span><span class="sxs-lookup"><span data-stu-id="337e3-105">Parameters</span></span>  
 `pbNeedsPriorityRescheduling`  
 <span data-ttu-id="337e3-106">[out]`true`，如果主應用程式應該嘗試重新排程目前的工作執行個體，儘速，否則`false`。</span><span class="sxs-lookup"><span data-stu-id="337e3-106">[out] `true`, if the host should attempt to reschedule the current task instance as soon as possible; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="337e3-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="337e3-107">Return Value</span></span>  
  
|<span data-ttu-id="337e3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="337e3-108">HRESULT</span></span>|<span data-ttu-id="337e3-109">描述</span><span class="sxs-lookup"><span data-stu-id="337e3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="337e3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="337e3-110">S_OK</span></span>|<span data-ttu-id="337e3-111">`NeedsPriorityRescheduling` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="337e3-111">`NeedsPriorityRescheduling` returned successfully.</span></span>|  
|<span data-ttu-id="337e3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="337e3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="337e3-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="337e3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="337e3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="337e3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="337e3-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="337e3-115">The call timed out.</span></span>|  
|<span data-ttu-id="337e3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="337e3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="337e3-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="337e3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="337e3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="337e3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="337e3-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="337e3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="337e3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="337e3-120">E_FAIL</span></span>|<span data-ttu-id="337e3-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="337e3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="337e3-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="337e3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="337e3-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="337e3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="337e3-124">備註</span><span class="sxs-lookup"><span data-stu-id="337e3-124">Remarks</span></span>  
 <span data-ttu-id="337e3-125">在工作即將由記憶體回收行程所收集的情況下，CLR 會設定的值`pbNeedsPriorityScheduling`至`true`，指出重新排定高優先順序。</span><span class="sxs-lookup"><span data-stu-id="337e3-125">In situations where the task is close to being collected by the garbage collector, the CLR sets the value of `pbNeedsPriorityScheduling` to `true`, indicating high-priority rescheduling.</span></span> <span data-ttu-id="337e3-126">這可讓主應用程式快速地重新排程工作，藉此降至最低的可能延遲，在記憶體回收，並讓主應用程式和執行階段一起合作，以節省記憶體資源。</span><span class="sxs-lookup"><span data-stu-id="337e3-126">This allows the host to reschedule the task quickly, thereby minimizing the potential for delays in garbage collection, and enabling the host and the runtime to cooperate in conserving memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="337e3-127">需求</span><span class="sxs-lookup"><span data-stu-id="337e3-127">Requirements</span></span>  
 <span data-ttu-id="337e3-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="337e3-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="337e3-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="337e3-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="337e3-130">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="337e3-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="337e3-131">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="337e3-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="337e3-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="337e3-132">See also</span></span>
- [<span data-ttu-id="337e3-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="337e3-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="337e3-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="337e3-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="337e3-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="337e3-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="337e3-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="337e3-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
