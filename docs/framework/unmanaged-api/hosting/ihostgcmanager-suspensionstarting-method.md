---
title: IHostGCManager::SuspensionStarting 方法
ms.date: 03/30/2017
api_name:
- IHostGCManager.SuspensionStarting
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::SuspensionStarting
helpviewer_keywords:
- SuspensionStarting method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionStarting method [.NET Framework hosting]
ms.assetid: c381f524-94cf-4fa2-9298-50f847a03431
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47ef5bb2539820d5a7bcd4ca6b4de86564290709
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213086"
---
# <a name="ihostgcmanagersuspensionstarting-method"></a><span data-ttu-id="906d6-102">IHostGCManager::SuspensionStarting 方法</span><span class="sxs-lookup"><span data-stu-id="906d6-102">IHostGCManager::SuspensionStarting Method</span></span>
<span data-ttu-id="906d6-103">Common language runtime (CLR) 會暫停執行的工作，以執行記憶體回收通知主機。</span><span class="sxs-lookup"><span data-stu-id="906d6-103">Notifies the host that the common language runtime (CLR) is suspending execution of tasks, to perform a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="906d6-104">語法</span><span class="sxs-lookup"><span data-stu-id="906d6-104">Syntax</span></span>  
  
```  
HRESULT SuspensionStarting ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="906d6-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="906d6-105">Return Value</span></span>  
  
|<span data-ttu-id="906d6-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="906d6-106">HRESULT</span></span>|<span data-ttu-id="906d6-107">描述</span><span class="sxs-lookup"><span data-stu-id="906d6-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="906d6-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="906d6-108">S_OK</span></span>|`SuspensionStarting` <span data-ttu-id="906d6-109">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="906d6-109">returned successfully.</span></span>|  
|<span data-ttu-id="906d6-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="906d6-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="906d6-111">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="906d6-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="906d6-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="906d6-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="906d6-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="906d6-113">The call timed out.</span></span>|  
|<span data-ttu-id="906d6-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="906d6-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="906d6-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="906d6-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="906d6-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="906d6-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="906d6-117">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="906d6-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="906d6-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="906d6-118">E_FAIL</span></span>|<span data-ttu-id="906d6-119">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="906d6-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="906d6-120">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="906d6-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="906d6-121">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="906d6-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="906d6-122">備註</span><span class="sxs-lookup"><span data-stu-id="906d6-122">Remarks</span></span>  
 <span data-ttu-id="906d6-123">CLR 會呼叫`SuspensionStarting`以通知主機進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="906d6-123">The CLR calls `SuspensionStarting` to inform the host that garbage collection is occurring.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="906d6-124">請勿重新排程這項工作。</span><span class="sxs-lookup"><span data-stu-id="906d6-124">Do not reschedule this task.</span></span> <span data-ttu-id="906d6-125">主機必須重新排程工作時[ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md)呼叫。</span><span class="sxs-lookup"><span data-stu-id="906d6-125">The host must reschedule a task when [ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="906d6-126">需求</span><span class="sxs-lookup"><span data-stu-id="906d6-126">Requirements</span></span>  
 <span data-ttu-id="906d6-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="906d6-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="906d6-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="906d6-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="906d6-129">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="906d6-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="906d6-130">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="906d6-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="906d6-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="906d6-131">See also</span></span>

- [<span data-ttu-id="906d6-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="906d6-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="906d6-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="906d6-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="906d6-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="906d6-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="906d6-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="906d6-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="906d6-136">IHostGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="906d6-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
