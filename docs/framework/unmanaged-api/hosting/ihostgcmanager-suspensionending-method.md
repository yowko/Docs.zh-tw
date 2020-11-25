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
ms.openlocfilehash: e2624f5fce168662fac8fd5f4324617c7acf802c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729547"
---
# <a name="ihostgcmanagersuspensionending-method"></a><span data-ttu-id="fd17c-102">IHostGCManager::SuspensionEnding 方法</span><span class="sxs-lookup"><span data-stu-id="fd17c-102">IHostGCManager::SuspensionEnding Method</span></span>

<span data-ttu-id="fd17c-103">通知主機 common language runtime (CLR) 正在繼續執行已暫止垃圾收集之執行緒上的工作。</span><span class="sxs-lookup"><span data-stu-id="fd17c-103">Notifies the host that the common language runtime (CLR) is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd17c-104">語法</span><span class="sxs-lookup"><span data-stu-id="fd17c-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd17c-105">參數</span><span class="sxs-lookup"><span data-stu-id="fd17c-105">Parameters</span></span>  

 `generation`  
 <span data-ttu-id="fd17c-106">在只是完成執行緒的垃圾收集產生，執行緒正在從中繼續。</span><span class="sxs-lookup"><span data-stu-id="fd17c-106">[in] The garbage collection generation that is just finishing, from which the thread is resuming.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd17c-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="fd17c-107">Return Value</span></span>  
  
|<span data-ttu-id="fd17c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fd17c-108">HRESULT</span></span>|<span data-ttu-id="fd17c-109">描述</span><span class="sxs-lookup"><span data-stu-id="fd17c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fd17c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fd17c-110">S_OK</span></span>|<span data-ttu-id="fd17c-111">`SuspensionEnding` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="fd17c-111">`SuspensionEnding` returned successfully.</span></span>|  
|<span data-ttu-id="fd17c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fd17c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fd17c-113">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="fd17c-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fd17c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fd17c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fd17c-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="fd17c-115">The call timed out.</span></span>|  
|<span data-ttu-id="fd17c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fd17c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fd17c-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="fd17c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fd17c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fd17c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fd17c-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="fd17c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fd17c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fd17c-120">E_FAIL</span></span>|<span data-ttu-id="fd17c-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="fd17c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fd17c-122">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="fd17c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fd17c-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="fd17c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd17c-124">備註</span><span class="sxs-lookup"><span data-stu-id="fd17c-124">Remarks</span></span>  

 <span data-ttu-id="fd17c-125">CLR 會在 `SuspensionEnding` 執行垃圾收集之後呼叫，以通知主機執行緒正在繼續執行。</span><span class="sxs-lookup"><span data-stu-id="fd17c-125">The CLR calls `SuspensionEnding` after it performs a garbage collection, to inform the host that the thread is resuming execution.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fd17c-126">請勿重新排程進行方法呼叫的執行緒。</span><span class="sxs-lookup"><span data-stu-id="fd17c-126">Do not reschedule the thread the method call was made from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd17c-127">需求</span><span class="sxs-lookup"><span data-stu-id="fd17c-127">Requirements</span></span>  

 <span data-ttu-id="fd17c-128">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fd17c-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd17c-129">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="fd17c-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fd17c-130">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="fd17c-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fd17c-131">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd17c-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd17c-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd17c-132">See also</span></span>

- [<span data-ttu-id="fd17c-133">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="fd17c-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="fd17c-134">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="fd17c-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="fd17c-135">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="fd17c-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="fd17c-136">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="fd17c-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="fd17c-137">IHostGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="fd17c-137">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)
