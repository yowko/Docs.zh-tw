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
ms.openlocfilehash: 8625f893c30700a47cc2db7b960715f748ccb299
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "44038719"
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="97319-102">IHostTaskManager::EnterRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="97319-102">IHostTaskManager::EnterRuntime Method</span></span>
<span data-ttu-id="97319-103">主應用程式的呼叫未受管理的方法，例如平台叫用方法，是執行將控制權傳回給 common language runtime (CLR)。</span><span class="sxs-lookup"><span data-stu-id="97319-103">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97319-104">語法</span><span class="sxs-lookup"><span data-stu-id="97319-104">Syntax</span></span>  
  
```  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="97319-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="97319-105">Return Value</span></span>  
  
|<span data-ttu-id="97319-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="97319-106">HRESULT</span></span>|<span data-ttu-id="97319-107">描述</span><span class="sxs-lookup"><span data-stu-id="97319-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="97319-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="97319-108">S_OK</span></span>|<span data-ttu-id="97319-109">`EnterRuntime` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="97319-109">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="97319-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="97319-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="97319-111">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="97319-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="97319-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="97319-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="97319-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="97319-113">The call timed out.</span></span>|  
|<span data-ttu-id="97319-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="97319-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="97319-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="97319-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="97319-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="97319-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="97319-117">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="97319-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="97319-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="97319-118">E_FAIL</span></span>|<span data-ttu-id="97319-119">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="97319-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="97319-120">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="97319-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="97319-121">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="97319-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="97319-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="97319-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="97319-123">記憶體不足，無法完成要求的配置。</span><span class="sxs-lookup"><span data-stu-id="97319-123">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97319-124">備註</span><span class="sxs-lookup"><span data-stu-id="97319-124">Remarks</span></span>  
 <span data-ttu-id="97319-125">`EnterRuntime` 呼叫以通知主應用程式的 unmanaged 函式，為其先前呼叫[LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)方法進行、 已完成執行，並會將執行控制權傳回給執行階段。</span><span class="sxs-lookup"><span data-stu-id="97319-125">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="97319-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)呼叫以通知主應用程式的 unmanaged 函式，為其先前呼叫`LeaveRuntime`進行，將 managed 程式碼呼叫。</span><span class="sxs-lookup"><span data-stu-id="97319-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97319-127">需求</span><span class="sxs-lookup"><span data-stu-id="97319-127">Requirements</span></span>  
 <span data-ttu-id="97319-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="97319-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97319-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="97319-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="97319-130">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="97319-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="97319-131">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97319-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97319-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97319-132">See Also</span></span>  
 [<span data-ttu-id="97319-133">進階 COM 互通性</span><span class="sxs-lookup"><span data-stu-id="97319-133">Advanced COM Interoperability</span></span>](https://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [<span data-ttu-id="97319-134">如何：使用 PInvoke 從 Managed 程式碼呼叫原生 DLL</span><span class="sxs-lookup"><span data-stu-id="97319-134">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)  
 [<span data-ttu-id="97319-135">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="97319-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="97319-136">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="97319-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="97319-137">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="97319-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="97319-138">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="97319-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="97319-139">LeaveRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="97319-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
