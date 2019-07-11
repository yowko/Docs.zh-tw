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
ms.openlocfilehash: cb3044927e0d9975ed9347cd4f4896b3b75d3e29
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749630"
---
# <a name="ihosttaskmanagergetcurrenttask-method"></a><span data-ttu-id="d958b-102">IHostTaskManager::GetCurrentTask 方法</span><span class="sxs-lookup"><span data-stu-id="d958b-102">IHostTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="d958b-103">取得目前正在進行這個呼叫的作業系統執行緒執行工作的介面指標。</span><span class="sxs-lookup"><span data-stu-id="d958b-103">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d958b-104">語法</span><span class="sxs-lookup"><span data-stu-id="d958b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTask (  
    [out] IHostTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d958b-105">參數</span><span class="sxs-lookup"><span data-stu-id="d958b-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="d958b-106">[out]位址指標[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)代表目前正在執行的工作或 null，如果沒有工作正在執行的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d958b-106">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the currently executing task, or null, if no task is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d958b-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="d958b-107">Return Value</span></span>  
  
|<span data-ttu-id="d958b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d958b-108">HRESULT</span></span>|<span data-ttu-id="d958b-109">描述</span><span class="sxs-lookup"><span data-stu-id="d958b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d958b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d958b-110">S_OK</span></span>|<span data-ttu-id="d958b-111">`GetCurrentTask` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="d958b-111">`GetCurrentTask` returned successfully.</span></span>|  
|<span data-ttu-id="d958b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d958b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d958b-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="d958b-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d958b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d958b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d958b-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="d958b-115">The call timed out.</span></span>|  
|<span data-ttu-id="d958b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d958b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d958b-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="d958b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d958b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d958b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d958b-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="d958b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d958b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d958b-120">E_FAIL</span></span>|<span data-ttu-id="d958b-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="d958b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d958b-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="d958b-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d958b-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d958b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d958b-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="d958b-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="d958b-125">`GetCurrentTask` 主應用程式的控制之外的作業系統執行緒上呼叫。</span><span class="sxs-lookup"><span data-stu-id="d958b-125">`GetCurrentTask` was called on an operating system thread outside the control of the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d958b-126">備註</span><span class="sxs-lookup"><span data-stu-id="d958b-126">Remarks</span></span>  
 <span data-ttu-id="d958b-127">主機也可以設定`pTask`參數為 null 以進入 CLR 時，防止不是由系統起始的工作。</span><span class="sxs-lookup"><span data-stu-id="d958b-127">The host can also set the `pTask` parameter to null to prevent a task that it did not initiate from entering the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d958b-128">需求</span><span class="sxs-lookup"><span data-stu-id="d958b-128">Requirements</span></span>  
 <span data-ttu-id="d958b-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d958b-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d958b-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d958b-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d958b-131">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d958b-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d958b-132">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d958b-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d958b-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d958b-133">See also</span></span>

- [<span data-ttu-id="d958b-134">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="d958b-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="d958b-135">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="d958b-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="d958b-136">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="d958b-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="d958b-137">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="d958b-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
