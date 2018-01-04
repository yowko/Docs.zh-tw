---
title: "IHostTaskManager::ReverseLeaveRuntime 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.ReverseLeaveRuntime
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::ReverseLeaveRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseLeaveRuntime method [.NET Framework hosting]
- ReverseLeaveRuntime method [.NET Framework hosting]
ms.assetid: 4837d398-16a1-4e32-902c-022cd1aad3ca
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa16e640cade9304916650c4ea13231cacb967f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagerreverseleaveruntime-method"></a><span data-ttu-id="01287-102">IHostTaskManager::ReverseLeaveRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="01287-102">IHostTaskManager::ReverseLeaveRuntime Method</span></span>
<span data-ttu-id="01287-103">通知主機，控制會讓 common language runtime (CLR)，並輸入，接著，從 managed 程式碼呼叫 unmanaged 函式。</span><span class="sxs-lookup"><span data-stu-id="01287-103">Notifies the host that control is leaving the common language runtime (CLR) and entering an unmanaged function that was, in turn, called from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01287-104">語法</span><span class="sxs-lookup"><span data-stu-id="01287-104">Syntax</span></span>  
  
```  
HRESULT ReverseLeaveRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="01287-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="01287-105">Return Value</span></span>  
  
|<span data-ttu-id="01287-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="01287-106">HRESULT</span></span>|<span data-ttu-id="01287-107">描述</span><span class="sxs-lookup"><span data-stu-id="01287-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="01287-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="01287-108">S_OK</span></span>|<span data-ttu-id="01287-109">`ReverseLeaveRuntime`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="01287-109">`ReverseLeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="01287-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="01287-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="01287-111">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="01287-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="01287-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="01287-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="01287-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="01287-113">The call timed out.</span></span>|  
|<span data-ttu-id="01287-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="01287-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="01287-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="01287-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="01287-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="01287-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="01287-117">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="01287-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="01287-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="01287-118">E_FAIL</span></span>|<span data-ttu-id="01287-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="01287-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="01287-120">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="01287-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="01287-121">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="01287-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="01287-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="01287-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="01287-123">沒有足夠的記憶體可完成要求的資源配置。</span><span class="sxs-lookup"><span data-stu-id="01287-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01287-124">備註</span><span class="sxs-lookup"><span data-stu-id="01287-124">Remarks</span></span>  
 <span data-ttu-id="01287-125">CLR 會呼叫`ReverseLeaveRuntime`通知所傳回的目前執行的工作主機控制項 unmanaged 呼叫函式，接著，從 managed 程式碼可透過平台叫用。</span><span class="sxs-lookup"><span data-stu-id="01287-125">The CLR calls `ReverseLeaveRuntime` to inform the host that the currently executing task is returning control to an unmanaged function that was, in turn, called from managed code through platform invoke.</span></span> <span data-ttu-id="01287-126">每次呼叫`ReverseLeaveRuntime`符合對應呼叫[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)。</span><span class="sxs-lookup"><span data-stu-id="01287-126">Each call to `ReverseLeaveRuntime` matches a corresponding call to [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01287-127">需求</span><span class="sxs-lookup"><span data-stu-id="01287-127">Requirements</span></span>  
 <span data-ttu-id="01287-128">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="01287-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01287-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="01287-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="01287-130">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="01287-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="01287-131">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01287-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01287-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="01287-132">See Also</span></span>  
 [<span data-ttu-id="01287-133">CallNeedsHostHook 方法</span><span class="sxs-lookup"><span data-stu-id="01287-133">CallNeedsHostHook Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)  
 [<span data-ttu-id="01287-134">EnterRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="01287-134">EnterRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)  
 [<span data-ttu-id="01287-135">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="01287-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="01287-136">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="01287-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="01287-137">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="01287-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="01287-138">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="01287-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="01287-139">LeaveRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="01287-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)  
 [<span data-ttu-id="01287-140">詳述平台叫用</span><span class="sxs-lookup"><span data-stu-id="01287-140">A Closer Look at Platform Invoke</span></span>](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)
