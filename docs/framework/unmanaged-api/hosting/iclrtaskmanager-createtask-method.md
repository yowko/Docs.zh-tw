---
title: "ICLRTaskManager::CreateTask 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTaskManager.CreateTask
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTaskManager::CreateTask
helpviewer_keywords:
- ICLRTaskManager::CreateTask method [.NET Framework hosting]
- CreateTask method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: eea570d9-2e53-4320-9ea0-eb777bf9dcf3
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e9e78db6e43397709f913f8f79a617221f98db87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskmanagercreatetask-method"></a><span data-ttu-id="dfc0e-102">ICLRTaskManager::CreateTask 方法</span><span class="sxs-lookup"><span data-stu-id="dfc0e-102">ICLRTaskManager::CreateTask Method</span></span>
<span data-ttu-id="dfc0e-103">明確要求的 common language runtime (CLR) 建立新的工作。</span><span class="sxs-lookup"><span data-stu-id="dfc0e-103">Requests explicitly that the common language runtime (CLR) create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfc0e-104">語法</span><span class="sxs-lookup"><span data-stu-id="dfc0e-104">Syntax</span></span>  
  
```  
HRESULT CreateTask (  
    [out] ICLRTask **pTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dfc0e-105">參數</span><span class="sxs-lookup"><span data-stu-id="dfc0e-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="dfc0e-106">[out]指標，新建的位址[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)，則為 null，如果無法建立工作。</span><span class="sxs-lookup"><span data-stu-id="dfc0e-106">[out] A pointer to the address of a newly created [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md), or null, if the task could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dfc0e-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="dfc0e-107">Return Value</span></span>  
  
|<span data-ttu-id="dfc0e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dfc0e-108">HRESULT</span></span>|<span data-ttu-id="dfc0e-109">描述</span><span class="sxs-lookup"><span data-stu-id="dfc0e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dfc0e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="dfc0e-110">S_OK</span></span>|<span data-ttu-id="dfc0e-111">方法成功傳回。</span><span class="sxs-lookup"><span data-stu-id="dfc0e-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="dfc0e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dfc0e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dfc0e-113">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="dfc0e-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dfc0e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dfc0e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dfc0e-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="dfc0e-115">The call timed out.</span></span>|  
|<span data-ttu-id="dfc0e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dfc0e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dfc0e-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="dfc0e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dfc0e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dfc0e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dfc0e-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="dfc0e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dfc0e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dfc0e-120">E_FAIL</span></span>|<span data-ttu-id="dfc0e-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="dfc0e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dfc0e-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="dfc0e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dfc0e-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="dfc0e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="dfc0e-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="dfc0e-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="dfc0e-125">沒有足夠的記憶體可配置要求的資源。</span><span class="sxs-lookup"><span data-stu-id="dfc0e-125">Not enough memory is available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfc0e-126">備註</span><span class="sxs-lookup"><span data-stu-id="dfc0e-126">Remarks</span></span>  
 <span data-ttu-id="dfc0e-127">當使用者程式碼會建立一個執行緒使用中的型別時，CLR 會建立新的工作，自動啟動時，<xref:System.Threading>命名空間，或當執行緒集區的大小會增加。</span><span class="sxs-lookup"><span data-stu-id="dfc0e-127">The CLR creates a new task automatically upon initialization, when user code creates a thread by using types in the <xref:System.Threading> namespace, or when the size of the thread pool is increased.</span></span> <span data-ttu-id="dfc0e-128">Unmanaged 程式碼會呼叫 managed 函式時，它也會建立工作。</span><span class="sxs-lookup"><span data-stu-id="dfc0e-128">It also creates tasks when unmanaged code makes a call to a managed function.</span></span>  
  
 <span data-ttu-id="dfc0e-129">`CreateTask`可讓主應用程式發出明確的要求 CLR 建立新的工作。</span><span class="sxs-lookup"><span data-stu-id="dfc0e-129">`CreateTask` allows the host to make an explicit request that the CLR create a new task.</span></span> <span data-ttu-id="dfc0e-130">例如，主機可以叫用這個方法，以將其預先初始化資料結構。</span><span class="sxs-lookup"><span data-stu-id="dfc0e-130">For example, the host can invoke this method to preinitialize data structures.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="dfc0e-131">新的工作會傳回處於暫停狀態，並保持暫停狀態，直到主機明確呼叫[ihosttask:: Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)。</span><span class="sxs-lookup"><span data-stu-id="dfc0e-131">The new task is returned in a suspended state and remains suspended until the host explicitly calls [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfc0e-132">需求</span><span class="sxs-lookup"><span data-stu-id="dfc0e-132">Requirements</span></span>  
 <span data-ttu-id="dfc0e-133">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dfc0e-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfc0e-134">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dfc0e-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dfc0e-135">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="dfc0e-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dfc0e-136">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfc0e-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfc0e-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="dfc0e-137">See Also</span></span>  
 [<span data-ttu-id="dfc0e-138">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="dfc0e-138">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="dfc0e-139">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="dfc0e-139">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="dfc0e-140">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="dfc0e-140">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="dfc0e-141">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="dfc0e-141">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
