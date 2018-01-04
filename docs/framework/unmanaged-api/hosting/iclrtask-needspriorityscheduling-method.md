---
title: "ICLRTask::NeedsPriorityScheduling 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.NeedsPriorityScheduling
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::NeedsPriorityScheduling
helpviewer_keywords:
- ICLRTask::NeedsPriorityScheduling method [.NET Framework hosting]
- NeedsPriorityScheduling method [.NET Framework hosting]
ms.assetid: 9c9db3f3-26bf-4317-88de-5eb926a22a1d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6ce57a4130c19ffd040bc9fbeba5e775a751efdb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskneedspriorityscheduling-method"></a><span data-ttu-id="d5165-102">ICLRTask::NeedsPriorityScheduling 方法</span><span class="sxs-lookup"><span data-stu-id="d5165-102">ICLRTask::NeedsPriorityScheduling Method</span></span>
<span data-ttu-id="d5165-103">取得值，指出目前的工作中，要切換移出，是否需要標示為高優先順序的重新排程。</span><span class="sxs-lookup"><span data-stu-id="d5165-103">Gets a value that indicates whether the current task, which is being switched out, needs to be marked as a high priority for rescheduling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5165-104">語法</span><span class="sxs-lookup"><span data-stu-id="d5165-104">Syntax</span></span>  
  
```  
HRESULT NeedsPriorityScheduling (  
    [out] BOOL *pbNeedsPriorityScheduling  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d5165-105">參數</span><span class="sxs-lookup"><span data-stu-id="d5165-105">Parameters</span></span>  
 `pbNeedsPriorityRescheduling`  
 <span data-ttu-id="d5165-106">[out]`true`，主機應嘗試重新排程目前的工作執行個體，儘速; 否則如果`false`。</span><span class="sxs-lookup"><span data-stu-id="d5165-106">[out] `true`, if the host should attempt to reschedule the current task instance as soon as possible; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5165-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="d5165-107">Return Value</span></span>  
  
|<span data-ttu-id="d5165-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d5165-108">HRESULT</span></span>|<span data-ttu-id="d5165-109">描述</span><span class="sxs-lookup"><span data-stu-id="d5165-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d5165-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d5165-110">S_OK</span></span>|<span data-ttu-id="d5165-111">`NeedsPriorityRescheduling`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="d5165-111">`NeedsPriorityRescheduling` returned successfully.</span></span>|  
|<span data-ttu-id="d5165-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d5165-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d5165-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="d5165-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d5165-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d5165-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d5165-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="d5165-115">The call timed out.</span></span>|  
|<span data-ttu-id="d5165-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d5165-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d5165-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="d5165-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d5165-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d5165-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d5165-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="d5165-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d5165-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d5165-120">E_FAIL</span></span>|<span data-ttu-id="d5165-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="d5165-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d5165-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="d5165-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d5165-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d5165-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5165-124">備註</span><span class="sxs-lookup"><span data-stu-id="d5165-124">Remarks</span></span>  
 <span data-ttu-id="d5165-125">在工作即將被記憶體回收行程所收集的情況下，CLR 會設定的值`pbNeedsPriorityScheduling`至`true`，表示高優先順序重新排程。</span><span class="sxs-lookup"><span data-stu-id="d5165-125">In situations where the task is close to being collected by the garbage collector, the CLR sets the value of `pbNeedsPriorityScheduling` to `true`, indicating high-priority rescheduling.</span></span> <span data-ttu-id="d5165-126">這可讓快速，重新排定工作主機，藉以降到最低的可能延遲在記憶體回收，並啟用主機和執行階段一起合作，以節省記憶體資源。</span><span class="sxs-lookup"><span data-stu-id="d5165-126">This allows the host to reschedule the task quickly, thereby minimizing the potential for delays in garbage collection, and enabling the host and the runtime to cooperate in conserving memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5165-127">需求</span><span class="sxs-lookup"><span data-stu-id="d5165-127">Requirements</span></span>  
 <span data-ttu-id="d5165-128">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d5165-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5165-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d5165-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d5165-130">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d5165-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d5165-131">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5165-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5165-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="d5165-132">See Also</span></span>  
 [<span data-ttu-id="d5165-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="d5165-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="d5165-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="d5165-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="d5165-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="d5165-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="d5165-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="d5165-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
