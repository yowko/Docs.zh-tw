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
ms.openlocfilehash: da30e75bf4a58e66bb0dd8210368b162cf14c3f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091261"
---
# <a name="ihosttaskmanager-interface"></a><span data-ttu-id="94bd9-102">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="94bd9-102">IHostTaskManager Interface</span></span>
<span data-ttu-id="94bd9-103">提供方法，可讓 common language runtime (CLR) 會使用透過主應用程式，而不是使用標準的作業系統執行緒或 fiber 函式的工作。</span><span class="sxs-lookup"><span data-stu-id="94bd9-103">Provides methods that allow the common language runtime (CLR) to work with tasks through the host instead of using the standard operating system threading or fiber functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="94bd9-104">方法</span><span class="sxs-lookup"><span data-stu-id="94bd9-104">Methods</span></span>  
  
|<span data-ttu-id="94bd9-105">方法</span><span class="sxs-lookup"><span data-stu-id="94bd9-105">Method</span></span>|<span data-ttu-id="94bd9-106">描述</span><span class="sxs-lookup"><span data-stu-id="94bd9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="94bd9-107">BeginDelayAbort 方法</span><span class="sxs-lookup"><span data-stu-id="94bd9-107">BeginDelayAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md)|<span data-ttu-id="94bd9-108">通知主機 managed 程式碼輸入的期間，不會中止目前的工作。</span><span class="sxs-lookup"><span data-stu-id="94bd9-108">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>|  
|[<span data-ttu-id="94bd9-109">BeginThreadAffinity 方法</span><span class="sxs-lookup"><span data-stu-id="94bd9-109">BeginThreadAffinity Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md)|<span data-ttu-id="94bd9-110">通知主機 managed 程式碼會進入目前的工作不會移至另一個作業系統執行緒的週期。</span><span class="sxs-lookup"><span data-stu-id="94bd9-110">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>|  
|[<span data-ttu-id="94bd9-111">CallNeedsHostHook 方法</span><span class="sxs-lookup"><span data-stu-id="94bd9-111">CallNeedsHostHook Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)|<span data-ttu-id="94bd9-112">可讓主應用程式指定通用語言執行平台是否可以內嵌指定呼叫 unmanaged 函式。</span><span class="sxs-lookup"><span data-stu-id="94bd9-112">Enables the host to specify whether the common language runtime can inline the specified call to an unmanaged function.</span></span>|  
|[<span data-ttu-id="94bd9-113">CreateTask 方法</span><span class="sxs-lookup"><span data-stu-id="94bd9-113">CreateTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md)|<span data-ttu-id="94bd9-114">主應用程式建立新工作的要求。</span><span class="sxs-lookup"><span data-stu-id="94bd9-114">Requests that the host create a new task.</span></span>|  
|[<span data-ttu-id="94bd9-115">EndDelayAbort 方法</span><span class="sxs-lookup"><span data-stu-id="94bd9-115">EndDelayAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md)|<span data-ttu-id="94bd9-116">通知主機 managed 程式碼正在結束的期間，在其中必須不會中止目前的工作，遵循先前呼叫`BeginDelayAbort`。</span><span class="sxs-lookup"><span data-stu-id="94bd9-116">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to `BeginDelayAbort`.</span></span>|  
|[<span data-ttu-id="94bd9-117">EndThreadAffinity 方法</span><span class="sxs-lookup"><span data-stu-id="94bd9-117">EndThreadAffinity Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md)|<span data-ttu-id="94bd9-118">通知主機 managed 程式碼正在結束目前的工作不會移至另一個的作業系統執行緒的週期遵循先前呼叫`BeginThreadAffinity`。</span><span class="sxs-lookup"><span data-stu-id="94bd9-118">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to `BeginThreadAffinity`.</span></span>|  
|[<span data-ttu-id="94bd9-119">EnterRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="94bd9-119">EnterRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)|<span data-ttu-id="94bd9-120">主應用程式的呼叫未受管理的方法，例如平台叫用方法，是執行將控制權還給 CLR。</span><span class="sxs-lookup"><span data-stu-id="94bd9-120">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the CLR.</span></span>|  
|[<span data-ttu-id="94bd9-121">GetCurrentTask 方法</span><span class="sxs-lookup"><span data-stu-id="94bd9-121">GetCurrentTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md)|<span data-ttu-id="94bd9-122">取得目前正在進行這個呼叫的作業系統執行緒執行工作的介面指標。</span><span class="sxs-lookup"><span data-stu-id="94bd9-122">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>|  
|[<span data-ttu-id="94bd9-123">GetStackGuarantee 方法</span><span class="sxs-lookup"><span data-stu-id="94bd9-123">GetStackGuarantee Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getstackguarantee-method.md)|<span data-ttu-id="94bd9-124">取得量的保證堆疊操作完成之後, 才能使用的堆疊空間，但處理程序關閉之前。</span><span class="sxs-lookup"><span data-stu-id="94bd9-124">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>|  
|[<span data-ttu-id="94bd9-125">LeaveRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="94bd9-125">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)|<span data-ttu-id="94bd9-126">通知主機 managed 程式碼呼叫 unmanaged 函式。</span><span class="sxs-lookup"><span data-stu-id="94bd9-126">Notifies the host that managed code is about to make a call to an unmanaged function.</span></span>|  
|[<span data-ttu-id="94bd9-127">ReverseEnterRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="94bd9-127">ReverseEnterRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)|<span data-ttu-id="94bd9-128">主應用程式到從 unmanaged 程式碼的 common language runtime (CLR) 進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="94bd9-128">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>|  
|[<span data-ttu-id="94bd9-129">ReverseLeaveRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="94bd9-129">ReverseLeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)|<span data-ttu-id="94bd9-130">控制項是離開 CLR，並輸入 unmanaged 函式，接著呼叫函式從 managed 程式碼，請通知主機。</span><span class="sxs-lookup"><span data-stu-id="94bd9-130">Notifies the host that control is leaving the CLR and entering an unmanaged function that was, in turn, called from managed code.</span></span>|  
|[<span data-ttu-id="94bd9-131">SetCLRTaskManager 方法</span><span class="sxs-lookup"><span data-stu-id="94bd9-131">SetCLRTaskManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setclrtaskmanager-method.md)|<span data-ttu-id="94bd9-132">主應用程式提供的介面指標[ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) ，CLR 所實作的執行個體。</span><span class="sxs-lookup"><span data-stu-id="94bd9-132">Provides the host with an interface pointer to an [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="94bd9-133">SetLocale 方法</span><span class="sxs-lookup"><span data-stu-id="94bd9-133">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)|<span data-ttu-id="94bd9-134">CLR 已變更目前的工作上的地區設定會告知主應用程式。</span><span class="sxs-lookup"><span data-stu-id="94bd9-134">Notifies the host that the CLR has changed the locale on the current task.</span></span>|  
|[<span data-ttu-id="94bd9-135">SetStackGuarantee 方法</span><span class="sxs-lookup"><span data-stu-id="94bd9-135">SetStackGuarantee Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setstackguarantee-method.md)|<span data-ttu-id="94bd9-136">已保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="94bd9-136">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="94bd9-137">SetUILocale 方法</span><span class="sxs-lookup"><span data-stu-id="94bd9-137">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)|<span data-ttu-id="94bd9-138">主應用程式使用者介面的地區設定已變更為不同於目前的工作。</span><span class="sxs-lookup"><span data-stu-id="94bd9-138">Notifies the host that the user interface locale has been changed on the current task.</span></span>|  
|[<span data-ttu-id="94bd9-139">Sleep 方法</span><span class="sxs-lookup"><span data-stu-id="94bd9-139">Sleep Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md)|<span data-ttu-id="94bd9-140">將目前的工作會進入睡眠會告知主應用程式。</span><span class="sxs-lookup"><span data-stu-id="94bd9-140">Notifies the host that the current task is going to sleep.</span></span>|  
|[<span data-ttu-id="94bd9-141">SwitchToTask 方法</span><span class="sxs-lookup"><span data-stu-id="94bd9-141">SwitchToTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md)|<span data-ttu-id="94bd9-142">主應用程式，它應該切換移出目前的工作。</span><span class="sxs-lookup"><span data-stu-id="94bd9-142">Notifies the host that it should switch out the current task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94bd9-143">備註</span><span class="sxs-lookup"><span data-stu-id="94bd9-143">Remarks</span></span>  
 `IHostTaskManager` <span data-ttu-id="94bd9-144">可讓 CLR 建立和管理工作，以提供主應用程式以採取動作，當控制權從 managed 到 unmanaged 程式碼，反之亦然，並指定特定動作的勾點主機可以和程式碼執行期間無法取得。</span><span class="sxs-lookup"><span data-stu-id="94bd9-144">allows the CLR to create and manage tasks, to provide hooks for the host to take action when control transfers from managed to unmanaged code and vice versa, and to specify certain actions the host can and cannot take during code execution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94bd9-145">需求</span><span class="sxs-lookup"><span data-stu-id="94bd9-145">Requirements</span></span>  
 <span data-ttu-id="94bd9-146">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="94bd9-146">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94bd9-147">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="94bd9-147">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="94bd9-148">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="94bd9-148">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="94bd9-149">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="94bd9-149">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="94bd9-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94bd9-150">See also</span></span>

- [<span data-ttu-id="94bd9-151">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="94bd9-151">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="94bd9-152">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="94bd9-152">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="94bd9-153">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="94bd9-153">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="94bd9-154">裝載介面</span><span class="sxs-lookup"><span data-stu-id="94bd9-154">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
