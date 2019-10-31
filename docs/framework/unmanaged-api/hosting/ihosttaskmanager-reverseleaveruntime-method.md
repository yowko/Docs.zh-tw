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
ms.openlocfilehash: 362239c584f469c9bd88f9f937bb3cdae7235429
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132960"
---
# <a name="ihosttaskmanagerreverseleaveruntime-method"></a><span data-ttu-id="46d99-102">IHostTaskManager::ReverseLeaveRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="46d99-102">IHostTaskManager::ReverseLeaveRuntime Method</span></span>
<span data-ttu-id="46d99-103">通知主控制項離開 common language runtime （CLR），並輸入從 managed 程式碼呼叫的非受控函式。</span><span class="sxs-lookup"><span data-stu-id="46d99-103">Notifies the host that control is leaving the common language runtime (CLR) and entering an unmanaged function that was, in turn, called from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46d99-104">語法</span><span class="sxs-lookup"><span data-stu-id="46d99-104">Syntax</span></span>  
  
```cpp  
HRESULT ReverseLeaveRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="46d99-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="46d99-105">Return Value</span></span>  
  
|<span data-ttu-id="46d99-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="46d99-106">HRESULT</span></span>|<span data-ttu-id="46d99-107">描述</span><span class="sxs-lookup"><span data-stu-id="46d99-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="46d99-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="46d99-108">S_OK</span></span>|<span data-ttu-id="46d99-109">已成功傳回 `ReverseLeaveRuntime`。</span><span class="sxs-lookup"><span data-stu-id="46d99-109">`ReverseLeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="46d99-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="46d99-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="46d99-111">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="46d99-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="46d99-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="46d99-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="46d99-113">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="46d99-113">The call timed out.</span></span>|  
|<span data-ttu-id="46d99-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="46d99-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="46d99-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="46d99-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="46d99-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="46d99-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="46d99-117">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="46d99-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="46d99-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="46d99-118">E_FAIL</span></span>|<span data-ttu-id="46d99-119">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="46d99-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="46d99-120">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="46d99-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="46d99-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="46d99-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="46d99-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="46d99-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="46d99-123">沒有足夠的記憶體可用來完成要求的資源配置。</span><span class="sxs-lookup"><span data-stu-id="46d99-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46d99-124">備註</span><span class="sxs-lookup"><span data-stu-id="46d99-124">Remarks</span></span>  
 <span data-ttu-id="46d99-125">CLR 會呼叫 `ReverseLeaveRuntime`，以通知主機目前正在執行的工作正在將控制權傳回給不受管理的函式，而該函式又會透過平台叫用從 managed 程式碼呼叫。</span><span class="sxs-lookup"><span data-stu-id="46d99-125">The CLR calls `ReverseLeaveRuntime` to inform the host that the currently executing task is returning control to an unmanaged function that was, in turn, called from managed code through platform invoke.</span></span> <span data-ttu-id="46d99-126">`ReverseLeaveRuntime` 的每個呼叫都會符合對應的[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)呼叫。</span><span class="sxs-lookup"><span data-stu-id="46d99-126">Each call to `ReverseLeaveRuntime` matches a corresponding call to [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46d99-127">需求</span><span class="sxs-lookup"><span data-stu-id="46d99-127">Requirements</span></span>  
 <span data-ttu-id="46d99-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="46d99-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46d99-129">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="46d99-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="46d99-130">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="46d99-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="46d99-131">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46d99-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46d99-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="46d99-132">See also</span></span>

- [<span data-ttu-id="46d99-133">CallNeedsHostHook 方法</span><span class="sxs-lookup"><span data-stu-id="46d99-133">CallNeedsHostHook Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)
- [<span data-ttu-id="46d99-134">EnterRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="46d99-134">EnterRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)
- [<span data-ttu-id="46d99-135">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="46d99-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="46d99-136">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="46d99-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="46d99-137">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="46d99-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="46d99-138">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="46d99-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="46d99-139">LeaveRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="46d99-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
- <span data-ttu-id="46d99-140">[詳述平台叫用](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="46d99-140">[A Closer Look at Platform Invoke](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span></span>
