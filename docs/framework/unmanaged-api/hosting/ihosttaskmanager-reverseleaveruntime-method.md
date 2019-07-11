---
title: IHostTaskManager::ReverseLeaveRuntime 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.ReverseLeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::ReverseLeaveRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseLeaveRuntime method [.NET Framework hosting]
- ReverseLeaveRuntime method [.NET Framework hosting]
ms.assetid: 4837d398-16a1-4e32-902c-022cd1aad3ca
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 920aecab03e386a48f59843b26610cf260419293
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749450"
---
# <a name="ihosttaskmanagerreverseleaveruntime-method"></a><span data-ttu-id="48891-102">IHostTaskManager::ReverseLeaveRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="48891-102">IHostTaskManager::ReverseLeaveRuntime Method</span></span>
<span data-ttu-id="48891-103">控制會讓 common language runtime (CLR)，並輸入 unmanaged 函式，接著呼叫函式從 managed 程式碼，請通知主機。</span><span class="sxs-lookup"><span data-stu-id="48891-103">Notifies the host that control is leaving the common language runtime (CLR) and entering an unmanaged function that was, in turn, called from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48891-104">語法</span><span class="sxs-lookup"><span data-stu-id="48891-104">Syntax</span></span>  
  
```cpp  
HRESULT ReverseLeaveRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="48891-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="48891-105">Return Value</span></span>  
  
|<span data-ttu-id="48891-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="48891-106">HRESULT</span></span>|<span data-ttu-id="48891-107">描述</span><span class="sxs-lookup"><span data-stu-id="48891-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="48891-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="48891-108">S_OK</span></span>|<span data-ttu-id="48891-109">`ReverseLeaveRuntime` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="48891-109">`ReverseLeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="48891-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="48891-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="48891-111">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="48891-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="48891-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="48891-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="48891-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="48891-113">The call timed out.</span></span>|  
|<span data-ttu-id="48891-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="48891-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="48891-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="48891-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="48891-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="48891-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="48891-117">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="48891-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="48891-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="48891-118">E_FAIL</span></span>|<span data-ttu-id="48891-119">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="48891-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="48891-120">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="48891-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="48891-121">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="48891-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="48891-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="48891-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="48891-123">沒有足夠的記憶體可完成要求的資源配置。</span><span class="sxs-lookup"><span data-stu-id="48891-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48891-124">備註</span><span class="sxs-lookup"><span data-stu-id="48891-124">Remarks</span></span>  
 <span data-ttu-id="48891-125">CLR 會呼叫`ReverseLeaveRuntime`通知的主應用程式目前正在執行的工作會傳回控制項至 unmanaged 函式，接著呼叫函式從 managed 程式碼，透過平台叫用。</span><span class="sxs-lookup"><span data-stu-id="48891-125">The CLR calls `ReverseLeaveRuntime` to inform the host that the currently executing task is returning control to an unmanaged function that was, in turn, called from managed code through platform invoke.</span></span> <span data-ttu-id="48891-126">每次呼叫`ReverseLeaveRuntime`符合對應呼叫[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)。</span><span class="sxs-lookup"><span data-stu-id="48891-126">Each call to `ReverseLeaveRuntime` matches a corresponding call to [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48891-127">需求</span><span class="sxs-lookup"><span data-stu-id="48891-127">Requirements</span></span>  
 <span data-ttu-id="48891-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="48891-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48891-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="48891-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="48891-130">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="48891-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="48891-131">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48891-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48891-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48891-132">See also</span></span>

- [<span data-ttu-id="48891-133">CallNeedsHostHook 方法</span><span class="sxs-lookup"><span data-stu-id="48891-133">CallNeedsHostHook Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)
- [<span data-ttu-id="48891-134">EnterRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="48891-134">EnterRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)
- [<span data-ttu-id="48891-135">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="48891-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="48891-136">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="48891-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="48891-137">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="48891-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="48891-138">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="48891-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="48891-139">LeaveRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="48891-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
- <span data-ttu-id="48891-140">[詳述平台叫用](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="48891-140">[A Closer Look at Platform Invoke](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span></span>
