---
title: IHostSemaphore::Wait 方法
ms.date: 03/30/2017
api_name:
- IHostSemaphore.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore::Wait
helpviewer_keywords:
- IHostSemaphore::Wait method [.NET Framework hosting]
- Wait method, IHostSemaphore interface [.NET Framework hosting]
ms.assetid: 0da962a3-ce55-44dd-ab7a-14ad7105af4a
topic_type:
- apiref
ms.openlocfilehash: 69b2338e6992c386a3cd34a632d69b73a67f14fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683000"
---
# <a name="ihostsemaphorewait-method"></a><span data-ttu-id="88eac-102">IHostSemaphore::Wait 方法</span><span class="sxs-lookup"><span data-stu-id="88eac-102">IHostSemaphore::Wait Method</span></span>

<span data-ttu-id="88eac-103">導致目前的 [IHostSemaphore](ihostsemaphore-interface.md) 實例等到其擁有或經過指定的時間量為止。</span><span class="sxs-lookup"><span data-stu-id="88eac-103">Causes the current [IHostSemaphore](ihostsemaphore-interface.md) instance to wait until it is owned or the specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88eac-104">語法</span><span class="sxs-lookup"><span data-stu-id="88eac-104">Syntax</span></span>  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88eac-105">參數</span><span class="sxs-lookup"><span data-stu-id="88eac-105">Parameters</span></span>  

 `dwMilliseconds`  
 <span data-ttu-id="88eac-106">在如果目前的 `IHostSemaphore` 實例不是擁有的，則傳回前等待的毫秒數。</span><span class="sxs-lookup"><span data-stu-id="88eac-106">[in] The number of milliseconds to wait before returning, if the current `IHostSemaphore` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="88eac-107">在其中一個 [WAIT_OPTION](wait-option-enumeration.md) 值，指定主機在此作業封鎖時應採取的動作。</span><span class="sxs-lookup"><span data-stu-id="88eac-107">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, specifying what action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88eac-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="88eac-108">Return Value</span></span>  
  
|<span data-ttu-id="88eac-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="88eac-109">HRESULT</span></span>|<span data-ttu-id="88eac-110">描述</span><span class="sxs-lookup"><span data-stu-id="88eac-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="88eac-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="88eac-111">S_OK</span></span>|<span data-ttu-id="88eac-112">`Wait` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="88eac-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="88eac-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="88eac-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="88eac-114">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="88eac-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="88eac-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="88eac-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="88eac-116">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="88eac-116">The call timed out.</span></span>|  
|<span data-ttu-id="88eac-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="88eac-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="88eac-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="88eac-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="88eac-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="88eac-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="88eac-120">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="88eac-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="88eac-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="88eac-121">E_FAIL</span></span>|<span data-ttu-id="88eac-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="88eac-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="88eac-123">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="88eac-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="88eac-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="88eac-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="88eac-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="88eac-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="88eac-126">主機在等候間隔期間偵測到鎖死，並選擇目前的 `IHostSemaphore` 實例作為鎖死的犧牲者。</span><span class="sxs-lookup"><span data-stu-id="88eac-126">The host detected a deadlock during the wait interval, and chose the current `IHostSemaphore` instance as a deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="88eac-127">需求</span><span class="sxs-lookup"><span data-stu-id="88eac-127">Requirements</span></span>  

 <span data-ttu-id="88eac-128">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="88eac-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88eac-129">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="88eac-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="88eac-130">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="88eac-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="88eac-131">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88eac-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88eac-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88eac-132">See also</span></span>

- [<span data-ttu-id="88eac-133">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="88eac-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="88eac-134">IHostAutoEvent 介面</span><span class="sxs-lookup"><span data-stu-id="88eac-134">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="88eac-135">IHostManualEvent 介面</span><span class="sxs-lookup"><span data-stu-id="88eac-135">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="88eac-136">IHostSemaphore 介面</span><span class="sxs-lookup"><span data-stu-id="88eac-136">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="88eac-137">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="88eac-137">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
