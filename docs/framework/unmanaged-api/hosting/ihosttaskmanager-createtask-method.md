---
title: IHostTaskManager::CreateTask 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CreateTask
helpviewer_keywords:
- CreateTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::CreateTask method [.NET Framework hosting]
ms.assetid: a6f8ad36-61e1-42b0-9db2-add575646d18
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2eddb11ab56bae5243ea7d00614090bbfe774f71
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096377"
---
# <a name="ihosttaskmanagercreatetask-method"></a><span data-ttu-id="706c7-102">IHostTaskManager::CreateTask 方法</span><span class="sxs-lookup"><span data-stu-id="706c7-102">IHostTaskManager::CreateTask Method</span></span>
<span data-ttu-id="706c7-103">主應用程式建立新工作的要求。</span><span class="sxs-lookup"><span data-stu-id="706c7-103">Requests that the host create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="706c7-104">語法</span><span class="sxs-lookup"><span data-stu-id="706c7-104">Syntax</span></span>  
  
```  
HRESULT CreateTask (  
    [in]  DWORD stacksize,   
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="706c7-105">參數</span><span class="sxs-lookup"><span data-stu-id="706c7-105">Parameters</span></span>  
 `stacksize`  
 <span data-ttu-id="706c7-106">[in]要求的大小，以位元組為單位，要求的堆疊，或預設大小為 0 （零）。</span><span class="sxs-lookup"><span data-stu-id="706c7-106">[in] The requested size, in bytes, of the requested stack, or 0 (zero) for the default size.</span></span>  
  
 `pStartAddress`  
 <span data-ttu-id="706c7-107">[in]工作是執行函式的指標。</span><span class="sxs-lookup"><span data-stu-id="706c7-107">[in] A pointer to the function the task is to execute.</span></span>  
  
 `pParameter`  
 <span data-ttu-id="706c7-108">[in]要傳遞至函式或如果函式的使用者資料的指標不接受任何參數。</span><span class="sxs-lookup"><span data-stu-id="706c7-108">[in] A pointer to the user data to be passed to the function, or null if the function takes no parameters.</span></span>  
  
 `ppTask`  
 <span data-ttu-id="706c7-109">[out]位址指標[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)建立主應用程式，則為 null，如果無法建立工作的執行個體。</span><span class="sxs-lookup"><span data-stu-id="706c7-109">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance created by the host, or null if the task cannot be created.</span></span> <span data-ttu-id="706c7-110">工作仍會留在暫停狀態，直到它明確呼叫來啟動[ihosttask:: Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)。</span><span class="sxs-lookup"><span data-stu-id="706c7-110">The task remains in a suspended state until it is explicitly started by a call to [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="706c7-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="706c7-111">Return Value</span></span>  
  
|<span data-ttu-id="706c7-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="706c7-112">HRESULT</span></span>|<span data-ttu-id="706c7-113">描述</span><span class="sxs-lookup"><span data-stu-id="706c7-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="706c7-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="706c7-114">S_OK</span></span>|<span data-ttu-id="706c7-115">`CreateTask` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="706c7-115">`CreateTask` returned successfully.</span></span>|  
|<span data-ttu-id="706c7-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="706c7-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="706c7-117">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="706c7-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="706c7-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="706c7-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="706c7-119">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="706c7-119">The call timed out.</span></span>|  
|<span data-ttu-id="706c7-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="706c7-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="706c7-121">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="706c7-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="706c7-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="706c7-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="706c7-123">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="706c7-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="706c7-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="706c7-124">E_FAIL</span></span>|<span data-ttu-id="706c7-125">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="706c7-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="706c7-126">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="706c7-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="706c7-127">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="706c7-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="706c7-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="706c7-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="706c7-129">沒有足夠的記憶體可用來建立要求的工作。</span><span class="sxs-lookup"><span data-stu-id="706c7-129">Not enough memory was available to create the requested task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="706c7-130">備註</span><span class="sxs-lookup"><span data-stu-id="706c7-130">Remarks</span></span>  
 <span data-ttu-id="706c7-131">CLR 會呼叫`CreateTask`要求主機建立新的工作。</span><span class="sxs-lookup"><span data-stu-id="706c7-131">The CLR calls `CreateTask` to request that the host create a new task.</span></span> <span data-ttu-id="706c7-132">主應用程式傳回的介面指標`IHostTask`執行個體。</span><span class="sxs-lookup"><span data-stu-id="706c7-132">The host returns an interface pointer to an `IHostTask` instance.</span></span> <span data-ttu-id="706c7-133">傳回的工作必須保持暫停，直到明確啟動呼叫`IHostTask::Start`。</span><span class="sxs-lookup"><span data-stu-id="706c7-133">The returned task must remain suspended until it is explicitly started by a call to `IHostTask::Start`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="706c7-134">需求</span><span class="sxs-lookup"><span data-stu-id="706c7-134">Requirements</span></span>  
 <span data-ttu-id="706c7-135">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="706c7-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="706c7-136">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="706c7-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="706c7-137">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="706c7-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="706c7-138">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="706c7-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="706c7-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="706c7-139">See also</span></span>

- [<span data-ttu-id="706c7-140">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="706c7-140">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="706c7-141">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="706c7-141">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="706c7-142">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="706c7-142">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="706c7-143">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="706c7-143">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
