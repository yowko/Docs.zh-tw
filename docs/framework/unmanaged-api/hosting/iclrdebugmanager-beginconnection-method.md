---
title: ICLRDebugManager::BeginConnection 方法
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.BeginConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::BeginConnection
helpviewer_keywords:
- ICLRDebugManager::BeginConnection method [.NET Framework hosting]
- BeginConnection method [.NET Framework hosting]
ms.assetid: bdd98146-ff4d-4150-a264-a4c1a32d31f3
topic_type:
- apiref
ms.openlocfilehash: fc25e250938d7549c7a9693bee937d4756268b93
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615809"
---
# <a name="iclrdebugmanagerbeginconnection-method"></a><span data-ttu-id="8f5f4-102">ICLRDebugManager::BeginConnection 方法</span><span class="sxs-lookup"><span data-stu-id="8f5f4-102">ICLRDebugManager::BeginConnection Method</span></span>
<span data-ttu-id="8f5f4-103">在主機與偵錯工具之間建立新的連接，以將工作清單與識別碼和易記名稱產生關聯。</span><span class="sxs-lookup"><span data-stu-id="8f5f4-103">Establishes a new connection between the host and the debugger to associate a list of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f5f4-104">語法</span><span class="sxs-lookup"><span data-stu-id="8f5f4-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginConnection (  
    [in] CONNID dwConnectionId,  
    [in, string] wchar_t* szConnectionName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f5f4-105">參數</span><span class="sxs-lookup"><span data-stu-id="8f5f4-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="8f5f4-106">在要與 common language runtime （CLR）工作清單建立關聯的識別碼。</span><span class="sxs-lookup"><span data-stu-id="8f5f4-106">[in] An identifier to associate with the list of common language runtime (CLR) tasks.</span></span>  
  
 `szConnectionName`  
 <span data-ttu-id="8f5f4-107">在要與 CLR 工作清單產生關聯的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="8f5f4-107">[in] A friendly name to associate with the list of CLR tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f5f4-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="8f5f4-108">Return Value</span></span>  
  
|<span data-ttu-id="8f5f4-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8f5f4-109">HRESULT</span></span>|<span data-ttu-id="8f5f4-110">說明</span><span class="sxs-lookup"><span data-stu-id="8f5f4-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8f5f4-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8f5f4-111">S_OK</span></span>|<span data-ttu-id="8f5f4-112">`BeginConnection`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="8f5f4-112">`BeginConnection` returned successfully.</span></span>|  
|<span data-ttu-id="8f5f4-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8f5f4-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8f5f4-114">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="8f5f4-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8f5f4-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8f5f4-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8f5f4-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="8f5f4-116">The call timed out.</span></span>|  
|<span data-ttu-id="8f5f4-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8f5f4-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8f5f4-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="8f5f4-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8f5f4-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8f5f4-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8f5f4-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="8f5f4-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8f5f4-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8f5f4-121">E_FAIL</span></span>|<span data-ttu-id="8f5f4-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="8f5f4-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8f5f4-123">在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="8f5f4-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8f5f4-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="8f5f4-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8f5f4-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8f5f4-125">E_INVALIDARG</span></span>|<span data-ttu-id="8f5f4-126">`dwConnectionId`為零，或 `BeginConnection` 已經使用此值呼叫 `dwConnectionId` ，或為 `szConnectionName` null。</span><span class="sxs-lookup"><span data-stu-id="8f5f4-126">`dwConnectionId` was zero, or `BeginConnection` was already called using this `dwConnectionId` value, or `szConnectionName` was null.</span></span>|  
|<span data-ttu-id="8f5f4-127">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="8f5f4-127">E_OUTOFMEMORY</span></span>|<span data-ttu-id="8f5f4-128">無法配置足夠的記憶體來保存與此連接相關聯的工作清單。</span><span class="sxs-lookup"><span data-stu-id="8f5f4-128">Not enough memory could be allocated to hold the list of tasks associated with this connection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f5f4-129">備註</span><span class="sxs-lookup"><span data-stu-id="8f5f4-129">Remarks</span></span>  
 <span data-ttu-id="8f5f4-130">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)提供三種方法： `BeginConnection` 、 [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)和[EndConnection](iclrdebugmanager-endconnection-method.md)，用於關聯工作清單與識別碼和易記名稱。</span><span class="sxs-lookup"><span data-stu-id="8f5f4-130">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and [EndConnection](iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8f5f4-131">這三種方法都必須以特定順序針對每一組工作進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="8f5f4-131">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="8f5f4-132">`BeginConnection`會先呼叫以建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="8f5f4-132">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="8f5f4-133">`SetConnectionTasks`接下來會呼叫，以提供與該連接相關聯的工作集合。</span><span class="sxs-lookup"><span data-stu-id="8f5f4-133">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="8f5f4-134">`EndConnection`最後會呼叫，以移除工作清單與識別碼和易記名稱之間的關聯。不過，可以嵌套不同連接的呼叫。</span><span class="sxs-lookup"><span data-stu-id="8f5f4-134">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f5f4-135">需求</span><span class="sxs-lookup"><span data-stu-id="8f5f4-135">Requirements</span></span>  
 <span data-ttu-id="8f5f4-136">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8f5f4-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f5f4-137">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="8f5f4-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8f5f4-138">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8f5f4-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8f5f4-139">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f5f4-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f5f4-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f5f4-140">See also</span></span>

- [<span data-ttu-id="8f5f4-141">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="8f5f4-141">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="8f5f4-142">ICLRDebugManager 介面</span><span class="sxs-lookup"><span data-stu-id="8f5f4-142">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="8f5f4-143">EndConnection 方法</span><span class="sxs-lookup"><span data-stu-id="8f5f4-143">EndConnection Method</span></span>](iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="8f5f4-144">SetConnectionTasks 方法</span><span class="sxs-lookup"><span data-stu-id="8f5f4-144">SetConnectionTasks Method</span></span>](iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="8f5f4-145">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="8f5f4-145">IHostControl Interface</span></span>](ihostcontrol-interface.md)
