---
title: IHostGCManager::ThreadIsBlockingForSuspension 方法
ms.date: 03/30/2017
api_name:
- IHostGCManager.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension
helpviewer_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: 2657d45d-26d2-4d0a-8473-32b652e3321d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 740f408b84dad67ee20c2508ae42a9569ed095f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993235"
---
# <a name="ihostgcmanagerthreadisblockingforsuspension-method"></a><span data-ttu-id="6e3f8-102">IHostGCManager::ThreadIsBlockingForSuspension 方法</span><span class="sxs-lookup"><span data-stu-id="6e3f8-102">IHostGCManager::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="6e3f8-103">主應用程式在進行方法呼叫的執行緒即將封鎖記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="6e3f8-103">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e3f8-104">語法</span><span class="sxs-lookup"><span data-stu-id="6e3f8-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForSuspension ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="6e3f8-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="6e3f8-105">Return Value</span></span>  
  
|<span data-ttu-id="6e3f8-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6e3f8-106">HRESULT</span></span>|<span data-ttu-id="6e3f8-107">描述</span><span class="sxs-lookup"><span data-stu-id="6e3f8-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6e3f8-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="6e3f8-108">S_OK</span></span>|<span data-ttu-id="6e3f8-109">`ThreadIsBlockingForSuspension` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="6e3f8-109">`ThreadIsBlockingForSuspension` returned successfully.</span></span>|  
|<span data-ttu-id="6e3f8-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6e3f8-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6e3f8-111">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="6e3f8-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6e3f8-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6e3f8-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6e3f8-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="6e3f8-113">The call timed out.</span></span>|  
|<span data-ttu-id="6e3f8-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6e3f8-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6e3f8-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="6e3f8-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6e3f8-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6e3f8-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6e3f8-117">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="6e3f8-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6e3f8-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6e3f8-118">E_FAIL</span></span>|<span data-ttu-id="6e3f8-119">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="6e3f8-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6e3f8-120">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="6e3f8-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6e3f8-121">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="6e3f8-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e3f8-122">備註</span><span class="sxs-lookup"><span data-stu-id="6e3f8-122">Remarks</span></span>  
 <span data-ttu-id="6e3f8-123">CLR 通常會呼叫`ThreadIsBlockForSuspension`方法以準備進行回收，若要讓主應用程式有機會重新排程未受管理的工作的執行緒。</span><span class="sxs-lookup"><span data-stu-id="6e3f8-123">The CLR typically calls the `ThreadIsBlockForSuspension` method in preparation for a garbage collection, to give the host an opportunity to reschedule the thread for unmanaged tasks.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6e3f8-124">主應用程式可以重新排程工作只有在呼叫之後`ThreadIsBlockingForSuspension`。</span><span class="sxs-lookup"><span data-stu-id="6e3f8-124">The host can reschedule tasks only after a call to `ThreadIsBlockingForSuspension`.</span></span> <span data-ttu-id="6e3f8-125">在執行階段會呼叫後[SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)，主機必須重新排程工作。</span><span class="sxs-lookup"><span data-stu-id="6e3f8-125">After the runtime calls [SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md), the host must not reschedule a task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e3f8-126">需求</span><span class="sxs-lookup"><span data-stu-id="6e3f8-126">Requirements</span></span>  
 <span data-ttu-id="6e3f8-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6e3f8-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e3f8-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6e3f8-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6e3f8-129">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6e3f8-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6e3f8-130">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e3f8-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e3f8-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e3f8-131">See also</span></span>

- [<span data-ttu-id="6e3f8-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="6e3f8-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="6e3f8-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="6e3f8-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="6e3f8-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="6e3f8-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="6e3f8-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="6e3f8-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="6e3f8-136">IHostGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="6e3f8-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
