---
title: IHostGCManager::SuspensionEnding 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f2835c9846657edffc745c435211f93b20f7173
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438830"
---
# <a name="ihostgcmanagersuspensionending-method"></a><span data-ttu-id="2b7f6-102">IHostGCManager::SuspensionEnding 方法</span><span class="sxs-lookup"><span data-stu-id="2b7f6-102">IHostGCManager::SuspensionEnding Method</span></span>
<span data-ttu-id="2b7f6-103">通知主機 common language runtime (CLR) 正在繼續執行的工作已暫止記憶體回收的執行緒上執行。</span><span class="sxs-lookup"><span data-stu-id="2b7f6-103">Notifies the host that the common language runtime (CLR) is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b7f6-104">語法</span><span class="sxs-lookup"><span data-stu-id="2b7f6-104">Syntax</span></span>  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2b7f6-105">參數</span><span class="sxs-lookup"><span data-stu-id="2b7f6-105">Parameters</span></span>  
 `generation`  
 <span data-ttu-id="2b7f6-106">[in]剛完成，記憶體回收集合產生的執行緒正在繼續。</span><span class="sxs-lookup"><span data-stu-id="2b7f6-106">[in] The garbage collection generation that is just finishing, from which the thread is resuming.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b7f6-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="2b7f6-107">Return Value</span></span>  
  
|<span data-ttu-id="2b7f6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2b7f6-108">HRESULT</span></span>|<span data-ttu-id="2b7f6-109">描述</span><span class="sxs-lookup"><span data-stu-id="2b7f6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2b7f6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2b7f6-110">S_OK</span></span>|<span data-ttu-id="2b7f6-111">`SuspensionEnding` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="2b7f6-111">`SuspensionEnding` returned successfully.</span></span>|  
|<span data-ttu-id="2b7f6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2b7f6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2b7f6-113">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="2b7f6-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2b7f6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2b7f6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2b7f6-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="2b7f6-115">The call timed out.</span></span>|  
|<span data-ttu-id="2b7f6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2b7f6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2b7f6-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="2b7f6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2b7f6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2b7f6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2b7f6-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="2b7f6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2b7f6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2b7f6-120">E_FAIL</span></span>|<span data-ttu-id="2b7f6-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="2b7f6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2b7f6-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="2b7f6-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2b7f6-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="2b7f6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b7f6-124">備註</span><span class="sxs-lookup"><span data-stu-id="2b7f6-124">Remarks</span></span>  
 <span data-ttu-id="2b7f6-125">CLR 會呼叫`SuspensionEnding`之後執行記憶體回收，以通知主機在執行緒正在繼續執行。</span><span class="sxs-lookup"><span data-stu-id="2b7f6-125">The CLR calls `SuspensionEnding` after it performs a garbage collection, to inform the host that the thread is resuming execution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2b7f6-126">請勿重新排程從發出方法呼叫的執行緒。</span><span class="sxs-lookup"><span data-stu-id="2b7f6-126">Do not reschedule the thread the method call was made from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b7f6-127">需求</span><span class="sxs-lookup"><span data-stu-id="2b7f6-127">Requirements</span></span>  
 <span data-ttu-id="2b7f6-128">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2b7f6-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b7f6-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2b7f6-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2b7f6-130">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2b7f6-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2b7f6-131">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b7f6-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b7f6-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b7f6-132">See Also</span></span>  
 [<span data-ttu-id="2b7f6-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="2b7f6-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="2b7f6-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="2b7f6-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="2b7f6-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="2b7f6-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="2b7f6-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="2b7f6-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="2b7f6-137">IHostGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="2b7f6-137">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
