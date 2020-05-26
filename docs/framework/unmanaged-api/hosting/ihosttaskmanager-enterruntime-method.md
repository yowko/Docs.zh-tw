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
ms.openlocfilehash: b255a1d35aa32975c879aac00f7d4edb8ea88d3b
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842032"
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="2f68e-102">IHostTaskManager::EnterRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="2f68e-102">IHostTaskManager::EnterRuntime Method</span></span>
<span data-ttu-id="2f68e-103">通知主機呼叫非受控方法（例如平台叫用方法），會將執行控制傳回給 common language runtime （CLR）。</span><span class="sxs-lookup"><span data-stu-id="2f68e-103">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f68e-104">語法</span><span class="sxs-lookup"><span data-stu-id="2f68e-104">Syntax</span></span>  
  
```cpp  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2f68e-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="2f68e-105">Return Value</span></span>  
  
|<span data-ttu-id="2f68e-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2f68e-106">HRESULT</span></span>|<span data-ttu-id="2f68e-107">描述</span><span class="sxs-lookup"><span data-stu-id="2f68e-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2f68e-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="2f68e-108">S_OK</span></span>|<span data-ttu-id="2f68e-109">`EnterRuntime`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="2f68e-109">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="2f68e-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2f68e-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2f68e-111">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="2f68e-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2f68e-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2f68e-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2f68e-113">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="2f68e-113">The call timed out.</span></span>|  
|<span data-ttu-id="2f68e-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2f68e-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2f68e-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="2f68e-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2f68e-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2f68e-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2f68e-117">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="2f68e-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2f68e-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2f68e-118">E_FAIL</span></span>|<span data-ttu-id="2f68e-119">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="2f68e-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2f68e-120">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="2f68e-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2f68e-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="2f68e-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2f68e-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="2f68e-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="2f68e-123">沒有足夠的記憶體可用來完成要求的配置。</span><span class="sxs-lookup"><span data-stu-id="2f68e-123">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f68e-124">備註</span><span class="sxs-lookup"><span data-stu-id="2f68e-124">Remarks</span></span>  
 <span data-ttu-id="2f68e-125">`EnterRuntime`呼叫以通知主機，先前呼叫[LeaveRuntime](ihosttaskmanager-leaveruntime-method.md)方法的非受控函式已完成執行，並將執行控制傳回執行時間。</span><span class="sxs-lookup"><span data-stu-id="2f68e-125">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f68e-126">呼叫[ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md)以通知主機，先前呼叫的非受控函式 `LeaveRuntime` 會呼叫 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="2f68e-126">[ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f68e-127">規格需求</span><span class="sxs-lookup"><span data-stu-id="2f68e-127">Requirements</span></span>  
 <span data-ttu-id="2f68e-128">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2f68e-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f68e-129">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="2f68e-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2f68e-130">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2f68e-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2f68e-131">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f68e-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f68e-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f68e-132">See also</span></span>

- <span data-ttu-id="2f68e-133">[進階 COM 互通性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2f68e-133">[Advanced COM Interoperability](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>
- [<span data-ttu-id="2f68e-134">如何：使用 PInvoke 從 Managed 程式碼呼叫原生 Dll</span><span class="sxs-lookup"><span data-stu-id="2f68e-134">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)
- [<span data-ttu-id="2f68e-135">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="2f68e-135">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="2f68e-136">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="2f68e-136">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="2f68e-137">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="2f68e-137">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="2f68e-138">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="2f68e-138">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="2f68e-139">LeaveRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="2f68e-139">LeaveRuntime Method</span></span>](ihosttaskmanager-leaveruntime-method.md)
