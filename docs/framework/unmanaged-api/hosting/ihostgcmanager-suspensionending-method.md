---
title: "IHostGCManager::SuspensionEnding 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostGCManager.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::SuspensionEnding
helpviewer_keywords:
- SuspensionEnding method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionEnding method [.NET Framework hosting]
ms.assetid: 8849a1db-17f0-44b7-880a-bd36d431eb91
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b9660a0aa755e297721679bcf6db798384f12abd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostgcmanagersuspensionending-method"></a><span data-ttu-id="20045-102">IHostGCManager::SuspensionEnding 方法</span><span class="sxs-lookup"><span data-stu-id="20045-102">IHostGCManager::SuspensionEnding Method</span></span>
<span data-ttu-id="20045-103">通知主機 common language runtime (CLR) 正在繼續執行的工作已暫止記憶體回收的執行緒上執行。</span><span class="sxs-lookup"><span data-stu-id="20045-103">Notifies the host that the common language runtime (CLR) is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20045-104">語法</span><span class="sxs-lookup"><span data-stu-id="20045-104">Syntax</span></span>  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20045-105">參數</span><span class="sxs-lookup"><span data-stu-id="20045-105">Parameters</span></span>  
 `generation`  
 <span data-ttu-id="20045-106">[in]剛完成，記憶體回收集合產生的執行緒正在繼續。</span><span class="sxs-lookup"><span data-stu-id="20045-106">[in] The garbage collection generation that is just finishing, from which the thread is resuming.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20045-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="20045-107">Return Value</span></span>  
  
|<span data-ttu-id="20045-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="20045-108">HRESULT</span></span>|<span data-ttu-id="20045-109">描述</span><span class="sxs-lookup"><span data-stu-id="20045-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="20045-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="20045-110">S_OK</span></span>|<span data-ttu-id="20045-111">`SuspensionEnding`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="20045-111">`SuspensionEnding` returned successfully.</span></span>|  
|<span data-ttu-id="20045-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="20045-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="20045-113">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="20045-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="20045-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="20045-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="20045-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="20045-115">The call timed out.</span></span>|  
|<span data-ttu-id="20045-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="20045-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="20045-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="20045-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="20045-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="20045-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="20045-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="20045-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="20045-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="20045-120">E_FAIL</span></span>|<span data-ttu-id="20045-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="20045-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="20045-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="20045-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="20045-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="20045-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20045-124">備註</span><span class="sxs-lookup"><span data-stu-id="20045-124">Remarks</span></span>  
 <span data-ttu-id="20045-125">CLR 會呼叫`SuspensionEnding`之後執行記憶體回收，以通知主機在執行緒正在繼續執行。</span><span class="sxs-lookup"><span data-stu-id="20045-125">The CLR calls `SuspensionEnding` after it performs a garbage collection, to inform the host that the thread is resuming execution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="20045-126">請勿重新排程從發出方法呼叫的執行緒。</span><span class="sxs-lookup"><span data-stu-id="20045-126">Do not reschedule the thread the method call was made from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20045-127">需求</span><span class="sxs-lookup"><span data-stu-id="20045-127">Requirements</span></span>  
 <span data-ttu-id="20045-128">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="20045-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20045-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="20045-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="20045-130">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="20045-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20045-131">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20045-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20045-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="20045-132">See Also</span></span>  
 [<span data-ttu-id="20045-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="20045-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="20045-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="20045-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="20045-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="20045-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="20045-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="20045-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="20045-137">IHostGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="20045-137">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
