---
title: "ICLRDebugManager::SetConnectionTasks 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugManager.SetConnectionTasks
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDebugManager::SetConnectionTasks
helpviewer_keywords:
- SetConnectionTasks method [.NET Framework hosting]
- ICLRDebugManager::SetConnectionTasks method [.NET Framework hosting]
ms.assetid: b38bbc9a-872c-41a9-b8c3-ca011d25456a
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 09f7e47acfcfbde8d5d9724c3a37303f1a584adb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebugmanagersetconnectiontasks-method"></a><span data-ttu-id="dae61-102">ICLRDebugManager::SetConnectionTasks 方法</span><span class="sxs-lookup"><span data-stu-id="dae61-102">ICLRDebugManager::SetConnectionTasks Method</span></span>
<span data-ttu-id="dae61-103">將一份[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)識別碼和易記名稱與執行個體。</span><span class="sxs-lookup"><span data-stu-id="dae61-103">Associates a list of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dae61-104">語法</span><span class="sxs-lookup"><span data-stu-id="dae61-104">Syntax</span></span>  
  
```  
HRESULT SetConnectionTasks (  
    [in] CONNID id,  
    [in] DWORD dwCount,  
    [in, size_is(dwCount)] ICLRTask **ppCLRTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dae61-105">參數</span><span class="sxs-lookup"><span data-stu-id="dae61-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="dae61-106">[in]連接與相關聯的主應用程式特定識別項`ppCLRTask`陣列。</span><span class="sxs-lookup"><span data-stu-id="dae61-106">[in] The host-specific identifier for the connection with which to associate the `ppCLRTask` array.</span></span>  
  
 `dwCount`  
 <span data-ttu-id="dae61-107">[in]成員數目`ppCLRTask`。</span><span class="sxs-lookup"><span data-stu-id="dae61-107">[in] The number of members of `ppCLRTask`.</span></span> <span data-ttu-id="dae61-108">這個數字必須小於或等於零。</span><span class="sxs-lookup"><span data-stu-id="dae61-108">This number must be greater than zero.</span></span>  
  
 `ppCLRTask`  
 <span data-ttu-id="dae61-109">[in]陣列`ICLRTask`與所識別的連接產生關聯的指標`id`。</span><span class="sxs-lookup"><span data-stu-id="dae61-109">[in] An array of `ICLRTask` pointers to associate with the connection identified by `id`.</span></span> <span data-ttu-id="dae61-110">這個陣列必須包含至少一個成員。</span><span class="sxs-lookup"><span data-stu-id="dae61-110">This array must contain at least one member.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dae61-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="dae61-111">Return Value</span></span>  
  
|<span data-ttu-id="dae61-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dae61-112">HRESULT</span></span>|<span data-ttu-id="dae61-113">描述</span><span class="sxs-lookup"><span data-stu-id="dae61-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dae61-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="dae61-114">S_OK</span></span>|<span data-ttu-id="dae61-115">`SetConnectionTasks`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="dae61-115">`SetConnectionTasks` returned successfully.</span></span>|  
|<span data-ttu-id="dae61-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dae61-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dae61-117">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="dae61-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dae61-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dae61-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dae61-119">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="dae61-119">The call timed out.</span></span>|  
|<span data-ttu-id="dae61-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dae61-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dae61-121">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="dae61-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dae61-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dae61-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dae61-123">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="dae61-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dae61-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dae61-124">E_FAIL</span></span>|<span data-ttu-id="dae61-125">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="dae61-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dae61-126">方法會傳回 E_FAIL 之後，CLR 就不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="dae61-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dae61-127">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="dae61-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="dae61-128">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="dae61-128">E_INVALIDARG</span></span>|<span data-ttu-id="dae61-129">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)尚未呼叫使用這個值`id`，或`dwCount`或`id`是零或一個項目的`ppCLRTask`為 null。</span><span class="sxs-lookup"><span data-stu-id="dae61-129">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) has not been called using this value of `id`, or `dwCount` or `id` is zero, or one of the elements of `ppCLRTask` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dae61-130">備註</span><span class="sxs-lookup"><span data-stu-id="dae61-130">Remarks</span></span>  
 <span data-ttu-id="dae61-131">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)提供三種方法， `BeginConnection`， `SetConnectionTasks`，和[EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)，將工作清單與識別項和好記的名稱產生關聯。</span><span class="sxs-lookup"><span data-stu-id="dae61-131">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, `SetConnectionTasks`, and [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="dae61-132">這三種方法必須針對每個工作集的特定順序呼叫。</span><span class="sxs-lookup"><span data-stu-id="dae61-132">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="dae61-133">`BeginConnection`會先呼叫來建立新的連線。</span><span class="sxs-lookup"><span data-stu-id="dae61-133">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="dae61-134">`SetConnectionTasks`呼叫下一個提供與該連接相關聯的工作集合。</span><span class="sxs-lookup"><span data-stu-id="dae61-134">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="dae61-135">`EndConnection`最後會呼叫以移除工作清單的識別碼和易記名稱之間的關聯。不過，可以是巢狀呼叫不同的連接。</span><span class="sxs-lookup"><span data-stu-id="dae61-135">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dae61-136">需求</span><span class="sxs-lookup"><span data-stu-id="dae61-136">Requirements</span></span>  
 <span data-ttu-id="dae61-137">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dae61-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dae61-138">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dae61-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dae61-139">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="dae61-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dae61-140">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dae61-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dae61-141">請參閱</span><span class="sxs-lookup"><span data-stu-id="dae61-141">See Also</span></span>  
 [<span data-ttu-id="dae61-142">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="dae61-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="dae61-143">ICLRDebugManager 介面</span><span class="sxs-lookup"><span data-stu-id="dae61-143">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="dae61-144">BeginConnection 方法</span><span class="sxs-lookup"><span data-stu-id="dae61-144">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)  
 [<span data-ttu-id="dae61-145">EndConnection 方法</span><span class="sxs-lookup"><span data-stu-id="dae61-145">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)  
 [<span data-ttu-id="dae61-146">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="dae61-146">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
