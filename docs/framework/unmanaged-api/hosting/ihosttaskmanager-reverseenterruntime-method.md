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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6eefdaf5dee423b0a9ae054446224a3ea97e3c9b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796664"
---
# <a name="ihosttaskmanagerreverseenterruntime-method"></a><span data-ttu-id="38111-102">IHostTaskManager::ReverseEnterRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="38111-102">IHostTaskManager::ReverseEnterRuntime Method</span></span>
<span data-ttu-id="38111-103">主應用程式到從 unmanaged 程式碼的 common language runtime (CLR) 進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="38111-103">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38111-104">語法</span><span class="sxs-lookup"><span data-stu-id="38111-104">Syntax</span></span>  
  
```  
HRESULT ReverseEnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="38111-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="38111-105">Return Value</span></span>  
  
|<span data-ttu-id="38111-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="38111-106">HRESULT</span></span>|<span data-ttu-id="38111-107">描述</span><span class="sxs-lookup"><span data-stu-id="38111-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="38111-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="38111-108">S_OK</span></span>|<span data-ttu-id="38111-109">`ReverseEnterRuntime` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="38111-109">`ReverseEnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="38111-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="38111-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="38111-111">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="38111-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="38111-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="38111-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="38111-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="38111-113">The call timed out.</span></span>|  
|<span data-ttu-id="38111-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="38111-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="38111-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="38111-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="38111-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="38111-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="38111-117">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="38111-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="38111-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="38111-118">E_FAIL</span></span>|<span data-ttu-id="38111-119">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="38111-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="38111-120">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="38111-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="38111-121">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="38111-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="38111-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="38111-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="38111-123">沒有足夠的記憶體可完成要求的資源配置。</span><span class="sxs-lookup"><span data-stu-id="38111-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38111-124">備註</span><span class="sxs-lookup"><span data-stu-id="38111-124">Remarks</span></span>  
 <span data-ttu-id="38111-125">如果 clr 呼叫的順序，產生從 managed 程式碼中，每個呼叫`ReverseEnterRuntime`對應至呼叫[ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)。</span><span class="sxs-lookup"><span data-stu-id="38111-125">If the call into the CLR is made from a sequence that originated in managed code, each call to `ReverseEnterRuntime` corresponds to a call to [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38111-126">呼叫可以起始從 unmanaged 程式碼，而不需要的巢狀結構。</span><span class="sxs-lookup"><span data-stu-id="38111-126">Calls can originate from unmanaged code without being nested.</span></span> <span data-ttu-id="38111-127">在此情況下，沒有以呼叫[EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)， [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)，或`ReverseLeaveRuntime`，和呼叫數目`ReverseEnterRuntime`不等於的呼叫次數`ReverseLeaveRuntime`。</span><span class="sxs-lookup"><span data-stu-id="38111-127">In this case, there is no call to [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), or `ReverseLeaveRuntime`, and the number of calls to `ReverseEnterRuntime` does not equal the number of calls to `ReverseLeaveRuntime`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38111-128">需求</span><span class="sxs-lookup"><span data-stu-id="38111-128">Requirements</span></span>  
 <span data-ttu-id="38111-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="38111-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38111-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="38111-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="38111-131">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="38111-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="38111-132">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38111-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38111-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38111-133">See also</span></span>

- [<span data-ttu-id="38111-134">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="38111-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="38111-135">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="38111-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="38111-136">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="38111-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="38111-137">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="38111-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
