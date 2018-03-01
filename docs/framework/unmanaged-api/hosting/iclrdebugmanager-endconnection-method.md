---
title: "ICLRDebugManager::EndConnection 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRDebugManager.EndConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::EndConnection
helpviewer_keywords:
- ICLRDebugManager::EndConnection method [.NET Framework hosting]
- EndConnection method [.NET Framework hosting]
ms.assetid: 89dc7363-2f29-4eb2-8f23-fccdda6a76a6
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 210226b697eb3dffe574bd842ca31e83948891a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebugmanagerendconnection-method"></a><span data-ttu-id="689a1-102">ICLRDebugManager::EndConnection 方法</span><span class="sxs-lookup"><span data-stu-id="689a1-102">ICLRDebugManager::EndConnection Method</span></span>
<span data-ttu-id="689a1-103">移除關聯的工作清單和識別項和好記的名稱。</span><span class="sxs-lookup"><span data-stu-id="689a1-103">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="689a1-104">語法</span><span class="sxs-lookup"><span data-stu-id="689a1-104">Syntax</span></span>  
  
```  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="689a1-105">參數</span><span class="sxs-lookup"><span data-stu-id="689a1-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="689a1-106">[in]連接和相關聯的 common language runtime (CLR) 工作清單的特定主機的識別碼。</span><span class="sxs-lookup"><span data-stu-id="689a1-106">[in] The host-specific identifier for the connection and the associated list of common language runtime (CLR) tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="689a1-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="689a1-107">Return Value</span></span>  
  
|<span data-ttu-id="689a1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="689a1-108">HRESULT</span></span>|<span data-ttu-id="689a1-109">描述</span><span class="sxs-lookup"><span data-stu-id="689a1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="689a1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="689a1-110">S_OK</span></span>|<span data-ttu-id="689a1-111">`EndConnection`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="689a1-111">`EndConnection` returned successfully.</span></span>|  
|<span data-ttu-id="689a1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="689a1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="689a1-113">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="689a1-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="689a1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="689a1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="689a1-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="689a1-115">The call timed out.</span></span>|  
|<span data-ttu-id="689a1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="689a1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="689a1-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="689a1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="689a1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="689a1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="689a1-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="689a1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="689a1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="689a1-120">E_FAIL</span></span>|<span data-ttu-id="689a1-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="689a1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="689a1-122">方法會傳回 E_FAIL 之後，CLR 就不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="689a1-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="689a1-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="689a1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="689a1-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="689a1-124">E_INVALIDARG</span></span>|<span data-ttu-id="689a1-125">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)永遠不會使用呼叫`dwConnectionId`，或`dwConnectionId`是零。</span><span class="sxs-lookup"><span data-stu-id="689a1-125">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) was never called using `dwConnectionId`, or `dwConnectionId` was zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="689a1-126">備註</span><span class="sxs-lookup"><span data-stu-id="689a1-126">Remarks</span></span>  
 <span data-ttu-id="689a1-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)提供三種方法， `BeginConnection`， [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)，和`EndConnection`，將工作清單與識別項和好記的名稱產生關聯。</span><span class="sxs-lookup"><span data-stu-id="689a1-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and `EndConnection`, for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="689a1-128">這三種方法必須針對每個工作集的特定順序呼叫。</span><span class="sxs-lookup"><span data-stu-id="689a1-128">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="689a1-129">`BeginConnection`會先呼叫來建立新的連線。</span><span class="sxs-lookup"><span data-stu-id="689a1-129">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="689a1-130">`SetConnectionTasks`呼叫下一個提供與該連接相關聯的工作集合。</span><span class="sxs-lookup"><span data-stu-id="689a1-130">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="689a1-131">`EndConnection`最後會呼叫以移除工作清單的識別碼和易記名稱之間的關聯。不過，可以是巢狀呼叫不同的連接。</span><span class="sxs-lookup"><span data-stu-id="689a1-131">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="689a1-132">需求</span><span class="sxs-lookup"><span data-stu-id="689a1-132">Requirements</span></span>  
 <span data-ttu-id="689a1-133">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="689a1-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="689a1-134">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="689a1-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="689a1-135">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="689a1-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="689a1-136">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="689a1-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="689a1-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="689a1-137">See Also</span></span>  
 [<span data-ttu-id="689a1-138">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="689a1-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="689a1-139">ICLRDebugManager 介面</span><span class="sxs-lookup"><span data-stu-id="689a1-139">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="689a1-140">BeginConnection 方法</span><span class="sxs-lookup"><span data-stu-id="689a1-140">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)  
 [<span data-ttu-id="689a1-141">SetConnectionTasks 方法</span><span class="sxs-lookup"><span data-stu-id="689a1-141">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)  
 [<span data-ttu-id="689a1-142">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="689a1-142">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
