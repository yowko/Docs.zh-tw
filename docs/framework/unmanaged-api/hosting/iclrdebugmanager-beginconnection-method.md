---
title: "ICLRDebugManager::BeginConnection 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugManager.BeginConnection
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDebugManager::BeginConnection
helpviewer_keywords:
- ICLRDebugManager::BeginConnection method [.NET Framework hosting]
- BeginConnection method [.NET Framework hosting]
ms.assetid: bdd98146-ff4d-4150-a264-a4c1a32d31f3
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a637ba71dc966cf311526f468393ef4207e10460
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebugmanagerbeginconnection-method"></a><span data-ttu-id="f9b42-102">ICLRDebugManager::BeginConnection 方法</span><span class="sxs-lookup"><span data-stu-id="f9b42-102">ICLRDebugManager::BeginConnection Method</span></span>
<span data-ttu-id="f9b42-103">建立主應用程式與偵錯工具與識別項和好記的名稱產生關聯的工作清單之間的新連接。</span><span class="sxs-lookup"><span data-stu-id="f9b42-103">Establishes a new connection between the host and the debugger to associate a list of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9b42-104">語法</span><span class="sxs-lookup"><span data-stu-id="f9b42-104">Syntax</span></span>  
  
```  
HRESULT BeginConnection (  
    [in] CONNID dwConnectionId,  
    [in, string] wchar_t* szConnectionName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f9b42-105">參數</span><span class="sxs-lookup"><span data-stu-id="f9b42-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="f9b42-106">[in]要使用的 common language runtime (CLR) 工作清單產生關聯的識別項。</span><span class="sxs-lookup"><span data-stu-id="f9b42-106">[in] An identifier to associate with the list of common language runtime (CLR) tasks.</span></span>  
  
 `szConnectionName`  
 <span data-ttu-id="f9b42-107">[in]與 CLR 工作清單中的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="f9b42-107">[in] A friendly name to associate with the list of CLR tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9b42-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="f9b42-108">Return Value</span></span>  
  
|<span data-ttu-id="f9b42-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f9b42-109">HRESULT</span></span>|<span data-ttu-id="f9b42-110">描述</span><span class="sxs-lookup"><span data-stu-id="f9b42-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f9b42-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f9b42-111">S_OK</span></span>|<span data-ttu-id="f9b42-112">`BeginConnection`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="f9b42-112">`BeginConnection` returned successfully.</span></span>|  
|<span data-ttu-id="f9b42-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f9b42-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f9b42-114">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="f9b42-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f9b42-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f9b42-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f9b42-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="f9b42-116">The call timed out.</span></span>|  
|<span data-ttu-id="f9b42-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f9b42-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f9b42-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="f9b42-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f9b42-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f9b42-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f9b42-120">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="f9b42-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f9b42-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f9b42-121">E_FAIL</span></span>|<span data-ttu-id="f9b42-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="f9b42-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f9b42-123">方法會傳回 E_FAIL 之後，CLR 就不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="f9b42-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f9b42-124">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="f9b42-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f9b42-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f9b42-125">E_INVALIDARG</span></span>|<span data-ttu-id="f9b42-126">`dwConnectionId`是零，或`BeginConnection`已經使用這項功能稱為`dwConnectionId`值，或`szConnectionName`為 null。</span><span class="sxs-lookup"><span data-stu-id="f9b42-126">`dwConnectionId` was zero, or `BeginConnection` was already called using this `dwConnectionId` value, or `szConnectionName` was null.</span></span>|  
|<span data-ttu-id="f9b42-127">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="f9b42-127">E_OUTOFMEMORY</span></span>|<span data-ttu-id="f9b42-128">記憶體不足，無法配置來保存與此連線相關聯的工作清單。</span><span class="sxs-lookup"><span data-stu-id="f9b42-128">Not enough memory could be allocated to hold the list of tasks associated with this connection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9b42-129">備註</span><span class="sxs-lookup"><span data-stu-id="f9b42-129">Remarks</span></span>  
 <span data-ttu-id="f9b42-130">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)提供三種方法， `BeginConnection`， [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)，和[EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)，將工作清單與識別項和好記的名稱產生關聯。</span><span class="sxs-lookup"><span data-stu-id="f9b42-130">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f9b42-131">這三種方法必須針對每個工作集的特定順序呼叫。</span><span class="sxs-lookup"><span data-stu-id="f9b42-131">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="f9b42-132">`BeginConnection`會先呼叫來建立新的連線。</span><span class="sxs-lookup"><span data-stu-id="f9b42-132">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="f9b42-133">`SetConnectionTasks`呼叫下一個提供與該連接相關聯的工作集合。</span><span class="sxs-lookup"><span data-stu-id="f9b42-133">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="f9b42-134">`EndConnection`最後會呼叫以移除工作清單的識別碼和易記名稱之間的關聯。不過，可以是巢狀呼叫不同的連接。</span><span class="sxs-lookup"><span data-stu-id="f9b42-134">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9b42-135">需求</span><span class="sxs-lookup"><span data-stu-id="f9b42-135">Requirements</span></span>  
 <span data-ttu-id="f9b42-136">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f9b42-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9b42-137">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f9b42-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f9b42-138">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f9b42-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f9b42-139">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9b42-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9b42-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="f9b42-140">See Also</span></span>  
 [<span data-ttu-id="f9b42-141">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="f9b42-141">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="f9b42-142">ICLRDebugManager 介面</span><span class="sxs-lookup"><span data-stu-id="f9b42-142">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="f9b42-143">EndConnection 方法</span><span class="sxs-lookup"><span data-stu-id="f9b42-143">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)  
 [<span data-ttu-id="f9b42-144">SetConnectionTasks 方法</span><span class="sxs-lookup"><span data-stu-id="f9b42-144">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)  
 [<span data-ttu-id="f9b42-145">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="f9b42-145">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
