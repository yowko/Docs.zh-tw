---
title: "IHostTaskManager::BeginDelayAbort 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.BeginDelayAbort
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::BeginDelayAbort
helpviewer_keywords:
- BeginDelayAbort method [.NET Framework hosting]
- IHostTaskManager::BeginDelayAbort method [.NET Framework hosting]
ms.assetid: 75f42a8b-ed68-4718-a030-a179cfba7d72
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 17af69c533c62b6a25d498fb245dfefe162690ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagerbegindelayabort-method"></a><span data-ttu-id="06e82-102">IHostTaskManager::BeginDelayAbort 方法</span><span class="sxs-lookup"><span data-stu-id="06e82-102">IHostTaskManager::BeginDelayAbort Method</span></span>
<span data-ttu-id="06e82-103">通知主機 managed 程式碼正在進入的期間，不會中止目前的工作。</span><span class="sxs-lookup"><span data-stu-id="06e82-103">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06e82-104">語法</span><span class="sxs-lookup"><span data-stu-id="06e82-104">Syntax</span></span>  
  
```  
HRESULT BeginDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="06e82-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="06e82-105">Return Value</span></span>  
  
|<span data-ttu-id="06e82-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="06e82-106">HRESULT</span></span>|<span data-ttu-id="06e82-107">描述</span><span class="sxs-lookup"><span data-stu-id="06e82-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="06e82-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="06e82-108">S_OK</span></span>|<span data-ttu-id="06e82-109">`BeginDelayAbort`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="06e82-109">`BeginDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="06e82-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="06e82-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="06e82-111">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="06e82-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="06e82-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="06e82-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="06e82-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="06e82-113">The call timed out.</span></span>|  
|<span data-ttu-id="06e82-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="06e82-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="06e82-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="06e82-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="06e82-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="06e82-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="06e82-117">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="06e82-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="06e82-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="06e82-118">E_FAIL</span></span>|<span data-ttu-id="06e82-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="06e82-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="06e82-120">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="06e82-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="06e82-121">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="06e82-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="06e82-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="06e82-122">E_UNEXPECTED</span></span>|<span data-ttu-id="06e82-123">`BeginDelayAbort`已經呼叫，但對應呼叫[EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md)尚未收到。</span><span class="sxs-lookup"><span data-stu-id="06e82-123">`BeginDelayAbort` has already been called, but the corresponding call to [EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) has not yet been received.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06e82-124">備註</span><span class="sxs-lookup"><span data-stu-id="06e82-124">Remarks</span></span>  
 <span data-ttu-id="06e82-125">主機必須不會中止目前的工作，直到`EndDelayAbort`呼叫。</span><span class="sxs-lookup"><span data-stu-id="06e82-125">The host must not abort the current task until `EndDelayAbort` is called.</span></span> <span data-ttu-id="06e82-126">如果另一個呼叫`BeginDelayAbort`在未經的中間呼叫`EndDelayAbort`，主應用程式應該會傳回 E_UNEXPECTED 從`BeginDelayAbort`，並應該採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="06e82-126">If another call to `BeginDelayAbort` is made without an intervening call to `EndDelayAbort`, the host should return E_UNEXPECTED from `BeginDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06e82-127">需求</span><span class="sxs-lookup"><span data-stu-id="06e82-127">Requirements</span></span>  
 <span data-ttu-id="06e82-128">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="06e82-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06e82-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="06e82-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="06e82-130">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="06e82-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="06e82-131">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06e82-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06e82-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06e82-132">See Also</span></span>  
 [<span data-ttu-id="06e82-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="06e82-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="06e82-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="06e82-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="06e82-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="06e82-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="06e82-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="06e82-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
