---
title: IHostTaskManager::GetCurrentTask 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: f17bca49-90bd-4dee-a5e1-b9a57ea46f85
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd92b03d87672875661bb5e5241c6fa46f099ce6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732462"
---
# <a name="ihosttaskmanagergetcurrenttask-method"></a><span data-ttu-id="dabbd-102">IHostTaskManager::GetCurrentTask 方法</span><span class="sxs-lookup"><span data-stu-id="dabbd-102">IHostTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="dabbd-103">取得目前正在進行這個呼叫的作業系統執行緒執行工作的介面指標。</span><span class="sxs-lookup"><span data-stu-id="dabbd-103">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dabbd-104">語法</span><span class="sxs-lookup"><span data-stu-id="dabbd-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTask (  
    [out] IHostTask **pTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dabbd-105">參數</span><span class="sxs-lookup"><span data-stu-id="dabbd-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="dabbd-106">[out]位址指標[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)代表目前正在執行的工作或 null，如果沒有工作正在執行的執行個體。</span><span class="sxs-lookup"><span data-stu-id="dabbd-106">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the currently executing task, or null, if no task is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dabbd-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="dabbd-107">Return Value</span></span>  
  
|<span data-ttu-id="dabbd-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dabbd-108">HRESULT</span></span>|<span data-ttu-id="dabbd-109">描述</span><span class="sxs-lookup"><span data-stu-id="dabbd-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dabbd-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="dabbd-110">S_OK</span></span>|<span data-ttu-id="dabbd-111">`GetCurrentTask` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="dabbd-111">`GetCurrentTask` returned successfully.</span></span>|  
|<span data-ttu-id="dabbd-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dabbd-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dabbd-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="dabbd-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dabbd-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dabbd-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dabbd-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="dabbd-115">The call timed out.</span></span>|  
|<span data-ttu-id="dabbd-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dabbd-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dabbd-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="dabbd-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dabbd-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dabbd-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dabbd-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="dabbd-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dabbd-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dabbd-120">E_FAIL</span></span>|<span data-ttu-id="dabbd-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="dabbd-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dabbd-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="dabbd-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dabbd-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="dabbd-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="dabbd-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="dabbd-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="dabbd-125">`GetCurrentTask` 主應用程式的控制之外的作業系統執行緒上呼叫。</span><span class="sxs-lookup"><span data-stu-id="dabbd-125">`GetCurrentTask` was called on an operating system thread outside the control of the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dabbd-126">備註</span><span class="sxs-lookup"><span data-stu-id="dabbd-126">Remarks</span></span>  
 <span data-ttu-id="dabbd-127">主機也可以設定`pTask`參數為 null 以進入 CLR 時，防止不是由系統起始的工作。</span><span class="sxs-lookup"><span data-stu-id="dabbd-127">The host can also set the `pTask` parameter to null to prevent a task that it did not initiate from entering the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dabbd-128">需求</span><span class="sxs-lookup"><span data-stu-id="dabbd-128">Requirements</span></span>  
 <span data-ttu-id="dabbd-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dabbd-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dabbd-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dabbd-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dabbd-131">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="dabbd-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dabbd-132">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dabbd-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dabbd-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dabbd-133">See also</span></span>
- [<span data-ttu-id="dabbd-134">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="dabbd-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="dabbd-135">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="dabbd-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="dabbd-136">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="dabbd-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="dabbd-137">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="dabbd-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
