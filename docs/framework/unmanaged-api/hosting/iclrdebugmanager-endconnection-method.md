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
ms.openlocfilehash: 425f40da7a53aa4af1bd14964a8136add2f59f0b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135222"
---
# <a name="iclrdebugmanagerendconnection-method"></a><span data-ttu-id="80007-102">ICLRDebugManager::EndConnection 方法</span><span class="sxs-lookup"><span data-stu-id="80007-102">ICLRDebugManager::EndConnection Method</span></span>
<span data-ttu-id="80007-103">移除工作清單與識別碼和易記名稱之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="80007-103">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80007-104">語法</span><span class="sxs-lookup"><span data-stu-id="80007-104">Syntax</span></span>  
  
```cpp  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80007-105">參數</span><span class="sxs-lookup"><span data-stu-id="80007-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="80007-106">在連接的主機特定識別碼，以及 common language runtime （CLR）工作的相關聯清單。</span><span class="sxs-lookup"><span data-stu-id="80007-106">[in] The host-specific identifier for the connection and the associated list of common language runtime (CLR) tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80007-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="80007-107">Return Value</span></span>  
  
|<span data-ttu-id="80007-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="80007-108">HRESULT</span></span>|<span data-ttu-id="80007-109">描述</span><span class="sxs-lookup"><span data-stu-id="80007-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="80007-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="80007-110">S_OK</span></span>|<span data-ttu-id="80007-111">已成功傳回 `EndConnection`。</span><span class="sxs-lookup"><span data-stu-id="80007-111">`EndConnection` returned successfully.</span></span>|  
|<span data-ttu-id="80007-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="80007-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="80007-113">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="80007-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="80007-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="80007-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="80007-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="80007-115">The call timed out.</span></span>|  
|<span data-ttu-id="80007-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="80007-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="80007-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="80007-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="80007-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="80007-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="80007-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="80007-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="80007-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="80007-120">E_FAIL</span></span>|<span data-ttu-id="80007-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="80007-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="80007-122">在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="80007-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="80007-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="80007-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="80007-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="80007-124">E_INVALIDARG</span></span>|<span data-ttu-id="80007-125">從未使用 `dwConnectionId`呼叫[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) ，或 `dwConnectionId` 為零。</span><span class="sxs-lookup"><span data-stu-id="80007-125">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) was never called using `dwConnectionId`, or `dwConnectionId` was zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80007-126">備註</span><span class="sxs-lookup"><span data-stu-id="80007-126">Remarks</span></span>  
 <span data-ttu-id="80007-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)提供三種方法： `BeginConnection`、 [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)和 `EndConnection`，以便將工作清單與識別碼和易記名稱產生關聯。</span><span class="sxs-lookup"><span data-stu-id="80007-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and `EndConnection`, for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="80007-128">這三種方法都必須以特定順序針對每一組工作進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="80007-128">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="80007-129">首先會呼叫 `BeginConnection` 以建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="80007-129">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="80007-130">下一步會呼叫 `SetConnectionTasks`，以提供與該連接相關聯的工作集合。</span><span class="sxs-lookup"><span data-stu-id="80007-130">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="80007-131">最後會呼叫 `EndConnection`，以移除工作清單與識別碼和易記名稱之間的關聯。不過，可以嵌套不同連接的呼叫。</span><span class="sxs-lookup"><span data-stu-id="80007-131">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80007-132">需求</span><span class="sxs-lookup"><span data-stu-id="80007-132">Requirements</span></span>  
 <span data-ttu-id="80007-133">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="80007-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80007-134">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="80007-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="80007-135">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="80007-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80007-136">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80007-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80007-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="80007-137">See also</span></span>

- [<span data-ttu-id="80007-138">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="80007-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="80007-139">ICLRDebugManager 介面</span><span class="sxs-lookup"><span data-stu-id="80007-139">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="80007-140">BeginConnection 方法</span><span class="sxs-lookup"><span data-stu-id="80007-140">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="80007-141">SetConnectionTasks 方法</span><span class="sxs-lookup"><span data-stu-id="80007-141">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="80007-142">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="80007-142">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
