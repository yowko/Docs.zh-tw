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
ms.openlocfilehash: b765d5449cebbdec5f106a8e4743fee2f0ee5521
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133132"
---
# <a name="ihosttaskmanagerbegindelayabort-method"></a><span data-ttu-id="35358-102">IHostTaskManager::BeginDelayAbort 方法</span><span class="sxs-lookup"><span data-stu-id="35358-102">IHostTaskManager::BeginDelayAbort Method</span></span>
<span data-ttu-id="35358-103">通知主機 managed 程式碼所輸入的期間不得中止目前的工作。</span><span class="sxs-lookup"><span data-stu-id="35358-103">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35358-104">語法</span><span class="sxs-lookup"><span data-stu-id="35358-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="35358-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="35358-105">Return Value</span></span>  
  
|<span data-ttu-id="35358-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="35358-106">HRESULT</span></span>|<span data-ttu-id="35358-107">描述</span><span class="sxs-lookup"><span data-stu-id="35358-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="35358-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="35358-108">S_OK</span></span>|<span data-ttu-id="35358-109">已成功傳回 `BeginDelayAbort`。</span><span class="sxs-lookup"><span data-stu-id="35358-109">`BeginDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="35358-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="35358-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="35358-111">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="35358-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="35358-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="35358-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="35358-113">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="35358-113">The call timed out.</span></span>|  
|<span data-ttu-id="35358-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="35358-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="35358-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="35358-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="35358-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="35358-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="35358-117">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="35358-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="35358-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="35358-118">E_FAIL</span></span>|<span data-ttu-id="35358-119">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="35358-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="35358-120">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="35358-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="35358-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="35358-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="35358-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="35358-122">E_UNEXPECTED</span></span>|<span data-ttu-id="35358-123">已呼叫 `BeginDelayAbort`，但尚未收到對[EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md)的對應呼叫。</span><span class="sxs-lookup"><span data-stu-id="35358-123">`BeginDelayAbort` has already been called, but the corresponding call to [EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) has not yet been received.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35358-124">備註</span><span class="sxs-lookup"><span data-stu-id="35358-124">Remarks</span></span>  
 <span data-ttu-id="35358-125">在呼叫 `EndDelayAbort` 之前，主機不得中止目前的工作。</span><span class="sxs-lookup"><span data-stu-id="35358-125">The host must not abort the current task until `EndDelayAbort` is called.</span></span> <span data-ttu-id="35358-126">如果在沒有呼叫 `EndDelayAbort`的情況下進行另一個 `BeginDelayAbort` 呼叫，主機應該會從 `BeginDelayAbort`傳回 E_UNEXPECTED，而不會採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="35358-126">If another call to `BeginDelayAbort` is made without an intervening call to `EndDelayAbort`, the host should return E_UNEXPECTED from `BeginDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35358-127">需求</span><span class="sxs-lookup"><span data-stu-id="35358-127">Requirements</span></span>  
 <span data-ttu-id="35358-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="35358-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35358-129">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="35358-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="35358-130">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="35358-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="35358-131">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35358-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35358-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="35358-132">See also</span></span>

- [<span data-ttu-id="35358-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="35358-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="35358-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="35358-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="35358-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="35358-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
