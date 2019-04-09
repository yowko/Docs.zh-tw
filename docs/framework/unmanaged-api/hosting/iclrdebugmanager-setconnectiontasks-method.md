---
title: ICLRDebugManager::SetConnectionTasks 方法
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.SetConnectionTasks
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::SetConnectionTasks
helpviewer_keywords:
- SetConnectionTasks method [.NET Framework hosting]
- ICLRDebugManager::SetConnectionTasks method [.NET Framework hosting]
ms.assetid: b38bbc9a-872c-41a9-b8c3-ca011d25456a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88078fa34910dca642eae3cf261c9e00fae4f27a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201984"
---
# <a name="iclrdebugmanagersetconnectiontasks-method"></a><span data-ttu-id="2d2d5-102">ICLRDebugManager::SetConnectionTasks 方法</span><span class="sxs-lookup"><span data-stu-id="2d2d5-102">ICLRDebugManager::SetConnectionTasks Method</span></span>
<span data-ttu-id="2d2d5-103">將一份[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)識別碼和易記名稱的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2d2d5-103">Associates a list of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d2d5-104">語法</span><span class="sxs-lookup"><span data-stu-id="2d2d5-104">Syntax</span></span>  
  
```  
HRESULT SetConnectionTasks (  
    [in] CONNID id,  
    [in] DWORD dwCount,  
    [in, size_is(dwCount)] ICLRTask **ppCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d2d5-105">參數</span><span class="sxs-lookup"><span data-stu-id="2d2d5-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="2d2d5-106">[in]與相關聯的連線的主應用程式特定識別項`ppCLRTask`陣列。</span><span class="sxs-lookup"><span data-stu-id="2d2d5-106">[in] The host-specific identifier for the connection with which to associate the `ppCLRTask` array.</span></span>  
  
 `dwCount`  
 <span data-ttu-id="2d2d5-107">[in]成員數目`ppCLRTask`。</span><span class="sxs-lookup"><span data-stu-id="2d2d5-107">[in] The number of members of `ppCLRTask`.</span></span> <span data-ttu-id="2d2d5-108">此數目必須小於或等於零。</span><span class="sxs-lookup"><span data-stu-id="2d2d5-108">This number must be greater than zero.</span></span>  
  
 `ppCLRTask`  
 <span data-ttu-id="2d2d5-109">[in]陣列`ICLRTask`所識別的連接相關聯的指標`id`。</span><span class="sxs-lookup"><span data-stu-id="2d2d5-109">[in] An array of `ICLRTask` pointers to associate with the connection identified by `id`.</span></span> <span data-ttu-id="2d2d5-110">這個陣列必須包含至少一個成員。</span><span class="sxs-lookup"><span data-stu-id="2d2d5-110">This array must contain at least one member.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d2d5-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="2d2d5-111">Return Value</span></span>  
  
|<span data-ttu-id="2d2d5-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2d2d5-112">HRESULT</span></span>|<span data-ttu-id="2d2d5-113">描述</span><span class="sxs-lookup"><span data-stu-id="2d2d5-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2d2d5-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="2d2d5-114">S_OK</span></span>|`SetConnectionTasks` <span data-ttu-id="2d2d5-115">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="2d2d5-115">returned successfully.</span></span>|  
|<span data-ttu-id="2d2d5-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2d2d5-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2d2d5-117">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="2d2d5-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2d2d5-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2d2d5-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2d2d5-119">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="2d2d5-119">The call timed out.</span></span>|  
|<span data-ttu-id="2d2d5-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2d2d5-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2d2d5-121">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="2d2d5-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2d2d5-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2d2d5-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2d2d5-123">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="2d2d5-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2d2d5-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2d2d5-124">E_FAIL</span></span>|<span data-ttu-id="2d2d5-125">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="2d2d5-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2d2d5-126">方法會傳回 E_FAIL 之後，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="2d2d5-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2d2d5-127">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="2d2d5-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2d2d5-128">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2d2d5-128">E_INVALIDARG</span></span>|<span data-ttu-id="2d2d5-129">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)尚未呼叫使用此值`id`，或`dwCount`或是`id`為零或其中一個的項目`ppCLRTask`為 null。</span><span class="sxs-lookup"><span data-stu-id="2d2d5-129">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) has not been called using this value of `id`, or `dwCount` or `id` is zero, or one of the elements of `ppCLRTask` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d2d5-130">備註</span><span class="sxs-lookup"><span data-stu-id="2d2d5-130">Remarks</span></span>  
 <span data-ttu-id="2d2d5-131">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)提供三種方法， `BeginConnection`， `SetConnectionTasks`，以及[EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)，關聯識別碼和易記名稱的工作清單。</span><span class="sxs-lookup"><span data-stu-id="2d2d5-131">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, `SetConnectionTasks`, and [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2d2d5-132">這三種方法必須呼叫每一組工作的特定順序。</span><span class="sxs-lookup"><span data-stu-id="2d2d5-132">These three methods must be called in a specific order for each set of tasks.</span></span> `BeginConnection` <span data-ttu-id="2d2d5-133">會先呼叫來建立新的連線。</span><span class="sxs-lookup"><span data-stu-id="2d2d5-133">is called first to establish a new connection.</span></span> `SetConnectionTasks` <span data-ttu-id="2d2d5-134">會接著呼叫以提供一組與該連接相關聯的工作。</span><span class="sxs-lookup"><span data-stu-id="2d2d5-134">is called next to provide the set of tasks to be associated with that connection.</span></span> `EndConnection` <span data-ttu-id="2d2d5-135">是最後呼叫以移除工作清單的識別碼和易記名稱之間的關聯。不過，可以是巢狀呼叫不同的連接。</span><span class="sxs-lookup"><span data-stu-id="2d2d5-135">is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d2d5-136">需求</span><span class="sxs-lookup"><span data-stu-id="2d2d5-136">Requirements</span></span>  
 <span data-ttu-id="2d2d5-137">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2d2d5-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d2d5-138">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2d2d5-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2d2d5-139">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2d2d5-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="2d2d5-140">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="2d2d5-140">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2d2d5-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d2d5-141">See also</span></span>

- [<span data-ttu-id="2d2d5-142">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="2d2d5-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="2d2d5-143">ICLRDebugManager 介面</span><span class="sxs-lookup"><span data-stu-id="2d2d5-143">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="2d2d5-144">BeginConnection 方法</span><span class="sxs-lookup"><span data-stu-id="2d2d5-144">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="2d2d5-145">EndConnection 方法</span><span class="sxs-lookup"><span data-stu-id="2d2d5-145">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="2d2d5-146">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="2d2d5-146">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
