---
title: IHostManualEvent::Wait 方法
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Wait
helpviewer_keywords:
- IHostManualEvent::Wait method [.NET Framework hosting]
- Wait method, IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 1fbb7d8b-8a23-4c2b-8376-1a70cd2d6030
topic_type:
- apiref
ms.openlocfilehash: 3fe8434ba4a7fc49b99bdf3084ce4f3981f25a9b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719823"
---
# <a name="ihostmanualeventwait-method"></a><span data-ttu-id="d1aa3-102">IHostManualEvent::Wait 方法</span><span class="sxs-lookup"><span data-stu-id="d1aa3-102">IHostManualEvent::Wait Method</span></span>

<span data-ttu-id="d1aa3-103">導致目前的 [IHostManualEvent](ihostmanualevent-interface.md) 實例等到其擁有或經過指定的時間量為止。</span><span class="sxs-lookup"><span data-stu-id="d1aa3-103">Causes the current [IHostManualEvent](ihostmanualevent-interface.md) instance to wait until it is owned, or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1aa3-104">語法</span><span class="sxs-lookup"><span data-stu-id="d1aa3-104">Syntax</span></span>  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1aa3-105">參數</span><span class="sxs-lookup"><span data-stu-id="d1aa3-105">Parameters</span></span>  

 `dwMilliseconds`  
 <span data-ttu-id="d1aa3-106">在如果目前的 `IHostManualEvent` 實例不是擁有的，則傳回前等待的毫秒數。</span><span class="sxs-lookup"><span data-stu-id="d1aa3-106">[in] The number of milliseconds to wait before returning, if the current `IHostManualEvent` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="d1aa3-107">在其中一個 [WAIT_OPTION](wait-option-enumeration.md) 值，指出此作業封鎖時，主機應採取的動作。</span><span class="sxs-lookup"><span data-stu-id="d1aa3-107">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, indicating the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1aa3-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="d1aa3-108">Return Value</span></span>  
  
|<span data-ttu-id="d1aa3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d1aa3-109">HRESULT</span></span>|<span data-ttu-id="d1aa3-110">描述</span><span class="sxs-lookup"><span data-stu-id="d1aa3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d1aa3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d1aa3-111">S_OK</span></span>|<span data-ttu-id="d1aa3-112">`Wait` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="d1aa3-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="d1aa3-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d1aa3-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d1aa3-114">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="d1aa3-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d1aa3-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d1aa3-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d1aa3-116">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="d1aa3-116">The call timed out.</span></span>|  
|<span data-ttu-id="d1aa3-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d1aa3-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d1aa3-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="d1aa3-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d1aa3-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d1aa3-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d1aa3-120">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="d1aa3-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d1aa3-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d1aa3-121">E_FAIL</span></span>|<span data-ttu-id="d1aa3-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="d1aa3-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d1aa3-123">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="d1aa3-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d1aa3-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d1aa3-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d1aa3-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="d1aa3-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="d1aa3-126">主機在等候間隔期間偵測到鎖死，並選擇目前的 `IHostManualEvent` 實例作為鎖死的犧牲者。</span><span class="sxs-lookup"><span data-stu-id="d1aa3-126">The host detected a deadlock during the wait interval, and chose the current `IHostManualEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d1aa3-127">需求</span><span class="sxs-lookup"><span data-stu-id="d1aa3-127">Requirements</span></span>  

 <span data-ttu-id="d1aa3-128">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d1aa3-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1aa3-129">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d1aa3-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d1aa3-130">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="d1aa3-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d1aa3-131">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1aa3-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1aa3-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1aa3-132">See also</span></span>

- [<span data-ttu-id="d1aa3-133">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="d1aa3-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="d1aa3-134">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="d1aa3-134">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="d1aa3-135">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="d1aa3-135">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="d1aa3-136">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="d1aa3-136">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="d1aa3-137">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="d1aa3-137">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
