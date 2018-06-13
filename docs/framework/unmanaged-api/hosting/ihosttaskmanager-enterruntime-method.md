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
ms.openlocfilehash: a47f51ba32a9dfc16300a8de7c2d4b380a8ba988
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445091"
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="a0fd7-102">IHostTaskManager::EnterRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="a0fd7-102">IHostTaskManager::EnterRuntime Method</span></span>
<span data-ttu-id="a0fd7-103">通知主機的呼叫未受管理的方法，例如平台叫用方法時，會執行將控制權傳回給 common language runtime (CLR)。</span><span class="sxs-lookup"><span data-stu-id="a0fd7-103">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0fd7-104">語法</span><span class="sxs-lookup"><span data-stu-id="a0fd7-104">Syntax</span></span>  
  
```  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a0fd7-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="a0fd7-105">Return Value</span></span>  
  
|<span data-ttu-id="a0fd7-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a0fd7-106">HRESULT</span></span>|<span data-ttu-id="a0fd7-107">描述</span><span class="sxs-lookup"><span data-stu-id="a0fd7-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a0fd7-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="a0fd7-108">S_OK</span></span>|<span data-ttu-id="a0fd7-109">`EnterRuntime` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="a0fd7-109">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="a0fd7-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a0fd7-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a0fd7-111">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="a0fd7-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a0fd7-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a0fd7-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a0fd7-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="a0fd7-113">The call timed out.</span></span>|  
|<span data-ttu-id="a0fd7-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a0fd7-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a0fd7-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="a0fd7-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a0fd7-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a0fd7-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a0fd7-117">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="a0fd7-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a0fd7-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a0fd7-118">E_FAIL</span></span>|<span data-ttu-id="a0fd7-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="a0fd7-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a0fd7-120">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="a0fd7-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a0fd7-121">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a0fd7-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a0fd7-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="a0fd7-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="a0fd7-123">記憶體不足，無法完成要求的配置。</span><span class="sxs-lookup"><span data-stu-id="a0fd7-123">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0fd7-124">備註</span><span class="sxs-lookup"><span data-stu-id="a0fd7-124">Remarks</span></span>  
 <span data-ttu-id="a0fd7-125">`EnterRuntime` 呼叫以通知主機的 unmanaged 函式，其之前呼叫[LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)方法進行、 已完成執行，並會將執行控制權傳回給執行階段。</span><span class="sxs-lookup"><span data-stu-id="a0fd7-125">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0fd7-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)呼叫以通知主機的 unmanaged 函式，其之前呼叫`LeaveRuntime`提出、 正在進行的呼叫至 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="a0fd7-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0fd7-127">需求</span><span class="sxs-lookup"><span data-stu-id="a0fd7-127">Requirements</span></span>  
 <span data-ttu-id="a0fd7-128">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a0fd7-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0fd7-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a0fd7-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a0fd7-130">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a0fd7-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a0fd7-131">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0fd7-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0fd7-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0fd7-132">See Also</span></span>  
 [<span data-ttu-id="a0fd7-133">進階 COM 互通性</span><span class="sxs-lookup"><span data-stu-id="a0fd7-133">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [<span data-ttu-id="a0fd7-134">如何：使用 PInvoke 從 Managed 程式碼呼叫原生 DLL</span><span class="sxs-lookup"><span data-stu-id="a0fd7-134">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)  
 [<span data-ttu-id="a0fd7-135">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="a0fd7-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="a0fd7-136">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="a0fd7-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="a0fd7-137">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="a0fd7-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="a0fd7-138">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="a0fd7-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="a0fd7-139">LeaveRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="a0fd7-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
