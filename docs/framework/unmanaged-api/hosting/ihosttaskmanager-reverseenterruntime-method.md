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
ms.openlocfilehash: 41955bd2f64d53e3620dede6b6da4cef2aab45f4
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842292"
---
# <a name="ihosttaskmanagerreverseenterruntime-method"></a><span data-ttu-id="4cee3-102">IHostTaskManager::ReverseEnterRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="4cee3-102">IHostTaskManager::ReverseEnterRuntime Method</span></span>
<span data-ttu-id="4cee3-103">通知主機正在從非受控碼對 common language runtime （CLR）進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="4cee3-103">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cee3-104">語法</span><span class="sxs-lookup"><span data-stu-id="4cee3-104">Syntax</span></span>  
  
```cpp  
HRESULT ReverseEnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="4cee3-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="4cee3-105">Return Value</span></span>  
  
|<span data-ttu-id="4cee3-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4cee3-106">HRESULT</span></span>|<span data-ttu-id="4cee3-107">描述</span><span class="sxs-lookup"><span data-stu-id="4cee3-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4cee3-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="4cee3-108">S_OK</span></span>|<span data-ttu-id="4cee3-109">`ReverseEnterRuntime`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="4cee3-109">`ReverseEnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="4cee3-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4cee3-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4cee3-111">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="4cee3-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4cee3-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4cee3-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4cee3-113">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="4cee3-113">The call timed out.</span></span>|  
|<span data-ttu-id="4cee3-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4cee3-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4cee3-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="4cee3-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4cee3-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4cee3-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4cee3-117">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="4cee3-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4cee3-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4cee3-118">E_FAIL</span></span>|<span data-ttu-id="4cee3-119">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="4cee3-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4cee3-120">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="4cee3-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4cee3-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="4cee3-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4cee3-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="4cee3-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="4cee3-123">沒有足夠的記憶體可用來完成要求的資源配置。</span><span class="sxs-lookup"><span data-stu-id="4cee3-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4cee3-124">備註</span><span class="sxs-lookup"><span data-stu-id="4cee3-124">Remarks</span></span>  
 <span data-ttu-id="4cee3-125">如果從衍生自 managed 程式碼的序列發出對 CLR 的呼叫，則每個呼叫都會 `ReverseEnterRuntime` 對應至[ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md)的呼叫。</span><span class="sxs-lookup"><span data-stu-id="4cee3-125">If the call into the CLR is made from a sequence that originated in managed code, each call to `ReverseEnterRuntime` corresponds to a call to [ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4cee3-126">呼叫可能是來自非受控程式碼，而不需要加以嵌套。</span><span class="sxs-lookup"><span data-stu-id="4cee3-126">Calls can originate from unmanaged code without being nested.</span></span> <span data-ttu-id="4cee3-127">在此情況下，不會呼叫[EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)、 [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md)或 `ReverseLeaveRuntime` ，而且呼叫的數目 `ReverseEnterRuntime` 不等於的呼叫次數 `ReverseLeaveRuntime` 。</span><span class="sxs-lookup"><span data-stu-id="4cee3-127">In this case, there is no call to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md), or `ReverseLeaveRuntime`, and the number of calls to `ReverseEnterRuntime` does not equal the number of calls to `ReverseLeaveRuntime`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cee3-128">規格需求</span><span class="sxs-lookup"><span data-stu-id="4cee3-128">Requirements</span></span>  
 <span data-ttu-id="4cee3-129">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4cee3-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cee3-130">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="4cee3-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4cee3-131">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4cee3-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4cee3-132">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cee3-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cee3-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4cee3-133">See also</span></span>

- [<span data-ttu-id="4cee3-134">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="4cee3-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="4cee3-135">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="4cee3-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="4cee3-136">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="4cee3-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="4cee3-137">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="4cee3-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
