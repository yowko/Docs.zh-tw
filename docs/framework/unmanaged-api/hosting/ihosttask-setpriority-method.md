---
title: IHostTask::SetPriority 方法
ms.date: 03/30/2017
api_name:
- IHostTask.SetPriority
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetPriority
helpviewer_keywords:
- IHostTask::SetPriority method [.NET Framework hosting]
- SetPriority method [.NET Framework hosting]
ms.assetid: cd8c379b-c7a0-434f-8e23-899bd26be75d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5382341a8c0c6455438af9e8c476348ab2467a6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189036"
---
# <a name="ihosttasksetpriority-method"></a><span data-ttu-id="13b1d-102">IHostTask::SetPriority 方法</span><span class="sxs-lookup"><span data-stu-id="13b1d-102">IHostTask::SetPriority Method</span></span>
<span data-ttu-id="13b1d-103">表示由目前的工作要求主應用程式調整的執行緒優先權層級[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)執行個體。</span><span class="sxs-lookup"><span data-stu-id="13b1d-103">Requests that the host adjust the thread priority level for the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13b1d-104">語法</span><span class="sxs-lookup"><span data-stu-id="13b1d-104">Syntax</span></span>  
  
```  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13b1d-105">參數</span><span class="sxs-lookup"><span data-stu-id="13b1d-105">Parameters</span></span>  
 `newPriority`  
 <span data-ttu-id="13b1d-106">[in]整數，表示要求的執行緒優先順序值，表示由目前的工作`IHostTask`執行個體。</span><span class="sxs-lookup"><span data-stu-id="13b1d-106">[in] An integer that represents the requested thread priority value for the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13b1d-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="13b1d-107">Return Value</span></span>  
  
|<span data-ttu-id="13b1d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="13b1d-108">HRESULT</span></span>|<span data-ttu-id="13b1d-109">描述</span><span class="sxs-lookup"><span data-stu-id="13b1d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="13b1d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="13b1d-110">S_OK</span></span>|`SetPriority` <span data-ttu-id="13b1d-111">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="13b1d-111">returned successfully.</span></span>|  
|<span data-ttu-id="13b1d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="13b1d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="13b1d-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="13b1d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="13b1d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="13b1d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="13b1d-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="13b1d-115">The call timed out.</span></span>|  
|<span data-ttu-id="13b1d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="13b1d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="13b1d-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="13b1d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="13b1d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="13b1d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="13b1d-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="13b1d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="13b1d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="13b1d-120">E_FAIL</span></span>|<span data-ttu-id="13b1d-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="13b1d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="13b1d-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="13b1d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="13b1d-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="13b1d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13b1d-124">備註</span><span class="sxs-lookup"><span data-stu-id="13b1d-124">Remarks</span></span>  
 <span data-ttu-id="13b1d-125">執行緒正在授與處理使用的部分以執行緒的優先權層級為基礎的循環配置資源系統的時間。</span><span class="sxs-lookup"><span data-stu-id="13b1d-125">Threads are granted processing time using a round-robin system that is partly based on a thread's priority level.</span></span> `SetPriority` <span data-ttu-id="13b1d-126">可讓 CLR 設定目前工作的執行緒優先權層級。</span><span class="sxs-lookup"><span data-stu-id="13b1d-126">allows the CLR to set that thread priority level for the current task.</span></span> <span data-ttu-id="13b1d-127">下列`newPriority`支援值。</span><span class="sxs-lookup"><span data-stu-id="13b1d-127">The following `newPriority` values are supported.</span></span>  
  
-   <span data-ttu-id="13b1d-128">THREAD_PRIORITY_ABOVE_NORMAL</span><span class="sxs-lookup"><span data-stu-id="13b1d-128">THREAD_PRIORITY_ABOVE_NORMAL</span></span>  
  
-   <span data-ttu-id="13b1d-129">THREAD_PRIORITY_BELOW_NORMAL</span><span class="sxs-lookup"><span data-stu-id="13b1d-129">THREAD_PRIORITY_BELOW_NORMAL</span></span>  
  
-   <span data-ttu-id="13b1d-130">THREAD_PRIORITY_HIGHEST</span><span class="sxs-lookup"><span data-stu-id="13b1d-130">THREAD_PRIORITY_HIGHEST</span></span>  
  
-   <span data-ttu-id="13b1d-131">THREAD_PRIORITY_IDLE</span><span class="sxs-lookup"><span data-stu-id="13b1d-131">THREAD_PRIORITY_IDLE</span></span>  
  
-   <span data-ttu-id="13b1d-132">THREAD_PRIORITY_LOWEST</span><span class="sxs-lookup"><span data-stu-id="13b1d-132">THREAD_PRIORITY_LOWEST</span></span>  
  
-   <span data-ttu-id="13b1d-133">THREAD_PRIORITY_NORMAL</span><span class="sxs-lookup"><span data-stu-id="13b1d-133">THREAD_PRIORITY_NORMAL</span></span>  
  
-   <span data-ttu-id="13b1d-134">THREAD_PRIORITY_TIME_CRITICAL</span><span class="sxs-lookup"><span data-stu-id="13b1d-134">THREAD_PRIORITY_TIME_CRITICAL</span></span>  
  
 <span data-ttu-id="13b1d-135">CLR 會呼叫`SetPriority`時的值<xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType>修改使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="13b1d-135">The CLR calls `SetPriority` when the value of the <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> is modified by user code.</span></span> <span data-ttu-id="13b1d-136">主機可以定義自己的演算法，來指派執行緒優先權，，而且可以自由地忽略這項要求。</span><span class="sxs-lookup"><span data-stu-id="13b1d-136">A host can define its own algorithms for thread priority assignment, and is free to ignore this request.</span></span>  
  
> [!NOTE]
>  `SetPriority` <span data-ttu-id="13b1d-137">不會報告是否已變更的執行緒優先權層級。</span><span class="sxs-lookup"><span data-stu-id="13b1d-137">does not report whether the thread priority level was changed.</span></span> <span data-ttu-id="13b1d-138">呼叫[ihosttask:: Getpriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)來判斷工作的執行緒優先權層級的值。</span><span class="sxs-lookup"><span data-stu-id="13b1d-138">Call [IHostTask::GetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) to determine the value of the task's thread priority level.</span></span>  
  
 <span data-ttu-id="13b1d-139">定義 win32 執行緒優先權層級值`SetThreadPriority`函式。</span><span class="sxs-lookup"><span data-stu-id="13b1d-139">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span> <span data-ttu-id="13b1d-140">如需執行緒優先權的詳細資訊，請參閱 < Windows 平台的文件。</span><span class="sxs-lookup"><span data-stu-id="13b1d-140">For more information about thread priority, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13b1d-141">需求</span><span class="sxs-lookup"><span data-stu-id="13b1d-141">Requirements</span></span>  
 <span data-ttu-id="13b1d-142">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="13b1d-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13b1d-143">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="13b1d-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="13b1d-144">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="13b1d-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="13b1d-145">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="13b1d-145">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="13b1d-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13b1d-146">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="13b1d-147">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="13b1d-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="13b1d-148">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="13b1d-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="13b1d-149">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="13b1d-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="13b1d-150">GetPriority 方法</span><span class="sxs-lookup"><span data-stu-id="13b1d-150">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)
- [<span data-ttu-id="13b1d-151">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="13b1d-151">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
