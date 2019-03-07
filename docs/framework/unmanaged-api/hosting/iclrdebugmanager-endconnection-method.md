---
title: ICLRDebugManager::EndConnection 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60e110e019619f9336b240fdc5aee8fa66c5bcdb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479178"
---
# <a name="iclrdebugmanagerendconnection-method"></a><span data-ttu-id="97fcb-102">ICLRDebugManager::EndConnection 方法</span><span class="sxs-lookup"><span data-stu-id="97fcb-102">ICLRDebugManager::EndConnection Method</span></span>
<span data-ttu-id="97fcb-103">移除工作清單和識別項和易記名稱之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="97fcb-103">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97fcb-104">語法</span><span class="sxs-lookup"><span data-stu-id="97fcb-104">Syntax</span></span>  
  
```  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97fcb-105">參數</span><span class="sxs-lookup"><span data-stu-id="97fcb-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="97fcb-106">[in]連接和相關聯的 common language runtime (CLR) 工作清單的主控件特有識別碼。</span><span class="sxs-lookup"><span data-stu-id="97fcb-106">[in] The host-specific identifier for the connection and the associated list of common language runtime (CLR) tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97fcb-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="97fcb-107">Return Value</span></span>  
  
|<span data-ttu-id="97fcb-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="97fcb-108">HRESULT</span></span>|<span data-ttu-id="97fcb-109">描述</span><span class="sxs-lookup"><span data-stu-id="97fcb-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="97fcb-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="97fcb-110">S_OK</span></span>|<span data-ttu-id="97fcb-111">`EndConnection` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="97fcb-111">`EndConnection` returned successfully.</span></span>|  
|<span data-ttu-id="97fcb-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="97fcb-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="97fcb-113">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="97fcb-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="97fcb-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="97fcb-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="97fcb-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="97fcb-115">The call timed out.</span></span>|  
|<span data-ttu-id="97fcb-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="97fcb-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="97fcb-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="97fcb-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="97fcb-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="97fcb-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="97fcb-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="97fcb-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="97fcb-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="97fcb-120">E_FAIL</span></span>|<span data-ttu-id="97fcb-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="97fcb-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="97fcb-122">方法會傳回 E_FAIL 之後，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="97fcb-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="97fcb-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="97fcb-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="97fcb-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="97fcb-124">E_INVALIDARG</span></span>|<span data-ttu-id="97fcb-125">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)永遠不會使用呼叫`dwConnectionId`，或`dwConnectionId`是零。</span><span class="sxs-lookup"><span data-stu-id="97fcb-125">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) was never called using `dwConnectionId`, or `dwConnectionId` was zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97fcb-126">備註</span><span class="sxs-lookup"><span data-stu-id="97fcb-126">Remarks</span></span>  
 <span data-ttu-id="97fcb-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)提供三種方法， `BeginConnection`， [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)，和`EndConnection`，關聯識別碼和易記名稱的工作清單。</span><span class="sxs-lookup"><span data-stu-id="97fcb-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and `EndConnection`, for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="97fcb-128">這三種方法必須呼叫每一組工作的特定順序。</span><span class="sxs-lookup"><span data-stu-id="97fcb-128">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="97fcb-129">`BeginConnection` 會先呼叫來建立新的連線。</span><span class="sxs-lookup"><span data-stu-id="97fcb-129">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="97fcb-130">`SetConnectionTasks` 會接著呼叫以提供一組與該連接相關聯的工作。</span><span class="sxs-lookup"><span data-stu-id="97fcb-130">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="97fcb-131">`EndConnection` 是最後呼叫以移除工作清單的識別碼和易記名稱之間的關聯。不過，可以是巢狀呼叫不同的連接。</span><span class="sxs-lookup"><span data-stu-id="97fcb-131">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97fcb-132">需求</span><span class="sxs-lookup"><span data-stu-id="97fcb-132">Requirements</span></span>  
 <span data-ttu-id="97fcb-133">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="97fcb-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97fcb-134">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="97fcb-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="97fcb-135">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="97fcb-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="97fcb-136">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97fcb-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97fcb-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97fcb-137">See also</span></span>
- [<span data-ttu-id="97fcb-138">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="97fcb-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="97fcb-139">ICLRDebugManager 介面</span><span class="sxs-lookup"><span data-stu-id="97fcb-139">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="97fcb-140">BeginConnection 方法</span><span class="sxs-lookup"><span data-stu-id="97fcb-140">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="97fcb-141">SetConnectionTasks 方法</span><span class="sxs-lookup"><span data-stu-id="97fcb-141">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="97fcb-142">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="97fcb-142">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
