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
ms.openlocfilehash: d2af6970907eb9895750ca58065b2e0cb735cea8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969399"
---
# <a name="iclrdebugmanagerendconnection-method"></a><span data-ttu-id="37a52-102">ICLRDebugManager::EndConnection 方法</span><span class="sxs-lookup"><span data-stu-id="37a52-102">ICLRDebugManager::EndConnection Method</span></span>
<span data-ttu-id="37a52-103">移除工作清單與識別碼和易記名稱之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="37a52-103">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37a52-104">語法</span><span class="sxs-lookup"><span data-stu-id="37a52-104">Syntax</span></span>  
  
```cpp  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37a52-105">參數</span><span class="sxs-lookup"><span data-stu-id="37a52-105">Parameters</span></span>  
 `dwConnectionId`  
 <span data-ttu-id="37a52-106">在連接的主機特定識別碼, 以及 common language runtime (CLR) 工作的相關聯清單。</span><span class="sxs-lookup"><span data-stu-id="37a52-106">[in] The host-specific identifier for the connection and the associated list of common language runtime (CLR) tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37a52-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="37a52-107">Return Value</span></span>  
  
|<span data-ttu-id="37a52-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="37a52-108">HRESULT</span></span>|<span data-ttu-id="37a52-109">描述</span><span class="sxs-lookup"><span data-stu-id="37a52-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="37a52-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="37a52-110">S_OK</span></span>|<span data-ttu-id="37a52-111">`EndConnection`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="37a52-111">`EndConnection` returned successfully.</span></span>|  
|<span data-ttu-id="37a52-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="37a52-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="37a52-113">CLR 尚未載入進程中, 或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="37a52-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="37a52-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="37a52-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="37a52-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="37a52-115">The call timed out.</span></span>|  
|<span data-ttu-id="37a52-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="37a52-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="37a52-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="37a52-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="37a52-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="37a52-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="37a52-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="37a52-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="37a52-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="37a52-120">E_FAIL</span></span>|<span data-ttu-id="37a52-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="37a52-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="37a52-122">在方法傳回 E_FAIL 之後, CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="37a52-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="37a52-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="37a52-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="37a52-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="37a52-124">E_INVALIDARG</span></span>|<span data-ttu-id="37a52-125">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)從未使用`dwConnectionId`呼叫, 或`dwConnectionId`為零。</span><span class="sxs-lookup"><span data-stu-id="37a52-125">[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) was never called using `dwConnectionId`, or `dwConnectionId` was zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37a52-126">備註</span><span class="sxs-lookup"><span data-stu-id="37a52-126">Remarks</span></span>  
 <span data-ttu-id="37a52-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)提供三種方法`BeginConnection`:、 [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)和`EndConnection`, 用於關聯工作清單與識別碼和易記名稱。</span><span class="sxs-lookup"><span data-stu-id="37a52-127">[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), and `EndConnection`, for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="37a52-128">這三種方法都必須以特定順序針對每一組工作進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="37a52-128">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="37a52-129">`BeginConnection`會先呼叫以建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="37a52-129">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="37a52-130">`SetConnectionTasks`接下來會呼叫, 以提供與該連接相關聯的工作集合。</span><span class="sxs-lookup"><span data-stu-id="37a52-130">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="37a52-131">`EndConnection`最後會呼叫, 以移除工作清單與識別碼和易記名稱之間的關聯。不過, 可以嵌套不同連接的呼叫。</span><span class="sxs-lookup"><span data-stu-id="37a52-131">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37a52-132">需求</span><span class="sxs-lookup"><span data-stu-id="37a52-132">Requirements</span></span>  
 <span data-ttu-id="37a52-133">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="37a52-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37a52-134">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="37a52-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="37a52-135">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="37a52-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="37a52-136">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37a52-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37a52-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37a52-137">See also</span></span>

- [<span data-ttu-id="37a52-138">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="37a52-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="37a52-139">ICLRDebugManager 介面</span><span class="sxs-lookup"><span data-stu-id="37a52-139">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="37a52-140">BeginConnection 方法</span><span class="sxs-lookup"><span data-stu-id="37a52-140">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="37a52-141">SetConnectionTasks 方法</span><span class="sxs-lookup"><span data-stu-id="37a52-141">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="37a52-142">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="37a52-142">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
