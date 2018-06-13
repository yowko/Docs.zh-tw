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
ms.openlocfilehash: 6a84da2a337554873e94b47eb51916088edbb5a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439029"
---
# <a name="ihostgcmanagersuspensionstarting-method"></a><span data-ttu-id="da636-102">IHostGCManager::SuspensionStarting 方法</span><span class="sxs-lookup"><span data-stu-id="da636-102">IHostGCManager::SuspensionStarting Method</span></span>
<span data-ttu-id="da636-103">通知主機 common language runtime (CLR) 會暫停執行的工作，以執行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="da636-103">Notifies the host that the common language runtime (CLR) is suspending execution of tasks, to perform a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da636-104">語法</span><span class="sxs-lookup"><span data-stu-id="da636-104">Syntax</span></span>  
  
```  
HRESULT SuspensionStarting ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="da636-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="da636-105">Return Value</span></span>  
  
|<span data-ttu-id="da636-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="da636-106">HRESULT</span></span>|<span data-ttu-id="da636-107">描述</span><span class="sxs-lookup"><span data-stu-id="da636-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="da636-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="da636-108">S_OK</span></span>|<span data-ttu-id="da636-109">`SuspensionStarting` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="da636-109">`SuspensionStarting` returned successfully.</span></span>|  
|<span data-ttu-id="da636-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="da636-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="da636-111">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="da636-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="da636-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="da636-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="da636-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="da636-113">The call timed out.</span></span>|  
|<span data-ttu-id="da636-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="da636-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="da636-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="da636-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="da636-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="da636-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="da636-117">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="da636-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="da636-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="da636-118">E_FAIL</span></span>|<span data-ttu-id="da636-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="da636-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="da636-120">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="da636-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="da636-121">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="da636-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da636-122">備註</span><span class="sxs-lookup"><span data-stu-id="da636-122">Remarks</span></span>  
 <span data-ttu-id="da636-123">CLR 會呼叫`SuspensionStarting`通知已發生記憶體回收的主機。</span><span class="sxs-lookup"><span data-stu-id="da636-123">The CLR calls `SuspensionStarting` to inform the host that garbage collection is occurring.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="da636-124">不重新排定此工作。</span><span class="sxs-lookup"><span data-stu-id="da636-124">Do not reschedule this task.</span></span> <span data-ttu-id="da636-125">主機必須排定工作時[ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md)呼叫。</span><span class="sxs-lookup"><span data-stu-id="da636-125">The host must reschedule a task when [ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md) is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da636-126">需求</span><span class="sxs-lookup"><span data-stu-id="da636-126">Requirements</span></span>  
 <span data-ttu-id="da636-127">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="da636-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da636-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="da636-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="da636-129">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="da636-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="da636-130">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da636-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da636-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da636-131">See Also</span></span>  
 [<span data-ttu-id="da636-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="da636-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="da636-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="da636-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="da636-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="da636-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="da636-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="da636-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="da636-136">IHostGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="da636-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
