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
ms.openlocfilehash: 4c05ee766bf40be2e9c39f01c7e1b16cb9fab50d
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804842"
---
# <a name="ihostgcmanagersuspensionending-method"></a><span data-ttu-id="52c0f-102">IHostGCManager::SuspensionEnding 方法</span><span class="sxs-lookup"><span data-stu-id="52c0f-102">IHostGCManager::SuspensionEnding Method</span></span>
<span data-ttu-id="52c0f-103">通知主機 common language runtime （CLR）正繼續執行已暫停進行垃圾收集的執行緒工作。</span><span class="sxs-lookup"><span data-stu-id="52c0f-103">Notifies the host that the common language runtime (CLR) is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52c0f-104">語法</span><span class="sxs-lookup"><span data-stu-id="52c0f-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52c0f-105">參數</span><span class="sxs-lookup"><span data-stu-id="52c0f-105">Parameters</span></span>  
 `generation`  
 <span data-ttu-id="52c0f-106">在剛完成的垃圾收集產生，執行緒正在從中繼續。</span><span class="sxs-lookup"><span data-stu-id="52c0f-106">[in] The garbage collection generation that is just finishing, from which the thread is resuming.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52c0f-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="52c0f-107">Return Value</span></span>  
  
|<span data-ttu-id="52c0f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="52c0f-108">HRESULT</span></span>|<span data-ttu-id="52c0f-109">描述</span><span class="sxs-lookup"><span data-stu-id="52c0f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="52c0f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="52c0f-110">S_OK</span></span>|<span data-ttu-id="52c0f-111">`SuspensionEnding`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="52c0f-111">`SuspensionEnding` returned successfully.</span></span>|  
|<span data-ttu-id="52c0f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="52c0f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="52c0f-113">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="52c0f-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="52c0f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="52c0f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="52c0f-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="52c0f-115">The call timed out.</span></span>|  
|<span data-ttu-id="52c0f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="52c0f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="52c0f-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="52c0f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="52c0f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="52c0f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="52c0f-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="52c0f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="52c0f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="52c0f-120">E_FAIL</span></span>|<span data-ttu-id="52c0f-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="52c0f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="52c0f-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="52c0f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="52c0f-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="52c0f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52c0f-124">備註</span><span class="sxs-lookup"><span data-stu-id="52c0f-124">Remarks</span></span>  
 <span data-ttu-id="52c0f-125">CLR 會在 `SuspensionEnding` 執行垃圾收集後呼叫，以通知主機執行緒正在繼續執行。</span><span class="sxs-lookup"><span data-stu-id="52c0f-125">The CLR calls `SuspensionEnding` after it performs a garbage collection, to inform the host that the thread is resuming execution.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="52c0f-126">請不要重新排程呼叫方法所用的執行緒。</span><span class="sxs-lookup"><span data-stu-id="52c0f-126">Do not reschedule the thread the method call was made from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52c0f-127">規格需求</span><span class="sxs-lookup"><span data-stu-id="52c0f-127">Requirements</span></span>  
 <span data-ttu-id="52c0f-128">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="52c0f-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52c0f-129">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="52c0f-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="52c0f-130">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="52c0f-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="52c0f-131">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52c0f-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52c0f-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52c0f-132">See also</span></span>

- [<span data-ttu-id="52c0f-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="52c0f-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="52c0f-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="52c0f-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="52c0f-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="52c0f-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="52c0f-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="52c0f-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="52c0f-137">IHostGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="52c0f-137">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)
