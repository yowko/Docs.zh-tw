---
title: ICLRTaskManager::CreateTask 方法
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::CreateTask
helpviewer_keywords:
- ICLRTaskManager::CreateTask method [.NET Framework hosting]
- CreateTask method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: eea570d9-2e53-4320-9ea0-eb777bf9dcf3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a89ea76d78431ae8833602588379d5150e473710
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938311"
---
# <a name="iclrtaskmanagercreatetask-method"></a><span data-ttu-id="94050-102">ICLRTaskManager::CreateTask 方法</span><span class="sxs-lookup"><span data-stu-id="94050-102">ICLRTaskManager::CreateTask Method</span></span>
<span data-ttu-id="94050-103">明確要求 common language runtime (CLR) 建立新的工作。</span><span class="sxs-lookup"><span data-stu-id="94050-103">Requests explicitly that the common language runtime (CLR) create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94050-104">語法</span><span class="sxs-lookup"><span data-stu-id="94050-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateTask (  
    [out] ICLRTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94050-105">參數</span><span class="sxs-lookup"><span data-stu-id="94050-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="94050-106">脫銷新建立之[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)的位址指標, 如果無法建立工作, 則為 null。</span><span class="sxs-lookup"><span data-stu-id="94050-106">[out] A pointer to the address of a newly created [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md), or null, if the task could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94050-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="94050-107">Return Value</span></span>  
  
|<span data-ttu-id="94050-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="94050-108">HRESULT</span></span>|<span data-ttu-id="94050-109">描述</span><span class="sxs-lookup"><span data-stu-id="94050-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="94050-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="94050-110">S_OK</span></span>|<span data-ttu-id="94050-111">已成功傳回方法。</span><span class="sxs-lookup"><span data-stu-id="94050-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="94050-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="94050-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="94050-113">CLR 尚未載入進程中, 或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="94050-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="94050-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="94050-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="94050-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="94050-115">The call timed out.</span></span>|  
|<span data-ttu-id="94050-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="94050-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="94050-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="94050-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="94050-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="94050-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="94050-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="94050-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="94050-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="94050-120">E_FAIL</span></span>|<span data-ttu-id="94050-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="94050-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="94050-122">當方法傳回 E_FAIL 時, CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="94050-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="94050-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="94050-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="94050-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="94050-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="94050-125">沒有足夠的記憶體可用來配置要求的資源。</span><span class="sxs-lookup"><span data-stu-id="94050-125">Not enough memory is available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94050-126">備註</span><span class="sxs-lookup"><span data-stu-id="94050-126">Remarks</span></span>  
 <span data-ttu-id="94050-127">當使用者程式碼使用命名空間中的<xref:System.Threading>類型建立執行緒, 或增加執行緒集區的大小時, CLR 會在初始化時自動建立新的工作。</span><span class="sxs-lookup"><span data-stu-id="94050-127">The CLR creates a new task automatically upon initialization, when user code creates a thread by using types in the <xref:System.Threading> namespace, or when the size of the thread pool is increased.</span></span> <span data-ttu-id="94050-128">它也會在未受管理的程式碼對 managed 函式進行呼叫時, 建立工作。</span><span class="sxs-lookup"><span data-stu-id="94050-128">It also creates tasks when unmanaged code makes a call to a managed function.</span></span>  
  
 <span data-ttu-id="94050-129">`CreateTask`允許主機提出 CLR 建立新工作的明確要求。</span><span class="sxs-lookup"><span data-stu-id="94050-129">`CreateTask` allows the host to make an explicit request that the CLR create a new task.</span></span> <span data-ttu-id="94050-130">例如, 主機可以叫用這個方法來 preinitialize 資料結構。</span><span class="sxs-lookup"><span data-stu-id="94050-130">For example, the host can invoke this method to preinitialize data structures.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="94050-131">新工作會以暫停狀態傳回, 而且會一直暫停, 直到主機明確呼叫[IHostTask:: Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)為止。</span><span class="sxs-lookup"><span data-stu-id="94050-131">The new task is returned in a suspended state and remains suspended until the host explicitly calls [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94050-132">需求</span><span class="sxs-lookup"><span data-stu-id="94050-132">Requirements</span></span>  
 <span data-ttu-id="94050-133">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="94050-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94050-134">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="94050-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="94050-135">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="94050-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="94050-136">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94050-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94050-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94050-137">See also</span></span>

- [<span data-ttu-id="94050-138">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="94050-138">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="94050-139">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="94050-139">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="94050-140">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="94050-140">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="94050-141">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="94050-141">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
