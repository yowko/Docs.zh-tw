---
title: "ICLRTaskManager::GetCurrentTask 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTaskManager.GetCurrentTask
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: c0b82a9f-edc6-4878-9c81-48de53c02142
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1adf2959beb8687dc3d08ceb7a118bb19a5fa68d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskmanagergetcurrenttask-method"></a><span data-ttu-id="d9e33-102">ICLRTaskManager::GetCurrentTask 方法</span><span class="sxs-lookup"><span data-stu-id="d9e33-102">ICLRTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="d9e33-103">取得[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)方法呼叫所起始的作業系統執行緒目前正在執行的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d9e33-103">Gets the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance that is currently running on the operating system thread from which the method call originated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9e33-104">語法</span><span class="sxs-lookup"><span data-stu-id="d9e33-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTask (  
    [out] ICLRTask **ppTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d9e33-105">參數</span><span class="sxs-lookup"><span data-stu-id="d9e33-105">Parameters</span></span>  
 `ppTask`  
 <span data-ttu-id="d9e33-106">[out]位址指標`ICLRTask`作業系統執行緒的呼叫來源，目前正在執行的執行個體或 null，如果沒有工作正在執行此執行緒上。</span><span class="sxs-lookup"><span data-stu-id="d9e33-106">[out] A pointer to the address of an `ICLRTask` instance that is currently executing on the operating system thread from which the call originated, or null if no task is currently executing on this thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9e33-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="d9e33-107">Return Value</span></span>  
  
|<span data-ttu-id="d9e33-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d9e33-108">HRESULT</span></span>|<span data-ttu-id="d9e33-109">描述</span><span class="sxs-lookup"><span data-stu-id="d9e33-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d9e33-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d9e33-110">S_OK</span></span>|<span data-ttu-id="d9e33-111">方法成功傳回。</span><span class="sxs-lookup"><span data-stu-id="d9e33-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="d9e33-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d9e33-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d9e33-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="d9e33-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d9e33-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d9e33-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d9e33-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="d9e33-115">The call timed out.</span></span>|  
|<span data-ttu-id="d9e33-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d9e33-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d9e33-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="d9e33-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d9e33-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d9e33-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d9e33-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="d9e33-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d9e33-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d9e33-120">E_FAIL</span></span>|<span data-ttu-id="d9e33-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="d9e33-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d9e33-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="d9e33-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d9e33-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d9e33-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9e33-124">備註</span><span class="sxs-lookup"><span data-stu-id="d9e33-124">Remarks</span></span>  
 <span data-ttu-id="d9e33-125">`ICLRTask`執行個體`ppTask`參數指向代表目前執行之工作的 CLR。</span><span class="sxs-lookup"><span data-stu-id="d9e33-125">The `ICLRTask` instance that the `ppTask` parameter points to represents the currently executing task for the CLR.</span></span> <span data-ttu-id="d9e33-126">`ICLRTask`執行個體都與對應[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)主機中代表工作的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d9e33-126">The `ICLRTask` instance is associated with a corresponding [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the task for the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9e33-127">需求</span><span class="sxs-lookup"><span data-stu-id="d9e33-127">Requirements</span></span>  
 <span data-ttu-id="d9e33-128">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d9e33-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9e33-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d9e33-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d9e33-130">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d9e33-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9e33-131">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9e33-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9e33-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9e33-132">See Also</span></span>  
 [<span data-ttu-id="d9e33-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="d9e33-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="d9e33-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="d9e33-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="d9e33-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="d9e33-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="d9e33-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="d9e33-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
