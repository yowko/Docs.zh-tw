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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a01779e6203ddfea32e72838b7e02996fd868c2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749608"
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="92584-102">IHostTaskManager::EnterRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="92584-102">IHostTaskManager::EnterRuntime Method</span></span>
<span data-ttu-id="92584-103">主應用程式的呼叫未受管理的方法，例如平台叫用方法，是執行將控制權傳回給 common language runtime (CLR)。</span><span class="sxs-lookup"><span data-stu-id="92584-103">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92584-104">語法</span><span class="sxs-lookup"><span data-stu-id="92584-104">Syntax</span></span>  
  
```cpp  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="92584-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="92584-105">Return Value</span></span>  
  
|<span data-ttu-id="92584-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="92584-106">HRESULT</span></span>|<span data-ttu-id="92584-107">說明</span><span class="sxs-lookup"><span data-stu-id="92584-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="92584-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="92584-108">S_OK</span></span>|<span data-ttu-id="92584-109">`EnterRuntime` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="92584-109">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="92584-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="92584-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="92584-111">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="92584-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="92584-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="92584-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="92584-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="92584-113">The call timed out.</span></span>|  
|<span data-ttu-id="92584-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="92584-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="92584-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="92584-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="92584-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="92584-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="92584-117">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="92584-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="92584-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="92584-118">E_FAIL</span></span>|<span data-ttu-id="92584-119">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="92584-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="92584-120">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="92584-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="92584-121">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="92584-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="92584-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="92584-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="92584-123">記憶體不足，無法完成要求的配置。</span><span class="sxs-lookup"><span data-stu-id="92584-123">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92584-124">備註</span><span class="sxs-lookup"><span data-stu-id="92584-124">Remarks</span></span>  
 <span data-ttu-id="92584-125">`EnterRuntime` 呼叫以通知主應用程式的 unmanaged 函式，為其先前呼叫[LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)方法進行、 已完成執行，並會將執行控制權傳回給執行階段。</span><span class="sxs-lookup"><span data-stu-id="92584-125">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="92584-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)呼叫以通知主應用程式的 unmanaged 函式，為其先前呼叫`LeaveRuntime`進行，將 managed 程式碼呼叫。</span><span class="sxs-lookup"><span data-stu-id="92584-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92584-127">需求</span><span class="sxs-lookup"><span data-stu-id="92584-127">Requirements</span></span>  
 <span data-ttu-id="92584-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="92584-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92584-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="92584-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="92584-130">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="92584-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92584-131">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92584-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92584-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92584-132">See also</span></span>

- [<span data-ttu-id="92584-133">進階 COM 互通性</span><span class="sxs-lookup"><span data-stu-id="92584-133">Advanced COM Interoperability</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx)
- [<span data-ttu-id="92584-134">如何：使用 PInvoke 從受控程式碼呼叫原生 DLL</span><span class="sxs-lookup"><span data-stu-id="92584-134">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)
- [<span data-ttu-id="92584-135">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="92584-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="92584-136">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="92584-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="92584-137">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="92584-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="92584-138">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="92584-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="92584-139">LeaveRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="92584-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
