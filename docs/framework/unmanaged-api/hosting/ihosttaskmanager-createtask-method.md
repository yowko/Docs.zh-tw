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
ms.openlocfilehash: fef2f56fd000a8610a40661a30aa306ae5a7884e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177992"
---
# <a name="ihosttaskmanagercreatetask-method"></a><span data-ttu-id="1ddae-102">IHostTaskManager::CreateTask 方法</span><span class="sxs-lookup"><span data-stu-id="1ddae-102">IHostTaskManager::CreateTask Method</span></span>
<span data-ttu-id="1ddae-103">請求主機創建新任務。</span><span class="sxs-lookup"><span data-stu-id="1ddae-103">Requests that the host create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ddae-104">語法</span><span class="sxs-lookup"><span data-stu-id="1ddae-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateTask (  
    [in]  DWORD stacksize,
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ddae-105">參數</span><span class="sxs-lookup"><span data-stu-id="1ddae-105">Parameters</span></span>  
 `stacksize`  
 <span data-ttu-id="1ddae-106">[在]請求的堆疊的請求大小（以位元組為單位），預設大小為 0（零）。</span><span class="sxs-lookup"><span data-stu-id="1ddae-106">[in] The requested size, in bytes, of the requested stack, or 0 (zero) for the default size.</span></span>  
  
 `pStartAddress`  
 <span data-ttu-id="1ddae-107">[在]指向任務要執行的函數的指標。</span><span class="sxs-lookup"><span data-stu-id="1ddae-107">[in] A pointer to the function the task is to execute.</span></span>  
  
 `pParameter`  
 <span data-ttu-id="1ddae-108">[在]指向要傳遞給函數的使用者資料的指標，如果函數不採用任何參數，則為 null。</span><span class="sxs-lookup"><span data-stu-id="1ddae-108">[in] A pointer to the user data to be passed to the function, or null if the function takes no parameters.</span></span>  
  
 `ppTask`  
 <span data-ttu-id="1ddae-109">[出]指向主機創建的[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)實例位址的指標，如果無法創建任務，則為 null。</span><span class="sxs-lookup"><span data-stu-id="1ddae-109">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance created by the host, or null if the task cannot be created.</span></span> <span data-ttu-id="1ddae-110">任務將保持掛起狀態，直到通過調用[IHostTask：：：開始](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)顯式啟動它。</span><span class="sxs-lookup"><span data-stu-id="1ddae-110">The task remains in a suspended state until it is explicitly started by a call to [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ddae-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="1ddae-111">Return Value</span></span>  
  
|<span data-ttu-id="1ddae-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1ddae-112">HRESULT</span></span>|<span data-ttu-id="1ddae-113">描述</span><span class="sxs-lookup"><span data-stu-id="1ddae-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1ddae-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="1ddae-114">S_OK</span></span>|<span data-ttu-id="1ddae-115">`CreateTask`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="1ddae-115">`CreateTask` returned successfully.</span></span>|  
|<span data-ttu-id="1ddae-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1ddae-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1ddae-117">公共語言運行時 （CLR） 尚未載入到進程中，或者 CLR 處於無法運行託管代碼或成功處理調用的狀態。</span><span class="sxs-lookup"><span data-stu-id="1ddae-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1ddae-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1ddae-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1ddae-119">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="1ddae-119">The call timed out.</span></span>|  
|<span data-ttu-id="1ddae-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1ddae-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1ddae-121">調用方不擁有鎖。</span><span class="sxs-lookup"><span data-stu-id="1ddae-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1ddae-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1ddae-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1ddae-123">當阻塞的執行緒或光纖等待事件時，事件已被取消。</span><span class="sxs-lookup"><span data-stu-id="1ddae-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1ddae-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1ddae-124">E_FAIL</span></span>|<span data-ttu-id="1ddae-125">發生了未知的災難性故障。</span><span class="sxs-lookup"><span data-stu-id="1ddae-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1ddae-126">當方法返回E_FAIL時，CLR 在進程中不再可用。</span><span class="sxs-lookup"><span data-stu-id="1ddae-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1ddae-127">對託管方法的後續調用返回HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="1ddae-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1ddae-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="1ddae-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="1ddae-129">沒有足夠的記憶體可用於創建請求的任務。</span><span class="sxs-lookup"><span data-stu-id="1ddae-129">Not enough memory was available to create the requested task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ddae-130">備註</span><span class="sxs-lookup"><span data-stu-id="1ddae-130">Remarks</span></span>  
 <span data-ttu-id="1ddae-131">CLR 調用`CreateTask`請求主機創建新任務。</span><span class="sxs-lookup"><span data-stu-id="1ddae-131">The CLR calls `CreateTask` to request that the host create a new task.</span></span> <span data-ttu-id="1ddae-132">主機返回指向實例的`IHostTask`介面指標。</span><span class="sxs-lookup"><span data-stu-id="1ddae-132">The host returns an interface pointer to an `IHostTask` instance.</span></span> <span data-ttu-id="1ddae-133">返回的任務必須保持掛起狀態，直到調用 顯式啟動`IHostTask::Start`。</span><span class="sxs-lookup"><span data-stu-id="1ddae-133">The returned task must remain suspended until it is explicitly started by a call to `IHostTask::Start`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ddae-134">需求</span><span class="sxs-lookup"><span data-stu-id="1ddae-134">Requirements</span></span>  
 <span data-ttu-id="1ddae-135">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1ddae-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ddae-136">**標題：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1ddae-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1ddae-137">**庫：** 作為資源包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="1ddae-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1ddae-138">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ddae-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ddae-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ddae-139">See also</span></span>

- [<span data-ttu-id="1ddae-140">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="1ddae-140">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="1ddae-141">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="1ddae-141">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="1ddae-142">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="1ddae-142">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="1ddae-143">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="1ddae-143">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
