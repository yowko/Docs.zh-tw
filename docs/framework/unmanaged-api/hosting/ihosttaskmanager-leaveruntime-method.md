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
ms.openlocfilehash: 2939f13933c4681e7e2220e5290e019e10c2844e
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841915"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a><span data-ttu-id="a3195-102">IHostTaskManager::LeaveRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="a3195-102">IHostTaskManager::LeaveRuntime Method</span></span>
<span data-ttu-id="a3195-103">通知主機目前正在執行的工作即將離開 common language runtime （CLR），並輸入非受控碼。</span><span class="sxs-lookup"><span data-stu-id="a3195-103">Notifies the host that the currently executing task is about to leave the common language runtime (CLR) and enter unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a3195-104">對[IHostTaskManager：： EnterRuntime](ihosttaskmanager-enterruntime-method.md)的對應呼叫，會通知主機目前正在執行的工作是重新進入 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="a3195-104">A corresponding call to [IHostTaskManager::EnterRuntime](ihosttaskmanager-enterruntime-method.md) notifies the host that the currently executing task is reentering managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3195-105">語法</span><span class="sxs-lookup"><span data-stu-id="a3195-105">Syntax</span></span>  
  
```cpp  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3195-106">參數</span><span class="sxs-lookup"><span data-stu-id="a3195-106">Parameters</span></span>  
 `target`  
 <span data-ttu-id="a3195-107">在要呼叫之非受控函式的對應可攜式可執行檔內的位址。</span><span class="sxs-lookup"><span data-stu-id="a3195-107">[in] The address within the mapped portable executable file of the unmanaged function to be called.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a3195-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="a3195-108">Return Value</span></span>  
  
|<span data-ttu-id="a3195-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a3195-109">HRESULT</span></span>|<span data-ttu-id="a3195-110">描述</span><span class="sxs-lookup"><span data-stu-id="a3195-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a3195-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a3195-111">S_OK</span></span>|<span data-ttu-id="a3195-112">`LeaveRuntime`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="a3195-112">`LeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="a3195-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a3195-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a3195-114">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="a3195-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a3195-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a3195-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a3195-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="a3195-116">The call timed out.</span></span>|  
|<span data-ttu-id="a3195-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a3195-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a3195-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="a3195-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a3195-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a3195-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a3195-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="a3195-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a3195-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a3195-121">E_FAIL</span></span>|<span data-ttu-id="a3195-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="a3195-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a3195-123">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="a3195-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a3195-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a3195-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a3195-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="a3195-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="a3195-126">沒有足夠的記憶體可用來完成要求的配置。</span><span class="sxs-lookup"><span data-stu-id="a3195-126">Not enough memory is available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3195-127">備註</span><span class="sxs-lookup"><span data-stu-id="a3195-127">Remarks</span></span>  
 <span data-ttu-id="a3195-128">不受管理程式碼的呼叫序列可以進行嵌套。</span><span class="sxs-lookup"><span data-stu-id="a3195-128">Call sequences to and from unmanaged code can be nested.</span></span> <span data-ttu-id="a3195-129">例如，下列清單描述一種假設的情況，其中的呼叫順序為 `LeaveRuntime` [IHostTaskManager：： ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)， [IHostTaskManager：： ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md)，並 `IHostTaskManager::EnterRuntime` 允許主機識別嵌套層。</span><span class="sxs-lookup"><span data-stu-id="a3195-129">For example, the list below describes a hypothetical situation in which the sequence of calls to `LeaveRuntime`, [IHostTaskManager::ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager::ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md), and `IHostTaskManager::EnterRuntime` allows the host to identify the nested layers.</span></span>  
  
|<span data-ttu-id="a3195-130">動作</span><span class="sxs-lookup"><span data-stu-id="a3195-130">Action</span></span>|<span data-ttu-id="a3195-131">對應的方法呼叫</span><span class="sxs-lookup"><span data-stu-id="a3195-131">Corresponding Method Call</span></span>|  
|------------|-------------------------------|  
|<span data-ttu-id="a3195-132">Managed Visual Basic 可執行檔會使用平台叫用，呼叫以 C 撰寫的非受控函式。</span><span class="sxs-lookup"><span data-stu-id="a3195-132">A managed Visual Basic executable calls an unmanaged function written in C by using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="a3195-133">非受控 C 函式會呼叫以 c # 撰寫的 managed DLL 中的方法。</span><span class="sxs-lookup"><span data-stu-id="a3195-133">The unmanaged C function calls a method in a managed DLL written in C#.</span></span>|`IHostTaskManager::ReverseEnterRuntime`|  
|<span data-ttu-id="a3195-134">Managed c # 函數會呼叫以 C 撰寫的另一個非受控函式，也會使用平台叫用。</span><span class="sxs-lookup"><span data-stu-id="a3195-134">The managed C# function calls another unmanaged function written in C, also using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="a3195-135">第二個非受控函式會將執行傳回 c # 函數。</span><span class="sxs-lookup"><span data-stu-id="a3195-135">The second unmanaged function returns execution to the C# function.</span></span>|`IHostTaskManager::EnterRuntime`|  
|<span data-ttu-id="a3195-136">C # 函式會將執行傳回給第一個非受控函式。</span><span class="sxs-lookup"><span data-stu-id="a3195-136">The C# function returns execution to the first unmanaged function.</span></span>|`IHostTaskManager::ReverseLeaveRuntime`|  
|<span data-ttu-id="a3195-137">第一個非受控函式會將執行傳回給 Visual Basic 程式。</span><span class="sxs-lookup"><span data-stu-id="a3195-137">The first unmanaged function returns execution to the Visual Basic program.</span></span>|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a><span data-ttu-id="a3195-138">規格需求</span><span class="sxs-lookup"><span data-stu-id="a3195-138">Requirements</span></span>  
 <span data-ttu-id="a3195-139">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a3195-139">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3195-140">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="a3195-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a3195-141">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a3195-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a3195-142">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3195-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3195-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3195-143">See also</span></span>

- [<span data-ttu-id="a3195-144">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="a3195-144">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="a3195-145">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="a3195-145">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="a3195-146">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="a3195-146">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="a3195-147">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="a3195-147">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
