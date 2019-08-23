---
title: ICLRDebugManager 介面
ms.date: 03/30/2017
api_name:
- ICLRDebugManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager
helpviewer_keywords:
- ICLRDebugManager interface [.NET Framework hosting]
ms.assetid: e835062c-c7d6-4945-8a44-2de7ebf3928e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a408995793caf879f8d5624ab727102c4859195
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959617"
---
# <a name="iclrdebugmanager-interface"></a><span data-ttu-id="f9d00-102">ICLRDebugManager 介面</span><span class="sxs-lookup"><span data-stu-id="f9d00-102">ICLRDebugManager Interface</span></span>
<span data-ttu-id="f9d00-103">提供可讓主機將一組工作與識別碼和易記名稱建立關聯的方法。</span><span class="sxs-lookup"><span data-stu-id="f9d00-103">Provides methods that allow a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f9d00-104">方法</span><span class="sxs-lookup"><span data-stu-id="f9d00-104">Methods</span></span>  
  
|<span data-ttu-id="f9d00-105">方法</span><span class="sxs-lookup"><span data-stu-id="f9d00-105">Method</span></span>|<span data-ttu-id="f9d00-106">說明</span><span class="sxs-lookup"><span data-stu-id="f9d00-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f9d00-107">BeginConnection 方法</span><span class="sxs-lookup"><span data-stu-id="f9d00-107">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|<span data-ttu-id="f9d00-108">在主機與偵錯工具之間建立新的連接, 以將工作與識別碼和易記名稱產生關聯。</span><span class="sxs-lookup"><span data-stu-id="f9d00-108">Establishes a new connection between the host and the debugger to associate tasks with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="f9d00-109">EndConnection 方法</span><span class="sxs-lookup"><span data-stu-id="f9d00-109">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|<span data-ttu-id="f9d00-110">移除工作清單與識別碼和易記名稱之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="f9d00-110">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="f9d00-111">GetDacl 方法</span><span class="sxs-lookup"><span data-stu-id="f9d00-111">GetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|<span data-ttu-id="f9d00-112">這個方法尚未實作。</span><span class="sxs-lookup"><span data-stu-id="f9d00-112">This method is not implemented.</span></span>|  
|[<span data-ttu-id="f9d00-113">IsDebuggerAttached 方法</span><span class="sxs-lookup"><span data-stu-id="f9d00-113">IsDebuggerAttached Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|<span data-ttu-id="f9d00-114">取得值，表示偵錯工具是否附加至處理序。</span><span class="sxs-lookup"><span data-stu-id="f9d00-114">Gets a value that indicates whether a debugger is attached to the process.</span></span>|  
|[<span data-ttu-id="f9d00-115">SetConnectionTasks 方法</span><span class="sxs-lookup"><span data-stu-id="f9d00-115">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|<span data-ttu-id="f9d00-116">將[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)實例的清單與識別碼和易記名稱產生關聯。</span><span class="sxs-lookup"><span data-stu-id="f9d00-116">Associates a list of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="f9d00-117">SetDacl 方法</span><span class="sxs-lookup"><span data-stu-id="f9d00-117">SetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|<span data-ttu-id="f9d00-118">這個方法尚未實作。</span><span class="sxs-lookup"><span data-stu-id="f9d00-118">This method is not implemented.</span></span>|  
|[<span data-ttu-id="f9d00-119">SetSymbolReadingPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="f9d00-119">SetSymbolReadingPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|<span data-ttu-id="f9d00-120">設定用於讀取程式資料庫 (PDB) 檔案的原則。</span><span class="sxs-lookup"><span data-stu-id="f9d00-120">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="f9d00-121">此原則會決定行號和檔案的相關資訊是否包含在呼叫堆疊中。</span><span class="sxs-lookup"><span data-stu-id="f9d00-121">The policy determines whether information about line numbers and files is included in call stacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9d00-122">備註</span><span class="sxs-lookup"><span data-stu-id="f9d00-122">Remarks</span></span>  
 <span data-ttu-id="f9d00-123">在偵錯工具案例中, 主機可能會想要根據工作的程式設計邏輯來分組工作。</span><span class="sxs-lookup"><span data-stu-id="f9d00-123">In debugging scenarios, a host might want to group tasks according to its own programming logic.</span></span> <span data-ttu-id="f9d00-124">例如, 群組可讓開發人員只查看開發人員的 Api 所需的工作, 而不會看到在進程中執行的每個工作。</span><span class="sxs-lookup"><span data-stu-id="f9d00-124">For example, a grouping would allow a developer to see only the tasks required by the developer's APIs, instead of seeing every task running in the process.</span></span> <span data-ttu-id="f9d00-125">`ICLRDebugManager`允許主機執行這種群組。</span><span class="sxs-lookup"><span data-stu-id="f9d00-125">`ICLRDebugManager` allows the host to implement this kind of grouping.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f9d00-126">有`ICLRDebugManager`三種`BeginConnection`方法`SetConnectionTasks` ,和`EndConnection`彼此相依。</span><span class="sxs-lookup"><span data-stu-id="f9d00-126">Three `ICLRDebugManager` methods, `BeginConnection`, `SetConnectionTasks` and `EndConnection`, are dependent upon each other.</span></span> <span data-ttu-id="f9d00-127">您必須在指定的順序中呼叫它們, 才能如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="f9d00-127">They must be called in the given order to work as expected.</span></span>  
  
 <span data-ttu-id="f9d00-128">群組以及主機指派給群組的識別碼和易記名稱, 對 common language runtime (CLR) 沒有任何意義。</span><span class="sxs-lookup"><span data-stu-id="f9d00-128">The grouping, and the identifiers and friendly names that the host assigns to the grouping, have no meaning for the common language runtime (CLR).</span></span> <span data-ttu-id="f9d00-129">CLR 只會將資訊傳遞給偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="f9d00-129">The CLR merely passes the information along to the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9d00-130">需求</span><span class="sxs-lookup"><span data-stu-id="f9d00-130">Requirements</span></span>  
 <span data-ttu-id="f9d00-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f9d00-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9d00-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f9d00-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f9d00-133">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f9d00-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f9d00-134">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9d00-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9d00-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9d00-135">See also</span></span>

- [<span data-ttu-id="f9d00-136">裝載介面</span><span class="sxs-lookup"><span data-stu-id="f9d00-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
