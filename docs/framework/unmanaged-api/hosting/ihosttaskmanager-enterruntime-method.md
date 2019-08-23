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
ms.openlocfilehash: aa756c98dc082774f7a8a6e050209525420b359f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913719"
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="8a35c-102">IHostTaskManager::EnterRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="8a35c-102">IHostTaskManager::EnterRuntime Method</span></span>
<span data-ttu-id="8a35c-103">通知主機呼叫非受控方法 (例如平台叫用方法), 會將執行控制傳回給 common language runtime (CLR)。</span><span class="sxs-lookup"><span data-stu-id="8a35c-103">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a35c-104">語法</span><span class="sxs-lookup"><span data-stu-id="8a35c-104">Syntax</span></span>  
  
```cpp  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8a35c-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="8a35c-105">Return Value</span></span>  
  
|<span data-ttu-id="8a35c-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8a35c-106">HRESULT</span></span>|<span data-ttu-id="8a35c-107">說明</span><span class="sxs-lookup"><span data-stu-id="8a35c-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8a35c-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="8a35c-108">S_OK</span></span>|<span data-ttu-id="8a35c-109">`EnterRuntime`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="8a35c-109">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="8a35c-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8a35c-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8a35c-111">CLR 尚未載入進程中, 或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="8a35c-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8a35c-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8a35c-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8a35c-113">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="8a35c-113">The call timed out.</span></span>|  
|<span data-ttu-id="8a35c-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8a35c-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8a35c-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="8a35c-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8a35c-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8a35c-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8a35c-117">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="8a35c-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8a35c-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8a35c-118">E_FAIL</span></span>|<span data-ttu-id="8a35c-119">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="8a35c-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8a35c-120">當方法傳回 E_FAIL 時, CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="8a35c-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8a35c-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="8a35c-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8a35c-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="8a35c-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="8a35c-123">沒有足夠的記憶體可用來完成要求的配置。</span><span class="sxs-lookup"><span data-stu-id="8a35c-123">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a35c-124">備註</span><span class="sxs-lookup"><span data-stu-id="8a35c-124">Remarks</span></span>  
 <span data-ttu-id="8a35c-125">`EnterRuntime`呼叫以通知主機, 先前呼叫[LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)方法的非受控函式已完成執行, 並將執行控制傳回執行時間。</span><span class="sxs-lookup"><span data-stu-id="8a35c-125">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8a35c-126">呼叫[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)以通知主機, 先前呼叫`LeaveRuntime`的非受控函式會呼叫 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="8a35c-126">[ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a35c-127">需求</span><span class="sxs-lookup"><span data-stu-id="8a35c-127">Requirements</span></span>  
 <span data-ttu-id="8a35c-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8a35c-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a35c-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8a35c-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8a35c-130">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8a35c-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8a35c-131">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a35c-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a35c-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a35c-132">See also</span></span>

- [<span data-ttu-id="8a35c-133">進階 COM 互通性</span><span class="sxs-lookup"><span data-stu-id="8a35c-133">Advanced COM Interoperability</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx)
- [<span data-ttu-id="8a35c-134">如何：使用 PInvoke 從受控程式碼呼叫原生 DLL</span><span class="sxs-lookup"><span data-stu-id="8a35c-134">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)
- [<span data-ttu-id="8a35c-135">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="8a35c-135">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="8a35c-136">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="8a35c-136">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="8a35c-137">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="8a35c-137">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="8a35c-138">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="8a35c-138">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="8a35c-139">LeaveRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="8a35c-139">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
