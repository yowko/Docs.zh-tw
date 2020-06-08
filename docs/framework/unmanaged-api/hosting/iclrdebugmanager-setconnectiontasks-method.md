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
ms.openlocfilehash: f63b761497b3e9a19a9b939b45acf60d5a7d37b0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504234"
---
# <a name="iclrdebugmanagersetconnectiontasks-method"></a><span data-ttu-id="e6b1a-102">ICLRDebugManager::SetConnectionTasks 方法</span><span class="sxs-lookup"><span data-stu-id="e6b1a-102">ICLRDebugManager::SetConnectionTasks Method</span></span>
<span data-ttu-id="e6b1a-103">將[ICLRTask](iclrtask-interface.md)實例的清單與識別碼和易記名稱產生關聯。</span><span class="sxs-lookup"><span data-stu-id="e6b1a-103">Associates a list of [ICLRTask](iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6b1a-104">語法</span><span class="sxs-lookup"><span data-stu-id="e6b1a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetConnectionTasks (  
    [in] CONNID id,  
    [in] DWORD dwCount,  
    [in, size_is(dwCount)] ICLRTask **ppCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6b1a-105">參數</span><span class="sxs-lookup"><span data-stu-id="e6b1a-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="e6b1a-106">在與陣列相關聯之連接的主機特定識別碼 `ppCLRTask` 。</span><span class="sxs-lookup"><span data-stu-id="e6b1a-106">[in] The host-specific identifier for the connection with which to associate the `ppCLRTask` array.</span></span>  
  
 `dwCount`  
 <span data-ttu-id="e6b1a-107">在的成員數目 `ppCLRTask` 。</span><span class="sxs-lookup"><span data-stu-id="e6b1a-107">[in] The number of members of `ppCLRTask`.</span></span> <span data-ttu-id="e6b1a-108">這個數位必須大於零。</span><span class="sxs-lookup"><span data-stu-id="e6b1a-108">This number must be greater than zero.</span></span>  
  
 `ppCLRTask`  
 <span data-ttu-id="e6b1a-109">在`ICLRTask`要與所識別之連接產生關聯的指標陣列 `id` 。</span><span class="sxs-lookup"><span data-stu-id="e6b1a-109">[in] An array of `ICLRTask` pointers to associate with the connection identified by `id`.</span></span> <span data-ttu-id="e6b1a-110">此陣列至少必須包含一個成員。</span><span class="sxs-lookup"><span data-stu-id="e6b1a-110">This array must contain at least one member.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6b1a-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="e6b1a-111">Return Value</span></span>  
  
|<span data-ttu-id="e6b1a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e6b1a-112">HRESULT</span></span>|<span data-ttu-id="e6b1a-113">說明</span><span class="sxs-lookup"><span data-stu-id="e6b1a-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e6b1a-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="e6b1a-114">S_OK</span></span>|<span data-ttu-id="e6b1a-115">`SetConnectionTasks`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="e6b1a-115">`SetConnectionTasks` returned successfully.</span></span>|  
|<span data-ttu-id="e6b1a-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e6b1a-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e6b1a-117">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="e6b1a-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e6b1a-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e6b1a-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e6b1a-119">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="e6b1a-119">The call timed out.</span></span>|  
|<span data-ttu-id="e6b1a-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e6b1a-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e6b1a-121">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="e6b1a-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e6b1a-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e6b1a-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e6b1a-123">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="e6b1a-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e6b1a-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e6b1a-124">E_FAIL</span></span>|<span data-ttu-id="e6b1a-125">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="e6b1a-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e6b1a-126">在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="e6b1a-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e6b1a-127">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="e6b1a-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e6b1a-128">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e6b1a-128">E_INVALIDARG</span></span>|<span data-ttu-id="e6b1a-129">尚未使用此值呼叫[BeginConnection](iclrdebugmanager-beginconnection-method.md) `id` ，或 `dwCount` 或 `id` 為零，或的其中一個元素 `ppCLRTask` 為 null。</span><span class="sxs-lookup"><span data-stu-id="e6b1a-129">[BeginConnection](iclrdebugmanager-beginconnection-method.md) has not been called using this value of `id`, or `dwCount` or `id` is zero, or one of the elements of `ppCLRTask` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6b1a-130">備註</span><span class="sxs-lookup"><span data-stu-id="e6b1a-130">Remarks</span></span>  
 <span data-ttu-id="e6b1a-131">[ICLRDebugManager](iclrdebugmanager-interface.md)提供三種方法： `BeginConnection` 、 `SetConnectionTasks` 和[EndConnection](iclrdebugmanager-endconnection-method.md)，用來建立工作清單與識別碼和易記名稱的關聯。</span><span class="sxs-lookup"><span data-stu-id="e6b1a-131">[ICLRDebugManager](iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, `SetConnectionTasks`, and [EndConnection](iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e6b1a-132">這三種方法都必須以特定順序針對每一組工作進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="e6b1a-132">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="e6b1a-133">`BeginConnection`會先呼叫以建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="e6b1a-133">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="e6b1a-134">`SetConnectionTasks`接下來會呼叫，以提供與該連接相關聯的工作集合。</span><span class="sxs-lookup"><span data-stu-id="e6b1a-134">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="e6b1a-135">`EndConnection`最後會呼叫，以移除工作清單與識別碼和易記名稱之間的關聯。不過，可以嵌套不同連接的呼叫。</span><span class="sxs-lookup"><span data-stu-id="e6b1a-135">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6b1a-136">規格需求</span><span class="sxs-lookup"><span data-stu-id="e6b1a-136">Requirements</span></span>  
 <span data-ttu-id="e6b1a-137">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e6b1a-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6b1a-138">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="e6b1a-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e6b1a-139">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e6b1a-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e6b1a-140">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6b1a-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6b1a-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6b1a-141">See also</span></span>

- [<span data-ttu-id="e6b1a-142">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="e6b1a-142">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="e6b1a-143">ICLRDebugManager 介面</span><span class="sxs-lookup"><span data-stu-id="e6b1a-143">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="e6b1a-144">BeginConnection 方法</span><span class="sxs-lookup"><span data-stu-id="e6b1a-144">BeginConnection Method</span></span>](iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="e6b1a-145">EndConnection 方法</span><span class="sxs-lookup"><span data-stu-id="e6b1a-145">EndConnection Method</span></span>](iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="e6b1a-146">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="e6b1a-146">IHostControl Interface</span></span>](ihostcontrol-interface.md)
