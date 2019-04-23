---
title: IHostTaskManager::BeginDelayAbort 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginDelayAbort
helpviewer_keywords:
- BeginDelayAbort method [.NET Framework hosting]
- IHostTaskManager::BeginDelayAbort method [.NET Framework hosting]
ms.assetid: 75f42a8b-ed68-4718-a030-a179cfba7d72
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 328462343669b3ea6bed2d86514ea348f6ae2b1e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197967"
---
# <a name="ihosttaskmanagerbegindelayabort-method"></a><span data-ttu-id="ec414-102">IHostTaskManager::BeginDelayAbort 方法</span><span class="sxs-lookup"><span data-stu-id="ec414-102">IHostTaskManager::BeginDelayAbort Method</span></span>
<span data-ttu-id="ec414-103">通知主機 managed 程式碼輸入的期間，不會中止目前的工作。</span><span class="sxs-lookup"><span data-stu-id="ec414-103">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec414-104">語法</span><span class="sxs-lookup"><span data-stu-id="ec414-104">Syntax</span></span>  
  
```  
HRESULT BeginDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ec414-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="ec414-105">Return Value</span></span>  
  
|<span data-ttu-id="ec414-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ec414-106">HRESULT</span></span>|<span data-ttu-id="ec414-107">描述</span><span class="sxs-lookup"><span data-stu-id="ec414-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ec414-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="ec414-108">S_OK</span></span>|<span data-ttu-id="ec414-109">`BeginDelayAbort` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="ec414-109">`BeginDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="ec414-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ec414-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ec414-111">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="ec414-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ec414-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ec414-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ec414-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="ec414-113">The call timed out.</span></span>|  
|<span data-ttu-id="ec414-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ec414-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ec414-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="ec414-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ec414-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ec414-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ec414-117">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="ec414-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ec414-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ec414-118">E_FAIL</span></span>|<span data-ttu-id="ec414-119">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="ec414-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ec414-120">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="ec414-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ec414-121">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="ec414-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ec414-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="ec414-122">E_UNEXPECTED</span></span>|<span data-ttu-id="ec414-123">`BeginDelayAbort` 已經呼叫，但對應的呼叫來[EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md)尚未收到。</span><span class="sxs-lookup"><span data-stu-id="ec414-123">`BeginDelayAbort` has already been called, but the corresponding call to [EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) has not yet been received.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec414-124">備註</span><span class="sxs-lookup"><span data-stu-id="ec414-124">Remarks</span></span>  
 <span data-ttu-id="ec414-125">主機必須中止目前的工作，直到`EndDelayAbort`呼叫。</span><span class="sxs-lookup"><span data-stu-id="ec414-125">The host must not abort the current task until `EndDelayAbort` is called.</span></span> <span data-ttu-id="ec414-126">如果另一個呼叫`BeginDelayAbort`的中間呼叫不會建立`EndDelayAbort`，主應用程式應該會傳回 E_UNEXPECTED 從`BeginDelayAbort`，以及應該採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="ec414-126">If another call to `BeginDelayAbort` is made without an intervening call to `EndDelayAbort`, the host should return E_UNEXPECTED from `BeginDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec414-127">需求</span><span class="sxs-lookup"><span data-stu-id="ec414-127">Requirements</span></span>  
 <span data-ttu-id="ec414-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ec414-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec414-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ec414-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ec414-130">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ec414-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ec414-131">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec414-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec414-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec414-132">See also</span></span>

- [<span data-ttu-id="ec414-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="ec414-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="ec414-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="ec414-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="ec414-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="ec414-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
