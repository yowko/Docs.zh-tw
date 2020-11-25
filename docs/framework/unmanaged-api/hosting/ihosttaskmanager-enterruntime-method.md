---
title: IHostTaskManager::EnterRuntime 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EnterRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EnterRuntime
helpviewer_keywords:
- IHostTaskManager::EnterRuntime method [.NET Framework hosting]
- EnterRuntime method [.NET Framework hosting]
ms.assetid: 1aa7a4b1-636a-4f5e-b834-b406d72f7120
topic_type:
- apiref
ms.openlocfilehash: 11515bbb5717222a0030c1953b4eab4eb1b83bb2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731640"
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="f604c-102">IHostTaskManager::EnterRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="f604c-102">IHostTaskManager::EnterRuntime Method</span></span>

<span data-ttu-id="f604c-103">通知主機未受管理方法的呼叫（例如平台叫用方法），會將執行控制權傳回給 common language runtime (CLR) 。</span><span class="sxs-lookup"><span data-stu-id="f604c-103">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f604c-104">語法</span><span class="sxs-lookup"><span data-stu-id="f604c-104">Syntax</span></span>  
  
```cpp  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f604c-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="f604c-105">Return Value</span></span>  
  
|<span data-ttu-id="f604c-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f604c-106">HRESULT</span></span>|<span data-ttu-id="f604c-107">描述</span><span class="sxs-lookup"><span data-stu-id="f604c-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f604c-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="f604c-108">S_OK</span></span>|<span data-ttu-id="f604c-109">`EnterRuntime` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="f604c-109">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="f604c-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f604c-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f604c-111">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="f604c-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f604c-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f604c-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f604c-113">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="f604c-113">The call timed out.</span></span>|  
|<span data-ttu-id="f604c-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f604c-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f604c-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="f604c-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f604c-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f604c-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f604c-117">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="f604c-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f604c-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f604c-118">E_FAIL</span></span>|<span data-ttu-id="f604c-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="f604c-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f604c-120">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="f604c-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f604c-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="f604c-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f604c-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="f604c-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="f604c-123">沒有足夠的記憶體可完成要求的配置。</span><span class="sxs-lookup"><span data-stu-id="f604c-123">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f604c-124">備註</span><span class="sxs-lookup"><span data-stu-id="f604c-124">Remarks</span></span>  

 <span data-ttu-id="f604c-125">`EnterRuntime` 會呼叫，以通知主機未受管理的函式，其中先前對 [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md) 方法的呼叫已完成執行，並將執行控制項傳回給執行時間。</span><span class="sxs-lookup"><span data-stu-id="f604c-125">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f604c-126">呼叫[ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md)時，會呼叫，以通知主機先前呼叫的非受控函式 `LeaveRuntime` 正在對 managed 程式碼進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="f604c-126">[ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f604c-127">需求</span><span class="sxs-lookup"><span data-stu-id="f604c-127">Requirements</span></span>  

 <span data-ttu-id="f604c-128">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f604c-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f604c-129">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f604c-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f604c-130">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="f604c-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f604c-131">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f604c-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f604c-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f604c-132">See also</span></span>

- <span data-ttu-id="f604c-133">[進階 COM 互通性](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f604c-133">[Advanced COM Interoperability](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>
- [<span data-ttu-id="f604c-134">如何：使用 PInvoke 從 Managed 程式碼呼叫原生 Dll</span><span class="sxs-lookup"><span data-stu-id="f604c-134">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)
- [<span data-ttu-id="f604c-135">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="f604c-135">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="f604c-136">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="f604c-136">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="f604c-137">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="f604c-137">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="f604c-138">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="f604c-138">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="f604c-139">LeaveRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="f604c-139">LeaveRuntime Method</span></span>](ihosttaskmanager-leaveruntime-method.md)
