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
ms.openlocfilehash: deb14d291bfd511e8f3534f3c5e32787c259c5e8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673107"
---
# <a name="ihosttaskmanager-interface"></a><span data-ttu-id="25f00-102">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="25f00-102">IHostTaskManager Interface</span></span>

<span data-ttu-id="25f00-103">提供可讓 common language runtime (CLR) 透過主機處理工作的方法，而不是使用標準作業系統執行緒或光纖函數。</span><span class="sxs-lookup"><span data-stu-id="25f00-103">Provides methods that allow the common language runtime (CLR) to work with tasks through the host instead of using the standard operating system threading or fiber functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="25f00-104">方法</span><span class="sxs-lookup"><span data-stu-id="25f00-104">Methods</span></span>  
  
|<span data-ttu-id="25f00-105">方法</span><span class="sxs-lookup"><span data-stu-id="25f00-105">Method</span></span>|<span data-ttu-id="25f00-106">描述</span><span class="sxs-lookup"><span data-stu-id="25f00-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="25f00-107">BeginDelayAbort 方法</span><span class="sxs-lookup"><span data-stu-id="25f00-107">BeginDelayAbort Method</span></span>](ihosttaskmanager-begindelayabort-method.md)|<span data-ttu-id="25f00-108">通知主機 managed 程式碼所輸入的期間，不能中止目前的工作。</span><span class="sxs-lookup"><span data-stu-id="25f00-108">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>|  
|[<span data-ttu-id="25f00-109">BeginThreadAffinity 方法</span><span class="sxs-lookup"><span data-stu-id="25f00-109">BeginThreadAffinity Method</span></span>](ihosttaskmanager-beginthreadaffinity-method.md)|<span data-ttu-id="25f00-110">通知主機 managed 程式碼所輸入的期間，不能將目前的工作移至另一個作業系統執行緒。</span><span class="sxs-lookup"><span data-stu-id="25f00-110">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>|  
|[<span data-ttu-id="25f00-111">CallNeedsHostHook 方法</span><span class="sxs-lookup"><span data-stu-id="25f00-111">CallNeedsHostHook Method</span></span>](ihosttaskmanager-callneedshosthook-method.md)|<span data-ttu-id="25f00-112">可讓主機指定 common language runtime 是否可以將指定的呼叫內嵌至非受控函式。</span><span class="sxs-lookup"><span data-stu-id="25f00-112">Enables the host to specify whether the common language runtime can inline the specified call to an unmanaged function.</span></span>|  
|[<span data-ttu-id="25f00-113">CreateTask 方法</span><span class="sxs-lookup"><span data-stu-id="25f00-113">CreateTask Method</span></span>](ihosttaskmanager-createtask-method.md)|<span data-ttu-id="25f00-114">要求主機建立新的工作。</span><span class="sxs-lookup"><span data-stu-id="25f00-114">Requests that the host create a new task.</span></span>|  
|[<span data-ttu-id="25f00-115">EndDelayAbort 方法</span><span class="sxs-lookup"><span data-stu-id="25f00-115">EndDelayAbort Method</span></span>](ihosttaskmanager-enddelayabort-method.md)|<span data-ttu-id="25f00-116">在先前的呼叫之後，通知主機 managed 程式碼即將結束，也就是目前的工作不得中止的期間 `BeginDelayAbort` 。</span><span class="sxs-lookup"><span data-stu-id="25f00-116">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to `BeginDelayAbort`.</span></span>|  
|[<span data-ttu-id="25f00-117">EndThreadAffinity 方法</span><span class="sxs-lookup"><span data-stu-id="25f00-117">EndThreadAffinity Method</span></span>](ihosttaskmanager-endthreadaffinity-method.md)|<span data-ttu-id="25f00-118">在先前的呼叫之後，通知主機 managed 程式碼即將結束，且目前的工作不得移至另一個作業系統執行緒 `BeginThreadAffinity` 。</span><span class="sxs-lookup"><span data-stu-id="25f00-118">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to `BeginThreadAffinity`.</span></span>|  
|[<span data-ttu-id="25f00-119">EnterRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="25f00-119">EnterRuntime Method</span></span>](ihosttaskmanager-enterruntime-method.md)|<span data-ttu-id="25f00-120">通知主機，對非受控方法的呼叫（例如平台叫用方法）會將執行控制傳回至 CLR。</span><span class="sxs-lookup"><span data-stu-id="25f00-120">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the CLR.</span></span>|  
|[<span data-ttu-id="25f00-121">GetCurrentTask 方法</span><span class="sxs-lookup"><span data-stu-id="25f00-121">GetCurrentTask Method</span></span>](ihosttaskmanager-getcurrenttask-method.md)|<span data-ttu-id="25f00-122">取得執行此呼叫之作業系統執行緒上目前正在執行之工作的介面指標。</span><span class="sxs-lookup"><span data-stu-id="25f00-122">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>|  
|[<span data-ttu-id="25f00-123">GetStackGuarantee 方法</span><span class="sxs-lookup"><span data-stu-id="25f00-123">GetStackGuarantee Method</span></span>](ihosttaskmanager-getstackguarantee-method.md)|<span data-ttu-id="25f00-124">取得在堆疊作業完成之後，但在進程關閉之前，保證可供使用的堆疊空間量。</span><span class="sxs-lookup"><span data-stu-id="25f00-124">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>|  
|[<span data-ttu-id="25f00-125">LeaveRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="25f00-125">LeaveRuntime Method</span></span>](ihosttaskmanager-leaveruntime-method.md)|<span data-ttu-id="25f00-126">通知主機 managed 程式碼即將呼叫非受控函式。</span><span class="sxs-lookup"><span data-stu-id="25f00-126">Notifies the host that managed code is about to make a call to an unmanaged function.</span></span>|  
|[<span data-ttu-id="25f00-127">ReverseEnterRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="25f00-127">ReverseEnterRuntime Method</span></span>](ihosttaskmanager-reverseenterruntime-method.md)|<span data-ttu-id="25f00-128">通知主機從非受控程式碼對 common language runtime (CLR) 進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="25f00-128">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>|  
|[<span data-ttu-id="25f00-129">ReverseLeaveRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="25f00-129">ReverseLeaveRuntime Method</span></span>](ihosttaskmanager-reverseleaveruntime-method.md)|<span data-ttu-id="25f00-130">通知主控制項正在離開 CLR，並輸入從 managed 程式碼呼叫的非受控函式。</span><span class="sxs-lookup"><span data-stu-id="25f00-130">Notifies the host that control is leaving the CLR and entering an unmanaged function that was, in turn, called from managed code.</span></span>|  
|[<span data-ttu-id="25f00-131">SetCLRTaskManager 方法</span><span class="sxs-lookup"><span data-stu-id="25f00-131">SetCLRTaskManager Method</span></span>](ihosttaskmanager-setclrtaskmanager-method.md)|<span data-ttu-id="25f00-132">為主機提供由 CLR 所執行之 [ICLRTaskManager](iclrtaskmanager-interface.md) 實例的介面指標。</span><span class="sxs-lookup"><span data-stu-id="25f00-132">Provides the host with an interface pointer to an [ICLRTaskManager](iclrtaskmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="25f00-133">SetLocale 方法</span><span class="sxs-lookup"><span data-stu-id="25f00-133">SetLocale Method</span></span>](ihosttaskmanager-setlocale-method.md)|<span data-ttu-id="25f00-134">通知主機 CLR 已變更目前工作的地區設定。</span><span class="sxs-lookup"><span data-stu-id="25f00-134">Notifies the host that the CLR has changed the locale on the current task.</span></span>|  
|[<span data-ttu-id="25f00-135">SetStackGuarantee 方法</span><span class="sxs-lookup"><span data-stu-id="25f00-135">SetStackGuarantee Method</span></span>](ihosttaskmanager-setstackguarantee-method.md)|<span data-ttu-id="25f00-136">已保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="25f00-136">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="25f00-137">SetUILocale 方法</span><span class="sxs-lookup"><span data-stu-id="25f00-137">SetUILocale Method</span></span>](ihosttaskmanager-setuilocale-method.md)|<span data-ttu-id="25f00-138">通知主機目前的工作已變更使用者介面地區設定。</span><span class="sxs-lookup"><span data-stu-id="25f00-138">Notifies the host that the user interface locale has been changed on the current task.</span></span>|  
|[<span data-ttu-id="25f00-139">Sleep 方法</span><span class="sxs-lookup"><span data-stu-id="25f00-139">Sleep Method</span></span>](ihosttaskmanager-sleep-method.md)|<span data-ttu-id="25f00-140">通知主機目前的工作即將進入睡眠狀態。</span><span class="sxs-lookup"><span data-stu-id="25f00-140">Notifies the host that the current task is going to sleep.</span></span>|  
|[<span data-ttu-id="25f00-141">SwitchToTask 方法</span><span class="sxs-lookup"><span data-stu-id="25f00-141">SwitchToTask Method</span></span>](ihosttaskmanager-switchtotask-method.md)|<span data-ttu-id="25f00-142">通知主機應該切換出目前的工作。</span><span class="sxs-lookup"><span data-stu-id="25f00-142">Notifies the host that it should switch out the current task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25f00-143">備註</span><span class="sxs-lookup"><span data-stu-id="25f00-143">Remarks</span></span>  

 <span data-ttu-id="25f00-144">`IHostTaskManager` 允許 CLR 建立和管理工作，以便在控制從 managed 至非受控程式碼的傳輸時，以及指定主機在程式碼執行期間可執行和不能執行的特定動作時，提供攔截功能讓主機採取動作。</span><span class="sxs-lookup"><span data-stu-id="25f00-144">`IHostTaskManager` allows the CLR to create and manage tasks, to provide hooks for the host to take action when control transfers from managed to unmanaged code and vice versa, and to specify certain actions the host can and cannot take during code execution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25f00-145">需求</span><span class="sxs-lookup"><span data-stu-id="25f00-145">Requirements</span></span>  

 <span data-ttu-id="25f00-146">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="25f00-146">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25f00-147">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="25f00-147">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="25f00-148">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="25f00-148">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25f00-149">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25f00-149">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25f00-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25f00-150">See also</span></span>

- [<span data-ttu-id="25f00-151">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="25f00-151">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="25f00-152">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="25f00-152">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="25f00-153">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="25f00-153">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="25f00-154">裝載介面</span><span class="sxs-lookup"><span data-stu-id="25f00-154">Hosting Interfaces</span></span>](hosting-interfaces.md)
