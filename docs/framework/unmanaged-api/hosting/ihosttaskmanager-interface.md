---
title: IHostTaskManager 介面
ms.date: 03/30/2017
api_name:
- IHostTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager
helpviewer_keywords:
- IHostTaskManager interface [.NET Framework hosting]
ms.assetid: 4a0b05b9-3ef1-4607-b7c8-bd4dd43647a0
topic_type:
- apiref
ms.openlocfilehash: 470e2ac06f433dc12d66f6cac97337a6de1d8183
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133013"
---
# <a name="ihosttaskmanager-interface"></a><span data-ttu-id="9b821-102">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="9b821-102">IHostTaskManager Interface</span></span>
<span data-ttu-id="9b821-103">提供的方法可讓 common language runtime （CLR）透過主機來處理工作，而不是使用標準作業系統執行緒或光纖函數。</span><span class="sxs-lookup"><span data-stu-id="9b821-103">Provides methods that allow the common language runtime (CLR) to work with tasks through the host instead of using the standard operating system threading or fiber functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9b821-104">方法</span><span class="sxs-lookup"><span data-stu-id="9b821-104">Methods</span></span>  
  
|<span data-ttu-id="9b821-105">方法</span><span class="sxs-lookup"><span data-stu-id="9b821-105">Method</span></span>|<span data-ttu-id="9b821-106">描述</span><span class="sxs-lookup"><span data-stu-id="9b821-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9b821-107">BeginDelayAbort 方法</span><span class="sxs-lookup"><span data-stu-id="9b821-107">BeginDelayAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md)|<span data-ttu-id="9b821-108">通知主機 managed 程式碼所輸入的期間不得中止目前的工作。</span><span class="sxs-lookup"><span data-stu-id="9b821-108">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>|  
|[<span data-ttu-id="9b821-109">BeginThreadAffinity 方法</span><span class="sxs-lookup"><span data-stu-id="9b821-109">BeginThreadAffinity Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md)|<span data-ttu-id="9b821-110">通知主機 managed 程式碼所輸入的期間，不能將目前的工作移至另一個作業系統執行緒。</span><span class="sxs-lookup"><span data-stu-id="9b821-110">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>|  
|[<span data-ttu-id="9b821-111">CallNeedsHostHook 方法</span><span class="sxs-lookup"><span data-stu-id="9b821-111">CallNeedsHostHook Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)|<span data-ttu-id="9b821-112">可讓主機指定通用語言執行時間是否可以將指定的呼叫內嵌至非受控函式。</span><span class="sxs-lookup"><span data-stu-id="9b821-112">Enables the host to specify whether the common language runtime can inline the specified call to an unmanaged function.</span></span>|  
|[<span data-ttu-id="9b821-113">CreateTask 方法</span><span class="sxs-lookup"><span data-stu-id="9b821-113">CreateTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md)|<span data-ttu-id="9b821-114">要求主機建立新的工作。</span><span class="sxs-lookup"><span data-stu-id="9b821-114">Requests that the host create a new task.</span></span>|  
|[<span data-ttu-id="9b821-115">EndDelayAbort 方法</span><span class="sxs-lookup"><span data-stu-id="9b821-115">EndDelayAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md)|<span data-ttu-id="9b821-116">在先前的 `BeginDelayAbort`呼叫之後，通知主機 managed 程式碼即將結束，但目前的工作不得中止。</span><span class="sxs-lookup"><span data-stu-id="9b821-116">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to `BeginDelayAbort`.</span></span>|  
|[<span data-ttu-id="9b821-117">EndThreadAffinity 方法</span><span class="sxs-lookup"><span data-stu-id="9b821-117">EndThreadAffinity Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md)|<span data-ttu-id="9b821-118">在先前的 `BeginThreadAffinity`呼叫之後，通知主機 managed 程式碼即將結束，而無法將目前的工作移至另一個作業系統執行緒。</span><span class="sxs-lookup"><span data-stu-id="9b821-118">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to `BeginThreadAffinity`.</span></span>|  
|[<span data-ttu-id="9b821-119">EnterRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="9b821-119">EnterRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)|<span data-ttu-id="9b821-120">通知主機呼叫非受控方法（例如平台叫用方法）時，會將執行控制傳回給 CLR。</span><span class="sxs-lookup"><span data-stu-id="9b821-120">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the CLR.</span></span>|  
|[<span data-ttu-id="9b821-121">GetCurrentTask 方法</span><span class="sxs-lookup"><span data-stu-id="9b821-121">GetCurrentTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md)|<span data-ttu-id="9b821-122">取得目前在執行此呼叫之作業系統執行緒上執行之工作的介面指標。</span><span class="sxs-lookup"><span data-stu-id="9b821-122">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>|  
|[<span data-ttu-id="9b821-123">GetStackGuarantee 方法</span><span class="sxs-lookup"><span data-stu-id="9b821-123">GetStackGuarantee Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getstackguarantee-method.md)|<span data-ttu-id="9b821-124">取得堆疊作業完成後，但在關閉進程之前，保證可以使用的堆疊空間量。</span><span class="sxs-lookup"><span data-stu-id="9b821-124">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>|  
|[<span data-ttu-id="9b821-125">LeaveRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="9b821-125">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)|<span data-ttu-id="9b821-126">通知主機 managed 程式碼即將進行非受控函式的呼叫。</span><span class="sxs-lookup"><span data-stu-id="9b821-126">Notifies the host that managed code is about to make a call to an unmanaged function.</span></span>|  
|[<span data-ttu-id="9b821-127">ReverseEnterRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="9b821-127">ReverseEnterRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)|<span data-ttu-id="9b821-128">通知主機正在從非受控碼對 common language runtime （CLR）進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="9b821-128">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>|  
|[<span data-ttu-id="9b821-129">ReverseLeaveRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="9b821-129">ReverseLeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)|<span data-ttu-id="9b821-130">通知主控制項離開 CLR，並輸入從 managed 程式碼呼叫的非受控函式。</span><span class="sxs-lookup"><span data-stu-id="9b821-130">Notifies the host that control is leaving the CLR and entering an unmanaged function that was, in turn, called from managed code.</span></span>|  
|[<span data-ttu-id="9b821-131">SetCLRTaskManager 方法</span><span class="sxs-lookup"><span data-stu-id="9b821-131">SetCLRTaskManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setclrtaskmanager-method.md)|<span data-ttu-id="9b821-132">提供具有 CLR 所實[ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)實例之介面指標的主機。</span><span class="sxs-lookup"><span data-stu-id="9b821-132">Provides the host with an interface pointer to an [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="9b821-133">SetLocale 方法</span><span class="sxs-lookup"><span data-stu-id="9b821-133">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)|<span data-ttu-id="9b821-134">通知主機 CLR 已變更目前工作的地區設定。</span><span class="sxs-lookup"><span data-stu-id="9b821-134">Notifies the host that the CLR has changed the locale on the current task.</span></span>|  
|[<span data-ttu-id="9b821-135">SetStackGuarantee 方法</span><span class="sxs-lookup"><span data-stu-id="9b821-135">SetStackGuarantee Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setstackguarantee-method.md)|<span data-ttu-id="9b821-136">已保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="9b821-136">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="9b821-137">SetUILocale 方法</span><span class="sxs-lookup"><span data-stu-id="9b821-137">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)|<span data-ttu-id="9b821-138">通知主機使用者介面地區設定已在目前的工作上變更。</span><span class="sxs-lookup"><span data-stu-id="9b821-138">Notifies the host that the user interface locale has been changed on the current task.</span></span>|  
|[<span data-ttu-id="9b821-139">Sleep 方法</span><span class="sxs-lookup"><span data-stu-id="9b821-139">Sleep Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md)|<span data-ttu-id="9b821-140">通知主機目前的工作即將進入睡眠狀態。</span><span class="sxs-lookup"><span data-stu-id="9b821-140">Notifies the host that the current task is going to sleep.</span></span>|  
|[<span data-ttu-id="9b821-141">SwitchToTask 方法</span><span class="sxs-lookup"><span data-stu-id="9b821-141">SwitchToTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md)|<span data-ttu-id="9b821-142">通知主機應該切換出目前的工作。</span><span class="sxs-lookup"><span data-stu-id="9b821-142">Notifies the host that it should switch out the current task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b821-143">備註</span><span class="sxs-lookup"><span data-stu-id="9b821-143">Remarks</span></span>  
 <span data-ttu-id="9b821-144">`IHostTaskManager` 可讓 CLR 建立和管理工作，以提供攔截程式，讓主機在控制從 managed 傳送至非受控碼時採取動作，反之亦然，以及指定主機在程式碼執行期間可以執行的特定動作。</span><span class="sxs-lookup"><span data-stu-id="9b821-144">`IHostTaskManager` allows the CLR to create and manage tasks, to provide hooks for the host to take action when control transfers from managed to unmanaged code and vice versa, and to specify certain actions the host can and cannot take during code execution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b821-145">需求</span><span class="sxs-lookup"><span data-stu-id="9b821-145">Requirements</span></span>  
 <span data-ttu-id="9b821-146">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9b821-146">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b821-147">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="9b821-147">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9b821-148">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9b821-148">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9b821-149">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b821-149">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b821-150">請參閱</span><span class="sxs-lookup"><span data-stu-id="9b821-150">See also</span></span>

- [<span data-ttu-id="9b821-151">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="9b821-151">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="9b821-152">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="9b821-152">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="9b821-153">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="9b821-153">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="9b821-154">裝載介面</span><span class="sxs-lookup"><span data-stu-id="9b821-154">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
