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
ms.openlocfilehash: 16916d62a528222db952a1d29dc7c69de2352191
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133117"
---
# <a name="ihosttaskmanagercreatetask-method"></a><span data-ttu-id="4a102-102">IHostTaskManager::CreateTask 方法</span><span class="sxs-lookup"><span data-stu-id="4a102-102">IHostTaskManager::CreateTask Method</span></span>
<span data-ttu-id="4a102-103">要求主機建立新的工作。</span><span class="sxs-lookup"><span data-stu-id="4a102-103">Requests that the host create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a102-104">語法</span><span class="sxs-lookup"><span data-stu-id="4a102-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateTask (  
    [in]  DWORD stacksize,   
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a102-105">參數</span><span class="sxs-lookup"><span data-stu-id="4a102-105">Parameters</span></span>  
 `stacksize`  
 <span data-ttu-id="4a102-106">在要求之堆疊的要求大小（以位元組為單位），或預設大小為0（零）。</span><span class="sxs-lookup"><span data-stu-id="4a102-106">[in] The requested size, in bytes, of the requested stack, or 0 (zero) for the default size.</span></span>  
  
 `pStartAddress`  
 <span data-ttu-id="4a102-107">在工作要執行之函式的指標。</span><span class="sxs-lookup"><span data-stu-id="4a102-107">[in] A pointer to the function the task is to execute.</span></span>  
  
 `pParameter`  
 <span data-ttu-id="4a102-108">在要傳遞至函式之使用者資料的指標，如果函數不接受任何參數，則為 null。</span><span class="sxs-lookup"><span data-stu-id="4a102-108">[in] A pointer to the user data to be passed to the function, or null if the function takes no parameters.</span></span>  
  
 `ppTask`  
 <span data-ttu-id="4a102-109">脫銷主機所建立之[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)實例的位址指標，如果無法建立工作，則為 null。</span><span class="sxs-lookup"><span data-stu-id="4a102-109">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance created by the host, or null if the task cannot be created.</span></span> <span data-ttu-id="4a102-110">工作會維持在暫停狀態，直到呼叫[IHostTask：： Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)明確啟動為止。</span><span class="sxs-lookup"><span data-stu-id="4a102-110">The task remains in a suspended state until it is explicitly started by a call to [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4a102-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="4a102-111">Return Value</span></span>  
  
|<span data-ttu-id="4a102-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4a102-112">HRESULT</span></span>|<span data-ttu-id="4a102-113">描述</span><span class="sxs-lookup"><span data-stu-id="4a102-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4a102-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="4a102-114">S_OK</span></span>|<span data-ttu-id="4a102-115">已成功傳回 `CreateTask`。</span><span class="sxs-lookup"><span data-stu-id="4a102-115">`CreateTask` returned successfully.</span></span>|  
|<span data-ttu-id="4a102-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4a102-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4a102-117">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="4a102-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4a102-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4a102-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4a102-119">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="4a102-119">The call timed out.</span></span>|  
|<span data-ttu-id="4a102-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4a102-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4a102-121">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="4a102-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4a102-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4a102-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4a102-123">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="4a102-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4a102-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4a102-124">E_FAIL</span></span>|<span data-ttu-id="4a102-125">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="4a102-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4a102-126">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="4a102-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4a102-127">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="4a102-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4a102-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="4a102-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="4a102-129">沒有足夠的記憶體可用來建立要求的工作。</span><span class="sxs-lookup"><span data-stu-id="4a102-129">Not enough memory was available to create the requested task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a102-130">備註</span><span class="sxs-lookup"><span data-stu-id="4a102-130">Remarks</span></span>  
 <span data-ttu-id="4a102-131">CLR 會呼叫 `CreateTask` 來要求主機建立新的工作。</span><span class="sxs-lookup"><span data-stu-id="4a102-131">The CLR calls `CreateTask` to request that the host create a new task.</span></span> <span data-ttu-id="4a102-132">主機會將介面指標傳回 `IHostTask` 實例。</span><span class="sxs-lookup"><span data-stu-id="4a102-132">The host returns an interface pointer to an `IHostTask` instance.</span></span> <span data-ttu-id="4a102-133">傳回的工作必須保持暫停，直到 `IHostTask::Start`的呼叫明確啟動為止。</span><span class="sxs-lookup"><span data-stu-id="4a102-133">The returned task must remain suspended until it is explicitly started by a call to `IHostTask::Start`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a102-134">需求</span><span class="sxs-lookup"><span data-stu-id="4a102-134">Requirements</span></span>  
 <span data-ttu-id="4a102-135">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4a102-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a102-136">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="4a102-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4a102-137">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4a102-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4a102-138">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a102-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a102-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="4a102-139">See also</span></span>

- [<span data-ttu-id="4a102-140">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="4a102-140">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="4a102-141">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="4a102-141">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="4a102-142">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="4a102-142">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="4a102-143">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="4a102-143">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
