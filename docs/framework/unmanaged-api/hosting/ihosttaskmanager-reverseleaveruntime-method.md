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
ms.openlocfilehash: 8e0981415c03120cc30e6349daced51e79216938
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95669961"
---
# <a name="ihosttaskmanagerreverseleaveruntime-method"></a><span data-ttu-id="9b0e3-102">IHostTaskManager::ReverseLeaveRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="9b0e3-102">IHostTaskManager::ReverseLeaveRuntime Method</span></span>

<span data-ttu-id="9b0e3-103">通知主機，該控制項會將 common language runtime 保留 (CLR) ，然後輸入從 managed 程式碼呼叫的非受控函式。</span><span class="sxs-lookup"><span data-stu-id="9b0e3-103">Notifies the host that control is leaving the common language runtime (CLR) and entering an unmanaged function that was, in turn, called from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b0e3-104">語法</span><span class="sxs-lookup"><span data-stu-id="9b0e3-104">Syntax</span></span>  
  
```cpp  
HRESULT ReverseLeaveRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9b0e3-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="9b0e3-105">Return Value</span></span>  
  
|<span data-ttu-id="9b0e3-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9b0e3-106">HRESULT</span></span>|<span data-ttu-id="9b0e3-107">描述</span><span class="sxs-lookup"><span data-stu-id="9b0e3-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9b0e3-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="9b0e3-108">S_OK</span></span>|<span data-ttu-id="9b0e3-109">`ReverseLeaveRuntime` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="9b0e3-109">`ReverseLeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="9b0e3-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9b0e3-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9b0e3-111">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="9b0e3-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9b0e3-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9b0e3-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9b0e3-113">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="9b0e3-113">The call timed out.</span></span>|  
|<span data-ttu-id="9b0e3-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9b0e3-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9b0e3-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="9b0e3-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9b0e3-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9b0e3-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9b0e3-117">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="9b0e3-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9b0e3-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9b0e3-118">E_FAIL</span></span>|<span data-ttu-id="9b0e3-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="9b0e3-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9b0e3-120">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="9b0e3-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9b0e3-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="9b0e3-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9b0e3-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="9b0e3-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="9b0e3-123">沒有足夠的記憶體可完成要求的資源配置。</span><span class="sxs-lookup"><span data-stu-id="9b0e3-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b0e3-124">備註</span><span class="sxs-lookup"><span data-stu-id="9b0e3-124">Remarks</span></span>  

 <span data-ttu-id="9b0e3-125">CLR 會呼叫， `ReverseLeaveRuntime` 以通知主機目前正在執行的工作正在將控制權傳回給非受控函式，而該函式則是透過平台叫用從 managed 程式碼呼叫。</span><span class="sxs-lookup"><span data-stu-id="9b0e3-125">The CLR calls `ReverseLeaveRuntime` to inform the host that the currently executing task is returning control to an unmanaged function that was, in turn, called from managed code through platform invoke.</span></span> <span data-ttu-id="9b0e3-126">每次呼叫都 `ReverseLeaveRuntime` 符合對應的 [ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md)呼叫。</span><span class="sxs-lookup"><span data-stu-id="9b0e3-126">Each call to `ReverseLeaveRuntime` matches a corresponding call to [ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b0e3-127">需求</span><span class="sxs-lookup"><span data-stu-id="9b0e3-127">Requirements</span></span>  

 <span data-ttu-id="9b0e3-128">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9b0e3-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b0e3-129">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9b0e3-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9b0e3-130">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="9b0e3-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9b0e3-131">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b0e3-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b0e3-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b0e3-132">See also</span></span>

- [<span data-ttu-id="9b0e3-133">CallNeedsHostHook 方法</span><span class="sxs-lookup"><span data-stu-id="9b0e3-133">CallNeedsHostHook Method</span></span>](ihosttaskmanager-callneedshosthook-method.md)
- [<span data-ttu-id="9b0e3-134">EnterRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="9b0e3-134">EnterRuntime Method</span></span>](ihosttaskmanager-enterruntime-method.md)
- [<span data-ttu-id="9b0e3-135">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="9b0e3-135">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="9b0e3-136">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="9b0e3-136">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="9b0e3-137">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="9b0e3-137">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="9b0e3-138">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="9b0e3-138">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="9b0e3-139">LeaveRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="9b0e3-139">LeaveRuntime Method</span></span>](ihosttaskmanager-leaveruntime-method.md)
- <span data-ttu-id="9b0e3-140">[進一步了解平台叫用](/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9b0e3-140">[A Closer Look at Platform Invoke](/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span></span>
