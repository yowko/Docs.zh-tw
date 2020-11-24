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
ms.openlocfilehash: 855f8a5d3582bbad59301a344d8a51198c40a051
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673042"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a><span data-ttu-id="45198-102">IHostTaskManager::LeaveRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="45198-102">IHostTaskManager::LeaveRuntime Method</span></span>

<span data-ttu-id="45198-103">通知主機目前正在執行的工作即將將 common language runtime (CLR) ，然後輸入非受控碼。</span><span class="sxs-lookup"><span data-stu-id="45198-103">Notifies the host that the currently executing task is about to leave the common language runtime (CLR) and enter unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="45198-104">對應的 [IHostTaskManager：： EnterRuntime](ihosttaskmanager-enterruntime-method.md) 呼叫會通知主機目前正在執行的工作正在重新進入 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="45198-104">A corresponding call to [IHostTaskManager::EnterRuntime](ihosttaskmanager-enterruntime-method.md) notifies the host that the currently executing task is reentering managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45198-105">語法</span><span class="sxs-lookup"><span data-stu-id="45198-105">Syntax</span></span>  
  
```cpp  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45198-106">參數</span><span class="sxs-lookup"><span data-stu-id="45198-106">Parameters</span></span>  

 `target`  
 <span data-ttu-id="45198-107">在要呼叫之非受控函式的對應可攜式可執行檔中的位址。</span><span class="sxs-lookup"><span data-stu-id="45198-107">[in] The address within the mapped portable executable file of the unmanaged function to be called.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45198-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="45198-108">Return Value</span></span>  
  
|<span data-ttu-id="45198-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="45198-109">HRESULT</span></span>|<span data-ttu-id="45198-110">描述</span><span class="sxs-lookup"><span data-stu-id="45198-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="45198-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="45198-111">S_OK</span></span>|<span data-ttu-id="45198-112">`LeaveRuntime` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="45198-112">`LeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="45198-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="45198-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="45198-114">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="45198-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="45198-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="45198-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="45198-116">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="45198-116">The call timed out.</span></span>|  
|<span data-ttu-id="45198-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="45198-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="45198-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="45198-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="45198-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="45198-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="45198-120">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="45198-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="45198-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="45198-121">E_FAIL</span></span>|<span data-ttu-id="45198-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="45198-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="45198-123">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="45198-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="45198-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="45198-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="45198-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="45198-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="45198-126">沒有足夠的記憶體可完成要求的配置。</span><span class="sxs-lookup"><span data-stu-id="45198-126">Not enough memory is available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45198-127">備註</span><span class="sxs-lookup"><span data-stu-id="45198-127">Remarks</span></span>  

 <span data-ttu-id="45198-128">不受管理程式碼的呼叫序列可以進行嵌套。</span><span class="sxs-lookup"><span data-stu-id="45198-128">Call sequences to and from unmanaged code can be nested.</span></span> <span data-ttu-id="45198-129">例如，下列清單描述的是對 `LeaveRuntime` 、 [IHostTaskManager：： ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md)、 [IHostTaskManager：： ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md)的呼叫順序，以及 `IHostTaskManager::EnterRuntime` 允許主機識別嵌套層的假設狀況。</span><span class="sxs-lookup"><span data-stu-id="45198-129">For example, the list below describes a hypothetical situation in which the sequence of calls to `LeaveRuntime`, [IHostTaskManager::ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager::ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md), and `IHostTaskManager::EnterRuntime` allows the host to identify the nested layers.</span></span>  
  
|<span data-ttu-id="45198-130">動作</span><span class="sxs-lookup"><span data-stu-id="45198-130">Action</span></span>|<span data-ttu-id="45198-131">對應的方法呼叫</span><span class="sxs-lookup"><span data-stu-id="45198-131">Corresponding Method Call</span></span>|  
|------------|-------------------------------|  
|<span data-ttu-id="45198-132">Managed Visual Basic 可執行檔會使用平台叫用呼叫以 C 撰寫的非受控函式。</span><span class="sxs-lookup"><span data-stu-id="45198-132">A managed Visual Basic executable calls an unmanaged function written in C by using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="45198-133">非受控 C 函式會在以 c # 撰寫的 managed DLL 中呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="45198-133">The unmanaged C function calls a method in a managed DLL written in C#.</span></span>|`IHostTaskManager::ReverseEnterRuntime`|  
|<span data-ttu-id="45198-134">Managed c # 函式會呼叫另一個以 C 撰寫的非受控函式，也會使用平台叫用。</span><span class="sxs-lookup"><span data-stu-id="45198-134">The managed C# function calls another unmanaged function written in C, also using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="45198-135">第二個非受控函式會將執行傳回給 c # 函式。</span><span class="sxs-lookup"><span data-stu-id="45198-135">The second unmanaged function returns execution to the C# function.</span></span>|`IHostTaskManager::EnterRuntime`|  
|<span data-ttu-id="45198-136">C # 函式會將執行傳回至第一個非受控函數。</span><span class="sxs-lookup"><span data-stu-id="45198-136">The C# function returns execution to the first unmanaged function.</span></span>|`IHostTaskManager::ReverseLeaveRuntime`|  
|<span data-ttu-id="45198-137">第一個非受控函式會將執行傳回給 Visual Basic 程式。</span><span class="sxs-lookup"><span data-stu-id="45198-137">The first unmanaged function returns execution to the Visual Basic program.</span></span>|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a><span data-ttu-id="45198-138">需求</span><span class="sxs-lookup"><span data-stu-id="45198-138">Requirements</span></span>  

 <span data-ttu-id="45198-139">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="45198-139">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45198-140">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="45198-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="45198-141">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="45198-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="45198-142">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45198-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45198-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45198-143">See also</span></span>

- [<span data-ttu-id="45198-144">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="45198-144">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="45198-145">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="45198-145">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="45198-146">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="45198-146">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="45198-147">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="45198-147">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
