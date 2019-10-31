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
ms.openlocfilehash: cb807a6a344c49baeedfa88aef989a9cb2ec8a46
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133910"
---
# <a name="ihostgcmanagerthreadisblockingforsuspension-method"></a><span data-ttu-id="edf94-102">IHostGCManager::ThreadIsBlockingForSuspension 方法</span><span class="sxs-lookup"><span data-stu-id="edf94-102">IHostGCManager::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="edf94-103">通知主機，方法呼叫的來源執行緒即將封鎖進行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="edf94-103">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edf94-104">語法</span><span class="sxs-lookup"><span data-stu-id="edf94-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="edf94-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="edf94-105">Return Value</span></span>  
  
|<span data-ttu-id="edf94-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="edf94-106">HRESULT</span></span>|<span data-ttu-id="edf94-107">描述</span><span class="sxs-lookup"><span data-stu-id="edf94-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="edf94-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="edf94-108">S_OK</span></span>|<span data-ttu-id="edf94-109">已成功傳回 `ThreadIsBlockingForSuspension`。</span><span class="sxs-lookup"><span data-stu-id="edf94-109">`ThreadIsBlockingForSuspension` returned successfully.</span></span>|  
|<span data-ttu-id="edf94-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="edf94-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="edf94-111">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="edf94-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="edf94-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="edf94-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="edf94-113">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="edf94-113">The call timed out.</span></span>|  
|<span data-ttu-id="edf94-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="edf94-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="edf94-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="edf94-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="edf94-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="edf94-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="edf94-117">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="edf94-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="edf94-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="edf94-118">E_FAIL</span></span>|<span data-ttu-id="edf94-119">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="edf94-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="edf94-120">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="edf94-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="edf94-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="edf94-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="edf94-122">備註</span><span class="sxs-lookup"><span data-stu-id="edf94-122">Remarks</span></span>  
 <span data-ttu-id="edf94-123">CLR 通常會在準備垃圾收集時呼叫 `ThreadIsBlockForSuspension` 方法，讓主機有機會重新排程未受管理工作的執行緒。</span><span class="sxs-lookup"><span data-stu-id="edf94-123">The CLR typically calls the `ThreadIsBlockForSuspension` method in preparation for a garbage collection, to give the host an opportunity to reschedule the thread for unmanaged tasks.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="edf94-124">只有在呼叫 `ThreadIsBlockingForSuspension`之後，主機才可以重新排定工作。</span><span class="sxs-lookup"><span data-stu-id="edf94-124">The host can reschedule tasks only after a call to `ThreadIsBlockingForSuspension`.</span></span> <span data-ttu-id="edf94-125">在執行時間呼叫[SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)之後，主機不得重新排定工作。</span><span class="sxs-lookup"><span data-stu-id="edf94-125">After the runtime calls [SuspensionStarting](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md), the host must not reschedule a task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edf94-126">需求</span><span class="sxs-lookup"><span data-stu-id="edf94-126">Requirements</span></span>  
 <span data-ttu-id="edf94-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="edf94-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edf94-128">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="edf94-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="edf94-129">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="edf94-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="edf94-130">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edf94-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edf94-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="edf94-131">See also</span></span>

- [<span data-ttu-id="edf94-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="edf94-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="edf94-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="edf94-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="edf94-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="edf94-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="edf94-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="edf94-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="edf94-136">IHostGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="edf94-136">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)
