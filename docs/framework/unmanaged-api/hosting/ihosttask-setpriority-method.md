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
ms.openlocfilehash: 6888e11038af09e797ebaff5a97107ceb8d662e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444059"
---
# <a name="ihosttasksetpriority-method"></a><span data-ttu-id="33683-102">IHostTask::SetPriority 方法</span><span class="sxs-lookup"><span data-stu-id="33683-102">IHostTask::SetPriority Method</span></span>
<span data-ttu-id="33683-103">表示由目前的工作要求主機調整的執行緒優先權等級[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)執行個體。</span><span class="sxs-lookup"><span data-stu-id="33683-103">Requests that the host adjust the thread priority level for the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33683-104">語法</span><span class="sxs-lookup"><span data-stu-id="33683-104">Syntax</span></span>  
  
```  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="33683-105">參數</span><span class="sxs-lookup"><span data-stu-id="33683-105">Parameters</span></span>  
 `newPriority`  
 <span data-ttu-id="33683-106">[in]整數，表示要求的執行緒優先順序值，表示由目前的工作`IHostTask`執行個體。</span><span class="sxs-lookup"><span data-stu-id="33683-106">[in] An integer that represents the requested thread priority value for the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="33683-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="33683-107">Return Value</span></span>  
  
|<span data-ttu-id="33683-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="33683-108">HRESULT</span></span>|<span data-ttu-id="33683-109">描述</span><span class="sxs-lookup"><span data-stu-id="33683-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="33683-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="33683-110">S_OK</span></span>|<span data-ttu-id="33683-111">`SetPriority` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="33683-111">`SetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="33683-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="33683-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="33683-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="33683-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="33683-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="33683-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="33683-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="33683-115">The call timed out.</span></span>|  
|<span data-ttu-id="33683-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="33683-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="33683-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="33683-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="33683-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="33683-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="33683-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="33683-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="33683-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="33683-120">E_FAIL</span></span>|<span data-ttu-id="33683-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="33683-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="33683-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="33683-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="33683-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="33683-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33683-124">備註</span><span class="sxs-lookup"><span data-stu-id="33683-124">Remarks</span></span>  
 <span data-ttu-id="33683-125">執行緒正在授與處理使用循環配置資源系統為部分基礎執行緒的優先權層級的時間。</span><span class="sxs-lookup"><span data-stu-id="33683-125">Threads are granted processing time using a round-robin system that is partly based on a thread's priority level.</span></span> <span data-ttu-id="33683-126">`SetPriority` 允許 CLR 設定為目前的工作的執行緒優先權等級。</span><span class="sxs-lookup"><span data-stu-id="33683-126">`SetPriority` allows the CLR to set that thread priority level for the current task.</span></span> <span data-ttu-id="33683-127">下列`newPriority`值才受到支援。</span><span class="sxs-lookup"><span data-stu-id="33683-127">The following `newPriority` values are supported.</span></span>  
  
-   <span data-ttu-id="33683-128">THREAD_PRIORITY_ABOVE_NORMAL</span><span class="sxs-lookup"><span data-stu-id="33683-128">THREAD_PRIORITY_ABOVE_NORMAL</span></span>  
  
-   <span data-ttu-id="33683-129">THREAD_PRIORITY_BELOW_NORMAL</span><span class="sxs-lookup"><span data-stu-id="33683-129">THREAD_PRIORITY_BELOW_NORMAL</span></span>  
  
-   <span data-ttu-id="33683-130">THREAD_PRIORITY_HIGHEST</span><span class="sxs-lookup"><span data-stu-id="33683-130">THREAD_PRIORITY_HIGHEST</span></span>  
  
-   <span data-ttu-id="33683-131">THREAD_PRIORITY_IDLE</span><span class="sxs-lookup"><span data-stu-id="33683-131">THREAD_PRIORITY_IDLE</span></span>  
  
-   <span data-ttu-id="33683-132">THREAD_PRIORITY_LOWEST</span><span class="sxs-lookup"><span data-stu-id="33683-132">THREAD_PRIORITY_LOWEST</span></span>  
  
-   <span data-ttu-id="33683-133">THREAD_PRIORITY_NORMAL</span><span class="sxs-lookup"><span data-stu-id="33683-133">THREAD_PRIORITY_NORMAL</span></span>  
  
-   <span data-ttu-id="33683-134">THREAD_PRIORITY_TIME_CRITICAL</span><span class="sxs-lookup"><span data-stu-id="33683-134">THREAD_PRIORITY_TIME_CRITICAL</span></span>  
  
 <span data-ttu-id="33683-135">CLR 會呼叫`SetPriority`時的值<xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType>修改由使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="33683-135">The CLR calls `SetPriority` when the value of the <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> is modified by user code.</span></span> <span data-ttu-id="33683-136">主機可定義它自己的演算法來指派優先權執行緒，而且可以自由地忽略此要求。</span><span class="sxs-lookup"><span data-stu-id="33683-136">A host can define its own algorithms for thread priority assignment, and is free to ignore this request.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33683-137">`SetPriority` 不會報告是否已變更執行緒的優先權層級。</span><span class="sxs-lookup"><span data-stu-id="33683-137">`SetPriority` does not report whether the thread priority level was changed.</span></span> <span data-ttu-id="33683-138">呼叫[ihosttask:: Getpriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)來判斷工作的執行緒優先權等級的值。</span><span class="sxs-lookup"><span data-stu-id="33683-138">Call [IHostTask::GetPriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) to determine the value of the task's thread priority level.</span></span>  
  
 <span data-ttu-id="33683-139">執行緒的優先權層級的值會由 Win32`SetThreadPriority`函式。</span><span class="sxs-lookup"><span data-stu-id="33683-139">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span> <span data-ttu-id="33683-140">如需詳細的執行緒優先順序的詳細資訊，請參閱 Windows 平台的文件。</span><span class="sxs-lookup"><span data-stu-id="33683-140">For more information about thread priority, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33683-141">需求</span><span class="sxs-lookup"><span data-stu-id="33683-141">Requirements</span></span>  
 <span data-ttu-id="33683-142">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="33683-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33683-143">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="33683-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="33683-144">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="33683-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="33683-145">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33683-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33683-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33683-146">See Also</span></span>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="33683-147">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="33683-147">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="33683-148">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="33683-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="33683-149">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="33683-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="33683-150">GetPriority 方法</span><span class="sxs-lookup"><span data-stu-id="33683-150">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)  
 [<span data-ttu-id="33683-151">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="33683-151">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
