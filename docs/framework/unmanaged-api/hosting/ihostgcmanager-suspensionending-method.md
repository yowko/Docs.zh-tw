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
ms.openlocfilehash: 527607d5c39e7f698ab44baf4af0e7600ae2f473
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222818"
---
# <a name="ihostgcmanagersuspensionending-method"></a><span data-ttu-id="fca40-102">IHostGCManager::SuspensionEnding 方法</span><span class="sxs-lookup"><span data-stu-id="fca40-102">IHostGCManager::SuspensionEnding Method</span></span>
<span data-ttu-id="fca40-103">通知主機 common language runtime (CLR) 會繼續已暫止記憶體回收的執行緒上的工作執行。</span><span class="sxs-lookup"><span data-stu-id="fca40-103">Notifies the host that the common language runtime (CLR) is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fca40-104">語法</span><span class="sxs-lookup"><span data-stu-id="fca40-104">Syntax</span></span>  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fca40-105">參數</span><span class="sxs-lookup"><span data-stu-id="fca40-105">Parameters</span></span>  
 `generation`  
 <span data-ttu-id="fca40-106">[in]記憶體回收層代是剛完成，從中執行緒正在繼續。</span><span class="sxs-lookup"><span data-stu-id="fca40-106">[in] The garbage collection generation that is just finishing, from which the thread is resuming.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fca40-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="fca40-107">Return Value</span></span>  
  
|<span data-ttu-id="fca40-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fca40-108">HRESULT</span></span>|<span data-ttu-id="fca40-109">描述</span><span class="sxs-lookup"><span data-stu-id="fca40-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fca40-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fca40-110">S_OK</span></span>|`SuspensionEnding` <span data-ttu-id="fca40-111">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="fca40-111">returned successfully.</span></span>|  
|<span data-ttu-id="fca40-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fca40-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fca40-113">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="fca40-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fca40-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fca40-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fca40-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="fca40-115">The call timed out.</span></span>|  
|<span data-ttu-id="fca40-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fca40-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fca40-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="fca40-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fca40-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fca40-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fca40-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="fca40-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fca40-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fca40-120">E_FAIL</span></span>|<span data-ttu-id="fca40-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="fca40-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fca40-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="fca40-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fca40-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="fca40-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fca40-124">備註</span><span class="sxs-lookup"><span data-stu-id="fca40-124">Remarks</span></span>  
 <span data-ttu-id="fca40-125">CLR 會呼叫`SuspensionEnding`執行記憶體回收中，以通知主機執行緒會繼續執行之後。</span><span class="sxs-lookup"><span data-stu-id="fca40-125">The CLR calls `SuspensionEnding` after it performs a garbage collection, to inform the host that the thread is resuming execution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fca40-126">請勿重新排程從進行方法呼叫的執行緒。</span><span class="sxs-lookup"><span data-stu-id="fca40-126">Do not reschedule the thread the method call was made from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fca40-127">需求</span><span class="sxs-lookup"><span data-stu-id="fca40-127">Requirements</span></span>  
 <span data-ttu-id="fca40-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fca40-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fca40-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fca40-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fca40-130">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fca40-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="fca40-131">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="fca40-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fca40-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fca40-132">See also</span></span>

- [<span data-ttu-id="fca40-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="fca40-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="fca40-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="fca40-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="fca40-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="fca40-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="fca40-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="fca40-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="fca40-137">IHostGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="fca40-137">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
