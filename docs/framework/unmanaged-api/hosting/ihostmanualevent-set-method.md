---
title: IHostManualEvent::Set 方法
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Set
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Set
helpviewer_keywords:
- Set method, IHostManualEvent interface [.NET Framework hosting]
- IHostManualEvent::Set method [.NET Framework hosting]
ms.assetid: e930c174-f71d-4faa-bb59-f0fb3df4d77b
topic_type:
- apiref
ms.openlocfilehash: bc2b178c6c26a6de62982c35d5aeb9ea5359c2bf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679126"
---
# <a name="ihostmanualeventset-method"></a><span data-ttu-id="f423d-102">IHostManualEvent::Set 方法</span><span class="sxs-lookup"><span data-stu-id="f423d-102">IHostManualEvent::Set Method</span></span>

<span data-ttu-id="f423d-103">將目前的 [IHostManualEvent](ihostmanualevent-interface.md) 實例設定為已發出信號的狀態。</span><span class="sxs-lookup"><span data-stu-id="f423d-103">Sets the current [IHostManualEvent](ihostmanualevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f423d-104">語法</span><span class="sxs-lookup"><span data-stu-id="f423d-104">Syntax</span></span>  
  
```cpp  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f423d-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="f423d-105">Return Value</span></span>  
  
|<span data-ttu-id="f423d-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f423d-106">HRESULT</span></span>|<span data-ttu-id="f423d-107">描述</span><span class="sxs-lookup"><span data-stu-id="f423d-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f423d-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="f423d-108">S_OK</span></span>|<span data-ttu-id="f423d-109">`Set` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="f423d-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="f423d-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f423d-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f423d-111">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="f423d-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f423d-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f423d-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f423d-113">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="f423d-113">The call timed out.</span></span>|  
|<span data-ttu-id="f423d-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f423d-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f423d-115">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="f423d-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f423d-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f423d-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f423d-117">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="f423d-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f423d-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f423d-118">E_FAIL</span></span>|<span data-ttu-id="f423d-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="f423d-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f423d-120">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="f423d-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f423d-121">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="f423d-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f423d-122">需求</span><span class="sxs-lookup"><span data-stu-id="f423d-122">Requirements</span></span>  

 <span data-ttu-id="f423d-123">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f423d-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f423d-124">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f423d-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f423d-125">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="f423d-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f423d-126">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f423d-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f423d-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f423d-127">See also</span></span>

- [<span data-ttu-id="f423d-128">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="f423d-128">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="f423d-129">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="f423d-129">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="f423d-130">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="f423d-130">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="f423d-131">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="f423d-131">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="f423d-132">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="f423d-132">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
