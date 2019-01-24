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
ms.openlocfilehash: 515eb0633c82c3e1386487d1866de79c9898c9cd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654603"
---
# <a name="iclrdebugmanager-interface"></a><span data-ttu-id="15a69-102">ICLRDebugManager 介面</span><span class="sxs-lookup"><span data-stu-id="15a69-102">ICLRDebugManager Interface</span></span>
<span data-ttu-id="15a69-103">提供方法，可讓主應用程式相關聯的一組工作識別碼和易記名稱。</span><span class="sxs-lookup"><span data-stu-id="15a69-103">Provides methods that allow a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="15a69-104">方法</span><span class="sxs-lookup"><span data-stu-id="15a69-104">Methods</span></span>  
  
|<span data-ttu-id="15a69-105">方法</span><span class="sxs-lookup"><span data-stu-id="15a69-105">Method</span></span>|<span data-ttu-id="15a69-106">描述</span><span class="sxs-lookup"><span data-stu-id="15a69-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="15a69-107">BeginConnection 方法</span><span class="sxs-lookup"><span data-stu-id="15a69-107">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|<span data-ttu-id="15a69-108">建立主應用程式與偵錯工具，將關聯工作識別碼和易記名稱之間的新連線。</span><span class="sxs-lookup"><span data-stu-id="15a69-108">Establishes a new connection between the host and the debugger to associate tasks with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="15a69-109">EndConnection 方法</span><span class="sxs-lookup"><span data-stu-id="15a69-109">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|<span data-ttu-id="15a69-110">移除工作清單和識別項和易記名稱之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="15a69-110">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="15a69-111">GetDacl 方法</span><span class="sxs-lookup"><span data-stu-id="15a69-111">GetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|<span data-ttu-id="15a69-112">這個方法尚未實作。</span><span class="sxs-lookup"><span data-stu-id="15a69-112">This method is not implemented.</span></span>|  
|[<span data-ttu-id="15a69-113">IsDebuggerAttached 方法</span><span class="sxs-lookup"><span data-stu-id="15a69-113">IsDebuggerAttached Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|<span data-ttu-id="15a69-114">取得值，表示偵錯工具是否附加至處理序。</span><span class="sxs-lookup"><span data-stu-id="15a69-114">Gets a value that indicates whether a debugger is attached to the process.</span></span>|  
|[<span data-ttu-id="15a69-115">SetConnectionTasks 方法</span><span class="sxs-lookup"><span data-stu-id="15a69-115">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|<span data-ttu-id="15a69-116">將一份[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)識別碼和易記名稱的執行個體。</span><span class="sxs-lookup"><span data-stu-id="15a69-116">Associates a list of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="15a69-117">SetDacl 方法</span><span class="sxs-lookup"><span data-stu-id="15a69-117">SetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|<span data-ttu-id="15a69-118">這個方法尚未實作。</span><span class="sxs-lookup"><span data-stu-id="15a69-118">This method is not implemented.</span></span>|  
|[<span data-ttu-id="15a69-119">SetSymbolReadingPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="15a69-119">SetSymbolReadingPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|<span data-ttu-id="15a69-120">設定用於讀取程式資料庫 (PDB) 檔案的原則。</span><span class="sxs-lookup"><span data-stu-id="15a69-120">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="15a69-121">原則會決定是否在呼叫堆疊中包含行號和檔案的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="15a69-121">The policy determines whether information about line numbers and files is included in call stacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15a69-122">備註</span><span class="sxs-lookup"><span data-stu-id="15a69-122">Remarks</span></span>  
 <span data-ttu-id="15a69-123">在偵錯案例中，主機可能會想要根據自己的程式設計邏輯的群組工作。</span><span class="sxs-lookup"><span data-stu-id="15a69-123">In debugging scenarios, a host might want to group tasks according to its own programming logic.</span></span> <span data-ttu-id="15a69-124">例如，群組可讓開發人員若要查看只將開發人員的 Api，而不是看到處理序中執行的每項工作所需的工作。</span><span class="sxs-lookup"><span data-stu-id="15a69-124">For example, a grouping would allow a developer to see only the tasks required by the developer's APIs, instead of seeing every task running in the process.</span></span> <span data-ttu-id="15a69-125">`ICLRDebugManager` 可讓主應用程式實作此類型的群組。</span><span class="sxs-lookup"><span data-stu-id="15a69-125">`ICLRDebugManager` allows the host to implement this kind of grouping.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="15a69-126">三個`ICLRDebugManager`方法， `BeginConnection`，`SetConnectionTasks`和`EndConnection`，依存於彼此。</span><span class="sxs-lookup"><span data-stu-id="15a69-126">Three `ICLRDebugManager` methods, `BeginConnection`, `SetConnectionTasks` and `EndConnection`, are dependent upon each other.</span></span> <span data-ttu-id="15a69-127">在指定的順序，如預期般運作，必須呼叫它們。</span><span class="sxs-lookup"><span data-stu-id="15a69-127">They must be called in the given order to work as expected.</span></span>  
  
 <span data-ttu-id="15a69-128">群組，以及識別碼和主應用程式會將指派給群組的易記名稱已對 common language runtime (CLR) 而言沒有意義。</span><span class="sxs-lookup"><span data-stu-id="15a69-128">The grouping, and the identifiers and friendly names that the host assigns to the grouping, have no meaning for the common language runtime (CLR).</span></span> <span data-ttu-id="15a69-129">只是，CLR 會將資訊傳遞給偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="15a69-129">The CLR merely passes the information along to the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15a69-130">需求</span><span class="sxs-lookup"><span data-stu-id="15a69-130">Requirements</span></span>  
 <span data-ttu-id="15a69-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="15a69-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15a69-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="15a69-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="15a69-133">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="15a69-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="15a69-134">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15a69-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15a69-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15a69-135">See also</span></span>
- [<span data-ttu-id="15a69-136">裝載介面</span><span class="sxs-lookup"><span data-stu-id="15a69-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
