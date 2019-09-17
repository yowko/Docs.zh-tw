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
ms.openlocfilehash: 85db4247ebe4a488f7907e195bb0f25f72d87e9b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951356"
---
# <a name="iclrdebugmanagersetconnectiontasks-method"></a><span data-ttu-id="82551-102">ICLRDebugManager::SetConnectionTasks 方法</span><span class="sxs-lookup"><span data-stu-id="82551-102">ICLRDebugManager::SetConnectionTasks Method</span></span>
<span data-ttu-id="82551-103">將[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)實例的清單與識別碼和易記名稱產生關聯。</span><span class="sxs-lookup"><span data-stu-id="82551-103">Associates a list of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82551-104">語法</span><span class="sxs-lookup"><span data-stu-id="82551-104">Syntax</span></span>  
  
```cpp  
HRESULT SetConnectionTasks (  
    [in] CONNID id,  
    [in] DWORD dwCount,  
    [in, size_is(dwCount)] ICLRTask **ppCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82551-105">參數</span><span class="sxs-lookup"><span data-stu-id="82551-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="82551-106">在與`ppCLRTask`陣列相關聯之連接的主機特定識別碼。</span><span class="sxs-lookup"><span data-stu-id="82551-106">[in] The host-specific identifier for the connection with which to associate the `ppCLRTask` array.</span></span>  
  
 `dwCount`  
 <span data-ttu-id="82551-107">在的成員`ppCLRTask`數目。</span><span class="sxs-lookup"><span data-stu-id="82551-107">[in] The number of members of `ppCLRTask`.</span></span> <span data-ttu-id="82551-108">這個數位必須大於零。</span><span class="sxs-lookup"><span data-stu-id="82551-108">This number must be greater than zero.</span></span>  
  
 `ppCLRTask`  
 <span data-ttu-id="82551-109">在要與所`ICLRTask` `id`識別之連接產生關聯的指標陣列。</span><span class="sxs-lookup"><span data-stu-id="82551-109">[in] An array of `ICLRTask` pointers to associate with the connection identified by `id`.</span></span> <span data-ttu-id="82551-110">此陣列至少必須包含一個成員。</span><span class="sxs-lookup"><span data-stu-id="82551-110">This array must contain at least one member.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82551-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="82551-111">Return Value</span></span>  
  
|<span data-ttu-id="82551-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="82551-112">HRESULT</span></span>|<span data-ttu-id="82551-113">描述</span><span class="sxs-lookup"><span data-stu-id="82551-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="82551-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="82551-114">S_OK</span></span>|<span data-ttu-id="82551-115">`SetConnectionTasks`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="82551-115">`SetConnectionTasks` returned successfully.</span></span>|  
|<span data-ttu-id="82551-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="82551-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="82551-117">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="82551-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="82551-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="82551-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="82551-119">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="82551-119">The call timed out.</span></span>|  
|<span data-ttu-id="82551-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="82551-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="82551-121">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="82551-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="82551-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="82551-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="82551-123">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="82551-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="82551-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="82551-124">E_FAIL</span></span>|<span data-ttu-id="82551-125">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="82551-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="82551-126">在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="82551-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="82551-127">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="82551-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="82551-128">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="82551-128">E_INVALIDARG</span></span>|<span data-ttu-id="82551-129">尚未使用此值`id`呼叫 [BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)，或`dwCount`或`id`為零，或的其中一個元素`ppCLRTask`為 null。</span><span class="sxs-lookup"><span data-stu-id="82551-129">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) has not been called using this value of `id`, or `dwCount` or `id` is zero, or one of the elements of `ppCLRTask` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82551-130">備註</span><span class="sxs-lookup"><span data-stu-id="82551-130">Remarks</span></span>  
 <span data-ttu-id="82551-131">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)提供三種方法`BeginConnection`： `SetConnectionTasks`、和[EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)，用來建立工作清單與識別碼和易記名稱的關聯。</span><span class="sxs-lookup"><span data-stu-id="82551-131">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, `SetConnectionTasks`, and [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="82551-132">這三種方法都必須以特定順序針對每一組工作進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="82551-132">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="82551-133">`BeginConnection`會先呼叫以建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="82551-133">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="82551-134">`SetConnectionTasks`接下來會呼叫，以提供與該連接相關聯的工作集合。</span><span class="sxs-lookup"><span data-stu-id="82551-134">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="82551-135">`EndConnection`最後會呼叫，以移除工作清單與識別碼和易記名稱之間的關聯。不過，可以嵌套不同連接的呼叫。</span><span class="sxs-lookup"><span data-stu-id="82551-135">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82551-136">需求</span><span class="sxs-lookup"><span data-stu-id="82551-136">Requirements</span></span>  
 <span data-ttu-id="82551-137">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="82551-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82551-138">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="82551-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="82551-139">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="82551-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="82551-140">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82551-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82551-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82551-141">See also</span></span>

- [<span data-ttu-id="82551-142">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="82551-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="82551-143">ICLRDebugManager 介面</span><span class="sxs-lookup"><span data-stu-id="82551-143">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="82551-144">BeginConnection 方法</span><span class="sxs-lookup"><span data-stu-id="82551-144">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="82551-145">EndConnection 方法</span><span class="sxs-lookup"><span data-stu-id="82551-145">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="82551-146">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="82551-146">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
