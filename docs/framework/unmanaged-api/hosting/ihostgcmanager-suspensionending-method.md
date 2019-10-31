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
ms.openlocfilehash: 6ef04799c0062c40f1671cbe6d897a148e1b93bb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130476"
---
# <a name="ihostgcmanagersuspensionending-method"></a><span data-ttu-id="52cab-102">IHostGCManager::SuspensionEnding 方法</span><span class="sxs-lookup"><span data-stu-id="52cab-102">IHostGCManager::SuspensionEnding Method</span></span>
<span data-ttu-id="52cab-103">通知主機 common language runtime （CLR）正繼續執行已暫停進行垃圾收集的執行緒工作。</span><span class="sxs-lookup"><span data-stu-id="52cab-103">Notifies the host that the common language runtime (CLR) is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52cab-104">語法</span><span class="sxs-lookup"><span data-stu-id="52cab-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52cab-105">參數</span><span class="sxs-lookup"><span data-stu-id="52cab-105">Parameters</span></span>  
 `generation`  
 <span data-ttu-id="52cab-106">在剛完成的垃圾收集產生，執行緒正在從中繼續。</span><span class="sxs-lookup"><span data-stu-id="52cab-106">[in] The garbage collection generation that is just finishing, from which the thread is resuming.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52cab-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="52cab-107">Return Value</span></span>  
  
|<span data-ttu-id="52cab-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="52cab-108">HRESULT</span></span>|<span data-ttu-id="52cab-109">描述</span><span class="sxs-lookup"><span data-stu-id="52cab-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="52cab-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="52cab-110">S_OK</span></span>|<span data-ttu-id="52cab-111">已成功傳回 `SuspensionEnding`。</span><span class="sxs-lookup"><span data-stu-id="52cab-111">`SuspensionEnding` returned successfully.</span></span>|  
|<span data-ttu-id="52cab-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="52cab-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="52cab-113">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="52cab-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="52cab-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="52cab-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="52cab-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="52cab-115">The call timed out.</span></span>|  
|<span data-ttu-id="52cab-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="52cab-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="52cab-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="52cab-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="52cab-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="52cab-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="52cab-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="52cab-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="52cab-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="52cab-120">E_FAIL</span></span>|<span data-ttu-id="52cab-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="52cab-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="52cab-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="52cab-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="52cab-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="52cab-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52cab-124">備註</span><span class="sxs-lookup"><span data-stu-id="52cab-124">Remarks</span></span>  
 <span data-ttu-id="52cab-125">CLR 會在執行垃圾收集後呼叫 `SuspensionEnding`，以通知主機執行緒正在繼續執行。</span><span class="sxs-lookup"><span data-stu-id="52cab-125">The CLR calls `SuspensionEnding` after it performs a garbage collection, to inform the host that the thread is resuming execution.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="52cab-126">請不要重新排程呼叫方法所用的執行緒。</span><span class="sxs-lookup"><span data-stu-id="52cab-126">Do not reschedule the thread the method call was made from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52cab-127">需求</span><span class="sxs-lookup"><span data-stu-id="52cab-127">Requirements</span></span>  
 <span data-ttu-id="52cab-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="52cab-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52cab-129">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="52cab-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="52cab-130">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="52cab-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="52cab-131">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52cab-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52cab-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="52cab-132">See also</span></span>

- [<span data-ttu-id="52cab-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="52cab-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="52cab-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="52cab-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="52cab-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="52cab-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="52cab-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="52cab-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="52cab-137">IHostGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="52cab-137">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
