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
ms.openlocfilehash: 6add3cf4d83796b2d95de46cb64f5880a835b6ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731666"
---
# <a name="ihosttaskmanagerenddelayabort-method"></a><span data-ttu-id="eb590-102">IHostTaskManager::EndDelayAbort 方法</span><span class="sxs-lookup"><span data-stu-id="eb590-102">IHostTaskManager::EndDelayAbort Method</span></span>

<span data-ttu-id="eb590-103">在先前對 [IHostTaskManager：： BeginDelayAbort](ihosttaskmanager-begindelayabort-method.md)的呼叫之後，通知主機 managed 程式碼即將結束，而無法中止目前的工作。</span><span class="sxs-lookup"><span data-stu-id="eb590-103">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to [IHostTaskManager::BeginDelayAbort](ihosttaskmanager-begindelayabort-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb590-104">語法</span><span class="sxs-lookup"><span data-stu-id="eb590-104">Syntax</span></span>  
  
```cpp  
HRESULT EndDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="eb590-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="eb590-105">Return Value</span></span>  
  
|<span data-ttu-id="eb590-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eb590-106">HRESULT</span></span>|<span data-ttu-id="eb590-107">描述</span><span class="sxs-lookup"><span data-stu-id="eb590-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eb590-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="eb590-108">S_OK</span></span>|<span data-ttu-id="eb590-109">`EndDelayAbort` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="eb590-109">`EndDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="eb590-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="eb590-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="eb590-111">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="eb590-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="eb590-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="eb590-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="eb590-113">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="eb590-113">The call timed out.</span></span>|  
|<span data-ttu-id="eb590-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="eb590-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="eb590-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="eb590-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="eb590-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="eb590-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="eb590-117">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="eb590-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="eb590-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="eb590-118">E_FAIL</span></span>|<span data-ttu-id="eb590-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="eb590-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="eb590-120">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="eb590-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="eb590-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="eb590-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="eb590-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="eb590-122">E_UNEXPECTED</span></span>|<span data-ttu-id="eb590-123">`EndDelayAbort` 呼叫時沒有對應的呼叫 `BeginDelayAbort` 。</span><span class="sxs-lookup"><span data-stu-id="eb590-123">`EndDelayAbort` was called without a corresponding call to `BeginDelayAbort`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb590-124">備註</span><span class="sxs-lookup"><span data-stu-id="eb590-124">Remarks</span></span>  

 <span data-ttu-id="eb590-125">在呼叫之前，CLR 會在目前的工作上進行對應的呼叫 `BeginDelayAbort` `EndDelayAbort` 。</span><span class="sxs-lookup"><span data-stu-id="eb590-125">The CLR makes a corresponding call to `BeginDelayAbort` on the current task before calling `EndDelayAbort`.</span></span> <span data-ttu-id="eb590-126">如果沒有這類對應的呼叫，主機的 [IHostTaskManager](ihosttaskmanager-interface.md) 應該會傳回 E_UNEXPECTED `EndDelayAbort` ，且不應該採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="eb590-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](ihosttaskmanager-interface.md) should return E_UNEXPECTED from `EndDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb590-127">需求</span><span class="sxs-lookup"><span data-stu-id="eb590-127">Requirements</span></span>  

 <span data-ttu-id="eb590-128">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eb590-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb590-129">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="eb590-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eb590-130">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="eb590-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eb590-131">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb590-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb590-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb590-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="eb590-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="eb590-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="eb590-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="eb590-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="eb590-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="eb590-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="eb590-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="eb590-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
