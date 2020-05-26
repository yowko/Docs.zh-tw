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
ms.openlocfilehash: f2b4028c78daf266e4ffecd86e6b0b30b9607d5b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804809"
---
# <a name="ihostgcmanagersuspensionstarting-method"></a><span data-ttu-id="95ec8-102">IHostGCManager::SuspensionStarting 方法</span><span class="sxs-lookup"><span data-stu-id="95ec8-102">IHostGCManager::SuspensionStarting Method</span></span>
<span data-ttu-id="95ec8-103">通知主機 common language runtime （CLR）正在暫停執行工作，以執行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="95ec8-103">Notifies the host that the common language runtime (CLR) is suspending execution of tasks, to perform a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95ec8-104">語法</span><span class="sxs-lookup"><span data-stu-id="95ec8-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="95ec8-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="95ec8-105">Return Value</span></span>  
  
|<span data-ttu-id="95ec8-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="95ec8-106">HRESULT</span></span>|<span data-ttu-id="95ec8-107">描述</span><span class="sxs-lookup"><span data-stu-id="95ec8-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="95ec8-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="95ec8-108">S_OK</span></span>|<span data-ttu-id="95ec8-109">`SuspensionStarting`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="95ec8-109">`SuspensionStarting` returned successfully.</span></span>|  
|<span data-ttu-id="95ec8-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="95ec8-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="95ec8-111">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="95ec8-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="95ec8-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="95ec8-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="95ec8-113">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="95ec8-113">The call timed out.</span></span>|  
|<span data-ttu-id="95ec8-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="95ec8-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="95ec8-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="95ec8-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="95ec8-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="95ec8-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="95ec8-117">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="95ec8-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="95ec8-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="95ec8-118">E_FAIL</span></span>|<span data-ttu-id="95ec8-119">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="95ec8-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="95ec8-120">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="95ec8-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="95ec8-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="95ec8-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95ec8-122">備註</span><span class="sxs-lookup"><span data-stu-id="95ec8-122">Remarks</span></span>  
 <span data-ttu-id="95ec8-123">CLR 會呼叫， `SuspensionStarting` 以通知主機發生垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="95ec8-123">The CLR calls `SuspensionStarting` to inform the host that garbage collection is occurring.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="95ec8-124">請勿重新排定此工作。</span><span class="sxs-lookup"><span data-stu-id="95ec8-124">Do not reschedule this task.</span></span> <span data-ttu-id="95ec8-125">呼叫[ThreadIsBlockingForSuspension](ihostgcmanager-threadisblockingforsuspension-method.md)時，主機必須重新排定工作。</span><span class="sxs-lookup"><span data-stu-id="95ec8-125">The host must reschedule a task when [ThreadIsBlockingForSuspension](ihostgcmanager-threadisblockingforsuspension-method.md) is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95ec8-126">規格需求</span><span class="sxs-lookup"><span data-stu-id="95ec8-126">Requirements</span></span>  
 <span data-ttu-id="95ec8-127">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="95ec8-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95ec8-128">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="95ec8-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="95ec8-129">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="95ec8-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="95ec8-130">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95ec8-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95ec8-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95ec8-131">See also</span></span>

- [<span data-ttu-id="95ec8-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="95ec8-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="95ec8-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="95ec8-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="95ec8-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="95ec8-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="95ec8-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="95ec8-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="95ec8-136">IHostGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="95ec8-136">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)
