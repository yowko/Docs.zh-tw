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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37e663cbad902b5740a14b9fe60f24537d999aac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969437"
---
# <a name="iclrdebugmanagerbeginconnection-method"></a><span data-ttu-id="eb6d9-102">ICLRDebugManager::BeginConnection 方法</span><span class="sxs-lookup"><span data-stu-id="eb6d9-102">ICLRDebugManager::BeginConnection Method</span></span>
<span data-ttu-id="eb6d9-103">在主機與偵錯工具之間建立新的連接, 以將工作清單與識別碼和易記名稱產生關聯。</span><span class="sxs-lookup"><span data-stu-id="eb6d9-103">Establishes a new connection between the host and the debugger to associate a list of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb6d9-104">語法</span><span class="sxs-lookup"><span data-stu-id="eb6d9-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginConnection (  
    [in] CONNID dwConnectionId,  
    [in, string] wchar_t* szConnectionName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb6d9-105">參數</span><span class="sxs-lookup"><span data-stu-id="eb6d9-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="eb6d9-106">在要與 common language runtime (CLR) 工作清單建立關聯的識別碼。</span><span class="sxs-lookup"><span data-stu-id="eb6d9-106">[in] An identifier to associate with the list of common language runtime (CLR) tasks.</span></span>  
  
 `szConnectionName`  
 <span data-ttu-id="eb6d9-107">在要與 CLR 工作清單產生關聯的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="eb6d9-107">[in] A friendly name to associate with the list of CLR tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eb6d9-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="eb6d9-108">Return Value</span></span>  
  
|<span data-ttu-id="eb6d9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eb6d9-109">HRESULT</span></span>|<span data-ttu-id="eb6d9-110">描述</span><span class="sxs-lookup"><span data-stu-id="eb6d9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eb6d9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="eb6d9-111">S_OK</span></span>|<span data-ttu-id="eb6d9-112">`BeginConnection`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="eb6d9-112">`BeginConnection` returned successfully.</span></span>|  
|<span data-ttu-id="eb6d9-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="eb6d9-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="eb6d9-114">CLR 尚未載入進程中, 或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="eb6d9-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="eb6d9-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="eb6d9-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="eb6d9-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="eb6d9-116">The call timed out.</span></span>|  
|<span data-ttu-id="eb6d9-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="eb6d9-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="eb6d9-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="eb6d9-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="eb6d9-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="eb6d9-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="eb6d9-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="eb6d9-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="eb6d9-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="eb6d9-121">E_FAIL</span></span>|<span data-ttu-id="eb6d9-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="eb6d9-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="eb6d9-123">在方法傳回 E_FAIL 之後, CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="eb6d9-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="eb6d9-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="eb6d9-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="eb6d9-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="eb6d9-125">E_INVALIDARG</span></span>|<span data-ttu-id="eb6d9-126">`dwConnectionId`為零, 或`BeginConnection`已經使用此`dwConnectionId`值呼叫, 或`szConnectionName`為 null。</span><span class="sxs-lookup"><span data-stu-id="eb6d9-126">`dwConnectionId` was zero, or `BeginConnection` was already called using this `dwConnectionId` value, or `szConnectionName` was null.</span></span>|  
|<span data-ttu-id="eb6d9-127">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="eb6d9-127">E_OUTOFMEMORY</span></span>|<span data-ttu-id="eb6d9-128">無法配置足夠的記憶體來保存與此連接相關聯的工作清單。</span><span class="sxs-lookup"><span data-stu-id="eb6d9-128">Not enough memory could be allocated to hold the list of tasks associated with this connection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb6d9-129">備註</span><span class="sxs-lookup"><span data-stu-id="eb6d9-129">Remarks</span></span>  
 <span data-ttu-id="eb6d9-130">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)提供三種方法`BeginConnection`:、 [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)和[EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), 用於關聯工作清單與識別碼和易記名稱。</span><span class="sxs-lookup"><span data-stu-id="eb6d9-130">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="eb6d9-131">這三種方法都必須以特定順序針對每一組工作進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="eb6d9-131">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="eb6d9-132">`BeginConnection`會先呼叫以建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="eb6d9-132">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="eb6d9-133">`SetConnectionTasks`接下來會呼叫, 以提供與該連接相關聯的工作集合。</span><span class="sxs-lookup"><span data-stu-id="eb6d9-133">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="eb6d9-134">`EndConnection`最後會呼叫, 以移除工作清單與識別碼和易記名稱之間的關聯。不過, 可以嵌套不同連接的呼叫。</span><span class="sxs-lookup"><span data-stu-id="eb6d9-134">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb6d9-135">需求</span><span class="sxs-lookup"><span data-stu-id="eb6d9-135">Requirements</span></span>  
 <span data-ttu-id="eb6d9-136">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eb6d9-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb6d9-137">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="eb6d9-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eb6d9-138">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="eb6d9-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eb6d9-139">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb6d9-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb6d9-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb6d9-140">See also</span></span>

- [<span data-ttu-id="eb6d9-141">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="eb6d9-141">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="eb6d9-142">ICLRDebugManager 介面</span><span class="sxs-lookup"><span data-stu-id="eb6d9-142">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="eb6d9-143">EndConnection 方法</span><span class="sxs-lookup"><span data-stu-id="eb6d9-143">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="eb6d9-144">SetConnectionTasks 方法</span><span class="sxs-lookup"><span data-stu-id="eb6d9-144">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="eb6d9-145">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="eb6d9-145">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
