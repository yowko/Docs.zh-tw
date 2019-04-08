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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194440"
---
# <a name="ihosttaskmanagerenddelayabort-method"></a><span data-ttu-id="dc01f-102">IHostTaskManager::EndDelayAbort 方法</span><span class="sxs-lookup"><span data-stu-id="dc01f-102">IHostTaskManager::EndDelayAbort Method</span></span>
<span data-ttu-id="dc01f-103">通知主機 managed 程式碼正在結束的期間，在其中必須不會中止目前的工作，遵循之前呼叫[ihosttaskmanager:: Begindelayabort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md)。</span><span class="sxs-lookup"><span data-stu-id="dc01f-103">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to [IHostTaskManager::BeginDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc01f-104">語法</span><span class="sxs-lookup"><span data-stu-id="dc01f-104">Syntax</span></span>  
  
```  
HRESULT EndDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="dc01f-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="dc01f-105">Return Value</span></span>  
  
|<span data-ttu-id="dc01f-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dc01f-106">HRESULT</span></span>|<span data-ttu-id="dc01f-107">描述</span><span class="sxs-lookup"><span data-stu-id="dc01f-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dc01f-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="dc01f-108">S_OK</span></span>|`EndDelayAbort` <span data-ttu-id="dc01f-109">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="dc01f-109">returned successfully.</span></span>|  
|<span data-ttu-id="dc01f-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dc01f-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dc01f-111">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="dc01f-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dc01f-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dc01f-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dc01f-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="dc01f-113">The call timed out.</span></span>|  
|<span data-ttu-id="dc01f-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dc01f-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dc01f-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="dc01f-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dc01f-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dc01f-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dc01f-117">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="dc01f-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dc01f-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dc01f-118">E_FAIL</span></span>|<span data-ttu-id="dc01f-119">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="dc01f-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dc01f-120">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="dc01f-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dc01f-121">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="dc01f-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="dc01f-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="dc01f-122">E_UNEXPECTED</span></span>|`EndDelayAbort` <span data-ttu-id="dc01f-123">呼叫卻沒有對應呼叫`BeginDelayAbort`。</span><span class="sxs-lookup"><span data-stu-id="dc01f-123">was called without a corresponding call to `BeginDelayAbort`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc01f-124">備註</span><span class="sxs-lookup"><span data-stu-id="dc01f-124">Remarks</span></span>  
 <span data-ttu-id="dc01f-125">CLR 會對應呼叫`BeginDelayAbort`針對目前的工作，然後再呼叫`EndDelayAbort`。</span><span class="sxs-lookup"><span data-stu-id="dc01f-125">The CLR makes a corresponding call to `BeginDelayAbort` on the current task before calling `EndDelayAbort`.</span></span> <span data-ttu-id="dc01f-126">如果沒有這類對應的呼叫，主應用程式的實作[IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)應該會傳回 E_UNEXPECTED 從`EndDelayAbort`，以及應該採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="dc01f-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED from `EndDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc01f-127">需求</span><span class="sxs-lookup"><span data-stu-id="dc01f-127">Requirements</span></span>  
 <span data-ttu-id="dc01f-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dc01f-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc01f-129">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dc01f-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dc01f-130">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="dc01f-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="dc01f-131">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="dc01f-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dc01f-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc01f-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="dc01f-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="dc01f-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="dc01f-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="dc01f-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="dc01f-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="dc01f-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="dc01f-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="dc01f-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
