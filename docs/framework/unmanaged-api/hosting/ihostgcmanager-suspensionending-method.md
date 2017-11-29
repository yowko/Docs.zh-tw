---
title: "IHostGCManager::SuspensionEnding 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostGCManager.SuspensionEnding
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostGCManager::SuspensionEnding
helpviewer_keywords:
- SuspensionEnding method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionEnding method [.NET Framework hosting]
ms.assetid: 8849a1db-17f0-44b7-880a-bd36d431eb91
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9952e62d4979efa0d07b19f183ca71adcc643365
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ihostgcmanagersuspensionending-method"></a><span data-ttu-id="93116-102">IHostGCManager::SuspensionEnding 方法</span><span class="sxs-lookup"><span data-stu-id="93116-102">IHostGCManager::SuspensionEnding Method</span></span>
<span data-ttu-id="93116-103">通知主機 common language runtime (CLR) 正在繼續執行的工作已暫止記憶體回收的執行緒上執行。</span><span class="sxs-lookup"><span data-stu-id="93116-103">Notifies the host that the common language runtime (CLR) is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93116-104">語法</span><span class="sxs-lookup"><span data-stu-id="93116-104">Syntax</span></span>  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="93116-105">參數</span><span class="sxs-lookup"><span data-stu-id="93116-105">Parameters</span></span>  
 `generation`  
 <span data-ttu-id="93116-106">[in]剛完成，記憶體回收集合產生的執行緒正在繼續。</span><span class="sxs-lookup"><span data-stu-id="93116-106">[in] The garbage collection generation that is just finishing, from which the thread is resuming.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="93116-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="93116-107">Return Value</span></span>  
  
|<span data-ttu-id="93116-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="93116-108">HRESULT</span></span>|<span data-ttu-id="93116-109">描述</span><span class="sxs-lookup"><span data-stu-id="93116-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="93116-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="93116-110">S_OK</span></span>|<span data-ttu-id="93116-111">`SuspensionEnding`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="93116-111">`SuspensionEnding` returned successfully.</span></span>|  
|<span data-ttu-id="93116-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="93116-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="93116-113">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="93116-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="93116-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="93116-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="93116-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="93116-115">The call timed out.</span></span>|  
|<span data-ttu-id="93116-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="93116-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="93116-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="93116-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="93116-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="93116-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="93116-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="93116-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="93116-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="93116-120">E_FAIL</span></span>|<span data-ttu-id="93116-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="93116-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="93116-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="93116-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="93116-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="93116-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93116-124">備註</span><span class="sxs-lookup"><span data-stu-id="93116-124">Remarks</span></span>  
 <span data-ttu-id="93116-125">CLR 會呼叫`SuspensionEnding`之後執行記憶體回收，以通知主機在執行緒正在繼續執行。</span><span class="sxs-lookup"><span data-stu-id="93116-125">The CLR calls `SuspensionEnding` after it performs a garbage collection, to inform the host that the thread is resuming execution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="93116-126">請勿重新排程從發出方法呼叫的執行緒。</span><span class="sxs-lookup"><span data-stu-id="93116-126">Do not reschedule the thread the method call was made from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93116-127">需求</span><span class="sxs-lookup"><span data-stu-id="93116-127">Requirements</span></span>  
 <span data-ttu-id="93116-128">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="93116-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93116-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="93116-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="93116-130">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="93116-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93116-131">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93116-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93116-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93116-132">See Also</span></span>  
 [<span data-ttu-id="93116-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="93116-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="93116-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="93116-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="93116-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="93116-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="93116-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="93116-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="93116-137">IHostGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="93116-137">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
