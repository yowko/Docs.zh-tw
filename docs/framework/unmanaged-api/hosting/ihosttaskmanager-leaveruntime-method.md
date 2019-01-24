---
title: IHostTaskManager::LeaveRuntime 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.LeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::LeaveRuntime
helpviewer_keywords:
- IHostTaskManager::LeaveRuntime method [.NET Framework hosting]
- LeaveRuntime method [.NET Framework hosting]
ms.assetid: 43689cc4-e48e-46e5-a22d-bafd768b8759
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e22ed258390f7adc9bbf8cd425afe208b2f9b12c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607039"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a><span data-ttu-id="6a2b9-102">IHostTaskManager::LeaveRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="6a2b9-102">IHostTaskManager::LeaveRuntime Method</span></span>
<span data-ttu-id="6a2b9-103">主應用程式目前正在執行的工作是要將 common language runtime (CLR) 並輸入 unmanaged 程式碼。</span><span class="sxs-lookup"><span data-stu-id="6a2b9-103">Notifies the host that the currently executing task is about to leave the common language runtime (CLR) and enter unmanaged code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6a2b9-104">對應呼叫[ihosttaskmanager:: Enterruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)主應用程式目前正在執行的工作重新進入 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="6a2b9-104">A corresponding call to [IHostTaskManager::EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) notifies the host that the currently executing task is reentering managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a2b9-105">語法</span><span class="sxs-lookup"><span data-stu-id="6a2b9-105">Syntax</span></span>  
  
```  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6a2b9-106">參數</span><span class="sxs-lookup"><span data-stu-id="6a2b9-106">Parameters</span></span>  
 `target`  
 <span data-ttu-id="6a2b9-107">[in]呼叫 unmanaged 函式對應可攜式執行檔內的位址。</span><span class="sxs-lookup"><span data-stu-id="6a2b9-107">[in] The address within the mapped portable executable file of the unmanaged function to be called.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a2b9-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="6a2b9-108">Return Value</span></span>  
  
|<span data-ttu-id="6a2b9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6a2b9-109">HRESULT</span></span>|<span data-ttu-id="6a2b9-110">描述</span><span class="sxs-lookup"><span data-stu-id="6a2b9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6a2b9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6a2b9-111">S_OK</span></span>|<span data-ttu-id="6a2b9-112">`LeaveRuntime` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="6a2b9-112">`LeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="6a2b9-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6a2b9-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6a2b9-114">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="6a2b9-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6a2b9-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6a2b9-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6a2b9-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="6a2b9-116">The call timed out.</span></span>|  
|<span data-ttu-id="6a2b9-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6a2b9-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6a2b9-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="6a2b9-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6a2b9-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6a2b9-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6a2b9-120">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="6a2b9-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6a2b9-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6a2b9-121">E_FAIL</span></span>|<span data-ttu-id="6a2b9-122">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="6a2b9-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6a2b9-123">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="6a2b9-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6a2b9-124">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="6a2b9-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6a2b9-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="6a2b9-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="6a2b9-126">沒有足夠的記憶體可完成要求的配置。</span><span class="sxs-lookup"><span data-stu-id="6a2b9-126">Not enough memory is available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a2b9-127">備註</span><span class="sxs-lookup"><span data-stu-id="6a2b9-127">Remarks</span></span>  
 <span data-ttu-id="6a2b9-128">與 unmanaged 程式碼的呼叫序列可以是巢狀。</span><span class="sxs-lookup"><span data-stu-id="6a2b9-128">Call sequences to and from unmanaged code can be nested.</span></span> <span data-ttu-id="6a2b9-129">例如，下列清單描述的假設性情況的呼叫順序`LeaveRuntime`， [ihosttaskmanager:: Reverseenterruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)， [ihosttaskmanager:: Reverseleaveruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)，和`IHostTaskManager::EnterRuntime`可讓主機識別巢狀層級。</span><span class="sxs-lookup"><span data-stu-id="6a2b9-129">For example, the list below describes a hypothetical situation in which the sequence of calls to `LeaveRuntime`, [IHostTaskManager::ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager::ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), and `IHostTaskManager::EnterRuntime` allows the host to identify the nested layers.</span></span>  
  
|<span data-ttu-id="6a2b9-130">動作</span><span class="sxs-lookup"><span data-stu-id="6a2b9-130">Action</span></span>|<span data-ttu-id="6a2b9-131">對應的方法呼叫</span><span class="sxs-lookup"><span data-stu-id="6a2b9-131">Corresponding Method Call</span></span>|  
|------------|-------------------------------|  
|<span data-ttu-id="6a2b9-132">受管理的 Visual Basic 可執行檔呼叫 unmanaged 函式以 C 撰寫使用平台叫用。</span><span class="sxs-lookup"><span data-stu-id="6a2b9-132">A managed Visual Basic executable calls an unmanaged function written in C by using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="6a2b9-133">Unmanaged 的 C 函式呼叫的方法中撰寫的 managed DLL C#。</span><span class="sxs-lookup"><span data-stu-id="6a2b9-133">The unmanaged C function calls a method in a managed DLL written in C#.</span></span>|`IHostTaskManager::ReverseEnterRuntime`|  
|<span data-ttu-id="6a2b9-134">ManagedC#函式會呼叫另一個以 C 撰寫的 unmanaged 函式，也使用平台叫用。</span><span class="sxs-lookup"><span data-stu-id="6a2b9-134">The managed C# function calls another unmanaged function written in C, also using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="6a2b9-135">第二個 unmanaged 函式會傳回執行C#函式。</span><span class="sxs-lookup"><span data-stu-id="6a2b9-135">The second unmanaged function returns execution to the C# function.</span></span>|`IHostTaskManager::EnterRuntime`|  
|<span data-ttu-id="6a2b9-136">C#函式會傳回第一個非受控函式執行。</span><span class="sxs-lookup"><span data-stu-id="6a2b9-136">The C# function returns execution to the first unmanaged function.</span></span>|`IHostTaskManager::ReverseLeaveRuntime`|  
|<span data-ttu-id="6a2b9-137">第一個非受控函式執行傳回 Visual Basic 程式。</span><span class="sxs-lookup"><span data-stu-id="6a2b9-137">The first unmanaged function returns execution to the Visual Basic program.</span></span>|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a><span data-ttu-id="6a2b9-138">需求</span><span class="sxs-lookup"><span data-stu-id="6a2b9-138">Requirements</span></span>  
 <span data-ttu-id="6a2b9-139">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6a2b9-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a2b9-140">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6a2b9-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6a2b9-141">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6a2b9-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6a2b9-142">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a2b9-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a2b9-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a2b9-143">See also</span></span>
- [<span data-ttu-id="6a2b9-144">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="6a2b9-144">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="6a2b9-145">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="6a2b9-145">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="6a2b9-146">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="6a2b9-146">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="6a2b9-147">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="6a2b9-147">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
