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
ms.openlocfilehash: 8ac1c18d094deca50d461ef9ff0933a4f87176e0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132998"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a><span data-ttu-id="e96ff-102">IHostTaskManager::LeaveRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="e96ff-102">IHostTaskManager::LeaveRuntime Method</span></span>
<span data-ttu-id="e96ff-103">通知主機目前正在執行的工作即將離開 common language runtime （CLR），並輸入非受控碼。</span><span class="sxs-lookup"><span data-stu-id="e96ff-103">Notifies the host that the currently executing task is about to leave the common language runtime (CLR) and enter unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e96ff-104">對[IHostTaskManager：： EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)的對應呼叫，會通知主機目前正在執行的工作是重新進入 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="e96ff-104">A corresponding call to [IHostTaskManager::EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) notifies the host that the currently executing task is reentering managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e96ff-105">語法</span><span class="sxs-lookup"><span data-stu-id="e96ff-105">Syntax</span></span>  
  
```cpp  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e96ff-106">參數</span><span class="sxs-lookup"><span data-stu-id="e96ff-106">Parameters</span></span>  
 `target`  
 <span data-ttu-id="e96ff-107">在要呼叫之非受控函式的對應可攜式可執行檔內的位址。</span><span class="sxs-lookup"><span data-stu-id="e96ff-107">[in] The address within the mapped portable executable file of the unmanaged function to be called.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e96ff-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="e96ff-108">Return Value</span></span>  
  
|<span data-ttu-id="e96ff-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e96ff-109">HRESULT</span></span>|<span data-ttu-id="e96ff-110">描述</span><span class="sxs-lookup"><span data-stu-id="e96ff-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e96ff-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e96ff-111">S_OK</span></span>|<span data-ttu-id="e96ff-112">已成功傳回 `LeaveRuntime`。</span><span class="sxs-lookup"><span data-stu-id="e96ff-112">`LeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="e96ff-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e96ff-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e96ff-114">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="e96ff-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e96ff-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e96ff-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e96ff-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="e96ff-116">The call timed out.</span></span>|  
|<span data-ttu-id="e96ff-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e96ff-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e96ff-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="e96ff-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e96ff-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e96ff-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e96ff-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="e96ff-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e96ff-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e96ff-121">E_FAIL</span></span>|<span data-ttu-id="e96ff-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="e96ff-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e96ff-123">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="e96ff-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e96ff-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="e96ff-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e96ff-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="e96ff-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="e96ff-126">沒有足夠的記憶體可用來完成要求的配置。</span><span class="sxs-lookup"><span data-stu-id="e96ff-126">Not enough memory is available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e96ff-127">備註</span><span class="sxs-lookup"><span data-stu-id="e96ff-127">Remarks</span></span>  
 <span data-ttu-id="e96ff-128">不受管理程式碼的呼叫序列可以進行嵌套。</span><span class="sxs-lookup"><span data-stu-id="e96ff-128">Call sequences to and from unmanaged code can be nested.</span></span> <span data-ttu-id="e96ff-129">例如，下列清單描述的是一種假設的情況，其中 `LeaveRuntime`、 [IHostTaskManager：： ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)、 [IHostTaskManager：： ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)和 `IHostTaskManager::EnterRuntime` 的呼叫順序，讓主機能夠識別嵌套層。</span><span class="sxs-lookup"><span data-stu-id="e96ff-129">For example, the list below describes a hypothetical situation in which the sequence of calls to `LeaveRuntime`, [IHostTaskManager::ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager::ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), and `IHostTaskManager::EnterRuntime` allows the host to identify the nested layers.</span></span>  
  
|<span data-ttu-id="e96ff-130">動作</span><span class="sxs-lookup"><span data-stu-id="e96ff-130">Action</span></span>|<span data-ttu-id="e96ff-131">對應的方法呼叫</span><span class="sxs-lookup"><span data-stu-id="e96ff-131">Corresponding Method Call</span></span>|  
|------------|-------------------------------|  
|<span data-ttu-id="e96ff-132">Managed Visual Basic 可執行檔會使用平台叫用，呼叫以 C 撰寫的非受控函式。</span><span class="sxs-lookup"><span data-stu-id="e96ff-132">A managed Visual Basic executable calls an unmanaged function written in C by using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="e96ff-133">非受控 C 函式會在以C#撰寫的 managed DLL 中呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="e96ff-133">The unmanaged C function calls a method in a managed DLL written in C#.</span></span>|`IHostTaskManager::ReverseEnterRuntime`|  
|<span data-ttu-id="e96ff-134">Managed C#函式會呼叫以 C 撰寫的另一個非受控函式，也會使用平台叫用。</span><span class="sxs-lookup"><span data-stu-id="e96ff-134">The managed C# function calls another unmanaged function written in C, also using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="e96ff-135">第二個非受控函式會C#將執行傳回函式。</span><span class="sxs-lookup"><span data-stu-id="e96ff-135">The second unmanaged function returns execution to the C# function.</span></span>|`IHostTaskManager::EnterRuntime`|  
|<span data-ttu-id="e96ff-136">C#函式會將執行傳回第一個非受控函式。</span><span class="sxs-lookup"><span data-stu-id="e96ff-136">The C# function returns execution to the first unmanaged function.</span></span>|`IHostTaskManager::ReverseLeaveRuntime`|  
|<span data-ttu-id="e96ff-137">第一個非受控函式會將執行傳回給 Visual Basic 程式。</span><span class="sxs-lookup"><span data-stu-id="e96ff-137">The first unmanaged function returns execution to the Visual Basic program.</span></span>|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a><span data-ttu-id="e96ff-138">需求</span><span class="sxs-lookup"><span data-stu-id="e96ff-138">Requirements</span></span>  
 <span data-ttu-id="e96ff-139">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e96ff-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e96ff-140">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="e96ff-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e96ff-141">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e96ff-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e96ff-142">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e96ff-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e96ff-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="e96ff-143">See also</span></span>

- [<span data-ttu-id="e96ff-144">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="e96ff-144">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="e96ff-145">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="e96ff-145">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="e96ff-146">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="e96ff-146">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="e96ff-147">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="e96ff-147">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
