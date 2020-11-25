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
ms.openlocfilehash: 9120085f6a241bcda04946a843799987bf82bb84
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723879"
---
# <a name="ihostgcmanagerthreadisblockingforsuspension-method"></a><span data-ttu-id="b430b-102">IHostGCManager::ThreadIsBlockingForSuspension 方法</span><span class="sxs-lookup"><span data-stu-id="b430b-102">IHostGCManager::ThreadIsBlockingForSuspension Method</span></span>

<span data-ttu-id="b430b-103">通知主機發出方法呼叫的執行緒，即將封鎖垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="b430b-103">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b430b-104">語法</span><span class="sxs-lookup"><span data-stu-id="b430b-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b430b-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="b430b-105">Return Value</span></span>  
  
|<span data-ttu-id="b430b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b430b-106">HRESULT</span></span>|<span data-ttu-id="b430b-107">描述</span><span class="sxs-lookup"><span data-stu-id="b430b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b430b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="b430b-108">S_OK</span></span>|<span data-ttu-id="b430b-109">`ThreadIsBlockingForSuspension` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="b430b-109">`ThreadIsBlockingForSuspension` returned successfully.</span></span>|  
|<span data-ttu-id="b430b-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b430b-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b430b-111">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="b430b-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b430b-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b430b-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b430b-113">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="b430b-113">The call timed out.</span></span>|  
|<span data-ttu-id="b430b-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b430b-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b430b-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="b430b-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b430b-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b430b-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b430b-117">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="b430b-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b430b-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b430b-118">E_FAIL</span></span>|<span data-ttu-id="b430b-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="b430b-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b430b-120">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="b430b-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b430b-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b430b-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b430b-122">備註</span><span class="sxs-lookup"><span data-stu-id="b430b-122">Remarks</span></span>  

 <span data-ttu-id="b430b-123">CLR 通常會 `ThreadIsBlockForSuspension` 在準備垃圾收集時呼叫方法，讓主機有機會重新排程未受管理工作的執行緒。</span><span class="sxs-lookup"><span data-stu-id="b430b-123">The CLR typically calls the `ThreadIsBlockForSuspension` method in preparation for a garbage collection, to give the host an opportunity to reschedule the thread for unmanaged tasks.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b430b-124">主機只能在呼叫之後重新排程工作 `ThreadIsBlockingForSuspension` 。</span><span class="sxs-lookup"><span data-stu-id="b430b-124">The host can reschedule tasks only after a call to `ThreadIsBlockingForSuspension`.</span></span> <span data-ttu-id="b430b-125">執行時間呼叫 [SuspensionStarting](ihostgcmanager-suspensionstarting-method.md)之後，主機不能重新排程工作。</span><span class="sxs-lookup"><span data-stu-id="b430b-125">After the runtime calls [SuspensionStarting](ihostgcmanager-suspensionstarting-method.md), the host must not reschedule a task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b430b-126">需求</span><span class="sxs-lookup"><span data-stu-id="b430b-126">Requirements</span></span>  

 <span data-ttu-id="b430b-127">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b430b-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b430b-128">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b430b-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b430b-129">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="b430b-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b430b-130">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b430b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b430b-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b430b-131">See also</span></span>

- [<span data-ttu-id="b430b-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="b430b-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="b430b-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="b430b-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="b430b-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="b430b-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="b430b-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="b430b-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="b430b-136">IHostGCManager 介面</span><span class="sxs-lookup"><span data-stu-id="b430b-136">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)
