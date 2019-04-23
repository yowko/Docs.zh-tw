---
title: IHostTaskManager::EndDelayAbort 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndDelayAbort
helpviewer_keywords:
- EndDelayAbort method [.NET Framework hosting]
- IHostTaskManager::EndDelayAbort method [.NET Framework hosting]
ms.assetid: 6e02facb-2504-4356-9af5-0cee1f8436a7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10d12e5cab41f016ddee78089dc1df1f5c942ecd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59194440"
---
# <a name="ihosttaskmanagerenddelayabort-method"></a><span data-ttu-id="a2bfc-102">IHostTaskManager::EndDelayAbort 方法</span><span class="sxs-lookup"><span data-stu-id="a2bfc-102">IHostTaskManager::EndDelayAbort Method</span></span>
<span data-ttu-id="a2bfc-103">通知主機 managed 程式碼正在結束的期間，在其中必須不會中止目前的工作，遵循之前呼叫[ihosttaskmanager:: Begindelayabort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md)。</span><span class="sxs-lookup"><span data-stu-id="a2bfc-103">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to [IHostTaskManager::BeginDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2bfc-104">語法</span><span class="sxs-lookup"><span data-stu-id="a2bfc-104">Syntax</span></span>  
  
```  
HRESULT EndDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a2bfc-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="a2bfc-105">Return Value</span></span>  
  
|<span data-ttu-id="a2bfc-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a2bfc-106">HRESULT</span></span>|<span data-ttu-id="a2bfc-107">描述</span><span class="sxs-lookup"><span data-stu-id="a2bfc-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a2bfc-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="a2bfc-108">S_OK</span></span>|<span data-ttu-id="a2bfc-109">`EndDelayAbort` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="a2bfc-109">`EndDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="a2bfc-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a2bfc-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a2bfc-111">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="a2bfc-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a2bfc-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a2bfc-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a2bfc-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="a2bfc-113">The call timed out.</span></span>|  
|<span data-ttu-id="a2bfc-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a2bfc-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a2bfc-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="a2bfc-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a2bfc-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a2bfc-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a2bfc-117">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="a2bfc-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a2bfc-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a2bfc-118">E_FAIL</span></span>|<span data-ttu-id="a2bfc-119">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="a2bfc-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a2bfc-120">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="a2bfc-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a2bfc-121">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a2bfc-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a2bfc-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="a2bfc-122">E_UNEXPECTED</span></span>|<span data-ttu-id="a2bfc-123">`EndDelayAbort` 呼叫卻沒有對應呼叫`BeginDelayAbort`。</span><span class="sxs-lookup"><span data-stu-id="a2bfc-123">`EndDelayAbort` was called without a corresponding call to `BeginDelayAbort`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2bfc-124">備註</span><span class="sxs-lookup"><span data-stu-id="a2bfc-124">Remarks</span></span>  
 <span data-ttu-id="a2bfc-125">CLR 會對應呼叫`BeginDelayAbort`針對目前的工作，然後再呼叫`EndDelayAbort`。</span><span class="sxs-lookup"><span data-stu-id="a2bfc-125">The CLR makes a corresponding call to `BeginDelayAbort` on the current task before calling `EndDelayAbort`.</span></span> <span data-ttu-id="a2bfc-126">如果沒有這類對應的呼叫，主應用程式的實作[IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)應該會傳回 E_UNEXPECTED 從`EndDelayAbort`，以及應該採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="a2bfc-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED from `EndDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2bfc-127">需求</span><span class="sxs-lookup"><span data-stu-id="a2bfc-127">Requirements</span></span>  
 <span data-ttu-id="a2bfc-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a2bfc-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2bfc-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a2bfc-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a2bfc-130">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a2bfc-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a2bfc-131">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2bfc-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2bfc-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2bfc-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="a2bfc-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="a2bfc-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="a2bfc-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="a2bfc-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="a2bfc-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="a2bfc-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="a2bfc-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="a2bfc-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
