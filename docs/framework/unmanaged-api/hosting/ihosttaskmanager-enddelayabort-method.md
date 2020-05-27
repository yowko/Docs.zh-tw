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
ms.openlocfilehash: 156626ce907c13987c0cca15016263291961037d
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841967"
---
# <a name="ihosttaskmanagerenddelayabort-method"></a><span data-ttu-id="d9576-102">IHostTaskManager::EndDelayAbort 方法</span><span class="sxs-lookup"><span data-stu-id="d9576-102">IHostTaskManager::EndDelayAbort Method</span></span>
<span data-ttu-id="d9576-103">遵循先前對[IHostTaskManager：： BeginDelayAbort](ihosttaskmanager-begindelayabort-method.md)的呼叫，通知主機 managed 程式碼即將結束，但目前的工作不得中止。</span><span class="sxs-lookup"><span data-stu-id="d9576-103">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to [IHostTaskManager::BeginDelayAbort](ihosttaskmanager-begindelayabort-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9576-104">語法</span><span class="sxs-lookup"><span data-stu-id="d9576-104">Syntax</span></span>  
  
```cpp  
HRESULT EndDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d9576-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="d9576-105">Return Value</span></span>  
  
|<span data-ttu-id="d9576-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d9576-106">HRESULT</span></span>|<span data-ttu-id="d9576-107">描述</span><span class="sxs-lookup"><span data-stu-id="d9576-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d9576-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="d9576-108">S_OK</span></span>|<span data-ttu-id="d9576-109">`EndDelayAbort`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="d9576-109">`EndDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="d9576-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d9576-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d9576-111">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="d9576-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d9576-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d9576-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d9576-113">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="d9576-113">The call timed out.</span></span>|  
|<span data-ttu-id="d9576-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d9576-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d9576-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="d9576-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d9576-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d9576-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d9576-117">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="d9576-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d9576-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d9576-118">E_FAIL</span></span>|<span data-ttu-id="d9576-119">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="d9576-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d9576-120">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="d9576-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d9576-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d9576-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d9576-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="d9576-122">E_UNEXPECTED</span></span>|<span data-ttu-id="d9576-123">`EndDelayAbort`已呼叫，但沒有對應的呼叫 `BeginDelayAbort` 。</span><span class="sxs-lookup"><span data-stu-id="d9576-123">`EndDelayAbort` was called without a corresponding call to `BeginDelayAbort`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9576-124">備註</span><span class="sxs-lookup"><span data-stu-id="d9576-124">Remarks</span></span>  
 <span data-ttu-id="d9576-125">在呼叫之前，CLR 會對目前的工作進行相對應的呼叫 `BeginDelayAbort` `EndDelayAbort` 。</span><span class="sxs-lookup"><span data-stu-id="d9576-125">The CLR makes a corresponding call to `BeginDelayAbort` on the current task before calling `EndDelayAbort`.</span></span> <span data-ttu-id="d9576-126">如果沒有這類對應的呼叫，主機的[IHostTaskManager](ihosttaskmanager-interface.md)的執行應該會從傳回 E_UNEXPECTED `EndDelayAbort` ，而不會採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="d9576-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](ihosttaskmanager-interface.md) should return E_UNEXPECTED from `EndDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9576-127">規格需求</span><span class="sxs-lookup"><span data-stu-id="d9576-127">Requirements</span></span>  
 <span data-ttu-id="d9576-128">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d9576-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9576-129">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="d9576-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d9576-130">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d9576-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9576-131">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9576-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9576-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9576-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="d9576-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="d9576-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="d9576-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="d9576-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="d9576-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="d9576-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="d9576-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="d9576-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
