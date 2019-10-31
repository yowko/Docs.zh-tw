---
title: IHostTaskManager::ReverseEnterRuntime 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.ReverseEnterRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::ReverseEnterRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseEnterRuntime method [.NET Framework hosting]
- ReverseEnterRuntime method [.NET Framework hosting]
ms.assetid: b1e26bff-d3ea-436e-9867-29720df999f4
topic_type:
- apiref
ms.openlocfilehash: 390a29760c0f3680ca082561607ab678e8bd1e8b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133001"
---
# <a name="ihosttaskmanagerreverseenterruntime-method"></a><span data-ttu-id="44ce2-102">IHostTaskManager::ReverseEnterRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="44ce2-102">IHostTaskManager::ReverseEnterRuntime Method</span></span>
<span data-ttu-id="44ce2-103">通知主機正在從非受控碼對 common language runtime （CLR）進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="44ce2-103">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44ce2-104">語法</span><span class="sxs-lookup"><span data-stu-id="44ce2-104">Syntax</span></span>  
  
```cpp  
HRESULT ReverseEnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="44ce2-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="44ce2-105">Return Value</span></span>  
  
|<span data-ttu-id="44ce2-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="44ce2-106">HRESULT</span></span>|<span data-ttu-id="44ce2-107">描述</span><span class="sxs-lookup"><span data-stu-id="44ce2-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="44ce2-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="44ce2-108">S_OK</span></span>|<span data-ttu-id="44ce2-109">已成功傳回 `ReverseEnterRuntime`。</span><span class="sxs-lookup"><span data-stu-id="44ce2-109">`ReverseEnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="44ce2-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="44ce2-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="44ce2-111">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="44ce2-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="44ce2-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="44ce2-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="44ce2-113">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="44ce2-113">The call timed out.</span></span>|  
|<span data-ttu-id="44ce2-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="44ce2-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="44ce2-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="44ce2-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="44ce2-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="44ce2-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="44ce2-117">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="44ce2-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="44ce2-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="44ce2-118">E_FAIL</span></span>|<span data-ttu-id="44ce2-119">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="44ce2-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="44ce2-120">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="44ce2-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="44ce2-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="44ce2-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="44ce2-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="44ce2-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="44ce2-123">沒有足夠的記憶體可用來完成要求的資源配置。</span><span class="sxs-lookup"><span data-stu-id="44ce2-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44ce2-124">備註</span><span class="sxs-lookup"><span data-stu-id="44ce2-124">Remarks</span></span>  
 <span data-ttu-id="44ce2-125">如果從衍生自 managed 程式碼的序列發出對 CLR 的呼叫，則每次呼叫 `ReverseEnterRuntime` 都會對應至[ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)的呼叫。</span><span class="sxs-lookup"><span data-stu-id="44ce2-125">If the call into the CLR is made from a sequence that originated in managed code, each call to `ReverseEnterRuntime` corresponds to a call to [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="44ce2-126">呼叫可能是來自非受控程式碼，而不需要加以嵌套。</span><span class="sxs-lookup"><span data-stu-id="44ce2-126">Calls can originate from unmanaged code without being nested.</span></span> <span data-ttu-id="44ce2-127">在此情況下，不會呼叫[EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)、 [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)或 `ReverseLeaveRuntime`，而且 `ReverseEnterRuntime` 的呼叫數目不等於 `ReverseLeaveRuntime`的呼叫數目。</span><span class="sxs-lookup"><span data-stu-id="44ce2-127">In this case, there is no call to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), or `ReverseLeaveRuntime`, and the number of calls to `ReverseEnterRuntime` does not equal the number of calls to `ReverseLeaveRuntime`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44ce2-128">需求</span><span class="sxs-lookup"><span data-stu-id="44ce2-128">Requirements</span></span>  
 <span data-ttu-id="44ce2-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="44ce2-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44ce2-130">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="44ce2-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="44ce2-131">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="44ce2-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44ce2-132">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44ce2-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44ce2-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="44ce2-133">See also</span></span>

- [<span data-ttu-id="44ce2-134">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="44ce2-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="44ce2-135">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="44ce2-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="44ce2-136">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="44ce2-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="44ce2-137">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="44ce2-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
