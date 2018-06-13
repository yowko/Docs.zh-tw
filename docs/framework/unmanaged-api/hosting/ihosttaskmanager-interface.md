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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9715738931d1b6a91ad9fae7e00ba607905d380f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449060"
---
# <a name="ihosttaskmanager-interface"></a><span data-ttu-id="c071f-102">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="c071f-102">IHostTaskManager Interface</span></span>
<span data-ttu-id="c071f-103">提供方法讓 common language runtime (CLR) 處理透過主應用程式，而不是使用標準的作業系統執行緒或 fiber 函式的工作。</span><span class="sxs-lookup"><span data-stu-id="c071f-103">Provides methods that allow the common language runtime (CLR) to work with tasks through the host instead of using the standard operating system threading or fiber functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c071f-104">方法</span><span class="sxs-lookup"><span data-stu-id="c071f-104">Methods</span></span>  
  
|<span data-ttu-id="c071f-105">方法</span><span class="sxs-lookup"><span data-stu-id="c071f-105">Method</span></span>|<span data-ttu-id="c071f-106">描述</span><span class="sxs-lookup"><span data-stu-id="c071f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c071f-107">BeginDelayAbort 方法</span><span class="sxs-lookup"><span data-stu-id="c071f-107">BeginDelayAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md)|<span data-ttu-id="c071f-108">通知主機 managed 程式碼正在進入的期間，不會中止目前的工作。</span><span class="sxs-lookup"><span data-stu-id="c071f-108">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>|  
|[<span data-ttu-id="c071f-109">BeginThreadAffinity 方法</span><span class="sxs-lookup"><span data-stu-id="c071f-109">BeginThreadAffinity Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md)|<span data-ttu-id="c071f-110">通知主機 managed 程式碼會進入目前的工作不會移至另一個作業系統執行緒的週期。</span><span class="sxs-lookup"><span data-stu-id="c071f-110">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>|  
|[<span data-ttu-id="c071f-111">CallNeedsHostHook 方法</span><span class="sxs-lookup"><span data-stu-id="c071f-111">CallNeedsHostHook Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)|<span data-ttu-id="c071f-112">可讓主應用程式指定通用語言執行平台是否可以內嵌指定呼叫 unmanaged 函式。</span><span class="sxs-lookup"><span data-stu-id="c071f-112">Enables the host to specify whether the common language runtime can inline the specified call to an unmanaged function.</span></span>|  
|[<span data-ttu-id="c071f-113">CreateTask 方法</span><span class="sxs-lookup"><span data-stu-id="c071f-113">CreateTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md)|<span data-ttu-id="c071f-114">主應用程式建立新工作的要求。</span><span class="sxs-lookup"><span data-stu-id="c071f-114">Requests that the host create a new task.</span></span>|  
|[<span data-ttu-id="c071f-115">EndDelayAbort 方法</span><span class="sxs-lookup"><span data-stu-id="c071f-115">EndDelayAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md)|<span data-ttu-id="c071f-116">通知主機 managed 程式碼正在結束的期間所在必須中止目前的工作，遵循之前呼叫`BeginDelayAbort`。</span><span class="sxs-lookup"><span data-stu-id="c071f-116">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to `BeginDelayAbort`.</span></span>|  
|[<span data-ttu-id="c071f-117">EndThreadAffinity 方法</span><span class="sxs-lookup"><span data-stu-id="c071f-117">EndThreadAffinity Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md)|<span data-ttu-id="c071f-118">通知主機 managed 程式碼會結束目前的工作不會移至另一個作業系統執行緒的期間遵循之前呼叫`BeginThreadAffinity`。</span><span class="sxs-lookup"><span data-stu-id="c071f-118">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to `BeginThreadAffinity`.</span></span>|  
|[<span data-ttu-id="c071f-119">EnterRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="c071f-119">EnterRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)|<span data-ttu-id="c071f-120">通知主機的呼叫未受管理的方法，例如平台叫用方法時，會執行將控制權傳回給 CLR。</span><span class="sxs-lookup"><span data-stu-id="c071f-120">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the CLR.</span></span>|  
|[<span data-ttu-id="c071f-121">GetCurrentTask 方法</span><span class="sxs-lookup"><span data-stu-id="c071f-121">GetCurrentTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md)|<span data-ttu-id="c071f-122">取得目前正在進行這個呼叫時之作業系統執行緒上執行工作的介面指標。</span><span class="sxs-lookup"><span data-stu-id="c071f-122">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>|  
|[<span data-ttu-id="c071f-123">GetStackGuarantee 方法</span><span class="sxs-lookup"><span data-stu-id="c071f-123">GetStackGuarantee Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getstackguarantee-method.md)|<span data-ttu-id="c071f-124">取得量保證堆疊操作完成之後, 可供使用的堆疊空間但之前結束處理序。</span><span class="sxs-lookup"><span data-stu-id="c071f-124">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>|  
|[<span data-ttu-id="c071f-125">LeaveRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="c071f-125">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)|<span data-ttu-id="c071f-126">通知主機 managed 程式碼即將呼叫以 unmanaged 函式。</span><span class="sxs-lookup"><span data-stu-id="c071f-126">Notifies the host that managed code is about to make a call to an unmanaged function.</span></span>|  
|[<span data-ttu-id="c071f-127">ReverseEnterRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="c071f-127">ReverseEnterRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)|<span data-ttu-id="c071f-128">通知主機到從 unmanaged 程式碼的 common language runtime (CLR) 進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="c071f-128">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>|  
|[<span data-ttu-id="c071f-129">ReverseLeaveRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="c071f-129">ReverseLeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)|<span data-ttu-id="c071f-130">通知主機，控制會離開 CLR，並輸入，接著，從 managed 程式碼呼叫 unmanaged 函式。</span><span class="sxs-lookup"><span data-stu-id="c071f-130">Notifies the host that control is leaving the CLR and entering an unmanaged function that was, in turn, called from managed code.</span></span>|  
|[<span data-ttu-id="c071f-131">SetCLRTaskManager 方法</span><span class="sxs-lookup"><span data-stu-id="c071f-131">SetCLRTaskManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setclrtaskmanager-method.md)|<span data-ttu-id="c071f-132">主機提供的介面指標[ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) CLR 所實作的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c071f-132">Provides the host with an interface pointer to an [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="c071f-133">SetLocale 方法</span><span class="sxs-lookup"><span data-stu-id="c071f-133">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)|<span data-ttu-id="c071f-134">通知主機，CLR 會變更目前的工作上的地區設定。</span><span class="sxs-lookup"><span data-stu-id="c071f-134">Notifies the host that the CLR has changed the locale on the current task.</span></span>|  
|[<span data-ttu-id="c071f-135">SetStackGuarantee 方法</span><span class="sxs-lookup"><span data-stu-id="c071f-135">SetStackGuarantee Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setstackguarantee-method.md)|<span data-ttu-id="c071f-136">已保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="c071f-136">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="c071f-137">SetUILocale 方法</span><span class="sxs-lookup"><span data-stu-id="c071f-137">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)|<span data-ttu-id="c071f-138">通知主機在目前的工作到已變更的使用者介面的地區設定。</span><span class="sxs-lookup"><span data-stu-id="c071f-138">Notifies the host that the user interface locale has been changed on the current task.</span></span>|  
|[<span data-ttu-id="c071f-139">Sleep 方法</span><span class="sxs-lookup"><span data-stu-id="c071f-139">Sleep Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md)|<span data-ttu-id="c071f-140">通知主機在目前的工作會進入睡眠。</span><span class="sxs-lookup"><span data-stu-id="c071f-140">Notifies the host that the current task is going to sleep.</span></span>|  
|[<span data-ttu-id="c071f-141">SwitchToTask 方法</span><span class="sxs-lookup"><span data-stu-id="c071f-141">SwitchToTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md)|<span data-ttu-id="c071f-142">通知主機，它應該切換移出目前的工作。</span><span class="sxs-lookup"><span data-stu-id="c071f-142">Notifies the host that it should switch out the current task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c071f-143">備註</span><span class="sxs-lookup"><span data-stu-id="c071f-143">Remarks</span></span>  
 <span data-ttu-id="c071f-144">`IHostTaskManager` 允許 CLR 建立和管理工作，提供主機控制權時從 managed 到 unmanaged 程式碼，反之亦然，採取動作，並指定特定動作的攔截程序主機可以和程式碼執行期間無法使用。</span><span class="sxs-lookup"><span data-stu-id="c071f-144">`IHostTaskManager` allows the CLR to create and manage tasks, to provide hooks for the host to take action when control transfers from managed to unmanaged code and vice versa, and to specify certain actions the host can and cannot take during code execution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c071f-145">需求</span><span class="sxs-lookup"><span data-stu-id="c071f-145">Requirements</span></span>  
 <span data-ttu-id="c071f-146">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c071f-146">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c071f-147">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c071f-147">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c071f-148">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c071f-148">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c071f-149">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c071f-149">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c071f-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c071f-150">See Also</span></span>  
 [<span data-ttu-id="c071f-151">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="c071f-151">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="c071f-152">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="c071f-152">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="c071f-153">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="c071f-153">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="c071f-154">裝載介面</span><span class="sxs-lookup"><span data-stu-id="c071f-154">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
